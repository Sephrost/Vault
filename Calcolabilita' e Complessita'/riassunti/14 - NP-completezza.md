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

Il teorema di Cook afferma che $SAT$ é **NP-completo**.
> Le definizioni aggiuntive utili all'esame sono l'enunciato di *SAT* e della *np-completezza*

Grazie a questo teorema é possibile dimostrare come ogni problema **NP** puó essere ridotto a $SAT$. Grazie a questo se fosse possibile trovare una soluzione di tempo polinomiale per una *TM* deterministica a singolo nastro allora $P=NP$.
#### Riducibilita' in tempo polinomiale
> Una funzione e' detta polinomialmente computabile se una qualche *TM* $M$ termina per $f(w)$ 

Un linguaggio $A$ e' **riducibile in tempo polinomiale** rispetto ad un linguaggio $B$ se esiste una funzione polinomiale $f:\Sigma^*\to\Sigma^*$ e per ogni $w$
$$w\in A \iff f(w)\in B$$
Quindi un linguaggio e' $NP-completo$ se 
1. il linguaggio e' in $NP$
2. ogni linguaggio $NP$ e' polinomialmente riducibile ad esso
###### La riducibilita' polinomiale preserva l'ordine polinomiale
Se $A\le_p B$ e $B\in B$, allora $A\in P$
Supponiamo che $f$ riduca polinomialmente $A$ a $B$, descriviamo l'agoritmo  di tempo polinomaiale $N$ che decide $A$ come segue:
$N =$ Su input $w$:
1. Calcoliamo $f(w)$
2. Eseguamo $M$ con input $f(w)$ e riportiamo cosa produce
Sappiamo che $w\in A$ se $f(w)\in B$, da definizione di ridubilita', allora $M$ accetta $f(w)$ per ogni $w\in A$.

Inoltre $N$ termina in tempo polinomiale.

> Se $M$ risolve $B$ in tempo $O(Q(n))$, con $Q$ polinomio, allora e' possibile verificare che $N$ risolve $A$ in tempo $O(Q(P(n)))$, con $Q(P(n))$ polinomio.