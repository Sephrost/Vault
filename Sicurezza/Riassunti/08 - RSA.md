RSA è un **cifrario asimmetrico a blocchi** (di dimensione M con M < n) basato su due chiavi $KA^-$ (privata) e $KA^+$ (pubblica). 

Abbiamo poi un numero $n$ detto **modulo RSA** molto grande (si parla di cento cifre decimali),generato dalla moltiplicazione di due numeri primi, $p$ e $q$. 

> Tipicamente $n$ è di **1024 bit** pertanto $p$ e $q$ sono di 512 bit ciascuno (capiremo meglio in seguito il perché di questi numeri).
>
> $n$ **non é primimo**, ma é composto da primi.

La sicurezza di RSA sta nella difficolta di fattorizzare un numero: essendo $n$ di $k$ cifre sará necessario effettuare $2^{k/2}$ divisioni, rendendo il problema non polinomiale(**NP**).
## Generazione di chiavi
Per generare e chiavi si effettuano i seguenti passaggi:
- si scelgono $p$ e $q$ primi
- si calcola il modulo $n=p\times q$
- si genera un numero $e<(p-1)(q-1)$ tale per cui $MCD(e,(p-1)(q-1))=1$
- si calcola $d$, ovvero l'inverso moltiplicativo in aritmetica modulare di $e$
	- $d=e^{-1}\mod(p-1)(q-1)$
- Si ottengono cosí la chiave pubblica $K^+=<e,n>$ e quella privata $K^-=<d,n>$

> Per semplicitá ci si riferisce a $e$ come chiave pubblica e $d$ come chiave privata
## Cifratura
La cifratura é molto semplica: si calcola l'esponente modulare $m^e\mod n$ per ottenere il messaggio cifrato $c$
## Decrittazione
La decrittazione é altrettanto semplice: si calcola l'esponente modulare $c^d\mod n$ per ottenere il messaggio in chiaro $m$
## Correttezza di RSA
Se cifrando $m$ otteniamo $c$, allora decifrando $c$ dovremmo ottenere $m$:
$$C(m)=c\to D(c)=m$$
ovvero
$$c=m^e\mod n\to m=c^d\mod n$$
ovvero 
$$m=(m^e\mod n)^e\mod n$$
Dobbiamo quindi dimostrare che 
$$m\equiv m^{ed}(\mod n)$$
