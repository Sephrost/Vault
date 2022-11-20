### Il problema
E' possibile descrivere il problema della **corrispondenza di Post** o **PCB** come una sorta di puzzle formati da diversi domino della forma 

![[Pasted image 20221114143724.png]]

L'obiettivo e' creare una lista di questi domino, anche con ripetizioni tali per cui ci sia un **match**.

> Si ha un match quando la stringa composta dalla meta' superiore di questi domino e' uguale a quella inferiore

Un'esempio di match e' 

![[Pasted image 20221114144057.png]]

> Inoltre per alcuni insiemi non e' possibile trovare un match.

### Definizione formale del problema
Sia $P$ un'insime di domino della forma $P=\{[\frac{t_1}{b_1}],[\frac{t_2}{b_2}],\dots,[\frac{t_k}{b_k}]\}$ e un match e' una sequenza $i_1,\dots,i_t$ dove $t_{i_1},\dots,t_{i_t}=b_{i_1},\dotsb_{i_t}$ allora 
$$PCP=\{<P>|P\;e'\;un'istanza\;del\;problema\;della\;corrisppondenza\;di\;post\;con\;un\;match\}$$

### Dimostrazione dell'indecidibilita'
Sia $R$ un decisore per $PCP$, supponiamo quindi per assurdo che esista un decisore $S$ per $A_{TM}$