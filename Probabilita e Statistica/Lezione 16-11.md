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

[mi sono distratto]

### Media e varianza di variabili aleatorie continue 
Diciamo media di $x$ la seguente quantita':

$E(x)=\int^{+\infty}_{-\infty}x\times f_x(x)dx$

Diciamo come varianza di $x$ la quantita':

$Var(x)=\int^{+\infty}_{-\infty}=(x-E(x))^2\times f_x(x)dx$

ovvero lo scarto quadratico medio.

### $x~Normale(\mu,\sigma^2)$
$f_x(x)=\frac{1}{\sqrt{2\pi \sigma^2}} exp[-\frac{(x-y)^2}{2\sigma^2}]$

La normale del tipo $y~NORMALE(0,1)$ e' detta standard. 

#### Proprieta'
La normalita' e' preservata per trasformazioni lineari.


## Funzione di distribuzione cumulata
La funzione di distribuzione cumulata, detta CDF: *cumulative distribution function*, di una variabile alatoria $x$ e' cosi' definita

$F_x:R\to R=x\to P(X\le x)=F_x(x)$