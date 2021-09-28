# Probabilita'
Disciplina della matematica che si occupa di fenomemi aleatori, ovvero esperimenti con esito **non prevedibile**.

In probabilita' usiamo gli **insiemi** per rappresentare gli esisiti degli esperimenti.

Esito|Cardinalita'
-|-
S={1,2}|Finito
S={1,2,3..}|Numerabile
S={$x\in ℝ t.c x \in [0,1]$}|Piu' che numerabile

## Partizione
Una partizione di un insieme S e' una partizione di insiemi finita o numerabile ($(Ai)^{+\inf}_{i=1}$)

- $Ai \cap Aj-0$ $\forall i \neq j$
- $U^{\inf}_{i-1}Ai =S$

Valgono inoltre le leggi di De Morgan.

## Modello Probabilistico
E' la struttura teorica che ci per formalizzare l'esperimento probabilistico.

E' composto da :
- Uno **spazio campionario** $\omega$, un insieme che contiene una rappresentazione di tutti i possibili esiti dell'esperimento
- La **misura di probabilita'** $P$, una funzione che associa ad ogni sottoinsieme un probabilita' in numeri reali

P e' una funzione del tipo $a$ e:
- P e' positiva ($\forall A\in P(\omega)\to P(A)\ge0$)
- $P(\omega)$ e' finita ($P(\omega)=1$), ovvero omega e' l'unico evento certo
- P e' additiva, ovvero dati A e B disgiunti, vale la relazione $P(A\cup B)=P(A)+P(B)$

### Legge uniforme discreta
Preso un sottoinsieme di $\omega$, P e' detta legge uniforme discreta se e' del tipo:

$P(A)=\frac{|A|}{|\omega|}$

ovvero ogni evento ha la stessa probabilita' di ogni evento appartenente allo spazio campionario, e questo esiste finito.




