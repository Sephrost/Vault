#### Esempio di problema NP
Sia 
$$SUBSET-SUM=\{<S,t>|S=\{x_1,\dots,x_k\}\;e\;per\;qualche \;sottotineme\;di\;S\;\Sigma y=t\}$$
dimostriamo che il problema e' NP.

> Quindi il problema e' la massimizzazione 
> Un esempio e' $<\{4,11,21,27\},25>\in SUBSET-SUM$ poiche' $4+21=25$ e $t=25$

Costruiamo quindi il verificatore $V$ per $SUBSET-SUM$
Su input $<<S,t>,c>$
1. Controlliamo se $c$ e' un'insieme di numeri la cui somma sia $t$
2. Controlliamo se $S$ contiene tutti i nuemri in $c$
3. Se entrambi $1$ e $2$ sono verificati, $accetto$, altrimenti $rifiuto$
> Il certificato sara' quindi il sottoinsieme stesso.
> Inoltre il problema e' NP poiche dati $k$ elementi in $S$, abbiamo $2^k$ possibilita'

### $P$ vs $NP$
PEr quanto abbiamo presentato che i problemi $P$ e $NP$ abbiano definizioni diverse, non e' stato ancora possibile provare che esisste un singolo linguaggio $NP$ che non sia $P$.

Se le due classi fossero uguali allora ogni problema polinomialmente verificabile sarebbe quindi polinomialmente decidibile.

> La maggior parte dei ricercatori credono che le due classi non sino equivalenti.

Rimangono quidni due possibilita'
![[Pasted image 20221114092559.png]]

### NP-Complettezza
Abbiamo mostrato prima che se fosse possibile dimostrare che un'agoritmo polinomiale esiste per un qualche problema di classe $NP$, allora tutti i problemi $NP$ sarebbero essere decidibili in tempo polinomiale.

I problemi **NP-completi** sono tutti problemi decidibili in tempo polinomiale.

#### Esempio di problema NP-Completo: SAT
> E' il primo problema NP-completo trovato

Il problema e' sostanzialmente verificare se una formula booleana e' soddisfacibile

Sia
$$SAT=\{<\phi>|\phi\;e'\;una\;formula\;booleana\;soddisfacibile\}$$

> Una formula booleana e' soddisfacibile se e' possibile valutarla come vera per qualche assegnamento di valori

###### Teorema di Cook-Levin
$SAT\in P \iff P=NP$

#### Riducibilita' in tempo polinomiale
> Una funzione e' detta polinomialmente computabile se una qualche *TM* $M$ termina per $f(w)$ 

Un linguaggio $A$ e' **riducibile in tempo polinomiale** rispetto ad un linguaggio $B$ se esiste una funzione polinomiale $f:\Sigma^*\to\Sigma^*$ e per ogni $w$
$$w\in A \iff f(w)\in B$$
Quindi un lignuaggio e' $NP-completo$ se 
1. il linguaggio e' $NP$
2. ogni linguaggio $NP$ e' polinomialmente riducibile a $B$
###### La riducibilita' polinomiale preserva l'ordine polinomiale
Se $A\le_p B$ e $B\in B$, allora $A\in P$
Supponiamo che $f$ riduca polinomialmente $A$ a $B$, descriviamo l'agoritmo  di tempo polinomaiale $N$ che decide $A$ come segue:
$N =$ Su input $w$:
1. Calcoliamo $f(w)$
2. Eseguamo $M$ con input $f(w)$ e riportiamo cosa produce
Sappiamo che $w\in A$ se $f(w)\in B$, da definizione di ridubilita', allora $M$ accetta $f(w)$ per ogni $w\in A$.

Inoltre $N$ termina in tempo polinomiale.

> Se $M$ risolve $B$ in tempo $O(Q(n))$, con $Q$ polinomio, allora e' possibile verificare che $N$ risolve $A$ in tempo $O(Q(P(n)))$, con $Q(P(n))$ polinomio.