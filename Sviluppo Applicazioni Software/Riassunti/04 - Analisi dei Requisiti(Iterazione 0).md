L’**ideazione** è il **breve passo iniziale** che permette di **definire** la **visione del progetto** e di ottenere una stima (approssimativa e non affidabile) dell’ordine di grandezza dei costi e dei tempi di sviluppo.

Questa é considerata come un'"**iterazione zero**".

> Lo scopo della fase di ideazione **non** è quello di definire tutti i requisiti, né di generare una stima o un piano di progetto affidabili.
> NON SI DEFINISCONO TUTTI I REQUISITI: si iniziano la programmazione di qualità produzione e il test molto tempo prima che la maggior parte dei requisiti siano stati analizzati o specificati
> 
> La maggior parte dell’analisi dei requisiti avviene quindi durante la fase di elaborazione.

Lo scopo dell’ideazione è stabilire una visione iniziale comune per gli obiettivi del progetto, stabilire se questo è fattibile e decidere se vale la pena di effettuare alcune indagini serie nell’elaborazione. 

### Elaborati di UP

Elaborato | Commento
--|--
Modello dei Casi d’Uso.| Un insieme di **scenari tipici** dell’utilizzo di un sistema. Usato principalmente per i requisiti funzionali (comportamento)
Specifiche Supplementari. |Essenzialmente tutto ciò che non rientra nei casi d’uso. Questo elaborato è principalmente per tutti i requisiti non funzionali, come prestazioni o licenze. È anche il posto per registrare delle caratteristiche funzionali non espresse (o non esprimibili) come casi d’uso.
Glossario.| Definisce i termini significativi. Esso ha anche il ruolo di dizionario dei dati, che registra i requisiti relativi ai dati, come regole di validazione, valori accettabili e così via. 
Visione. |Riassume i requisiti ad alto livello che sono dettagliati nel Modello dei Casi d’Uso e nelle Specifiche Supplementari, nonché lo studio economico per il progetto. Un documento sintetico (una sorta di “executive summary”) per apprendere rapidamente le idee principali del progetto.
Regole di Business. |Le Regole di Business (chiamate anche Regole di Dominio) descrivono di solito i requisiti o le politiche che trascendono un unico progetto software


### Requisiti
Un **requisito** è una **capacità** o una condizione a cui il sistema, e più in generale il progetto, deve **essere conforme**.

Ci sono due tipi principali di requisiti:
- I **requisiti funzionali** (**comportamentali**) 
	- descrivono il comportamento del sistema, in termini di funzionalità fornite ai suoi utenti
	- Possono essere espressi come casi d'uso
	-  comprendono anche gli aspetti relativi alle informazioni che il sistema deve gestire
- I **requisiti non funzionali** (**tutti gli altri** ) 
	- non riguardano le specifiche funzioni del sistema, ma sono relativi a proprietà del sistema nel suo complesso

UP promuove un insieme di **best practice**, una delle quali è **gestire i requisiti**, che indica un approccio **sistematico** per **trovare**, **documentare**, **organizzare** e **tracciare** i **requisiti** che cambiano di un sistema.

UP incoraggia un’acquisizione dei requisiti abile, attraverso tecniche quali scrivere i casi d’uso con i clienti, workshop dei requisiti a cui partecipano sia sviluppatori che clienti, e altri per sollecitare il feedback.

#### Tipi di requisiti
- Funzionale
- **Usabilità**. 
	- Riguarda aspetti legati alla facilità d’uso del sistema, documentazione e aiuto per l’utente. 
- **Affidabilità**. 
	- Riguarda caratteristiche come la disponibilità , la capacità del sistema di tollerare guasti o di poter essere ripristinato a seguito di fallimenti. 
- **Prestazioni**. 
	- Riguarda caratteristiche come tempi di risposta, throughput, capacità e uso delle risorse. 
- **Sicurezza**. 
	- Riguarda la capacità del sistema di resistere ad usi non autorizzati, ma al tempo stesso di poter essere utilizzato dai suoi utenti legittimi 
- **Sostenibilità**.
	- È l’abilità del sistema software di essere facilmente modificabile per consentire miglioramenti e riparazioni

