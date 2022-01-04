# Linguaggi Liberi
## Grammatica libera
Una grammatica libera e' una quadrupla del tipo $G=(V,T,P,S)$ dove :
- $V$ e' un'insieme finito di **variabili**(simboli **non** terminali)
- $T$ e' un alfabeto di **simboli terminali**
- $P$ e' un'insieme finito di produzioni(coppie Variablie -> Stringa di simboli, terminali o non) della forma $A\to \alpha$ in cui:
	- $A\in V$ e' detta testa della produzione
	- $\alpha \in(V\cup T)^{*}$ e' detto corpo della produzione
- $S\in V$ e' il simbolo inizale della gramamatica.
 
 Le grammatiche possono generare tutti i linguaggi regolari e non.
 ### Convenzione
 - Con le lettere **minuscole** indichiamo gli elementi di T, quindi i simboli **terminali**.
 - Con le lettere **maiuscole** indichiamo gli elementi di V, quindi le **variabili**.
 - Con $X,Y,Z,...$ indichiamo i simboli($\in V\cup T$)
 - Con $u,v,w,...$ denotiamo le stringhe di simboli($(V\cup T)^*$)
 - Con le lettere $u,v,w..$ indichiamo gli elementi di $T^{*}$

### Derivazioni

Data una grammatica $G$, definiamo una derivazione cosí come segue:

- scriviamo $\alpha A \beta \Rightarrow_G \alpha \gamma \beta$ se $A\to \gamma \in P$
	- Diciamo quindi che $\alpha \gamma \beta$ **deriva in un passo** da $\alpha A \beta$ in $G$
- Scriviamo $\Rightarrow_G^*$ per la chiusura riflessiva e transitiva di $\Rightarrow_G$, ovvero:
	- una variabile deriva se stessa in 0 o piú passi ($\alpha \Rightarrow^*_G \alpha$)
	- se $\alpha \Rightarrow_G \beta$ e $\beta \Rightarrow^*_G \gamma$, allora $\alpha \Rightarrow^*_G \gamma$

###### Esempio
Data la grammatica $G=(\{A\},\{0,1\},\{A\to \epsilon|0|1|0A0|1A1\},A)$, ecco alcune possibili derivazioni:
- $A\to \epsilon$
- $A\to 0$
- $A\to 1$
- $A\to 0A0\to 00$
- ...
###  Linguaggio generato da una grammatica

Dato una grammatica G, il linguaggio generato da esso e' denotato da L(G) ed e'e definito come 

$L(G)=\{w\in T^{*}|S\Rightarrow^{*}_{g}w\}$

###### Esempio
La grammatica $G$ dell'esempio precedente é 

$L(G)=\{w\in \{0,1\}^*|w=w^R\}$

Un linguaggio $L$ e' libero se esiste una grammatica libera che lo genera.

Le grammatiche possono generare tutti i linguaggi regolari, ma possono generare anche linguaggi non regolari, quindi i linguaggi liberi includono propriamente i linguaggi regolari.


 
 