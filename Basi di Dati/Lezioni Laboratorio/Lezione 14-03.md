### Documentazioen associata agli schemi concettuali
Uno schema E-R non è mai sufficiente a rappresentare tutti gli aspetti di un'applicazione.

#### Regole aziendali
Uno schema ER non e' completo senza regole associate.

Sono uno strumento per rappresentare delle caratteristiche del dominio applicativo.

In particolare: 
- Descrizione di un concetto rappresentato nel diagramma ER(Dizionario dei dati)
	- Entita',relazione, attributo
- Vincolo di integrita'(Asserzioni)
	- Non possono essere rappesentato nell'ER
- Regole di Derivazione
	- Concetti che possono essere ottenuti attraversi inferenza o calcoli da altri concetti dello schema

## Requisiti di una base di dati
E' divisa in piu' parti:
- Raccolta dei requisiti
	- Si individuano i problemi da risolvere
	- Si dividono le carrateristiche 
		- Dati
		- Operazioni sui dati
- Analisi dei requisiti
	- Chiarire e organizzare le specifiche raccolte.
### Raccolta dei requisiti
Le possibili fonti possono esere:
- Utenti e committenti, attraverso interviste e documentazione
- Documentazione esistente
	- Normative
	- Regolamenti interni 
	- Modulistica
- Realizzazioni preesistenti
### Regole per l'analisi dei requisiti
- Costruire un glossario dei termini
- Scegliere il corretto livello di astrazione
	- Scegliere termini generici
	- Evitare di scegliere termini troppo generici o troppo specifici
- Standardizzare la struttura delle frasi
	- Semplificare le frasi contorte
- Suddividere le frasi articolate
- Separare le frasi sui dati da quelle sulle funzioni
	- Separazione della parte statica da quella dinamica

## progettazione concettuale
### Criteri generali di rappresentazione
Definizione|Costrutto
--|--
Se un concetto ha proprietà significative e/o descrive classi di oggetti con esistenza autonoma|Entita'
Se un concetto è semplice e non ha proprietà associate| Attributo
Se un concetto correla due o più entità|Relazione
Se uno o più concetti sono casi particolari di un altro| Generalizzazione
