## Automi non deterministici
Si ha un automa non deterministico quando il comportamento dell'automa non e' determinato, ovvero, a parita' di stato e simbolo letto, ha a disposizione piu' transizione tra cui "scegliere"

$\sigma:Q$ x $\sum\to P(Q)$ 

E' un quintupla $A=${$Q,\sum,\delta,q_{0},F$} dove:
- Q e' l'insieme finito degli stati
- $\sum$ e' l'alfabeto riconosciuto dall'automa
- $\delta:Q$x$\sum \to P(A)$ e' la funzione di transizione
- $q_{0}\in Q$ e' lo stato iniziale
- $F\subseteq Q$ e' l'insieme degli stati finali

La sua funzione di  transizione estesa e':

$\sigma:Q$x$\sum^{*} \to P(Q)$

definita per induzione:
- $\overline{\sigma}(q,\epsilon)=${$q$}
- $\overline{\sigma}(q,wa)=${$r\in\sigma(p,a)|p\in\overline{\sigma}(q,w)$}

Un NFA riconsoce le stringhe definite in $\sigma$ che gli consentono di arrivare in uno qualsiasi dei suoi stati finali:

$L(A)=${$w\in\sum^{*}|\overline{\sigma}(q_{0},w)\cap F\ne0$}

### DFA -> NFA
Dato un automa a stati finiti **D** esiste un automa a stati non finiti **N** identico, ad esclusione della funzione di transizione ($L(N)=L(D)$)

$\delta_{N}(q,a)=${$\delta_{D}(q,a)$}

### NFA -> DFA
Dato un automa a stati non finiti (che ha un numero finito di stati), e' possibile tracciare tutti gli stati in cui l'NFA si puo' trovare durante in riconoscimento di una stringa all' interno di un DFA.

## Automi con $\epsilon$ transizioni
Sono automi che possono eseguire transizioni spontanee senza leggere alcun sinbolo nella strainga da riconoscere

$\sigma:Q$x$(\sum\cap\\$ {$\epsilon$}$)\to P(Q)$

E' un quintupla $A=${$Q,\sum,\delta,q_{0},F$} dove:
- Q e' l'insieme finito degli stati
- $\sum$ e' l'alfabeto riconosciuto dall'automa
- $\sigma:Q$x$(\sum\cap\\$ {$\epsilon$}$)\to P(Q)$ e' la funzione di transizione
- $q_{0}\in Q$ e' lo stato iniziale
- $F\subseteq Q$ e' l'insieme degli stati finali
## $\epsilon$ chiusura
**ECLOSE(q)** e' il piu' piccolo insime di stati che 
- $q\in$ ECLOSE(q), cioe' include lo stato stesso, impedendogli di essere vuota
- se $p\in$ ECLOSE(q), allora $\sigma(p,\epsilon)\subseteq$ ECLOSE(q), cioe' include tutte le transizioni $\epsilon$

La $\epsilon$-chiusura di un insieme e' l'insieme delle $\epsilon$-chiusure dei suoi elementi.
Se l'insieme e' vuoto questa puo' essere vuota.

### Fuzione di transizione estesa
La $\overline{\sigma}$ di un automa con $\epsilon$ chiusure e' definito per induzione come segue:
- $\overline{\sigma}(q,\epsilon)$=ECLOSE(q)
- $\overline{\sigma}(q,wa)=${$r\in$ECLOSE$(\sigma(p,a))|p\in\overline{\sigma}(q,w)$}

L'automa riconsosce una stringa $w$ se esiste un percorso etichettato con $w$ che lo porta dallo stato iniziale $q_{0}$ a uno dei suoi stati finali in **$F$**.

### NFA -> $\epsilon$-NFA
Un NFA **N**

### $\epsilon$-NFA -> DFA