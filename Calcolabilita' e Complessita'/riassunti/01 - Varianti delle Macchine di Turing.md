## Macchina di Turing multi-registro
Una **macchina di Turing multi-registro** é una macchina di Turing con diversi nastri, ognuno dei quali ha una propria testina, e puo' essere letto e scritto.

### Funzione di Transizione
La funzione di transizione diventa la seguente
$$δ: Q\times Γ^k\to Q\times Γ^k\times\{L,R,S\}^k$$
dove $k$ é il numero di nastri.

### Equivalenza con le Macchine di Turing a nastro singolo
É possibile dimostrare che una macchina a piú registri ne ha una a singolo equivalente.

> Due macchine sono equivalenti se riconoscono lo stesso linguaggio

Per convertire una TM $M$ multinastro ad una a nastro singolo $S$ é sufficiente partizionare il nastro in $k$(il numero di nastri di $M$) partizioni separate dal delimitatore **#**,  

![[Pasted image 20220921101942.png]]

Immaginando che il dato di partenza sia una sringa $w=w_1\dots w_s$ partizioniamo il nastro usando i simbolo # come separatore.

Avremo quindi una posizione iniziale del tipo

![[Pasted image 20220921102125.png]]

> Gli asterischi indicano il valore attuale del segmento di nastro(memoria)

> Le macchine a singolo nastro sono molte piú lente poiche per accedere alle diverse aree di memoria dovremo spostare l'intero nastro, questo pero' non intocca la decidibilitá della macchina.

## Macchine di Turing non deterministiche

Una **Macchina di Turing non deterministica** é una TM che, in ogni momento della computazione, puó decidere tra diverse possibilitá.

### Funzione di Transizione
La funzione di transizione diventa la seguente
$$\delta:Q\times\Gamma\to P(Q\times\Gamma\times\{L,R\})$$
dove $P$ rappresenta l'insieme di stati producibili da una data configurazione.

### Computazione di una ndTM
La computazione di una macchina di Turing non deterministica é un'**albero**, con i rami che rappresentano le diverse possibilitá prodotte dalla macchina.

Se un ramo porta allo stato di accettazione, la macchina accetta l'input.

### Equivalenza con le Macchine di Turing deterministiche
É possibile simulare ogni TM non deterministica $N$ con una TM  deterministica $D$, facendo provare a $D$ tutti i **possibili cammini** generati da $N$, e supponendo che ogni nodo sia una configurazione, dove la radice é il nodo di partenza. 

Andiamo quindo a cercare uno stato di accetazione con una $BFS$(*breadth-first search*), garantendo quindi che $D$ esplori l'intero albero finché non trova uno stato di accettazione.

###### Dimostrazione
Supponiamo che $D$ abbia 3 nastri:
- il **primo** per contenere la **stringa** di **input**, che non verrá alterata
- il **secondo** contiene una copia del nastro di $N$ per qualche ramo(durante la computazione)
- il **terzo** tiene traccia della posizione di $D$ nell'abero generato da $N$

![[Pasted image 20221016145107.png]]

Ogni nodo dell'abero puó avere al massimo $b$ figli, quindi assegnamo ad ogni nodo un **indirizzo** rappresentato da una stringa nell'alfabeto $\Gamma_b=\{1,2,\dots,b\}$ (per esempio l'indirizzo $123$ rappresenta quello raggiungibile dal cammino primo figlio $\to$ secondo figlio $\to$ terzo figlio partendo dalla radice). Se una scelta non é possibile l'indirizzo non é valido.

Il terzo nastro contiene quindi una stringa di $\Gamma_b$, che rappresenta il ramo che sta computando $N$. 

$D$ di comporta quindi nella seguente maniera:
1. Inizialmente il nastro $1$ contiene $w$, $2$ e $3$ sono vuoti
2. copiamo $1$ su $2$ e inizializziamo $3$ ad $\epsilon$ (la radice)
3. Usiamo $2$ per simulare $N$ con input $w$ su un suo ramo: prima di ogni step consulta $3$ per decidere che scelta fare tra le possibili.
	- Se non rimangono simboli su $3$ ,la scelta non-deterministica non é valida o incontriamo una configurazione rifiutata proseguiamo al punto 4
	- Se incontriamo una configurazione accettatta, accettiamo allora anche l'input
4. Rimpiazziamo la stringa in $3$ con la successiva e ritorniamo al punto 2


## Enumeratori
Un'**enumeratore** é una macchina di Turing a singolo nastro collegata ad una stampante(che rappresentai il secondo nastro) che puo' usare per stampare delle stringhe.

![[Pasted image 20220928090856.png]]

Essa restituisce un flusso infinito di dati.

L'enumerator stampa tutte le stringhe con radice intera. Puo' inoltre generare ripetizioni, e le stringhe possono essere generate in qualunque ordine.

