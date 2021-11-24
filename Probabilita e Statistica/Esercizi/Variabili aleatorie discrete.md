### Esercizio 1
![[Pasted image 20211123120402.png]]

1. Il numero di casi favorevoli é $5$, no need to explain
2. Il numero di casi possibili é $5+8=13$
3. La probabilitá di estrarre una gialla é $P(G)=\frac{5}{13}=\\0,3846$

![[Pasted image 20211123120842.png]]

4. La probabilitá che entrambe le palline siano gialle con reimbussolamento é uguale a $P(G)^2+P(R)^2=\frac{5}{13} \times \frac{5}{13}+\frac{8}{13}\times \frac{8}{13}=0,5266$
5. Interpreto la consegna come cercare il complementare di ottenere 2 palline rosse:$1-P(R\times R)=1-(\frac{8}{13})^2=0,6213$

![[Pasted image 20211123123655.png]]
Grazie JJ per la spiegazione:
6. Usiamo la formula delle probabilitá totali:
$$
\begin{gather}
P(G|GG)P(GG)+P(G|RG)P(RG)\times 2+P(G|RR)P(RR)= \\
1\times (\frac{5}{13})^2+\frac{1}{2}\times(\frac{5}{13}\times \frac{8}{13})\times 2+0=0,3846
\end{gather}
$$ 
7. Applichiamo l'inversione della probabilitá condizionata $P(GR|G)=\frac{P(G|GR)\times P(GR)}{P(G)}=\frac{\frac{1}{2}\times2\times \frac{5}{13}\times\frac{8}{13}}{\frac{5}{13}}=0,6154$
### Esecizio 2
É identico a quello prima, ma segnamo i cambiamenti
![[Pasted image 20211123173345.png]]
3. $P(VVV)+P(BBB)(\frac{10}{14}\times\frac{9}{13}\times\frac{8}{12})+(\frac{4}{14}\times\frac{3}{13}\times\frac{2}{12})=0,3297$
4. $1-P(BBB)=1-(\frac{4}{14}\times\frac{3}{13}\times\frac{2}{12})=0,9890$

![[Pasted image 20211123174016.png]]
	5. - $$
	\begin{gather}
	P(V|VVV)P(VVV)+P(V|VVB)P(VVB)\times8+P(V|VBB)P(VBB)\times 8+P(V|BBB)P(BBB)=\\ 1\times\frac{10}{14}\times\frac{9}{13}\times\frac{8}{12}+\frac{2}{3}\times\frac{10}{14}\times\frac{9}{13}\times\frac{4}{12}\times3+\frac{1}{3}\times\frac{10}{14}\times\frac{4}{13}\times\frac{3}{12}\times3+0=0,7143
\end{gather}$$

7. $P(VVB|V)=\frac{P(V|VVB)\times3\times P(VVB)}{P(V)}=\frac{0,3297}{0,7143}=0,4615$
### Esercizio 3
![[Pasted image 20211123123855.png]]

1. Usiamo una variabile aleatoria geometrica, ponendo 
	- $k=5$(prove effettuate)
	-  $p=\frac{8}{17}=0,4706$
Applicando la formula otteniamo:
	- $Px(5)=(1-\frac{8}{17})^{5-1} \times \frac{8}{17}=0,0370$ 
2. Interpreto la consegna come trovare il complementare di fare 4 o meno estrazioni, quindi:
	- $Px(1,2,3,4)=\sum^{4}_{k=1}(1-\frac{8}{17})^{k-1}\times \frac{8}{17}=0,9215$ 
	- $Px(k\ge 5)=1-0,9215=0,0785$

![[Pasted image 20211123131705.png]]
3. La probabilitá é quella di ottenere 4 su un dado a 5 facce, quindi $P(4)=\frac{1}{5}=0,2$
4. Stesso ragionamento di sopra:$P(6)+P(7)=\frac{1}{7}+\frac{1}{7}=0,2857$

### Esercizio 4
![[Pasted image 20211123172524.png]]
1. Applichiamo la formula delle probabilitá totali:$P(N)=P(N|M)P(M)+P(N|M^c)P(M^c)=(1-0,75)\times 0,5+(1-0,03)\times 0,5=0,61$
2. Applichiamo l'inversione della probabilitá condizionata:$P(M^c|N)=\frac{P(N|M^c)\times P(M^c)}{P(N)}=\frac{(1-0,03)\times 0,5}{0,61}=0,7951$
3. Stesso procedimento di sopra, ma prendiamo $P(N^c|M^c)$ dai dati del problema:$P(M^c|N^c)=\frac{P(N^c|M^c)\times P(M^c)}{P(N^c)}=\frac{0,03\times 0,5}{0,39}=0,0385$
### Esercizio 5
![[Pasted image 20211123143046.png]]

1. Usiamo una v.a. geometrica sommando i gli 8 giorni indicati:$Px(1,..,8)=\sum^{8}_{k=1}(1-0,25)^{k-1}\times 0,25=0,8999$
2. Usiamo la probabilitá condizionata per calcolare $P($entro il decimo giorno|entro 8 giorni$^c))$, utilizziamo quindi delle geometriche $Px(k)$:$\frac{Px(9)+Px(10)}{1-Px(1,..,8)}$
3. Calcolo la probabilitá che vanga spedito, o da Giovanna o da sua madre$P(S|MG)P(MG)+P(S|MG^c)P(MG^c)=0,69\times 0,73+0,25\times 0,27=0,5712$, dopo di che la applico ad una v.a. geometrica $Px(1,..,8)=\sum^{8}_{k=1}((1-0,5712)^{k-1}\times 0,5712)=0,9989$

### Esercizio 6

![[Pasted image 20211123184328.png]]

### Esercizio 7 
![[Pasted image 20211123152006.png]]
1. Utilizziamo una variabile aleatoria binomiale $Px(K)=\sum^9_{k=5}(\binom{9}{k}\times 0,61^k(1-0,61)^{n-k})=0,7540$
	```R
	sum(dbinom(5:9,prob=0.61,9))
	```
2. Stessa cosa di sopra,m acambiamo la probabilitá:$Px(K)=\sum^9_{k=5}(\binom{9}{k}\times 0,69^k(1-0,69)^{n-k})=0.8885$
3. Applichiamo la media strana di Ale:$125\times 9 \times0,61=686,25$, perché sí(testuali parole).
4. Riapplichiamo la media strana di Ale $125\times 9 \times0,69=776,25$
5. Facciamo la differenze tra le medie strane di Ale=$776,25-686,25=90$


Grazie Miriam <3
### Esercizio 8
![[8.PNG]]
1. $P(R) = \frac{18}{28}\times\frac{17}{27}\times\frac{16}{26}=0.2491$
2. Stessa probabilità di prima, dato che ci chiede di estrarre almeno 3 palline rosse (ma noi già estraiamo 3 palline, non di più, non di meno).
3. $P(R) =\frac{18}{28}$ (Eventualmente, è possibile usare le somme totali ma il risultato non cambia -dovrebbero essere eventi indipendenti-).

### Esercizio 9
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

### Esercizio 10
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

### Esercizio 11
![[11.PNG]]
1. Usando la formula $Var(X)=E(X^2) - E^2(X)$ ottengo che
$E(X^2)=9+2^2 =13$
2. Essendo un'operazione lineare, basta sottrarre al risultato di prima 7, quindi il risultato è uguale a $6$.
3. Usando la formula $Var(aX + b)=a^2\times Var(X)$ ottengo che $Var(3X + 1) = 3^2 \times 9 = 81$
4. Sapendo che $StDev = \sqrt{Var(X)}$, calcoliamo la radice quadrata del risultato precedente, quindi otteniamo $9$.

### Esercizio 12
![[12.PNG]]
1. Come una matrice, vediamo la cella corrispondente a $(X=10, Y=7)=\frac{1}{12}$
2. Calcoliamo la somma della colonna in cui $X=30$
$(X=30)=\frac{1}{12}+\frac{2}{12}+0+\frac{1}{12}=0.33$
3. L'indipendenza delle variabili aleatorie può essere calcolata sfruttando le PFM congiunte nel seguente modo: X e Y sono indipendenti se $P(\{X=x\} \cap \{Y=y\})=P(X=x) \times P(Y=y)$. Nel nostro caso, se $X=10$ e $Y=20$, la regola non viene rispettata e basta un controesempio per dimostrare che <b>non sono indipendenti</b>.

