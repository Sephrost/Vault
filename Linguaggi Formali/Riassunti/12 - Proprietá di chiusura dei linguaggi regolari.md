### Proprietá di chiusura dei linguaggi regolari

#### Unione e concatenazione

I linguaggi liberi sono chiusi per contatenazione

###### Dimostrazione 
Dati due linguaggi liberi $L_1$ ed $L_2$, esistono sicuramente due grammatiche libere t.c. $L_1=L(G_1)$ e $L_2=L(G_2)$.

Possiamo assumere che le grammatiche **non** abbiano **variabili** in **comune** ($V_1\cap V_2=0$) e che il **simbolo iniziale** non appartenga alle variabili di **nessuna** dei due grammatiche($S\notin V_1\cup V_2$), poiché e sempre possibile scegliere **nuovi nomi** per le grammatiche, o quantomeno rinominarle.

Quindi la grammatica 

$(V_1\cup V_2,T_1\cup T_2,P_1 \cup P_2\cup \{S\to S_1|S_2\},S)$

genera $L_1\cup L_2$, mentre la grammatica

$(V_1\cup V_2,T_1\cup T_2,P_1 \cup P_2\cup \{S\to S_1S_2\},S)$

genera $L_1L_2$.

#### Intersezione

I linguaggi liberi **non** sono chiusi per intersezione.

###### Dimostrazione 
I linguaggi 
- $L_1=\{a^nb^nc^m|m,n\ge 0\}$
- $L_2=\{a^mb^nc^n|m,n\ge 0\}$

sono liberi. Se i linguaggi liberi fossero chiusi per intersezione, allora anche il linguaggio

$L_1\cap L_2=\{a^nb^nc^n|n\ge 0\}$

sarebbe libero, ma abbiamo dimostrato che non lo é.

##### Intersezione con un linguaggio regolare

Se $L$ é un linguaggio libero ed $R$ é un linguaggio regolare, allora $L\cap R$ é un linguaggio libero.

###### Dimostrazione

Se $L$ è un linguaggio libero allora esiste un PDA che accetta $L$ per stato finale.
Se $R$ è un linguaggio regolare allora esiste un DFA che accetta $R$.
Si può costruire quindi un PDA che accetta $L\cap R$ per stato finale costruendo il “prodotto” di $P$ ed $M$.

##### Complemento e differenza
I linguaggi liberi non sono chiusi per complemento e differenza

###### Dimostrazione 
I linguaggi liberi sono chiusi per unione. Se fossero chiusi anche per complemento, allora avremmo che

$L_1\cap L_2=\overline{\overline{L_1\cap L_2}=\overline{L_1}\cup \overline{L_2}}$

sarebbe sempre un linguaggio libero, contrariamente a quanto dimostrato in precedenza.

##### Inversione
Se $L$ é un linguaggio libero, allora $L^R$ é un linguaggio libero.
###### Dimostrazione 
