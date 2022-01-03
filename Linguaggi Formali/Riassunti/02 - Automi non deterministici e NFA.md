## Automi non deterministici
Si ha un automa non deterministico quando il comportamento dell'automa non e' determinato, ovvero, a parita' di stato e simbolo letto, ha a disposizione piu' transizione tra cui "scegliere"

## Automi a stati finiti non deterministici

Un'**automa a stati finiti non deterministico** é un quintupla $A=\{Q,\Sigma,\delta,q_{0},F\}$ dove:
- $Q$ e' l'insieme finito degli **stati**
- $\Sigma$ e' l'**alfabeto** riconosciuto dall'automa
- $\delta:Q\times \Sigma \to P(Q)$ e' la funzione di transizione
- $q_{0}\in Q$ e' lo stato **iniziale**
- $F\subseteq Q$ e' l'insieme degli stati **finali**

Alcune osservazioni:
- $\delta(q,a)$ é l'**insieme** di stati in cui l'NFA di puó trovare partendo da $q$ e riconoscendo il simbolo $a$
- Se $\delta(q,a)$ é un singoletto, l'NFA ha una sola scelta
- Se $\delta(q,a)$ é vuoto, l'NFA rifiuta la scelta

### Funzione di transizione estesa

La sua funzione di  transizione estesa dell'automa é la funzione:

$\hat{\delta}:Q\times \Sigma \to Q$

definita per induzione come segue:
- $\hat{\delta}(q,\epsilon)=q$
- $\hat{\delta}(q,wa)=\delta(\hat{\delta}(q,w),a)$

La funzione ritornerá l'insime di stati in cui l'automa di potrá trovare dopo aver preso in input la stringa $arg[1]$ partendo dallo stato $arg[0]$.

### Linguaggio riconosciuto 

Un NFA riconosce le stringhe definite in $\delta$ che gli consentono di arrivare in uno qualsiasi dei suoi stati finali:

$L(A)=\{w\in \Sigma^* | \hat{\delta}(q_0,w)\cap F\ne 0\}$

### Tabella di transizione

Anche in questo caso l'automa si puó rappresentare in forma tabellare come segue:

Stato|b
--|--
$\to q_0$|$q_1$
$*q_1$|$q_0$

dove:
- Le righe corrispondono agli stati dell'automa
- Le colonne corrispondono ai simboli dell'alfabeto dell'automa
- Lo stato iniziale é marcato con $\to$
- Ogni stato finale é marcato con *
- La cella corrispomdente alla riga $q$ e alla colonna $b$ contiene l'insieme $\delta(q,a)$

### DFA -> NFA
Dato un automa a stati finiti **D** esiste un automa a stati non finiti **N** identico, ad esclusione della funzione di transizione ($L(N)=L(D)$)

$\delta_N(q,a)=\{\delta_D(q,a)\}$

possiamo quindi dimostrare per induzione su |$w$| che 

$\hat{\delta}_D(q_0,w)=p \Leftrightarrow \hat{\delta}_N(q_0,w)=\{p\}$
 
 concludiamo quindi che 
 
$\hat{\delta}_D(q_0,w)\in F \Leftrightarrow \hat{\delta}_N(q_0,w)\cap F\ne 0$

### NFA -> DFA
Dato un automa a stati non finiti (che ha un numero finito di stati), e' possibile tracciare tutti gli stati in cui l'NFA si puo' trovare durante in riconoscimento di una stringa all' interno di un DFA.

Gli stati dell'DFA saranno quindi $2^n$, dove $n$ é il numero di stati dell'NFA.