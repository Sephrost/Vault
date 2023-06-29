La soluzione ad un problema, per un agente come per noi, non é sempre ovvia.
Un'agente risolutore di problemi deve essere in grado di pianificare per poter raggiungere una soluzione, cercandola.

### Elementi di un problema di ricerca
Un problema di ricerca pó essere definito come un'insieme di:
- **stati**, in cui puó trovarsi l'ambiente
	- di questi stati vi sono uno stato iniziale, in cui l'agente si trova, e degli stati obiettivo, in cui il problema é risolto
- Una serie di **azioni**, che agiscono l'ambiente
- Una **funzione di transizione**, che descrive come un'azione influisce su uno stato
- una **funzione costo**, che restituisce il costo che comporterebbepassare da uno stato ad un'altro data un'azione

Questo problema puó essere rappresentato come un **grafo**, dove i vertici sono gli stati e le azioni sono gli archi. Una soluzione é quidni un cammino dallo stato iniziale ad uno dei possibili stati obiettivo, e una soluzione é ottima se il suo costo é minimo, ovvero se la somma delle azioni é minima.

Per cercare una soluzione possiamo usare degli algoritmi di ricerca, che superimpongono un'albero di ricerca ad un grafo. 

### Criteri di valutazione
Le performance di questi algoritmi si possono misuare attraverso 4 criteri:
- **completezza**: ovvero sé esiste una soluzione, allora é in gradi di trovarla
- **ottimalitá**: se trova sempre la soluzione di costo minimo
- **complessitá temporale**: quanto tempo impiega a trovare una soluzione
- **complessitá spaziale**: quanto spazio impiega a trovare una soluzione

### Classificazione
Gli algoritmi di ricerca si dividono in due categorie:
- Strategie di ricerca **non informate**: dove l'unica informazione disponibile é la descrizione del problema
- Strategie di ricerca informate: dove viene untilizzata un'euristica oltre alla descrizione del problema

Le strategie di ricerca che abbiamo visto a lezione sono:
Ricerca in ampiezza(BFS): espande tutti i nodi su uno stesso livello prima di passare al successivo. Puó far ció grazie all'utilizzo di una coda FIFO a cui un nodo viene aggiunto appena dopo essere stato scoperto. Questo algoritmo é ottimale per i problemi a costo uniforme, poiché si assicura di aver esplorato un livello prima di passare al successivo. Presenta inoltre complessitá, sia spaziale che temporale, $O(b^d)$, ovvero il branching factor alla profonditá massima, poiché nel caso peggiore deve esplorare l'intero albero e anche tenerlo in memoria.

Ricerca in profonditá: espande sempre il nodo piú profondo che non é una foglia. la complessit;a temporale non é migliore di quella della BFS, ma quella spaziale é soltanto $O(bd)$, poiché non dobbiamo tenere tutto l'albero in memoria.

DFS a profonditá limitata: la DFS ha il brutto vizio di perdersi per cammini infiniti. Per ovviare al problema possiamo impostare una profonditá massima da esplorare, e trattare tutti i nodi a quella profonditá come delle foglie. Questo rende la complessitá temporale O(b^l) e quella spaziale O(bl).
 
Iterative deepening DFS: La profonditá limitata fa sorgere un'altro problema, scegliere una buona profonditá massima: se la soluzione, per esempio, si trova a profonditá l+1 non verrá mai trovata. Una soluzione é quindi provare tutte, incrementando iterativamente la profonditá massima, fino a quando una soluzione non é trovata. Per certti versi é molto simile ad una BFS, presentando quindi complessitá temporale O(b^d) e profonditá spaziale O(bd).

Ricerca bidirezionale: anziché esplorare tutto l'albero dalla radice, possiamo esplorarlo in avanti dalla cima e all'indietro dallo stato obiettivo. Se le due frontiere collidono significa che c'é una soluzione. Questo permette di esplorare l'albero in O(b^n/2)

Passando agli algoritmi di ricerca informata, utilizzano un qualche tipo di informazione aggiuntiva, che costituisce l'euristica h, per esempio la distanza da uno stato allo stato obiettivo.
Gli algoritmi di ricerca informata che abbiamo visto sono: 
Greedy Best FS: é una BFS dove l'euristica viene utilizzata per decidere quale stato espandere, ovvero quello che appare piú vicino allo stato obiettivo. Come algoritmo non é il massimo poiché non sempre il nodo con funzione euristica inferiore é la scelta migliore.

A*: questo algoritmo usa come euristica la distanza di un nodo dallo stato obiettivo, come greedy BFS, ma la somma al costo del cammino dalla radice al nodo n. L'euristica é quindi il costo della soluzione migliore passante per n. 
A* é ottimo se l'euristica é ammissibile, ovvero sovrastima il costo del cammino verso lo stato obiettivo.
> Un'euristica é detta ammissibile quando $\forall n,h(n)\le h^* (n)$, dove $h^*(n)$ é il costo minimo reale per raggiungere il nodo obiettivo a partire dal nodo n.

A* é una ricerca in ampiezza, che mantiene in memoria tutti i nodi espolorati

.|Ricerca in ampiezza|Ricerca in profonditá|Depth-limited|Itertive deeperning|Bidirezionale|Greedy|A*
--|--|--|--|--|--|--|--
Tempo|$O(b^d)$|$O(b^d)$|$O(b^l)$|$O(b^d)$|$O(b^{d/2})$|$O(V)$|
Spazio|$O(b^d)$|$O(bd)$|$O(bl)$|$O(bd)$|$O(b^{d/2})$|$O(V)$|$O(b^d)$