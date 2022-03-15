## Corretteza
### Correttezza parziale
Una procedura é parzialmente corretta rispetto a una specifica, se **ogni** volta che **termina** su dei risultati che **soddisfano** l'**ipotesi**, allora **soddisfa** la **specifica**.

Se l'esecuzione non termina si dice che un programma é parzialmente corretto a vuoto.

### Correttezza totale
Una procedura é **totalmente corretta** se é **parzialmente** corretta e **termina sempre** la sua esecuzione.

#### Pre condizione
É un'**ipotesi** sugli **ingressi**, che deve essere rispettata.

#### Post condizione 
É una **descrizione** di ció che é l'**output** se la pre condizione e' soddisfatta.

###### Esempio di pre e post condizione
$Div(a,b)$
Pre condizione:
 - $a\ge0,b\ge 0$
 Post condizione:
 - $a=bq+r$ e $0\ge r < b$

### Schema per l'induzione

Se voglio dimostra che una proprietá $P$ vale per ogni $n$, dimostro prima che vale per $P(k)$, detto **passo base** e solitamente $P(0)$, e dimostro che vale per $P(k+1)$, detto **passo induttivo**.

### Invariante
É un **asserto** che, pur cambiando i valori della variabili, rimane sempre vero.

L'invariante é una formula diversa dalla guardia di un ciclo che permette di dedurre la post condizione di un ciclo.