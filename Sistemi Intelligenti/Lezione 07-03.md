### Ricerca a costo uniforme
> Non é l'algoritmo di Dijkstra.

Se i costi delle azioni non sono uguali é meglio applicare questa strategia.

L'idea é applicare la ricerca in ampiezza a cammini di costo uniforme.

La complessitá della ricerca a costo uniforme é $O(b^{1+|\frac{C^*}{\epsilon}|})$ , con $\epsilon>0$ che ne rappresenta il limite inferiore, ovvero il costo minimo delle azioni. inoltre $C^*$ é il costo della soluzione ottima. 

### Ricerca in profonditá
La ricerca in profonditá estende la ricerca dal nodo piú profondo nella frontiera.

> in caso di uno spazio di stati ciclico puó risultare in un loop.

É preferibile usare la ricerca in profonditá quando la complessitá spaziale é importante, poiché richede meno memoria in quando non teniamo conto degli stati esplorati.

La complessitá temporale é legata al numero di nodi dell'albero , risultando in $O(bm)$, dove $b$ é il fattore di diramazione e $m$ é la profonditá massima dell'albero.
La complessitá spaziale é uguale a quella temporale.

#### Ricerca in profonditá con backtracing
Con questa variante viene generato solo un successore per volta, e ogni nodo parzialmente espanso ricorda quale successore bisogna generare dopo.

Inoltre il successore viene generato modificando lo stato corrente piuttosto che allocare risorse per un nuovo stato, riducendo la complessitá spaziale a $O(m)$.

#### Ricerca con profonditá limitata
> é un modo per evitare la ricerca su un ramo infinito.

Questo é possibile fornendo una profonditá massima $l$, e trattare tutti i nodi alla stessa profonditá come se non avessero successori.

Questo permette di ridurre la complessitá temporale a $O(b^l)$, e la complessitá spaziale a $O(bl)$.

> Questa implementazione portrebbe rendere impossibile raggiungere una soluzione.

Per poter scegliere un limite si possono usare le informazione sul problema, ma fondamentalmente non é possibile decidere a priori un limite adeguato senza conoscere la soluzione al problema.

##### Iterative deepening depth first search
Un modo per scegliere un buon limite puó esserequello quindi di tutti i valori fino a quando una soluzione non viene trovata.

![[Pasted image 20230307123658.png]]

La complessitá temporale é quindi $O(b^d)$ quando é presente una soluzione, e $O(b^m)$ quando questa non esiste,il costo di esplorare l'intero albero.

