# Automi riconoscitori
L'automa riconoscitore analizza il codice come una sequenza di caratteri, ricercando i **token** (costanti, operatori,simboli...) e produce a sua volta una sequenza di token da fornire al compilatore.

#### Costante numerica intera
una sequenza non vuota di cifre decimale, eventualmente preceduta dal segno

#### Costante numerica con virgola
Due sequenze di cifre decimale separate da un punto, eventualmente precedute dal segno

#### Identificatore
una sequenza non vuota di lettere, numeri e "_" che non iniziano con un numero che contiene almeno un carattere diverso da _

# Automa a stati finiti 
Una macchina che riconosce stringhe con **memoria limitata.** Esso legge la stringa **un simbolo** alla volta, da destra verso sinistra, ogni simbolo letto **altera lo stato** della macchina, una volta finito da' esito affermativo se si trova in un suo stato finale(La stringa e' riconosciuta).

In generale possono esserci 0 o piu' stati finali.

## Automi a stati finiti deterministici

Un'automa a stati finiti deterministico é indicato con la quintupla A=($Q,\Sigma,\delta, q_0,F$), dove:

- $Q$ e' un insieme finito di **stati**
- $\sum$ e' l'**alfabeto** riconosciuto dall'automa 
- $\delta:Q\times \Sigma$ e' la **funzione di transizione** 
- $q_{0}\in Q$ e' lo stato **iniziale** 
- $F \subseteq Q$ é l'isieme degli **stati finali**

### Funzione di transizione estesa
Una funzione di transizione estesa e' la funzione $\hat{\delta}:Q\times \Sigma^*\to Q$ definita per induzione sul suo secondo argomento che segue:

- $\hat{\delta}(q,\epsilon)=q$
- $\hat{\delta}(q,wa)=\delta(\hat{\delta}(q,w),a)$

La funzione restitusce lo stato in cui si trova l'automa dopo il riconoscimento della stringa $arg[1]$ partendo dallo stato $arg[0]$.

### Linguaggio riconosciuto

Il linguaggio riconosciuto da un Automa **A** e' denotato da **L(A)**

$L(A)$={$w\in\Sigma^{*}$|$\hat{\delta}(q_{0},w)\in F$}

Ovvero l'insieme delle stringhe che portano l' automa dal suo stato iniziale ad uno qualsiasi dei suoi stati finali.

Il linguaggio **L** si dice regolare se esiste un automa a stati finiti deterministico che lo riconosce, appartenente alla famiglia dei linguaggi regolari.

### Tabella di transizione
Un DFA di puó rappresentare in forma tabellare, come segue:  

Stato|b
--|--
$\to q_0$|$q_1$
$*q_1$|$q_0$

dove:
- Le righe corrispondono agli stati dell'automa
- Le colonne corrispondono ai simboli dell'alfabeto dell'automa
- Lo stato iniziale é marcato con $\to$
- Ogni stato finale é marcato con *

