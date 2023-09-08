É il primo esempio di tecnica crittografica a chiave pubblica presentato.
Il suo scopo é di **permettere** uno **scambio** delle **chiavi** da usare per la cifratura simmetrica sicuro.

Questa tecnica é basata su **operazioni di aritmetica modulare**, in particolare sulla **difficoltá** di **calcolare** i **logaritmi discreti**.
### Modulo
Sia $a$ un intero e $n$ un intero positvo, definiamo l'operazione di **modulo** $a\mod n$ come il resto della divisione su $a$ per $n$.

Due interi $a$ e $b$ sono detti **congruenti in modulo $n$** se $a\mod n=b\mod n$.Puó anche essere scritto come $a\equiv b(\mod n)$
### Operazioni in aritmetica modulare
Dato l'operatore modulo ($\mod n$), é possibile definire delle operazioni con esso.
#### Proprietá dell'aritmetica modulare
L'aritmetica modulare gode delle seguenti proprietá:
1. $(a+b) \mod n=[(a\mod n)+(b\mod n)]\mod n$
2. $(a-b) \mod n=[(a\mod n)-(b\mod n)]\mod n$
3. $(a\times b) \mod n=[(a\mod n)\times(b\mod n)]\mod n$
###### Dimostrazione della somma
Siano $(a\mod n)=x$ e $b\mod n = y$, entrambi($x$ e $y$) minori di $M$.
Allora esiste una coppia di valori $j$ e $k$ per cui $a=x+j\times n$ e $b=y+k\times n$.

Quindi
$$
\begin{equation}
\begin{split}
(a + b) \mod n &=(x + jn + y + kn) \mod n \\
&=(x+y+(j+k)n)\mod n\\
&=(x+y)\mod n\\
&=[(a\mod n)+(b\mod n)]\mod n
\end{split}
\end{equation}
$$
> $(a\times b)\mod b=0$
###### Dimostrazione della moltiplicazione
Siano $(a\mod n)=x$ e $b\mod b = y$, entrambi($x$ e $y$) minori di $M$.
Allora esiste una coppia di valori $j$ e $k$ per cui $a=x+j\times n$ e $b=y+k\times n$.

Quindi 
$$
\begin{equation}
\begin{split}
(ab) \mod n &=[(x + jn)(y + kn)] \mod n \\
&=(xy+xkn+ykn+n^2jk)\mod n\\
&=(xy)\mod n\\
&=[(a\mod n)(b\mod n)]\mod n
\end{split}
\end{equation}
$$
poiché $z\times n\mod n=0$.
### La radice primitiva(generatore)
Viene detta **radice primitiva** di $n$ un intero le cui potenze modulo $n$ sono congruienti con i numeri coprimi ad $n$. In formule, $\alpha$ é una radice primitiva di $q$ se
$$\forall b<q\;\exists i\; |\;\alpha^i\mod q=b $$
La radice primitiva **genera** tutti i numeri dell'aritmetica modulo $n$.
> Esempio: **2 é la radice primitiva di 5**
> $2^0\equiv 1=1(\mod 5)$
> $2^1\equiv 2=2(\mod 5)$
> $2^2\equiv 4=4(\mod 5)$
> $2^3\equiv 8=3(\mod 5)$
> $2^4\equiv 16=1(\mod 5)$
> $\dots$
## L'algoritmo
Per utilizzare l'algoritmo sono note alcune informazioni:
- un intero primo $q$
- un intero $a$ che é la radice primitiva di $q$

Se si vuole creare una chiave condivisa tra due utenti A e B si procede nella seguente maniera:
- A sceglie un intero casuale $X_A$ minore di $q$, che sará la propria chiave privata
- A computa $Y_A=a^{X_A}\mod q$, ovvero la propria chiave pubblica
	- B effettua le medesime operazioni, ovvero computa la propria chiave privata $X_B<q$ e pubblica $Y_B=a^{X_B} \mod q$.
- A questo punto sia A che B sono in grado di calcolare la chiave condivisa $K$, ottenendo lo stesso risultato
	- A calcola $K=(Y_B)^{X_A}\mod q$
	- B calcola $K=(Y_A)^{X_B}\mod q$

![[Pasted image 20230821171010.png]]

Possiamo dimostrare che il risultato é il medesimo
$$
\begin{equation}
\begin{split}
K &= (Y_B)^{X_A} \mod q\\
&=(a^{X_B} \mod q)^{X_A} \mod q\\
&= (a^{X_B})^{X^A} \mod q\\
&=a^{X_BX^A} \mod q\\
&=(a^{X_A})^{X^B} \mod q\\
&=(a^{X_A} \mod q)^{X_B} \mod q\\
&= (Y_A)^{X_B} \mod q\\
\end{split}
\end{equation}
$$
Il valore segreto $K$ viene solitamente usato per condividere una chiave simmetrica segreta.
### Sicurezza di Diffie-Hellman
Un avversario vuole conoscre il valore segreto $K$, e le informazioni a sua disposizione sono
- la chiavi pubbliche $Y_A$ e $Y_B$
- il numero primo $q$
- la sua radice primitiva $a$

> Le chiavi private sono segrete.

L'avversario é quindi costretto a calcolare il **logaritmo discreto** per determinare la chiave privata di A o B, per esempio volendo ottenere quella di B dovrebbe calcolare 
$$X_B=dlog_{q,a}(Y_B)$$
per poi poter calcolare la chiave segreta $K$ nella stessa maniera di B
$$K=(Y_A)^{X_B}\mod q$$
La sicurezza di D-H sta nel fatto che é molto **economico** calcolare il **logarimo esponenziale** di un numero primo, mentre é molto difficile calcolare il logaritmo discreto, in quanto é un'operazione che richiede **forza bruta**, rendendo l'operazione impratica per numeri molto grandi.
### Requisiti di implementazione di Diffie-Hellman
Per poter rendere pratica l'implementazione di DH occorrono 3 requisiti fondamentali:
- Algoritmo efficiente per calcolare l'esponente modulare ($a^b\mod q$)
- Algoritmo efficiente per generare un numero primo $q$
- Algoritmo efficiente per generare una radice primitiva di $q$

> Per efficente intendiamo un problema polinomiale (in $P$)
#### Algoritmo per il calcolo dell'esponente modulare
Per poter ottenere un algoritmo polinomiale e veloce per il calcolo dell'esponente modulare una soluzione semplice come la seguente non andrebbe bene
```python
s = a
for i in range(1,b-1)
	s = (a*s)%q
end

return s%q
```
non andrebbe bene poiché avrebbe complessitá $O(b-1)$, che con $b$ avente $n$ bit porterebbe la complessitá a $O(2^{n-1})$, ovvero $NP$.
##### Algoritmo per il calcolo dell'esponente modulare ricorsivo
Possiamo peró effettuare delle osservazioni:
$$

\begin{equation}
    \begin{cases}
      se \;b=0  & a^b\mod q=1 \\
      se \;b\;é\;pari &a^b \mod q=(a^\frac{b}{2}\mod q)^2\mod q \\
      se \;b\;é\;dispari &a^b \mod q=(a^{b-1}\mod q)^2\mod q
    \end{cases}
\end{equation}

$$
portando la complessitá a $O(2\log_2 b)$, e quindi $O(log_2n)$, permettendoci di scrivere il seguente metodo ricorsivo
```python
function expmod(a,b,q):
	if(b==0) return 1
	if(b%2==0) 
		return sq(expmod(a,b/2,q))%q # b dispari, sq ritorna l'input alla seconda
	return (a*expmod(a,b-1,q))%q # b pari
end
```
> É possibile dimezzare l'esponente applicando il divide-et-impera all'algoritmo: $(a^b)\mod c$ é uguale a $(a^{b/2}\times a^{b/2})\mod c$
##### Algoritmo per il calcolo dell'esponente modulare iterativo
Gli algoritmi ricorsivi possono essere molto dispendiosi a livello di spazio, presentiamo quindi una versione iterativa:

Con questo approccio rappresentiamo $b$ come una sequenza di $k+1$ bit($b=b_j\dots b_2b_1b_0$).
 ```python
function expmod(a,b,q):
	d=1
	for i in range(k,0):
		d = (d*d)%q
		if b[i]==1:
			d = (d*a)%q
		end
	end
	return d
end```
#### Algoritmo efficiente per generare un numero primo grande
Per evitare che il calcolo del logaritmo discreto sia facile per un'avversario, il valore del numero primo generato $q$ deve essere abbastanza grande da rendere il calcolo infattibile.

Un primo approccio é sempre del tipo deterministico: 
1. genero un numero casuale $M$ di $k$ bit
2. per ogni numero in range $2\to \sqrt M$ controllo se é un divisore
	1. Se ne trovo uno il numero non é primo, e torno al passo 1
	2. Altrimenti é primo

Questo algoritmo presenta peró complessitá proibitiva($O(2^{\frac{k}{2}})$), ed é quindi troppo lento.
###### Dimostrazione dell'infinitá dei numeri primi(Euclide)
Supponiamo che i numeri primi siano finiti, allora $p$ é l'ultimo numero primo.
Sia quindi $q$ il prodotto dei numeri primi fino a $p$($\prod_{i=2}^pi$).
Allora:
- Se $q+1$ é primo, $p$ non era l'ultimo
- Se $q+1$ non é primo, allora é divisibile per un qualche numero primo $r>p$, in quanto non era divisibile per alcun numero minore di $p$.

$p$ non puó essere quindi l'ultimo numero primo.
###### Teorema dei numeri primi
Sappiamo quindi che ci sono infiniti numeri primi, ma quanto é facile trovarne uno in un tempo utile? 

Sia $\pi(x)$ il numero di primi minori dell'intero $x$.
Allora $\pi(x)\sim \frac{x}{\ln x}$, ovvero $\lim_{x\to \infty}\frac{\pi(x)}{x/\ln(x)}=1$ 

Per esempio:
- $\pi(10)=4$
- $\pi(30)=10$

In crittografia useremo numeri primi grandi, di almeno 100 cifre decimali.
I numeri primi di cento cifre decimali sono 
$$
\pi(10^{100})-\pi(10^{90})\simeq [\frac{10^{100}}{\ln(10^{100})}]-[\frac{10^{99}}{\ln(10^{99})}]
\simeq3,9\times10^{97}
$$
I numeri di 100 cifre sono $10^{100}$, quindi avermo in media un numero primo ogni $\frac{10^{100}}{3,9\times10^{97}}=256$ tentativi.

É un buon risultato, ma puó essere uteriormente rimuovendo dal dominio  di ricerca i numeri che certamente non sono primi, come i multipli di 2,3,5 e 7.
##### Approccio probabilistico
Osserviamo ora l'approccio probabilistico, ovvero utilizziamo un test di probabilitá non sempre accurato:
1. genero un numero casuale $M$ di $k$ bit
2. per ogni numero in range $0\to T$ 
	1. genero $a<M$ casualmente
	2. controllo se $a$ divide $M$
		1. Se la condizione é verificata, torno ad 1
3. Restituisco $M$

Con questo approccio sappiamo che la probabilitá che $M$ si primo é maggiore di $1-2^{-T}$, quindi basta impostare un $T$ molto grande per ridurre la probabilitá ché $M$ non sia primo.

> Per esempio con $T=100$ la probabilità che un numero sia primo é $>0,999999999999999999999999999999211$
##### Test di Miller-Rabin
Per verificare che un grande numero sia primo si utilizza solitamente il **Test di Miller-Rabin**.

Questo ha probabilitá di successo di almeno un quarto per ogni tentativo.
###### Proprietá dei numeri primi
Per poter utilizzare Miller-Rabin ci avvaliamo di due **proprietá fondamentali** dei **numeri primi**:
- Se $M$ é un numero primo e $a<M$, allora $a^{M-1}\mod M=1$(Piccolo teorema di Fermant)
- Se $M$ é primo e $x^2\mod M=1$, allora $x=1$ oppure $x=M-1$
Andiamo a dimostrare quese proprietá.
###### Dimostrazione principio fondamentale
Per dimostrare la seconda ci avvaliamo di questo principio fondamentale.

Se esistono $x$ e $y$ tali per cui $x^2\equiv y^2(\mod n)$ e $x\not\equiv\pm y (\mod n)$ allora $n$ non é primo.

Prendiamo quindi $d= MCD(x-y,n)$, allora:
- se $d=n$, allora $x\equiv y(\mod n)$, e quindi $d\ne n$
- se $d=1$, allora $n|x^2-y^2=n|(x-y)\times(x+y)$ come scritto nella premessa,ma n non puó dividere $x-y$ e deve quindi poter dividere $x+y$. 
Ció contraddice peró la premessa, quindi $d$ non puó essere né 1 né $n$, quindi $n$ non é primo poiché possiede sicuramente un'altro divisore.


#### Algoritmo efficiente per generare una radice primitiva $\alpha$ di $q$
Per ottenere una radice primitiva si utilizza un metodo probabilistico, genereremo $a<q$ e verificheremo se non é un radice primitiva

### Algoritmop

#### Attacco man in the middle(MITM)
Il protocollo di Diffie-Hellman é peró debole all'attacco **man in the middle**.

Supponiamo che un'utente Alice voglia inviare un messaggio a Bob, e che l'avversario si Darth, allora
1. Alice e Bob generano ciascuno una coppia di chiavi privata/pubblica ($<X_a,Y_a>$,$<X_b,Y_b>$).
2. Darth genera due chiavi private $X_{d1}$ e $X_{d2}$ e le corrispondenti chiavi pubbliche $Y_{d1}$ e $X_{d2}$
3. Alice trasmette $Y_a$ a Bob
4. Bob intercetta $Y_a$ e inoltra a Bob $Y_{d1}$, e calcola l'esponente modulare $K2=Y_a^{X_{d2}}\mod q$
5. Bob riceve $Y_d1$, calcola $K1=(Y_{d1})^{X_{b}}\mod q$
6. Bob trasmette quindi $Y_b$ ad alice
7. Darth intercetta $Y_b$ e trasmette $Y_{d2}$ ad Alice, calcolando inoltre $K1=(Y_{b})^{X_{d1}}\mod q$
8. Alice riceve $Y_{d2}$ e calcola $K2 = (Y_{d2})^{X_a} \mod q$

Da questo momento la comunicazione tra Alice e Bob é compromessa da Darth, il quale é in grado di decifrare eventuali messaggi e eventualmente alterarne il contenuto, poiché Alice e Darth condividono la chiave $K2$, mentre Bob e Darth condividono la chiave $K1$.

![[Pasted image 20230823164817.png]]

