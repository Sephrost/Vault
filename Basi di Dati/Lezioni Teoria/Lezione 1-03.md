# Introduzione
## Sistema informativo
**Componente**  di una organizzazione che **gestisce**  le **informazioni** di interesse.

### Sistema informatico 
**Porzione automatizzata** del sistema informativo.

Di solito non corrisponde mai al sistema informativo nella sua interezza

#### Gestione delle informazioni
Le attivita' della gestione delle informazioni **tipiche** sono:

- **Raccolta**, ovvero l'acquisizione delle informazioni
	- Tipicamente e' un'attivita' umana, ma puo' essere anche automatizzata
- **Archiviazione**, ovvero la conservazione automatizzata delle informazioni che devono essere conservate per lunghi periodi di tempo 
- **Elaborazione**, ovvero la trasformazione e la produzione delle informazioni
- **Distribuzione**, ovvero la comunicazione e dello scambio delle informazioni

### Informazioni e dati
I **dati** hanno senso solo nei sistemi informatici, in quanto sono il modo nel quale vengono **rappresentate** le **informazioni**.

Le **informazioni** sono invece dati che assumono **significato** in base al **contesto**, ovvero quando vengono interpretati e correlati tra di loro.

## Basi di Dati
### Definizione

Una base di dati e' un'**insieme** di **dati atomici** strutturati e persistenti, raggruppati in **insiemi omegenei** in relazione fra loro e organizzati con la minima ridondanza per essere utilizzati da applicazioni **diverse** in modo **sicuro** e controllato

#### Definizioni alternative
Insieme **organizzato** di dati utilizzato per il
supporto allo svolgimento delle attività di un ente
pubblico o privato.

In liguaggio tecnico intendiamo un'insieme di dati gestito da un **DBSM**(**D**ata**B**ase **M**anagement **S**ystem)

### Condivisione delle basi di dati
Ogni organizzazione è divisa in settori o comunque svolge diverse attività.

Ciascun settore ha un proprio sistema informativo (non necessariamente disgiunto).

La condivisione di una base di dati permette di effetturare **accessi concorrenti** da parte degli utenti, anche con permessi diversi, questo attraverso l'implementazione di **meccanismi** di **autorizzazione** e di **controllo** della **concorrenza**.

### Sviluppo integrato
1. Data la struttura organizzativa si inizia con un'**analisi** attenta e il più possibile esaustiva del **sistema informativo** nella sua interezza **indipendentemente** dalle **applicazioni**
2. Definiti lo **schema** e i **dati** e le **informazioni** di interesse dell'organizzazione si sviluppa l'applicazione
3. L'applicazione si **interfaccerà** con il DBMS  in base alle sue **esigenze**, in quando le modifiche da effettuare al programma saranno minime 

### Data Base Management System
E' un sistema centralizzato o distribuito ce consente di:
- **definire** gli **schemi** di basi di dati
- specificare i **vincoli di integrita'** dei dati
- **scegliere** le **strutture** dati per la **memorizzazione** e l'**accesso** ai dati
- **memorizzare**, **recuperare** e **modificare** i dati da utenti autorizzati
### Archetittura standart a tre liveli per DBMS
Nello schema **logico** risiede la **descrizione formale** dell'intero patrimonio informativo della realtà rappresentata.

Lo schema **interno** definisce come sono memorizzati **fisicamente** i dati all'interno del DBMS.

Lo schema **esterno** è la porzione di schema logico visibile alla singola applicazione

![[2022-02-28--1646041326_494x279_scrot.png]]

#### Indipendenza fisica 
I programmi applicativi o le attività interattive rimangono logicamente inalterate a fronte di eventuali **modifiche** delle **strutture di memorizzazione** dei dati o delle vie di accesso.

#### Indipendanza logica
I programmi applicativi o le attività interattive devono rimanere **logicamente inalterate** a fronte di **variazioni** dello schema logico che preservano le informazioni originarie.
### Modelli di dati
Un insieme di **meccanismi** di **astrazione** per definire una base di dati, con associato un insieme predefinito di operatori e di vincoli d’integrità.

### Modello logico
%%Da aggiungere %%
### Modelli concettuali 

Insiemi di astrazioni che servono per detrivere i concetti del mondo reale.

Sono utilizzati nelle prime fasi di progettazione.
