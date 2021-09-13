# Modifiche da apportare per implementare nuove istruzioni
Per imprementare una nuova istruzione é necessario modificare il file ijvm.conf inserendo il codice esadecimale che associeremo all'istruzione seguito dal nome dell'istruzione e da eventuali parametri(per esempio varnum). Questo non deve essere giá utilizzato per altre istruzioni.
Successivamente é necessario inserire nel file mic1ijvm.mal aggiungendo ".label" seguito dalla prima istuzione del codice e dal codice esadecimale 
In questo caso aggiungeremo quindi..., suppenendo che il codice operativo non sia impiegato per altre istruzioni
# IJVM
### Uguali
```java
.constant
objref 0xCAFE
.end-constant

.main
.var
result 
.end-var 
        LDC_W objref
        BIPUSH -1
        INVOKEVIRTUAL uguali
        ISTORE result
        HALT
.end-main

.method uguali(X)
.var
    mask 
    i
.end-var
        BIPUSH 16
        ISTORE i
        ILOAD X
        ISTORE mask
loop16: ILOAD i
        IFEQ end //controllo se il contatore i==0
        ILOAD mask //preparo lo shift
        DUP 
        IADD //shift a sinistra di 1
        ISTORE mask //pulisco lo stack
        IINC i -1 //decremento il contatore
        GOTO loop16
end:    ILOAD mask  //carico x<<16
        DUP
        ILOAD X
        IAND //pulizia bit non importanti 
        IF_ICMPEQ one
        BIPUSH 0 
        IRETURN
one:    BIPUSH 1
        IRETURN
.end-method
```
### Compl2range
```java
.constant
objref  0xCAFE
.end-constant

.main
.var
result
.end-var
        LDC_W objref
        BIPUSH 63
        BIPUSH 7
        INVOKEVIRTUAL compl2range
        ISTORE result
        HALT
.end-main

.method compl2range(x,n)
.var
min
max
.end-var
        IINC n -1 //n-1
        BIPUSH 1 
loop:   DUP 
        IADD //shift <<1
        IINC n -1 //decremento il contantore n
        ILOAD n
        IFEQ e-loop //controllo n==0
        GOTO loop
e-loop: DUP //sullo stack ho 2^(n-1)
        DUP 
        DUP //ho 4 copie di 2^n sullo stack
        ISUB //0
        SWAP
        ISUB //-2^(n-1)
        ISTORE min
        BIPUSH -1
        IADD //2^(n-1)-1
        ISTORE max
        ILOAD max
        ILOAD x
        ISUB //max-x
        DUP
        IFLT false 
        IFEQ false
        ILOAD x
        IFLT neg //x<0
        GOTO true 
neg:    ILOAD min
        ILOAD x
        ISUB //min-x
        DUP
        IFLT true
        IFEQ true
false:  BIPUSH 0 //x>=max
        IRETURN
true:   BIPUSH 1 //min<=x<=max
        IRETURN
.end-method
```
### Close
```java
.constant
objref  0xCAFE
.end-constant
.main
            LDC_W objref
            BIPUSH 123
            BIPUSH 4
            INVOKEVIRTUAL close
            HALT
.end-main
.method close(x,n)
            IINC n -1
            BIPUSH 1
loop:       DUP
            BIPUSH 1
            IADD
            IADD//shift<<1
            IINC n -1
            ILOAD n
            IFEQ end-loop
            GOTO loop
end-loop:   DUP
            ILOAD x
            SWAP
            ISUB //Se la maschera é piú grande del numero da controllare non ci saranno mai n bit a 1 in x
            IFLT false
            DUP
            DUP
            IAND //Cleanse bit inutili e applicazione maschera
            ISUB //Se le maschere sono uguali attendo 0 sullo stack
            IFEQ true //Se la maschera é uguale al risultato dell'operazione precedente ho n bit consecutivi a 1
            goto end-loop
false:      BIPUSH 0
            IRETURN
true:       BIPUSH 1
            IRETURN
.end-method
```
### ContaUni
```java
.constant
objref      0xCAFE
.end-constant
.main
        LDC_W objref
        BIPUSH 13
        INVOKEVIRTUAL ContaUni 
        HALT
.end-main
.method ContaUni(x)
.var
res
.end-var
        BIPUSH 0
        ISTORE res //inizializzo contatore
        BIPUSH 1 //inizializzo maschera
loop1:  DUP
        ILOAD x
        SWAP
        ISUB 
        IFLT end //Se la maschera é piú grande di X é inutile controllare
        DUP
        DUP
        ILOAD x
        IAND //cleanse bit inutili
        ISUB //Se il bit é ad 1 allora ho come risultato atteso 0 sullo stack
        IFEQ true
loop2:  DUP 
        IADD //SHIFT<<1
        GOTO loop1
true:   IINC RES 1 //incremento il contantore
        GOTO loop2
end:    ILOAD res
        IRETURN
.end-method
```
# Mic1
### ADDC2
```java
addc21  MAR = SP = SP - 1; rd //Decremento lo stack pointer e avvio una lettura, disponibile fra 2 cicli di clock    
addc22  H = TOS  //Salvo il contenuto di TOS in H              
addc23  MDR = TOS = MDR + H; wr; //Sommo MDR ad H, deposito poi il risultato in MDR e TOS
addc24  H=NOT TOS //Inverto i bit di TOS, ottenendo quindi il complemento ad 1, e salvandoli in H
addc25  MDR=TOS=H+1;wr;goto Main1 //sommo 1 ad H, salvando il risultato in TOS e MDR, avviando poi la scrittura
```
### POPIFEQ
```java
popifeq1 H=LV //Salvo il riferimento al fondo del frame delle variabili locali in H
popifeq2 MAR=H+MBRU; rd //Calcolo lo scostamento MBRU da LV
popifeq3 PC=PC+1; fetch //Mentre aspetto il contenuto di MDR incremento il program counter
popifeq4 H=MDR //Salvo il contenuto di MDR in H
popifeq5 Z = TOS - H; if(Z) goto popifeq6; else goto Main1 // 
popifeq6 MAR=SP=SP-1; rd //Se sono uguali decremento lo stack pointer(pop)
popifeq7 //ciclo a vuoto mentre attendo il contenuto del nuovo MDR
popifeq8 TOS=MDR; goto Main1 //Aggiorno TOS con il contenuto di MDR e continuo l'esecuzione del programma
```
### SumDif
```java
sumdif1 MAR=SP=SP-1;rd //leggo il valore di A, disponibile tra 2 cicli di clock  
sumdif2 H=TOS //Salvo B nel registro H  
sumdif3 TOS=OPC=MDR //A é disponibile in lettura in MDR, aggiorno TOS e faccio una copia su OPC  
sumdif4 N=TOS-H;if(N) goto sumdif8;else goto sumdif5 //Faccio A(TOS)-B(H), se N sará uguale ad 1 allora A<B  
sumdif5 MAR=SP=SP+1;rd //reincremento lo stack pointer per far ripuntare MAR ad B, attendo di poter operare su MDR  
sumdif6 MDR=TOS=TOS+H;wr //TOS=A(TOS)+B(H), attendo la scrittura in memoria  
sumdif7 MDR=TOS=OPC-H;wr;goto Main1 //MDR=TOS=a(MDR)  
sumdif8 MAR=SP=SP+1;rd;goto Main1 //Rimetto lo stack pointer a posto e vado a Main1
```
### Store2V
```java
sumdif1 MAR=SP=SP-1;rd //leggo il valore di A, disponibile tra 2 cicli di clock  
sumdif2 H=TOS //Salvo B nel registro H  
sumdif3 TOS=OPC=MDR //A é disponibile in lettura in MDR, aggiorno TOS e faccio una copia su OPC  
sumdif4 N=TOS-H;if(N) goto sumdif8;else goto sumdif5 //Faccio A(TOS)-B(H), se N sará uguale ad 1 allora A<B  
sumdif5 MAR=SP=SP+1;rd //reincremento lo stack pointer per far ripuntare MAR ad B, attendo di poter operare su MDR  
sumdif6 MDR=TOS=TOS+H;wr //TOS=A(TOS)+B(H), attendo la scrittura in memoria  
sumdif7 MDR=TOS=OPC-H;wr;goto Main1 //MDR=TOS=a(MDR)  
sumdif8 MAR=SP=SP+1;rd;goto Main1 //Rimetto lo stack pointer a posto e vado a Main1
```
### OVWRIFGT
```java
ovwrifgt1 H=LV //Salvo il riferimento a LV in H per calcolarmi successivamente lo scostamento 
ovwrifgt2 MAR=H+MBRU;rd  //Calcolo lo scostamento,avvio la lettura del contenuto della variabile, disponibile in MDR tra 2 cicli di clock
ovwrifgt3 PC=PC+1;fetch //Mentre aspetto il risultato della lettura, avvio il fetch del prossimo opcode
ovwrifgt4 H=MDR //Salvo il risultato della lettura in H
ovwrifgt5 N=TOS-H;if(N) goto ovwrifgt6;else goto Main1 //Facendo questa operazione controllo se TOS é maggiore di H.Se N avrá valore 1 allora proseguo nell'esuzione di OVRIFGT, altrimenti vado a Main1 e proseguo nell'esecuzione del programma
ovwrifgt6 MAR=SP;wr  //Pongo MAR uguale allo Stack Pointer e avvio una scrittura
ovwrifgt7 TOS=MDR;goto Main1 //Aggiorno TOS con il valore di MDR e vado a Main1
```

```java
INST3  MDR=TOS=TOS+H;wr
````