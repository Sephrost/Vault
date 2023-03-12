# Unified Process/UP
**Unified Process**, o UP, è un processo **iterativo** diffuso per lo sviluppo del soft­ware per la costruzione di sistemi orientati agli oggetti.

> É un processo di sviluppo relativamente diffuso per progetti che fanno uso dell'OOA/D.

UP è flessibile e può essere applicato usando un approccio leggero e agile che comprende pratiche di altri metodi agili, come il timeboxing e il test driven development.

Combina quindi le best practice comunemente accettate, come un ciclo di vita iterativo e il risk driven development.

## Best practice di UP
Le best practice e i concetti chiave di UP sono:
- Affrontare le problematiche di rischio maggiore e valore elevato nelle iterazioni iniziali. 
- Impegnare gli utenti continuamente sulla valutazione, il feedback e i requisiti. 
- Creare una architettura coesa nelle iterazioni iniziali. 
- Verificare continuamente le qualità; testare presto, spesso e in modo realistico. 
- Applicare i casi d’uso, se appropriato. 
- Fare della modellazione visuale (con UML). 
- Gestire attentamente i requisiti. 
- Gestire le richieste di cambiamento e le configurazioni.

## Fasi di UP
Un progetto UP organizza il lavoro in 4 fasi principali:
- **Ideazione**
	- Visione approssimativa, studio economico, portata, stime approssimative dei costi e dei tempi
	- É diversa dalla fasi dei requisiti
	- É una fase di fattibilitá, in cui viene eseguita un’indagine sufficiente a sostenere la decisione di proseguire con il progetto o di interromperlo
- **Elaborazione**
	- Visione raffinata, implementazione iterativa del nucleo dell’architettura, risoluzione dei rischi maggiori, identificazione della maggior parte dei requisiti e della portata, stime più realistiche.
	- Non é la fase dei requisiti o della progettazione
	- É una fase in cui viene implementata in modo iterativo l’architettura del sistema
	- Vengono inoltre mitigati i rischi maggiori
- **Costruzione**
	- Implementazione iterativa degli elementi rimanenti, più facili e a rischio minore, e preparazione al rilascio
- **Transizione**
	- Beta,test e rilascio

![[Pasted image 20230306191206.png]]

## Discipline di UP

Un **disciplina** é un'**insieme** di **attivitá** e dei relativi **elaborati** in una determinata area.

Un'esempio di disciplina sono le attivitá relative all'analisi dei requisiti.

Ci sono diverse discipline di UP, tra le quali:
- **Modellazione del business**
	- L’elaborato Modello di Dominio, per visualizzare i concetti significativi nel dominio dell’applicazione.
- **Requisiti**
	- Gli elaborati Modello dei Casi d’Uso e Specifica Supplementare, per descrivere i requisiti funzionali e non funzionali.
- **Progettazione**
	- L’elaborato Modello di Progetto, per il progetto degli oggetti software.
- **Implementazione**
	- Attivitá di progetto dettagliato e codifica del sistema, test su componenti.
- **Test**
	- Attivitá di controllo di qualitá, test di integrazione e di sistema. 
- **Rilascio**
	- Attivitá di consegna e messa in opera.

### Discipline di supporto
- **Gestione delle configurazioni e del cambiamento**
	- Attivitá di manutenzione durante il progetto. 
-  **Gestione del progetto**
	- Attivitá di pianificazione e governo del progetto. 
- **Infrastruttura**
	- Attivitá che supportano il team di progetto, riguardo ai processi e strumenti utilizzati.

![[Pasted image 20230306192116.png|450]]

> Durante un’iterazione viene svolto del lavoro in quasi tutte le discipline.

### Elaborati
Un **elaborato**, o **artefatto**, é il termine generico che indica un qualsiasi **prodotto** di un **lavoro**, come:
- il codice
- schemi di base di dati
- documenti di testo
- diagrammi
- modelli


### Altro sulle discipline
Le discipline **non sono sequenziali** e si eseguono nel progetto in ogni iterazione.

Le iterazioni iniziali tendono in modo naturale a dare una maggiore enfasi relativa sui requisiti e sulla progettazione, mentre quelle successive lo faranno in misura minore . Questo perché i requisiti e il progetto si stabilizzano attraverso un processo di feedback e adattamento.

