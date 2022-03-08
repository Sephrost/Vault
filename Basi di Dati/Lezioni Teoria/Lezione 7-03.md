##### Proprieta' di una superchiave

Se sk e' una superchiave, qualsiasi insieme che la contiene e' anche una superchiave.

Qualsiasi relazione teorica di Cod contiene almeno una chiave candidata, al massimo anche lo schema intero della relazione.

#### Chiave principale/Primary Key
La chiave principale $pk \subseteq A$ e' una chiave scelta tra le possibili chiave candidate, in base alla significativita' nel contesto.

Ci puo' essere una sola chiave principale.

Tutti gli attributi della chiave principale devono essere non nulli.

Si rappresenta nel modello di COD sottolineando gli attributi che lo compongono.

###### Correttezza di una relazione 

Un'istanza di una relazione e' corretta se ogni tupla appartenente all'istanza e' compatibile con lo schema e sono soddisfatti tutti i vincoli locali.

#### Schema di una base di dati
Uno schema di una base di dati e' un'insieme di schemi di relazione tutti con nome 
$$S=\{R_1,R_1,\dots,R_n\}$$
con le seguenti proprieta' :
- I nomi devono essere distinti, in quanto non ci possono essere relazioni con lo stesso nome
	- Possono avere nome diverso ma schema uguale
- Ad ogni schema si abbinano i rispettivi vincoli locali
- Ogni relazione $R_i$ esibisce una chiave principale


#### Vincoli globali 

Così come è possibile definire dei vincoli locali (intrarelazionali) su ogni relazione R è altresì possibile definire vincoli globali interrelazionali su uno schema di basi di dati S.

Il vincolo globali si verifica nello schema di basi di dati, convolgendo 2 o piu' relazioni.

Il più importante è il vincolo di integrità referenziale.

##### Vincolo di integrità referenziale/ Foreign Key/Chiave esterna

Il vincolo di integrita' relazionale impone

$$\forall T_i(t_i\in r(R_s))\to \exist t_i( t_i\in r(R_h))\and (t_i[B]=t_j[PK])$$

Presa una tupla qualsiasi esista una tupla nelal relazione rh che ha gli stessi attributi in corripondenza delle chiave.

Se il vincolo non è rispettato la base dati non è corretta.

##### Condizione necessaria per il vincolo

E' necessario che i domini degli attributi in $PK$ siano compatibili con i domini degli attributi in $B$.

##### Stato/Istanza di una base di dati 
Dato uno schema di base di dati $S$, lo stato della base di dati e' un'insieme di coppie DB relazione/istanza, dove ogni istanza e' corretta e soddifa i vincoli globali.

## Algebra relazionale 
### Modello dell'interrogazione di Codd
Un' interrogazione su uba base di dotai e' una domanda che pongo al SO e la cui risposta si trova nella base di dati.

L'input di un'interrogazione e' la base di dati e l'output e' una relazione.

#### Operatori dell'algebra relazionale 
L'algebra relazionale e' costituita da operatori di base e operatori derivati
##### Operatori di base
- Selezione
- Proiezione
- Prodotto cartesiano 
- Unione 
- Differenza
- Ridenominazione
##### Operatori derivati
- Intersezione
- Join, nelle sue varie forme
- Quozione
#### Operatori algebrici
Gli operatori dell'algebra relazionale ricevono come argomenti relazioni e producono relazioni virtuali.

##### Operatore di selezione
Data una relazione r su uno schema A ,$\sigma_p(r(A))$ e' l'operatore di selzione dove p e' un predicato e r(A) e' l'argomento.

###### Sinstassi del predicato di selezione
Un predicato p e' un'espressione booleana di preficato atomici, che possono essere di due tipi distinti:
- $A_i $costante
- $A_i (confronto)A_j$
dove 
- $A_j$ e $A_i$ sono attributi dello schema A
- Il confornto e' un'operatore di confronto nell'insieme $\{=,\ne,>,\ge,<,\le\}$
