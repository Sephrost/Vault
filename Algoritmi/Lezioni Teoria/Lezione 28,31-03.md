## Confine superiore alla complessita' di un problema
Con confine superiore intendiamo il tempo di calcolo nel caso peggiore necessario alla soluzione di un problema mediante algoritmo.

## confine inferiore alla complessita' di un problema
Con confine inferiore intendiamo il tempo do calcolo nel caso peggiore di tutti gli algoritmi che risolvono il problema(?) 

$$\forall T_i.T_i(n)\in \Omega(f(n))$$

## Confini banali
Derivano da informazioni ovvie, e non sono molto informativi.

- Dimensioni dei dati
- Eventi contabili

### Soluzioni ottime
Un algoritmo e' considerato ottimo se
- ha tempo algoritmo $O(f(n))$
- Il confine inferiore e' $\Omega(f(n))$

ovvero il confine superiore e' $O(f(n))$ e il suo confine inferiore $\Omega(f(n))$.

### Alberi di Decisione
Un albero rappresenta un algoritmo:
- i nodi interni(non le foglie) rappresentano decisioni(test)
- le foglie rappresentano le possibili uscite
- i rami rappresentano le singole esecuzioni

L’albero di decisione che minimizza l’altezza fornisce un confine inferiore al numero di decisioni necessarie nel caso peggiore.

Per comodita' noi useremo degli alberi binari nelle rappresentazioni.