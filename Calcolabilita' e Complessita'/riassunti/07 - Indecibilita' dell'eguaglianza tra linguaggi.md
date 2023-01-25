### Indecidibilitá dell'eguaglianza tra linguaggi
Sia 
$$EQ_{TM}=\{<M_1,M_2>|M_1\;e\;M_2\;sono\;TM\;e\;L(M_1)=L(M_2)\}$$
dimostriamo che $EQ_{TM}$ e' indecidibile.

Supponiamo che esista una *TM* $R$ che decida $EQ_{TM}$, e che esista inoltre un'altra *TM* $S$ che decide $E_{TM}$ come segue:
$S$ = su input $<M>$, dove $M$ e' una *TM*:
1. Eseguo $R$ con input $<M,M_1>$, dove $M$ e' una *TM* che *rifiuta* tutti gli input
2. Se $R$ accetta, $accetto$, se $R$ rifiuta, $rifiuto$

Se il linguaggio di $M_1$ o $M_2$ fosse il inguaggio vuoto $\{\emptyset\}$, allora $S$ dovrebbe essere in grado di decidere $E_{TM}$, ma poiche' il problema e' indecidibile lo e' anche $EQ_{TM}$.

### Corollario Indecidibilitá assoluta di $E_{TM}$
$EQ_{TM}$ non é né positivamente né negativamente decidibile
#### Dimostrazione
Per dimostrare che non é positivamente decidibile riduciamo il complementare di $EQ_{TM}$ ad $A_{TM}$ come segue:

Per input $<M,w>$, dove $M$ é una *TM* e $w$ una stringa, costruisco $M_1$ che rifiuta ogni input ed $M_2$ che esegue $M$ su ogni input e accetta se $M$ accetta. $M$ ritornerá $<M_1,M_2>$.

Quindi se $M$ accetta $w$, allora $M_2$ accetterá ogni stringa, ma poiché $M_1$ non accetta mai le due macchine non sono equivalenti.
Viceversa, se $M$ non accetta $w$, allora neanche $M_2$ accetterá, ma in questo caso $M_1$ e $M_2$ sarebbero equivalenti. quindi $f$ riduce $A_{TM}$ a $\overline{EQ_{TM}}$. 

Per dimostrare che il complemento di $EQ_{TM}$ non é decidibile positivamente mostriamo che esiste una riduzione per il complemento del problema appena citato a $A_{TM}$, ma il complemento del complemento é il linguaggio stesso