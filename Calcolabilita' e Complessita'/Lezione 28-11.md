#### Esempio algoritmo NP - VERTEX-COVER
Sia 
$$VERTEX-COVER=\{<G,k>|G\;e'\;un\;grafo\;indiretto\;con\;k\;vertici\;collegati\;a\;tutti\;gli\;archi\}$$
Dimostriamo  che e' NP.

Come certificato usiamo il numero di nodi $k$, e dimostriamo che $3SAT$ e' polinomialmente riducibile a $VERTEX-COVER$, convertendo una forumla 3-congiuntiva $\phi$ ad un grafo $G$ con $k$ vertici senza sapere se $\phi$ e' soddisfacibile.

La conversione avviene come segue:
- per ogni variabile $n\in \phi$ produciamo un arco che connette due nodi, assegnando un gadget al nodo avente la coppia $x$ e $\not x$
	- Se $x$ e' vera allora il nodo e' selezionato per la copertura


