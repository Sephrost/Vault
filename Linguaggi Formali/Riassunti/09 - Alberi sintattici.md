## Alberi sintattici
Data una grammatica $G=(V,T,P,S)$, gli alberi sintattici di $G$ sono alberi con le seguenti caratteristiche:
- Ogni nodo interno diverso da una foglia e' etichettato con $V$
- Ogni foglia e' etichettata con $V$,con $T$(terminale) o con $\epsilon$
- Se una foglia e' etichettata da $\epsilon$ ,e' l'unico figlio del suo parent
- Se un nodo e' etichettato con $A$, i suoi figli sono definiti con una produzione del tipo $A\to X_1X_2X_3...X_n$

Il **prodotto** di un'albero sintattico é la **stringa** ottenuta **concatenando** da sinistra verso destra le etichette di **tutte** le **foglie** dell'albero

###### Esempio

![[Pasted image 20220104120602.png]]

### Grammatiche ambigue
Una grammatica é **ambigua** se ammette **piú alberi** sintattici distinti con lo **stesso prodotto**.

Basta trovare due alberi sintattici distinti con lo stesso prodotto per dire che una grammatica ambigua, trovare due derivazioni distinte che generano la stessa stringa **non** é sufficiente.

###### Esempio 
![[Pasted image 20220104121019.png]]
Entrambi questi alberi rappresentano l'espressione $1+2\times 3$

#### Derivazioni canoniche
Una derivazione $X\Rightarrow^* \alpha$ si dice **derivazione a sinistra** se ad ogni passo viene riscritta la **variabile** che si trova a **sinistra**.

Usiamo $\Rightarrow_{lm}$ e $\Rightarrow_{lm}^*$ come simboli per la derivazione sinistra, e scularmente utilizziamo $\Rightarrow_{rm}$ e $\Rightarrow_{rm}^*$ per la derivazione destra.

Se esistono **due** derivazioni canoniche **distinte** dello **stesso tipo** nella grammatica $G$ per derivare la stessa stringa, allora la grammatica é **ambigua**. 

###### Esempio

![[Pasted image 20220104122344.png]]


## Eliminazione dell'ambiguita'
Eliminare l'ambiguita' di una grammatica significa ottenerne una **equivalente** non ambigua. Attraverso questo la grammatica solitamente si complica.

La strategia da utilizzare é **stratificare** le **espressioni**, ovvero anziché mettere tutte le produzioni nella stessa categoria, le **divido** in diverse **espressioni**,**termini** e **fattori**.

###### Esempio

Per disambiguare la grammatica $G=(\{E\},\{[0-9],+,*,(,)\},\{E\to [0-9]|E+E|E*E|(E)\},E)$

si puó stratificare la grammatica nella seguente maniera:

$G=(\{E,T,F\},\{[0-9],+,*,(,)\},P,E)$

dove P é l'insieme delle produzioni:
$E\to T| E+T$
$T\to F| T*F$
$F\to 0|..|9|(E)$
