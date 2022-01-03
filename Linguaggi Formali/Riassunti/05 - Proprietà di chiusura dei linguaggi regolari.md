## Chiusura dei linguaggi regolari
Dati due lunguaggi **regolari** $L$ ed $L'$ andiamo ad osservare sei i linguaggi regolari generati dalle seguenti **operazioni** sono anch'essi regolari
### Unione e concatenazione
Dati due linguaggi regolari $L_{1}$ e $L_{2}$, essi sono chiusi rispetto all'unione e alla concatenzazione.

###### Dimostrazione
Date due espressioni regolari $E_1$ ed $E_2$ generate rispettivamente dal linguaggio di $L_1$ ed $L_2$ ($L_1=L(E_1)$ e $L_2=L(E_2)$), l'espressione regolare $E_1+E_2$ genererá sicuramente $L_1\cup L_2$, cosí come $E_1 E_2$ genererá sicuramente $L_1 L_2$.

### Complemento
Dato un linguaggio regolare $L$, esso e' chiuso rispetto al complento poiche $\overline{L}=L(B)$.

###### Dimostrazione
Sé un linguaggio é regolare allora esiste sicuramente un DFA $A$ in grado di riconoscerlo.

Definiamo ora un'altro DFA $B=(Q,\Sigma,\delta,q_0,Q-F)$, dove la definizione di stato finale é invertita e quindi ogni stato non finale lo sará invece e viceversa.

Allora é ovvio che se una stringa $w$ appartiene al linguaggio di $A$ non apparterrá al linguaggio di $B$

$w\in L(A)\Leftrightarrow \hat{\delta}(q_0,w)\in F \Leftrightarrow w \notin L(B)$

### Intersezione
I linguaggi regolari sono chiusi rispetto all'intersezione

###### Dimostrazione 
Dati due linguaggi regolari $L_{1}$ e $L_{2}$, $L_{1}\cap L_{2}$ e' un linguaggio regolare, poiche' per le leggi di de morgan: $L_{1}\cap L_{2}=\overline{\overline{L_{1}\cap L_{2}}}=\overline{\overline{L_{1}}\cup\overline{L_{2}}}$ e i linguaggi regolari sono chiusi per intersezioni ed unione.
### Differenza
I linguaggi regolari sono chiusi per differenza

###### Dimostrazione
Dati due linguaggi regolari $L_{1}$ e $L_{2}$,  sono chiusi per la differenza poiche' $L_{1}-L_{2}=L_{1}\cup\overline{L_{2}}$ e questi sono chiusi per intersezione e complemento.
### Inversione
I linguaggi regolari sono chiusi per inversione.

###### Dimostrazione
Se $L$ é un linguaggio regolare allora deve esistere un'espressione regolare $E$ riconosciuta dal linguaggio.

Definiamo quindi l'espressione regolare $E^R$ per induzione sulla struttura di $E$

$0^R=0$
$\epsilon^R=\epsilon$
$a^R=a$
$(E_1+E_2)^R=E^R_1+E^R_2$
$(E_1E_2)=E_2^RE^R_1$
$(E^*)^R=(E^R)^*$

Allora $L(E^R)=L(E)^R$, quindi $L^R$ é regolare.