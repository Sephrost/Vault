### Indecidibilitá
Ci sono alcune categorie di problemi irrisolvibili da un computer, per esempio verifica di un software.

Il primo problema che andiamo ad osservare é il problema dell'accettazione per le *TM*.

#### Accettazione per le *TM*
Sia 
$$A_{TM}=\{<M,w>|\,M\;é\;una\;TM\;che\;accetta\;w\}$$
Dimostriamo che $A_{TM}$ é indecidibile.

Osserviamo che il problema é **decidibile positivamente**, ma perché un problema sia decidibile deve terminare su tutti gli input. 
Costruiamo quindi la *TM* $U$, che riconosce $A_{TM}$
$U$ = Dati in input $<M,w>$, dove $M$ é una *TM* e $w$ é una stringa
1. Simuliamo $M$ con input $w$
2. Se $M$ entra in uno stato di accettazione, $accetta$, se $M$ non entra in uno stato di rifiuto, $rifiuta$

$U$ peró entra in loop su input $<M,w>$ se $M$ entra in loop su $w$.
Proprio per questo motivo $U$ **non decide** $A_{TM}$.

> Se l'algoritmo potesse individuare se $M$ non termina su $w$, allora potrebbe entrare in stato di rifiuto peró questo non é possibile per un algoritmo.

