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