# Macchine di Turing
Una **macchina di Turing** é simile ad un automa a stati finiti, ma con memoria illimitata, rappresentata da un nastro infinito.

Inizialmente il nastro contiene soltanto la stringa di input, mentre tutto il resto é vuota. Se la macchina ne ha necessitá quindi puó scriverci sopra.

É inoltre in grado di leggere e scrivere sul nastro, attraverso i movimenti di una testina che puó muoversi a destra e sinistra, al fine di produrre un'output *accettato* o *rifiutato*. 

> Se non finisce in nessuno dei suoi stati continuerá ad elaborare per sempre.

###### Esempio
$$(q_1,a)\to(q_2,b,right)=S(q_1,a)$$

Qualsiasi cosa che puo' essere rappresentato con un calcolo puo' essere definito in questa maniera.
## Definizione
Una macchina di turing é una settupla $(Q,\Sigma,\Gamma,\delta,q_0,q_{accept},q_{reject})$
dove:
- $Q$ é un'insieme di stati
- Un' alfabeto di input $\Sigma$, che non contiene il carattere di padding (*blank*)
- Un'alfabeto del nastro $\Gamma$ contenente il carattere di padding e dove $\Sigma\subseteq\Gamma$
- Una funzione di transizione $Q\times\Gamma\to Q\times\Gamma\times\{L,R\}$
- Uno stato $q_0\in Q$ che rappresenta lo stato iniziale 
- Uno stato di accettazione $q_{accept}\in Q$
- Uno stato di rifiuto $q_{reject}\in Q$, con $q_{reject}\ne q_{accept}$

Una macchina di Turing riceve in input una stringa $w=w_1w_2\dots w_n\in\Gamma^*$ nei primi $n$ spazi del nastro(il resto é costituito da caratteri vuoti). Il primo carattere di padding rappresenta quindi la fine della stringa $w$.

#### Convenzione per la lettura di una configurazione
Una **configurazione** é una combinazione di *stato corrente*, *contenuto del nastro corrente* e *posizione della testina attuale*.

Diciamo che una configurazione $C_1$ **produce** una configurazione $C_2$ se la $M.T$ puó  legalmente passare dallo stato della configurazione $C_1$ a quello di $C_2$ in un singolo passo.

Come convenzione per la lettura di una configurazione usiamo la seguente dicitura, scrivendo il nastro e inserendo lo stato del controllo prima del prossimo carattere da leggere, nella srguente maniera:
$$0100q_71100$$
quindi la macchina prima di riconoscere il carattere 1 si trovera' nello stato $q_7$.

![[Pasted image 20220921114716.png]]

Una macchina di Turing deve poter accettare tutte le stringhe comprese nel linguaggio $L$, composto da tutte le strighe che la macchina deve riconoscere, e rifiutare tutte le altre.

### Linguaggio riconosciuto da una macchina di Turing
$$L(M)=\{w\in \Sigma^*|M\; accetta\; w\}$$
$$(M\;accetta\;w)\iff(w\in L)$$
Se $w\notin L$ e $M$ riconosce $L$ allora $M$ rifiuta $w$ oppure $M$ non termina su $w$.

## Linguaggi Decidibili Positivamente
> Un linguaggio é detto **Decidibile Positivamente** (*Turing-Recognizable*) se una qualche macchina di Turing lo riconosce

## Linguaggi Decidibili
Poiché alcuni riconoscitori possono non terminare mai, rendendo difficile distinguere una macchina che sta elaborando da una in loop, introduciamo la nozione di *decisori*.

> Un linguaggio é detto **Decidibile** (Turing-Decidable) se esiste una macchina di Turing che termina su ogni input $\in L(M)$ 

Ogni Linguaggio Decidibile é anche riconoscibile, ma non il contrario.

> Diciamo inoltre che un linguaggio é **Decidibile** se é sia positivamente che negativamente decidibile per il **teorema di Post**

### Legenda per i Linguaggi
Per ogni $w^*\in L$
|Italiano|Inglese|Accettazione($w\in L$)|Rifiuto($w\notin L$)|
|:--:|:--:|:--:|:--:|
|Decidibile|Turing Recognizable|$M$ accetta $w$|$M$ rifiuta $w$|
|Decidibile Positivamente|Turing Decidable|$M$ accetta $w$|$M$ rifiuta $w\;\lor\;M$ non termina su $w$ |
|Decidibile negativamente|Co-Turing Recognizable|$M$ accetta $w\;\lor\;M$ non termina su $w$ |$M$ rifiuta $w$|

[[01 - Varianti delle Macchine di Turing]]