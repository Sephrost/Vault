# Sicurezza
Definiamo come sicurezza di un computer i sistemi di protezione applicati ad un sistema informatico al fine di mantenere l'**integritá**, la **disponibilitá** e la **confidenzialitá** delle risorse del sistema.

## C.I.A. 
Gli obiettivi principali della sicurezza sono quindi
- **Confidenzialitá**(*confidentiality*)
	- **Confidenzialitá dei dati**: Assicura che le informazioni private non siano rese disponibili a individui non autorizzati
	- **Privacy**: Assicura che i singoli individui possano controllare quali informazioni a loro collegate possano essere raccolte e da chi possano essere condivise
- **Integritá**(*Integrity*)
	- **Integritá dei dati**: Garantisce che le infromazioni siano modificati solo in maniera specifica e da soggetti autorizzati
	- **Integritá del sistema**: Assicura che un sistema svolga le funzioni per cui é stato programmato senza alcuna manipolazione accidentale o voluta
- **Disponibilitá**(*Availability*): Assicura che i sistemi funzionino prontamente.

Per alcuni campi particolari della sicurezza informatica possono essere presenti obiettivi aggiuntivi come per esempio l'[**autenticitá**](Autenticitá) e la **responsabilitá**([*Accountability*](Accountability.md)).

##  Architettura di sicurezza OSI 
Per poter valutare efficacemente i requisiti di sicurezza e scegliere che misure e politiche applicare, l'architettura di sicurezza OSI puó essere un modo efficace 

### Attacchi alla sicurezza
Ogni azione volta a compromettere la sicurezza.

Vengono classificati in attacchi **passivi** e **attivi**.
#### Attacchi Passivi
Possono essere una maniera di ottenere e usare informazioni senza intaccare le risorse di un sistema.

Alcuni esempi di questi tipi di attacchi sono:
- Divulgazione del contenuto di un messaggio
- Analisi del traffico

Sono inoltre difficili da scoprire, poiché non prevono alcuna modifica ai dati, am rimangono comunque facili da prevenire.

#### Attacchi Attivi
Gli attacchi attivi includono una qualche modifica del flusso di dati.

Possono essere divisi in 4 categorie:
- **Masquerade**: quando un'entitá si finge un'altra
	- Di solito ivolvono un'altro vettore di attacco attivo
- 