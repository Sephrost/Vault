Nello sviluppo iterativo non si implementano tutti i requisiti in una sola volta: nell’iterazione 1 questi **requisiti** sono dei **sottoinsiemi** dei requisiti o dei casi d’uso completi.

> Un caso d'uso o una caratteristica sono spesso troppo complessi per poter essere completati in una sola breve iterazione.
> Pertanto le varie parti o scenari possono essere distribuiti su diverse iterazioni.

## Ideazione
> Puó durare anche una sola settimana.

L’ideazione è un **passo breve** verso l’elaborazione. 
Essa determina la **fattibilità**, il **rischio** e la **portata** di base, al fine di stabilire se il progetto merita un’indagine più seria.

Alcune attività ed elaborati probabili dell’ideazione sono i seguenti:
- Un breve workshop dei requisiti.
- Assegnazione dei nomi per la maggior parte degli attori, degli obiettivi e dei casi d’uso. 
- Scrittura in formato breve della maggior parte dei casi d’uso; 
	- il 10-20% dei casi d’uso è scritto in formato dettagliato.
- Identificazione della maggior parte dei requisiti di qualità più influenti e rischiosi. 
- Scrittura della prima versione dei documenti di Visione e Specifiche Supplementari. 
- Lista dei rischi.
- Prototipi tecnici proof-of-concept e altre indagini per esaminare la fattibilità tecnica dei requisiti speciali.
- Prototipi orientati all’interfaccia utente per chiarire la visione dei requisiti funzionali. 
- Raccomandazioni su quali componenti acquistare/costruire/riusare, da raffinare durante l’elaborazione. 
- Proposta dell’architettura di alto livello e dei componenti candidati. 
	- Non si tratta di una descrizione dettagliata dell’architettura
	- è una breve speculazione da utilizzare come punto di partenza dell’indagine nell’elaborazione.
- Piano per la prima iterazione.
- Elenco di strumenti candidati.

## Elaborazione
L’**elaborazione** è la **serie iniziale** di **iterazioni** durante le quali il team esegue un’**indagine** seria, **implementa** il nucleo dell’**architettura**, **chiarisce** la maggior parte dei **requisiti** e affronta le problematiche di alto rischio.

> É spesso costituita da due o più iterazioni, ciasucna delle quali dovrebbe durare dalle due alle 6 settimane. 
> Ciascuna di queste iterazione é timeboxed.

Durante questa fase il codice e la progettazione prodotti sono parti di qualità produzione del sistema finale.

### Best practice per l'elaborazione
- Eseguire iterazioni guidate dal rischio, brevi e timeboxed. 
- Iniziare presto la programmazione. 
- Progettare, implementare e testare, in modo adattivo, le parti principali e più rischiose dell’architettura.
- Effettuare test presto, spesso e in modo realistico.
- Adattare in base al feedback proveniente da test, utenti e sviluppatori. 
- Scrivere la maggior parte dei casi d’uso e degli altri requisiti nel dettaglio.

## Pianificazione dell'iterazione successiva
I requisiti e le iterazioni vanno organizzati in base a rischio, copertura e criticità. 
- **Rischio** 
	- comprende tanto la complessità tecnica quanto altri fattori, come l’incertezza dello sforzo o l’usabilità.
- **Copertura**
	- implica che le iterazioni iniziali prendano in considerazione tutte le parti principali del sistema, probabilmente con un’implementazione “in ampiezza e poco profonda” di molti componenti. 
- **Criticità** (*valore*)
	- si riferisce alle funzioni che il cliente considera di elevato valore di business.

> Questi criteri sono utilizzati per collocare il lavoro nelle iterazioni

A ciascun caso d'uso viene assegnato un voto per l'imprementazione, e nelle prime iterazioni verranno implementati gli scenari con votazione elevata.

La classifica viene stilata e aggiornata prima di ogni iterazione. 