### Progettazione logica
L'obiettivo della progettazione concettuale e' tradurre lo schema concettuale in uno logico che rappresenti gli stessi dati in una maniera corretta ed efficiente.

Bisogna ristrutturare lo schema ER per 
- Semplificrae la tradutuzione, poiche' non tutti i costrutti ER possono essere tradotti
- Ottimizzare il progetto per massimizzare le prestazioni, poiche' la poca efficienta produce pessime prestazioni

#### Analisi delle prestazioni 
Le prestazioni non possono essere valute con precisione, in quanto non e' ancora possibile fare interorgazioni e test.

E' possibile stimare alcuni indicatori di parametri coinvolte nelle prestazioni del DBMS:
- spazio
	- In riferimento al numero di occorrenze previste
- Tempo
	- In riferimento al numero di occorrenze mi aspetto di coinvolgere durante un'operazione e quante sono visitate durante un'operazione
##### Tavola dei volumi
E' una stima nel numero di occorrenze per ogni associazione, in forma tabellare.

%%Aggiungere immagine%%

##### Tavola delle operazioni
E' una stima della frequenza delle operazioni per ogni giorno, anche questa in forma tabellare.

In quetsa tabella le operazioni di dividono in:
- Interattive
	- Quelle che avvengono a richiesta dell'utente e in tempo reale
	- Sono operazioni frequenti
- Batch
	- Sono operazioni programmate
	- Avvengono per mezzo di script in particolari momenti
##### Tavola degli accessi
A partire dall'entry point, vado a costruire una tabella dove indico il numero di accessi effettuate durante una data operazione.

Indico inoltre il tipo di accessi, che e' solitamente di lettura per le query.

#### Ristrutturazione dello schema ER
Si ristruttura lo schema ER per:
- Semplificare la traduzione 
- Ottimizzare le prestazioni
Lo schema ER ristrutturato non e' uno schema concettuale, poiche' e' pensato in un'ottica di progettazione logica e miglioramento delle prestazioni.

##### passaggi della ristrutturazione
###### Analisi delle ridondanze
Sono delle informazioni significativa e funzionale al progetto ma derivabile da altre informazioni.

In questa fase si decide se eliminare le ridondanze eventualmente presenti o mantenerle.

Le ridondanze possono essere:
- Attributi derivabili,da
	- altri attributi delle stessa entita'
	- attributi di altre entita'
	- conteggio delle occorrenze
- Relazioni derivabili
	- Dalla coposizioni di altre, ovvero dei cili di relazioni

Le ridondanze possono semplificare le interrogazioni, ma appesantiscono lgi aggiornamenti e occupano piu' spazio.

###### Eliminazione delle generalizzazioni
Il modello relazonale non puo' rappresentare direttamente dle generalizzazioni

Per eliminarel e generalizzazioni ci sono 3 possibilita'
1. Accorpo le entita' figlie nella generalizzazione
2. Accorpo le entita' genitorein quelle figlie
3. Sostituisco le generalizzazioni con delle relazioni