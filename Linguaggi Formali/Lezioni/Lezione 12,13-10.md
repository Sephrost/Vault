## Linguaggi non regolari
Data una proprieta' **$P$** soddisfatta da un linguaggio regolare, allora un Linguaggio non Regolare e' un linguaggio che non soddisfa $P$, detta pumpling lemma.

Esistono linguaggi non regolari per il quale vale il pumpling lemma.
### Pumpling lemma per i linguaggi 
Per ogni linguaggio regolare $L$, esiste un numero naturale $n$, esistono $x, y$ e $z$ con queste caratteristiche:
- $y$ non puo' essere la stringa vuota
- La lunghezza del segmento $xy$ ha una lunghezza non superiore ad $n$
- Tutte le stringhe della forma $xy^{k}z$ appartengono al linguaggio, per qualunque $k\ge0$

Riascoltare la registrazione

#### Esempio
Il linguaggio $L=${$a^{k}b^{k}|k\geq0$}(k $a$ seguite da k $b$) non e' regolare, considero una stringa appartenente al linguaggio lunga almeno $n$, allora devono esistere $x,y$ e $z$

# Minimizzazione
## Stati distinguibili
Dato un automa $L$, 2 stati $p$ e $q$ dello stesso sono distinguibili se **esiste una stringa** per cui,partendo da questi, uno mi conduce in uno stato finale, mentre invece l'altro no.
## Stati indistinguibili
Dato un automa $L$, 2 stati $p$ e $q$ dello stesso sono indistinguibili se **per ogni stringa** ,partendo da questi, arrivo in uno **stesso stato** (anche non finale). 

Gli stati indistinguibili sono anche detti **ridondanti**.

Un automa e' ottimizzato se **non esistono** stati ridontanti.

Ogni stato e' indistinguibile da se stesso.

Se p e' indistinguibile da q e viceversa allora sono indistinguibili.

La relazione di indistingibilita' tra stati e' indicata dalla tilde "~". inoltre indichiamo con [q] la classe di equivalenza di q ([q]={$q\in Q|p$~$q$}).

### Algoritmo per trovare gli stati indistinguibili
- All'inizio oni stato e' marcato come distinguibile
[aggiungere]


### Equivalenza tra automi
Dati 2 automi P e Q, e' possibile verificare la loro equivalenza con il seguente processo:
-  Creo l'unione dei 2 DFA
-  Eseguo l'algoritmo riempi-tabella su P
-  P e Q sono equivalenti solo se p e q sono equivalenti

