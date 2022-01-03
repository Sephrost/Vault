#### Mappatura dei file 
Per svolgere operazioen dei file bisogna vedere ai dati usando una tabella delle pagine , caricando il file un pezzo per volta nelle celle della ram e facendola puntare alla tabella di riferimento.
#### Mappatura dei device
Si utilizzano i meccanismi di gestione della memoria per gestire componenti fisici.
### Assegnazione della ram ai processi kernel 
#### Sistema Buddy(gemellare)
La memoria disponibile viene vista come un'unico **segmento continuo**, all'inizio, con una dimensioen fissata. 

Ad ogni processo creato la memoria viene divisa in **2 buddy** di pari dimensioni, fino a quando la memoria non diventa troppo piccola per l'allocazione del processo.

Se un buddy si libera viene rifuso al suo corrispettivo.

Questa metodologia non e' pero' efficente, poiche' si possono allocare processi con dimensione piu' piccola di un buddy.

#### Cache di slab
Interpetando la ram come una array di descrittori di tipo uniforme liberi.

Quando bisogna allocare un processo si alloca nell'array i descrittori relativi al processo.

Quando la slub viene occupata completamente, alla prossima allocazione ne viene creata un'altra.

L'insieme delle slub che contengono elemente nello stesso genere viene chiamata **cache**.

Se tutti gli elementi all'interno di una slub si liberano la memoria viene riliasciata, riducendo la frammentazione interna.

## File System
Il sistema operativo contiene un **file control block** che contiene i metadati sul file 
Si dicidono in 
1. Alfanumerici
	- Sono costtuiti da seguenze di caratteri(txr,src) 
2. Binari
	- Sono costituiti da sequenze di bytecode(fiel oggetto)

### File system logico 
e' il livello piu' astratto 
#### Creazione
Comporta la ricerca dello spazio disco nel quale verranno iseriti i dati, assime al suo descrittore ed inizializzarlo con i suoi metadati
#### Lettura
Bisogna assicurarci che si possa accedere al file ed identificarne la posizione e quando si accede si aggiornano i metadati(Last access)
##### Scrittura
Stessa cosa della lettura
##### Cancellazione
Viene liberata della memoria, si aggiorna la struttura del file system
##### Troncamento
Si taglia una parte dei dati presenti nel file 
#### Riposizionamento
Riguarda un puntatore, che viene cambiato di posizione 

