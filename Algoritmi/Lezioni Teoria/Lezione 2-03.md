### Problemi insolubili
Non basta che un problema ben definito perche' sia risolubile.

Es:*Problema dell'halt*

### Problemi intrattabili 
Problemi che anche se risolvibili non hanno un tempo di elaborazione accettabile, e quindi polinomiale.

Es:*Torri di Hanoi*

## Corretteza
### Correttezza parziale
Una procedura e' parzialmente corretta rispetto a una specifica, se ogni volta che termina su dei risultati che soddisfano l'ipotesi, allora soddisfa la specifica.

Se l'esecuzione non termina si dice che un programma e' parzialmente corretto a vuoto.

### Correttezza totale
Una procedura e' totalmente corretta se e' parzialmente corretta e termina sempre la sua esecuzione.

#### Pre condizione
E' un'ipotesi sugli ingressi, che deve essere rispettata
#### Post condizione 
E' una descrizione di cio' che e' l'output se la pre condizione e' soddisfatta.

Nel caso di chiamata ad una procedura ricorsiva pre e post condizione si invertono, ed e' il motivo per il quale si puo' unsare la dimostrazione per induzione.

###### Esempio di pre e post condizione
$$Div(a,b)$$
Pre condizione:
 - $a\ge0,b\ge 0$
 Post condizione:
 - $a=bq+r$ e $0\ge r < b$

### Ricorsione
Una funzione e' ricorsiva se nella sua definizione viene utilizzata direttamente o indirettamente la funzione stessa.

Si ottiene una soluzione solo quando il passo base e' soddisfatto.


%%Aggiungere definizione di fase analitica e sintetica%%
#### Ricorsione lineare 
E' una ricorsione dove una fase analitica e' seguita da una fase sintetica.

#### Schema di induzione

Se voglio dimostra che unap roprieta' P vale per ogni n, dimostro prima che vale per p(k), detto passo base, e domostro che vale per (k+1), detto passo induttivo.

