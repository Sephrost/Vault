## Automi a pila
Un' **automa a pila**(o **PDA**) e' una settupla del tipo $A=(Q,\Sigma,\Gamma,\delta,q_0,Z_0,F)$ dove
- $Q$ e' un **insieme** finito di **stati**
- $\Sigma$ e' l'alfabeto di **input**
- $\Gamma$ e' l'alfabeto della **pila**
- $\delta: Q\times(\Sigma\cup\{\epsilon\})\times\Gamma\to p(Q \times\Gamma^*)$
- $q_0\in Q$ e' lo **stato iniziale**
- $Z_0\in \Gamma$ e' il **simbolo iniziale** presente sulla pila, e quindi in terminatore
- $F\subset Q$e' l'insieme degli **stati finali**

Generalmente $\Sigma$ e $\Gamma$ sono distinte, poiché il terminatore $Z_0\in \Gamma$, anche se in moltio casi $\Sigma \subset \Gamma$.

##### Funzione di transizione

A differenza dei DFA, un'automa a pila potrebbe aver la necessitá di **leggere** il contenuto della **pila** per determianre il suo **comportamento**.

La funzione di transizione prende quindi in input la **tripla**:
- $Q$: lo stato in cui si trova l'automa
- $\Sigma \cup \{\epsilon\}$: un simbolo della stringa da riconoscere, oppure epsilon nel caso di una transizione spontanea
- $\Gamma$: un elemento della pila, che verrá rimosso dalla stessa

La funzione pone quindi in output la coppia:
- $Q$: lo stato in cui si troverá dopo il riconoscimento
- $\Gamma^*$: l'insieme degli elementi che verranno aggiunti alla pila
	- Notare che $\epsilon \in \Gamma^*$

###### Esempio
Un'esempio del riconoscimento delle stringhe $a^n b^n$ é il seguente

![[Pasted image 20220104154437.png]]

### Descrizioni istantanee
Per conoscere a **configurazione globale** di un PDA $P$ durante il processo di riconoscimento si usano le **descrizioni istantanee**, ovvero delle triple $(q,w,\alpha)$, dove:
- $q\in Q$ e' lo **stato** in cui si trova l'automa
- $w\in \Sigma$ e' ció che rimane da riconoscere  della **stringa** in input
- $\alpha \in \Gamma^*$ e' il **contenuto** della **pila** dalla cima al fondo

### Mosse di un'automa a pila
Dato un'automa a pila $P$, definiamo con la relazione binaria $\vdash_p$,che descrive la transizione da una descrizione instantanea ad un'altra, nella seguente maniera:

- $(q,aw,X\beta)\vdash_p(p,w,\alpha \beta)se(p\alpha)\in \delta(q,a,X)$
	- In questo caso la stringa da riconoscere non é vuota($aw$)

- $(q,w,X\beta)\vdash_p(p,w,\alpha \beta)se(p\alpha)\in \delta(q,\epsilon,X)$

Diciamo un PDA fa una mossa da una D.I. A ad una B se vale la relazione $A\vdash_p B$

###### Esempio

![[Pasted image 20220104164517.png]]

### Linguaggio accettato da un'automa a pila 
Dato un'automa a pila, il linguaggio
e' l'insieme delle stringhe per le quali, partendo dalla descrizione istantanea iniziale,l'automa puo' raggiungere in 0 o piu' **mosse** un suo stato finale, la **stringa** di input e' stata **consumata** completamente e il contenuto della **pila** e' **arbitrario** nel riconoscimento per stato finale, oppure **vuoto** nel riconoscimento per pila vuota.

Il Linguaggio accettato da $P$ per stato finale é 

$L(P)=\{w\in\Sigma^*|(q_0,w,Z_0)\vdash_P^*(q,\epsilon,\alpha),q\in F\}$

mentre il linguaggio accettato da $P$ per pila vuota é 

$N(P)=\{w\in \Sigma^*|(q_0,w,Z_0)\vdash^*_P(q,\epsilon,\epsilon)\}$
