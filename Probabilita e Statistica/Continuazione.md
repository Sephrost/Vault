#### Esercizio 8
![[8.PNG]]
1. $P(R) = \frac{18}{28}\times\frac{17}{27}\times\frac{16}{26}=0.2491$
2. Stessa probabilità di prima, dato che ci chiede di estrarre almeno 3 palline rosse (ma noi già estraiamo 3 palline, non di più, non di meno).
3. $P(R) =\frac{18}{28}$ (Eventualmente, è possibile usare le somme totali ma il risultato non cambia -dovrebbero essere eventi indipendenti-).

#### Esercizio 9
![[9.PNG]]
1. Calcoliamo la Poisson con parametri $x=9$ e $\lambda=5$ 
```R  
dpois(x=9, lambda=5) = 0.0363
```
2. Calcoliamo il complementare della somma delle Poisson con $x\in[0,8]$ (per calcolare i casi in cui ha cantato 0, 1, 2... volte) e $\lambda=5$.
```R  
 1-sum(dpois(x=0:8, lambda=5)) = 0.0681
```
3. Calcoliamo la Poisson con variabile aleatoria pari a 0, considerando i casi in cui il canarino canta nei giorni di sole e non. La si può tradurre come la formula delle somme totali, in cui calcoliamo la probabilità che il canarino non canti condizionata dal meteo.
```R  
dpois(0, 5) * (254/365) + dpois(0,2) * (1-(254/365)) = 0.0459
```
4. $P(Sole| Cantato^C) = \frac{P(Cantato^C| Sole)\times P(Sole)}{P(Cantato^C)}= \frac{0.0067\times \frac{254}{365}}{0.0459}= 0.1022$ 
```R  
# probabilità che non ha cantato dato che c'era il sole
dpois(0,5) = 0.0067
```

#### Esercizio 10
![[10.PNG]]
1. La finestra di osservazione si rimpicciolisce a 6 mesi, quindi lambda vale la meta (ovvero $1.5$). Calcoliamo il complementare che vi siano 0 o 1 terremoto.
```R  
1 - sum(dpois(0:1, 1.5)) = 0.44
```
2. Sapendo che $P(X\ge 2)=0.4421746$ (calcolo di cui sopra), calcoliamo
$P(X = 4 | X \ge 2) = \frac{P( X \ge 2 | X = 4)\times P(X = 4)}{P(X\ge2)}= \frac{1\times 0.04706652}{0.4421746}=0,11$
```R  
#probabilità che ci siano 4 terremoti in 6 mesi
dpois(4,1.5) = 0.04706652 
```

#### Esercizio 11
![[11.PNG]]
1. Usando la formula $Var(X)=E(X^2) - E^2(X)$ ottengo che
$E(X^2)=9+2^2 =13$
2. Essendo un'operazione lineare, basta sottrarre al risultato di prima 7, quindi il risultato è uguale a $6$.
3. Usando la formula $Var(aX + b)=a^2\times Var(X)$ ottengo che $Var(3X + 1) = 3^2 \times 9 = 81$
4. Sapendo che $StDev = \sqrt{Var(X)}$, calcoliamo la radice quadrata del risultato precedente, quindi otteniamo $9$.

#### Esercizio 12
![[12.PNG]]
1. Come una matrice, vediamo la cella corrispondente a $(X=10, Y=7)=\frac{1}{12}$
2. Calcoliamo la somma della colonna in cui $X=30$
$(X=30)=\frac{1}{12}+\frac{2}{12}+0+\frac{1}{12}=0.33$
3. L'indipendenza delle variabili aleatorie può essere calcolata sfruttando le PFM congiunte nel seguente modo: X e Y sono indipendenti se $P(\{X=x\} \cap \{Y=y\})=P(X=x) \times P(Y=y)$. Nel nostro caso, se $X=10$ e $Y=20$, la regola non viene rispettata e basta un controesempio per dimostrare che <b>non sono indipendenti</b>.