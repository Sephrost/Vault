Un **problema di soddisfacimento dei vincoli** é composto da:
- un'insieme $X$ di **variabili**
- un'insieme di **domini** $D$, uno per variabile
	- un dominio é un'insieme di valori assegnabbili ad una variabile
- un'insieme di **vincoli** $C$

Un'assegnamento é detto **consistente** se non viola i vincoli, e **completo** se ad ogni variabile é assegnato un valore.

Una soluzione per un CSP é un'assegnamento consistente e completo.

> Un assegnamento parziale lascia delle variabili non assegnate, e se questi soddisfano i vincoli allora si ottiene una **soluzione parziale**.

## Domini dei CSP
I Csp piú semplici involvono variabili con domini **finiti** e **discreti**. Peró questi possono essere infiniti, che non permettono di esprimere i valori come delle tuple. 

> I vincoli globali involvono un numero arbitrario di vincoli

## Consistenza
Un algoritmo di ricerca procede solo espandendo i nodi per visitare i successori, ma un algoritmo per CSP puó procedere in diverse maniere:
- generando assegnamenti e verificando se risolvono il problema
- propagando i vincoli per ridurre il numero di valori legali assegnabili ad una variabile(costraint propagation)

Quindi trattiamo ogni variabile come un nodo e ogni vincolo binario come un arco e cerchiamo di ridurre lo spazio di ricerca mantenendo l'assegnamento consistente.

### Node consistency
Una variabile, ovvero un nodo, é node-consistente se **tutti** i valori del suo **dominio** **soddisfano** i **vincoli unari**.

Possiamo eliminare tutti i vincoli unari in un CSP riducendo il dominio delle variabili con vincoli unari

### Arc consistency
Una variabile é arc-consistent se ogni valore del dominio soddisfa i vincoli binari.

> $X_i$ é consistente rispetto ad una variabile $X_j$ se per ogni valore del dominio $D_i$ esiste un valore del dominio $D_j$ che soddisfa i vincoli binari.

Un grafo é arc-consistent se ogni variabile é arc-consistente per ogni altra variabile.

#### AC-3
Per assicurare l'arc-consistenza si puó utilizzare l'algoritmo AC-3.

Questo utilizza una coda di archi, che li contiene tutti inizialmente, e si svuota man mano che l'algoritmo termina.

Quando un arco ($X_i,X_j$) viene estratto dalla coda si rende arc-consistente $X_i$ rispetto a $X_j$, e
- se $D_i$ rimane inalterato, proseguo
- Altrimenti aggiungo $(X_j,X_i)$ alla coda, poiché potrebbe essere possibile ridurre ulterormente $D_j$

Se un dominio non contiene piú valori, allora il problema non ha soluzioni consistenti.
![[Pasted image 20230629170315.png]]

### Path-consistency
Una coppia di variabili $(X_i,X_j)$ sono path consistenti con una terza $X_k$ se ogni assegmento della coppia soddisfa i vincoli binari su ($X_i,X_k$) e ($X_k,X_k$).

### Ricerca con backtracking per CSP
Talvolta la propagazione dei vincoli basta a risolver il problema, ma nel caso ci siano variabili con piú valori ammissibili bisonga cercare una soluzione.

Se usassimo una ricerca in profonditá non informata sarebbe comunque un problema non polinomiale.
![[Pasted image 20230629174857.png]]


#### Ricerca informata per CSP
Se notiamo l'algoritmo di ricerca con backtracking sceglie la variabile per cui generare un assegnamento in modo sequenzuale o casuale, ma nessuna delle due é ottimale.

Si puó migliorare la ricerca introducendo l'euristica **fail-first**(o minum-remaining -values), con la quale si sceglie una delle variabili col minor numero di valori alternativi consistenti per l'assegnamento corrente. Questo permette di potare l'albero di ricerca.

L'euristiva MRV non aiuta peró a scegliere la prima variabile da assegnare, quindi si puó utilizzare **l'euristica di grado**, la quale sceglie la variabile coinvolta in piú vincoli per cercare di ridurre il branching factor per le scelte future.

#### Forward Checking
AC-3 puó anche essere usata durante l'esecuzione della ricerca con backtracking: ogni volta che effettuiamo un'assegnamento per una variabile possiamo stabilire l'arc-consistency su tuttle le variabili collegate ad essa da vincoli binari