Per progettare in ogge ci sono fondamentalmente 3 modi:
- **Codificare**
	- Progettare mentre si codifica
- **Disegnare, poi codificare**
	- Disegnare alcuni diagrammi UML, poi passare al punto alla codifica
- **Solo disegno**
	- Lo strumento genera ogni cosa dai diagrammi

La modellazione agile ha, tra gli altri, lo scopo di ridurre il costo aggiuntivo del disegno e modellare per comprendere e comunicare, anziché per documentare.
Per ottenere ció comprende le seguenti pratiche:
- Modellare insieme agli altri. 
- Creare diversi modelli in parallelo

## Modellazione statica e dinamica
Ci sono **due tipi** di modelli per gli oggetti: 
- **dinamici**/**diagrammi di interazione**
	- aiutano a **progettare** la **logica**, il comportamento del codice o il corpo dei metodi
- **statici**/**diagrammi delle classi**
	- aiutano a **progettare** la **definizione** dei **package**, dei nomi delle classi, degli attributi e delle firme (*ma non dei corpi*) dei metodi

> In agile si dedichi un po' di tempo ai diagrammi di interazione (dinamici), poi si passi ai diagrammi delle classi corrispondenti (statici).

![[Pasted image 20230516214147.png]]

### Messaggi
Un’interazione è motivata dalla necessità di eseguire un determinato compito, rappresentato da un messaggio(**mesaggio trovato**). 
**Se** il compito è **complesso**, questo oggetto non lo svolge da solo, ma collabora e interagisce con altri oggetti (**partecipanti**). Ciascun partecipante **svolge un proprio ruolo** nell’ambito di questa collaborazione, in modo da **implementare collettivamente** il compito richiesto.
La **collaborazione** avviene **mediante** lo **scambio di messaggi**: **ciascun** messaggio **è una richiesta** che un oggetto fa a un altro oggetto di eseguire un’operazione.

### Diagrammi di iterazione
I **diagrammi di interazione** illustrano il modo in cui gli **oggetti** interagiscono **attraverso** lo scambio di messaggi.
Sono una **generalizzazione** di due tipi più specifici di diagrammi di UML: 
- **diagrammi di sequenza**
- **diagrammi di comunicazione**

I diagrammi di sequenza **mostrano** le **interazioni** in una specie di **formato a steccato**, in cui gli oggetti che partecipano all’interazione sono mostrati in alto.

![[Pasted image 20230516215008.png]]

I diagrammi di comunicazione mostrano le **interazioni** **tra** gli **oggetti** in un f**ormato a grafo** o a rete, in cui gli oggetti possono essere posizionati ovunque nel diagramma.

![[Pasted image 20230516215052.png|500]]

> Ogni tipo di diagramma ha dei vantaggi, e i modellatori hanno le loro preferenze personali; non esiste una scelta “corretta” in senso assoluto.

#### Notazione dei diagrammi di interazione
###### Partecipanti
I **partecipanti** all'interazione vengono rappresentati con **rettangoli**, chiamati **linee di vita**(*lifeline*).
Questa comprende sia un rettangolo che una linea verticale che si estende sotto di esso, che puó essere sia continua che tratteggiata.

![[Pasted image 20230516220559.png]]

###### Messaggi
I **messaggi** (di solito sincroni) tra gli oggetti sono rappresentati da un’**espressione messaggio** mostrata su una linea continua con una freccia piena tra le linee di vita verticali.

> Il pallino rappresentante il messaggio trovato, ovvero quello iniziale, che dá inizio al compito, puó essere omesso.

![[Pasted image 20230516221816.png]]

I **messaggi** vengono espressi con la seguente sintassi:
```c
return = message(parameter : parameterType) : returnType
```
Le parentesi vengono solitamente escluse se non ci sono parametri, anche se sono permesse.

Alcuni esempi validi
```c
initialize(code) 
initialize 
d = getProductDescription(id) 
d = getProductDescription(id:ItemID) 
d = getProductDescription(id:ItemID) : ProductDescription
```

###### Singleton
I **singleton** vengono indicati **specificando** un '**1**' sulla lifeline, per indicare che esiste una singola istanza.
![[Pasted image 20230516222022.png]]

###### Risultati o Ritorni
Ci sono **due modi** per **mostrare** il **risultato** di ritorno per un messaggio:
- Utilizzare per il messaggio la sintassi `returnVar = message(parameter)`.
- Utilizzare una linea di messaggio di risposta (o ritorno) alla fine di una barra di specifica di esecuzione.
ma durante l'abbozzo é preferibile il primo.

![[Pasted image 20230516222808.png|500]]

###### Messaggi "self" o "this"
É possibile mostrare i messaggi inviati a sé stessi(**self** o **this**) nella seguente maniera:
![[Pasted image 20230516222941.png|350]]

###### Creazione e distruzione di istanze
Per creare un'istanza si indica il messaggio *create*, indicando una linea tratteggia a freccia piena.
![[Pasted image 20230516223144.png]]

Se si vuole indicare che un'oggetti non é piú utilizzabile si usa invece la seguente sintassi:
![[Pasted image 20230516223338.png]]

###### Formazione di collegamenti
Formazione di un collegamento di un’associazione “a molti”:
![[Pasted image 20230516231613.png]]

Formazione di un collegamento di un’associazione “a uno”:
![[Pasted image 20230516231639.png|600]]
Il **vincolo** va interpretato come una **post-condizione** dell’operazione.

###### Frame
I **frame** sono **regioni** o frammenti dei **diagrammi** con un **operatore**(o **etichetta**) e una **guardia**(ovvero una clausola condizionale, posizionata sopra alla lifeline di valutazione).
Operatore Frame|Significato
--|--
alt|Frammento alternativo per logica mutuamente espressa nella guardia.(if-else)
opt|Frammento opzionale che viene eseguito se la guardia è vera (if).
loop|Frammento da eseguire ripetutamente finché la guardia è vera.Si può anche scrivere loop(n) per indicare un ciclo da ripetere n volte
par|Frammenti che vengono eseguiti in parallelo.
region|Regione critica all’interno della quale può essere in esecuzione un solo thread.
I Frame possono essere annidati.

Frame opzionale:
![[Pasted image 20230516232246.png]]
Frame Alternativo:
![[Pasted image 20230516232345.png]]
Frame di cilo:
![[Pasted image 20230516232425.png]]

###### Correlare i diagrammi di interazione
Una **occorrenza di interazione** (chiamata anche un **uso di interazione**) è un **riferimento** a un’**interazione** all’interno di un’**altra interazione** che permette di **correlare** e collegare i relativi **diagrammi**.

![[Pasted image 20230516233014.png]]

> Utile per decompore porzioni in piú diagrammi.

Esse sono create con due frame correlati: 
- un **frame** attorno a un intero diagramma di iterazione, **etichettato** con il **tag sd** e con un nome
- un **frame** con **tag ref**, chiamato un **riferimento**, che **referenzia** un altro **diagramma** di iterazione tramite il nome

###### Messaggi alle classi per invocare metodi statici
È possibile **mostrare** le **chiamate** a un **metodo di classe**, o statico, utilizzando un’**etichetta** nella lifeline per **indicare** che l’**oggetto** **ricevente** è una classe.

![[Pasted image 20230516233809.png]]

###### Messaggi e casi polimorfi
> Non é presente nelle slides.

Per mostra il polimorfismo in un diagramma si utilizzano più diagrammi di sequenza: 
- uno che mostra il messaggio polimorfo all’oggetto della superclasse astratta o dell’interfaccia
- dei diagrammi di sequenza separati che descrivono nel dettaglio ciascun caso polimorfo, ciascuno che inizia con un messaggio trovato polimorfo

![[Pasted image 20230516234159.png]]

###### Chiamate sincrone e asincrone
La notazione UML per le **chiamate asincrone** è un **messaggio** con una **freccia** con la **punta non piena**. Il contrario per le chiamate sincrone(bloccanti).

![[Pasted image 20230516234424.png]]

Un oggetto come Clock  è detto anche un **oggetto attivo**, di cui ciascuna istanza è eseguita nel proprio thread di esecuzione, indicato con delle doppie linee verticali.

### Diagrammi delle classi
UML comprende i **diagrammi delle classi** per illustrare le **classi**, le **interfacce** e le relative **associazioni** utilizzate nella modellazione statica degli oggetti.
Questi vengono di solito chiamati **diagrammi delle classi di progetto**(**DCD**, *Design Class Diagram*).

![[Pasted image 20230516234819.png]]

#### Attributi delle classi: Notazione testuale
Gli **attributi** di una classe possono essere mostrati usando una **notazione testuale**,scrivendoli nella **seconda sezione** del rettangolo per una classe.

![[Pasted image 20230516235451.png|400]]

Il formato della notazione testuale per un attributo è: 
```c
visibility name: type multiplicity = default {property-string}
```
dove la visibilitá comprende due simboli
- +(pubblica)
- -(privata)

Se non viene indicata alcuna visibilità, solitamente si ipotizza che gli attributi siano privati.

#### Attributi delle classi: Notazione testuale
Le linee di associazione di una classe vengono mostrate mediante una linea di associazione, usando il seguente stile:
- Una **freccia di navigabilità** rivolta dalla classe sorgente alla classe destinazione dell’associazione, che indica che un oggetto ha un attributo di determinato tipo.
- Una **molteplicità** all’estremità vicina alla destinazione, ma non all’estremità vicina alla sorgente.
- Un **nome di ruolo**, opzionale, solo all’estremità vicina alla destinazione, per indicare il nome dell’attributo.
- Nessun nome per l’associazione

![[Pasted image 20230517000721.png]]

> Si utilizzi la notazione testuale per gli attributi il cui tipo è un tipo di dato, e la notazione delle linee di associazione per gli altri attributi.

###### Simboli per le annotazioni
Un simbolo di nota consente di rappresentare diverse cose, tra cui:
- una nota o un commento 
![[Pasted image 20230517001138.png]]
- un vincolo 
![[Pasted image 20230517001149.png]]
- il corpo di un metodo

###### Operazioni
Un’**operazione** di UML è una **dichiarazione**, con un **nome**, dei **parametri**, un **tipo** di **ritorno**, un elenco di **eccezioni** e magari un insieme di vincoli di precondizioni e post-condizioni.

> Non sono né un metodo né la sua implementazione.

Una delle sezioni del rettangolo per una classe UML mostra le firme delle operazioni. La sintassi ufficiale é la seguente:
```c
visibility name (parameter-list) : return-type {property-string}
```

La stringa di proprietà contiene **informazioni aggiuntive**, come le eccezioni che possono essere sollevate.

###### Metodi
Un metodo è l’implementazione di un’operazione, che ne rispetta i vincoli.

Puó essere rappresentato:
- nei diagrammi di interazione, dai dettagli e dalla sequenza dei messaggi;
- nei diagrammi delle classi, con una nota di UML stereotipata con «method».

###### Parole chiave
Una **parola chiave** in UML è un **decoratore testuale** per classificare un elemento di un modello.

La maggior parte delle parole chiave è mostrata tra **virgolette basse** (« ») ma **alcune** di esse sono mostrate tra **parentesi graffe**, come {abstract}, che è un vincolo che contiene la parola chiave *abstract*.

Parola Chiave|Significato
--|--
« actor »|Il classificatore é un attore.
« interface »|Il classificatore é un'interfaccia
{abstract}|l’elemento è astratto; non può essere istanziato
{ordered}|un insieme di oggetti ha un ordine predefinito

###### Stereotipi
Uno **stereotipo** rappresenta un raffinamento di un **concetto** di modellazione **esistente**, ed è definito all’interno di un profilo UML(una collezione di stereotipi), fornendo  un meccanismo di estensione.

Gli stereotipi sono mostrati con i simboli delle virgolette basse, come le parole chiave.
![[Pasted image 20230517114923.png]]

###### Generalizzazioni
Una **generalizzazione** é una **relazione tassonomica** tra un **classificatore** più **generale** e un **classificatore** più **specifico**. 
Ogni istanza del classificatore più specifico è anche un’**istanza indiretta** del classificatore più generale. Pertanto il classificatore più specifico **possiede** indirettamente le **caratteristiche** del classificatore più generale.

Le classi astratte e le operazioni astratte possono essere mostrate con un **tag {abstract}**, oppure specificando il nome in corsivo.

###### Dipendenze
UML comprende una **relazione di dipendenza** generale che indica che un **elemento cliente**  è a conoscenza di un altro **elemento fornitore** e che un **cambiamento** nel fornitore **potrebbe influire** sul cliente.

> Le dipendenze possono essere viste come un’altra versione dell’accoppiamento.

Esistono molte tipologie di dipendenze:
- Avere un attributo del tipo del fornitore. 
- Inviare un messaggio a un fornitore; la visibilità verso il fornitore potrebbe essere data da: 
	- un attributo
	- una variabile parametro
	- una variabile locale
	- una variabile globale 
	- una visibilità di classe (chiamata di metodi statici o di classe).
- Ricevere un parametro del tipo del fornitore. 
- Il fornitore è una superclasse o un’interfaccia implementata.

> Nei diagrammi delle classi le linee delle dipendenze vanno usate per descrivere le dipendenze tra gli oggetti per visibilità globale, per variabile parametro, per variabile locale e per metodo statico (quando viene effettuata una chiamata a un metodo statico di un’altra classe).

![[Pasted image 20230517120605.png]]

Per mostrare il tipo di una dipendenza, la linea della dipendenza può essere etichettata con parole chiave o stereotipi.
![[Pasted image 20230517120645.png]]

###### Interfacce
UML offre diversi modi per mostrare l’implementazione di un’interfaccia:
- **fornire un’interfaccia** ai propri clienti (un’**interfaccia fornita**)
- **dipendenza** da un’**interfaccia** (un’**interfaccia richiesta**)
L’implementazione di un’interfaccia viene chiamata anche una **realizzazione** di **interfaccia**.

![[Pasted image 20230517120837.png]]

La **notazione** a **pallina** (*lollipop*) indica che una **classe X implementa** (fornisce) un’interfaccia Y, senza disegnare il rettangolo per l’interfaccia Y.

La **notazione** a **semicerchio** (*socket*) indica che una **classe X richiede** (usa) un’interfaccia Y, senza disegnare una linea che punta all’interfaccia Y.

###### Composizione
Una possibile interpretazione (dal punto di vista software) di una composizione tra le classi A e B é  la seguente: 
- Gli oggetti B non possono esistere indipendentemente da un oggetto A 
- L’oggetto A é responsabile della creazione e distruzione dei suoi oggetti B
![[Pasted image 20230517121126.png]]

> Nel dubbio, meglio tralasciarla.

###### Vincoli
Un vincolo indica una **restrizione** o una condizione su un elemento di un diagramma. viene visualizzato come testo tra parentesi graffe(*{ size >= 0 }*).

###### Classi singleton
É un pattern per il quale esiste sempre una sola istanza di una classe. 
Può essere contrassegnata da ‘1’ nell’angolo superiore destro nella sezione del nome.
![[Pasted image 20230517121421.png]]

###### Classi e interfacce template
Molti linguaggi  supportano **tipi a template**, noti anche come template, tipi parametrizzati e generici, usati comunemente come tipo per gli elementi delle classi collezione.

![[Pasted image 20230517121604.png]]

### Relazione tra diagrammi di interazione e diagrammi delle classi
Quando si disegnano i diagrammi di interazione, dal processo di progettazione emergono un insieme di classi e i relativi metodi.
Pertanto, è possibile generare le definizioni dei diagrammi delle classi dai diagrammi di interazioni.

Ciò suggerisce un ordinamento lineare secondo cui disegnare i diagrammi di interazione prima dei diagrammi delle classi, ma non é sempre corretto.

