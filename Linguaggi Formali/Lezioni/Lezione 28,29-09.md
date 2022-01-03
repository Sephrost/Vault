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

## Automi con ε-transizioni
Sono automi che possono eseguire transizioni spontanee **senza leggere** alcun simbolo nella stringa da riconoscere.

Ogni $\epsilon$-NFA é un **quintupla** $A=(Q,\Sigma,\delta,q_0,F)$ dove:
- $Q$ e' l'insieme finito degli **stati**
- $\Sigma$ e' l'**alfabeto** riconosciuto dall'automa
- $\delta:Q\times (\Sigma \cup \{\epsilon\})\to p(Q)$ e' la **funzione di transizione**
- $q_{0}\in Q$ e' lo stato **iniziale**
- $F\subseteq Q$ e' l'**insieme** degli stati **finali**

Alcune osservazioni:
- $\delta(q,a)$ é l'insieme degli stati in cui l'$\epsilon$-NFA  puó transire quando si trova nello stato $q$ leggendo il simbolo $a$
- $\delta(q,\epsilon)$ é l'insieme di stati in cui l'$\epsilon$-NFA puó **transire spostaneamente** quando si trova nello stato $q$ senza leggere alcun simbolo
### $\epsilon$ chiusura
Dato uno stato $q$, la sua **ECLOSE(q)** e' il piu' piccolo insime di stati tale per cui: 
- $q\in$ ECLOSE(q), includendo lo stato stesso e impedendogli di essere vuota
- se $p\in$ ECLOSE(q), allora $\delta(p,\epsilon)\subseteq$ ECLOSE(q), includiamo quindi tutte le transizioni per $\epsilon$

La $\epsilon$-chiusura di un insieme e' l'insieme delle $\epsilon$-chiusure dei suoi elementi.
Se l'insieme e' vuoto questa puo' essere vuota.

###### Esempio
![[Pasted image 20220103140233.png]]
$ECLOSE(q_1)=\{q_1,q_2,q_3,q_4,q_6\}$
$ECLOSE(q_2)=\{q_2,q_3,q_6\}$
$ECLOSE(q_3)=\{q_3,q_6\}$
$ECLOSE(q_4)=\{q_4\}$
$ECLOSE(q_5)=\{q_5,q_7\}$
$ECLOSE(q_6)=\{q_6\}$
$ECLOSE(q_7)=\{q_7\}$
### Fuzione di transizione estesa
La funzione di transizione estesa di un $\epsilon$-NFA e' la funzione

$\hat{\delta}:Q\times \Sigma^*\to p(Q)$

definito per induzione come segue:

- $\hat{\delta}(q,\epsilon)=ECLOSE(q)$
- $\hat{\delta}(q,wa)=\{r\in ECLOSE(\delta(p,a)) | p \in \hat{\delta}(q,w)\}$

### Linguaggio riconosciuto

L'automa riconosce una stringa $w$ se esiste un percorso etichettato con $w$ che lo porta dallo stato iniziale $q_{0}$ a uno dei suoi stati finali in **$F$**.

### NFA -> $\epsilon$-NFA
###### Teorema
Dato un NFA $N$, esiste un $\epsilon$-NFA $E$, t.c. $L(E) = L(N)$

###### Dim.
Basta osservare che un NFA è un caso particolare di un $\epsilon$-NFA

###### Conseguenze
- Ogni linguaggio regolare è riconoscouto da un $\epsilon$-NFA
- gli $\epsilon$-NFA hanno potere riconoscitivo almeno pari a quello dei DFA/NFA equivalenti

### $\epsilon$-NFA -> DFA
Dato un $\epsilon$-NFA $E$, esiste un DFA $D$ tale che $L(D)=L(E)$

###### Intuizione
- usiamo la costruzione per sottoinsiemi come nel caso NFA → DFA
- occorre fare attenzione agli stati raggiungibili da ε-transizioni 
- possiamo usare la nozione di ε-chiusura!

###### Conseguenze
- ogni linguaggio riconosciuto da un ε-NFA è **regolare** 
- commbinando questo risultato e quello della , concludiamo che ε-NFA, NFA e DFA hanno lo **stesso potere riconoscitivo**