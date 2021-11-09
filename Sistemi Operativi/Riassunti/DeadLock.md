# DeadLock
E' un problema di sincronizzazione dipendente dalle specifiche esecuzioni dei vari processi.

Se processo,richiedente una risorsa, la trova occupata, entra in uno stato di attesa. Puó capitare che questa peró non cambi mai stato, poiché altri processi in attesa attendono la stessa risorsa. 

Si verifica il DeadLock se:
- Le risorse sono in mutua esclusione
	- Solo un processo alla volta puó usare una risorsa
- Le risorse sono in possesso e attesa:
	- Se detengono il possesso di alcune risorse e ne attendono altre
- La presenza di un'attesa circolare
	- Un processo attende una risorsa, occupata da un'altro che attende un'altra risorsa, e cosí via
- Assenza di prelazione(il SO non puo' sottrarre risorse per riassegnarle)

Basta che una delle condizioni sopra citate non si verifichí per evitare il deadlock.

E' un problema di sincronizzazione dipendente dalle specifiche esecuzioni dei vari processi.

## Grafi di assegnazione delle risorse
Per rappresentare piú precisamente il deadlock utilizziamo i **grafi di assegnazione delle risorse**.

Sono grafi della forma $G=<V,E>$, dove :
- $V$ é l'insieme dei **vertici**. A sua volta é partizionato in 2 tipi di nodi:
	- $P=\{P_1,P_2,...,P_n\}$ é l'insieme dei processi attivi
	- $R=\{R_1,R_2,...,R_m\}$ é l'insieme dei tipi di risorse presenti nel sistema
- $E$ é l'insieme degli archi:
	- un'arco da un processo ad una risorsa($P_i\to R_j$) indica una richiesta di una risorsa di tipo $R_j$ da parte del processo $P_i$ ed é definito **arco di richiesta**
	- un'arco da una richiesta ad una risorsa($R_i\to P_j$) indica l'assegnazione di una risorsa di tipo $R_i$ al processo $P_j$ ed é definito **arco di assegnazione**

Un gradi di assegnazione puó essere composto nella seguente maniera:	
-	$P=\{P_1,P_2,P_3,P_4\}$
-	$R=\{R_1,R_2\}$
-	$E=\{P_1\to R_1,R_1\to P_2,P_2\to R_2,R_2\to P_3,R_2\to P_4\}$
e rappresentato nella seguente:

![[Pasted image 20211108165721.png]]

### Utilizzo dei grafi per la localizzazione del deadlock
Possiamo definire delle regole generali per l'individuazione del deadlock a partire dai grafi:
- Se **non** sono presenti **cicli** non é neanche presente il deadlock
- La presenza di un **ciclo** é una condizione **necessaria ma non sufficiente** al verificarsi del deadlock:
	- Se nel ciclo sono presenti solo **risorse** aventi una **sola istanza** allora é sicuramente presente il deadlock
	- Se nel ciclo sono presenti piú istanze di ogni ris