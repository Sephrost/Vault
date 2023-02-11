## Riducibilitá
Con riducibilita' intendiamo la possibilita' di ridurre un problema $A$ ad un problema $B$ mostrando che esiste una funzione computabile che converte le istanze del primo problema ad instanze del secondo.

> Se tale conversione e' possibile diciamo che esiste una *riduzione*.

Una riduzione é quindi in modo per convertire un problema in un'altro problema in modo che la soluzione del secondo possa risolvere il primo.

### Funzione computabili
Una funzione $f:\Sigma^*\to \Sigma^*$ e' una **funzione computabile** se una *TM* $M$ termina con $f(w)$ per ogni input $w$.

### Definizione
Un linguaggio $A$ é **riducibile** ad un lignuaggio $B$, ovvero $A\le_m B$ se esiste una funzione computabile $f:\Sigma^*\to \Sigma^*$ che per ogni input $w$ 
$$w\in A \iff f(w)\in B$$

![[Pasted image 20221124113905.png]]

La riducibilitá ci permette di convertire il problema dell'appartenenza ad un linguaggio $A$ all'appatenenza a $B$.

> Per verificare che $w\in A$, usiamo la riduzione per mappare $w$ a $f(w)$ e verificare se $f(w)\in B$. 

#### Decidibilitá attraverso la riduzione
Se $A\le_m B$ e $B$ é decidibile, allora $A$ é decidibile.

Sia $M$ un decisore per $B$ e $f$ una riduzione da $A$ ad $B$,
Allora esiste un decisore $N$ per $A$:
Per input $w$:
1. Computa $f(w)$ 
2. Esegue $M$ con $f(w)$ e restituice cosa restituisce $M$

Se $w\in A$, allora $f(w)\in B$ poiché $f$ é una riduzione da $A$ a $B$, di conseguenza $M$ accetta $f(w)$ quando $w\in A$. La riduzione é quindi valida.
