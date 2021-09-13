# Introduzione 
Un calcolatore digitale è una macchina che può risolvere problemi eseguendo le istruzioni che le vengono assegnate. La serie di istruzioni che descrive come portare a termine un dato compito prende il nome di *programma*.

I circuiti elettronici di un qualsiasi computer possono riconoscere ed eseguire solo un numero limitato di istruzioni (come la somma di due numeri, controllare se un numero vale zero, copiare una porzione di dati da una parte di memoria all'altra). Tali istruzioni primitive formano un linguaggio, chiamato **linguaggio macchina**, attraverso il quale è possibile comunicare con il computer.

## Approccio strutturale
L'**approccio strutturale** è nato per consentire a chi progetta un calcolatore di poter realizzare un linguaggio macchina più agevole e sistemare l'organizzazione dell'architettura del computer: consiste nel *strutturare i computer come una serie di livelli di astrazione, ciascuno dei quali è costruito sulla base di quello soprastante*.

Esiste una grand differenza tra ciò che è adatto agli utenti e ciò che lo è per il computer. Tale problema si risolve mediante la definizione di un nuovo insieme di istruzioni (chiamiamolo **L1**) che sia più comodo rispetto alle istruzioni in macchina predefinite (chiamiamole **L0**). L1 viene anch'esso considerato un lunguaggio, e per eseguirlo non ci resta che *tradurre* o *intepretare*.
- Traduzione (o **compilazione**):
consiste, nel sostituire in una fase iniziale, ogni istruzione di L1 con un'equivalente sequenza di L0;
- **Interpretazione**:
consiste nello scrivere un programma in L0 che accetta come dati in ingresso programmi nel nuovo linguaggio L1; tale programma (quello di L1), chiamato *interprete*, esegue i dati di L1 esaminando un'istruzione alla volta e sostituendola direttamente con l'equivalente sequenza di istruzioni del linguaggio macchina.
##### Compilazione VS Interpretazione 
|Voce|Compilatore|Interprete|
|:----:|:---:|:----:|
|Tempo di traduzione del codice sorgente|Prima dell'esecuzione del software|Durante l'esecuzione del software|
|Procedura di traduzione|Codice intero|Linea per linea|
|Visualizzazione degli errori del codice|Dopo la compilazione completa|Dopo ogni linea|
|Velocità di traduzione|Bassa|Alta|
|Efficienza di traduzione|Alta|Bassa|
|Spese di sviluppo|Alte|Basse|
|Linguaggi tipici|C, C++, Pascal|PHP, Perl, Python, Ruby, BASIC|

Adesso diamo un'occhiata ai vantaggi e svantaggi nell'utilizzo di questi programmi:

||Vantaggi|Svantaggi|
|:----:|:----:|:----:|
|**Interprete**|Processo di sviluppo semplice (specialmente nel debug)|Processo di traduzione inefficace e bassa velocità di esecuzione|
|**Compilatore**|Trasmette al processore il linguaggio macchina completo pronto all'uso ed eseguibile|Eventuali modifiche al codice richiedono una nuona traduzione (gestione degli errori, estensione del sotware, ecc.)|

&nbsp
#### Macchine virtuali (o livelli)
Invece di ragionare in termini di compilazione e interpretazione, spesso è più semplice immaginare l'esistenza di un ipotetico computer o **macchina virtuale**, il cui linguaggio macchina sia L1. Chiamiamo questa macchina virtuale M1 (e M0 la macchina che corrisponde al linguaggio L0). Per agevolare la traduzione o l'interpretazione, i linguaggi L0 e L1 devono essere simili tra di loro. A man a mano creeremo quindi nuovi set di istruzioni che si avvicineranno al linguaggio dell'utente. Ci ritroveremo con una serie di linguaggi L0, L1, L2, ..., LN che avrà come base il linguaggio precedente.
Un computer che usa tale tecnica può essere immaginato come una serie di **strati** o **livelli** disposti l'uno sopra l'altro. Il più basso è il più semplice, mentre il più alto è il più sofisticato.

Tra i linguaggi e le macchine virtuali sussiste un'importante relazione:
- una macchina ha un proprio linguaggio macchina, costituito da tutte le istruzione che è in grado di eseguire (di fatto, la macchina *definisce* il linguaggio);
- un linguaggio definisce una macchina virtuale, ovvero è in grado di eseguire tutti i programmi scritti in quel linguaggio.

# Livelli di astrazione
I computer sono progettati su una serie di livelli, o rachitetture, cialcuno costruito su quello precedente.
![[livelli.PNG]]
## Livello 0
Il livello **logico digitale** é il piú basso ed é copmposto da **porte**(*gate*) costituite da componenti analigici come transistors. Ogni gate puó essere modellato come un dispositivo digitale, dotato di input digitali binari e calcola un output, anche questo in binario.

## Livello 1
Il livello di microarchitettura é composto da un gruppo di registri e un circuito chiamato **ALU**(*Arithmetic Logic Unito*), capace di compiere operazioni aritmetiche semplici.

I registri sono connessi all'ALU per formare un **Data Path**(*percorso dati*) attraverso il quale i dati passano per essere depositati nei registri, solitamente dopo essere stati elaborati dalla ALU.
Solitamente questo livello é controlalto da un microprogramma ma in alcune architetture puó essere controllato direttamente dall'hardware.

## Livello 2
Il livello **ISA**(*Istruction Set Architecture*) é il livello di programmazione piú basso, composto da **singole istruzioni** eseguite dall'elaboratore.

Ogni architettura ha il proprio set di istruzione, solitamente proprietario, che viene **interpretato** dal microprogramma o dai circuiti logici.

## Livello 3
Il livello **macchina del sistema operativo** presenta istruzioni identiche a quelle del livello sottostante, quindi alcune istruzioni di questo livello vengono eseguite dal sistema operativo ed altre direttamente dal microprogramma.
## Livello 4
Il livello del **linguaggio microassemblativo** rappresenta il forma simbolica i linguaggi sottotstanti, in quanto i primi 3 non sono pensati per lo sviluppatore medio.

I linguaggio microassemblativo viene prima tradotto nel linguaggio di destinazione(del livello 1,2 o 3) e successivamente interpretato dal **microassemblatore**, una macchina reale o virtuale.
## Livello 5
Questo livello é costituito dai **linguaggi ad alto livello**, definiti per essere impiegati nella programmazione delle applicazioni.

I linguaggi di questo livello sono solitamente tradotti(*Compilati*) nei linguaggi dei livelli 3 o 4.

### Rappresentazione dei numeri floating point -IEEE 754

Il metodo standard per rappresentare i numeri floating point in binario è mediante la rappresentazione IEEE 754. 
Ci sono due rappresentazioni:
- Precisione singola (32 bit)
![[Pasted image 20210618135550.png]]
&nbsp

- Precisione doppia (64 bit)
&nbsp&nbsp&nbsp1 bit  per segno; 11 bit per l'esponente mediante  &nbsp&nbsprappresentazione in eccesso 1023; 52 bit per la mantissa

Numero normalizzato: il primo bit della mantissa, pari a 1, viene omesso per convenienza. 
Nei nostri esercizi dovremo inserire la virgola a destra del primo 1 leggendo da sinistra. 


Nel sistema IEEE 754 risparmiamo un bit imponendo l'utilizzo della forma normalizzata. 
Intervallo esponente in precisione singola (0 , 255)
Intervallo esponente in precisione doppia (0 , 1024)


Casi Particolari: 
-	Zero
	Esponente = 0 	Mantissa = 0
-	Infinito
	Esponente = 255 Mantissa = 0
-	NaN
	Esponente = 255 Mantissa $\neq$ 0
	
<u> Nota </u>: nei casi in cui ci venga fornita una precisinoe "inventata", ricorda che:
-	il bit di segno è sempre 1
-	l'esponente viene fatto in eccesso, l' eccesso si calcola facendo: $2^{n-1}-1$  (dove *n* è il numero di bit)
- la mantissa sono i bit rimanenenti sempre in forma normalizzata

# Algebra Booleana
## Leggi dell'algebra di boole

![Algebra%20Booleana%20a4b3bb1a697046e9a2dd21ea6fec2378/Untitled.png](Riassunti/02-Algebra%20Booleana/PNGs/Untitled.png)

- Due operatori costanti **0** e **1**
- Operatore unario **NOT**
    - $\bar{\mathrm{A}}$: "not" $\mathrm{A} \space(\neg\mathrm{A})$
- Operatori binari **AND** e **OR**:
    - AB: A "and" B
    - $\mathrm A+\mathrm B$ : $\mathrm A$ "or" $\mathrm B$
- Una qualunque combinazione di variabili o costanti boolenae legate tra loro dagli **operatori fondamentali** è un'**espressione logica**.
- In assenza di parentesi **AND** ha precedenza su **OR**.

## Funzioni booleane

Una **funzione booleana** di $n$ varabili $x_1, x_2,..., x_n$ è una relazione che associa un valore booleano a ciascuna delle $2^n$ configurazioni possibili delle $n$ variabili:

$$y=f(x_1,x_2,...,x_n)$$

Una funzione booleana può essere espressa in varie forme:

- Tabelle di verità
- Formule agebriche
- Mappe di Karnaugh
- Binary Decision Diagrams (BDDS)

### Proprietà delle funzioni booleane

**Tabelle di verità:**

Descrivono completamente il valore di una funzione Booleana attraverso tutte le combinazioni di input. $n$ input corrispondono a $2^n$ combinazioni (righe).

**Finità:**

È finito l'insieme delle funzioni Booleane di $n$ input:

$$2^{2^{n}}$$

funzioni (es. se $n=2$ allora esistono $16$ funzioni diverse)

**Forma canonica**

Righe ordinate per valori crescenti degli ingressi interpretando i valori delle variabili di ingresso come cifre di una codifica binaria.

![Algebra%20Booleana%20a4b3bb1a697046e9a2dd21ea6fec2378/tabellediverit.png](tabellediverit.png)

## Forme canoniche

### **Formla normale disgiuntiva (FND)**

- Sommatoria di termini ciascuno dei quali è una produttoria di **letterali**  costituiti da nomi di variabili di ingresso o da negazioni dei nomi di variabili di ingresso
- È **minimale** quando, applicando le proprietà algebriche di equivalenza non è possibile ottenere una FND equivalente contenente un numero di letterali inferiore

### **Formula nominale congiuntiva (FNC)**

- Concetto "duale" del precendente, ossia è una produttoria di termini ciascuno dei quali è una sommatoria di **letterali** costituiti da nomi di variabili di ingresso o da negazioni di nomi di variabili di ingresso

## Da formula algebrica a tabelle di verità

1. Elencare tutte le possibili configurazioni delle $n$ variabili di ingresso
2. Per ogni configurazione, valutare i valori di uscita delle funzioni elementari **NOT**, **AND** e **OR** che compongono l'espressione
3. Assumendo che l'espressione iniziale sia una **FND**, l'uscita della funzione **OR** rappresenta il valore da inserire nella corrispondente riga della tabella di verità

$$\mathrm{Tabella\space di\space verità} \longleftrightarrow \mathrm{Formula\space algebrica}$$

## Da tabella di verità a formula algebrica

![Algebra%20Booleana%20a4b3bb1a697046e9a2dd21ea6fec2378/tavole_di_vertit.png](tavole_di_vertit.png)

# Equivalenza di circuiti

Due funzioni sono equivalenti se e solo se hanno lo stesso valore di output per tutti i possibili input.

Di solito un progettista parte da una formula e in seguito applicando le leggi dell'algebra di Boole e alcune identità ([Leggi dell'algebra di boole]()) cerca di semplificarla.

# Circuiti integrati

Le porte logiche non sono prodotte o vendute inidividualmente ma in unità chiamate **circuiti integrati**.

Esistono 3 supporti differenti per i chip integrati:

![Circuiti%20integrati%20941c2ece2d764b34b2a581e7f608774d/Pasted_image_20210411171026.png](Pasted_image_20210411171026.png)

DIP

![Circuiti%20integrati%20941c2ece2d764b34b2a581e7f608774d/Pasted_image_20210411170924.png](Pasted_image_20210411170924.png)

PGA

![Circuiti%20integrati%20941c2ece2d764b34b2a581e7f608774d/Pasted_image_20210411171108.png](Pasted_image_20210411171108.png)

LGA

Per noi le porte logiche considerate sono ideali, quindi l'aoutput appare nello stesso momento in cui applichiamo il voltaggio. Il realtà i chip hanno un ritardo temporale finito, chiamato **ritardo della porta**.

# Reti combinatorie

Molte applicazioni richiedono un circuito, chiamato **rete combinatoria**, con più input e più output, in cui gli output sono unicamente determinati dagli input.

Una rete combinatoria è una **rete logica** che ha  $n$ ingressi binari $x_1,...,x_n$ ed $m$ uscite binarie $z_1,...,z_m$. A ciascuna combinazione dei valori degli ingressi corrisponde una ed una sola ombinazione dei valori delle uscite.

Per descrivere le proprietà e la struttura interna delle reti combinatorie si usa l'[[Algebra Booleana]].

## Schema logico

Lo chema logico viene fatto usando i *componenti hardware elementari*, detti anche porte logiche, ***AND***, ***OR***, ***NOT***. I simboli per tali porte sono:

![Circuiti%20integrati%20941c2ece2d764b34b2a581e7f608774d/Pasted_image_20210408082007.png](Pasted_image_20210408082007.png)

Partendo da un'espressione logica in forma SP 

$$f=ab+\overline{ac}$$

si arriva alla corrispondente espressione logica

![Circuiti%20integrati%20941c2ece2d764b34b2a581e7f608774d/Pasted_image_20210408082332.png](Pasted_image_20210408082332.png)

# Circuiti Combinatori
Sono dei circuiti con piú input ed output, dove le uscite sono unicamente determinate dagli ingressi.
Possono fare eccezione i circuiti contenenti elementi di memoria.

## Decoder

Chiamato anche decodificatore, é un circuito che prende in input __n__ bit e lo usa per impostare ad 1 una tra le $2^n$ linee di output.
Viene solitamente utilizzato per __l'indirizzamento__ della memoria, quindi per selezionare i banchi di memoria su cui andare a scrivere.

La corretta rappresentazione del gate(ingresso) in $base_2$ ci permette inoltre di comprendere a quale linea di uscita corrisponderá.

Ogni segnale di ingresso presenta anche la sua controparte negata.

![[Decoder.png]]

Livelli logici: 1
## Multiplexer
É un circuito con $2^n$ input, __un solo__ valore di output e n bit che controllano l'instradamento.

I bit di controllo permettono di selezionare quale input verrá instradato verso l'output, e poiché questi avranno valore 1, questo permette di 
portare il valore di input come output.

![[multiplexer.png]]
Livelli logici: 2
## Demultiplexer

É l'opposto del multiplexer, ovvero é un circuito che dato un singolo segnale di input, invia il segnale di output alle $2^n$ possibili segnali di output, controllati dagli n bit di controllo che ne vincolano l'instradamento.

Come nel multiplexer, l'output sará uguale all'input.
![[Pasted image 20210406110835.png]]
Livelli logici:1
## Comparatore

É un circuito in grado di confrontare  di srringhe di **n bit**.

Si basa sulle porte logiche **xor**, confrontando ogni coppia di bit e producendo 0 se sono uguali.
Se tutte le porte producono me risultato 0, significa che tutti i bit sono uguali e quindi il **nor** invertirá il risultato, ponendo in output 1.

![[Pasted image 20210617153625.png]]
Livelli logici:3
## Shifter 

É uno shifter é un circuito in grado di prendere n bit in input e sportare il tutto di una posizione a sinistra, se il segnale C é 0, ponendo il bit piú significativo a 0, se é ad uno viene invece spostata a destra, col il bitr meno significativo che viene posto sempre a 0.

![[Pasted image 20210618164900.png]]

# Circuiti Aritmetici

## Half Adder
Un **half hadder**(o *semisommatore*) é un circuito capace di calcolare il bit della somma con eventuale riporto, secondo la seguenter tabella:

A | B | Somma | Riporto
---|---|---|---
0|0|0|0
0|1|1|0
1|0|1|0
1|1|0|1
![[Pasted image 20210618140820.png]]

É importante ricordare che un half hadder non tiene conto del riporto precedente(**Carry in**).
## Full Adder
Un** full hadder**(o *sommatore*) é un circuito costituito da due half hadder e permette di tenere con del riporto in ingreso(Carry in).
La somma e il riporto di valutano secondo la seguente tabella:

A|B|Carry in|Somma|Carry out
---|---|----|---|---|
0|0|0|0|0
0|0|1|1|0
0|1|0|1|0
0|1|1|0|1
1|0|0|1|0
1|0|1|0|1
1|1|0|0|1
1|1|1|1|1

![[Pasted image 20210618141846.png]]

É possibile mettere insieme piú full hadder per comporre un **sommatorare a propagazione di riporto** a n bit, ma il riporto in ingresso del primo sommatore avrá valore 0.

# Memoria Principale
la **memoria** è quella parte del calcolatore in cui sono depositati i programmi e dati

- ## Bit
E' l'unità base della memoria; può avere valore 1 / 0 

- ## Inidirizzi di memoria
  - Sono costruite da un certo numero di **celle**, ciascuna delle quali può memorizzare informazioni
  - Ogni cella ha un **indirizzo** utile al programma per riferirsi ad una cella specifica
  Per ogni *n* celle, gli indirizzi vanno da 0 a *n-1* 
  - Tutte le celle contengono lo stesso numero di Bit. -> Se sono costituite da *k* bit, può contenere $2^k$ combinazioni di bit.
  - I calolatori che sfruttano un sistema di numerico binario, se hanno indirizzi da *m* bit, posso avere al massimo $2^m$ celle indirizzabili
  - Il numero di bit nell'indirizzo (che determina il max n. di celle) è indipendente dal numero di bit per cella.
       - sia una memoria con $2^{12}$ celle da 8bit che una con $2^{12}$ celle da 64bit richiedono indirizzi da 12 bit
      
	 
  - Generalmente si sfruttano celle a 8 bit dette **Byte**, raggruppate in **Word**, che possono essere da 4 Byte (32 bit) o 8 Byte (64 bit)
      - Le parole sono inportanti, in quanto le istruzioni generalmente operano su intere parole (una macchina a 32 bit avrà registri a 32bit per manipolare parole da 32bit --> stesso discorso per le 64bit)
 - ## Ordinamento dei Byte | Endianness
	 - I Byte posso essere numerati da Sx a Dx oppure da Dx a Sx

Big-endian           

| 0 | 1 | 2 | 3 |        
|---|---|---|---|    
| 4 | 5 | 6 | 7 |        
| 8 | 9 | 10| 11|
| 12| 13| 14| 15|
<-->Byte
<---------->  Parola 32 Bit

Little-endian           

| 3 | 2 | 1 | 0 |         
|---|---|---|---|    
| 7 | 6 | 5 | 4 |        
| 11 | 10 | 9| 8|
| 15 | 14 |13|12|
 - Esempio: il numero 6 è rappresentanto in entrambi i casi con i bit 110 nei 3 bit più a destra (meno significativi) e 0 negli altri 29.
 Nel Big-endian i bit 110 si troveranno nel byte 3/7/11/15, mentre nel little-endian nel byte 0/4/8/12
 - Memorizzando tipi diversi dagli interi (char, String ...) i sistemi rimangono coerenti internamente ma si creano problemi di comunicazione se le macchine non sfruttano lo steso tipo di memorizzazione
	 - non essite un metodo unico di conversione, quinidi si è costretti a sfruttare un "intestazione" per inidicare il tipo del dato e quindi procedere con la corretta conversione --> grande scomodità
- ## Memoria Cache
  - Le CPU sono sempre state più veloci delle memorie
	Cio crea uno squilibrio che porta la cpu a dover aspettare molti cicli prima di ricevere una parola creando uno "stallo software" dopo ogni LOAD (rifacendosi alla IJVM) da riempire con istruzioni fasulle dette NOP

     - Per tamponare questo problema si abbina una memoria più spaziosa e lenta ad una piccola ma molto veloce (posizionata nel processore) detta **Cache**
     - L'idea di base e memorizzare le parole più utilizzate nella Cache così che la Cpu necessiti di effettuare meno chiamate verso la memoria lenta.
     Ciò riduce nettamente il tempo medio di lettura di una parola.
	     - L'efficenza dipedende dalla capacità di salvare nella cache le parole necessarie prima che vengano richieste dalla cpu
	     - Per fare ciò, ci si rifà al **Principio di Località** cioè l'osservazione secondo cui le chiamate fatte in un ristretto intervallo di tempo tendono a rifarsi ad una piccola frazzione della memoria totale.
	     - Generalmente nel momento in cui una parola viene referenziata, viene copiata nella cache insieme ad alcune delle parole nelle vicinanze. 
	        - Così se la parola $X$ serve $k$ volte verrà letta 1 sola volta lentamente, ed altre k-1 volte velocemente
	      
		  - *Tempo di accesso medio* = $c + (1-h)m$
		      - Se $h \to 1$, tutte le richieste sono soddisfatte dalla cache.
		      Se $h \to 0$, bisogna rifarsi ogni volta alla emoria più lenta
			  - $c$ è il tempo necessario per controllare inizialmente la cache
			  - $m$ tempo per fare riferimento alla memoria
	     
	   - Sia Cache che memoria centrale sono divise in blocchi di dimensioni fisse, così da sfruttare al meglio il Principio di località -> se la lettura della cache va a vuoto, si riscrive l'intero blocco
	     - all'interno della Cache prendono il nome di **Linee di Cache**  
	 
	 - I problemi principali nello sviluppo delle cache sono:
	   - Costi crescenti con le dimensioni
	   - Dimensioni delle linee
	   - Tener traccia di cosa si memorizza e dove
	   - Decidere se tenere dati e istruzioni salvati in una solo cache o più
	   	- Sfruttando una **Cache unificata** si semplifica il tutto, ma ad oggi tutte le cpu sfruttano **Cache specializzate** in una struttura chiamata **Architettura Harvard**

### Circuiti Sequenziali
Sono circuiti che mantegono uno stato interno e possono essere usati come memorie memorizzando dei bit.
### Latch - SR (Set - Reset)
Un circuito utilizzato come memoria:
-	Quando il valore del Set è a 1, lo stato del latch viene memorizzato a 1
-	Quando R (reset) è a 1, il latch viene settato a 0
Il circuito "ricorda" l'ultimo valore settato (se Set o Reset) e di conseguenza è possibile mantenere uno stato della memoria
-	Ha due output Q e <span style="text-decoration:overline">Q</span> che sono determinati dai valori di input e dallo stato interno
-	Se sia S che R sono a 1, lo stato risulta instabile

![[Pasted image 20210619112613.png]]
### Latch - SR Temporizzato
Serve per impedire al latch di cambiare stato in momenti indesiderati ma non risolve il problema di instabilità se S = R = 1.
Un latch-sr con l'aggiunta di un trigger (clock) che preserva lo stato del latch finchè l'input è 0.
Le 2 porte AND collegate al trigger (TS , TR) sono 0 finchè T è 0

![[Pasted image 20210619113058.png]]
### Latch - D 
Un latch-sr temporizzato cocn un solo ingresso D e una porta NOT collegata al trigger (clock) che impedisce l'ambiguità.
Questo circuito risolve i problemi di indeterminazione in cui S e R potrebbero essere entrambi a 1.
![[Pasted image 20210618174525.png]]

### Flip - Flop
È un circuito a commutazione sul  fronte,  in cui vengono registrate le variazioni di segnale non sullo stato 0/1 del segnale ma sul fronte di discesa/salita, grazie al ritardo temporale causato dalla porta NOT.
![[Pasted image 20210619105015.png]]
![[Pasted image 20210619105030.png]]

# Reti sequenziali

## Combinatori vs Sequenziali

I circuiti **combinatori** sono in grado di calcolare funzioni che dipendono solo da dati di input mentre i circruiti **sequenziali** sono invece in frado di calcolare funzioni che dipendono anche da uno **stato interno**, quindi dipendono anche da informazioni *memorizzate in elementi di memoria interni*. La funzione calcolata dal circuito in un dato istante *dipende dalla sequenza temporale dei valori storci di input*.

## Macchine a stati finiti

### Macchina o Automa:

- dispositivo automatico in grado di interagire con l'ambiene esterno
- a fronte di uno stimolo in ingresso (input), esibisce un comportamento in uscita (output) che dipende anche da informazioni memorizzate in elementi interni (stati).

Una **macchina a stati finiti (FSM)**, è vista come una scatola "nera", che possiamo descrivere mostrando cosa succede ad ogni passo:

- leggere un simbolo in ingresso ( insieme finito $A$ )
- produce un simbolo in uscita ( insieme finito $B$ )
- cambia il proprio stato interno ( iniseme finito $A$ )

![Reti%20sequenziali%207ecff385053844b4add0780e4e6a39c8/Pasted_image_20210408084933.png](Pasted_image_20210408084933.png)

## Macchina di Mealy

È un **automa a stati finiti** i cui valori di uscita sono determinati dalo stato attuale e dall'ingresso corrente, a differenza della [Macchina di Moore](),  he invece lavora solo in funzione dello stato corrente.

![https://i.stack.imgur.com/Gho6d.png](https://i.stack.imgur.com/Gho6d.png)

### Definizione formale

Una macchina di Mealy è una [sestupla](https://it.wikipedia.org/wiki/Ennupla), { $S,S_0,Σ,Λ,T,G$ }, costituita da:

- un insieme finito di stati $S$
- uno stato iniziale $S_0$, che è un elemento di $S$
- un insieme finito chiamato alfabeto degli ingressi $Σ$
- un insieme finito chiamato alfabeto delle uscite $Λ$
- una funzione di transizione $T: S × Σ → S$
- una funzione uscita $G:S × Σ → Λ$

## Macchina di Moore

È un **automa a stati finiti** in cui le uscite sono determinate in funzione dei soli stati correnti e non anche dagli stati d'ingresso, come accade invece nella [Macchina di Mealy]().

![https://upload.wikimedia.org/wikipedia/commons/b/b9/Moore_Machine.PNG](https://upload.wikimedia.org/wikipedia/commons/b/b9/Moore_Machine.PNG)

### Definizione formale

Una macchina di Moore può essere definita come una [sestupla](https://it.wikipedia.org/wiki/Ennupla) ( $S , S_0 , Σ , Λ , T , G$ ) costituita da:

- un insieme finito di stati ( $S$ )
- uno stato iniziale $S_0$ che è un elemento di $S$
- un insieme finito chiamato alfabeto degli ingressi $Σ$
- un insieme finito chiamato alfabeto delle uscite $Λ$
- una funzione di transizione $T : S × Σ → S$ che mappa uno stato ed un ingresso nello stato successivo
- una funzione di trasformazione, o di output, $G : S → Λ$ che mappa ciascun stato nell'alfabeto delle uscite

# IJVM

## Definizione
L'IJVM é una macroarchichettura composta da un'insime di istruzione (ISA -> Instruction set architecture)

Si basa sull'utilizzo di una pila denominata "**Stack**" per la memorizzazione delle variabili, dove non vengono stabiliti indirizzi assoluti, alle quali verrá invece assegnato un offset. Questo viene inoltre utilizzato per effettuare le operazioni aritmetiche.

Consiste in un array di 4GB, che non utilizza degli indirizzi di memoria assoluti direttamente visibili, ma degli indirizzi impliciti, quindi é possibile accedere alla memoria solo attraverso l'impego di **puntatori**.

Sono quindi sempre definite le seguenti porzioni di codice:
- Una **Porzione costante di memoria** che viene caricata dalla memoria quando il programma viene eseguito e non viene piú modificata in seguito.

- Un **blocco delle variabili costanti**, dove allo care le variabili locali dopo la chiamata di un metodo . La variabile chiamante del metodo é memoriazzata in cima, ma lo stack degli operandi é separato.
- Lo **stack degli operandi**, che non puó superare una cerda dimensione, ed é allocato subiso sopra il blocco dell variuabili locali.
- **L'area dei metodi**, chiamato anche Program Counter.

![[Pasted image 20210418181359.png]]

```java
.constant
objectref 0xCAFE 
.end-constant

.main

.end-main

.mathod 

.end-method
```
&nbsp
&nbsp

&nbsp
&nbsp
&nbsp
## Istruzioni IJVM 

Hex | Nome | Significato
---|---|---|
0x10|BIPUSH *Byte*| Scrive un byte in cima allo stack
0x59|DUP|Duplica la parola in cima allo stack
0xA7|GOTO *offset*| Diramazione incondizionata
0x60|IADD|Somma le 2 parole in cima allo stack
0x7E|IAND|Sostituisce le parole in cima allo stack con il loro AND
0x99|IFEQ *offset*| (IF EQUALS (0)) Esegue una diramazione se la parola in cima allo stack é zero
0x9B|IFLT *offset*|Esegue una diramazione se la parola in cima allo stack é negativa
0x9F|IF_ICMPEQ *offset*| (COMPARE EQUALS) Effettua una diramazione se le 2 parole in cima allo stack sono uguali
0x84|IINC *var* *const*| Aggiunge una costante ad una variabile locale
0x15|ILOAD *var*| Scrive una variabile locale in cima allo stack
0xB6|INVOKEVIRTUAL *met*| invoca un metodo
0x80|IOR|Sostituisce le 2 parole in cima allo stack con il loro OR
0xAC|IRETURN|Termina il metodo restituendo un valore intero
0x36|ISTORE *var*|Memorizza la variabile in cima allostack come una variabile locale
0x64|ISUB|Sostituisce le 2 parole in cima llo stack con la loro differenza
0x13|LDC_W *index*| Scrive sullo stack una costante proveniente da una porzione di memoria
0x00|NOP|Non fa niente
0x57|POP|Rimuove la cima dello stack
0x5F|SWAP|Scambia le 2 parole in cima allo stack
0xC4|WIDE|IStruzione prefisso:L'istruzione successiva ha un indice di 16 bit

# Bus

## In generale

![Bus%205bfee53a6286489fa639c2ad052188b6/Untitled.png](Riassunti/Bus/PNGs/Untitled.png)

Il bus è l'insieme di linee elettriche che collegano i moduli di un elaboratore 

In genere viene rappresentato mediante una freccia larga ad indicare che le linee in esso contenute hanno funzionalità distinte (controllo, indirizzo, dati)

Affinché i moduli connessi dal bus siano in grado di comunicare è necessario che essi interagiscano con il bus secondo un insieme di regole ben definite chiamate **protocollo**

Le linee del bus possono essere di vari tipi:

- **Linee di dati $\Longrightarrow$** è detto *data bus.* Il numero di linee (larghezza del data bus) determina il numero di bit che possono essere trasmessi alla volta
- **Linee di indirizzo $\Longrightarrow$** permettono di individuare la sorgente/destinazione dei dati trasmessi sul data bus
- **Linee di controllo $\Longrightarrow$** controllano l'accesso e l'utilizzo delle linee dati e di indirizzo

## Connessioni di una CPU

- **Indirizzo:** *n* piedini corrispondono a $2^n$ locazioni di memoria indirizzabili
- **Dati:** *n* piedini permettono di leggere/scrivere una parola di *n* bit con una sola operazione
- **Controllo:** regolano il flusso

![Bus%205bfee53a6286489fa639c2ad052188b6/Untitled%201.png](Riassunti/Bus/PNGs/Untitled%201.png)

## Dispositivi attivi e passivi

I dispositivi hanno connesioni diverse a seconda della loro natura e si dividono in:

- **Attivi** (**master**): possono decidere di iniziare un trasferimento, in genere sono collegati al bus per mezzo di un particolare chip detto *bus driver*
- **Passivi** (**slave**): rimangono in attesa di richieste, in genere sono collegati per mezzo di un chip detto *bus receiver*
- **La via di mezzo**: i dispositivi che sono sia slave che master sono collegati per mezzo di un chip chiamato *bus transceiver*

## Progettazione di un bus

I problemi principali della progettazione di un bus riguardano

- **[Larghezza** del bus](): numero di linee
- **Arbitraggio**: come scegliere tra due dispositivi che vogliono diventare contemporaneamente arbitri dello stesso bus
- **Funzionamento** del bus: come avviene il trasferimento dei bit

### Larghezza del bus

![Bus%205bfee53a6286489fa639c2ad052188b6/Untitled%202.png](Riassunti/Bus/PNGs/Untitled%202.png)

- Il numero delle linee utilizzate per trasferire gli indirizzi determinano la
massima quantità della memoria indirizzabile
- Il numero delle linee utilizzate per il trasferimento di dati determinano la
quantità di informazioni che è possibile trasferire con una singola
operazione

![Bus%205bfee53a6286489fa639c2ad052188b6/Untitled%203.png](Riassunti/Bus/PNGs/Untitled%203.png)

- Bus “larghi” sono più costosi di quelli stretti ma offrono una banda più larga
e quindi maggiore velocità di trasferimento
- Per ovviare ai problemi dati da bus molto larghi talvolta si opta per un multiplexed bus: le linee utilizzate per il trasferimento dei dati e degli indirizzi sono le stesse; prima si trasmettono gli indirizzi e poi i dati. Ovviamente il bus multiplexato è più lento.

## Bus clocking

I bus si possono dividere in due categorie ben distinte:

- **[Bus sincroni]()**: sono clockati e tutte le operazioni sul bus richiedono un numero intero di cicli
- **Bus asincroni**: non hanno un clock principale, i cicli del bus possono essere di una lunghezza arbitraria e non devono essere uguali per tutti i dispositivi

## Bus sincrono

![Bus%205bfee53a6286489fa639c2ad052188b6/Untitled%204.png](Riassunti/Bus/PNGs/Untitled%204.png)

![Bus%205bfee53a6286489fa639c2ad052188b6/Untitled%205.png](Riassunti/Bus/PNGs/Untitled%205.png)

![Bus%205bfee53a6286489fa639c2ad052188b6/Untitled%206.png](Riassunti/Bus/PNGs/Untitled%206.png)

## Bus asincrono

![Bus%205bfee53a6286489fa639c2ad052188b6/Untitled%207.png](Riassunti/Bus/PNGs/Untitled%207.png)

![Bus%205bfee53a6286489fa639c2ad052188b6/Untitled%208.png](Riassunti/Bus/PNGs/Untitled%208.png)

![Bus%205bfee53a6286489fa639c2ad052188b6/Untitled%209.png](Riassunti/Bus/PNGs/Untitled%209.png)

![Bus%205bfee53a6286489fa639c2ad052188b6/Untitled%2010.png](Riassunti/Bus/PNGs/Untitled%2010.png)

## Sincrono vs Asincrono

![Bus%205bfee53a6286489fa639c2ad052188b6/Untitled%2011.png](Riassunti/Bus/PNGs/Untitled%2011.png)

![Bus%205bfee53a6286489fa639c2ad052188b6/Untitled%2012.png](Riassunti/Bus/PNGs/Untitled%2012.png)

## Arbitraggio del bus

Se più di un dispositivo richiede l'utilizzo del bus contemporaneamente è necessario un meccanismo di **arbitraggio del bus** e il **meccanismo del grant**, esistono due tipi di arbitraggio:

- arbitraggio centralizzato
- arbitraggio decentralizzato

### Arbitraggio centralizzato

![Bus%205bfee53a6286489fa639c2ad052188b6/Untitled%2013.png](Riassunti/Bus/PNGs/Untitled%2013.png)

![Bus%205bfee53a6286489fa639c2ad052188b6/Untitled%2014.png](Riassunti/Bus/PNGs/Untitled%2014.png)

## Arbitraggio decentralizzato

![Bus%205bfee53a6286489fa639c2ad052188b6/Untitled%2015.png](Riassunti/Bus/PNGs/Untitled%2015.png)

# Mic-1
Al di sopra del livello logico digitale si trova il livello di microarchitettura, il quale compito consiste nell'**implementare il livello ISA (*Instructions Set Architecture*)**.
L'ISA che useremo sarà IJVM; la nostra microarchitettura conterrà un microprogramma (registrato nella ROM) il cui compito sarà quello di prelevare, decodificare ed eseguire istruzioni IJVM (ciclo di *fetch-decode-execute*)
Il microprogramma ha delle variabili che costituiscono lo **stato** del calcolatore: ogni funzione cambia il valore di almeno una delle variabili, modificando di conseguenza lo stato del calcolatore, mentre il PC viene fatto avanzare in modo da puntare all'istruzione successiva.
Ogni istruzione è composta da alcuni campi, di solito uno o due, e, fattore più importante, viene identificata con un **opcode** (codice operativo). Questo modello di esecuzione viene chiamato *fetch-execute*.

![[Mic-1.png]]
<h2 style="color:#ff8080;">
Data Path
</h2>

Le microistruzioni controllano un ciclo di data path, ovvero il processo mediante il quale due operandi passano attraverso l'ALU e viene memorizzato il risultato.
È costituito da:
- 10 registri di 32 bit (ad eccezione di un registro);
- ALU con 6 bit di controllo;
- Bus C per i dati in output verso i registri dallo shifter;
- Bus B per i dati verso l'ALU;
- Registro speciale H per l'input da sinistra dell'ALU; 
- Shifter con 2 bit di controllo.

|Nome Registro|Funzione|
|:----:|:----:|
|MAR|*Memory Address Register*|
|MDR|*Memory Data Register*|
|PC|*Program Counter* <br> Punta alla prossima istruzione da eseguire|
|MBR|*Memory Buffer Register*|
|SP|*Stack Pointer* <br> Punta alla cima dello stack|
|LV|*Local Variables* <br> Punta alla base del frame di attivazione della procedura in esecuzione |
|CPP|*Costant Pool Pointer* <br> Punta alla base dell'area delle costanti|
|TOS|*Top Of Stack* <br> La parola in cima allo stack|
|OPC|*Old Program Counter* <br> Registro che contiene PC-1|
|H|*Registro Holding*|
Ogni registro è comandato da uno o due *segnali di controllo*:
- una freccia bianca sotto un registro indica un segnale di controllo che abilita l'output del registro verso il bus B;
Nota: MAR non ha una connesione al bus B, quindi non ha segno di abilitazione
- una freccia nera sotto un registro indica un segnale di controllo che scrive nel registro (cioè "carica") un valore proveniente dal bus C
Nota: MBR non può essere caricato dal bus C, non ha un segnale di scrittura. 

Tutti i registri contenenti indirizzi, come MAR, utilizzano registri indirizzati espressi in parole, mentre registri come PC contengono indirizzi espressi in byte. Per ovviare questa differenza di conversione, si mappano i 32 bit dell'indirizzo MAR sull'indirizzo del bus B shiftando a sinistra di due i 32 bit del MAR.

##### Funzionamento Memoria (MAR/MDR)
La CPU comunica con la memoria mediante due modi:
- una porta di memoria da 32 bit indirizzabile a parola dai registri MAR e MDR;
- una porta di memoria da 8 bit indirizzabile a byte controllata dal registro PC che legge i byte e li memorizza negli 8 bit meno significativi di MBR. Questa porta può solo leggere in memoria e non può scrivere.
La combinazione MAR/MDR è utilizzata per leggere e scrivere parole di dati del livello ISA, mentre la combinazione PC/MBR è utilizzata per leggere il programma eseguibile del livello ISA che consiste in un flusso di byte.  

Il registro MBR può essere copiato sul bus B in due modi distinti:
- senza segno, ovvero la parola a 32 bit che verrà inserita nel bus B conterrà il valore di MBR negli 8 bit meno significativi, mentre i restanti 24 sono impostati a 0;
- con segno, ovvero mediante l'*estensione del segno*, che consiste nel duplicare il bit del segno di MBR nei 24 bit più alti del bus B. Questa tecnica infattifa sì che la nostra parola abbia i primi 24 bit o tutti uguali a 0 o uguali a 1.

La scelta tra convertire gli 8 bit di MBR in un valore con o senza segno prima di copiarlo sul bus B è determinata dal segnale di controllo (frecce bianche sotto MBR) che è asserito. 
L'unione di questi registri prende il nome di *Memory control registers*.

##### ALU e Shifter
L'ALU ha due input, quello sinistro collegato al registro H e quello destro collegato al bus B. L'output dell'ALU è collegato allo shifter, e mediante 2 segnali di controllo (e le loro combinazioni), posso decidere se shiftare l'output di 8 bit a sinistra (**SLL8**) o 1 bit a destra (**SRA1**) (o non farlo per niente).
Le funzioni dell'ALU vengono controllate da 6 bit di controllo, che combinati generano le funzioni elencate nella tabella: 
![[alu.png]]
##### H come registro generico
H è l'unico registro che comunica direttamente con l'ALU, perciò rappresenta l'input sinistro di quest'ultima. Ha un unico bit di controllo per l'abilitazione dell'input dal bus C, mentre l'output verso l'ALU è sempre attivo.
##### Due bus
Il nostro ciclo di data path beneficia di due bus:
- bus B, che può essere caricato con un qualsiasi valore di uno dei 9 registri collegati ad esso mediante la freccia bianca;
- bus C, ovvero il bus contenente il risultato proveniente dall'ALU che può essere memorizzato nei 9 registri collegati ad esso mediante freccia nera (quindi MBR è escluso in quanto la freccia nera al suo interno indica che è un registro da 8 bit).


<h2 style="color:#cc66ff;">
	Controllo
</h2>

L'unità di controllo microprogrammata ha il compito di decidere quali segnali di controllo abilitare durante ciascun ciclo. Ciò è determinato da una *sequenzializzazione* che ha la responsabilità di far avanzare passo passo la sequenza di operazioni necessarie per eseguire una singola istruzione ISA. 
Durante ogni ciclo il sequenzializzatore deve produrre due tipi di informazioni:

1. lo stato di ogni segnale di controllo del sistema;
2. l'indirizzo della microistruzione da eseguire subito dopo.

L'elemento più grande e più importante della sezione di controllo è una memoria chiamata **memoria di controllo**, ovvero un circuito che memorizza le microistruzioni invece che le istruzioni ISA. 
La memoria di controllo differisce dalla memoria centrale in quanto le istruzioni della seconda sono sempre eseguite nell'ordine determinato dagli indirizzi, mentre i microprogrammi richiedono maggiore flessibilità e quindi ognuna deve specificare in modo esplicito il proprio successore.
### MPC (MicroProgram Counter)
È il registro degli **indirizzi della memoria** di controllo. 
È collegato al **control store**(memoria di controllo) che contiene **512 microistruzioni**, ciascuna da **36 bit**.
All'inizio del ciclo di clock, MPC contiene l'indirizzo della microistruzione corrente, che viene propagato dal control store al MIR.


<h3 style="color:#009933;">
	MIR (MicroInstruction Register)
</h3>

È il registro dei **dati della memoria** ed il suo compito consiste nel memorizzare le microistruzioni in corso di esecuzione, i cui bit determinano i segnali di controllo che guidano il percorso dati. 

![[mir.png]]

- **Address** - *9 bit* - Contiene l'indirizzo di una potenziale successiva microistruzione;
- **JAM** - *3 bit* - Determina come viene selezionata la successiva microistruzione;
- **ALU** - *8 bit* -Seleziona le funzioni dell'ALU e dello shifter;
- **C** - *9 bit* - Seleziona quali registri sono scritti dal bus C;
- **Mem** - *3 bit* - Seleziona la funzione della memoria;
- **B** - *4 bit* - Seleziona la sorgente del bus B, la cui codifica è mostrata nella figura. 

1. Il microprogramma deve determinare quale sarà la microistruzione successiva, dato che non è necessario che esse vengano eseguite nello stesso ordine in cui appaiono nella memoria di controllo. Il calcolo dell'indirizzo della microistruzione successiva comincia dopo che MIR è stato caricato ed è stabile. Adesso dobbiamo verificare che valori ha assunto la serie di bit raggruppati sotto il nome di JAM. 
2. Se JAM è uguale a 000, allora il NEXT_ADDRESS verrà copiato in MPC e conterrà il valore della microistruzione successiva.
Se uno o più bit di JAM valgono 1, allora è necessario compiere delle azioni verificando il valore dei bit N e Z (opportunamente memorizzati in flip-flop per garantire la correttezza dei valori utilizzati): 

   - se $JAMN = 1$, si calcola l'OR logico con il flip-flop N e si memorizza il risultato nel bit più significativo di MPC;
   - se  $JAMZ = 1$, si calcola l'OR logico con il flip-flop Z e si memorizza il risultato nel bit più significativo di MPC.
  
  
   I componenti logici che effettuano questa elaborazione sono etichettati nella microarchitettura con la scritta **Bit alto** e la funzione booleana che calcola questo bit è:
  $F = (JAMZ$ $AND$ $Z)$ $OR$ $(JAMN$ $AND$ $N)$ $OR$ $NEXT$_ $ADDRESS[8]$
  JAMN e JAMZ si occupano dei salti condizionati, infatti se sono entrambi a 0 viene copiato il NEXT_ADDRESS (quindi la condizione è falsa e proseguo con il codice), mentre se uno di loro è 1 e la funzione restituisce 1 vi sarà un salto condizionato, in quanto il prossimo indirizzo in MBR sarà quello dell'etichetta del vero (ovvero MBR OR 0x100 -- convenzione vuole che l'etichetta del vero abbia il valore di Addr più una costante di 256).
 ![[jmpc.png]]
  
   Il terzo bit del campo JAM è $JMPC$ e regola i salti incondizionati:
   - se $JMPC=1$, si esegue l'OR tra gli 8 bit più bassi di Addr ed MBR ed il risultato è scritto sugli 8 bit più bassi di MPC (il bit più significativo verrà sempre regolato dalla rete Bit alto). Quindi implementa un salto a più vie, ovvero viene utilizzato per saltare all'indirizzo contenuto in MBR (opcode dell'istruzione). Questo avviene poiché quando $JMPC=1$, il valore degli 8 bit meno significativi di Addr è zero, quindi effettivamente salveremo il valore di MBR in MPC;
   - se $JMPC=0$, gli 8 bit più bassi di Addr sono copiati sugli 8 bit più bassi di MPC (il bit più alto di MPC dipende da JAMZ/JAMN). 
   
   Queste operazioni vengono effettuate dal quadrato etichettato con "O".
   
3. I 9 bit raggruppati sotto il nome di ALU servono per guidare le operazioni dell'ALU.
4. I 9 bit raggruppati sotto il nome di C occorrono per selezionare quale registri verranno caricati del valore di uscita dell'ALU (infatti si collegano ai registri mediante le frecce nere).
5. I 3 bit raggruppati sotto il nome di Mem abilitano la lettura, scrittura o il fetch, infatti invia tre bit di controllo alla Memory Control Registers. Le operazioni di lettura/scrittura vengono svolte dall'accoppiata MAR/MDR, mentre il fetch occorre per prelevare il prossimo byte del programma.
6. I 4 bit raggruppati sotto il nome di B utilizzano un decoder per generare 16 segnali di controllo che occorreranno per selezionare il registro da inserire nel bus B. Tutto il procedimento parte dai 4 bit di B che faranno da ingresso nel decoder, e da qui si genereranno $2^4$ uscite, 7 delle quali verranno tagliate in quante ce ne occorrono 9.

MPC non viene considerato come un registro vero e proprio, bensì un **registro virtuale**, cioè il luogo in cui raccogliere dei segnali e che assomiglia ad un pannello elettrico. Questo è possibile perché tutti i suoi input possono alimentare direttamente la memoria di controllo: sarà quindi sufficiente che siano inviati alla memoria di controllo in corrispondenza del fronte di discesa del clock, quando MIR viene seleizonato e letto (non è necessario memorizzare i segnali assunti al suo interno). //pag 253



La seguente figura mostra la temporizzazione degli eventi sul percorso dati:

**![[Pasted image 20210618160850.png]]**
1. all'inizio di ogni ciclo viene generato un breve inpulso che può essere determinato dal clock principale
2. sul fronte di discesa vengono impostati i bit che piloteranno tutte le porte logiche
   - quest'operazione richiede un intervallo di tempo definito: $\Delta w$
3.   Il registro richiesto viene selezionato e portato sul bus B.
      - Il valore si stabilizza in un tempo: $\Delta x$
4. La ALU e lo shifter cominciano ad operare sui dati validi.
      - l'output si stabilizza in un tempo: $\Delta y$
4. Passa un tempo $\Delta z$ ed i risultati vengono prorogati sul bus C  e vengono caricati nei registri durante il fronte di risalita
   - Anche se modifico dei registri di input, gli effetti delle modifiche giungeranno al bus C dopo un tempo sufficientemente lungo rispetto a quando sono stati caricati i registri
   - Sul fronte di salita non viene più alimentato il bus B, in preparazione al ciclo successivo

Ricordarsi che esiste un tempo di propagazione finito: una modifica sul bus B, intaccherà il bus C solo dopo un intervallo finito.
 - Per far si che ciò funzioni serve una rigida temporizzazione, un lungo ciclo di clock, un ritardo del'ALU conosciuto ed un rapido caricamento dei registri dal bus C

Un modo diverso per vedere il ciclo è la sua divisione in sottocicli **definiti implicitamente** e che l'inizio del sottociclo 1 sia guidato dal fronte di discesa del clock:
1. Si impostano i segnali di controllo ($\Delta w$)
2. I registri vengono caricati nel bus B ($\Delta x$)
3. La ALU e lo shifter svolgono le loro operazini ($\Delta y$)
4. I risultati vengono prorogati lungo il bus C e ritornano nei registri ($\Delta z$)

Con Definiti Implicitamente si intende che: nessun segnale comunica all'ALU quando funzionare, nè dice ai risultati quando entrare nel bus C.
ALU e shifter funzionano continuamente, ma i loro input sono da considerare inconsistenti fino al tempo $\Delta w + \Delta x$ dopo il fronte di discesa.
   - Analogo per l'output finchè non passa $\Delta w + \Delta x + \Delta y$ dopo il fronte di discesa
   
  Gli unici segnali espliciti sono:
   - il fronte di discesa del clock, che fa partire il ciclo del percorso dati
   - il fronte di salita del clock, che carica i registri dal bus C.

I limiti degli altri sottocili sono delterminati implicitamente dai tempi di propagazione dei circuiti.
È responsabilità del progettista assicurasi che $\Delta w + \Delta x + \Delta y + \Delta z$ giunga in anticipo rispetto il fronte di risalita del clock, per far funzionare il caricamento in ogni momento

## Comunicazione con la memoria
tramite i registri **MAR** e **MDR** a 32bit
- **MAR**: Memory Address Register
  - ha un solo segnale di controllo (input da bus C, ma nessun output verso bus B)
  - Mappatura particolare
    - Mar indicizza barole, mentre la memoria fisica byte
    - viene eseguita una moltiplicazione x4 -> perdo i 2 bit più a sinistra ed i 2 più a destra varranno 0
	 - è  caricato durante la discesa del Clock
	 - Accesso alla memoria entro il ciclo

- **MDR**: Memory Data Register
 - 2 segnali di controllo: lettura/scrittura da e per la memoria
  - Dopo una richiesta di lettura nel ciclo $k$, i dati saranno disponibili in MDR nel ciclo $k+2$
  - i dati sono disponibilli in MDR dopo 1 ciclo di data path
    - Durante il tempo di lettura dei nuovi dati, in MDR rimangono ancora i vecchi dati, su cui si può ancora operare
  - Si possono effettuare 2 richieste di lettura consecutive
    
## MAL
Nell'architettura MIC-1, il linguaggio IJVM non è abbastanza "di basso livello" per essere interpretato direttamente dal processore.
Ogni istruzione IJVM viene dunque codificata in una serie di istruzioni assemblative a più basso livello.
Viene dunque definito un linguaggio assemblativo MAL: Micro Assembly Language

##### Main:
```java
Main1 PC = PC + 1; fetch; goto(MBR)
```
E' l'istruzione principale del MAL. Incrementa il Program Counter, preleva il prossimo *opcode* (istruzione successiva o eventuale argomento) e fa un salto ad essa.
Questa istruzione deve essere presente alla fine di ogni altra micro-istruzione per garantire l'invariante che PC punti sempre alla prossima istruzione e MBR contenga il prossimo opcode

##### NOP:
```java
nop1 goto Main1
```
Micro-istruzione nulla che và direttamente alla micro-istruzione "*Main1*"

##### IADD:
```java
iadd1 MAR = SP = SP - 1; rd
iadd2 H = TOS
iadd3 MDR = TOS = MDR + H; wr; goto Main1
```
Decrementa lo stack di 1 ( SP = SP - 1) e avvia una richiesta di lettura del secondo valore dalla cima dello stack. Poi somma il valore letto con il TOS, lo scrive in cima allo stack(che ricordiamo che è stato decrementato)

##### ISUB:
```java
isub1 MAR = SP = SP - 1; rd
isub2 H = TOS
isub3 MDR = TOS = MDR - H; wr; goto Main1
```
Decrementa lo stack di 1 ( SP = SP - 1) e avvia una richiesta di lettura del secondo valore dalla cima dello stack. Poi sottrae il valore letto con il TOS, lo scrive in cima allo stack(che ricordiamo che è stato decrementato)

##### IAND:
```java
isub1 MAR = SP = SP - 1; rd
isub2 H = TOS
isub3 MDR = TOS = MDR AND H; wr; goto Main1
```
Decrementa lo stack di 1 ( SP = SP - 1) e avvia una richiesta di lettura del secondo valore dalla cima dello stack. Poi effettua l'AND logico bit-a-bit tra il valore letto e il TOS ,lo scrive in cima allo stack(che ricordiamo che è stato decrementato)

##### IOR:
```java
isub1 MAR = SP = SP - 1; rd
isub2 H = TOS
isub3 MDR = TOS = MDR OR H; wr; goto Main1
```
Decrementa lo stack di 1 ( SP = SP - 1) e avvia una richiesta di lettura del secondo valore dalla cima dello stack. Poi effettua l'OR logico bit-a-bit tra il valore letto e il TOS ,lo scrive in cima allo stack(che ricordiamo che è stato decrementato)

##### DUP:
```java
dup1 MAR = SP = SP + 1
dup2 MDR = TOS; wr; goto Main1
```
Aumenta lo stack di 1 ( SP = SP + 1) e scrive in cima allo stack(che è stato incrementato) il valore in TOS. L'istruzione duplica quindi il valore e lo mette in cima allo stack.

##### SWAP
```java
swap1 MAR = SP - 1; rd
swap2 MAR = SP
swap3 H = MDR; wr
swap4 MDR = TOS
swap5 MAR = SP - 1; wr
swap6 TOS = H; goto Main1
```

A=primo elemento, quello in cima allo stack. B=secondo elemento dalla cima dello stack.
 Decremento SP per puntarlo alla cella contenente B e avvio una lettura
Faccio puntare MAR in cima allo stack.
Qui MDR contiene il valore di B, lo memorizzo in H e avvio la scrittura. 
Scrivo il valore di B nella cella di A(ricordiamo che MAR punta ad A)
Assegno a MDR il valore di A (TOS) 
Faccio puntare MAR alla cella di B e scrivo il valore di A su di esso
Imposto TOS al valore di B

#### BIPUSH *num*
```java
bipush1 SP = MAR = SP + 1
bipush2 PC = PC + 1; fetch
bipush3 MDR = TOS = MBR; wr; goto Main1
```
Incrementa lo stack di 1 e aggiorna MAR ad esso (SP = MAR = SP + 1)
Incremento PC e avvio un'operazione di fetch per garantire l'invariante e infine aggiorno la cima dello stack e TOS con il parametro di BIPUSH passato

#### ILOAD *offset-var*
```java
iload1 H = LV
iload2 MAR = MBRU + H;rd
iload3 MAR = SP = SP + 1
iload4 PC = PC + 1;fetch;wr
iload5 TOS = MDR; goto Main1
```
Imposto MAR all'indirizzo della variabile(calcolato facendo la somma tra LV e l'offset MBRU) e avvio una lettura. Incremento lo stack di 1 e aggiorno MAR. Prelevo il prossimo OPCODE e imposto TOS al valore della variabile.

#### ISTORE *offset-var*
```java
istore1 H = LV
istore2 MAR = MBRU + H
istore3 MDR = TOS; wr
istore4 SP = MAR = SP - 1;rd
istore5 PC = PC + 1;fetch
istore6 TOS = MDR; goto Main1
```
Mi calcolo l'offset della variabile e lo salvo in MAR. Imposto MDR al valore di TOS e avvio una operazione di scrittura(scriverò dunque il valore in cima allo stack nella locazione di memoria della variabile passata come argomento).
Decremento lo stack di 1, aggiorno MAR e avvio una operazione di lettura. Incremento PC per garantire l'invariante e aggiorno il TOS.

#### WIDE
```java
wide1 PC = PC + 1; fetch
wide2 goto(MBR OR 0x100)
```
Faccio l'OR tra l'opcode (che sarà ILOAD o ISTORE) e il valore 0x100.
Il valore risultante corrisponderà all'indirizzo dell'istruzione wide_iload o wide_istore nel file MAL(non c'è nel file config in quanto lì si trovano le istruzioni IJVM)

#### WIDE ILOAD
```java
wide_iload1 PC = PC + 1;fetch
wide_iload2 H = MBRU << 8
wide_iload3 H = MBRU OR H
wide_iload4 MAR = LV + H;rd; goto iload3
```
Incremento il PC e avvio una operazione di fetch. Faccio diventare MBRU a 32 bit 
(H = MBRU << 8) e faccio l'OR con il MBRU *fetchato* prima.
Aggiorno MAR a LV + H(indirizzo della variabile), avvio una lettura e vado all'istruzione iload3
Nota bene! Anche se *WIDE ILOAD* ha un offset a 16 bit come il LDC_W, il valore caricato è comunque quello di una variabile, non di una costante!
#### WIDE ISTORE
```java
wide_istore1 PC = PC + 1;fetch
wide_istore2 H = MBRU << 8
wide_istore3 MAR = LV + H;goto istore3
```
Incremento il PC e avvio una operazione di fetch. Faccio diventare MBRU a 32 bit 
(H = MBRU << 8) e faccio l'OR con il MBRU *fetchato* prima.
Aggiorno MAR a LV + H(indirizzo della variabile) e vado all'istruzione iload3

#### LDC_W *offset-const*
```java
ldc_w1 PC = PC + 1; fetch
ldc_w2 H = MBRU << 8
ldc_w3 H = MBRU OR H
ldc_w4 MAR = CPP + H;rd;goto iload3
```
Uguale al WIDE ILOAD ma all'ultima istruzione, l'indirizzo della variabile viene costruito tramite la somma di CPP e H(contenente l'offset)

#### IINC *offset-var*  *numeric value*
```java
iinc1 H = LV
iinc2 MAR = MBRU + H;rd 
iinc3 PC = PC + 1;fetch
iinc4 H = MDR
iinc5 PC = PC + 1;fetch
iinc6 MDR = MBR + H;wr; goto Main1
```
Imposto MAR all'indirizzo della variabile(MBRU+H) e avvio una operazione di lettura.
Prelevo il prossimo opcode, mi salvo il valore di MDR appena caricato e prelevo di nuovo il prossimo opcode. Sommo il valore della variabile con il  valore numerico caricato.
Scrivo il valore nuovo sul MAR.

#### GOTO *offset-address*
```java
goto1 OPC = PC - 1
goto2 PC = PC + 1;fetch
goto3 H = MBR << 8
goto4 H = MBRU OR H
goto5 PC = OPC + H;fetch
goto6 goto main1
```
Decremento PC e lo salvo in OPC.
Leggo il secondo byte dell'etichetta
Mi costruisco l'indirizzo a 16 bit della prossima istruzione(H = MBR <<8;H = MBRU OR H)
Porto il PC a OPC + H (dove H è l'offset e OPC il PC iniziale)

#### IFLT *offset-address*
```java
iflt1 MAR = SP = SP - 1;rd
iflt2 OPC = TOS
iflt3 TOS = MDR
iflt4 N = OPC;if(N) goto T;else goto F
```
Decremento lo stack di 1,aggiorno MAR e avvio una operazione di lettura.
Mi salvo temporaneamente TOS in OPC e aggiorno il TOS(visto che lo stack è stato decrementato). Infine mi salvo OPC nel registro "virtuale" in N e se il valore di questo è negativo, vado all'istruzione *T* se no all'istruzione *F*

#### IFEQ *offset-address*
```java
iflt1 MAR = SP = SP - 1;rd
iflt2 OPC = TOS
iflt3 TOS = MDR
iflt4 Z = OPC;if(Z) goto T;else goto F
```
Decremento lo stack di 1,aggiorno MAR e avvio una operazione di lettura.
Mi salvo temporaneamente TOS in OPC e aggiorno il TOS(visto che lo stack è stato decrementato). Infine mi salvo OPC nel registro "virtuale" in Z e se il valore di questo è 0, vado all'istruzione *T* se no all'istruzione *F*

#### IF_ICMPEQ *offset-address*
```java
if_icmpeq1 MAR = SP = SP - 1;rd
if_icmpeq2 MAR = SP = SP - 1
if_icmpeq3 H = MDR;rd
if_icmpeq4 OPC = TOS
if_icmpeq5 TOS = MDR
if_icmpeq6 Z = OPC - H; if(Z) goto T;else goto F
```
Decremento lo stack di 1,aggiorno MAR e avvio una operazione di lettura.
Decremento lo stack di nuovo di uno, mi salvo il valore letto in H e avvio un'altra lettura.
Mi salvo temporaneamente TOS in OPC e aggiorno il TOS(visto che lo stack è stato decrementato). Infine mi salvo OPC - H nel registro "virtuale" in Z e se il valore di questo è 0, vado all'istruzione *T* se no all'istruzione *F*

#### T
```java
T OPC = PC - 1;goto goto2
```
Questa micro-istruzione viene eseguita se la condizione dell'IF è vera
Imposto OPC a PC - 1 e vado all'istruzione *goto2*

#### F
```java
F  PC = PC + 1
F2 PC = PC + 1; fetch
F3 goto Main1
```
Incremento PC di 1, avvio una operazione di fetch e incremento di nuovo PC.
In questo PC punterà all'operazione dopo l'IF

#### INVOKEVIRTUAL *offset-method*
```java
invokevirtual1 PC = PC + 1; fetch
invokevirtual2 H = MBRU << 8
invokevirtual3 H = MBRU OR H
invokevirtual4 MAR = CPP + H;rd
invokevirtual5 OPC = PC + 1
invokevirtual6 PC = MDR;fetch
invokevirtual7 PC = PC + 1;fetch
invokevirtual8 H = MBRU << 8
invokevirtual9 H = MBRU OR H
```
*invokevirtual1_4*:Mi costruisco l'indirizzo del metodo(H=MBRU<<8;H=MBRU OR H), lo salvo nel MAR e avvio una operazione di lettura. 
*invokevirtual5*:Mi salvo in OPC il vecchio PC(che mi servirà per il ritorno
*invokevirtual6*: PC viene impostato a MDR(ovvero alla base del frame di attivazione del metodo) e avvio una operazione di fetch
*invokevirtual7_9*: Prelevo i due byte e mi salvo in H il numero dei parametri
(H=MBRU << 8;H=MBRU OR H)



```java
invokevirtual10 PC = PC + 1; fetch
invokevirtual11 TOS = SP - H
invokevirtual12 TOS = MAR = TOS + 1
invokevirtual13 PC = PC + 1;fetch
invokevirtual14 H = MBRU << 8
invokevirtual15 H = MBRU OR H
invokevirtual16 MDR = SP + H + 1;wr
invokevirtual17 MAR = SP = MDR
invokevirtual18 MDR = OPC;wr
invokevirtual19 MAR = SP = SP + 1
invokevirtual20  MDR = LV;wr
invokevirtual21 PC = PC + 1;fetch
invokevirtual22 LV = TOS;goto Main1
```
*invokevirtual10-1->15*: Mi costruisco il numero di variabili locali del nuovo metodo e lo salvo in H

*invokevirtual11->12*: SP punta all'ultimo parametro passato al nuovo metodo nel main
Questo valore viene decrementato di H(ovvero numero di parametri del modo) e poi incrementato di 1 per puntare a OBJREF. Tutto ciò viene salvato in MAR e TOS

*invokevirtual16*: Sovrascrivo MDR con l'indirizzo della cella del puntatore dell'indirizzo di rientro al main e avvio una scrittura sulla cella che contiene OBJREF 
(dunque sovrascrivo la cella di OBJREF con un link pointer)

*invokevirtual17->18*: Imposto MAR e SP all'indirizzo del link pointer e ci scrivo il vecchio valore di PC (contenuto in OPC)

*invokevirtual19->20*: Salvo il vecchio LV sopra la cella che contiene OPC ( SP + 1)

*invokevirtual21*: Prelevo l'opcode dell'istruzione successiva

*invokevirtual22*: Imposto LV del metodo al link pointer ( da dove il MIC 1 prenderà le variabili che gli occorrono  per il metodo) e poi vado al Main1

#### IRETURN
```java
ireturn1 MAR = SP = LV;rd
ireturn2 //attendo che si completi la lettura
ireturn3 LV = MAR = MDR;rd
ireturn4 MAR = LV + 1
ireturn5 PC = MDR;rd;fetch
ireturn6 MAR = SP
ireturn7 LV = MDR 
ireturn8 MDR = TOS;wr;goto Main1
```

*ireturn1->3*: Avvio una lettura per ottenere il link pointer(che risiede in LV). Una volta ottenuto leggo il contenuto della cella puntata dal link pointer

*ireturn4->5*: Imposto MAR per leggere il vecchio LV (LV del "Main Stack"), ripristino PC al valore originale(prima della chiamata del metodo) e infine leggo il vecchio LV	e prelevo l'opcode successivo

*ireturn6->8*: Visto che SP punta al TOS del metodo, lo salvo in MAR, ripristino LV nel "Main Stack" e scrivo il valore del TOS del metodo nel TOS del Main


### Tips & Miscellaneous
- All'inizio di ogni micro istruzione SP punta sempre alla cima dello stack

- All'inizio di ogni micro istruzione TOS contiene sempre il valore della cima dello stack

- LDC_W, GOTO, WIDE ILOAD/ISTORE e IFLT,IFEQ,IF_ICMPEQ e INVOKEVIRTUAL hanno come parametro un offset a 16 bit

- Se si ha bisogno di un registro ausiliario conviene usare OPC

- Se si vuole convertire MBR(1 byte) in una parola(4 bit)si usa MBRU se MBR è inteso positivo, altrimenti si usa MBR

- Se si vuole costruire un intero da 2 byte(indice o offset) si usa la sottosequenza tipica:
  1. PC = PC + 1;fetch
  2. H = MBRU << 8(o MBR se è intero con segno)
  3. H = MBRU OR H


 - E' soltanto possibile shiftare a sinistra di 8 bit e a destra di 1 bit

- Se l'istruzione da implementare richiede un parametro, bisognerà effettuare un fetch all'interno di esso

- Se si ha bisogno di effettuare una sottrazione, il sottraendo va messo in H

# Incrementare la velocità del mic-1

Esisono tre modi per incrementare la velocità:

- **Ridurre il numero di cicli di clock** necessari all'esecuzione di un'istruzione
- **Semplificare l'organizzazione** in modo che il ciclo di clock sia più breve
- **Sovrapporre l'esecuzione** delle istruzioni

La sequenza di operazioni che devono necessariamente essere eseguite in modo seriale determina la **lunghezza minima** del ciclo di clock

### Ridurre il numero di microistruzioni

Come fare?

- **Fusione del ciclo di esecuzione dell'interprete** (*goto Main1*) **con in microcodice**: introdurre il ciclo dell'interprete al termine di ogni sequenza di microcodice (implementazione di goto Main1 a livello hardware)

    esempio:

    ![Incrementare%20la%20velocita%CC%80%200fe39e89836a40de835d9d6df47fac7b/Untitled.png](Riassunti/12-Mic2/Incrementare%20la%20velocità%200fe39e89836a40de835d9d6df47fac7b/Untitled.png)

- **Introduzione di un terzo bus**

    Architettura schematizzata:

    ![Incrementare%20la%20velocita%CC%80%200fe39e89836a40de835d9d6df47fac7b/Untitled%201.png](Riassunti/12-Mic2/Incrementare%20la%20velocità%200fe39e89836a40de835d9d6df47fac7b/Untitled%201.png)

    esempio istruzione iload:

    ![Incrementare%20la%20velocita%CC%80%200fe39e89836a40de835d9d6df47fac7b/Untitled%202.png](Riassunti/12-Mic2/Incrementare%20la%20velocità%200fe39e89836a40de835d9d6df47fac7b/Untitled%202.png)

- **IFU** introduzione di un'unità per il fetch delle istruzioni $\Longrightarrow$ leggere le istruzioni dalla memoria per mezzo di un'unità funzionale specializzata

## IFU

![Incrementare%20la%20velocita%CC%80%200fe39e89836a40de835d9d6df47fac7b/Untitled%203.png](Riassunti/12-Mic2/Incrementare%20la%20velocità%200fe39e89836a40de835d9d6df47fac7b/Untitled%203.png)

### Senza la IFU

Per ogni istruzione:

1. Il PC viene **passato attraverso la ALU** e incrementato
2. il PC viene **usato per leggere il byte** seguente nel programma
3. gli operandi vengono **letti dalla memoria**
4. l'ALU **esegue un calcolo** e i risultati vengono memorizzati

La **letura e la decodifica** dei campi delle istruzioni è un'operazione ripetitiva, comune a tutte le istruzioni, quindi vale la pena trovare un modo per automatizzarla e addirittura creare un nuovo organo a livello hardware specializzato per svolgerla  

### Con la IFU

1. L'IFU incrementa il PC in modo indipendente (meno carico sulla ALU) e fare operazioni di pre-fetch, prima era necessario un intero ciclo di attesa dopo aver lanciato un operazione di fetching, ora il codice operativo è subito disponibile

e bon, ez, un passaggio invece che 4 🤯

### Come funziona ?

![Incrementare%20la%20velocita%CC%80%200fe39e89836a40de835d9d6df47fac7b/Untitled%204.png](Riassunti/12-Mic2/Incrementare%20la%20velocità%200fe39e89836a40de835d9d6df47fac7b/Untitled%204.png)

Fuori dalla IFU:

- Aggiungiamo un nuovo registro **MBR2** che ha un'ampiezza di 16 bit (spesso necessari per istruzioni che richiedono offsets), anche lui come MBR1 può essere signed (MBR2) e unsigned (MBR2U)

Dento la IFU:

- Un circuito che si occupa di **aumentare il PC** di 1 o di 2 eliminando la necessità di usare la ALU per incrementarlo, l'**incremento è automatico** quando preleviamo qualcosa dai due MBR assieme all'**operazione di fetch**

- Una **memoria a scorrimento** che contiene tutti i dati che arrivano dalla memoria, ogni volta che viene letto un nuovo byte quello precendente viene shiftato

    ![Incrementare%20la%20velocita%CC%80%200fe39e89836a40de835d9d6df47fac7b/Untitled%205.png](Riassunti/12-Mic2/Incrementare%20la%20velocità%200fe39e89836a40de835d9d6df47fac7b/Untitled%205.png)

    Ogni volta che uno dei byte dello shift register viene prelevato gli altri vengono fatti scorrere verso destra 😯

- Gli input di MBR2 sono incrociati a causa del registro a scorrimento

    ![Incrementare%20la%20velocita%CC%80%200fe39e89836a40de835d9d6df47fac7b/Untitled%206.png](Riassunti/12-Mic2/Incrementare%20la%20velocità%200fe39e89836a40de835d9d6df47fac7b/Untitled%206.png)

- Ogni volta che la **coda si svuota** la IFU inizia una **nuova** operazione di **fetch** per riempirla di nuovo
- Viene introdotto un nuovo registro interno chiamato **IMAR** che accede alla memoria a gruppi di 4 byte come MAR ed è un modo per **leggere 4 byte alla volta** e scriverli dentro allo shift register, OP, ha pure un suo incrementatore dedicato che quindi ci permetti di incrementare di 4 byte.

    Inoltre ogni volta che scriviamo sul PC, quello che abbiamo scritto in PC **viene scritto in IMAR** azzerando i due bit meno significativi che equivale a scrivere l'inidirizzo della parola contenuta in PC
	
	# Livello del linguaggio assembletivo (Livello 4)
La differenza che contraddistingue questo livello rispetto ai livelli di microarchitettura, ISA e macchina del sistema operativo è che il livello del linguaggio assembletivo è implementato mediante traduzione (compilazione) invece che interpretazione. I programmi che si occupano di tradurre in un particolare linguaggio sono chiamati traduttori. 
Il linguaggio nel quale è scritto il programma originale viene chiamato **linguaggio sorgente**, mentre quello nel quale viene convertito viene chiamato **linguaggio destinazione**. 
La traduzione viene implementata in due passi distinti:
1. generazione di un programma equivalente nel linguaggio di destinazione;
2. esecuzione del programma appena generato.

A seconda della relazione che intercorre tra il linguaggio sorgente e il linguaggio destinazione è possibile dividere i traduttori in due gruppi:
- quando il linguaggio sorgente è essenzialmente una rappresentazione simbolica di un linguaggio macchina numerico, il traduttore si chiama **assembletore** e il linguaggio sorgente viene chiamato **linguaggio assemblativo**;
- quando il linguaggio sorgente è linguaggio ad alto livello come Java o C e il linguaggio macchina numerico oppure una rappresentazione simbolica, il traduttore viene chiamato **compilatore**.

###### Che cos'è un linguaggio assemblativo e perché utilizzarlo
È un linguaggio nel quale ciascuna istruzione produce esattamente un'struzione macchina. Quindi esiste una corrispondenza tra le istruzioni macchina e le istruzioni del programma assemblativo: se ciascuna linea del linguaggio assemblativo contiene esattamente un'istruzione macchina, un programma assemblativo  di n linee genererà un programma in linguaggio macchina di n parole.

La ragione dell'utilizzo del linguaggio assemblativo al posto del linguaggio macchina (in esadecimale) è che è molto più facile programmare utilizzando il linguaggio assemblativo, in quanto l'uso di una forma simbolica per i nomi e gli indiririzzi è più agevole rispetto alla rappresentazione binaria (ottale, esadecimale). Il linguaggio assemblativo infatti:
- memorizza dei nomi simbolici per delle operazioni, come l'addizione e la sottrazione;
- determina dei valori numeri per le locazioni di memoria assegnate dal programmatore mediante nomi simbolici;
- ha accesso a tutte le funzionalità e a tutte le istruzioni disponibili nella macchina di destinazione, mentre il programmatore in linguaggio ad alto livello non ha la stessa modalità di accesso. 
(es.: se la macchina di destinazione ha un bit di overflow, un programma assemblativo può testarlo, mentre un programma Java non lo può fare direttamente.)

![[linker.png]]

## Come funziona un assemblatore
L'assemblatore ha il compito di associare ad ogni simbolo del linguaggio IJVM ad un valore numerico. Talvolta, i simboli del nostro programma vengono definiti in punti successivi, e quindi si fa riferimento a simboli non ancora definiti (*forward references*). Per ovviare a questo tipo di problema, l'assemblatore effettua una lettura del programma in più (letture ≈ *passate*). Per questo il compito dell'assemblatore si divide in due passi:
 - **Prima passo**:
l'assemblatore costruisce due tabelle: 
   - la **Tabella delle Costanti**, contenente le costanti globali e i nomi simbolici dei sottoprogrammi;
   - la **Tabella dei Simboli**, contenente i valori dei simboli;
   - la **Tabella degli Opcode**, per determinare la lunghezza di un'istruzione. Infatti contiene almeno un elemento per ogni opcode del linguaggio IJVM.
   
   Nell'assegnare un valore ad un simbolo nel campo etichetta di un'istruzione, l'assemblatore deve sapere quale indirizzo avrà quell'istruzione in fase di esecuzione. Per tenere traccia di tale indirizzo, l'assemblatore mantiene una variabile durante l'assemblaggio, nota come *contatore della locazione dell'istruzione* o **ILC**.
   
  
- **Secondo passo**:
l'assemblatore generare il codice oggetto (di livello inferiore) del programma sorgente. 

Una volta terminati questi passi, **ottengo il codice oggetto**.


### Linker (processo di collegamento)
Prima che il programma possa essere eseguito è necessario recuperare
tutte le procedure e collegarle fra loro in modo appropriato. Inoltre, in assenza di memoria virtuale, occorre caricare in memoria centrale il programma ottenuto dal collegamento delle procedure. I programmi che eseguono questi passi sono chiamati in vari modi, tra cui linker, linking Ioader e linkage editor. Quindi il lnker deve fondere i due moduli oggetto separati in un unico spazio di indirizzamento. 
A tale scopo, il link costituisce una tabella contenente per ciascun modulo (es. main e metodi):
- nome;
- lunghezza;
- indirizzo di inizio.

L'ultima operazione consiste nello scandire il modulo oggetto per sostituire ai riferimenti non risolti i relativi valori di offset. 
Una volta terminato ciò **ottengo il codice eseguibile**.
### Loader
Il loader ha il compito di portare tutti i moduli oggetto in memoria centrale. 

# Struttura generale di un sistema a livello firmware

# 1. Unità di elaborazione

Un **sistema di elaborazione** a livello firmware è costituito da un certo numero di unià di elaborazione tra loro interagenti $\text{U}_1,...,\text{U}_n$, come mostrato in figura 

![Struttura%20generale%20di%20un%20sistema%20a%20livello%20firmwar%20d25d7800694b49ad81f05cc6fafaf696/Untitled.png](Riassunti/14-Riassunti%20pdf%20Aldinucci/Struttura%20generale%20di%20un%20sistema%20a%20livello%20firmwar%20d25d7800694b49ad81f05cc6fafaf696/Untitled.png)

Ad ogni unità di elaborazione vengono affidati compiti specifici e e l'insieme di essi, in un calcolatore *genral purpose,* ha la caratteristica di essere generale nei confronti del supporto fornito ai livelli superiori.

Un'unità di elaborazione per essere considerata tale deve avere le seguenti caratteristiche:

- **Autonomo** : deve essere capace di controllare la propria elaborazione in modo autonomo, può però ricevere informazioni utili all'elaborazione tramite l'interazione con altre unità
- **Sequenziale** : il funzionamento dell’unità è descritto da un programma sequenziale. Il  microprogramma é la descrizione del funzionamento dell’unità, e il microlinguaggio è il linguaggio di programmazione sequenziale con cui esprimere il microprogramma.

# 2. Modello Parte di Controllo - Parte Operativa

Il microprogramma di un'unità di elaborazione è interpretato a sua volta dal **livello hardware.** L'interpretazione viene svolta da due reti sequenziali tra loro interagenti dette **Parte di Controllo (PC)** e **Parte Operativa** come in figura

![Struttura%20generale%20di%20un%20sistema%20a%20livello%20firmwar%20d25d7800694b49ad81f05cc6fafaf696/Untitled%201.png](Riassunti/14-Riassunti%20pdf%20Aldinucci/Struttura%20generale%20di%20un%20sistema%20a%20livello%20firmwar%20d25d7800694b49ad81f05cc6fafaf696/Untitled%201.png)

### Parte Operativa - PO

La Parte Operativa (PO) esegue le operazioni dettate dai comandi del microlinguaggio (istruzioni) e le esegue grazie all'utilizzo di tipici circuiti come:

- **Commutatori** (Multiplexer)
- **Selezionatori** (Decoder)
- **Reti di calcolo** mono-funzione o multi-funzione (**ALU**)
- **Registri**

### Parte di Controllo - PC

La Parte di Controllo (PC) provvede:

- al **controllo della sequenzializzazione** delle microistruzioni utilizzando le **variabili di condizionamento $\{\text{X}\}$** che rappresentano lo stato della Parte Operativa (PO)
- ad ordinare alla Parte Operativa (PO) l'esecuzione di ogni microistruzione mediante le varibaili di controllo $y=\{\alpha\} \smallsmile \{\beta\}$.
    - $\beta$ abilita/disabilita la scrittura nei registri della Parte Operatica (PO)
    - $\alpha$ fornisce gli ingressi secondari di commutatori, selezionatori e reti di calcolo

PC e PO messe assieme sono **reti sequenziali LLC (Level-input Level-output Clocked)** impulsate dallo stesso segnale di clock.

Il **clock** detto "ciclo di clock dell'unità" verrà determinato in modo tale de permettere la stabilizzazione di entrambe le reti.

# 3. Procedimento di progettazione delle unità

I passi essenziali nel procedimento formale di progettazione di una unità di elaborazione sono i seguenti :

1. **Specifica delle operazioni esterne affidate all'unità**  $\Longrightarrow$ le operazioni esterne sono le funzionalità che dall'esterno (quindi da altre unità) vengono richieste all'unità in questione.
2. **Scrittura del microprogramma che interpreta le operazioni esterne**
3. **Derivazione formale dello schema della rete sequenziale Parte Operativa a partire dal
microprogramma**
4. **Derivazione formale della rete sequenziale Parte Controllo a partire dal microprogramma**
5. **Valutazione del ciclo di clock dell’unità** in funzione dei ritardi temporali delle risorse hardware adottate
6. **Valutazione del tempo medio di elaborazione** di ogni operazione e/o relativo all’insieme delle
operazioni affidate all’unità

# Formalizzazione del procedimento di progettazione
Il procedimento di progettazione ha lo scopo di **realizzare la struttura** dell’unità di elaborazione, secondo il modello PC - PO e di **valutarne le prestazioni**, attraverso la stima del  tempo medio di elaborazione e della banda di elaborazione.

## Microlinguaggio

La formalizzazione, in questo campo, si basa sulla **scrittura** di un microprogramma eseguibile , nel quale ogni *microistruzione* é eseguibile all'interno di **un ciclo** di clock.


Nel modello *Mealy-Moore* il microlinguaggio é detto **Phase Structured**

case $x_{i1}, x_{i2} ...x_{in}$ of
&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp00 .. 0 : $\mu op_0$, goto $j_0$
&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp00 .. 0 : $\mu op_1$, goto $j_1$

dove 
1. *i* é l'indirizzo della microistruzione
2. $x_{i1} x_{i2} ...x_{in}$ sono varibili di condizionamento
3. Le condizioni logiche della microstruzioni sono la combinazione di tutte le variabili di controllo ($C_{ih}$ con $h=0...2_n-1$)
4. $\mu op_0$ é una microperazione che puó:
	- non fare nulla (*nop*) 
	- un trasferimento tra registri
	- un insieme di operazioni tra registri eseguite in parallelo nello stesso ciclo di clock
5. $j_h$ é l'indirizzo della microistruzione successiva
6. la coppia $\mu op_{ih}, goto_{jb}$ é detta **frase**, la tripla $C_{ih}:\mu op_{ih}, goto_{jb}$  é detta **frase condizionale**

In alternativa alla struttura sopra indicata possiamo usare una struttura piú compatta:
$(C_i0)\mu op_{0}, j_0;(C_i1)\mu op_{1}, goto_{1}$

## Struttura della Parte Operativa
La struttura della Parte Operativa si ricava nel seguente modo:
1. Si individuano  gli ingressi di ogni registro
2. Si individua la sottostruttra indipendente di ogni registro, con il proprio segnale $\beta$ indirizzato verso la parte operativa. Nel caso gli ingressi siano piú di uno al registro é connesso un multiplexer(commutatore), anche questi con $lg_2 r$ segnali di controllo $\alpha$.
3. Si individuano gli ingressi delle reti logiche
4. Si ricava la sottostruttura indipendente di ogni rete logica. Se ti stratta di una ALU, con r funzioni occorrono $lg_2 r$ segnali di controllo. Se sono presenti piú di un input per ogni ingresso si inserisce un multiplexer.
	Se le operazioni non sono parallele di norma basta un'ALU sola, altrimenti possono servire una serie di reti logiche tra ALU e reti dedicate(es: shift)
	
![[Pasted image 20210617225335.png]] 

## Struttura della Parte di controllo
La struttura di una parte di controllo si ricava mediante il seguente procedimento:
1. Gli stati interni corrispondono biunicamente alle etichette delle microistruzioni. Il registro degli stati di controllo é di ($lg_2$ m) bit.
2. Gli stati di ingresso corrispondono biunivocamente alle possibili combinazioni di variabili di condizionamento.
3. . Gli stati di uscita corrispondono biunivocamente alle possibili combinazioni di segnali di controllo $\epsilon$
4. La tabella di verità della funzione delle uscite e della funzione di transizione dello stato interno viene ricavata in base alle tre corrispondenze suddette ed alla struttura del microprogramma

# Ciclo di clock
A differenza di una rete sequenziale isolata, per un'unità di elaborazione PC-PO occorre *ricavare la condizione di stabilizzazione* di entrambe le reti sequenziali PC e PO. Infatti il ciclo di clock non può terminare se non si stabilizzano le funzioni di transizioni della PC (ingressi del registro di stato del controllo PC) e di tutti i registri della PO. 

![[Pasted image 20210617225223.png]]
La foto sopra indica come ricavare la lunghezza del ciclo di clock attraverso una sequenza di eventi temporali:
- le frecce indicano eventi di "stabilizzazione di funzioni";
- gli intervalli temporali indicano i ritardi massimi di stabilizzazione.

|Voce|Definizione|
|:----:|:----:|
|$T_{\omega PO}$|Massimo ritardo della funzione delle uscite della PO|
|$T_{\sigma PO}$|Massimo ritardo della funzione di transizione dello stato interno della PO|
|$T_{\omega PC}$|Massimo ritardo della funzione delle uscite della PC|
|$T_{\sigma PC}$|Massimo ritardo della funzione di transizione dello stato interno della PC|
|$\delta$|Impulso di clock|

Ci sono diversi tipi di PC-PO:
- Mealy-Moore:
Se PO è una rete di Moore, la sua uscita è disponibile all'inizio del ciclo di clocl; dopo un tempo $T_{\omega PO}$ sono quindi stabili le variabili di condizionamento. Solo a questo punto, poiché PC è una rete di Mealy, può iniziare la stabilizzazione della funzione $\omega_{PC}$ e della funzione $\sigma_{PC}$ in parallelo. Una volta che $\omega_{PC}$ si è stabilizzata, dopo un intervallo $T_{\omega PC}$, può iniziare la stabilizzazione della funzione $\sigma_{PO}$. Quindi il ciclo di clock si può concludere quando si sono stabilizzate tanto la $\sigma_{PC}$ e la $\sigma_{PO}$.
**Lunghezza del ciclo di clock: $\tau = T_{\omega PO} + max (T_{\omega PC}+T_{\sigma PO}, T_{\sigma PC}) + \delta$**. 
Nella formula di $\tau$, spesso è il termine $T_{\omega PC}+T_{\sigma PO}$ a predominare, fornendo una buona approssimazione del valore di $\tau$.

- Moore-Moore:
**Lunghezza del ciclo di clock: $\tau = max(T_{\omega PC}+T_{\sigma PO},T_{\omega PO}+T_{\sigma PC})+ \delta$**.

La conversione in MHz si ottiene dal rapporto $1/\tau$.
Riferendosi alle voci della tabella, enunciamo alcuni tempi standars per le diverse componenti dell'unità di elaborazione:
- $singola$ $porta$ $AND/OR: 1$ $ns$;
- $ALU= 5$ $ns$;
- $\delta = 1$ $ns$;
- $porte$ $not, collegamenti$ ≅ $0$.

1. **Condizioni per la parallelizzazione**
	Generalmente, una microoperazioni consta di più elementi eseguiti in parallelo (nello stesso ciclo)
	   -  es: A+B -> A, C+1 -> C

   
   A + B -> A e C +1 -> C sono computazioni completamente indipendenti, nessuna delle 2 dipende dal risultato dell'altra, dunque posso eseguirle contemporaneamente.
    - Ciò è possibile solo se la PO contenga risorse sufficenti, nel nostro caso specifico necessitiamo di 2 differenti reti di calcolo (1 ALU ed 1 incrementatore). &nbsp
    Se forzassimo le 2 op sulla stessa ALU, il parallelismo sarebbe impossibile
	
	![[Pasted_image_20210617213656.png.png]]
	
	Formalmente, l'operazione in parallelo ha luogo durante l'intervallo $T_{\sigma PO}$ del ciclo di clock. 
	Le reti della PO utilizzare per le operazioni elementari eseguite in parallelo si stabilizzano contemporaneamente
	
	Occorre rispettare delle precise condizioni per far si che le stesse computanzioni eseguite in parallelo o sequenzale siano equivalenti.
	- indichiamo con ";" le op in sequenza ed "," quelle in paralleo
	1. &nbsp&nbspA+B->A;C->D &nbsp&nbsp $=$ &nbsp&nbspA+B,C->D
	2. &nbsp&nbspA+B->A;C->A  &nbsp &nbsp$\neq$ &nbsp&nbspA+B->A,C->A (modifica stesso registro)
	3.  &nbsp&nbspA+B->A;B->D &nbsp&nbsp $=$  &nbsp&nbspA+B->A,B->D (permessa uscita in contemporanea, "si ricordi il significato di segnali a livelli")
	4.  &nbsp&nbspA+B->A;B+C->D &nbsp&nbsp $=$ &nbsp&nbspA+B->A;B+C->D (purchè presenti 2 reti di calcolo)
	5.  &nbsp&nbspA+B->A;C->B &nbsp&nbsp$=$ &nbsp&nbspA+B->A;C->B (il riferimento a B rimane stabile per tutto il ciclo di clock)
	6.  &nbsp&nbspA+B->A;A->B &nbsp&nbsp$\neq$ &nbsp&nbspA+B->A,A->B (il valore di A in A->B è il risultato di A+B nel sequenziale, ma non nel paralleno)
	7.  &nbsp&nbspA->TEMP;B->A;TEMP->B &nbsp&nbsp$=$ A->&nbsp&nbspTEMP,B->A,TEMP->B

    Più formalmente, valogono le **Condizioni di Bernstein** per la trasf. da sequenziale a parallela
	- Data la computazione sequenziale:
	&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp $f_1:D_1 \to R_1 ; f_2 D_2 \to R_2$
	- dove $f_i$ sono funz. di dominio $D_i$ e rango $R_i$, la computazione parallela:
	&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp $f_1 : D_1 \to R_1,f_2:D_2\to R_2$
	
	- è equivalente se:
	&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp $R_1 \cap D_2 = Ø$ e $R_1 \cap R_2 = Ø$
	
	
   In un modello *asincrono* di computazione, esente di ipotesi sulla durata temporale delle operazioni e sui loro istanti di inizio, deve valere anche la condizione: &nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp$R_2 \cap D_1 = Ø$
   
   Occorre ribadire che Bernstein serve solo per strasformare una descrizione sequenziale in parallela. 
   È possibile scrivere direttamente in paralleo saltando la descrizione sequenziale.
   
  1. **Parallelismo nelle microoperazioni e nelle condizioni logiche**
  Partendo dalla descrizione sequenziale, o dal microprogramma ad alto livello, 
  possiamo ora semplificare, riordinando le operazioni di trasferimento tra registri, così da:
     1. Da sostituire condizioni logiche di tipo *if then else* con condizioni logiche *case* ; per generalizzare,  sostituire condizioni logiche *case* con altre condizioni logiche *case* con più variabili di condizionamento
	 2. In modo da aumentare il parallelismo di micooperazioni
	 
	 Entrambe le tecniche devono rispettare le condizioni di Bernstein per i microprogrammi.
	 es tecnica 2: &nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbspA+B->A; **if** $M_0$ = 0 **then** C+1->C **else** C-1->C
	 
	 Può essere adattata in:
	 &nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbspi. ($M_0$ = 0)A+B->A, C+1->C,i+1;($M_0$=1)A+B->A,C-1->C,i+1
	 
# Componente logico di memoria
###### Realizzazione logica
Nella realizzazione di unità di elaborazione è spesso conveniente, o necessario, fare uso di un ulteriore componente logico "*standard*": il componente memoria. 

In versione **RAM**, una memoria è definita come un array unidimensionale M di registri su cui sono definite le seguenti operazioni fondamentali:
- *lettura* sull'uscita *out* del contenuto della cella di indirizzo i:  
	*out* = M[ i ];
- *scrittura* del valore presente sull'ingresso *in* nella locazione di indirizzo i: M[ i ] : = *in*. 

  ![[Pasted image 20210617214215.png]]

Possiamo immaginare tale struttura più dettagliata.

![[unknown.png]]

- il *decoder* **S** all'ingresso ha come ingressi primari il segnale di controllo $\beta$  per l'abilitazione alla scrittura, mentre gli ingressi secondari sono i bit dell'indirizzo. L'ingresso *in* viene collegato a tutti gli ingressi dei registri, perciò se $\beta = 1$, il valore di *in* viene scritto solo nel registro indirizzato;
- il *multiplexer* **K** all'uscita ha come ingressi primari le uscite dei registri e come ingressi secondari (le variabili di controllo) i bit dell'indirizzo; questo realizza le operazioni di *lettura*.

In versione **ROM**, è presente solo il commutatore di uscita.

### 8 - Tecnologie integrate
La caratteristica delle tecnologie integrate è quella di cercare di realizzare su un chip, il maggior numero possibile di componenti di una unità o di un intero sottosistema.
Il problema dell’integrazione consiste nella ricerca del miglior compromesso tra area e tempo di elaborazione. L'area del chip è proporzionale al numero di elementi da integrare e il perimetro del chip è proporzionale al numero di bit presenti aall’interfaccia (pin) dell’unità. All'aumentare delle dimensioni del chip aumenta quindi la capacità di interfacciamento. 
Bisogna fare attenzione che all' aumento di area deve effettivamente corrispondere anche un aumento proporzionale nel numero dei componenti da integrare, se l’impaccamento dei componenti non fosse almeno proporzionalmente più denso, si otterebbe un aumento dei ritardi interni( ritardi dei collegamenti e ciclo di clock).

### 9 - Parte controllo microprogrammata
Quando il numero di microistruzioni è relativamente alto, la progettazione della PC rappresenta un problema di complessità notevole. La Realizzazione microprogrammata permette di ridurre la complessità di progettazione e di rendere la struttura della PC più regolare.
Consiste nel memorizzare gran parte del microprogramma in una memoria di controllo(MC), con la quale implementare in gran parte le funzioni di transizione delle uscite PC(bandierina, aldinucci falliito) di transizione dello stato interno PC. La parte restante di tali funzioni viene delegata ad una rete combinatoria (Rete di Condizionamento).
Nel caso della PC di Mealy con microlinguaggio PS, si tratta di memorizzare in MC tutte le coppie: *microperazione, indirizzo successivo*.


Il registro di stato RC e le variabili di condizionamento sono gli ingressi della Rete di Condizionamento, la cui uscita indirizza MC.

Schema di PC microprogrammata, modello di Mealy:
![[Pasted image 20210617220112.png]] 

Ogni parola di controllo contiene, la configurazione dei valori delle variabili di controllo {$\alpha$, $\beta$} necessari ad eseguire la microoperazione e  l’indirizzo di microistruzione successiva che viene inviato all’ingresso del registro di stato del controllo RC ($K_{RC}$). L’implementazione microprogrammata risolve i problemi di complessità della progettazione e della struttura di PC, ma ad una minore velocità: PC ha un ritardo più grandre rispetto ad uno realizzato con rete conbinatorica "classica" (ciclo di clock più lungo).
Il problema si può risolvere usando una tecnologia più avanzata con quindi costi maggiori.

### 10 - Cenno ai modelli Moore-Moore e Moore-Mealy

Le prestazioni dipendono anche dal modello di microprogrammazione.
Oltre al modello Mealy\-Moore, c'è il modello Moore\-Mooreche, genera un maggior numero di cicli di clock per uno stesso algoritmo, ma di una minore lunghezza perchè è  	maggiore il grado di sovrapposizione tra gli intervalli di stabilizzazione delle funzioni della PC e quelle della PO

Al modello Moore\-Moore corrisponde il microlinguaggio TS (Transfer Structured)
ha la struttura: 

etichetta.	 &nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbspmicroperazione
&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp**case** condizione logica *of*
&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbspvalore 1: indirizzo successivo 1;
&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp. . . 
&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbspvalore k: indirizzo successivo k;

													

Questa unità impiega un maggior numero di cicli di clock rispetto al modello Mealy\-Moore(T = 2.5 $\tau_1$) in quanto alcune *nop* sono ineliminabili nel modello Moore\-Moore. La minore lunghezza del ciclo di clock attenua la differenza e in alcuni casi rende minore il tempo di elaborazione nel caso Moore\-Moore. 
Con una PC di Moore, è anche possibile avere una PO di Mealy: il modo più semplice di vedere una PO di Mealy è quello di anticipare il prelievo delle variabili di condizionamento all’ingresso dei registri (“Moore anticipato”).

Nel modello Moore\-Mealy ottiene lo stesso numero di cicli di clock del caso Mealy\-Moor quindi i due modelli sono completamente equivalenti e interscambiabili.





