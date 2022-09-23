%%Recuperare introduzione, grazie trenitalia%%
## Macchina di Turing multi nastro
Una macchina di Turin multi nastro e' una macchina di Turing con diversi nastri, ognuno dei quali puo' essere letto e scritto.

La funzione di transizione diventa la seguente
$$δ: Q\times Γ^k\to Q\times Γ^k\times\{L,R,S\}^k$$
dove $k$ e' il numero di nastri.

E' possibile dimostrare che una macchina a piu' registri ne ha una a singolo equivalente.

![[Pasted image 20220921101942.png]]

Immaginando che il dato di partenza sia una sringa $w=w_1\dots w_s$ partizioniamo il nastro usando i simbolo # come separatore.

Avremo quindi una posizione iniziale del tipo

![[Pasted image 20220921102125.png]]

> Gli asterischi indicano il valore attuale del segmento di nastro(memoria)

Le macchine a singolo nastro sono molte piu' lente poiche per accedere alle diverse aree di memoria dovremo spostare l'intero nastro, questo pero' non intocca la deicibilita' della macchina.

%%Aggiungere punto 3 pagina 177%%

