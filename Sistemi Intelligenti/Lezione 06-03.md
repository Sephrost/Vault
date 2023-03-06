## Ambiente statico e Dinamico
> Prenderemo in considerazione solo ambienti statici

Un'ambiente statico é un ambiente nel quale lap ercezione dell'ambiente di un agente non cambia senza che abbia compiuto un'azione.

Sono tipici dei sistemi multiagente. 
L'ambiente é deterministico, ovvero ad ogni azione si produce solo un successore.

## Strutture dati per la risoluzione di un problema
- Alberi di ricerca
- Grafi di ricerca


Un'algoritmo di ricerca é un'algoritmo che prende un problema in input e ritorna una soluzione, oppure qualcosa che ne indichi il fallimento.

Questi algoritmi si appoggiano a delelstrutture dati, quali:
- Alberi di ricerca
- Grafi di ricerca

Ogni nodo di queste strutture corrisponde a uno stato e ogni arco ad un'azione.

![[Pasted image 20230306121608.png]]

dove 
- IS-EMPTY(frontier), restituisce vero se non ci sono nodi nella frontiera
- POP(frontier) rimuove il nodo della frontiera in cima alla coda
- 

### Misurare le performance della cricera
Per misuare le performance di un'agoritmo di ricerca utilizziamo i seguenti criteri:
- **Completezza**
	- Se é in grado di trovare una soluzione se esiste
- **Ottimalitá**
	- L'algoritmo é sempre in grado di trovare una soluzione di costo minimo
- **Complessitá temporale**
	- L'algoritmo trova la soluzione nel minor tempo possibile
- **Complessitá spaziale**
	- L'algoritmo impiega la minore quantitá di memoria possibile

## Strategie di ricerca cieca
Una strategia di ricerca cieca implica che l'unica informazione fornita é la descizione del problema
#### Ricerca in Ampiezza - BFS
![[Pasted image 20230306123348.png]]

> Richiedo l'utilizzo di molta memoria.

La ricerca in apiezza trova sempre la soluzione cl numero minimo di pass irichiesti, poiché quando genera i nodi di profonditá $d$, genera anche quelli di profonditá $d-1$, quindi se uno di questi é una soluzione, la trova,

Questo significa che la BFS é ottima solo se tutte le azioni hanno lo stesso costo.

#### Complessitá della BFS
Consideriamo un branching factor di $b$.

Questo significa che la ridice genera $b$ nodi, e ognuno di questi produce altri $b$ successori, generando quidni $b^2$ nodi al secondo livello, e $b^3$ nodi al terzo livello, e cosí via.

supponendo quidni che l'albero abbia profonditá $d$, la complessitá temporale é quidni $O(b^d)$.
Ma poiché i nodi non vengono rimssi dalla memoria ha la stessa complessitá spaziale.

