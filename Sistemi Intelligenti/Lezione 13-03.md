### Ricerca bidirezionale
Nella ricerca bidirezionale venegono eseguite contemporaneamente una ricerca fw dallo stato iniziale e una ricerca bw dallo stato finale.

Dobbiamo quindi tener conto della frontiera delle due ricerche, e otteniamo una soluzione se le due frontiere collidono.

Per rendere la ricerca backward simile a quella fw viene indicato uno sttao fittizio che non corrisponde a nessun goal, ma collegato a tutti gli stati target.

É inoltre necessario invertire la funzione successore per la ricerca bw. Questo risulta difficile poiché piú risultati della funzione successore possono portare allo stesso stato.

Per quanto riguarda la complessitá, notiamo che $b^{\frac{d}{2}}+b^{\frac{d}{2}}$ é molto piú piccolo di $b^d$ .

### Confronto fra trategie di ricerche blind
![[Pasted image 20230313124618.png]]

## Stategie di ricerca informata
> Sono strategie di ricerca nei quali vengono usate informazioni sulla posizione dello stato obiettivo nell'albero.

L'informazione é presente sotto forma di **funzione euristica** $h(n)$, dove $n$ é un nodo dell'albero di ricerca, e che restituisce il costo stimato del cammino piú economico da $n$ ad uno degli stati obiettivo.

### Ricerca greedy
é una forma di ricerca in ampiezza che espande il nodo con $h(n)$ minore, che orrisponde al nodo piú vicino alla soluzione.

In questa ricerca la funzione di valutazione é uguale all'euristica: $f(n)=h(n)$.

Questa ricerca é efficente ma non efficace.

### $A^*$
É il piú comune algoritmo di ricerca informata.

É un tipo di ricerca in ampiezza che usa la funzione di valutazione 
$$f(n)=g(n)+h(n)$$
dove 
- $g(n)$ é il costo del cammino dallo stato iniziale al nodo $n$
- $h(n)$ é il costo stimato per il cammino minimo dallo stato $n$ ad uno stato obiettivo

$A^*$ é una ricerca di costo ottimale. Usiamo la notazione $g^*(n)$ per indicare il cammino di costo ottimale dalla radice ad $n$, e $h^*(n)$ per indicare il cammino di costo ottimale da $n$ al piú vicino stato obiettivo.

%%inserire algoritmo%%

