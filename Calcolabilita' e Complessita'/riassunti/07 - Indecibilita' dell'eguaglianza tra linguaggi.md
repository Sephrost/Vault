Sia 
$$EQ_{TM}=\{<M_1,M_2>|M_1\;e\;M_2\;sono\;TM\;e\;L(M_1)=L(M_2)\}$$
dimostriamo che $EQ_{TM}$ e' indecidibile.

Supponiamo che esista una *TM* $R$ che decida $EQ_{TM}$, e che esista inoltre un'altra *TM* $S$ che decide $E_{TM}$ come segue:
$S$ = su input $<M>$, dove $M$ e' una *TM*:
1. Eseguo $R$ con input $<M,M_1>$, dove $M$ e' una *TM* che *rifiuta* tutti gli input
2. Se $R$ accetta, $accetto$, se $R$ rifiuta, $rifiuto$

Se il linguaggio di $M_1$ o $M_2$ fosse il inguaggio vuoto $\{\emptyset\}$, allora $S$ dovrebbe essere in grado di decidere $E_{TM}$, ma poiche' il problema e' indecidibile lo e' anche $EQ_{TM}$.
