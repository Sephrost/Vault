### Ancora media e varianza di variabili aleatorie discrete
#### Momenti di ordine K
Definiamo momenti di ordine K della variabile aleatoria discreta $x$ la media di $x^k$ cosi' calcolata:

$E(x^k)=\displaystyle \sum_{x \in imm(x)} x^k\times px(k)$
#### Varianza
Definiamo varianza di x la seguente quantita':

$var(x)=E[(x-E(x))^2]=\displaystyle \sum_{x \in Imm(x)}(x-E(x))^2 \times P(X=x)$

E' una quantita' sicuramente maggiore di zero poiche' $(y-E(X))^2\ge0$ e $P(X=x)\ge0$.

La varianza, scarto quadratico medio, e' la media degli scarti quadratici ed e' quindi una misura di dispersione, ovvero mi dice mediamente quanto posso trovare valori lontani dalla media.

La varianza di x vale 0($Var(x)\equiv 0$) quando gli scarti quadratici sono nulli, ovvero $(y-E(X))^2=0$. Avviene quando la varianza di $y$ ha un solo punto nell'immagine, che e' costante degenere($c$) che prende un solo valore.

La radice quadrata della varianza e' definita **deviazione standard**

$\sqrt{Var(x)}=StDev(x)$

##### Esempio
$x$
$Imm(x)=\{1,-1\}$
$P(x)=(1/2)$

$E(x)=\displaystyle \sum_{x \in Imm(x)}x \times P(X=x)=1 \times 1/2-1 \times1/2=0$
$Var(x)=\displaystyle \sum_{x \in Imm(x)}(x-E(x))^2 \times P(X=x)=(1-E(x))^2\times P(X=1)+(-1-E(x))^2\times P(X=-1)=1\times 1/2 +(-1)^2\times 1/2=1$

$y$
$Imm(y)=\{-100,100\}$
$E(y)=\displaystyle \sum_{y \in Imm(y)}x \times P(Y=y)=100\times P(Y=100)-100\times P(Y=-100)=0$
$Var(y)=\displaystyle \sum_{y \in Imm(y)}(y-E(y))^2 \times P(Y=y)= (100-0)^2\times 1/2+ (-100-0)^2\times 1/2=100^2=10000$

#### Proprieta' di media e varianza
- $E(aX+bY)=aE(X)+bE(Y)$
	- La media di combinazioni linerari e' uguali alla combianzione lineare di medie
	- La media e' un'operatore lineare
	- $E(10Y)=1-\times E(y)$
	- $E(X+)$
- $Var(X)=E(x^2)-E^2(x)$
	- Possiamo riscrivere la varianza come momento secondo meno quadrato della media
- La varianza non e' lineare: $Var(aX+b)=a^2\times Var(x)$
	- $Var(10X)=10^2\times Var(X)=100\times Var(X)$
	- La varianza e' quadratica nelle costanti e invarianti nelle traslazioni

#### Media e varianza delle variabili discrete note
##### Prove bernulliane
$E(x)=\displaystyle \sum_{x\in Imm(x)}x\times P(X=x)=0\times P(X=0)+1\times P(X=1)=1\times p=p$

$Var(x)=\displaystyle \sum_{x \in Imm(x)}(x-E(x))^2 \times P(X=x)=p^2\times(1-p)+(1-p^2)\times p=p\times (1-p)$

##### Binomiale
$E(x)=n\times p$
$Var(x)=n\times p\times(1-p)$
##### Geometrica
$E(x)=\frac{1}{p}$
$Var(x)=\frac{1-p}{p^2}$
###### Poisson
$E(x)=\lambda$
$Var(x)=\lambda$

##### Ipergeometrica
$E(x)=n\times \frac{S}{N}$

## PMF congiunte

Data una coppia di variabili aleatorie $X$ ed $Y$, definisco come pmf congiunta la seguente funzione 

$P_{XY}\times^{Imm(X)\times Imm(y)\to R}_{(xy)\to P_{x,y=P(\{X=x\}\cap\{Y=y\})}}$