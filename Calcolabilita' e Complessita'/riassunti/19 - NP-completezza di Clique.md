### Clique
> Un *clique* e' un insieme di $k$ vertici di un grafo indiretto, dove ogni due nodi sono connessi da un'arco

Il problema e' determinare se un grafo contiene una *clique* di una certa dimensione é cosí definito
$$CLIQUE=\{<G,k>|\,G\;e'\;un\;grafo\;indiretto\;con\;una\;k-clique\}$$

Si puó dimostrare che é NP-completo mostrando un a riduzione da $3SAT$.
## Dimostrazione
Sia $\phi$ una formula booleana della forma normale 3-congiuntiva(ogni clausola ha esattamente 3 letterali) con $k$ clausole. La riduzione genera quindi la coppia $<G,k>$, dove $G$ é un **grafo indiretto** e $k$ é il numero di clausole, dette anche **triple**, poiché composte dai 3 vertici che ne rappresentano i letterali, e rappresentante una clausola di $\phi$.

Ogni vertice del grafo ha un arco verso ogni altro vertice, con alcune eccezioni:
1. Non ci sono archi tra vertici di una stessa tripla
2. non ci sono archi tra vertici corrispondenti ad un letterale ed al suo negato( anche se appartengono a clausole differenti)

Dimostriamo che $\phi\in3SAT\iff <G,k>\in Clique$:
Se $\phi$ avesse un'assegnamento che lo soddisfa allora **ogni clausola** di $\phi$ ha **almeno** **un** letterale **vero**.

Prendiamo in considerazione quindi **un letterale vero** per **clausola**, i nodi selezionati corrisponderebbero a un **sottografo** rappresentante una $k-clique$, poiché ogni letterale appartiene a una tripla(clausola) diversa, e non avente vertici tra un letterale e il suo negato(per il punto $2$ delle eccezioni) mantenendo inoltre un'assegnamento valido.

Poiché ogni clausola in questo caso é soddisfatta possiamo conscludere che $\phi$ sarebbe soddisfacibile e quindi $CLIQUE$ é **NP-completo** poiché $CLIQUE\in NP$ ed esiste una riduzione da ogni linguaggio $NP$ a $3SAT$ e quindi a $CLIQUE$.
