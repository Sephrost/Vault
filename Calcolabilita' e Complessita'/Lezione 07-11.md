#### Esempio di problema P
Voglio controllare che l' esistenza di un cammino in un grafo sia polinomiale -> $Path\in P$

Dato un gtafo $G$ controlliamo tutti i possibili cammini da due vertici $s$ e $t$. Un cammino possibile e' una sequenza di nodi di $G$, con lunghezza al massimo $m$(il numero di vertici). Ma il numero di possibili cammini e' $m^m$, che e' esponenziale.

Per ottenereun tempo polinomiale dobbiamo quindi evitare la forza bruta(*bruteforce*). Per migliorare la ricerca possiamo usare la ricerca in ampizza, marchiando i nodi raggiungibili da $s$ attraverso cammini diretti di lunghezza $1,2,\dots ,m$, limitando il tmpo a polinomiale
##### Prova
Dato un input $<G,s,t>$, dove $G$ e' un grafo e $s$ e $t$ sono vertici
1. Etichetto il nodo $s$
2. Ripetiamo il seguente passaggio fino a che tutti i nodi non sono etichettati
	1. Ogni volta che trovo un arco $<a,b>$ con $a$ etichettato, etichetto anche $b$
3. Se $t$ e' etichettato, $accetto$, altrimenti $rifiuto$

La tappa $1$ e $3$ vengono eseguiti una sola volta, mentre la subroutine 2 viene eseguita $m$ volte, quindi la complessita' dell'algoritmo e' $2n\times n^2=2n^3$.
> Il caso peggiore avviene se tutti i nodi sono connessi e il grafo e' indiretto 

$REALPRIME=\{<x,y>|x\;e\;y\sono\;primi\;tra\;loro\}$