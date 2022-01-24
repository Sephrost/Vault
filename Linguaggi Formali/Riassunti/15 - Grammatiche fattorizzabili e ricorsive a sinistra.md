## Grammatiche fattorizzabili e ricorsive a sinistra
Molte gramamtiche utili per descrivere linguaggi di programmazione non sono LL(1).

I problemi sono:
### Fattorizzazione
Produzione dove nel corpo individuiamo un prefisso comune a 2 produzioni

$A \to \alpha \beta_1|\alpha \beta_2$

dove 

$Guida(A\to\alpha \beta_1)\cap Guida(A\to \alpha \beta_2)\ne 0$


Possiamo quindi fattorizzare il prefisso in comune $\alpha$ introducendo una nuova variabile $A'$:

$A\to \alpha A'$ e $A'\to \beta_1|\beta_2$

a patto che,cosi' facendo, le produzioni degli insiemi guida siano disgiunti

### Ricorsione immediata a sinistra

La variabile in testa di una produzione e' anche il primo di una produzione.

Per esempio una grammatica con le produzioni

$A\to A\alpha|\beta$

e' detta immediatamente ricorsiva a sinistra in quanto la produzione $A\to A\alpha$ ha $A$ come primo simbolo del corpo.

Possiamo risolvere il problema introducendo una variable per spostare la ricorsione da sinistra a destra:

$A\to \beta A'$  se la dervazione non era in origine ricorsiva

$A'\to \epsilon|\alpha A'$ se la derivazione era ricorsiva

Una produzione di questo tipo **elimina l'ambiguita'**, ma rende **meno chiaro** il **linguaggio** che va' a generare.

L'eliminzazione della ricorsione **non** grantisce di ottenere una grammatica LL(1), oltre al rendere difficile la realizzazione di un parser ricorsivo discendente.

#### Ricorsioni indirette
Alcune ricorsioni sono dette indirette, per esempio la grammatica

$S\to Aa|b$
$A\to Ac|Sd|\epsilon$

presenta una ricorsione diretta a sinistra che riguarda la variabile $A$, oltre ad una ricorsione indiretta.

$A\to Sd \to Aad$

Tentando di eliminare quella ricorsione otteniamo 

$S\to Aa|b$
$A\to SdA'|A'$
$A'\to \epsilon|cA'$

Per eliminare la ricorsione indiretta utilizziamo invece il seguente algoritmo :
1. Imponiamo un **ordine** arbitrario alle **variabili** della grammatica
2. Consideriamo ogni variabile, seguendo l' ordine, ed eliminiamo la ricorsione immediata per quella variabile  e riscriviamo le occorrenze della stessa che compaiono nei corpi delle produzioni delle variabili seguenti.

![[pngs/2021-11-17--1637145673_550x99_scrot.png]]