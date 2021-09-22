# Casistica
Caso|Risultato
-|-
Stringa/0|0
L{$\epsilon$}|L

# Automi riconoscitori
L'automa riconoscitore analizza il codice come una sequenza di caratteri, ricercando i **token** (costanti, operatori,simboli...) e produce a sua volta una sequenza di token da fornire al compilatore.

## Costante numerica intera
una sequenza non vuota di cifre decimale, eventualmente preceduta dal segno

## Costante numerica con virgola
Due sequenze di cifre decimale separate da un punto, eventualmente precedute dal segno

## Identificatore
una sequenza non vuota di lettere, numeri e "_" che non iniziano con un numero che contiene almeno un carattere diverso da _

# Automa a stati finiti 
Una macchina che riconosce stringhe con **memoria limitata.** Esso legge la stringa un simbolo alla volta, da destra verso sinistra, ogni simbolo letto altera lo stato della macchina, una volta finito da' esito affermativo se si trova in un suo stato finale(La stringa e' riconosciuta).

In generale possono esserci 0 o piu' stati finali.

E' indicato con la quintupla A=($Q,\sum,\sigma, q_{0},F$)

- Q e' un insieme finito di stati
- $\sum$ e' l'alfabeto riconosciuto dall'automa 
- $\sigma$: $Q$x$\sum \to Q$ e' la funzione di transizione 
- $q_{0}\in Q$ e' lo stato iniziale 
- F [subinsieme]Q e; l'isieme degli stati finali

## Funzione di transizione 
Una funzione di transizione e' la funzione $\sigma=Q$x$\sum^{*}\to Q$ definita per induzione sul suo secondo argomento che segue:

$\sigma(q,\epsilon)=q$
$\sigma(q,wa)=\sigma(\sigma(q,w),a)$

Il linguaggio riconosciuto da un Automa **A** e' denotato da **L(A)**

$L(A)$={$w\in\sum^{*}$|$\sigma(q_{0}w)\in F$}

Ovvero l'insieme delle stringhe che portano l' automa dal suo stato iniziale ad uno qualsiasi dei suoi stati finali.

Il linguaggio **L** si dice regolare se esiste un automa a stati finiti deterministico che lo riconosce, appartenente alla famiglia dei linguaggi regolari.

[tabelle di transizione da aggiungere]



