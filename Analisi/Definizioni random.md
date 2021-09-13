# Limite superiore ed inferiore di una funzione
Siano $D⊆ℝ$ e f: D->ℝ

## Limite superiore
Una funzione é limitata superiormente su D se esiste M∈ℝ t.c
$f(x)≤M$ , $∀X∈D$

![[Pasted image 20210411115943.png]]
## Limite inferiore
Una funzione é inferiormente limitata su D se esiste m∈ℝ t.c
$m≤f(x)$ , $∀X∈D$
![[Pasted image 20210411120103.png]]
## Limite inferiore e superiore
Una funzione si dice limitata superiormente ed inferiormente se esistono m,M∈ℝ t.c
$m≤f(x)≤M$ ,$∀X∈D$
![[Pasted image 20210411115905.png]]

# Funzioni pari,dispari e periodica
Siano $D⊆ℝ$ simmetrico rispetto all'origine(x∈D<->-x∈D) e f: D->ℝ
## Funzioni pari 
f é pari se $f(-x)=f(x)$ ,$∀X∈D$
Ovvero il grafico sará simmetrico rispetto all'asse delle ordinate

![[Pasted image 20210411121345.png]]

## Funzione dispari
f é dispari se $f(-x)=f(x)$ ,$∀X∈D$
Ovvero il grafico sará simmetrico rispetto all'origine

![[Pasted image 20210411121435.png]]

## Funzione periodica

f é detta periodica se esiste $T>0$ t.c
$x∈D$ <-> $x+T∈D$ e $f(x+T)=f(x)$ ,$∀X∈D$
T é definito quindi come _periodo_ di f.

![[Pasted image 20210411122105.png]]

# Funzioni monotone e strettamente monotone
Sia $I⊆ℝ$ un intervallo e sia f: I->ℝ
## Funzioni monotone
f si dice monotona su I se é crescente ($f(x_1)≤f(x_2)$) oppure decrescente ($f(x_1)≥f(x_2)$)

![[Pasted image 20210411124119.png]]
## Funzioni strettamente monotone
f si dice strettamente monotona su I se é strettamente crescente ($f(x_1)<f(x_2)$) oppure strettamente decrescente ($f(x_1)>f(x_2)$)

![[Pasted image 20210411124433.png]]

La differenza tra una funzione strettamente monotona e una monotona semplice é che la seconda é costante su qualche intervallo

Todo :
- Aggiungere concavitá 

# Funzioni 

## Funzioni lineari
sono funzioni del tipo $f(x)=mx+q$ , $m,q∈ℝ$

![[Pasted image 20210411135948.png]]
- m é la pendenza della retta $(\frac{y_2-y_1}{x_2-x_1})$=$(\frac{Δy}{Δx})$
	- Se m é positiva la retta sará crescente
	- Se m é negativa la retta sará decrescente
	- Se m é 0 allora la retta sará parallela all'asse delle ascisse

- q é invece il punto in cui la retta intersecherá l'asse delle ordinate

# Derivata di una funzione 
## Pendenza di una funzione in un punto 
La pendenza di una funzione in un punto é uguale alla pendenza della tangente passante per il punto stesso 

Pendenza come funzione lineare -> m

Pendenza in un punto c ->p(c)
$p(c)=lim\to0$ &nbsp   $\frac{f(c+Δx)-f(c)}{Δx}$
&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp  $^{Δ(x)}$

Bisogna comunque considerare che $m\equiv p(c)$

La pendenza sará positiva se la tangente é crescente, mentre sará negativa se questa decresce

## Retta tangente o derivata
Si definisce la retta tangente al grafico di f in $(c,f(c))$, la retta passante per il punto prima definito e avente pendenza p(c), ed avente seguente equazione:

$y=f(c)+p(c)(x-c)$

Si puó quindi definire la pendenza di una funzione f in un punto $(c,f(c))$ é uguale alla pendenza dellla retta tangente al punto stesso.

## Calcolo esatto della derivata
Il coefficiente di Newton ci permette di approssimare la derivata, per calcolare la derivata esatta ci affidiamo alla seguente tabella.

Funzione semplice | Derivata
--------|-------
$x^\alpha$|$\alpha$ $x^{\alpha-1}$
$e^x$|$e^x$
$logx$|$\frac{1}{x}$
$sin$ $x$|$cos$ $x$
$cos$ $x$|$-sin$ $x$
$tg$ $x$|$\frac{1}{cos^2x}$
$arcsin$ $x$|$\frac{1}{\sqrt{1-x^2}}$
$arctg$ $x$|$\frac{1}{1+x^2}$
**Funzione composta**| **Derivata**
$(f(x))^\alpha$|$\alpha(f(x))^{\alpha-1}f'(x)$
$e^{f(x)}$|$e^{f(x)}f'(x)$
$logf(x)$|$\frac{1}{f(x)}f'(x)$
$sinf(x)$|$(cosf(x))f'(x)$
$cosf(x)$|$-(sinf(x))f'(x)$
$arctgf(x)$|$\frac{1}{1+(f(x))^2}f'(x)$

# Lavoro compiuto da una forza

Consideriamo un'oggetto che si muove lungo una traiettoria rettilinea sotto l'azione di una forza, diremo che $f(x)>0$ se la forza agisce nel verso del moto, altrimenti $f(x)<0$ se agisce nel senso opposto.

## Lavoro compiuto da una forza costante

Sia $F: [a;b]\to ℝ$ costante. Allora:

$L_{F;a\to b}=F(b-a)$

Ció equivale a moltiplicare la forza per la distanza percorsa.

## Lavoro di una forza costante a tratti

Basandoci sulla forza sopra indicata é possibile ricavare la formula per una forza costante a tratti:

$L_{F;a\to b}=\frac{\sum_{i=0}^{h-1}F_{i+1}(x_{i+i}-x_i)}
{n}$

La formula sopra indicato permette di dividere l'intervallo da analizzare in n parti(possibilemente tutte uguali) e di approssimare la forza esercitata in quel frangente, accumulando i vari risultatai attraverso la sommatoria.

## Somme di Riemann

Sia $f:[a;b]\toℝ$, sia questo diviso in n intervalli di ugual lunghezza $\frac{b-a}{n}$ e siano $z_1,..,z_n$ dei punti appartenenti agli intervalli sopra citati,considerati come punti intermedi agli intervalli scelti con qualche criterio.
Allora si chiama *somme di Riemann* di $f$ relativa alla suddivione e ad punti di compionamento l'espressione:

$S_n(f;z_1,..,z_n)=\sum^{n-1}_{i=0}\frac{b-a}{n}f(z_{i+1})$

## TL;DR

TL;DR , abbiamo :
- un intervallo da analizzare [a,b]
-  una suddivisione in *n* intervalli $x_1,...,x_{h-1}$, dove $h=b$, di ampiezza $\frac{b-a}{n}$
-  Dei punti $z_i$ ,parziali a questi intervalli, appartenenti a $[x_{i-1},x_i)$ , determianti secondo un qualche criterio (di solito il punto medio). 

![[Pasted image 20210426162813.png]]

## Integrale definito di una funzione limitata

Riprendendo la funzione sopra citata, diciamo che 

$lim(h\to+\infty)\frac{b-a}{h}\sum^{h}_{i=1}F(z_i)$

é l'integrale definito di F su [a;b] se questo esiste finito e non é vincolato dalla scelta dei punti di campionamento ($z_i$).

Si puó indicare inoltre con $\int^{b}_{a}F(x)dx$.

La definizione non ci permette peró di calcolare con precisine l'integrale definito, ma ci permette di approssimarlo :

$\int^{b}_{a}F(x)dx\approx\frac{b-a}{h}f(\frac{x_0+x_1}{2})+...+\frac{b-a}{h}f(\frac{x_{h-1}+x_h}{2})$

## Definizione geometrica di integrale

Consideriamo una funzione $f \in R([a;b])$ ed indichiamo con $R_{f;a;b}$ la regione di piano compresa tra il grafico di $f$, l'asse delle ascisse e le rette di equazione $x=a$ ed $x=b$. Se $f$ é positiva allora l'area di $R_{f;a;b}$ coincide con l'integrale definito di $f$ su [a;b].

Poiché $|f|=f$ e $|-f|=f$ possiamo affermare che:

$Area(R_{f;a;b})=\int^{b}_{a}|f(x)|dx$

# Limiti

## Intorno di un punto

Dato un punto $c \in ℝ$, di definisce suo intorno di *raggio r* l'insieme dei punti in prossimitá del punto $c$.

Formalmente quindi scriviamo
$I_{r}(c)=${ $x \in ℝ: |x-c|<r$ }
che coincide  con l'intervallo ($c-r;c+r$).

![[Pasted image 20210511153755.png]]

Si dice inoltre che un proprietá vale **Definitivamente** per $x \to c$ se esiste un intorno  tale che essa é vera per ogni $x \in I_r(c)$, tranne eventuialmente x=c.

Si chiamo intorno di $+\infty$ e $-\infty$ ,rispettivamente, 
$I(+\infty)=${$x \in ℝ: x>a$} $= (a;+\infty)$ e $I(-\infty)=$ {$x \in ℝ: x<a$}$= (-\infty;a)$ 
dove $a \in ℝ$.

## Limite finito di una funzione in un punto
Dato un intorno $f:(c-r;c+r)$\ {$c$}$\to ℝ$ con $r>0$, si dice che:

$\displaystyle{\lim_{x\to c}} f(x)= L$ , con $L \in ℝ$

se:

$∀ y>0$, $Ǝ I(c):c \in I(c), x\ne c \to |f(x)-L|<y$

Ovvero se dato un intorno di $c$ di raggio $r$ che non comprende il punto c, allora il limite di x che tende a $c$ esiste finito se il punto c appartiene ad un'altro intorno $I(c)$.
## Funzioni continue

Dato un intorno f:(c-r;c+r)$\to ℝ$, con $c \in ℝ$ e $r>0$, la funzione di dice continua in un punto $c$ se $\displaystyle{\lim_{x \to c}}=f(c)$.

Una funzione risulta non continua se non é definita in un suo punto o se il suo limite é diverso dal valore assunto dalla funzione($\displaystyle{\lim_{x\to c}}\ne f(c)$).

Una funzione risulta invece continua su un intervallo se é continua in ogni $c$ interno all'intervallo ed é continua da destra o da sinistra negli estremi dello stesso.



