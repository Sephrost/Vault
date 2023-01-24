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
La dimostrazione si effettua per riduzione da $A_{TM}$ attraverso l'accettazione di storie computazionali poiche' per ogni *TM* $M$ e input $w$, possiamo costruire un'istanza $P$ dove un match e' l'accettazione di una storia computazionale.

Per far cio' iniziamo con un domino che ha nella parte inferiore la configurazione iniziale e nella superiore la stringa vuota, e aggiungiamo a $P$ dei domino la cui parte inferiore e' la configurazione successiva.

Assumiamo inoltre, per comoditá, che:
1. $M$ non provi mai a muovere la testina a sinistra su input $w$ quando si trova all'inizio del nastro
2. Se $w$ é la stringa vuota, usiamo il carattere *blank* al suo posto durante la costruzione
3. Modifichiamo **PCP** per far sí che un match debba iniziare con il primo domino

L'ultima regola ci permette di definire $MPCP$ come 
$$MPCP=\{<P>|P\;e'\;un'istanza\;di\;PCP\;con\;un\;match\;che\;inizia\;col\;primo\;domino\;e\;con\;la\;parte\;inferiore\;dei\;domino\;non\;vuota\}$$

Dati quindi $<M,w>$ costruiamo quindi $P'$ che e' un' istanza di $MPCP$ che computa come segue:

mettiamo come primo pezzo il domino che ha la prima configurazione nella storia computazionale accettante , come richiesto da $MPCP$. Questo domino avrá quindi solo il simbolo # sulla parte superiore e la stringa $\#q_0,w_1,\dots w_n\#$ sulla parte inferiore.

> Il simbolo # è un nuovo simbolo non appartenente all'alfabeto del nastro e serve come separatore

![[Pasted image 20221128143652.png]]

Per ottenere un match dobbiamo far corrispondere la parte superiore a quella inferiore aggiuggendo dei domino. 
L'aggiunta dei domino provoca l'apparizione della prossima configurazione di $M$ nella stringa inferiore forzando l'esecuzione passo-passo di $M$.

