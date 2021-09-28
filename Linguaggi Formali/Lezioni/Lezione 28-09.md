## Automi non deterministici
Si ha un automa non deterministico quando il comportamento dell'automa non e' determinato, ovvero, a parita' di stato e simbolo letto, ha a disposizione piu' transizione tra cui "scegliere"

$\sigma:Q$ x $\sum\to P(Q)$ 

E' un quintupla $A=${$Q,\sum,\delta,q_{0},F$} dove:
- Q e' l'insieme finito degli stati
- $\sum$ e' l'alfabeto riconosciuto dall'automa
- $\delta:Q$x$\sum \to P(A)$ e' la funzione di transizione
- $q_{0}\in Q$ e' lo stato iniziale
- $FQ$ e' l'insieme degli stati finali

La sua funzione di  transizione estesa e':

$\sigma:Q$x$\sum^{*} \to P(Q)$

definita per induzione:
- $\sigma(q,\epsilon)=${$q$}
- $\sigma(q,wa)=${$r\in\sigma(p,a)|p\in\sigma(q,w)$}

Un NFA riconsoce le stringhe definite in $\sigma$ che gli consentono di arrivare in uno qualsiasi dei suoi stati finali

### DFA -> NFA
Dato un automa a stati finiti esiste un automa a stati non finiti identico, ad esclusione della funzione di transizione ($L(N)=L(D)$)

### NFA -> DFA
Dato un automa a stati non finiti (che ha un numero finito di stati), e' possibile tracciare tutti gli stati in cui l'NFA si puo' trovare durante in riconoscimento di una stringa all' interno di un DFA 