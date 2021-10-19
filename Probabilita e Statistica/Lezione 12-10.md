# Indipendenza
Due eventi A e B, appartenenti ad $\omega$, si dicono indipendenti se vale:
- $P(A|B)=P(A)$

ovvero la probabilita' di A e la probabilita' di A condiziona da B hanno lo stesso valore, ovvero il condizionamento non ne altera la sua probabilita'.

## Osservazioni
- L'indipendenza e' **simmetrica**
	 quindi $P(A|B)=P(A)$ e' uguale a scrivere $\frac{P(A\cap B)}{P(B)}=P(A)$ e quindi $P(A\cap B)=P(A)P(B)$
-  Usando **Bayes** sulla definizione, possiamo riscriverla come $\frac{P(B|A)P(A)}{P(B)}$ e quindi $P(B|A)=P(B)$, quindi $P(A)=P(B)$.
-  Dati A e B con $P\cap B=0$ ma con $P(A)\ge 0$ e $P(B)\ge 0$ non sono mai indipendenti poiche' $P(A\cap B)=0$ e $P(A)P(B)\ge0$
