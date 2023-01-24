### Problemi di classe NP
#### Esempio: la traiettoia Hamiltoniana
$$HAMPATH=\{<G,s,t>|G\;e'\;diretto\; con\;un\;cammino\;\;hamiltoniano\;tra\;se\;t\}$$
Un cammino hamiltoniano e' un cammino che tocca tutti i punti di un grafo una sola volta.

![[Pasted image 20221109091558.png]]

Un modo semplice per risolvere il problema e' provare tutti i cammini possibili e verificare che sia una cammino di hamilton, con tempo esponenziale (dato dalla forza bruta).

La traiettoia hamiltoniana e' **polinomialmente verificabile**.
In questo caso dato un cammino posso controllare che sia un cammino di hamilton in tempo polinomiale.

> *Verificare* l'esistenza di un cammino di hamilton e' piu' facile di *determinarla*

### Verificatori 
Un verificatore per un linguaggio $A$ e' un algoritmo $V$, dove
$$A=\{w\,|\,V\;accetta\;<w,c>\;per\;qualche\;stringa\;c\}$$
Misuriamo il tempo di verifica per i soli termini di lunghezza $w$, quindi un **verificatore di tempo polinomiale** termina in tempo polinomiale per una lunghezza $w$.
$c$ rappresenta quindi una sorta di certificato, che rappresenta le condizioni aggiuntive per appartenere ad $A$.

L'algoritmo espolara inoltre $w$ un passo alla volta, come le *TM*.

> Un linguaggio $A$ e' quindi **polinomialmente verificabile** se esiste un verificatore polinomiale

###### Esempio di certificato per il cammino di Hamilton
Un certificato per la stringa $<G,s,t>\in HAMPATH$ e' un cammino di hamillton da $s$ a $t$.

### Definizione
**NP** e' la classe di linguaggi che hanno un verificatore di tempo polinomiale

Un linguaggio $A\in NP$ se e solo se é deciso da una *TM* polinomiale non deterministica.

##### Esempio di problema NP - Clique
> Un *clique* e' un insieme di $k$ vertici di un grafo indiretto, dove ogni due nodi sono connessi da un'arco

Il problema e' determinare se un grafo contiene una *clique* di una certa dimensione
$$CLIQUE=\{<G,k>|\,G\;e'\;un\;grafo\;indiretto\;con\;una\;k-clique\}$$
Dimostriamo che e' un problema di classe NP.

> Un modo per dimostrarlo e' definire la condizione di clique come certificato.

Sia quindi $V$ il verificatore per $CLIQUE$:
Su input $<<G,k>,c>$
1. Vetrifichiamo che $c$ sia un sottografo di $G$ con $k$ nodi
2. Verifichiamo che $G$ contiene tutti gli archi che collegano tutti i nodi di $c$
3. Se $1$ e $2$ sono verificati, $accetto$, atrimenti $rifiuto$

Ogni passo viene ripetuto una volta sola, e sono tutte operazioni tempo polinomiali. $V$ è termina in tmepo polinomiale, quindi $CLIQUE\in NP$.

#### Esempio di problema NP
Sia 
$$SUBSET-SUM=\{<S,t>|S=\{x_1,\dots,x_k\}\;e\;per\;qualche \;sottotineme\;di\;S\;\Sigma y=t\}$$
dimostriamo che il problema e' NP.

> Quindi il problema e' la massimizzazione 
> Un esempio e' $<\{4,11,21,27\},25>\in SUBSET-SUM$ poiche' $4+21=25$ e $t=25$

Costruiamo quindi il verificatore $V$ per $SUBSET-SUM$
Su input $<<S,t>,c>$
1. Controlliamo se $c$ e' un'insieme di numeri la cui somma sia $t$
2. Controlliamo se $S$ contiene tutti i nuemri in $c$
3. Se entrambi $1$ e $2$ sono verificati, $accetto$, altrimenti $rifiuto$
> Il certificato sara' quindi il sottoinsieme stesso.
> Inoltre il problema e' NP poiche dati $k$ elementi in $S$, abbiamo $2^k$ possibilita'

Ogni passo viene ripetuto una volta sola, e sono tutte operazioni tempo polinomiali. $V$ è termina in tmepo polinomiale, quindi $SUBSET-SUM\in NP$.