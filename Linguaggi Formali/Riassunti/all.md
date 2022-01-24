# Introduzione
Inizialmento gli elaboratori venivano programmati fornendo delle istruzioni in codice macchina, che il processore poteva eseguire direttamente, ma scrivere istruzioni risultava difficile.

Naque quindi la necessita' di usare dei linguaggi di programmazione per scrivere programmi a livello piu' alto. 

Il compilatore si pone quindi tra il linguaggio umano a quello macchina, traducendo il programma scritto dall' utente e riscriverlo in un programma equivalente a linguaggio macchina.

## Fasi di un compilatore
- Analisi Lessicale 
- Analisi Sintatica 
- Generazione del codice intermedio

## Alfabeto 
Un alfabeto e' un'inseme finito e non vuoto di simboli:

- Utlizziamo $\sum$ per indicare l'alfabeto generico 
- utilizziamo $a,b,c..$  per indicare generici simboli

## Stringhe
Una **stringa** su un alfabeto $\sum$ e' una sequenza **finita** di simboli in $\sum$
- Usiamo $u,v,w...$ per indicare stringhe generice
- Usiamo $\epsilon$ per indicare una **stringa vuota**  composta da *0 simboli*
### Operazioni su stringhe 
La **lunghezza** di una stringa $u$ e' il numero di simboli di cui e' costituita e si indica con $|u|$ .

La **concatenazione** di $u$ e $v$ e' indicata con $uv$, attacando la sequenza di $u$ dopo la sequenza di $v$. 

- La concatenazione é **neutra** rispetto alla **stringa vuota** ($u\epsilon=u$), **associtativa** ($u(vw)=(uv)w$), ma **non commutativa** ($uv\ne vu$)

La **lunghezza** della concatenzione sara' uguale alla somma della lunghezza delle sue stringhe.

Un **suffiso** di una stringa se la concatenazione di essa con un'altra stringa e' uguale ad un'altra.

L'**inverso** ($w^{R}$) di una stringa $w$ e' una stringa che constiene gli stessi suffissi ma in ordine inverso($w=a_1,a_2,..,a_n$ e $w^R=a_n,..,a_2,a_1$).

Una stringa e' **palindroma** se una stringa e' uguale al suo inverso ($w=w^{R}$)

La **potenza** di una stringa ($u^{n}$)e' la stringa che otteniamo concatenando la stessa $n$ volte.

## Linguaggio
Un linguaggio $L$ e' un'alfabeto $\sum$ di un qualunque insieme di stringhe su $\sum$

- Usiamo $\sum^{*}$ per indicare l'insieme di tutte le stringhe su $\sum$, inclusa quella vuota ($\epsilon$)
- Usiamo $\sum^{+}$ per indicare tutte le stringhe non vuote su $\sum$

 
$L=0$ e' un linguaggio vuoto, che non contiene la stringa vuota $\epsilon$

### Operazioni sui linguaggio

|Operazione|Definizione|
---|---
Unione|$L_1\cup L_2$
Intersezione|$L_1\cap L_2$
Complemento(not)|$L=\sum^{*}-L$
Concatenzazione|$L_1L_2=\{uv\| u\in L_1,v\in L_2\}$
Potenza|$L^0=\{\epsilon\}$ e $L^{n+1}=LL^n$
Chiusura di Kleene(Arbitrarie)|$L^*=L^0\cup L^1\cup L^2 \cup ...$ 
Chiusura transitiva(non la stringa vuota)|$L^+=L^1\cup L^2 \cup ...$
# Automi riconoscitori
L'automa riconoscitore analizza il codice come una sequenza di caratteri, ricercando i **token** (costanti, operatori,simboli...) e produce a sua volta una sequenza di token da fornire al compilatore.

#### Costante numerica intera
una sequenza non vuota di cifre decimale, eventualmente preceduta dal segno

#### Costante numerica con virgola
Due sequenze di cifre decimale separate da un punto, eventualmente precedute dal segno

#### Identificatore
una sequenza non vuota di lettere, numeri e "_" che non iniziano con un numero che contiene almeno un carattere diverso da \_

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

## Automi non deterministici
Si ha un automa non deterministico quando il comportamento dell'automa non e' determinato, ovvero, a parita' di stato e simbolo letto, ha a disposizione piu' transizione tra cui "scegliere"

## Automi a stati finiti non deterministici

Un'**automa a stati finiti non deterministico** é un quintupla $A=\{Q,\Sigma,\delta,q_{0},F\}$ dove:
- $Q$ e' l'insieme finito degli **stati**
- $\Sigma$ e' l'**alfabeto** riconosciuto dall'automa
- $\delta:Q\times \Sigma \to P(Q)$ e' la funzione di transizione
- $q_{0}\in Q$ e' lo stato **iniziale**
- $F\subseteq Q$ e' l'insieme degli stati **finali**

Alcune osservazioni:
- $\delta(q,a)$ é l'**insieme** di stati in cui l'NFA di puó trovare partendo da $q$ e riconoscendo il simbolo $a$
- Se $\delta(q,a)$ é un singoletto, l'NFA ha una sola scelta
- Se $\delta(q,a)$ é vuoto, l'NFA rifiuta la scelta

### Funzione di transizione estesa

La sua funzione di  transizione estesa dell'automa é la funzione:

$\hat{\delta}:Q\times \Sigma \to Q$

definita per induzione come segue:
- $\hat{\delta}(q,\epsilon)=q$
- $\hat{\delta}(q,wa)=\delta(\hat{\delta}(q,w),a)$

La funzione ritornerá l'insime di stati in cui l'automa di potrá trovare dopo aver preso in input la stringa $arg[1]$ partendo dallo stato $arg[0]$.

### Linguaggio riconosciuto 

Un NFA riconosce le stringhe definite in $\delta$ che gli consentono di arrivare in uno qualsiasi dei suoi stati finali:

$L(A)=\{w\in \Sigma^* | \hat{\delta}(q_0,w)\cap F\ne 0\}$

### Tabella di transizione

Anche in questo caso l'automa si puó rappresentare in forma tabellare come segue:

Stato|b
--|--
$\to q_0$|$q_1$
$*q_1$|$q_0$

dove:
- Le righe corrispondono agli stati dell'automa
- Le colonne corrispondono ai simboli dell'alfabeto dell'automa
- Lo stato iniziale é marcato con $\to$
- Ogni stato finale é marcato con *
- La cella corrispomdente alla riga $q$ e alla colonna $b$ contiene l'insieme $\delta(q,a)$

### DFA -> NFA
Dato un automa a stati finiti **D** esiste un automa a stati non finiti **N** identico, ad esclusione della funzione di transizione ($L(N)=L(D)$)

$\delta_N(q,a)=\{\delta_D(q,a)\}$

possiamo quindi dimostrare per induzione su |$w$| che 

$\hat{\delta}_D(q_0,w)=p \Leftrightarrow \hat{\delta}_N(q_0,w)=\{p\}$
 
 concludiamo quindi che 
 
$\hat{\delta}_D(q_0,w)\in F \Leftrightarrow \hat{\delta}_N(q_0,w)\cap F\ne 0$

### NFA -> DFA
Dato un automa a stati non finiti (che ha un numero finito di stati), e' possibile tracciare tutti gli stati in cui l'NFA si puo' trovare durante in riconoscimento di una stringa all' interno di un DFA.

Gli stati dell'DFA saranno quindi $2^n$, dove $n$ é il numero di stati dell'NFA.
## Automi con ε-transizioni
Sono automi che possono eseguire transizioni spontanee **senza leggere** alcun simbolo nella stringa da riconoscere.

Ogni $\epsilon$-NFA é un **quintupla** $A=(Q,\Sigma,\delta,q_0,F)$ dove:
- $Q$ e' l'insieme finito degli **stati**
- $\Sigma$ e' l'**alfabeto** riconosciuto dall'automa
- $\delta:Q\times (\Sigma \cup \{\epsilon\})\to p(Q)$ e' la **funzione di transizione**
- $q_{0}\in Q$ e' lo stato **iniziale**
- $F\subseteq Q$ e' l'**insieme** degli stati **finali**

Alcune osservazioni:
- $\delta(q,a)$ é l'insieme degli stati in cui l'$\epsilon$-NFA  puó transire quando si trova nello stato $q$ leggendo il simbolo $a$
- $\delta(q,\epsilon)$ é l'insieme di stati in cui l'$\epsilon$-NFA puó **transire spostaneamente** quando si trova nello stato $q$ senza leggere alcun simbolo
### $\epsilon$ chiusura
Dato uno stato $q$, la sua **ECLOSE(q)** e' il piu' piccolo insime di stati tale per cui: 
- $q\in$ ECLOSE(q), includendo lo stato stesso e impedendogli di essere vuota
- se $p\in$ ECLOSE(q), allora $\delta(p,\epsilon)\subseteq$ ECLOSE(q), includiamo quindi tutte le transizioni per $\epsilon$

La $\epsilon$-chiusura di un insieme e' l'insieme delle $\epsilon$-chiusure dei suoi elementi.
Se l'insieme e' vuoto questa puo' essere vuota.

###### Esempio
![[Pasted image 20220103140233.png]]
$ECLOSE(q_1)=\{q_1,q_2,q_3,q_4,q_6\}$
$ECLOSE(q_2)=\{q_2,q_3,q_6\}$
$ECLOSE(q_3)=\{q_3,q_6\}$
$ECLOSE(q_4)=\{q_4\}$
$ECLOSE(q_5)=\{q_5,q_7\}$
$ECLOSE(q_6)=\{q_6\}$
$ECLOSE(q_7)=\{q_7\}$
### Fuzione di transizione estesa
La funzione di transizione estesa di un $\epsilon$-NFA e' la funzione

$\hat{\delta}:Q\times \Sigma^*\to p(Q)$

definito per induzione come segue:

- $\hat{\delta}(q,\epsilon)=ECLOSE(q)$
- $\hat{\delta}(q,wa)=\{r\in ECLOSE(\delta(p,a)) | p \in \hat{\delta}(q,w)\}$

### Linguaggio riconosciuto

L'automa riconosce una stringa $w$ se esiste un percorso etichettato con $w$ che lo porta dallo stato iniziale $q_{0}$ a uno dei suoi stati finali in **$F$**.

### NFA -> $\epsilon$-NFA
###### Teorema
Dato un NFA $N$, esiste un $\epsilon$-NFA $E$, t.c. $L(E) = L(N)$

###### Dim.
Basta osservare che un NFA è un caso particolare di un $\epsilon$-NFA

###### Conseguenze
- Ogni linguaggio regolare è riconoscouto da un $\epsilon$-NFA
- gli $\epsilon$-NFA hanno potere riconoscitivo almeno pari a quello dei DFA/NFA equivalenti

### $\epsilon$-NFA -> DFA
Dato un $\epsilon$-NFA $E$, esiste un DFA $D$ tale che $L(D)=L(E)$

###### Intuizione
- usiamo la costruzione per sottoinsiemi come nel caso NFA → DFA
- occorre fare attenzione agli stati raggiungibili da ε-transizioni 
- possiamo usare la nozione di ε-chiusura!

###### Conseguenze
- ogni linguaggio riconosciuto da un ε-NFA è **regolare** 
- commbinando questo risultato e quello della , concludiamo che ε-NFA, NFA e DFA hanno lo **stesso potere riconoscitivo**
# Espressioni regolari 
Rispetto ad un alfabeto $\Sigma$ di riferimento, le espressioni regolari sono definite come segue:
- $0$ ed $\epsilon$ sono espressioni regolari 
- se $a \in \Sigma$, allora $a$ e' un'espressione regolare
- se $E$ ed $F$ sono espressioni regolari, $E+F$ ed $EF$ sono espressioni regolari 
- se $E$ e' un'espressione regolare, **$E^{*}$** e' un'espresione regolare

## Convenzioni
- Per quanto riguarda la priorita', si una come convenzione la seguente priorita': + < concat < *
- Usiamo le parentesi per rendere disambigua la struttura

Forma|Significato
-|-
$L(0)=0$|Linguaggio vuoto
$L(\epsilon)=${$\epsilon$}|{$\epsilon$}
$L(a)=${$a$}|Simbolo dell'afabeto
$L(E+F)=L(E)\cup L(F)$|unione
$L(EF)=L(E)L(F)$|concatenazione
$L(E^{*})=L(E)^{*}$|chiusura di Kleene

Diciamo che $E$ ed $F$ sono equivalenti se $L(E)=L(F)$

### Esempio 
Il linguaggio generato da $(a+b)^{*}$ e' 
$L(a+b)^{*}$
$(L(a)\cup L(b))^{*}$
$(${$a$}$\cup${$b$}$)^{*}$
{$a,b$}$^{*}$
{$\epsilon,a,b,aa,bb,ab,ba,...$}

Il linguaggio generato da $(ab)^{*}$
$(L(a)L(b))^{*}$
({$a$}{$b$})$^{*}$
{$ab$}$^{*}$
{$\epsilon,ab,abab,abababa,...$}

### Proprieta' 
#### Unione
Proprieta'|Esempio
-|-
Commutativitá|$E+F=F+E$
Associativitá|$E+(F+G)=(E+F)+G$
Idempotenza|$E+E=E$
Identitá|$E+0=0+E=E$
#### Concatenazione
Proprieta'|Esempio
-|-
Associativitá|$E(FG)=(EF)G$
Identitá|$E\epsilon=\epsilon E=E$
Assorbimento|$E0=0E=0$
Distributivitá sinistra|$E(F+G)=EF+EG$
Distributivitá destra|$(E+F)G=EG+FG$
#### chiusura di Klenee
Proprieta'|Esempio
-|-
Idempotenza|$(E^{*})^{*}=E^{*}$
Casi banali|$\epsilon=0^{*}=\epsilon$

## Espressione regolare -> $\epsilon-NFA$
Data un'espressione regolare $E$, esiste un $\epsilon$-NFA $A$ tale che $L(A)=L(E)$, con esattamente uno stato finale.
#### Caso 0(Linguaggio vuoto)
In questo caso lo stato finale e quello inizale non sono cllegati in alcun modo

![[2021-10-06--1633512145_199x67_scrot.png]]
#### Caso $\epsilon$(Solo stringa vuota)
L'unisca transizione e' rappresentata dalla sola stringa vuota

![[2021-10-06--1633512590_185x64_scrot.png]]
#### Caso a(Linguaggio che contiene solo a)
L'unica transizione e' rappresentata dalla sola stringa "a".

![[2021-10-06--1633512759_171x60_scrot.png]]
#### Caso unione 
In questo casi si analizzano gli automi singolarmente, per poi ottenere un automa che riconosce il linguaggio generato dall'unione dei linguaggi.

![[2021-10-06--1633512920_376x175_scrot.png]]
#### Caso concatenzione
Si analizzano gli automi singolarmente, per ottenere un automa che parte dallo stato inizale del primo automa per arrivare allo stato finale del secondo automa, riconoscendo tutte le concatenazioni possibili.

![[2021-10-06--1633513037_411x112_scrot.png]]
#### Chiusura di Kleene
![[2021-10-06--1633513055_387x126_scrot.png]]

## Esempi
- stringhe di a, b e c che iniziano con due a e finiscono con due b
	$aa(a+b+c)^{*}bb$
- stringhe di 0 e 1 la cui lunghezza è un multiplo di 3
	$((0+1)(0+1)(0+1))^{*}$
- stringhe di 0 e 1 con un numero pari di 0
	$(1^{*}01^{*}0)^{*}1^{*}$
- stringhe di a, b e c che non contengono la sottostringa ab
	$(a^{*}c+b)^{*}a^{*}$
- costanti numeriche binarie pari senza 0 inutili a sinistra (es. 0, 10, ma non 010 o 11)
	$0+1(0+1)^{*}0$## Chiusura dei linguaggi regolari
Dati due lunguaggi **regolari** $L$ ed $L'$ andiamo ad osservare sei i linguaggi regolari generati dalle seguenti **operazioni** sono anch'essi regolari
### Unione e concatenazione
Dati due linguaggi regolari $L_{1}$ e $L_{2}$, essi sono chiusi rispetto all'unione e alla concatenzazione.

###### Dimostrazione
Date due espressioni regolari $E_1$ ed $E_2$ generate rispettivamente dal linguaggio di $L_1$ ed $L_2$ ($L_1=L(E_1)$ e $L_2=L(E_2)$), l'espressione regolare $E_1+E_2$ genererá sicuramente $L_1\cup L_2$, cosí come $E_1 E_2$ genererá sicuramente $L_1 L_2$.

### Complemento
Dato un linguaggio regolare $L$, esso e' chiuso rispetto al complento poiche $\overline{L}=L(B)$.

###### Dimostrazione
Sé un linguaggio é regolare allora esiste sicuramente un DFA $A$ in grado di riconoscerlo.

Definiamo ora un'altro DFA $B=(Q,\Sigma,\delta,q_0,Q-F)$, dove la definizione di stato finale é invertita e quindi ogni stato non finale lo sará invece e viceversa.

Allora é ovvio che se una stringa $w$ appartiene al linguaggio di $A$ non apparterrá al linguaggio di $B$

$w\in L(A)\Leftrightarrow \hat{\delta}(q_0,w)\in F \Leftrightarrow w \notin L(B)$

### Intersezione
I linguaggi regolari sono chiusi rispetto all'intersezione

###### Dimostrazione 
Dati due linguaggi regolari $L_{1}$ e $L_{2}$, $L_{1}\cap L_{2}$ e' un linguaggio regolare, poiche' per le leggi di de morgan: $L_{1}\cap L_{2}=\overline{\overline{L_{1}\cap L_{2}}}=\overline{\overline{L_{1}}\cup\overline{L_{2}}}$ e i linguaggi regolari sono chiusi per intersezioni ed unione.
### Differenza
I linguaggi regolari sono chiusi per differenza

###### Dimostrazione
Dati due linguaggi regolari $L_{1}$ e $L_{2}$,  sono chiusi per la differenza poiche' $L_{1}-L_{2}=L_{1}\cup\overline{L_{2}}$ e questi sono chiusi per intersezione e complemento.
### Inversione
I linguaggi regolari sono chiusi per inversione.

###### Dimostrazione
Se $L$ é un linguaggio regolare allora deve esistere un'espressione regolare $E$ riconosciuta dal linguaggio.

Definiamo quindi l'espressione regolare $E^R$ per induzione sulla struttura di $E$

$0^R=0$
$\epsilon^R=\epsilon$
$a^R=a$
$(E_1+E_2)^R=E^R_1+E^R_2$
$(E_1E_2)=E_2^RE^R_1$
$(E^*)^R=(E^R)^*$

Allora $L(E^R)=L(E)^R$, quindi $L^R$ é regolare.## Linguaggi non regolari
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
## Minimizzazione di un DFA
### Stati distinguibili
Dato un DFA $A$, 2 stati $p$ e $q$ dello stesso sono distinguibili se **esiste una stringa** per cui,partendo da questi, uno mi conduce in uno stato finale, mentre invece l'altro no.

### Stati indistinguibili
Dato un automa $L$, 2 stati $p$ e $q$ dello stesso sono indistinguibili se **per ogni stringa** ,partendo da questi, arrivo in uno **stesso stato** (anche non finale). 

$\hat{\delta}(p,w)\in F \Leftrightarrow\hat{\delta}(q,w)\in F$
per ogni $w\in \Sigma^*$.

Gli stati indistinguibili sono anche detti **ridondanti**.

Un automa e' ottimizzato se **non esistono** stati ridontanti.

Ogni stato e' **indistinguibile** da **se stesso**.

Se $p$ e' indistinguibile da $q$ e viceversa allora sono indistinguibili.

La relazione di indistingibilita' tra stati e' indicata dalla tilde "~". inoltre indichiamo con [q] la classe di equivalenza di q ([q]={$q\in Q|p$~$q$}).

#### Algoritmo per trovare gli stati indistinguibili
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

#### Minimizzazione dato la tabella di indistinguibilitá 

Per ottenere un DFA minimo che presenta degli stati indistinguibili, **partendo dalla tabella** posso andare a **ricostruire** la sua **struttura** fondendo insieme gli **stati indistinguibili**(generando delle **coppie**) e collegandoli agli stati distinguibili come den DFA non minimo.

###### Esempio
In riferimento all'esempio del punto precedente

![[Pasted image 20220103174115.png]]

#### Equivalenza tra automi
Dati 2 automi $P$ e $Q$, e' possibile verificare la loro equivalenza con il seguente processo:
-  Creo l'unione dei 2 DFA $A=(Q_1\cup Q_2,\Sigma,\delta,q_1,F_1\cup F_2)$ dove
	-  $\delta(q,a)=\{^{\delta_1(q,a)if( q\in Q_1)}_{\delta_2(q,a)if( q\in Q_2)}$
-  Eseguo l'algoritmo riempi-tabella su P
-  $P$ e $Q$ sono equivalenti solo se $p$ e $q$ sono equivalenti

# Linguaggi Liberi
## Grammatica libera
Una grammatica libera e' una quadrupla del tipo $G=(V,T,P,S)$ dove :
- $V$ e' un'insieme finito di **variabili**(simboli **non** terminali)
- $T$ e' un alfabeto di **simboli terminali**
- $P$ e' un'insieme finito di produzioni(coppie Variablie -> Stringa di simboli, terminali o non) della forma $A\to \alpha$ in cui:
	- $A\in V$ e' detta testa della produzione
	- $\alpha \in(V\cup T)^{*}$ e' detto corpo della produzione
- $S\in V$ e' il simbolo inizale della gramamatica.
 
 Le grammatiche possono generare tutti i linguaggi regolari e non.
 ### Convenzione
 - Con le lettere **minuscole** indichiamo gli elementi di T, quindi i simboli **terminali**.
 - Con le lettere **maiuscole** indichiamo gli elementi di V, quindi le **variabili**.
 - Con $X,Y,Z,...$ indichiamo i simboli($\in V\cup T$)
 - Con $u,v,w,...$ denotiamo le stringhe di simboli($(V\cup T)^*$)
 - Con le lettere $u,v,w..$ indichiamo gli elementi di $T^{*}$

### Derivazioni

Data una grammatica $G$, definiamo una derivazione cosí come segue:

- scriviamo $\alpha A \beta \Rightarrow_G \alpha \gamma \beta$ se $A\to \gamma \in P$
	- Diciamo quindi che $\alpha \gamma \beta$ **deriva in un passo** da $\alpha A \beta$ in $G$
- Scriviamo $\Rightarrow_G^*$ per la chiusura riflessiva e transitiva di $\Rightarrow_G$, ovvero:
	- una variabile deriva se stessa in 0 o piú passi ($\alpha \Rightarrow^*_G \alpha$)
	- se $\alpha \Rightarrow_G \beta$ e $\beta \Rightarrow^*_G \gamma$, allora $\alpha \Rightarrow^*_G \gamma$

###### Esempio
Data la grammatica $G=(\{A\},\{0,1\},\{A\to \epsilon|0|1|0A0|1A1\},A)$, ecco alcune possibili derivazioni:
- $A\to \epsilon$
- $A\to 0$
- $A\to 1$
- $A\to 0A0\to 00$
- ...
###  Linguaggio generato da una grammatica

Dato una grammatica G, il linguaggio generato da esso e' denotato da L(G) ed e'e definito come 

$L(G)=\{w\in T^{*}|S\Rightarrow^{*}_{g}w\}$

###### Esempio
La grammatica $G$ dell'esempio precedente é 

$L(G)=\{w\in \{0,1\}^*|w=w^R\}$

Un linguaggio $L$ e' libero se esiste una grammatica libera che lo genera.

Le grammatiche possono generare tutti i linguaggi regolari, ma possono generare anche linguaggi non regolari, quindi i linguaggi liberi includono propriamente i linguaggi regolari.


 
 ## Alberi sintattici
Data una grammatica $G=(V,T,P,S)$, gli alberi sintattici di $G$ sono alberi con le seguenti caratteristiche:
- Ogni nodo interno diverso da una foglia e' etichettato con $V$
- Ogni foglia e' etichettata con $V$,con $T$(terminale) o con $\epsilon$
- Se una foglia e' etichettata da $\epsilon$ ,e' l'unico figlio del suo parent
- Se un nodo e' etichettato con $A$, i suoi figli sono definiti con una produzione del tipo $A\to X_1X_2X_3...X_n$

Il **prodotto** di un'albero sintattico é la **stringa** ottenuta **concatenando** da sinistra verso destra le etichette di **tutte** le **foglie** dell'albero

###### Esempio

![[Pasted image 20220104120602.png]]

### Grammatiche ambigue
Una grammatica é **ambigua** se ammette **piú alberi** sintattici distinti con lo **stesso prodotto**.

Basta trovare due alberi sintattici distinti con lo stesso prodotto per dire che una grammatica ambigua, trovare due derivazioni distinte che generano la stessa stringa **non** é sufficiente.

###### Esempio 
![[Pasted image 20220104121019.png]]
Entrambi questi alberi rappresentano l'espressione $1+2\times 3$

#### Derivazioni canoniche
Una derivazione $X\Rightarrow^* \alpha$ si dice **derivazione a sinistra** se ad ogni passo viene riscritta la **variabile** che si trova a **sinistra**.

Usiamo $\Rightarrow_{lm}$ e $\Rightarrow_{lm}^*$ come simboli per la derivazione sinistra, e scularmente utilizziamo $\Rightarrow_{rm}$ e $\Rightarrow_{rm}^*$ per la derivazione destra.

Se esistono **due** derivazioni canoniche **distinte** dello **stesso tipo** nella grammatica $G$ per derivare la stessa stringa, allora la grammatica é **ambigua**. 

###### Esempio

![[Pasted image 20220104122344.png]]


## Eliminazione dell'ambiguita'
Eliminare l'ambiguita' di una grammatica significa ottenerne una **equivalente** non ambigua. Attraverso questo la grammatica solitamente si complica.

La strategia da utilizzare é **stratificare** le **espressioni**, ovvero anziché mettere tutte le produzioni nella stessa categoria, le **divido** in diverse **espressioni**,**termini** e **fattori**.

###### Esempio

Per disambiguare la grammatica $G=(\{E\},\{[0-9],+,*,(,)\},\{E\to [0-9]|E+E|E*E|(E)\},E)$

si puó stratificare la grammatica nella seguente maniera:

$G=(\{E,T,F\},\{[0-9],+,*,(,)\},P,E)$

dove P é l'insieme delle produzioni:
$E\to T| E+T$
$T\to F| T*F$
$F\to 0|..|9|(E)$
## Automi a pila
Un' **automa a pila**(o **PDA**) e' una settupla del tipo $A=(Q,\Sigma,\Gamma,\delta,q_0,Z_0,F)$ dove
- $Q$ e' un **insieme** finito di **stati**
- $\Sigma$ e' l'alfabeto di **input**
- $\Gamma$ e' l'alfabeto della **pila**
- $\delta: Q\times(\Sigma\cup\{\epsilon\})\times\Gamma\to p(Q \times\Gamma^*)$
- $q_0\in Q$ e' lo **stato iniziale**
- $Z_0\in \Gamma$ e' il **simbolo iniziale** presente sulla pila, e quindi in terminatore
- $F\subset Q$ e' l'insieme degli **stati finali**

Generalmente $\Sigma$ e $\Gamma$ sono distinte, poiché il terminatore $Z_0\in \Gamma$, anche se in moltio casi $\Sigma \subset \Gamma$.

##### Funzione di transizione

A differenza dei DFA, un'automa a pila potrebbe aver la necessitá di **leggere** il contenuto della **pila** per determianre il suo **comportamento**.

La funzione di transizione prende quindi in input la **tripla**:
- $Q$: lo stato in cui si trova l'automa
- $\Sigma \cup \{\epsilon\}$: un simbolo della stringa da riconoscere, oppure epsilon nel caso di una transizione spontanea
- $\Gamma$: un elemento della pila, che verrá rimosso dalla stessa

La funzione pone quindi in output la coppia:
- $Q$: lo stato in cui si troverá dopo il riconoscimento
- $\Gamma^*$: l'insieme degli elementi che verranno aggiunti alla pila
	- Notare che $\epsilon \in \Gamma^*$

###### Esempio
Un'esempio del riconoscimento delle stringhe $a^n b^n$ é il seguente

![[Pasted image 20220104154437.png]]

### Descrizioni istantanee
Per conoscere a **configurazione globale** di un PDA $P$ durante il processo di riconoscimento si usano le **descrizioni istantanee**, ovvero delle triple $(q,w,\alpha)$, dove:
- $q\in Q$ e' lo **stato** in cui si trova l'automa
- $w\in \Sigma$ e' ció che rimane da riconoscere  della **stringa** in input
- $\alpha \in \Gamma^*$ e' il **contenuto** della **pila** dalla cima al fondo

### Mosse di un'automa a pila
Dato un'automa a pila $P$, definiamo con la relazione binaria $\vdash_p$,che descrive la transizione da una descrizione instantanea ad un'altra, nella seguente maniera:

- $(q,aw,X\beta)\vdash_p(p,w,\alpha \beta)se(p\alpha)\in \delta(q,a,X)$
	- In questo caso la stringa da riconoscere non é vuota($aw$)

- $(q,w,X\beta)\vdash_p(p,w,\alpha \beta)se(p\alpha)\in \delta(q,\epsilon,X)$

Diciamo un PDA fa una mossa da una D.I. A ad una B se vale la relazione $A\vdash_p B$

###### Esempio

![[Pasted image 20220104164517.png]]

### Linguaggio accettato da un'automa a pila 
Dato un'automa a pila, il linguaggio
e' l'insieme delle stringhe per le quali, partendo dalla descrizione istantanea iniziale,l'automa puo' raggiungere in 0 o piu' **mosse** un suo stato finale, la **stringa** di input e' stata **consumata** completamente e il contenuto della **pila** e' **arbitrario** nel riconoscimento per stato finale, oppure **vuoto** nel riconoscimento per pila vuota.

Il Linguaggio accettato da $P$ per stato finale é 

$L(P)=\{w\in\Sigma^*|(q_0,w,Z_0)\vdash_P^*(q,\epsilon,\alpha),q\in F\}$

mentre il linguaggio accettato da $P$ per pila vuota é 

$N(P)=\{w\in \Sigma^*|(q_0,w,Z_0)\vdash^*_P(q,\epsilon,\epsilon)\}$
### Proprietá di chiusura dei linguaggi regolari

#### Unione e concatenazione

I linguaggi liberi sono chiusi per contatenazione

###### Dimostrazione 
Dati due linguaggi liberi $L_1$ ed $L_2$, esistono sicuramente due grammatiche libere t.c. $L_1=L(G_1)$ e $L_2=L(G_2)$.

Possiamo assumere che le grammatiche **non** abbiano **variabili** in **comune** ($V_1\cap V_2=0$) e che il **simbolo iniziale** non appartenga alle variabili di **nessuna** dei due grammatiche($S\notin V_1\cup V_2$), poiché e sempre possibile scegliere **nuovi nomi** per le grammatiche, o quantomeno rinominarle.

Quindi la grammatica 

$(V_1\cup V_2,T_1\cup T_2,P_1 \cup P_2\cup \{S\to S_1|S_2\},S)$

genera $L_1\cup L_2$, mentre la grammatica

$(V_1\cup V_2,T_1\cup T_2,P_1 \cup P_2\cup \{S\to S_1S_2\},S)$

genera $L_1L_2$.

#### Intersezione

I linguaggi liberi **non** sono chiusi per intersezione.

###### Dimostrazione 
I linguaggi 
- $L_1=\{a^nb^nc^m|m,n\ge 0\}$
- $L_2=\{a^mb^nc^n|m,n\ge 0\}$

sono liberi. Se i linguaggi liberi fossero chiusi per intersezione, allora anche il linguaggio

$L_1\cap L_2=\{a^nb^nc^n|n\ge 0\}$

sarebbe libero, ma abbiamo dimostrato che non lo é.

##### Intersezione con un linguaggio regolare

Se $L$ é un linguaggio libero ed $R$ é un linguaggio regolare, allora $L\cap R$ é un linguaggio libero.

###### Dimostrazione

Se $L$ è un linguaggio libero allora esiste un PDA che accetta $L$ per stato finale.
Se $R$ è un linguaggio regolare allora esiste un DFA che accetta $R$.
Si può costruire quindi un PDA che accetta $L\cap R$ per stato finale costruendo il “prodotto” di $P$ ed $M$.

##### Complemento e differenza
I linguaggi liberi non sono chiusi per complemento e differenza

###### Dimostrazione 
I linguaggi liberi sono chiusi per unione. Se fossero chiusi anche per complemento, allora avremmo che

$L_1\cap L_2=\overline{\overline{L_1\cap L_2}=\overline{L_1}\cup \overline{L_2}}$

sarebbe sempre un linguaggio libero, contrariamente a quanto dimostrato in precedenza.

##### Inversione
Se $L$ é un linguaggio libero, allora $L^R$ é un linguaggio libero.
###### Dimostrazione 
# Parsing
Data una grammatica $G$ e una stringa $w\in T^*$, dobbiamo determianre se esiste un'albero sintattico di $G$ con radice $S$ e prodotto $w$.

La costruzione di un'automa corrispondente a $G$ produce un PDA non deterministico, e per alcune gramamtiche non é possibile trovare un DPDA.

Identifichiamo quindi una famiglia di grammatiche libere per le quali é possibile costruire un parser deterministico.
## Strategia di parsing top-down

Data una grammatica $G=(V,T,P,S)$ e una stringa $w\in T^*$, il parser cerca di ottenere una derivazione sinistra $S\to^*_{im}$ in cui, al passo $i$, il parser sa' che 

$S\to^*_{im}uA\beta$

ovvero la derivazione canonica sinistra che ci permetterebbe di ottenere $u$(stringa di simboli terminali) e' indicato come sopra.

Deve inoltre stabilire se 

$uA\beta \to^*_{im}w$

attraverso le derivazioni.

Ci sono due casi da considerare:
- Se $u$ non e' un prefisso $w$, allora il parser rifiuta $w$ poiche' i simboli terminali non possono essere riscritti.
- Se $w=uav$ allora il parser deve segliere una produzione per riscrivere A($A\to \alpha_1|...|\alpha_n$) e puo' usare $a$ come "guida" per riconoscere il prossimo passo da effettuare.
	- Es:Supponiamo di avere due produzioni $A\to aA|b$, utilizziamo la prima poiche' il corpo della produzione ci permette di generare $a$. 
	- Se abbiamo invece $A\to aA|b|C$ sobbiamo anche controllare le produzioni con $C$ poiche' potrebbe generare $a$.
	- Se abbiamo produzioni distinte che generano un prefisso comune non siamo invece di determinare qual'e' la produzione giusta da utilizzare(Es:$A\to aB|aC$)
### Stringa annullabile 
Una stringa $\alpha$(terminale o non) e' annullabile($NULL(\alpha)$) se e solo se puo' essere riscritta nella stringa vuota

Per determinarle l'annullabilita' utilizziamo un algoritmo:
- Se $Null(X_1),...,Null(X_n)$ allora la stringa e' annullabile
	- Se ogni produzione e' annullabile($X_1,...,X_n\to \epsilon$) allora la stringa e' annullabile
- Se $A\to \alpha \in P$ e $Null(\alpha)$, allora $Null(A)$

Note
- Una stringa che contiene dei simboli terminali non e' annullabile
- $\epsilon$ e' sempre annullabile
- Se una produzione di $A$ e' $\epsilon$, allora $Null(A)$

### Inizio di una stringa (FIRST)

Indichiamo con **First($\alpha$)** gli inizi di $\alpha$  l'inizio dei simboli terminali che possiamo trovare all'inizio delle stringe generate da $\alpha$

$FIRST(\alpha)=\{a\in T|\alpha \to^*_G \alpha \beta\}$

E' possibile calcolare $FIRST(\alpha)$ nella seguente maniera:
- $FIRST(\epsilon)=0$
- $FIRST(a)=\{a\}$
- $FIRST(A)=\bigcup _{A\to a} FIRST(\alpha)$
- $FIRST(X\alpha)=\{^{FIRST(X)\cup FIRST(\alpha) se NULL(X)}_{FIRST(X) altrimenti}$

### Seguiti di una variabile (FOLLOW)
Data una grammatica $G=\{V,T,P,S\}$ e una variabile $A \in V$Indichiamo come $FOLLOW(A)$ un'insime di simboli terminali $a$ che possiamo trovare dopo un'occorenza di $A$ dopo uan derivazione anche non canonica

$FOLLOW(A)=\{a \in T|S\to^*_G \alpha A\alpha B\}$

E' possibile calcolare il $FOLLOW$ nella seguente maniera:

Fase 1:
- Annotiamo le relazioni appartenenza ed inclusione insiemistica secondo il seguente algoritmo:
	- Annotiamo $\$ \in FOLLOW(S)$
	- Ripetiamo per ogni produzione e ogni variabile del corpo:
		- Se $A\to \alpha B\beta$ annotiamo $FIRST(\beta)\subseteq FOLLOW(B)$
		- Se $A\in \alpha B\beta$ e $NULL(\beta)$, allora $FOLLOW(A)\subseteq FOLLOW(B)$

Fase 2:
- Le relazioni sono strate tutte annotate, quindi partendo dai simboli di relazione diretta determiniamo i seguiti

#### Esempio 1
$S\to Ac|Ba$
$A\to \epsilon|a$
$B\to b$
$C\to a|Cb$
$D\to \epsilon|d|Db$

allora
$Null(A)$ e $Null(D)$
$\$\in FOLLOW(S)$
$c\in FOLLOW(A)$
$a\in FOLLOW(B)$
$b\in FOLLOW(C)$
$b\in FOLLOW(D)$

da cui generiamo la tabella

X|FOLLOW(X)
--|--
S|$\{\$\}$
A|$\{c\}$
B|$\{a\}$
C|$\{b\}$
D|$\{b\}$

#### Esempio 2
$E\to TE'$
$E'\to +TE'|\epsilon$
$T\to FT'$
$T'\to *FT'|\epsilon$
$F\to (E)|id$
allora
$\$\in FOLLOW(E)$
$FIRST(E')\subseteq FOLLOW(T)$||$+\in FOLLOW(T)$
$FOLLOW(E)\subseteq FOLLOW(T)$
$FOLLOW(E)\subseteq FOLLOW(E')$
$FOLLOW(E')\subseteq FOLLOW(T)$
$FIRST(T')\subseteq FOLLOW(F)$||$*\in FOLLOW(F)$
$FOLLOW(T)\subseteq FOLLOW(F)$
$FOLLOW(T)\subseteq FOLLOW(T')$
$FOLLOW(T')\subseteq FOLLOW(F)$
$)\in FOLLOW(E)$

da cui possiamo calcolare

Var|Follow
--|--
E|$,)
E'|$,)
T|$,+,)
T'|$,+,)
F|$,+,*,)

Prendendo in cosiderazione innanzitutto i simboli di appartenenza, e propagandolo in base ai follow seguendo i versi delle inclusioni(*left to right*).

#### Insiemi guida
Data una grammatica qualsiasi e una produzione di questa grammatica($A\to \alpha$), definiamo insieme guida di una produzione l'insieme:

$GUIDA(A\to \alpha)=\displaystyle \{^{FIRS(\alpha)\cup FOLLOW(A) se NULL(\alpha)}_{FIRST(\alpha) altrimenti}$

Ci permettono di intuire la riscrittura giusta che il parser deve effettuare al fine di riconoscere al fine del riconoscimento di una stringa, attraverso il controllo del prossimo carattere e controllando a quale insieme guida appartiene.

Nel caso gli insiemi guida non sono disguinti il parser va' in errore

#### Grammatica LL(1)
Un grammatica e' definita LL(1) se per ogni coppia di produzioni distinte per la stessa variabile($A\to \alpha$ e $A\to \beta$) gli insiemi guida hanno intersezione vuota,ovvero sono disgiunti

$Guida(A\to \alpha)\cap GUIDA(A\to \beta)=0$

##### Esempi
Calcoliamo gli insiemi guida
$A\to BC|D$
$B\to \epsilon|a$
$C\to b|cCc$
$D\to \epsilon|CD$
I simboli annullabili sono
$NULL(B)$
$NULL(D)$
$NULL(A)$
I first sono
$FIRST(A)=FIRST(BC)\cup FIRST(D)=FIRST(B)\cup FIRST(C)\cup FIRST(D)=\{a,b,c\}$
$FIRST(B)=FIRST(\epsilon)\cup FIRST(A)=\{a\}$
$FIRST(C)=\{b,c\}$
$FIRST(D)=\{b,c\}$
I follow sono:
$\$\in FOLLOW(A)$
$b.c\in FOLLOW(C)$
$FOLLOW\subseteq FOLLOW(C)$
$FOLLOW(A)\subseteq FOLLOW(D)$
$c\in FOLLOW(C)$
$b,c\in FOLLOW(C)$
$FOLLOW(D)\subseteq FOLLOW(C)$
generiamo quindi la seguente tabella

Var|Follow
--|--
A|$
B|b,c
C|$,b,c
D|$

Calcoliamo alcuni insiemi guida
$GUIDA(A\to BC)=FIRST(BC)=FIRST(B)\cup FIRST(C)=\{a,b,c\}$
poiche' $BC$ non e' annullabile
$GUIDA(A\to D)=FIRST(D)\cup FOLLOW(A)=\{\$,b,c\}$
Possiamo quindi concludere che non e' una grammatica LL(1) poiche' gli insiemi guida sopra citati non sono disgiunti

$GUIDA(B\to \epsilon)=FIRST(\epsilon)\cup FOLLOW(B)=\{b,c\}$
$GUIDA(B\to a)=\{a\}$
### Parsing ricorsivo discendente
Per realizzare un parser basato sulla **ricorsione** usiamo la pila del linguaggio di programmazione per **ricordare** il **suffisso** della forma sentenziale sinistra da riconoscere.

#### Elementi chiave
- Il parser ha una **procedura**(metodo) per ogni **variabile** della grammatica
- La procedura $A$ nel parser riconsoce le stringhe generate da $A$ nella grammatica
- La procedura $A$ usa il **simbolo** corrente e gli **insiemi guida** per scegliere la produzione da usare per riscrivere $A$
- Per ogni **simbolo** $X$ trovato nel corpo della produzione:
	- Se è un simbolo **terminale**, il metodo **controlla** che il simbolo corrente sia proprio $X$ e fa **avanzare** il **lexer** al simbolo successivo. In caso contrario, il metodo segnala un errore di sintassi.
	- Se é una **variabile**, il metodo invoca la **procedura** $X$


##### Esempio: Parser per il linguaggio $A^nB^n$
###### Grammatica
$S\to aSb|\epsilon$
###### Insiemi guida
$Guida(A\to aSb)=\{a\}$
$Guida(A\to \epsilon)=\{b,\$\}$
###### Codice del parser
```java
public class AnBn extends Parser { 
	protected void S() { 
		switch (peek()) { 
			case 'a': // S → aSb 
				match('a'); 
				S(); 
				match('b'); 
				break; 
			case 'b': // S → ε 
			case '$': 
				break; 
			default: throw error(); } 
	} 
}
```

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
## Traduzione
Un **parser** ci permette solo di capire se un'espressione é corretta sintatticamente,

Per valutare le espressioni vogliamo produrre **informazioni** aggiuntive al riconoscimento, per far cio' **associamo** ad ogni **nodo** dell'albero associamo degli **attributi** che ci permettano di capire il valore delle sottoespressioni corrispondente ad un certo sottoalbero.

![[Pasted image 20220110143220.png]]


### Definizioni dirette dalla sintassi

#### Prefazione

Un **attributo** è una **coppia** (nome, valore) che rappresenta una qualunque **informazione** associata ad un **nodo** di un albero sintattico.

Un **albero** sintattico **annotato** è un albero sintattico in cui ogni **nodo** può essere annotato con **zero o più attributi**.

#### Definizione

Una **Definizione Diretta dalla Sintassi ** (o SDD, da
*Syntax-Directed Definition*) è una grammatica le
cui produzioni sono associate a zero o più **regole
semantiche** che specificano come calcolare il
valore degli attributi associati ai nodi degli alberi
sintattici della grammatica.

Il **valore** di eventuali **attributi** associati ai simboli terminali è fornito dal **lexer**.

###### Esempio

![[Pasted image 20220110143834.png]]

#### Attributi sintetizzati 
Un attributo di un nodo $N$ in un'albero annotato si dice **sintetizzato** se il suo **valore** dipende da quello degli **attributi e dei figli ** di $N$ ed eventualmente dagli attributi di $N$ **stesso**.

Il valore di un attributo sintetizzato per da un nodo $N$ e' determinato da una regola semantica associata ad una sua produzione.

###### Esempio

![[Pasted image 20220110144420.png]]

Il valore dell'attributo sintetizzato $s$ associato alla variabile $A$ in una sua produzione $A\to X_1X_2..X_n$ é indicato nella seguente maniera:

- $A.s=f(X_1.a_1,X_2.a_2,...,X_n.a_n)$

#### Attributi ereditati 

Un **attributo** di un nodo $N$ in un albero annotato si dice **ereditato** se il suo valore dipende da quello degli attributi del padre e dei fratelli.

###### Esempio

Il valore dell'attributo $e$ associato alla vairabile $A$ per una produzione $B\to X_1X_2..A..X_n$ é indicato nella seguente maniera:

- $A.e=f(B.a,X_1.a_1,X_2.a_2,...,X_n.a_n)$


### Ordine ddi valutazione degli attributi

#### Grafo delle dipendenze

Se il **calcolo** di un'**attributo** sintetizzato (es:$A.a$) richieda di **conoscere** il valore di un'**altro attributo** (es:$B.b$), allora scriviamo

$A.a=f(..,B.b,..)$

Per indicare ció introduciamo un **grafo delle dipendenze**, che attraverso l'utilizzo di <i style="color:red;">frecce rosse tratteggiate</i>, ci permette di indicare le **dipendenze** per la sintesi di un'attributo.

Se il grafo delle dipendenze contiene dei **cicli**, **non** é possibile trovare un'**ordine** di valutazione degli attributi.

#### Definizione S-attribuita
Una SDD si dice **S-attribuita** se contiene **solo** attributi **sintetizzati**.

#### Definizione L-attribuita
Una SDD si dice **L-attribuita** se per ogni **produzione** $A\to X_1X_2...X_n$ ed ogni **attributo ereditato** $X_i.e$, la **regola** semantica che definisce i valori di $X_i.e$ **dipende** solo da
- gli **attributi ereditati** da $A$
- gli **attributi sintetizzati** ed **ereditati** dal corpo della produzione ma a **sinistra** di $X_i$

##### Osservazioni
- Ogni SDD é sia S-attribuita che L-attribuita
- Ogni SDD L-attribuita ha un grafo delle dipendenze aciclico
### Schemi di Traduzione
Uno **schema di traduzione** (o **SDT**, da Syntax-Directed Translation scheme) è una **grammatica** in cui le **produzioni** sono **arricchite** da frammenti di **codice** detti **azioni semantiche** che sono eseguite quando tutti i simboli alla loro sinistra sono stati riconosciuti.

###### Esempi
Produzione|Produzione+Azioni|Descrizione
--|--|--
$A\to BC$|$A\to BC\{code\}$|Il codice viene seguito dopo il riconoscimento di $BC$
$A\to BC$|$A\to B\{code\}C$|Il codive viene seguito dopo il riconoscimento di $B$ ma prima di quello di $C$
$A\to BC$|$A\to \{code_1\}BC\{code_2\}$|Il primo codice viene eseguito dopo la riscrittura di $A$, mentre il secondo dopo il riconoscimento di $BC$
$A\to \epsilon$|$a\to \{code\}$|Il codice viene eseguito dopo la riscrittura di $A$

#### Differenze tra regole e azioni semantiche

Regole semantiche(SDD)|Azioni semantiche(SDT)
--|--
Specificano come ottenere il valore degli attributi|Specificanono come ottenere il valore degli attributi, ma  possono contenere anche codice arbitrario
Sono valutate seguendo il grafo delle dipendenze, in ordine implicito|Sono eseguite in ordine esplicito, in base alla loro posizione nel corpo della produzione
Richiedono la costruzione di un'albero annotato, poiché valutate in ordine arbitrario|Possono essere integrato ad un parser ricorsivo discendente, poiché eseguite da destra verso sinistra 

#### Conversione da SDD L-attribuita a SDT

Data una SDD L-attribuita, si può ottenere uno SDT corrispondente nel modo seguente.

Per ogni produzione $A\to X_1X_2..X_n$ della grammatica:

- Subito prima di $X_i$, con $i>1$ si **aggiunge** un'**azione** semantica che calcola il valore degli attributi **ereditati** di $X_i$
- In **fondo** alla produzione (dopo $X_n$), aggiungo un'azione semantica che calcola il valore di **tutti** gli attributi **sintetizzati** da $A$

#### Parser ricorsivo discendente di una SDT

Per integrare una SDT in un parser ricorsivo discendente, questo deve avere una procedura per ogni variabile che riconosce le stringhe generate dalla stessa.

La procedura ha tanti argomenti quanti sono gli attributi ereditati e restituisce tanti valori quanti sono gli attributi sintetizzati.

Per ogni simbolo o azione semantica $X$ nel corpo della produzione scelta:

- Se $X$ é un **simbolo terminale**, il metodo **controlla** che sia proprio $X$, per poi far **avanzare** il **lexer** se é vero.
- Se $X$ é una **variabile**, viene invocata la **procedura** $X$, passando i suoi attributi **ereditati** come **argomenti** e raccogliendo in **variabili** locali gli attributi **sintetizzati** restituiti dalla procedura.
- Se $X$ é un'**azione semantica**, il metodo la **esegue**.

###### Esempio

![[Pasted image 20220112165148.png]]

```java
private int S() {
	switch (peek()) {
		case 'a': { // S → aSb 
			check('a'); 
			int S_n = S(); 
			check('b'); 
			return S_n + 1; } 
		case 'b': // S → ε 
		case '$': 
			return 0; 
		default: 
			throw error("S");
	} 
}
```

#### Traduzione "on-the-fly"
Un attributo sintetizzato si dice principale se:
1. Il suo valore **include una concatenzazione ** dei valori dello stesso attributo, cioe' il corpo delle variabili di ogni produzione 
2. La concatenazione rispetta sempre l'ordine di comparsa delle variabili nel corpo della produzione 

$E\to E_1+T\{E.post=E_1.post||T.post||"T"\}$

Gli attributi principali possono essere eliminati “emettendo al volo” solo gli elementi ausiliari nel punto in cui devono comparire. ### Codice intermedio
 
 Stabilito che il programma da tradurre è sintatticamente corretto, il compilatore lo deve tradurre in un programma equivalente scritto in codice intermedio.
 
 Per far ció utiliziamo il bytecode di java come codice intermedio.
 
 ![[Pasted image 20220112181117.png]]
 
 Non aggiungo la spiegazione poiché giá vista ad architettura degli elaboratori.
 
 #### Comandi
 
 Nome | Significato
---|---|
BIPUSH *Byte*| Scrive un byte in cima allo stack
DUP|Duplica la parola in cima allo stack
GOTO *offset*| Diramazione incondizionata
IADD|Somma le 2 parole in cima allo stack
IAND|Sostituisce le parole in cima allo stack con il loro AND
IFEQ *offset*| (IF EQUALS (0)) Esegue una diramazione se la parola in cima allo stack è zero
IFLT *offset*|Esegue una diramazione se la parola in cima allo stack è negativa
IF_ICMPEQ *offset*| (COMPARE EQUALS) Effettua una diramazione se le 2 parole in cima allo stack sono uguali
IINC *var* *const*| Aggiunge una costante ad una variabile locale
ILOAD *var*| Scrive una variabile locale in cima allo stack
INVOKEVIRTUAL *met*| invoca un metodo
IOR|Sostituisce le 2 parole in cima allo stack con il loro OR
IRETURN|Termina il metodo restituendo un valore intero
ISTORE *var*|Memorizza la variabile in cima allo stack come una variabile locale
ISUB|Sostituisce le 2 parole in cima llo stack con la loro differenza
LDC *index*| Scrive sullo stack una costante proveniente da una porzione di memoria
NOP|Non fa niente
POP|Rimuove l'elemento in cima allo stack
SWAP|Scambia le 2 parole in cima allo stack
INEG|Nega la parola in cima allo stack
IMUL| Moltiplicazione dei 2 valori in cima allo stack
IDIV| Divisione dei 2 valori in cima allo stack
IREM| Modulo dei 2 valori in cima allo stack
IF_ICMPNE *offset*| Salta se le 2 parole in cima allo stack non sono uguali
IF_ICMPLE| flavor con il less equal $\le$
IF_ICMPGE| flavor con il less equal $\ge$
IF_ICMPLT| flavor con il less equal $\lt$
IF_ICMPGT| flavor con il less equal $\gt$
NEWARRAY|Crea un'array della lunghezza del valore sulla pila
ARRAYLENGTH| Deposita sulla pila la lunghezza dell'array presente sulla stessa
IALOAD| Carica sulla pila la posizione della parola in cima e dell'array in seconda posizione
IASTORE| Assegna il valore in cima alla posizione i(seconda) nell'array in terza posizione# Introduzione
Inizialmento gli elaboratori venivano programmati fornendo delle istruzioni in codice macchina, che il processore poteva eseguire direttamente, ma scrivere istruzioni risultava difficile.

Naque quindi la necessita' di usare dei linguaggi di programmazione per scrivere programmi a livello piu' alto. 

Il compilatore si pone quindi tra il linguaggio umano a quello macchina, traducendo il programma scritto dall' utente e riscriverlo in un programma equivalente a linguaggio macchina.

## Fasi di un compilatore
- Analisi Lessicale 
- Analisi Sintatica 
- Generazione del codice intermedio

## Alfabeto 
Un alfabeto e' un'inseme finito e non vuoto di simboli:

- Utlizziamo $\sum$ per indicare l'alfabeto generico 
- utilizziamo $a,b,c..$  per indicare generici simboli

## Stringhe
Una **stringa** su un alfabeto $\sum$ e' una sequenza **finita** di simboli in $\sum$
- Usiamo $u,v,w...$ per indicare stringhe generice
- Usiamo $\epsilon$ per indicare una **stringa vuota**  composta da *0 simboli*
### Operazioni su stringhe 
La **lunghezza** di una stringa $u$ e' il numero di simboli di cui e' costituita e si indica con $|u|$ .

La **concatenazione** di $u$ e $v$ e' indicata con $uv$, attacando la sequenza di $u$ dopo la sequenza di $v$. 

- La concatenazione é **neutra** rispetto alla **stringa vuota** ($u\epsilon=u$), **associtativa** ($u(vw)=(uv)w$), ma **non commutativa** ($uv\ne vu$)

La **lunghezza** della concatenzione sara' uguale alla somma della lunghezza delle sue stringhe.

Un **suffiso** di una stringa se la concatenazione di essa con un'altra stringa e' uguale ad un'altra.

L'**inverso** ($w^{R}$) di una stringa $w$ e' una stringa che constiene gli stessi suffissi ma in ordine inverso($w=a_1,a_2,..,a_n$ e $w^R=a_n,..,a_2,a_1$).

Una stringa e' **palindroma** se una stringa e' uguale al suo inverso ($w=w^{R}$)

La **potenza** di una stringa ($u^{n}$)e' la stringa che otteniamo concatenando la stessa $n$ volte.

## Linguaggio
Un linguaggio $L$ e' un'alfabeto $\sum$ di un qualunque insieme di stringhe su $\sum$

- Usiamo $\sum^{*}$ per indicare l'insieme di tutte le stringhe su $\sum$, inclusa quella vuota ($\epsilon$)
- Usiamo $\sum^{+}$ per indicare tutte le stringhe non vuote su $\sum$

 
$L=0$ e' un linguaggio vuoto, che non contiene la stringa vuota $\epsilon$

### Operazioni sui linguaggio

|Operazione|Definizione|
---|---
Unione|$L_1\cup L_2$
Intersezione|$L_1\cap L_2$
Complemento(not)|$L=\sum^{*}-L$
Concatenzazione|$L_1L_2=\{uv\| u\in L_1,v\in L_2\}$
Potenza|$L^0=\{\epsilon\}$ e $L^{n+1}=LL^n$
Chiusura di Kleene(Arbitrarie)|$L^*=L^0\cup L^1\cup L^2 \cup ...$ 
Chiusura transitiva(non la stringa vuota)|$L^+=L^1\cup L^2 \cup ...$# Automi riconoscitori
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

## Automi non deterministici
Si ha un automa non deterministico quando il comportamento dell'automa non e' determinato, ovvero, a parita' di stato e simbolo letto, ha a disposizione piu' transizione tra cui "scegliere"

## Automi a stati finiti non deterministici

Un'**automa a stati finiti non deterministico** é un quintupla $A=\{Q,\Sigma,\delta,q_{0},F\}$ dove:
- $Q$ e' l'insieme finito degli **stati**
- $\Sigma$ e' l'**alfabeto** riconosciuto dall'automa
- $\delta:Q\times \Sigma \to P(Q)$ e' la funzione di transizione
- $q_{0}\in Q$ e' lo stato **iniziale**
- $F\subseteq Q$ e' l'insieme degli stati **finali**

Alcune osservazioni:
- $\delta(q,a)$ é l'**insieme** di stati in cui l'NFA di puó trovare partendo da $q$ e riconoscendo il simbolo $a$
- Se $\delta(q,a)$ é un singoletto, l'NFA ha una sola scelta
- Se $\delta(q,a)$ é vuoto, l'NFA rifiuta la scelta

### Funzione di transizione estesa

La sua funzione di  transizione estesa dell'automa é la funzione:

$\hat{\delta}:Q\times \Sigma \to Q$

definita per induzione come segue:
- $\hat{\delta}(q,\epsilon)=q$
- $\hat{\delta}(q,wa)=\delta(\hat{\delta}(q,w),a)$

La funzione ritornerá l'insime di stati in cui l'automa di potrá trovare dopo aver preso in input la stringa $arg[1]$ partendo dallo stato $arg[0]$.

### Linguaggio riconosciuto 

Un NFA riconosce le stringhe definite in $\delta$ che gli consentono di arrivare in uno qualsiasi dei suoi stati finali:

$L(A)=\{w\in \Sigma^* | \hat{\delta}(q_0,w)\cap F\ne 0\}$

### Tabella di transizione

Anche in questo caso l'automa si puó rappresentare in forma tabellare come segue:

Stato|b
--|--
$\to q_0$|$q_1$
$*q_1$|$q_0$

dove:
- Le righe corrispondono agli stati dell'automa
- Le colonne corrispondono ai simboli dell'alfabeto dell'automa
- Lo stato iniziale é marcato con $\to$
- Ogni stato finale é marcato con *
- La cella corrispomdente alla riga $q$ e alla colonna $b$ contiene l'insieme $\delta(q,a)$

### DFA -> NFA
Dato un automa a stati finiti **D** esiste un automa a stati non finiti **N** identico, ad esclusione della funzione di transizione ($L(N)=L(D)$)

$\delta_N(q,a)=\{\delta_D(q,a)\}$

possiamo quindi dimostrare per induzione su |$w$| che 

$\hat{\delta}_D(q_0,w)=p \Leftrightarrow \hat{\delta}_N(q_0,w)=\{p\}$
 
 concludiamo quindi che 
 
$\hat{\delta}_D(q_0,w)\in F \Leftrightarrow \hat{\delta}_N(q_0,w)\cap F\ne 0$

### NFA -> DFA
Dato un automa a stati non finiti (che ha un numero finito di stati), e' possibile tracciare tutti gli stati in cui l'NFA si puo' trovare durante in riconoscimento di una stringa all' interno di un DFA.

Gli stati dell'DFA saranno quindi $2^n$, dove $n$ é il numero di stati dell'NFA.## Automi con ε-transizioni
Sono automi che possono eseguire transizioni spontanee **senza leggere** alcun simbolo nella stringa da riconoscere.

Ogni $\epsilon$-NFA é un **quintupla** $A=(Q,\Sigma,\delta,q_0,F)$ dove:
- $Q$ e' l'insieme finito degli **stati**
- $\Sigma$ e' l'**alfabeto** riconosciuto dall'automa
- $\delta:Q\times (\Sigma \cup \{\epsilon\})\to p(Q)$ e' la **funzione di transizione**
- $q_{0}\in Q$ e' lo stato **iniziale**
- $F\subseteq Q$ e' l'**insieme** degli stati **finali**

Alcune osservazioni:
- $\delta(q,a)$ é l'insieme degli stati in cui l'$\epsilon$-NFA  puó transire quando si trova nello stato $q$ leggendo il simbolo $a$
- $\delta(q,\epsilon)$ é l'insieme di stati in cui l'$\epsilon$-NFA puó **transire spostaneamente** quando si trova nello stato $q$ senza leggere alcun simbolo
### $\epsilon$ chiusura
Dato uno stato $q$, la sua **ECLOSE(q)** e' il piu' piccolo insime di stati tale per cui: 
- $q\in$ ECLOSE(q), includendo lo stato stesso e impedendogli di essere vuota
- se $p\in$ ECLOSE(q), allora $\delta(p,\epsilon)\subseteq$ ECLOSE(q), includiamo quindi tutte le transizioni per $\epsilon$

La $\epsilon$-chiusura di un insieme e' l'insieme delle $\epsilon$-chiusure dei suoi elementi.
Se l'insieme e' vuoto questa puo' essere vuota.

###### Esempio
![[Pasted image 20220103140233.png]]
$ECLOSE(q_1)=\{q_1,q_2,q_3,q_4,q_6\}$
$ECLOSE(q_2)=\{q_2,q_3,q_6\}$
$ECLOSE(q_3)=\{q_3,q_6\}$
$ECLOSE(q_4)=\{q_4\}$
$ECLOSE(q_5)=\{q_5,q_7\}$
$ECLOSE(q_6)=\{q_6\}$
$ECLOSE(q_7)=\{q_7\}$
### Fuzione di transizione estesa
La funzione di transizione estesa di un $\epsilon$-NFA e' la funzione

$\hat{\delta}:Q\times \Sigma^*\to p(Q)$

definito per induzione come segue:

- $\hat{\delta}(q,\epsilon)=ECLOSE(q)$
- $\hat{\delta}(q,wa)=\{r\in ECLOSE(\delta(p,a)) | p \in \hat{\delta}(q,w)\}$

### Linguaggio riconosciuto

L'automa riconosce una stringa $w$ se esiste un percorso etichettato con $w$ che lo porta dallo stato iniziale $q_{0}$ a uno dei suoi stati finali in **$F$**.

### NFA -> $\epsilon$-NFA
###### Teorema
Dato un NFA $N$, esiste un $\epsilon$-NFA $E$, t.c. $L(E) = L(N)$

###### Dim.
Basta osservare che un NFA è un caso particolare di un $\epsilon$-NFA

###### Conseguenze
- Ogni linguaggio regolare è riconoscouto da un $\epsilon$-NFA
- gli $\epsilon$-NFA hanno potere riconoscitivo almeno pari a quello dei DFA/NFA equivalenti

### $\epsilon$-NFA -> DFA
Dato un $\epsilon$-NFA $E$, esiste un DFA $D$ tale che $L(D)=L(E)$

###### Intuizione
- usiamo la costruzione per sottoinsiemi come nel caso NFA → DFA
- occorre fare attenzione agli stati raggiungibili da ε-transizioni 
- possiamo usare la nozione di ε-chiusura!

###### Conseguenze
- ogni linguaggio riconosciuto da un ε-NFA è **regolare** 
- commbinando questo risultato e quello della , concludiamo che ε-NFA, NFA e DFA hanno lo **stesso potere riconoscitivo**# Espressioni regolari 
Rispetto ad un alfabeto $\Sigma$ di riferimento, le espressioni regolari sono definite come segue:
- $0$ ed $\epsilon$ sono espressioni regolari 
- se $a \in \Sigma$, allora $a$ e' un'espressione regolare
- se $E$ ed $F$ sono espressioni regolari, $E+F$ ed $EF$ sono espressioni regolari 
- se $E$ e' un'espressione regolare, **$E^{*}$** e' un'espresione regolare

## Convenzioni
- Per quanto riguarda la priorita', si una come convenzione la seguente priorita': + < concat < *
- Usiamo le parentesi per rendere disambigua la struttura

Forma|Significato
-|-
$L(0)=0$|Linguaggio vuoto
$L(\epsilon)=${$\epsilon$}|{$\epsilon$}
$L(a)=${$a$}|Simbolo dell'afabeto
$L(E+F)=L(E)\cup L(F)$|unione
$L(EF)=L(E)L(F)$|concatenazione
$L(E^{*})=L(E)^{*}$|chiusura di Kleene

Diciamo che $E$ ed $F$ sono equivalenti se $L(E)=L(F)$

### Esempio 
Il linguaggio generato da $(a+b)^{*}$ e' 
$L(a+b)^{*}$
$(L(a)\cup L(b))^{*}$
$(${$a$}$\cup${$b$}$)^{*}$
{$a,b$}$^{*}$
{$\epsilon,a,b,aa,bb,ab,ba,...$}

Il linguaggio generato da $(ab)^{*}$
$(L(a)L(b))^{*}$
({$a$}{$b$})$^{*}$
{$ab$}$^{*}$
{$\epsilon,ab,abab,abababa,...$}

### Proprieta' 
#### Unione
Proprieta'|Esempio
-|-
Commutativitá|$E+F=F+E$
Associativitá|$E+(F+G)=(E+F)+G$
Idempotenza|$E+E=E$
Identitá|$E+0=0+E=E$
#### Concatenazione
Proprieta'|Esempio
-|-
Associativitá|$E(FG)=(EF)G$
Identitá|$E\epsilon=\epsilon E=E$
Assorbimento|$E0=0E=0$
Distributivitá sinistra|$E(F+G)=EF+EG$
Distributivitá destra|$(E+F)G=EG+FG$
#### chiusura di Klenee
Proprieta'|Esempio
-|-
Idempotenza|$(E^{*})^{*}=E^{*}$
Casi banali|$\epsilon=0^{*}=\epsilon$

## Espressione regolare -> $\epsilon-NFA$
Data un'espressione regolare $E$, esiste un $\epsilon$-NFA $A$ tale che $L(A)=L(E)$, con esattamente uno stato finale.
#### Caso 0(Linguaggio vuoto)
In questo caso lo stato finale e quello inizale non sono cllegati in alcun modo

![[2021-10-06--1633512145_199x67_scrot.png]]
#### Caso $\epsilon$(Solo stringa vuota)
L'unisca transizione e' rappresentata dalla sola stringa vuota

![[2021-10-06--1633512590_185x64_scrot.png]]
#### Caso a(Linguaggio che contiene solo a)
L'unica transizione e' rappresentata dalla sola stringa "a".

![[2021-10-06--1633512759_171x60_scrot.png]]
#### Caso unione 
In questo casi si analizzano gli automi singolarmente, per poi ottenere un automa che riconosce il linguaggio generato dall'unione dei linguaggi.

![[2021-10-06--1633512920_376x175_scrot.png]]
#### Caso concatenzione
Si analizzano gli automi singolarmente, per ottenere un automa che parte dallo stato inizale del primo automa per arrivare allo stato finale del secondo automa, riconoscendo tutte le concatenazioni possibili.

![[2021-10-06--1633513037_411x112_scrot.png]]
#### Chiusura di Kleene
![[2021-10-06--1633513055_387x126_scrot.png]]

## Esempi
- stringhe di a, b e c che iniziano con due a e finiscono con due b
	$aa(a+b+c)^{*}bb$
- stringhe di 0 e 1 la cui lunghezza è un multiplo di 3
	$((0+1)(0+1)(0+1))^{*}$
- stringhe di 0 e 1 con un numero pari di 0
	$(1^{*}01^{*}0)^{*}1^{*}$
- stringhe di a, b e c che non contengono la sottostringa ab
	$(a^{*}c+b)^{*}a^{*}$
- costanti numeriche binarie pari senza 0 inutili a sinistra (es. 0, 10, ma non 010 o 11)
	$0+1(0+1)^{*}0$## Chiusura dei linguaggi regolari
Dati due lunguaggi **regolari** $L$ ed $L'$ andiamo ad osservare sei i linguaggi regolari generati dalle seguenti **operazioni** sono anch'essi regolari
### Unione e concatenazione
Dati due linguaggi regolari $L_{1}$ e $L_{2}$, essi sono chiusi rispetto all'unione e alla concatenzazione.

###### Dimostrazione
Date due espressioni regolari $E_1$ ed $E_2$ generate rispettivamente dal linguaggio di $L_1$ ed $L_2$ ($L_1=L(E_1)$ e $L_2=L(E_2)$), l'espressione regolare $E_1+E_2$ genererá sicuramente $L_1\cup L_2$, cosí come $E_1 E_2$ genererá sicuramente $L_1 L_2$.

### Complemento
Dato un linguaggio regolare $L$, esso e' chiuso rispetto al complento poiche $\overline{L}=L(B)$.

###### Dimostrazione
Sé un linguaggio é regolare allora esiste sicuramente un DFA $A$ in grado di riconoscerlo.

Definiamo ora un'altro DFA $B=(Q,\Sigma,\delta,q_0,Q-F)$, dove la definizione di stato finale é invertita e quindi ogni stato non finale lo sará invece e viceversa.

Allora é ovvio che se una stringa $w$ appartiene al linguaggio di $A$ non apparterrá al linguaggio di $B$

$w\in L(A)\Leftrightarrow \hat{\delta}(q_0,w)\in F \Leftrightarrow w \notin L(B)$

### Intersezione
I linguaggi regolari sono chiusi rispetto all'intersezione

###### Dimostrazione 
Dati due linguaggi regolari $L_{1}$ e $L_{2}$, $L_{1}\cap L_{2}$ e' un linguaggio regolare, poiche' per le leggi di de morgan: $L_{1}\cap L_{2}=\overline{\overline{L_{1}\cap L_{2}}}=\overline{\overline{L_{1}}\cup\overline{L_{2}}}$ e i linguaggi regolari sono chiusi per intersezioni ed unione.
### Differenza
I linguaggi regolari sono chiusi per differenza

###### Dimostrazione
Dati due linguaggi regolari $L_{1}$ e $L_{2}$,  sono chiusi per la differenza poiche' $L_{1}-L_{2}=L_{1}\cup\overline{L_{2}}$ e questi sono chiusi per intersezione e complemento.
### Inversione
I linguaggi regolari sono chiusi per inversione.

###### Dimostrazione
Se $L$ é un linguaggio regolare allora deve esistere un'espressione regolare $E$ riconosciuta dal linguaggio.

Definiamo quindi l'espressione regolare $E^R$ per induzione sulla struttura di $E$

$0^R=0$
$\epsilon^R=\epsilon$
$a^R=a$
$(E_1+E_2)^R=E^R_1+E^R_2$
$(E_1E_2)=E_2^RE^R_1$
$(E^*)^R=(E^R)^*$

Allora $L(E^R)=L(E)^R$, quindi $L^R$ é regolare.## Linguaggi non regolari
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

Dovendo esserci lo stesso numero di $a$ e $b$, allora la proprietá non é verificata poiché ci possono essere arbitrarie $a$ dovute ad $y^k$.## Minimizzazione di un DFA
### Stati distinguibili
Dato un DFA $A$, 2 stati $p$ e $q$ dello stesso sono distinguibili se **esiste una stringa** per cui,partendo da questi, uno mi conduce in uno stato finale, mentre invece l'altro no.

### Stati indistinguibili
Dato un automa $L$, 2 stati $p$ e $q$ dello stesso sono indistinguibili se **per ogni stringa** ,partendo da questi, arrivo in uno **stesso stato** (anche non finale). 

$\hat{\delta}(p,w)\in F \Leftrightarrow\hat{\delta}(q,w)\in F$
per ogni $w\in \Sigma^*$.

Gli stati indistinguibili sono anche detti **ridondanti**.

Un automa e' ottimizzato se **non esistono** stati ridontanti.

Ogni stato e' **indistinguibile** da **se stesso**.

Se $p$ e' indistinguibile da $q$ e viceversa allora sono indistinguibili.

La relazione di indistingibilita' tra stati e' indicata dalla tilde "~". inoltre indichiamo con [q] la classe di equivalenza di q ([q]={$q\in Q|p$~$q$}).

#### Algoritmo per trovare gli stati indistinguibili
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

#### Minimizzazione dato la tabella di indistinguibilitá 

Per ottenere un DFA minimo che presenta degli stati indistinguibili, **partendo dalla tabella** posso andare a **ricostruire** la sua **struttura** fondendo insieme gli **stati indistinguibili**(generando delle **coppie**) e collegandoli agli stati distinguibili come den DFA non minimo.

###### Esempio
In riferimento all'esempio del punto precedente

![[Pasted image 20220103174115.png]]

#### Equivalenza tra automi
Dati 2 automi $P$ e $Q$, e' possibile verificare la loro equivalenza con il seguente processo:
-  Creo l'unione dei 2 DFA $A=(Q_1\cup Q_2,\Sigma,\delta,q_1,F_1\cup F_2)$ dove
	-  $\delta(q,a)=\{^{\delta_1(q,a)if( q\in Q_1)}_{\delta_2(q,a)if( q\in Q_2)}$
-  Eseguo l'algoritmo riempi-tabella su P
-  $P$ e $Q$ sono equivalenti solo se $p$ e $q$ sono equivalenti

# Linguaggi Liberi
## Grammatica libera
Una grammatica libera e' una quadrupla del tipo $G=(V,T,P,S)$ dove :
- $V$ e' un'insieme finito di **variabili**(simboli **non** terminali)
- $T$ e' un alfabeto di **simboli terminali**
- $P$ e' un'insieme finito di produzioni(coppie Variablie -> Stringa di simboli, terminali o non) della forma $A\to \alpha$ in cui:
	- $A\in V$ e' detta testa della produzione
	- $\alpha \in(V\cup T)^{*}$ e' detto corpo della produzione
- $S\in V$ e' il simbolo inizale della gramamatica.
 
 Le grammatiche possono generare tutti i linguaggi regolari e non.
 ### Convenzione
 - Con le lettere **minuscole** indichiamo gli elementi di T, quindi i simboli **terminali**.
 - Con le lettere **maiuscole** indichiamo gli elementi di V, quindi le **variabili**.
 - Con $X,Y,Z,...$ indichiamo i simboli($\in V\cup T$)
 - Con $u,v,w,...$ denotiamo le stringhe di simboli($(V\cup T)^*$)
 - Con le lettere $u,v,w..$ indichiamo gli elementi di $T^{*}$

### Derivazioni

Data una grammatica $G$, definiamo una derivazione cosí come segue:

- scriviamo $\alpha A \beta \Rightarrow_G \alpha \gamma \beta$ se $A\to \gamma \in P$
	- Diciamo quindi che $\alpha \gamma \beta$ **deriva in un passo** da $\alpha A \beta$ in $G$
- Scriviamo $\Rightarrow_G^*$ per la chiusura riflessiva e transitiva di $\Rightarrow_G$, ovvero:
	- una variabile deriva se stessa in 0 o piú passi ($\alpha \Rightarrow^*_G \alpha$)
	- se $\alpha \Rightarrow_G \beta$ e $\beta \Rightarrow^*_G \gamma$, allora $\alpha \Rightarrow^*_G \gamma$

###### Esempio
Data la grammatica $G=(\{A\},\{0,1\},\{A\to \epsilon|0|1|0A0|1A1\},A)$, ecco alcune possibili derivazioni:
- $A\to \epsilon$
- $A\to 0$
- $A\to 1$
- $A\to 0A0\to 00$
- ...
###  Linguaggio generato da una grammatica

Dato una grammatica G, il linguaggio generato da esso e' denotato da L(G) ed e'e definito come 

$L(G)=\{w\in T^{*}|S\Rightarrow^{*}_{g}w\}$

###### Esempio
La grammatica $G$ dell'esempio precedente é 

$L(G)=\{w\in \{0,1\}^*|w=w^R\}$

Un linguaggio $L$ e' libero se esiste una grammatica libera che lo genera.

Le grammatiche possono generare tutti i linguaggi regolari, ma possono generare anche linguaggi non regolari, quindi i linguaggi liberi includono propriamente i linguaggi regolari.


 
 ## Alberi sintattici
Data una grammatica $G=(V,T,P,S)$, gli alberi sintattici di $G$ sono alberi con le seguenti caratteristiche:
- Ogni nodo interno diverso da una foglia e' etichettato con $V$
- Ogni foglia e' etichettata con $V$,con $T$(terminale) o con $\epsilon$
- Se una foglia e' etichettata da $\epsilon$ ,e' l'unico figlio del suo parent
- Se un nodo e' etichettato con $A$, i suoi figli sono definiti con una produzione del tipo $A\to X_1X_2X_3...X_n$

Il **prodotto** di un'albero sintattico é la **stringa** ottenuta **concatenando** da sinistra verso destra le etichette di **tutte** le **foglie** dell'albero

###### Esempio

![[Pasted image 20220104120602.png]]

### Grammatiche ambigue
Una grammatica é **ambigua** se ammette **piú alberi** sintattici distinti con lo **stesso prodotto**.

Basta trovare due alberi sintattici distinti con lo stesso prodotto per dire che una grammatica ambigua, trovare due derivazioni distinte che generano la stessa stringa **non** é sufficiente.

###### Esempio 
![[Pasted image 20220104121019.png]]
Entrambi questi alberi rappresentano l'espressione $1+2\times 3$

#### Derivazioni canoniche
Una derivazione $X\Rightarrow^* \alpha$ si dice **derivazione a sinistra** se ad ogni passo viene riscritta la **variabile** che si trova a **sinistra**.

Usiamo $\Rightarrow_{lm}$ e $\Rightarrow_{lm}^*$ come simboli per la derivazione sinistra, e scularmente utilizziamo $\Rightarrow_{rm}$ e $\Rightarrow_{rm}^*$ per la derivazione destra.

Se esistono **due** derivazioni canoniche **distinte** dello **stesso tipo** nella grammatica $G$ per derivare la stessa stringa, allora la grammatica é **ambigua**. 

###### Esempio

![[Pasted image 20220104122344.png]]


## Eliminazione dell'ambiguita'
Eliminare l'ambiguita' di una grammatica significa ottenerne una **equivalente** non ambigua. Attraverso questo la grammatica solitamente si complica.

La strategia da utilizzare é **stratificare** le **espressioni**, ovvero anziché mettere tutte le produzioni nella stessa categoria, le **divido** in diverse **espressioni**,**termini** e **fattori**.

###### Esempio

Per disambiguare la grammatica $G=(\{E\},\{[0-9],+,*,(,)\},\{E\to [0-9]|E+E|E*E|(E)\},E)$

si puó stratificare la grammatica nella seguente maniera:

$G=(\{E,T,F\},\{[0-9],+,*,(,)\},P,E)$

dove P é l'insieme delle produzioni:
$E\to T| E+T$
$T\to F| T*F$
$F\to 0|..|9|(E)$
## Automi a pila
Un' **automa a pila**(o **PDA**) e' una settupla del tipo $A=(Q,\Sigma,\Gamma,\delta,q_0,Z_0,F)$ dove
- $Q$ e' un **insieme** finito di **stati**
- $\Sigma$ e' l'alfabeto di **input**
- $\Gamma$ e' l'alfabeto della **pila**
- $\delta: Q\times(\Sigma\cup\{\epsilon\})\times\Gamma\to p(Q \times\Gamma^*)$
- $q_0\in Q$ e' lo **stato iniziale**
- $Z_0\in \Gamma$ e' il **simbolo iniziale** presente sulla pila, e quindi in terminatore
- $F\subset Q$ e' l'insieme degli **stati finali**

Generalmente $\Sigma$ e $\Gamma$ sono distinte, poiché il terminatore $Z_0\in \Gamma$, anche se in moltio casi $\Sigma \subset \Gamma$.

##### Funzione di transizione

A differenza dei DFA, un'automa a pila potrebbe aver la necessitá di **leggere** il contenuto della **pila** per determianre il suo **comportamento**.

La funzione di transizione prende quindi in input la **tripla**:
- $Q$: lo stato in cui si trova l'automa
- $\Sigma \cup \{\epsilon\}$: un simbolo della stringa da riconoscere, oppure epsilon nel caso di una transizione spontanea
- $\Gamma$: un elemento della pila, che verrá rimosso dalla stessa

La funzione pone quindi in output la coppia:
- $Q$: lo stato in cui si troverá dopo il riconoscimento
- $\Gamma^*$: l'insieme degli elementi che verranno aggiunti alla pila
	- Notare che $\epsilon \in \Gamma^*$

###### Esempio
Un'esempio del riconoscimento delle stringhe $a^n b^n$ é il seguente

![[Pasted image 20220104154437.png]]

### Descrizioni istantanee
Per conoscere a **configurazione globale** di un PDA $P$ durante il processo di riconoscimento si usano le **descrizioni istantanee**, ovvero delle triple $(q,w,\alpha)$, dove:
- $q\in Q$ e' lo **stato** in cui si trova l'automa
- $w\in \Sigma$ e' ció che rimane da riconoscere  della **stringa** in input
- $\alpha \in \Gamma^*$ e' il **contenuto** della **pila** dalla cima al fondo

### Mosse di un'automa a pila
Dato un'automa a pila $P$, definiamo con la relazione binaria $\vdash_p$,che descrive la transizione da una descrizione instantanea ad un'altra, nella seguente maniera:

- $(q,aw,X\beta)\vdash_p(p,w,\alpha \beta)se(p\alpha)\in \delta(q,a,X)$
	- In questo caso la stringa da riconoscere non é vuota($aw$)

- $(q,w,X\beta)\vdash_p(p,w,\alpha \beta)se(p\alpha)\in \delta(q,\epsilon,X)$

Diciamo un PDA fa una mossa da una D.I. A ad una B se vale la relazione $A\vdash_p B$

###### Esempio

![[Pasted image 20220104164517.png]]

### Linguaggio accettato da un'automa a pila 
Dato un'automa a pila, il linguaggio
e' l'insieme delle stringhe per le quali, partendo dalla descrizione istantanea iniziale,l'automa puo' raggiungere in 0 o piu' **mosse** un suo stato finale, la **stringa** di input e' stata **consumata** completamente e il contenuto della **pila** e' **arbitrario** nel riconoscimento per stato finale, oppure **vuoto** nel riconoscimento per pila vuota.

Il Linguaggio accettato da $P$ per stato finale é 

$L(P)=\{w\in\Sigma^*|(q_0,w,Z_0)\vdash_P^*(q,\epsilon,\alpha),q\in F\}$

mentre il linguaggio accettato da $P$ per pila vuota é 

$N(P)=\{w\in \Sigma^*|(q_0,w,Z_0)\vdash^*_P(q,\epsilon,\epsilon)\}$
### Proprietá di chiusura dei linguaggi regolari

#### Unione e concatenazione

I linguaggi liberi sono chiusi per contatenazione

###### Dimostrazione 
Dati due linguaggi liberi $L_1$ ed $L_2$, esistono sicuramente due grammatiche libere t.c. $L_1=L(G_1)$ e $L_2=L(G_2)$.

Possiamo assumere che le grammatiche **non** abbiano **variabili** in **comune** ($V_1\cap V_2=0$) e che il **simbolo iniziale** non appartenga alle variabili di **nessuna** dei due grammatiche($S\notin V_1\cup V_2$), poiché e sempre possibile scegliere **nuovi nomi** per le grammatiche, o quantomeno rinominarle.

Quindi la grammatica 

$(V_1\cup V_2,T_1\cup T_2,P_1 \cup P_2\cup \{S\to S_1|S_2\},S)$

genera $L_1\cup L_2$, mentre la grammatica

$(V_1\cup V_2,T_1\cup T_2,P_1 \cup P_2\cup \{S\to S_1S_2\},S)$

genera $L_1L_2$.

#### Intersezione

I linguaggi liberi **non** sono chiusi per intersezione.

###### Dimostrazione 
I linguaggi 
- $L_1=\{a^nb^nc^m|m,n\ge 0\}$
- $L_2=\{a^mb^nc^n|m,n\ge 0\}$

sono liberi. Se i linguaggi liberi fossero chiusi per intersezione, allora anche il linguaggio

$L_1\cap L_2=\{a^nb^nc^n|n\ge 0\}$

sarebbe libero, ma abbiamo dimostrato che non lo é.

##### Intersezione con un linguaggio regolare

Se $L$ é un linguaggio libero ed $R$ é un linguaggio regolare, allora $L\cap R$ é un linguaggio libero.

###### Dimostrazione

Se $L$ è un linguaggio libero allora esiste un PDA che accetta $L$ per stato finale.
Se $R$ è un linguaggio regolare allora esiste un DFA che accetta $R$.
Si può costruire quindi un PDA che accetta $L\cap R$ per stato finale costruendo il “prodotto” di $P$ ed $M$.

##### Complemento e differenza
I linguaggi liberi non sono chiusi per complemento e differenza

###### Dimostrazione 
I linguaggi liberi sono chiusi per unione. Se fossero chiusi anche per complemento, allora avremmo che

$L_1\cap L_2=\overline{\overline{L_1\cap L_2}=\overline{L_1}\cup \overline{L_2}}$

sarebbe sempre un linguaggio libero, contrariamente a quanto dimostrato in precedenza.

##### Inversione
Se $L$ é un linguaggio libero, allora $L^R$ é un linguaggio libero.
###### Dimostrazione 
# Parsing
Data una grammatica $G$ e una stringa $w\in T^*$, dobbiamo determianre se esiste un'albero sintattico di $G$ con radice $S$ e prodotto $w$.

La costruzione di un'automa corrispondente a $G$ produce un PDA non deterministico, e per alcune gramamtiche non é possibile trovare un DPDA.

Identifichiamo quindi una famiglia di grammatiche libere per le quali é possibile costruire un parser deterministico.
## Strategia di parsing top-down

Data una grammatica $G=(V,T,P,S)$ e una stringa $w\in T^*$, il parser cerca di ottenere una derivazione sinistra $S\to^*_{im}$ in cui, al passo $i$, il parser sa' che 

$S\to^*_{im}uA\beta$

ovvero la derivazione canonica sinistra che ci permetterebbe di ottenere $u$(stringa di simboli terminali) e' indicato come sopra.

Deve inoltre stabilire se 

$uA\beta \to^*_{im}w$

attraverso le derivazioni.

Ci sono due casi da considerare:
- Se $u$ non e' un prefisso $w$, allora il parser rifiuta $w$ poiche' i simboli terminali non possono essere riscritti.
- Se $w=uav$ allora il parser deve segliere una produzione per riscrivere A($A\to \alpha_1|...|\alpha_n$) e puo' usare $a$ come "guida" per riconoscere il prossimo passo da effettuare.
	- Es:Supponiamo di avere due produzioni $A\to aA|b$, utilizziamo la prima poiche' il corpo della produzione ci permette di generare $a$. 
	- Se abbiamo invece $A\to aA|b|C$ sobbiamo anche controllare le produzioni con $C$ poiche' potrebbe generare $a$.
	- Se abbiamo produzioni distinte che generano un prefisso comune non siamo invece di determinare qual'e' la produzione giusta da utilizzare(Es:$A\to aB|aC$)
### Stringa annullabile 
Una stringa $\alpha$(terminale o non) e' annullabile($NULL(\alpha)$) se e solo se puo' essere riscritta nella stringa vuota

Per determinarle l'annullabilita' utilizziamo un algoritmo:
- Se $Null(X_1),...,Null(X_n)$ allora la stringa e' annullabile
	- Se ogni produzione e' annullabile($X_1,...,X_n\to \epsilon$) allora la stringa e' annullabile
- Se $A\to \alpha \in P$ e $Null(\alpha)$, allora $Null(A)$

Note
- Una stringa che contiene dei simboli terminali non e' annullabile
- $\epsilon$ e' sempre annullabile
- Se una produzione di $A$ e' $\epsilon$, allora $Null(A)$

### Inizio di una stringa (FIRST)

Indichiamo con **First($\alpha$)** gli inizi di $\alpha$  l'inizio dei simboli terminali che possiamo trovare all'inizio delle stringe generate da $\alpha$

$FIRST(\alpha)=\{a\in T|\alpha \to^*_G \alpha \beta\}$

E' possibile calcolare $FIRST(\alpha)$ nella seguente maniera:
- $FIRST(\epsilon)=0$
- $FIRST(a)=\{a\}$
- $FIRST(A)=\bigcup _{A\to a} FIRST(\alpha)$
- $FIRST(X\alpha)=\{^{FIRST(X)\cup FIRST(\alpha) se NULL(X)}_{FIRST(X) altrimenti}$

### Seguiti di una variabile (FOLLOW)
Data una grammatica $G=\{V,T,P,S\}$ e una variabile $A \in V$Indichiamo come $FOLLOW(A)$ un'insime di simboli terminali $a$ che possiamo trovare dopo un'occorenza di $A$ dopo uan derivazione anche non canonica

$FOLLOW(A)=\{a \in T|S\to^*_G \alpha A\alpha B\}$

E' possibile calcolare il $FOLLOW$ nella seguente maniera:

Fase 1:
- Annotiamo le relazioni appartenenza ed inclusione insiemistica secondo il seguente algoritmo:
	- Annotiamo $\$ \in FOLLOW(S)$
	- Ripetiamo per ogni produzione e ogni variabile del corpo:
		- Se $A\to \alpha B\beta$ annotiamo $FIRST(\beta)\subseteq FOLLOW(B)$
		- Se $A\in \alpha B\beta$ e $NULL(\beta)$, allora $FOLLOW(A)\subseteq FOLLOW(B)$

Fase 2:
- Le relazioni sono strate tutte annotate, quindi partendo dai simboli di relazione diretta determiniamo i seguiti

#### Esempio 1
$S\to Ac|Ba$
$A\to \epsilon|a$
$B\to b$
$C\to a|Cb$
$D\to \epsilon|d|Db$

allora
$Null(A)$ e $Null(D)$
$\$\in FOLLOW(S)$
$c\in FOLLOW(A)$
$a\in FOLLOW(B)$
$b\in FOLLOW(C)$
$b\in FOLLOW(D)$

da cui generiamo la tabella

X|FOLLOW(X)
--|--
S|$\{\$\}$
A|$\{c\}$
B|$\{a\}$
C|$\{b\}$
D|$\{b\}$

#### Esempio 2
$E\to TE'$
$E'\to +TE'|\epsilon$
$T\to FT'$
$T'\to *FT'|\epsilon$
$F\to (E)|id$
allora
$\$\in FOLLOW(E)$
$FIRST(E')\subseteq FOLLOW(T)$||$+\in FOLLOW(T)$
$FOLLOW(E)\subseteq FOLLOW(T)$
$FOLLOW(E)\subseteq FOLLOW(E')$
$FOLLOW(E')\subseteq FOLLOW(T)$
$FIRST(T')\subseteq FOLLOW(F)$||$*\in FOLLOW(F)$
$FOLLOW(T)\subseteq FOLLOW(F)$
$FOLLOW(T)\subseteq FOLLOW(T')$
$FOLLOW(T')\subseteq FOLLOW(F)$
$)\in FOLLOW(E)$

da cui possiamo calcolare

Var|Follow
--|--
E|$,)
E'|$,)
T|$,+,)
T'|$,+,)
F|$,+,*,)

Prendendo in cosiderazione innanzitutto i simboli di appartenenza, e propagandolo in base ai follow seguendo i versi delle inclusioni(*left to right*).

#### Insiemi guida
Data una grammatica qualsiasi e una produzione di questa grammatica($A\to \alpha$), definiamo insieme guida di una produzione l'insieme:

$GUIDA(A\to \alpha)=\displaystyle \{^{FIRS(\alpha)\cup FOLLOW(A) se NULL(\alpha)}_{FIRST(\alpha) altrimenti}$

Ci permettono di intuire la riscrittura giusta che il parser deve effettuare al fine di riconoscere al fine del riconoscimento di una stringa, attraverso il controllo del prossimo carattere e controllando a quale insieme guida appartiene.

Nel caso gli insiemi guida non sono disguinti il parser va' in errore

#### Grammatica LL(1)
Un grammatica e' definita LL(1) se per ogni coppia di produzioni distinte per la stessa variabile($A\to \alpha$ e $A\to \beta$) gli insiemi guida hanno intersezione vuota,ovvero sono disgiunti

$Guida(A\to \alpha)\cap GUIDA(A\to \beta)=0$

##### Esempi
Calcoliamo gli insiemi guida
$A\to BC|D$
$B\to \epsilon|a$
$C\to b|cCc$
$D\to \epsilon|CD$
I simboli annullabili sono
$NULL(B)$
$NULL(D)$
$NULL(A)$
I first sono
$FIRST(A)=FIRST(BC)\cup FIRST(D)=FIRST(B)\cup FIRST(C)\cup FIRST(D)=\{a,b,c\}$
$FIRST(B)=FIRST(\epsilon)\cup FIRST(A)=\{a\}$
$FIRST(C)=\{b,c\}$
$FIRST(D)=\{b,c\}$
I follow sono:
$\$\in FOLLOW(A)$
$b.c\in FOLLOW(C)$
$FOLLOW\subseteq FOLLOW(C)$
$FOLLOW(A)\subseteq FOLLOW(D)$
$c\in FOLLOW(C)$
$b,c\in FOLLOW(C)$
$FOLLOW(D)\subseteq FOLLOW(C)$
generiamo quindi la seguente tabella

Var|Follow
--|--
A|$
B|b,c
C|$,b,c
D|$

Calcoliamo alcuni insiemi guida
$GUIDA(A\to BC)=FIRST(BC)=FIRST(B)\cup FIRST(C)=\{a,b,c\}$
poiche' $BC$ non e' annullabile
$GUIDA(A\to D)=FIRST(D)\cup FOLLOW(A)=\{\$,b,c\}$
Possiamo quindi concludere che non e' una grammatica LL(1) poiche' gli insiemi guida sopra citati non sono disgiunti

$GUIDA(B\to \epsilon)=FIRST(\epsilon)\cup FOLLOW(B)=\{b,c\}$
$GUIDA(B\to a)=\{a\}$
### Parsing ricorsivo discendente
Per realizzare un parse basato sulla **ricorsione** usiamo la pila del linguaggio di programmazione per **ricordare** il **suffisso** della forma sentenziale sinistra da riconoscere.

#### Elementi chiave
- Il parser ha una **procedura**(metodo) per ogni **variabile** della grammatica
- La procedura $A$ nel parser riconsoce le stringhe generate da $A$ nella grammatica
- La procedura $A$ usa il **simbolo** corrente e gli **insiemi guida** per scegliere la produzione da usare per riscrivere $A$
- Per ogni **simbolo** $X$ trovato nel corpo della produzione:
	- Se è un simbolo **terminale**, il metodo **controlla** che il simbolo corrente sia proprio $X$ e fa **avanzare** il **lexer** al simbolo successivo. In caso contrario, il metodo segnala un errore di sintassi.
	- Se é una **variabile**, il metodo invoca la **procedura** $X$


##### Esempio: Parser per il linguaggio $A^nB^n$
###### Grammatica
$S\to aSb|\epsilon$
###### Insiemi guida
$Guida(A\to aSb)=\{a\}$
$Guida(A\to \epsilon)=\{b,\$\}$
###### Codice del parser
```java
public class AnBn extends Parser { 
	protected void S() { 
		switch (peek()) { 
			case 'a': // S → aSb 
				match('a'); 
				S(); 
				match('b'); 
				break; 
			case 'b': // S → ε 
			case '$': 
				break; 
			default: throw error(); } 
	} 
}
```

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

![[pngs/2021-11-17--1637145673_550x99_scrot.png]]## Traduzione
Un **parser** ci permette solo di capire se un'espressione é corretta sintatticamente,

Per valutare le espressioni vogliamo produrre **informazioni** aggiuntive al riconoscimento, per far cio' **associamo** ad ogni **nodo** dell'albero associamo degli **attributi** che ci permettano di capire il valore delle sottoespressioni corrispondente ad un certo sottoalbero.

![[Pasted image 20220110143220.png]]


### Definizioni dirette dalla sintassi

#### Prefazione

Un **attributo** è una **coppia** (nome, valore) che rappresenta una qualunque **informazione** associata ad un **nodo** di un albero sintattico.

Un **albero** sintattico **annotato** è un albero sintattico in cui ogni **nodo** può essere annotato con **zero o più attributi**.

#### Definizione

Una **Definizione Diretta dalla Sintassi ** (o SDD, da
*Syntax-Directed Definition*) è una grammatica le
cui produzioni sono associate a zero o più **regole
semantiche** che specificano come calcolare il
valore degli attributi associati ai nodi degli alberi
sintattici della grammatica.

Il **valore** di eventuali **attributi** associati ai simboli terminali è fornito dal **lexer**.

###### Esempio

![[Pasted image 20220110143834.png]]

#### Attributi sintetizzati 
Un attributo di un nodo $N$ in un'albero annotato si dice **sintetizzato** se il suo **valore** dipende da quello degli **attributi e dei figli ** di $N$ ed eventualmente dagli attributi di $N$ **stesso**.

Il valore di un attributo sintetizzato per da un nodo $N$ e' determinato da una regola semantica associata ad una sua produzione.

###### Esempio

![[Pasted image 20220110144420.png]]

Il valore dell'attributo sintetizzato $s$ associato alla variabile $A$ in una sua produzione $A\to X_1X_2..X_n$ é indicato nella seguente maniera:

- $A.s=f(X_1.a_1,X_2.a_2,...,X_n.a_n)$

#### Attributi ereditati 

Un **attributo** di un nodo $N$ in un albero annotato si dice **ereditato** se il suo valore dipende da quello degli attributi del padre e dei fratelli.

###### Esempio

Il valore dell'attributo $e$ associato alla vairabile $A$ per una produzione $B\to X_1X_2..A..X_n$ é indicato nella seguente maniera:

- $A.e=f(B.a,X_1.a_1,X_2.a_2,...,X_n.a_n)$


### Ordine ddi valutazione degli attributi

#### Grafo delle dipendenze

Se il **calcolo** di un'**attributo** sintetizzato (es:$A.a$) richieda di **conoscere** il valore di un'**altro attributo** (es:$B.b$), allora scriviamo

$A.a=f(..,B.b,..)$

Per indicare ció introduciamo un **grafo delle dipendenze**, che attraverso l'utilizzo di <i style="color:red;">frecce rosse tratteggiate</i>, ci permette di indicare le **dipendenze** per la sintesi di un'attributo.

Se il grafo delle dipendenze contiene dei **cicli**, **non** é possibile trovare un'**ordine** di valutazione degli attributi.

#### Definizione S-attribuita
Una SDD si dice **S-attribuita** se contiene **solo** attributi **sintetizzati**.

#### Definizione L-attribuita
Una SDD si dice **L-attribuita** se per ogni **produzione** $A\to X_1X_2...X_n$ ed ogni **attributo ereditato** $X_i.e$, la **regola** semantica che definisce i valori di $X_i.e$ **dipende** solo da
- gli **attributi ereditati** da $A$
- gli **attributi sintetizzati** ed **ereditati** dal corpo della produzione ma a **sinistra** di $X_i$

##### Osservazioni
- Ogni SDD é sia S-attribuita che L-attribuita
- Ogni SDD L-attribuita ha un grafo delle dipendenze aciclico### Schemi di Traduzione
Uno **schema di traduzione** (o **SDT**, da Syntax-Directed Translation scheme) è una **grammatica** in cui le **produzioni** sono **arricchite** da frammenti di **codice** detti **azioni semantiche** che sono eseguite quando tutti i simboli alla loro sinistra sono stati riconosciuti.

###### Esempi
Produzione|Produzione+Azioni|Descrizione
--|--|--
$A\to BC$|$A\to BC\{code\}$|Il codice viene seguito dopo il riconoscimento di $BC$
$A\to BC$|$A\to B\{code\}C$|Il codive viene seguito dopo il riconoscimento di $B$ ma prima di quello di $C$
$A\to BC$|$A\to \{code_1\}BC\{code_2\}$|Il primo codice viene eseguito dopo la riscrittura di $A$, mentre il secondo dopo il riconoscimento di $BC$
$A\to \epsilon$|$a\to \{code\}$|Il codice viene eseguito dopo la riscrittura di $A$

#### Differenze tra regole e azioni semantiche

Regole semantiche(SDD)|Azioni semantiche(SDT)
--|--
Specificano come ottenere il valore degli attributi|Specificanono come ottenere il valore degli attributi, ma  possono contenere anche codice arbitrario
Sono valutate seguendo il grafo delle dipendenze, in ordine implicito|Sono eseguite in ordine esplicito, in base alla loro posizione nel corpo della produzione
Richiedono la costruzione di un'albero annotato, poiché valutate in ordine arbitrario|Possono essere integrato ad un parser ricorsivo discendente, poiché eseguite da destra verso sinistra 

#### Conversione da SDD L-attribuita a SDT

Data una SDD L-attribuita, si può ottenere uno SDT corrispondente nel modo seguente.

Per ogni produzione $A\to X_1X_2..X_n$ della grammatica:

- Subito prima di $X_i$, con $i>1$ si **aggiunge** un'**azione** semantica che calcola il valore degli attributi **ereditati** di $X_i$
- In **fondo** alla produzione (dopo $X_n$), aggiungo un'azione semantica che calcola il valore di **tutti** gli attributi **sintetizzati** da $A$

#### Parser ricorsivo discendente di una SDT

Per integrare una SDT in un parser ricorsivo discendente, questo deve avere una procedura per ogni variabile che riconosce le stringhe generate dalla stessa.

La procedura ha tanti argomenti quanti sono gli attributi ereditati e restituisce tanti valori quanti sono gli attributi sintetizzati.

Per ogni simbolo o azione semantica $X$ nel corpo della produzione scelta:

- Se $X$ é un **simbolo terminale**, il metodo **controlla** che sia proprio $X$, per poi far **avanzare** il **lexer** se é vero.
- Se $X$ é una **variabile**, viene invocata la **procedura** $X$, passando i suoi attributi **ereditati** come **argomenti** e raccogliendo in **variabili** locali gli attributi **sintetizzati** restituiti dalla procedura.
- Se $X$ é un'**azione semantica**, il metodo la **esegue**.

###### Esempio

![[Pasted image 20220112165148.png]]

```java
private int S() {
	switch (peek()) {
		case 'a': { // S → aSb 
			check('a'); 
			int S_n = S(); 
			check('b'); 
			return S_n + 1; } 
		case 'b': // S → ε 
		case '$': 
			return 0; 
		default: 
			throw error("S");
	} 
}
```

#### Traduzione "on-the-fly"
Un attributo sintetizzato si dice principale se:
1. Il suo valore **include una concatenzazione ** dei valori dello stesso attributo, cioe' il corpo delle variabili di ogni produzione 
2. La concatenazione rispetta sempre l'ordine di comparsa delle variabili nel corpo della produzione 

$E\to E_1+T\{E.post=E_1.post||T.post||"T"\}$

Gli attributi principali possono essere eliminati “emettendo al volo” solo gli elementi ausiliari nel punto in cui devono comparire. ### Codice intermedio
 
 Stabilito che il programma da tradurre è sintatticamente corretto, il compilatore lo deve tradurre in un programma equivalente scritto in codice intermedio.
 
 Per far ció utiliziamo il bytecode di java come codice intermedio.
 
 ![[Pasted image 20220112181117.png]]
 
 Non aggiungo la spiegazione poiché giá vista ad architettura degli elaboratori.
 
 #### Comandi
 
 Nome | Significato
---|---|
BIPUSH *Byte*| Scrive un byte in cima allo stack
DUP|Duplica la parola in cima allo stack
GOTO *offset*| Diramazione incondizionata
IADD|Somma le 2 parole in cima allo stack
IAND|Sostituisce le parole in cima allo stack con il loro AND
IFEQ *offset*| (IF EQUALS (0)) Esegue una diramazione se la parola in cima allo stack è zero
IFLT *offset*|Esegue una diramazione se la parola in cima allo stack è negativa
IF_ICMPEQ *offset*| (COMPARE EQUALS) Effettua una diramazione se le 2 parole in cima allo stack sono uguali
IINC *var* *const*| Aggiunge una costante ad una variabile locale
ILOAD *var*| Scrive una variabile locale in cima allo stack
INVOKEVIRTUAL *met*| invoca un metodo
IOR|Sostituisce le 2 parole in cima allo stack con il loro OR
IRETURN|Termina il metodo restituendo un valore intero
ISTORE *var*|Memorizza la variabile in cima allo stack come una variabile locale
ISUB|Sostituisce le 2 parole in cima llo stack con la loro differenza
LDC *index*| Scrive sullo stack una costante proveniente da una porzione di memoria
NOP|Non fa niente
POP|Rimuove l'elemento in cima allo stack
SWAP|Scambia le 2 parole in cima allo stack
INEG|Nega la parola in cima allo stack
IMUL| Moltiplicazione dei 2 valori in cima allo stack
IDIV| Divisione dei 2 valori in cima allo stack
IREM| Modulo dei 2 valori in cima allo stack
IF_ICMPNE *offset*| Salta se le 2 parole in cima allo stack non sono uguali
IF_ICMPLE| flavor con il less equal $\le$
IF_ICMPGE| flavor con il less equal $\ge$
IF_ICMPLT| flavor con il less equal $\lt$
IF_ICMPGT| flavor con il less equal $\gt$
NEWARRAY|Crea un'array della lunghezza del valore sulla pila
ARRAYLENGTH| Deposita sulla pila la lunghezza dell'array presente sulla stessa
IALOAD| Carica sulla pila la posizione della parola in cima e dell'array in seconda posizione
IASTORE| Assegna il valore in cima alla posizione i(seconda) nell'array in terza posizione# Introduzione
