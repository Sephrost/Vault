### Alberi 
#### albero libero
Un albero libero e' un grafo connesso aciclico.

Non e' presente una gerarchia, fino a quando non introduciamo il conetto di radice dell'albero.

Un'insieme di alberi forma una foresta.

#### Albero radicato
Un'albero radicato e' un albero libero in cui di individua un nodo privilegiato detto radice.

Una foglia e' un nodo che non ha discendenti.

Un nodo che non e' una fogla si dice interno

#### Orientamento dell'albero
Nel caso in cui l'albero sia un grafo orientato allora:
- Se il verso va dalla radice verso le foglie e' detto **sorgente**
- Se parte dalle foglie e risale verso la radice di dice **pozzo**

##### Cammino 
Un cammino e' una sequenza di archi ciascuno incidente nel vertice successive.

Il cammino segue sempre il verso dell'arco.

Un cammino massimale e' un cammino che va dalla radice ad una foglia. E' anche chiamato ramo.

##### Livello
I livelli sono insiemi di nodi.

L'altezza e' la massima distanza dalla radice di un livello non vuoto.

L'altezza di un albero e' la massima distanza dalla sua radice.

##### Grado
Il grado di un vertice e' il numero dei suoi figli.

Una foglia ha sempre grado 0.

Il grado di un'albero finito e' il massimo grado dei suoi nodi.

#### Alberi ordinati
Un albero si dice ordinato quando tutti i suoi livelli sono ordinati.

#### Albero binario posizionale
Un'albero ordinato si dice posizionale se:
- Puo' essere vuoto
- Se tiene conto della posizione dei suoi sottonodi

Si utilizza quindi il concetto di sottoalbero sinistro e destro.

