### Esercizio 1
![[Pasted image 20211124161209.png]]
1. Usiamo la formula dell'esponenziale:$1-\int^{2,2}_{0}(1,5\times 2,2718^{-(1,5\times 2,2)})=0,0369$
2. Stessa cosa di sopra: 
	```R
	pexp(1.73,1.5)
	```
3. $Media=\frac{1}{1,5}=0,6667$

### Esercizio 2
![[Pasted image 20211124164151.png]]

1. ```R
	pnorm(4.1,3.8,0.3)=0.8413
	```
2. ```R
pnorm(4.25,3.8,0.3)-pnorm(3.95,3.8,0.3)=0,9331928-0,6914625=0,2417```

### Esercizio 3
![[Pasted image 20211125125133.png]]
La risposta é la B e vale 
```R
1-pnorm(0,-2,2)=0.1587
```
### Esercizio 4
![[Pasted image 20211125125739.png]]
1. Sapendo che la media di $X$ é 100, la media di $6X$ é $100\times 6=600$
2. Sapendo che $\lambda=\frac{1}{100}$, allora la varianza di $X$ é uguale a $\frac{1}{(\frac{1}{100})^2}=(100)^2=10000$ e quindi la varianza di $6x$ é uguale a $6^2\times 10000=360000$, poiché la varianza é quadratica
3. $P(X>200)=1-pexp(200,\frac{1}{100})=0.1353$
4. Usiamo l'assenza di memoria:$P(X>200|p>130)=pexp(200-130,\frac{1}{100})=$
### Esercizio 5
![[Pasted image 20211125164815.png]]
1. $300\times5+250$
2. Poiché la deviazione standard non puó essere sommata, sommiamo invece la varianza:$\sqrt{(290\times5)^2+290^2}=1456.271$
3. ```R
	pnorm(0,300,290)=0.1505 
	```

4. ```R
	sum(dbinom(3:5,5,1-pnorm(0,300,290)))=0.9731
	```

### Esercizio 6
![[Pasted image 20211125171940.png]]
1. ```R
	1-pexp(480,1/160)=0.0498
	```
2. ```R
	sum(dbinom(1:6,6,1-pexp(480,1/160)))
	```
3. La media é lineare, quindi $E(x_1+X_2)=160+160=320$
4. $Var(X_1+X_2)=(\frac{1}{(\frac{1}{160})^2})\times2$

### Esercizio 7
![[Pasted image 20211125174740.png]]
1. ```R
	1-pnorm(37,36.4,sqrt(0.5))
	```
2. ```R
	(1-pnorm(37,36.4,sqrt(0.5)))*(1-pnorm(37,36.5,sqrt(0.6)))
	```
3. Ce lo dá il testo: $36.4$
4. $Var(2X+7)=2^2Var(X+7)=2^2Var(X)=2$

### Esercizio 8
![[Pasted image 20211125180609.png]]
1. $P(9<X<18)=\frac{18-9}{18-4}=0,6429$
2. ```R
	sum(dbinom(1:5,5,punif(9,4,18)))
	```

3. $E(6X)=\frac{18+4}{2}\times5=55$
4. $Var(5X)=\frac{(18-4)^2}{12}\times 5^2$