# Macchina di Turing
Immaginata come una macchina composta da un sensore, in grado di leggere un imput per cambiare stato
> Come un automa a stati finiti

e di muovere il nastro a sinistra e destra. Vedremo macchine illimitate soltanto a destra.
###### Esempio
$$(q_1,a)\to(q_2,b,right)=S(q_1,a)$$

Qualsiasi cosa che puo' essere rappresentato con un calcolo puo' essere definito in questa maniera.

## Definizione
Una macchina di turing e' una settupla $(Q,\Sigma,\tau,\dots,q_0,q_{accept},q_{reject})$
dove
- $Q$ e' un'insieme di stati
- Un' alfabeto di input $\Sigma$, che non contiene il carattere di padding
- Un'alfabeto del nastro $\Sigma\subseteq\tau$
- Una funzione di transizione $Q\times\tau\to Q\times\tau\times\{L,R\}$
- Uno stato di accettazione $q_{accept}\in Q$
- Uno stato di rifiuto $q_{reject}\in Q$, con $q_{reject}\neq_{accept}$

Come convenzione per la lettura usiamo la seguente dicitura, scrivendo il nastro e inserendo lo stato del controllo prima del'ultimo carattere letto
$$0100q_71100$$
quindi la macchina prima di riconoscere il carattere 1 si trovera' nello stato $q_7$.

Una macchina di Turing deve poter accettare tutte le stringhe comprese nel linguaggio $L$, composto da tutte le strighe che la macchina deve riconoscere, e rifiutare tutte le altre.

> Un ringuaggio e' detto **riconoscibile** se una macchina di Turing lo riconosce

### Linguaggio riconosciuto da una macchina di Turing
$$L(M)=\{w\in \Sigma^*|M\; accetta\; w\}$$

$$(M\;accetta\;w)\doblearrow(w\in L)$$

Se $w\notin L$ e $M$ riconosce $L$ allora $M$ rifiuta $w$ oppure $M$ non termina si $w$.