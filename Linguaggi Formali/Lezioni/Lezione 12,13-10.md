## Linguaggi non regolari
Data una proprieta' **$P$** soddisfatta da un linguaggio regolare, allora un **Linguaggio non Regolare** e' un linguaggio che **non soddisfa** $P$, detta **pumpling lemma**.

Esistono linguaggi non regolari per il quale vale il pumpling lemma.
### Pumpling lemma per i linguaggi regolari
Per ogni linguaggio regolare $L$, esiste un numero naturale $n$ per cui $|w|\ge n$ con $w\in L$,ed esistono $x, y$ e $z$ t.c $w=xyz$ con queste caratteristiche:
- $y$ non puo' essere la stringa vuota ($y\ne \epsilon$)
- La lunghezza del segmento $xy$ ha una lunghezza non superiore ad $n$ ($|xy|\le n$)
- Tutte le stringhe della forma $xy^{k}z$ appartengono al linguaggio $L$, per qualunque $k\ge0$

Quindi se prendiamo un linguaggio regolare, prese delle stinghe sufficientementemente lunghe di questo linguaggio, sono sempre in grado di individuare una parte "centrale" replicabile con regolaritá, generando stringhe sempre appartenenti al linguaggio.

##### Esempio di dimostrazione
Il linguaggio $L=${$a^{k}b^{k}|k\geq0$}(k $a$ seguite da k $b$) non e' regolare.

Considero una stringa $w=a^nb^n$ appartenente al linguaggio $L$ con $|w|=2n\ge n$,allora devono esistere $x$,$y$ e $z$ tali che $w=xyz$ e che soddisfano le 3 proprietá del pumpling lemma.

Sappiamo che:
- Per la prima proprietá $y$ non deve essere nulla, quindi conterrá almeno una $a$,o una $b$
- Per la seconda proprietá $xy$ conterrá solo a, poiché se contenesse anche delle b allora supererebbe $n$
- Per la terza condizione $xz\in L$

Dovendo esserci lo stesso numero di $a$ e $b$, allora la proprietá non é verificata poiché ci possono essere arbitrarie $a$ dovute ad $y^k$.
# Minimizzazione DFA
## Stati distinguibili
Dato un DFA $A$, 2 stati $p$ e $q$ dello stesso sono distinguibili se **esiste una stringa** per cui,partendo da questi, uno mi conduce in uno stato finale, mentre invece l'altro no.

## Stati indistinguibili
Dato un automa $L$, 2 stati $p$ e $q$ dello stesso sono indistinguibili se **per ogni stringa** ,partendo da questi, arrivo in uno **stesso stato** (anche non finale). 

$\hat{\delta}(p,w)\in F \Leftrightarrow\hat{\delta}(q,w)\in F$
per ogni $w\in \Sigma^*$.

Gli stati indistinguibili sono anche detti **ridondanti**.

Un automa e' ottimizzato se **non esistono** stati ridontanti.

Ogni stato e' **indistinguibile** da **se stesso**.

Se $p$ e' indistinguibile da $q$ e viceversa allora sono indistinguibili.

La relazione di indistingibilita' tra stati e' indicata dalla tilde "~". inoltre indichiamo con [q] la classe di equivalenza di q ([q]={$q\in Q|p$~$q$}).

### Algoritmo per trovare gli stati indistinguibili
Per trovare gli stati indistinguibili all'interno di un DFA utilizziamo il seguente algoritmo:

1. All'inizio oni stato e' marcato come distinguibile
2. Si marcano come distinguibili le coppie di stati $\{p,q\}$ in cui $p$ é finale ($p\in F$), mentre $q$ no ($q\notin F$) 
3. Se esistono una coppia di stati $p,q\in Q$ e un simbolo $a\in \Sigma$ per cui la coppia $\{\delta(p,a),\delta(q,a)\}$ é giá marcata come distinguibile, si marchia $\{p,q\}$  come distinguibile
4. Si itera il passo precendete finché trovo stati distinguibili

Per applicare l'algoritmo ci avvaliamo di una **tabella triangolare**, dove sulle **righe** indichiamo gli stati dal **secondo** all'**ultimo**, mentre sulle **colonne** gli stati dal **primo** al **penultimo**.

###### Esempio
Applichiamo l'algoritmo al seguente DFA:

![[Pasted image 20220103171633.png]]

Applichiamo il passo 2 dell'algortmo, etichettando tutte le coppie in cui compare C come distinguibili

![[Pasted image 20220103171746.png]]

Applichiamo il passo 3 dell'algoritmo:
- Dalla coppia $\{A,B\}$, con 1 come simbolo é possibile raggiungere la coppia $\{F,C\}$, quindi la segno come distinguibile
- Dalla coppia $\{B,G\}$, con 1 come simbolo raggiungo la coppia $\{E,G\}$, quindi la segno come distinguibile
- ...
Alla fine otterró la seguente tabella

![[Pasted image 20220103172342.png]]

### Minimizzazione dato la tabella di indistinguibilitá 

Per ottenere un DFA minimo che presenta degli stati indistinguibili, **partendo dalla tabella** posso andare a **ricostruire** la sua **struttura** fondendo insieme gli **stati indistinguibili**(generando delle **coppie**) e collegandoli agli stati distinguibili come den DFA non minimo.

###### Esempio
In riferimento all'esempio del punto precedente

![[Pasted image 20220103174115.png]]

### Equivalenza tra automi
Dati 2 automi $P$ e $Q$, e' possibile verificare la loro equivalenza con il seguente processo:
-  Creo l'unione dei 2 DFA $A=(Q_1\cup Q_2,\Sigma,\delta,q_1,F_1\cup F_2)$ dove
	-  $\delta(q,a)=\{^{\delta_1(q,a)if( q\in Q_1)}_{\delta_2(q,a)if( q\in Q_2)}$
-  Eseguo l'algoritmo riempi-tabella su P
-  $P$ e $Q$ sono equivalenti solo se $p$ e $q$ sono equivalenti

