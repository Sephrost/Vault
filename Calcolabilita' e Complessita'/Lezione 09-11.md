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

##### Esempio di problema NP
> Un *clique* e' un insieme di $k$ vertici di un grafo indiretto, dove ogni due nodi sono connessi

Il problema e' determinare se un grafo contiene una *clique* di una certa dimensione
$$CLIQUE=\{<G,k>|\,G\;e'\;un\;grafo\;indiretto\;con\;una\;k-clique\}$$
Dimostriamo che e' un problema di classe NP.

> Un modo per dimostrarlo e' definire la condizione di clique come certificato.

Sia quindi $V$ il verificatore per $CLIQUE$:
Su input $<<G,k>,c>$
1. Vetrifichiamo che $c$ sia un sottografo di $G$ con $k$ nodi
2. Verifichiamo che $G$ contiene tutti gli archi che collegano tutti i nodi di $c$
3. Se $1$ e $2$ sono verificati, $accetto$, atrimenti $rifiuto$
