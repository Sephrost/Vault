# Formulario 
## Variabili aleatorie
Una variabile aleatoria é una funzione di $\Omega$ in R

Le variabili aleatorie si dividono in 
### Variabili aleatorie discrete
Hanno immagine discreta(finita o numerabile)
#### Notazione
$X(\omega)=x$ con $x\in R$
#### V.A. discrete note
##### V.A. di Bernoulli
###### Esperimento Probabilistico di riferimento
É un esperimento probabilistico di tipo dicotomico, ovvero con 2 possibili esiti:
- 1: Successo (p)
- 0: Fallimento (1-p)
###### PMF
Px:
- $Im(X)\to R$
- $x\to Px(x)=P(X=x)$
 
con $Im(X)=\{0,1\}$


##### V.A. binomiale
###### Esperimento Probabilistico di riferimento
$N$ prove ripetute di bernulliano indipendenti e identicamente distribuite, con probabilitá di successo costante.

É una V.A. che conta il numero di successi ottenuti in $n$ prove.

###### PMF
Px:
- $Im(X)\to \{0,1,2,..,n\}$
- $x\to Px(x)=P(X=x)$
 
$Px(K) = P(X=K)=\binom{n}{k}\times p^k(1-p)^{n-k}$

dove
- $p$ indica la probabilitá di successo
- $n$ indica l'higher end $k$ il lower end del range di oggetti di interesse
In R scriviamo 
```R
dbinom(k,n,p)
```

##### V.A. geometriche
###### Esperimento Probabilistico di riferimento
Svolgiamo prove ripetute di tipo bernulliano fino a quando non otteniamo il primo successo

É una V.A. che conta il numero di prove effettuate.

###### PMF
Px:
- $Im(X)\to R$
- $x\to Px(x)=P(X=x)=P(\{\omega \in R|X(\omega)=x\}$

$Px(k)=(1-p)^{k-1}\times p$

dove 
- $k-1$ rappresenta le prove effettua meno il successo
- $p$ é il successo, dove $p=1$
In R scriviamo
```R
dgeom(k-1,p)
```
##### V.A. di Poisson
###### Esperimento Probabilistico di riferimento
X conta il numero di successi che si verificano in una finestra di osservazione

###### PMF
- $Im(X)=\{0,1,2,3,...\}$
- $Px(k)=P(X=k)=\frac{\lambda^k}{k!}\times e^{-\lambda}$
 
o in R
```R
dpois(x,lambda)
```
dove 
- $\lambda$ é il parametro di intensitá, ovvero quante volte di solito si verifica un determinato evento
- $e=2,718$ é una costante
- $x$ indica il numero di eventi di interesse
###### Proprietá 
Se $X~Poisson(\lambda)$ su una finestra di osservazione, se dilatiamo la finestra con una parametro $k$, se:
- $k>1\to allarghiamo$
- $k<1\to Stringiamo$

##### V.A. ipergeometrica
###### Esperimento Probabilistico di riferimento
Estraiamo senza reimbussolamento $n$ oggetto da una scatola che ne contiene $N$ dei quali $C$ hanno una **caratteristica di interesse**

###### PMF
- $Im(X)=\{0,1,2,...,min(n,C)\}$
- $Px(k)=P(X=k)=\frac{\binom{C}{k}\times \binom{N-C}{n-k}}{\binom{N}{n}}$
dove:
- $k$ rappresentano gli oggetti con la caratteristica di interesse, su una percentuale
- $n$ sono gli oggetti totali sulla percentuale
- $C$ sono gli oggetti con una caratteristica di interesse sull'estrazione
- $N$ sono gli oggetti totali su cui si basa l'estrazione

In R scriviamo
```R
dhyper(k,C,N-C,n)
```
#### Media
Definiamo momenti di ordine K della variabile aleatoria discreta $x$ la media di $X^k$ cosi' calcolata:

$E(x^k)=\displaystyle \sum_{x \in imm(x)} x^k\times px(k)$
#### Varianza
Definiamo varianza di x la seguente quantita':

$var(x)=E[(x-E(x))^2]=\displaystyle \sum_{x \in Imm(x)}(x-E(x))^2 \times P(X=x)$

dove $x-E(x)$ é lo scarto quadratico medio.

La radice quadrata della varianza e' definita **deviazione standard**

$\sqrt{Var(x)}=StDev(x)$

Le deviazioni standard non si possono sommare.
##### Proprietá di media e varianza
- $E(aX+bY)=aE(X)+bE(Y)$
	- $E(10Y)=1-\times E(y)$
	- $E(X+Y)=E(X)+E(Y)$
- $Var(X)=E(x^2)-E^2(x)$
	- Possiamo riscrivere la varianza come momento secondo meno quadrato della media
- La varianza non e' lineare:
	- $Var(10X)=10^2\times Var(X)=100\times Var(X)$
	- La varianza e' quadratica nelle costanti e invarianti nelle traslazioni

#### Media e varianza delle variabili discrete note
##### Prove bernulliane
$E(x)p$

$Var(x)=p\times (1-p)$

##### Binomiale
$E(x)=n\times p$
$Var(x)=n\times p\times(1-p)$
##### Geometrica
$E(x)=\frac{1}{p}$
$Var(x)=\frac{1-p}{p^2}$
###### Poisson
$E(x)=\lambda$
$Var(x)=\lambda$

### Variabili aleatorie continue
Sono variabili aleatotrie che hanno immagine con natura del continuo, ovvero se $Imm(x)$ e' un insieme continuo($Imm(x)\subseteq$).

Per trattarle usiamo la PMF 

### Densita' 
Una variabile aleatoria $x$ continua ammette una funzione $f_x$ $R\to R_+$(non negativa) detta **densita'** (PDF:*Probability density function*) tale che :

$P(x\in A)=\int_a f_x(t)dt$

in particolare x $A=\{a,b\}$

$P(x\in a)=P\{a\le x \le b\}=\int^b_af_x(t)dt$

##### Osservazione
se $A=\{a\}$ $P(x\in A)=P(x=a)=\int^a_af_x(t)dt=0$

Le variabili aleatorie continue assumono valori singoli con probabilita' nulla.

Quindi di conseguenza

$\int^{+\infty}_{-\infty}f_x(t)=P(-\infty\le X \le +\infty)=P(\Omega)=1$

##### X~uniforme[a,b]
Rappresenta la probabilitá che un evento si verifichi in un'intervallo.

É una variabile aleatoria continua con densitá 
$fx(t)=\displaystyle\{^{0\_se\_ t!\in[a,b]}_{\frac{1}{b-a}\_if\_t\in [a,b]}$

$P(a<X<b)=\frac{b-a}{\beta-\alpha}$, con intervallo $[\alpha,\beta]$

###### Media di un un'uniforme
$E[X]=\frac{\alpha+\beta}{2}$
###### Varianza di un un'uniforme
$Var[X]=\frac{(\alpha-\beta)^2}{12}$
$Var[X^2]=\frac{\beta^2+\alpha \beta+\alpha^2}{3}$
##### X~Esponenziale($\lambda$)
Dato $P(x\ge y)$
É una variabile aleatoria continua con densitá 
$fx(t)=\displaystyle\{^{\lambda e^{-\lambda t}\_se\_t\ge 0}_{0\_if\_t<0}$
in R scriviamo
```R
pexp(y,lambda)
```
###### Media di un esponenziale
$E[X]=\frac{1}{\lambda}$
###### Varianza di un esponenziale
$Var(x)=\frac{1}{\lambda^2}$
###### Assenza di memoria
$a$
### x~$Normale(\mu,\sigma^2)$
$f_x(x)=\frac{1}{\sqrt{2\pi \sigma^2}} exp[-\frac{(x-\mu)^2}{2\sigma^2}]$
dove:
- $\mu$ é la distribuzione normale di media
- $\sigma$ é la deviazione standard
Su R scriviamo
```R
pnorm(y,mu,sigma)
```
La normale del tipo $y~NORMALE(0,1)$ e' detta standard. 
#### Media della normale
$E[x]=\mu$
#### Varianza della normale
$Var(X)=\sigma^2$
#### Proprieta'
La normalita' e' preservata per trasformazioni lineari.


## Funzione di distribuzione cumulata
La funzione di distribuzione cumulata, detta CDF: *cumulative distribution function*, di una variabile alatoria $x$ e' cosi' definita

$F_x:R\to R=x\to P(X\le x)=F_x(x)$

### Strumenti per Calcolare P con variabili Aleatorie
La **funzione della massa di probabilitá** (PMF) é cosí definita
Px: 
- $Im(x)\to R$
- $x\to Px(x)=P(X=x)=P(\{\omega \in R|X(\omega)=x\})$

### PMF congiunte

Data una coppia di variabili aleatorie $X$ ed $Y$, definisco come pmf congiunta la seguente funzione 

$P_{XY}\times^{Imm(X)\times Imm(y)\to R}_{(xy)\to P_{x,y=P(\{X=x\}\cap\{Y=y\})}}$

Usando la PMF congiunta posso calcolare le PMF marginali(delle singole variabili aleatorie)
$$
\begin{gather}
Px(x)=p(X=x)=P(\{X=x\}\cap\Omega)=P(\{X=x\}\cap\cup\{Y=y\})=\\ P(\displaystyle \bigcup_{y\in Imm(y)}\{X=x\}\cap\{Y=y\})=\displaystyle \sum_{y\in Imm(y)}P_{x,y}(x,y)
\end{gather}
$$

La P(X=x) e' uguale alla probabilita' che X=x e Y=y per uno qualunque dei valori nella sua PMF

La PMF congiunta e' il prodotto delle marginali

## Indipendenza tra variabili aleatorie
$A$ e $B$ sono indipendenti se:
- $P(A|B)=P(A)$
- $P(B|A)=P(B)$
- $P(A\cap B)=P(A)\times P(B)$


