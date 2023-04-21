## Architettura logica
L’**architettura logica**  è l’**organizzazione** su **larga scala** delle **classi** software in package, sottosistemi e strati.

Essa puó essere illustrata mediante un **diagramma dei package** UML, il quale fornisce un modo per raggruppare gli elementi.

Un package UML rappresenta un **namespace**.

> Il nome di un package può essere scritto sulla sua linguetta (tab), se all’interno del package sono mostrati dei membri, oppure nella cartella principale, in caso contrario.

Per mostrare le dipendenze tra pacchetti vengono utilizzate le **dipendenze** UML una linea tratteggiata con una freccia che punta verso il package da cui si dipende.

![[Pasted image 20230420153032.png]]

### Architettura a strati
Uno stile comune per l’architettura logica è l’**architettura a strati**, nel quale il sistema è formato da un **insieme** di elementi chiamati **strati**.

L'idea fondamentale degli strati é quindi la separazione delle responsabilitá sulla struttura logica del progetto.
Questo avviene suddividendo il sistema, che sarebbe troppo complesso in un insieme di elementi software in maniera tale da poter sviluppare e modificare ciascun elemento in maniera indipendente dagli altri.

Ciascuno strato é un gruppo di classi, package o sottosistemi.
Un'applicazione software comprende solitamente i seguenti strati:
- **User Interface**
	- Oggetti software per gestire l’interazione con l’utente.
- **Application Logic** e **Domain Objects**
	- Oggetti software che rappresentano concetti del dominio e soddisfano i requisiti dell'applicazione.
- **Technical Services**
	- Oggetti e sottosistemi d’uso generale che forniscono servizi tecnici di supporto.

> Uno strato può richiamare solo i servizi dello strato immediatamente sottostante.

L'utilizzo degli strati presenta quindi **diversi vantaggi**, tra cui:
- La **separazione** degli **interessi** e dei **servizi**
- L'**incapsulamento** della **complessitá**
- La **sostituzione** di alcuni **strati** con **nuove implementazioni**
- La **riusabilitá** degli strati piú bassi

> Le responsabilità degli oggetti devono essere fortemente correlate l’uno all’altro, e non devono essere mischiate con le responsabilità degli altri strati.

#### Separazione Modello-Vista
Il principio di **Separazione Modello-Vista** afferma che gli **oggetti** del dominio non devono avere una conoscenza diretta degli oggetti della vista.

Le le classi di **dominio** **incapsulano** le **informazioni** e il comportamento relativi alla logica applicativa, mentre gli oggetti della vista sono responsabili dell’input e dell’output, e di catturare gli eventi della GUI, ma **non mantengono** i dati dell’applicazione né forniscono direttamente della logica applicativa.

La Separazione Modello-Vista si basa sulle seguenti motivazioni:
- Favorire la definizione coesa dei modelli
- Consentire lo sviluppo separato degli strati del modello e dell’interfaccia utente.
- Minimizzare l’impatto sullo strato del dominio dei cambiamenti dei requisiti relativi all’interfaccia. 
- Consentire di connettere facilmente nuove viste a uno strato del dominio esistente, senza ripercussioni sullo strato del dominio. 
- Consentire viste multiple simultanee sugli stessi oggetti modello, 
- Consentire l’esecuzione dello strato del modello indipendente da quella dello strato dell’interfaccia utente, come in sistema batch o basato sull’elaborazione di messaggi.
- Consentire un porting facile dello strato del modello a un altro framework per l’interfaccia utente.