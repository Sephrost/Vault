# Parsing
## Strategia di parsing top-down
[aggiungere introduzione e riquadro grigio]
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
Una stringa $\alpha$(terminale o non) e' annullabile($NULL(\alpha)$) se e solo se puo' essere riscritta nelal stringa vuota

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
$FIRST(E')\subseteq FOLLOW(T)$
$FOLLOW(E)\subseteq FOLLOW(T)$
$FOLLOW(E)\subseteq FOLLOW(E')$
$FOLLOW(E')\subseteq FOLLOW(T)$
$FIRST(T')\subseteq FOLLOW(F)$
$FOLLOW(T)\subseteq FOLLOW(F)$
$FOLLOW(T)\subseteq FOLLOW(T')$
$FOLLOW(T')\subseteq FOLLOW(F)$
$)\in FOLLOW(E)$