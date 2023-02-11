## Decidibilitá
Ricordiamo che un liguaggio é decidibile sé la terminazione per l'accettazione di una stringa é garantita, e quindi una *TM* é in grado di decidere sempre sé una stringa appartiene al suo linguaggio.

Definiamo quindi il problema dell'accettazione per gli automi a stati finiti nella seguente maniera, attraverso un linguaggio
$$A_{DFA}=\{<B,w>|B\;é\;un\;DFA\;che\;accetta\;la\;stringa\;in\;input\;w\}$$
> Il problema di verificare se un DFA $B$ accetta $w$ é lo stesso di verificare se $<B,w>$ appartiene al linguaggio $A_{DFA}$.
> Inoltre mostrare che un linguaggio é decidibile é la stessa cosa di mostrare che un problema computazionale é decidibile.

### Decidibilitá di $A_{DFA}$
Dimostramo ora che $A_{DFA}$ é decidibile, e per far cioó bastra mostrare una *TM* $M$ che decide $A_{DFA}$, e che opera come segue:
Su input $<B,w>$, dove $B$ é un $DFA$ e $w$ una stringa:
1. Simulo $B$ su $w$.
2. Se la simulazione termina in uno stato di accettazione, $accetto$, altrimenti $rifiuto$.

Vista la nozione di decidibilitá possiamo osservare che un DFA termina sempre per ogni input, poiché la terminazione della computazione é vincolata al termine della stringa stessa. Possiamo quindi concludere che il linguaggio $A_{DFA}$ é decidibile.
### Altri linguaggi decidibili
#### $A_{REX}$
Definamo $A_{REX}$ come segue
$$A_{REX}=\{<R,w>|R\;é\;un'espressione\;regolare\;che\;genera\;w\}$$
Per dimostrare che é decidibile mostriamo una *TM* $D$ che decide il problema. $P$ computa come segue:
Su input $<R,w>$:
1. Converte l'espressione regolare $R$ in un'$NFA$ equivalente $A$
2. Eseguiamo una *TM* universale $N$ con $A$ come subroutine su input $<R,w>$
3. Se $N$ accetta, $accetto$, se $N$ rifiuta, $rifiuto$.

Poiché un'NFA termina sempre per ogni input ed é in grado di determianre se una stringa appartiene o no al suo linguaggio, $A_{REX}$ é decidibile.
#### $E_{DFA}$
Definiamo $E_{DFA}$ come segue
$$E_{DFA}=\{<A>|A\;é\;un\;DFA\;e\;L(A)=0\}$$
Dimostriamo che é decidibile.

Un DFA acceta una stringa sé e solo sé é possibile raggiungere uno stato di accettazione, per verificare questa condizione definiamo una *TM* $D$ che computa come segue:
Su input $<A>$, dove $A$ é un DFA:
1. Marchiamo lo stato iniziale di $A$
2. Ripetiamo finché nessun nuovo stato viene marchiato
	1. Marchiamo ogni stato raggiunto partendo da uino stato giá marchiato
3. Se nessuno stato di accettazione é marchiato, $accetto$, altrimenti $rifiuto$

