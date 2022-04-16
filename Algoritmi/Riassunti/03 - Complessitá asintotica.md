## Complessità asintotica
Il tasso di crescita del tempo di esecuzione di un'algoritmo ci fornisce una semplice caratterizzazione della sua efficienza.

Nel caso di input particolamente grandi studiamo quindi l'**efficienza asintotica** dell'agoritmo, ovvero come aumenta il tempo di esecuzione di un algoritmo al crescere della dimensione dell’input, senza limitazioni.

Per far ció introduciamo alcune **notazioni** che possono essere utili per **rappresentare** l'efficienza asintotica di un algoritmo.

### Notazione Asintotica

> Le notazioni che usiamo per descrivere il tempo di esecuzione asintotico di un algoritmo sono definite in termini di funzioni il cui il dominio $\in N$

> Quasi sempre ci capiterá di utilizzare il simbolo = al posto del simbolo $\in$, é una storpiatura voluta

#### Notazione $O$

La notazione $O$ (detto **o grande**) si utilizza per descrivere la crescita di una funzione **trascurando costanti** moltiplicative e un **numero finito** di **valori**.

Si usa inoltre per assegnare un **limite superiore** a una funzione

###### Definizione di $O$

$$f(n)\in O(g(n))\iff \exists c>0,\exists n_0,\forall n>n_0(f(n)\le c\cdot g(n)) $$

$f(n) \in O(g(n))$ significa che $f(n)$ **cresce**, a parte un fattore costante $c$ e trascurando un numero finito di valori (quelli $\le n_0$), al massimo come la funzione $g(n)$.

![[Pasted image 20220329175409.png|300]]

> Si scrive $f(n) = O(g(n))$ se esistono delle costanti positive $n_0$ e $c$ tali che, a destra di $n_0$, il valore di $f(n)$ e sempre uguale o minore di $c\cdot g(n)$.

##### $O$ come notazione insiemistica

La notazione $O$ è una **notazione insiemistica**. 

L'insieme $O(g(n))$ indica l'**insieme** di **funzioni** che sono $O$ di $g(n)$.

###### Esempio
Per esempio, l'insieme $O(n)$ indica l'insieme di tutte le funzioni che crescono al massimo linearmente. 

##### Algebra di $O$
$$
\begin{gather*}
f(n)+O(g(n))=O(f(n)+g(n))\\
f(n) \cdot O(g(n)) =O(f(n) \cdot g(n))\\
c\cdot O(f(n))=O(f(n))\\
O(f(n))+O(f(n))=O(f(n))\\
\end{gather*}
$$

#### Notazione $Θ$
La notazione $Θ$ fornisce invece una relazione di equivalenza.
###### Definizione di $Θ$
$$f(n) \in \Omega(g(n))\iff \exists  c>0,\exists n_0,\forall > n_0(f(n)\ge c\cdot g(n))$$

Una funzione $f(n)$ appartiene all’insieme $Θ(g(n))$ se esistono delle costanti positive $c_1$ e $c_2$ tali che essa possa essere compresa fra $c_1g(n)$ e $c_2g(n)$, per un valore sufficientemente grande di $n$.

In altre parole, per ogni $n \ge n_0$, la funzione $f(n)$ é **uguale** a  $g(n)$ a meno di un fattore costante.

![[Pasted image 20220329174918.png|300]]

>   Si scrive $f(n) = Θ(g(n))$ se esistono delle costanti positive $n_0$, $c_1$ e $c_2$ tali che, a destra di $n_0$, il valore di $f(n)$ e sempre compreso fra  $c1\cdot g(n)$ e $c2\cdot g(n)$, estremi inclusi.

#### Notazione $\Omega$
Cosí come la notazione $O$ fornisce un **limite** asintotico **superiore** a una funzione, la notazione $\Omega$ fornisce un **limite** asintotico **inferiore**.
###### Definizione di $\Omega$
$$f(n)\in\Omega (g(n))\iff \exists c>0,\exists n_0,\forall n>n_0(f(n)\ge c \cdot g(n))$$

$f(n)$ è $\Omega$ di $g(n)$ se e solo se esistono due costanti $c > 0$, $n_0$ tali che per ogni $n > n_0$ abbiamo $f(n) \ge cg(n)$. 

![[Pasted image 20220329175549.png|300]]

> Si scrive $f(n) = Ω(g(n))$ se esistono delle costanti positive $n_0$ e $c$ tali che, a destra di $n_0$, il valore di $f(n)$ e sempre uguale o maggiore di $c\cdot g(n)$.


#### Notazione $o$

Utilizziamo la notazione o per denotare un limite superiore che **non** é **asintoticamente stretto**.


Nella notazione $o$ la funzione $f(n)$ diventa insignificante rispetto a $g(n)$ quando n tende all’infinito

$$\lim_{x\to \infty}\frac{f(n)}{g(n)}=0$$
