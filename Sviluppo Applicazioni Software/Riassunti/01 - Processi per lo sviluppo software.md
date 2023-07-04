### Caratteristiche di un software
Le principali caratteristiche di un prodotto software sono
- **mantenibilitá**: il software dovrebbe essere scritto in modo da evolversi in base alle richieste del cliente
- **fidatezza**: un software non dovrebbere creare danni fisici ed economici
- **efficienza**: il software non dovrebbe essere dispendioso in termini di risorse di sistema utilizzate
- **accettabilità**: il software deve essere utilizzabile da diversi dipi di utente

# Processi Software
> Un processo descrive chi fa cosa, dove e quando per raggiungere un obiettivo.

Un  processo per lo sviluppo del software, o **processo software**, descrive un approccio disciplinare alla **costruzione**, **rilascio** e **manutenzione** del codice.

### Attivitá di processo
Le quattro attivitá di processo fondamentali sono:
- **Specifiche del software**: vengono definite le funzionalitá e i vincoli del software
- **Sviluppo del software**: il software viene progettato e sviluppato
- **Convalida del software**: viene convalidato il software per garantire le richieste del cliente
- **Evoluzione del software**: viene modificato il software per soddisfare dei cambiamenti dei requisiti

> Queste sono comuni a tutti i processi software.

#### Specifiche del software
> É anche detta ingegneria dei requisiti.

É l'attivitá svolta per capire e definire i servizi richiesti dal sistema e i vincoli di operativitá e sviluppo.

E uno stadio particolarmente critico del processo software, poich´e gli errori in questa fase portano inevitabilmente a problemi successivi nella progettazione e implementazione del sistema.

É diviso in 3 sottofasi:
- Deduzione ed analisi dei requisiti
- Specifica dei requisiti
- Convalida dei requisiti, dove si controllano che i requisiti siano realistici e coerenti

### Sviluppo del software
É l'attivitá di conversione delle specifiche in un sistema eseguibile, da consegnare al cliente.

Le attivitá principali di questa fase sono:
- la progettazione dell'architettura
- la progettazione del database
- la progettazione dell'interfaccia
- la progettazione e scelta dei componenti, dove si si ricercano i componenti riutilizzabili o vengono progettati i nuovi componenti

### Convalida del software
É l'attivitá volta a confermare che un sistema é conforme alle specifiche e soddisfa le aspettiative del cliente.

Le attivitá principali sono: 
- Test dei componenti (o delle unitá), dove si testano i singoli componenti
- Test del sistema, si occupa di trovare gli errori causati da interazioni impreviste tra componenti e i problemi con le relative interfacce
- Test del cliente

### Evoluzione del software

> Il software puó essere modificato in qualunque momento.

I cambiamenti sono inevitabili nella maggior parte dei progetti, ed é essenziale quindi che sia possibile adeguare il software che si sta sviluppando.

Per ridurre quindi i costi di rielaborazione del progetto si possono usare due approcci correlati:
- Anticipare i cambiamenti, predicendo o anticipando le possibili variazioni, prima che richieda una rielaborazione(*refactoring*) del codice
- Tollerare i cambiamenti, permettendo che le modifiche siano facilmente apportabili

Invece per far fronte ai cambiamenti dei requisiti di sistema si possono usare due metodi:
- Prototipazione del sistema, il sistema (o una parte) viene sviluppato rapidamente per verificare i requisiti del cliente e la fattibilitá delle scelte di progettazione. 
- Consegna incrementale, vengono consegnati al cliente gli incrementi del sistema per essere commentati e provati.

## Processi a cascata

> É statto definito tra glia anni 60 e 70, ed é quindi il processo software piú vecchio tra quelli ancora utilizzati.

Il **processo** software con ciclo di vita **a cascata**, o *sequenziale*, è basato su uno svolgimento sequenziale delle diverse attività dello sviluppo del software.

### Timeline del processo

> Durante il processo a cascata, le seguenti attivitá vengono svolte in sequenza.

All’inizio di un progetto vengono definiti in dettaglio **tutti** i **requisiti**, o almeno la maggior parte di essi. Allo stesso tempo si cerca di definire un **piano temporale** dettagliato e "*affidabile*" delle **attivitá** da svolgere.

Poi si prosegue con la **modellazione** e viene quindi creato un progetto completo del software.
Solo a questo punto inizia la programmazione del sistema software, a cui seguiranno verifica e rilascio.

### Criticitá riscontrate

Il processo a cascata é un'ottimo approccio per i progetti le cui specifiche difficilmente variano nel tempo.

Ma poiché questo difficilmente accade, impiegare gran parte del tempo a disposizione della progettazione non é sempre una buona idea.

## Sviluppo incrementale

Lo **sviluppo incrementale** si basa sull’idea di sviluppare un'**implementazione iniziale**, esporla agli utenti e perfezionarla **attraverso** molte versioni, finché non si ottiene il sistema richiesto.

> Lo sviluppo incrementale in qualche forma é  l'approccio piú comune per sviluppare sistemi di applicazioni e prodotti software.

Puó essere: 
- **Plan Driven**
- **Agile**
- Una **combinazione** dei due

La gran flessibilitá che offre questo tipo di processo lo rende migliore di quello a casacata per i progetti i cui requisiti é probabile cambiano nel tempo, rendendo piú economico e semplice apportare modifiche.

%%Aggiungere Integrazione e configurazione%%

## Sviluppo Iterativo ed Evolutivo

In questo approccio lo sviluppo è organizzato in una serie di miniprogetti brevi, di lunghezza fissa chiamati **iterazioni**.

Il risultato di ciascuna iterazione è un sistema eseguibile, testato e integrato, anche se parziale.

> Ciascuna iterazione comprende le proprie attività di analisi dei requisiti, progettazione, implementazione e test.

Questa strategia di sviluppo permette un'approccio stutturato dell'applicativo che valorizza il feedback del clienti o tester(molto importante soprattutto nelle fasi iniziali) piuttosto che una speculazione sui requisiti del progetto.

Il feedback delle varie iterazioni puó venire da diverse fonti:
- dai **programmatori**, soprattutto nelle attivitá iniziali
- dai test
- dal cliente
- dal mercato

### Vantaggi
- Minore probabilitá di fallimento
- Migliore produttivitá
- Percentuale piú bassa di difetti
- Riduzione precoce dei rischi maggiori
	- tecnici, requisiti, obiettivi, usabilità,$\dots$
- Progresso visibile sin dall'inizio
- Feedback precoce
- Gestione della complessità del progetto
	- Il team non viene sopraffatto dalla “paralisi da analisi” o da passi molto lunghi e complessi.

### Durata delle iterazioni
Molti metodi iterativi raccomandano una durata delle tirazione di **2-6 settimane**.

Iterazioni piú lunghe possono essere controproducenti e aumentare il rischio del progetto.

> Meno di due settimane sono insufficienti per produrre abbastanza software per avere un feedback significativo, mentre piú di 6 possono portare a una complessitá eccessiva e quindi ad un feedback ritardato.

Una buona pratica é quindi quella di fissare la durata delle iterazioni, fissando delle **timebox**.
Se sembra difficile rispettare una scadenza, si possono rimandare alcune attivitá o requisiti alle iterazioni successive, ma **non ritardare** la scadenza.


### Pianificazione Iterativa
Una fase critica dello sviluppo iterativo é la pianificazione delle iterazioni.

> Poiché nello sviluppo iterativo si adatta il progetto al feedback, é inutile pianificare tutto all'inizio.

Si predilige quindi la pratica della **pianificazione iterativa**, o adattiva, in cui in ciascuna iterazione viene stabilito il piano di lavoro per una singola iterazione.

Lo sviluppo iterativo promuove la pianificazione guidata da due aspetti critici:
- Pianificazione guidata al **rischio**
	- Si identificano e attenuano i rischi maggiori
- Pianificazione guidata al cliente
	- Si construiscono le caratteristiche di maggior rilievo per il cliente

> Lo sviluppo iterativo guidato al rischio comprende la creazione di una base architetturale solida nelle prime fasi, detto sviluppo iterativo centrato sull'architettura.

