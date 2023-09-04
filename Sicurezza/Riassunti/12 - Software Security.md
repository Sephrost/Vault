Abbiamo precentemente trattato alcune problematiche che l'esecuzione di software(arbitrario o meno) puó causare per la sicurezza.

Ma possono essere presenti vulnerabilitá anche nel codice scritto senza porre troppa attenzione o nelle librerie di sistema.

## Concetti fondamentali
### Istruction Architecture
La CPU é la componente principale di ogni elaboratore, che preleva ed esegue i comandi descritti nel codice.

Esistono diverse architetture di CPU, ma le piú diffuse sicuramente sono:
- x86/i386(Amd e Intel)
- x86-64/amd64(Microsoft)
- ARM(Acorn)

Ognuna di queste architetture é costruita in una maniera specifica, l'**istruction set architecture**(**ISA**), che la CPU utilizza per eseguire i processi.
Noi tratteremo l'IA32/x86.

> Il docente usa il termine IA al posto di ISA, non só se fanno rifermiento alla stessa cosa ma suppongo di sí.

#### IA 32/x86
É la versione **little endian** a **32 bit** dell'ISA **x86** di Intel. É un'architettura **CISC**(*Complex Instruction Set Computer*), presenta quindi istruzioni di lunghezza variabile, e molte istruzioni per accedere e modificare le aree di memoria.

Presenta 8 registri general purpose di 32 bit e 6 segment register di 16 bit.

I resistri principali sono:

Nome del registro|Funzione
--|--
ESB|Top of stack pointer
EBP|Base pointer dello stack
EIP|Instruction pointer
EFLAGS|Flag
ESI|Stringa di origine/operazioni di memoria
EDI|Stringa di destinazione/operazioni di memoria
ECX|Contatore per i cicli
EAX|Valore di ritorno di una funzione

#### Gestione della memoria
Quando un programma viene chiamato, viene caricato in memoria e le sue sezioni vengono associate ai segmenti nel processo.

La struttura della memoria allcoata in un processo puó essere cosí descritta:
![[Pasted image 20230903151659.png]]

É divisa in varie sezioni:
- **.text**: le istruzione in linguaggio assembrativo del programma
- **.data**: le variabili statiche e globali inizializzate dal programma
- **.bss**: contiene le variabili allocate staticamente
- **heap**

Lo stack lo tratteremo a parte.
> Le sezioni sopra citate non sono state trattate a lezione, é solo per cultura personale.

##### Stack
Lo stack é una struttura dati **LIFO** che cresce verso il basso, dove vengono salvati gli indirizzi di ritorno, i parametri e talvolta i puntatori del frame.

Si accede ad esso tramite lo stack pointer, impostato al valore piú alto dello stack durante l'inizializzazione. Durante l'esecuzione lo stack puó crescere e decrescevere verso il basso attraverso due operazioni:
- **PUSH**: **inserisce** un elemento in **cima** allo stack
- **POP**: **rimuove** un **elemento** in cima allo stack e ne ritorna il valore

Ogni funzione del programma ha un proprio **stack frame**, posizionato tra il base pointer e lo stack pointer, nel quale vengono salvati:
- le variabili locali
- lo stato della macchina: l'indirizzo di ritorno, ovvero il vecchio base pointer
- i parametri della chiamata

###### Esempio
```c
int function_B(int a, int b){
	int x, y;
	x = a * a;
	y = b * b;
	return (x + y);
}

int function_A(int p, int q){
	int c;
	c = function_B(p,q);
	return c;
}

int main(int argc, char** argv, char** envp){
	int ret;
	ret = function_A(1,2);
	return ret;
}
```

![[Pasted image 20230903153426.png]]

Codice assemblativo di B:
```assembly
push 	ebp
mov 	ebp,esp
sub 	esp,0x10
mov 	eax,DWORD PTR [ebp+0x8]
imul 	eax,DWORD PTR [ebp+0x8]
mov 	DWORD PTR [ebp-0x4],eax
mov 	eax,DWORD PTR [ebp+0xc]
imul 	eax,DWORD PTR [ebp+0xc]
mov 	DWORD PTR [ebp-0x8],eax
mov 	eax,DWORD PTR [ebp-0x8]
mov 	edx,DWORD PTR [ebp-0x4]
add 	eax,edx
leave
ret
```
##### Preambolo e prologo di una funzione
Ogni funzione inizia con un **preambolo**:
```assembly
push 	ebp      ; Salvo sullo stack il valore del vecchio base pointer EBP
mov 	ebp,esp  ; Sostituisco il vecchio base pointer con lo stack pointer per creare lo stack frame
sub 	esp,0x10 ; Faccio crescere lo stack di 16 byte, o 4 celle
```
e termina con un **prologo**:
```assembly
mov 	esp,ebp ; ripristino il vecchio base pointer
pop     ebp
sub 	ret
```

#### Buffer overflow
Un **buffer overlow** é un **bug software** che si verifica quando dei dati vengono copiati in un’area di memoria ed eccedono lo spazio riservato per quella variabile.

Presentiamo quí sotto un esempio:
```c
#include <stdio.h>
#include <string.h>

int main(int argc, char** argv) {
	int cookie;
	char buf[80];


	printf("buf: %08x cookie: %08x\n", &buf, &cookie);
	gets(buf);
	if (cookie == 0x41424344)
  		printf("you win!\n");
}
```
possiamo notare che per prendere un input, arbitrario, dell'utente viene utilizzata la funzione `gets`, che presenta la seguente dicitura nella sua manpage:
![[Pasted image 20230903160536.png]]

Si tratta quindi una vulnerabilitá sfruttabile da un attaccante. 

Analizziamo l'esecuzione del programma:
eseguendolo con input 1234 otteniamo
```bash
~ ./a.out
buf: 244cc510 cookie: 244cc56c
1234
```
senza aver triggerato la condizione. Peró fornendo un input piú lungo del buffer siamo in grado di sovrascrivere lo stack e di conseguenza il valore del cookie:
```c
~ ./a.out <<<  python3 -c "print('A'*80+'DCBA')"
buf: bf8279a0 cookie: bf8279fc
you win!
```
Questo esempio é molto semplice, ma i buffer overflow possono essere utilizzati per:
- **eseguire codice arbitrario**, modificando l'instruction pointer
- **Sovrascrivere interi frame**

##### Contromisure
Negli anni sono stati presentati delle contromisure, piú o meno efficaci:
- **Canarino**: un valore noto scritto sullo stack tra il buffer e levariabili locali per rilevare i buffer overflow. Esso viene inserito durante la compilazione con l'idea che, in caso di bof, sarebbe il primo valore ad essere sovrascritto, e in caso di alterazione, l'esecuzione verrebbe bloccata.
- **Address Space Layout Randomization (ASLR)**: un meccanismo di sicurezza che randomizza gli indirizzi di memoria usati dal sistema operativo quando alloca la memoria del programma. in questa maniera evita che l'intera memoria sia contigua, rendendo piú difficili gli attacchi.
- Separare lo spazio di Memoria del codice dai dati
- stack non eseguibile