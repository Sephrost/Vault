Con riducibilita' intendiamo la possibilita' di ridurre un problema $A$ ad un problema $B$ mostrando che esiste una funzione computabile che converte le istanze del primo problema ad instanze del secondo.

> Se tale conversione e' possibile diciamo che esiste una *riduzione*.

### Funzione computabili
Una funzione $f:\Sigma^*\to \Sigma^*$ e' una **funzione computabile** se una *TM* $M$ termina con $f(w)$ per ogni input $w$.

### Definizione
Un linguaggio $A$ e' **riducibile** ad un lignuaggio $B$, ovvero $A\le_m B$ se esiste una funzione computabile $f:\Sigma^*\to \Sigma^*$ che per ogni input $w$ 
$$w\in A \iff f(w)\in B$$

![[Pasted image 20221124113905.png]]

La riducibilita' ci permette di convertire il problema dell'appartenenza ad un linguaggio $A$ all'appatenenza a $B$.

> Per verificare che $w\in A$, usiamo la riduzione per mappare $w$ a $f(w)$ e verificare se $f(w)\in B$. 

#### Decidibilita' attraverso la riduzione
Se $A\le_m B$ e $B$ e' decidibile, allora $A$ e' decidibile.

Sia $M$ un decisore per $B$ e $f$ una rifuzione da $A$ ad $B$,
Allora esiste un decisore $N$ per $A$:
Per input $w$:
1. Computa $f(w)$ 
2. Esegue $M$ con $f(w)$ e restituice cosa restituisce $M$

Se $w\in A$, allora $f(w)\in B$ poiche' la riduzione e' valida.

