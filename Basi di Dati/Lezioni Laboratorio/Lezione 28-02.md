# Progettare una base di dati
Significa **definirne** la **struttura**, le **caratteristiche** e il **contenuto** della base di dati.

### Ciclo vita dei sistemi informativi
1. Studio di fattibilita' 
2. Raccolta e analisi dei requisiti
3. Progettazione
	Ha 2 aspetti da considerare:
	- Progettazione dei dati, ovvero i requisiti statici(dati)
	- Progettazione delle applicazioni, ovvero i requisiti dinamici(attivita' sulle informazioni)
4. Implementazione e popolazione
5. Validazione e collaudo
6. Funzionamento

Noi ci occuperamo principalmente dei punti 2 e 3.

## Metodologia di progettazione
Consiste nel definire alcuni passaggi per :
- Decomporre l'attivita' del progetto in modo atomico, quinid in fasi successive e indipendenti
- Definire le strategie da seguire in ogni fase e i criteri per le scelte delle alternative 
- Definire i modelli di riferimento per la descrizione dei dati di I/O delle varie fasi

## Fasi della progettazione
La progettazione si distigue in 3 fasi:
### Progettazione concettuale
In questa fase di definisce cosa si vuole rapprestenare con una base di dati.

Permette di **rappresentare specifiche** informali tramite una descrizione formale indipendente dai criteri di rappresentazione usati nel DBMS.

Deve fornire un alto livello di astrazione e non richiede nessun dettaglio implementativo.

Parte dai requisiti della base di dati, per realizzare uno **schema concettuale**(nel nostro caso un Entity Relationship) sfruttando un modello concettuale.

### Progettazione logica
Consiste nella **traduzione** di uno schema **concettuale** secondo il modello di **rappresentazione** usato nel **DBMS**.

I modelli logici prodotti sono molto rigidi.

Questo schema logico e' indipendente dai dettagli fisici, ma richiede schelte basate sull'ottimizzazione delle operazioni.

E' possibile valutare la qualita' dello schema mediante tecniche formali(nel caso del corso la normalizzazione)

In questa fase,**partendo** dallo schema **concettuale** e  utilizzando un modello logico(nel nostro caso relazionale), si **produce** uno **schema logico**.
### Progettazione fisica
In questa fase,partendo dallo schema logico e utilizzando un modello fisico, si produce uno schema fisico.

Ogni schema puo' essere prodotto da una persona diversa per incrementarne la leggibilita'.

## Modello dei dati
E' un'**insieme** di **costrutti** che sono utilizzati per **organizzare** i **dati** di interesse e per **descriverne** la **dinamica**.

Un componente fondamentale sono i meccanismi di strutturazione (o costruttori di tipo).


### Modelli concettuali
I modelli concettuali servono per ragionare sulla realtà di interesse, indipendentemente dagli aspetti
realizzativi.

Permettono di rappresentare le classi di oggetti di interesse e le loro correlazioni.

Prevedono efficaci rappresentazioni grafiche utili anche per documentazione e comunicazione.

#### Modelli Entity Relationship
E' il modello concettuale piu' diffuso.

Fornisce costrutti per descrivere le specifiche sulla struttura dei dati in modo semplice e comprensibile attraverso l'utilizzo di un formalismo grafico.

Permette di produrre un modello in maniera del tutto indipendente dal modello logico dei dati, per poter scegliere quello piu' adeguato successivamente.

##### Costrutti principali
###### Entita'
E' un **costrutto** che **rapprenenta** **classi** di **oggetti** del mondo reale che hanno **proprietà comuni** ed **esistenza autonoma**.

Un’occorrenza di un’entità è un oggetto della classe che l’entità rappresenta.

###### Relazioni/Associazioni
Rappresentano un legame logico tra due o più entità.

Una occorrenza di una relazione è un'ennupla costituita da occorrenze di entità (una per ciascuna entità coinvolta).

Non vi possono essere ennuple identiche

In una relazione ricorsiva, un’entità è in relazione con se stessa.Se la relazione non è simmetrica, occorre definire i due ruoli dell’entità.

###### Attributi
Un attributo descrive una proprietà elementare di un’entità o di una relazione.

Ogni attributo è caratterizzato dal dominio, l’insieme dei valori ammissibili per l’attributo.


