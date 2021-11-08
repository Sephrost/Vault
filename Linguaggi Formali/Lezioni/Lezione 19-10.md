# Linguaggi Liberi
## Grammatica libera
Una grammatica libera e' una quadrupla del tipo G=(V,T,P,S) dove :
- V e' un'insieme finito di variabili
- T e' un alfabeto di simboli terminali
- P e' un'insieme finito di produzioni(coppie Variablie -> Stringa di simboli, terminali o non) della forma $A\to \alpha$ in cui:
	- $A\in V$ e' detta testa della produzione
	- $\alpha \in(V\cup T)^{*}$ e' detto corpo della produzione
- $S\in V$ e' il simbolo inizale della gramamatica.
 
 Le grammatiche possono generare tutti i linguaggi regolari e non.
 ### Convenzione
 - Con le lettere minuscole indichiamo gli elementi di T
 - Con le lettere maiuscole indichiamo gli elementi di V
 - Con X,Y,Z indichiamo i simboli($\in V\cup T$)
 - Con le lettere $u,v,w..$ indichiamo gli elementi di $T^{*}$

###  Linguaggio generato da una grammatica

Dato una grammatica G, il linguaggio generato da esso e' denotato da L(G) ed e'e definito come 
$L(G)=${$w\int T^{*}|S\to^{*}_{g}w$}

Un linguaggio $L$ e' libero se esiste una grammatica libera che lo genera.

 
 