#### SAT e' NP-completo
> Mostriamo che e' possibile costruire una riduzione di tempo polinomiale per ogni linguaggio a SAT.

Mostriamo innazitutto che sat e' un problema di tipi NP.

Una macchina non deterministica polinomiale puo' indovinare l'assegnamento di una formula $\phi$ e accetta se l'assegnamneto la soddisfa.

Sia quindi $N$ una *TM* non deterministica che decide un linguaggio $A$ in tempo $O(n^k)$, per qualche costante $k$.

Una **tableau** di $N$ su $w$ e' una tabella $n^k\times n^k$ dove le righe rappresentano le configurazioni del ramo della computazione di $N$ su input $w$, come in figura

![[Pasted image 20221121091519.png]]

> Assumiamo che ogni configurazione inizi con e finisca con il simbolo #, che funge da delimitatore.
> 
> Inoltre la prima righa rappresentera' la configurazione inizale di $N$ su $w$, ed ogni riga segue quella precedente secondo la funzione di transizione di $N$.

Essendo il tableau il risultato di una computazione di $N$, ogni ramo di computazione accettante corrisponde ad un tableau accettante.

> Il problema quindi si riduce dall'accettazione di $w$ su $N$ al determinare se esiste una tavola per cui $N$ accetta $w$.

Definiamo quindi una formula $\phi$, prodotta da una riduzione polinomiale $f$ da $A$ a $SAT$.

Ora definiamo come **cella** ognuna delle caselle della tabella $(n^k)^2$, che contiene un simbolo di $C = Q \cup \Gamma \cup \{\#\}$, e rappresentiamo il contenuto di ogni cella con una variabile di $\phi$. 

> Quindi per ogni $i$ e $j$ nel range $1-n^k$ e per ogni $s\in C$, abbiamo una variabile $x_{i,j,s}$.
> Inoltre $x_{i,j,s}$ assume valore $1$ se $cell[i,j]$ contiene un valore di $C$.

Per poter far corrispondere $\phi$ ad un tableau accettante di $N$ per $w$ , rappresentiamo la formula come una congiunzione logica di 4 parti: 
$$\phi_{cella}\land\phi_{start}\land\phi_{move}\land\phi_{accept}$$

Dobbiamo ora garantire la corrispondenza tra la formula e il tableau, e per far cio' ci assicuriamo che ogni cella rappresenti un assegnamento, assicurato tramite la formula $\phi_{cell}$:

$$\phi_{cell}=\bigwedge_{1\le i,j\le n^k}[(\bigvee_{s\in C}x_{i,j,s})\land(\bigwedge_{s,t\in C|s\ne t}(\overline{x_{i,j,s}}\lor \overline {x_{i,j,t}}))]$$
> Per esempio $\bigvee_{s\in C} x_{i,j,s}$ contiene $x_{i,j,s_1}\lor x_{i,j,s_2}\lor \dots \lor x_{i,j,s_t}$
> Inoltre se $cell[i,j]=s$ allora $x_{i,j,s}=1$ altrimenti $x_{i,j,s}=0$

La formula $\phi_{cell}$ contiene quindi un frammento per ogni cella del tableau. La prima parte di $\phi_{cell}$ dentro le parentesi vincola che **almeno una** delle variabili in una una cella sia vera,  mentre la seconda vincola che **non piu'** di una variabile e' **vera** per ogni cella.

> Letteralmente, per ogni cella del tableau,

La formula $\phi_{start}$ assicura che la prima riga del tableau e' la configurazione iniziale, controllando frammento per frammento:
$$\phi_{start}=x_{1,1,\#}\land x_{1,2,q_0}\land x_{1,3,w_1}\land\dots\land x_{1,n^k,\#}$$

La formula $\phi_{accept}$ assicura che **esiste** una **configurazione accettante** nel tableau:

$$\phi_{accept}=\bigvee_{1\le i,j\le n^k}x_{i,j,q_{accept}}$$

La formula $\phi_{move}$ assicura che per ogni riga del tableau corrisponde una configurazione che segue legalmente la riga precedente secondo le regole di $N$.

Per far cio' ci assicuriamo che ogni finestra $2\times 3$ ha solo **celle legali**, ovvero se non viola le azioni specificate dalla funzione di transizione di $N$. 

> La finestra ci serve per osservare il comportamento dell'esecuzione di $N$ 

Se la riga in cima al tableau e' la configurazione iniziale e ogni finestra del tableau e' legale, allora ogni riga del tableau e' una configurazione che segue legalmente la riga precedente.

> Per provare l'affermazione precedente osserviamo che se la riga superiore di una finestra non ha simboli di stato adiacenti e' la cella centrale di una finestra che non contiene simboli di stato adiacenti sulla riga superiore.
>
> Di conseguenza lo stesso simbolo si trovera' uguale nella stessa posizione ma sulla cella inferiore, poiche' non e' stato alterato dalla funzione di transizione di $N$.
>
> La presenza di un simbolo di stato nella riga superiore garantisce che la riga inferiore sia aggiornata costantemente secondo la funzione di transizione.
>
> Di conseguenza se la configurazione superiore e' una configurazione legale lo e' anche quella superiore

$\phi_{move}$ stabilisce che tutte finestre nel tableau devono essere legali., ovvero

$$\phi_{move}=\bigwedge_{1\le i\le n^k,1<j<n^k}(la\;finestra\;(i,j)-esima\;e'\;legale)$$
scrivibile anche come 

$$\bigvee_{a_1,\dots ,a_6\;e'\;una\;finestra\;legale}(x_{i,j-1,a_1}\land x_{i,j,a_2}\land x_{i,j+1,a_3}\land x_{i+1,j-1,a_4}\land x_{i+1,j,a_5}\land x_{x+1,j+1,a_6})$$

##### Stime della riduzione
Innazitutto stimiamo il numero di variabili di $\phi$:
Ogni tableau ha $n^k\times n^k$ celle, quindi $n^{2k}$, e ogni cella ha $l$ variabili associate ad essa, dove $l$ e' il numero di variabili di $C$, quindi il numero di variabili non dipende dall'input $n$ ma dalla *TM* $N$.

Di conseguanza il numero di variabili e' $O(n^{2k})$.