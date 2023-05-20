Dopo aver identificato i requisiti e a ver creato un modello di dominio, si dovrebbero definire:
- i metodi delle classi 
- i messaggi tra gli oggetti necessari per soddisfare i requisiti

> Il decidere quali metodi appartengono a chi e come devono interagire gli oggetti ha delle conseguenze, e pertanto queste scelte vanno fatte con serietà.

### Input della progettazione ad oggetti
Nome|Funzione
--|--
Testo dei casi d’uso|definisce il comportamento visibile che gli oggetti software devono in definitiva supportare
Specifiche Supplementari|definiscono gli obiettivi non funzionali, che gli oggetti devono soddisfare
Glossario|Permette di chiarire i dettagli dei parametri o dei dati che vengono dallo strato UI, i dati che vengono passati alla base di dati, e la logica specifica per ciascun elemento e i requisiti di validazione
Modello di dominio|Suggerisce alcuni nomi e attributi degli oggetti software di dominio nello strato del dominio dell’architettura software
Diagrammi di sequenza di sistema|Identificano i messaggi per le operazioni di sistema
Contratti delle operazioni|Sono complementari al testo dei casi d’uso per chiarire che cosa devono compiere gli oggetti software in un’operazione di sistema. <br>Le postcondizioni definiscono in modo dettagliato i risultati da ottenere.

**Tutti** questi elaborati in UP sono peró **opzionali**, vengono solo creati per ridurre i rischi.

Dato uno o più di questi input, gli sviluppatori possono 
1. iniziare **immediatamente** a **codificare**,progettando mentre si codifica
2. **iniziare** con un po’ di **modellazione UML** per la progettazione a oggetti
3. iniziare con un’**altra tecnica** di modellazione, come le schede CRC

La cosa più importante è che, durante le attività di disegno (e codifica), vengano applicati vari principi di **progettazione OO**, come i **pattern GRASP** e i design **pattern Gang-of-Four** (GoF).

### Output della progettazione ad oggetti
Gli output della programmazione ad oggetti sono i diagrammi di interazione(DSD) e i diagrammi delle classi UML.

### RDD - Responsability-driven Programming
Durante la progettazione ad oggetti vengono utilizzati spesso i concetti di responsabilitá, ruolo e collaborazioni.
Questi fanno parte di un approccio chiamato **progettazione guidata dalle responsabilità** (**RDD**, *Responsibility-Driven Development*).

Nella RDD, gli **oggetti software** sono considerati come **dotati** di **responsabilità**, un’**astrazione** di **ciò** che **fa** o **rappresenta** un oggetto.
Queste sono correlate agli obblighi o al comportamento di un oggetto in relazione al suo ruolo, e sono di sue tipi:
- di **fare**
	- fare qualcosa esso stesso(creare un oggetto,eseguire un calcolo, $\dots$)
	- chiedere ad altri oggetti di eseguire azioni
	- controllare e coordinare le attività di altri oggetti
- di **conoscere**
	- conoscere i propri dati privati
	- conoscere gli oggetti correlati
	- conoscere cose che può derivare o calcolare	  

> Le responsabilità sono assegnate alle classi di oggetti durante la progettazione a oggetti.

Per gli oggetti software di dominio, il **modello di dominio** spesso **ispira le responsabilità** più importanti relative al “conoscere”, grazie agli attributi e alle associazioni che mostra.

> L’idea di responsabilità è solo un’**astrazione**.
> Nel software non c’è niente che corrisponde direttamente a una responsabilità, ma sono implementate per mezzo degli oggetti e metodi che agiscono da soli oppure che collaborano con atri oggetti e metodi

La **RDD** viene **eseguita iterativamente**:
1. **Identifica** le **responsabilità**, e considerale una alla volta
2. Chiediti **a quale oggetto** software **assegnare** questa **responsabilità**
3. Chiediti **come** fa l’oggetto scelto a **soddisfare** questa **responsabilità**

Questo procedimento va basato su **opportuni criteri** per l’**assegnazione** di **responsabilità**, come i pattern GRASP.

### GRASP - General Responsability Assignment Software Pattern
I **pattern GRASP** sono un **aiuto** per l’**apprendimento** degli **aspetti essenziali** della progettazione a oggetti e per l’applicazione dei ragionamenti di progettazione in un modo metodico, razionale e spiegabile.

**GRASP** è l’acronimo di **General Responsibility Assignment Software Patterns,** ovvero di Pattern Generali per l’Assegnazione di Responsabilità nel Software.

#### Grasp e UML
Le **decisioni** sull’**assegnazione** delle **responsabilità** agli oggetti possono essere prese: 
- mentre si esegue la codifica 
- durante la modellazione

Il disegnare i diagrammi di interazione diventa l’occasione per considerare tali responsabilità.
Il disegno deve poi illustrare le scelte di progetto fatte.
![[Pasted image 20230518171413.png]]

È possibile applicare i principi GRASP mentre si disegnano i diagrammi di interazione di UML, ma anche durante la codifica.

#### Pattern
Un pattern é una **descrizione**, con **nome**, di un **problema di progettazione ricorrente** e di una sua soluzione ben provata e che puó essere applicata a nuovi contesti.

Esso dà consigli su come applicare la sua soluzione in circostanze diverse e considera le forze e i compromessi.

I GRASP definiscono nove principi di progettazione OO di base o blocchi di costruzione elementari della progettazione.

#### I nove pattern grasp
1. Creator 
2. Information Expert 
3. Low Coupling 
4. Controller 
5. High Cohesion 
6. Polymorphism 
7. Pure Fabrication 
8. Indirection 
9. Protected Variations

#### Sistemi software bel progettati e GRASP
Un sistema software **ben progettato** è **facile da comprendere**, da **mantenere** e da **estendere**. Inoltre le scelte fatte consentono delle buone opportunità di riusare i suoi componenti software in applicazioni future. 
Queste qualitá sono sostenute dal principio classico della progettazione modulare, rappresentato dai pattern GRASP **high cohesion** e **low coupling**.

Questi due pattern sarebbero sufficienti per guidare correttamente l’assegnazione di molte responsabilità e sostenere le qualità di progetto indicate sopra, ma nella realtá sono **difficili da applicare direttamente**, per questo vengono aggiunti ulteriori pattern (Information Expert, Creator e Controller) per aiutare nel processo decisionale della progettazione.

I rimanenti pattern GRASP (Pure Fabrication, Polymorphism, Indirection e Protected Variations) favoriscono **l’assegnazione di responsabilità** in altri casi.

#### Creator
###### Problema
Chi deve essere responsabile della creazione di una nuova istanza di una classe?
###### Soluzione
Sia dato una classe creatrice B.

Assegna alla classe B la responsabilità di creare un’istanza della classe A se una delle seguenti condizioni è vera (più sono vere, meglio è):
- B “contiene” o aggrega con una composizione oggetti di tipo A.
- B registra A. 
- B utilizza strettamente A.
- B possiede i dati per l’inizializzazione di A, che saranno passati ad A al momento della sua creazione. Pertanto B è un Expert rispetto alla creazione di A.

Se sono applicabili più opzioni, solitamente va preferita una classe B che aggrega o contiene la classe A.

###### Vantaggi
Creator favorisce un **accoppiamento basso**(*low coupling*), il che implica **minori dipendenze** di manutenzione e **maggiori opportunità di riuso**.

###### Controindicazioni
Talvolta la creazione di oggetti è un’attività complessa o addirittura molto complessa, in questi casi è consigliabile delegare la creazione a una classe di supporto (helper) (pattern non-GRASP, come le *Factory*).

#### Information expert/expert
###### Problema
Qual è un principio generale nell’assegnazione di responsabilità agli oggetti?

Se le scelte sono buone, i sistemi tendono a essere:
- più facili da comprendere
- da mantenere
- da estendere
- consentono maggiori opportunità di riuso dei suoi componenti
###### Soluzione
Assegna una responsabilità all’**esperto delle informazioni**, ovvero alla **classe** che **possiede** le **informazioni necessarie** per soddisfare la responsabilità.
###### Vantaggi
L’incapsulamento delle informazioni viene mantenuto, poiché gli oggetti usano le proprie informazioni per adempiere ai propri compiti. Questo sostiene un accoppiamento basso, che dà luogo a sistemi più robusti e mantenibili.

Il comportamento è inoltre distribuito tra tutte le classi che possiedono le informazioni richieste, incoraggiando in tal modo definizioni di classe più coese e “leggere”
###### Controindicazioni
In alcune situazioni, una soluzione suggerita da Expert non è opportuna, solitamente a causa di problemi di accoppiamento e di coesione. 

#### Low Coupling
###### Problema
L’**accoppiamento** (*coupling*) è una misura di **quanto fortemente** un **elemento** è **connesso** ad **altri elementi**, in termini di conoscenza e dipendenza.

Un elemento con un accoppiamento basso (o debole) non dipende da troppi altri elementi, e é quindi piú facile da modificare,comprendere e riusare.

Come sostenere una dipendenza bassa, un impatto dei cambiamenti basso e una maggiore opportunità di riuso?
###### Soluzione
Assegna una responsabilità in modo che l’accoppiamento rimanga basso. Usa questo principio per valutare le alternative.
###### Definizione di accoppiamenti
Nei linguaggi di programmazione orientati agli oggetti le **forme** più **comuni** di **accoppiamento** da una tipo **X** a un tipo **Y** comprendono le seguenti:
- La classe X ha un attributo (una variabile d’istanza o un dato membro) di tipo Y o referenzia un’istanza di tipo Y o una collezione di oggetti Y.
- Un oggetto di tipo X richiama operazioni o servizi di un oggetto di tipo Y.
- Un oggetto di tipo X crea un oggetto di tipo Y.
- Il tipo X ha un metodo che contiene un elemento (parametro, variabile locale oppure tipo di ritorno) di tipo Y o che referenzia un’istanza di tipo Y
- La classe X è una sottoclasse, diretta o indiretta, della classe Y.
- Y è un’interfaccia, e la classe X implementa questa interfaccia
###### Vantaggi
- Una classe o componente con un accoppiamento basso non è influenzata dai cambiamenti nelle altre classi e componenti. 
- È semplice da capire separatamente dalle altre classi e componenti. 
- È conveniente da riusare
###### Controindicazioni
Il problema non é l'accoppiamento alto di per sé, se questo avviene tra elementi stabili o pervasisvi. Se peró questo avviene con elementi, per certi aspetti, "instabili" é sicuramente qualcosa che é meglio evitare. 
###### Esempio
Si consideri il seguente diagramma parziale delle classi
![[Pasted image 20230519190744.png|500]]
Si supponga di dover creare un’**istanza** di *CashPayment* e di **associarla** alla *Sale* **corrispondente**.

Poiché un *Register* nel dominio del mondo reale registra i pagamenti, il pattern Creator suggerisce *Register* come un candidato per la creazione di *CashPayment*. L’istanza di Register potrebbe poi inviare un messaggio setPayment alla Sale, passandogli come parametro il nuovo CashPayment, come nella seguente foto.
![[Pasted image 20230519191225.png|500]]
Questa assegnazione di responsabilità **accoppia** la classe *Register* alla **conoscenza** della **classe** *CashPayment*.

Una soluzione alternativa prevede di assegnare a la responsabilitá di creare *CashPayment* a *Sale*.
![[Pasted image 20230519191629.png|500]]

In entrambi i casi *Sale* deve essere accoppiata a *CashPayment*, ma la prima prevede un ulteriore accoppiamento tra *Register* e *CashPayment*, rendento quindi il secondo preferibile, in quanto non incrementa gli accoppiamenti.

##### High Cohesion
###### Problema
Come mantenere gli oggetti focalizzati, comprensibili e gestibili e, come effetto collaterale, sostenere Low Coupling?
###### Coesione
**La coesione** (coesione funzionale) è una **misura** di quanto fortemente siano **correlate** e **concentrate** le **responsabilità** di un elemento.
Un elemento con responsabilità altamente correlate che non esegue una quantità di lavoro eccessiva ha una coesione alta.

In pratica, esistono diverse forme di coesione, relative a diversi criteri di “raggruppamento” delle responsabilità.
Alcune forme di coesione sono le seguenti:
- **Coesione dei dati**
	- Una classe implementa un tipo di dati (questa forma di coesione di solito è molto buona). 
- **Coesione funzionale**
	- Gli elementi di una classe svolgono una singola funzione (buona o molto buona). 
- **Coesione temporale**
	- Gli elementi sono raggruppati perché usati circa nello stesso tempo (è la forma di coesione usata negli oggetti controller, ed è buona in questo caso, ma meno buona in altri casi). 
- **Coesione per pura coincidenza**
	-  Per esempio, una classe usata per raggruppare tutti i metodi il cui nome inizia per una certa lettera dell’alfabeto (molto cattiva).


###### Soluzione
**Assegna** una **responsabilità** in modo tale che la **coesione** rimanga **alta**. 

Una classe con una **coesione bassa** fa **molte cose** **non correlate** tra loro o svolge **troppo lavoro**.
Tali classi non sono opportune, e presentano i seguenti problemi:
- Sono difficili da comprendere. 
- Sono difficili da mantenere.
- Sono difficili da riusare.
- Sono delicate; sono continuamente soggette a cambiamenti.


###### Vantaggi
- High Cohesion sostiene maggiore chiarezza e facilità di comprensione del progetto. 
- Spesso sostiene Low Coupling. 
- La manutenzione e i miglioramenti risultano semplificati.
- Maggiore riuso di funzionalità a grana fine e altamente correlate, poiché una classe coesa può essere usata per uno scopo molto specifico.
###### Controindicazioni
Cercare di massimizzare la coesione non é sempre la scelta giusta, infatti in certi casi puó peggiorare la manutenzione.
###### Esempio
Riprendiamo in analisi l'esempio di Low Coupling. Dobbiamo quindi creare un'istanza di *CashPayment* e associarlo alla *Sale* corrispondente. Terniamo in considerazione il primo esempio.

Poiché il Register, nel dominio del mondo reale, registra i pagamenti, il pattern Creator suggerisce Register come un candidato per la creazione di CashPayment.
Supponendo quindi che *Register* sia un controller, allora questo ha sia la responsabilitá di ricevere il messaggio *makeCashPayment*, ma anche di soddisfarlo.

Poiché questo é un'esempio isolato é ok, ma se si continuano ad assegnarli responsabilitá essa diventerá meno coesa.

Al contrario il secondo progetto delega la responsabilità della creazione del pagamento alla *Sale* e sostiene una **coesione più alta** di *Register*. Poiché il secondo progetto sostiene una coesione alta e un accoppiamento basso è preferibile.

##### Controller
###### Problema
Qual è il primo oggetto oltre lo strato UI che riceve e coordina (“controlla”) un’operazione di sistema?

Le **operazioni di sistema** sono state inizialmente esaminate durante l’analisi degli SSD e sono quindi  gli eventi di input principali nel sistema.
Un **controller** è il **primo oggetto** oltre lo strato UI che è **responsabile** di **ricevere** o **gestire** un **messaggio** di un’operazione di sistema.

Normalmente un controller deve delegare ad altri oggetti il lavoro da eseguire durante l’operazione di sistema; il controller coordina o controlla le attività, ma non esegue di per sé molto lavoro.
###### Facade controller e controller di caso d'uso
La soluzione proposta dal pattern Controller fa riferimento a due categorie di controller: i facade controller o i controller di caso d’uso.

La prima categoria di controller è un **facade controller** che rappresenta il sistema complessivo, un dispositivo, un punto d’accesso al sistema o un sottosistema. 
L’idea è di **scegliere** un **nome** di classe che **suggerisca una copertina** o una facciata sopra agli altri strati dell’applicazione, e che **fornisca il punto di accesso principale** per le **chiamate** dei **servizi** dallo strato UI agli altri strati sottostanti.
I facade controller sono **adatti** quando **non ci sono “troppi” eventi di sistema**, o quando l’interfaccia utente (UI) non può riindirizzare i messaggi per gli eventi di sistema a più controller alternativi, come in un sistema per l’elaborazione di messaggi.

Se invece si sceglie un **controller di caso d’uso**, si avrà un **controller** diverso **per ciascun caso d’uso**. Si sceglie solitamente quando un facade controller avrebbe responsabilitá eccessive, con una coesione bassa e/o un'accoppiamento alto.

Una **decisione “intermedia”** tra facade controller e controller di caso d’uso è scegliere un **controller diverso per ciascun attore del sistema software**, che gestisce tutti i casi d’uso di quell’attore.
###### Soluzione
**Assegna** la **responsabilità** a una **classe** che rappresenta una delle seguenti scelte:
- Rappresenta il “sistema” complessivo, un “oggetto radice”, un dispositivo all’interno del quale viene eseguito il software, un punto d’accesso al software, o un sottosistema principale;
	- sono tutte varianti di un *facade controller*.
- Rappresenta uno scenario di un caso d’uso all’interno del quale si verifica l’evento di sistema, spesso chiamato \<UseCaseName>Handler, \<UseCaseName>Coordinator, o \<UseCaseName>Session. 
	- Si utilizzi la stessa classe controller per tutti gli eventi di sistema nello stesso scenario di caso d’uso. 
	- Una sessione è un’istanza di una conversazione con un attore. Le sessioni possono avere una lunghezza qualsiasi, ma spesso una sessione corrisponde a un’esecuzione di un caso d’uso (sessioni di caso d’uso).
###### Vantaggi
- **Maggiore potenziale** di **riuso** e interfacce inseribili.
	- L’applicazione di Controller assicura che la logica applicativa non sia gestita nello strato dell’interfaccia o della presentazione. Le responsabilità di un controller potrebbero essere gestite, tecnicamente, in un oggetto dell’interfaccia, ma un tale progetto implicherebbe che il codice del programma e l’esecuzione della logica applicativa sono incorporati negli oggetti dell’interfaccia (nelle finestre). Un progetto “interfaccia come controller” riduce l’opportunità di riusare la logica in altre applicazioni future o tramite altre interfacce (per esempio, un’interfaccia web), poiché la logica che è legata a una particolare interfaccia (per esempio, oggetti di tipo finestra) può essere difficilmente riutilizzata in altre applicazioni. Al contrario, la delega delle responsabilità delle operazioni di sistema a un controller favorisce il riuso della logica in altre applicazioni future. E dal momento che la logica applicativa non è legata allo strato dell’interfaccia, è possibile anche utilizzarla con un’interfaccia diversa.
- Opportunità di **ragionare sullo stato del caso d’uso**.
	- A volte è necessario assicurarsi che le operazioni di sistema si susseguano in una sequenza legale, oppure si desidera poter ragionare sullo stato corrente dell’attività e delle operazioni all’interno del caso d’uso in corso di esecuzione. Per esempio, se bisogna garantire che l’operazione makeCashPayment non possa essere eseguita fino a che non è stata eseguita l’operazione endItemEntry, oppure se bisogna ricordare la Sale corrente per tutta l’esecuzione del caso d’uso (sessione). In questo caso, occorre catturare da qualche parte queste informazioni sullo stato del caso d’uso o della sessione; il controller è una scelta ragionevole, soprattutto se lo stesso controller è utilizzato per l’intero caso d’uso (come consigliato).
###### Problemi e soluzioni
Se progettata in modo mediocre, una classe controller può avere una **coesione bassa**, si parla quindi di **controller gonfi**, che ha le seguenti caratteristiche

- Nel sistema c’è un’**unica classe controller** che riceve tutti gli eventi di sistema.
	- Ciò avviene talvolta quando viene scelto un facade controller. 
- Il **controller** stesso **svolge molti** dei **compiti** necessari **per soddisfare l’evento** di sistema, senza delegare il lavoro.
	- Ciò solitamente coinvolge una violazione di Information Expert e High Cohesion.
- Un controller ha numerosi attributi, e conserva informazioni significative sul sistema o sul dominio, che avrebbero dovuto essere distribuite ad altri oggetti, oppure duplica informazioni trovate altrove

Tra i rimedi per un controller gonfio, due sono i seguenti. 
1. **Progettare** il **controller** in modo tale che esso, in primo luogo, **deleghi** la **soddisfazione** della **responsabilità** di ciascuna operazione di sistema agli altri oggetti. 
2. **Aggiungere più controller**

Si ricorda inoltre che non é respossabilitá dell'UI il portare a compimento l'operazione richiesta. Utilizzando un controller si ottiene una maggiore riusabilitá.


> No, non mi sono dimenticato gli altri 4, non sono stati trattati

