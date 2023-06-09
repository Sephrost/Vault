## Modelli di dominio
Un **modello di dominio** è una **rappresentazione visuale** di **classi** concettuali o di oggetti del mondo reale e delle **relazioni** tra di essi in un dominio di interesse, mostrando un'astrazione del dominio di innteresse.
Può essere realizzato come **uno** o **più diagrammi delle classi** in cui non sono definite operazioni e adottando un punto di vista concettuale.

> É il modello piú importante dell'analisi ad oggetti.
> Non necessita di un grande sforzo di modellazione, bisogna evitare l'approccio a cascata.

### Elementi del modello di dominio
Un modello di dominio può mostrare i seguenti elementi:
- classi concettuali od **oggetti** di **dominio**.
	- rappresentano un insieme di cose o oggetti con caratteristiche simili
- **associazioni**, o *collegamenti*, tra classi concettuali.
	- una relazione fra istanze di classi concettuali, indicante una connessione significativa
- **attributi** di classi concettuali.
	- una proprietà elementare, o *valore logico*, degli oggetti di una classe.

![[Pasted image 20230608230310.png|500]]

### Creare un modello di dominio
É possibile creare un modello di dominio affrontando i seguenti passi:
1. Trovare le classi concettuali.
2. Disegnarle come classi in un diagramma delle classi UML.
3. Aggiungere associazioni e attributi.

#### Trovare le classi concettuali
Una **classe concettuale** rappresenta un **concetto** del mondo reale o nel dominio di interesse.

> Le classi concettuali non sono classi software.

Per individuarle é possibile usare 3 strategie.

##### Strategia 1: Riusare o modificare dei modelli esistenti
É l'approccio piú facile dal quale iniziare, nonché un'ottimo metodo.
> Non hanno detto altro a lezione

##### Strategia 2: Identificare nomi e locuzioni nominali
È basata sull’**identificazione** di **nomi** e di **locuzioni nominali** (ovvero, di frasi formate da un nome principale insieme ai suoi aggettivi e determinanti) nelle descrizioni testuali di un dominio.

Questi vengono poi considerati possibili classi concettuali o attributi.

Questo metodo non é banale da utilizzare, poiché il linguaggio naturale é ambiguo, e infatti non ;e possibile trovare una corrispondenza meccanica tra nomi e classi.

##### Strategia 3: Utilizzare un elenco di categorie comuni
Una tecnica migliore della precedente consiste nell’identificare un elenco di classi concettuali candidate **basandosi** su un **elenco** di **categorie comuni** di classi concettuali.

##### Utilizzare i termini del dominio
Un aspetto importante della modellazione di dominio riguarda l’assegnazione dei nomi agli elementi del modello. 
Nel modello **VANNO** utilizzati **nomi significativi**, propri del dominio, che rivelano (anziché offuscare) il significato o l’intenzione dei diversi elementi.
Questi di solito sono al **singolare**.

##### Classi descrizioni
Una **classe descrizione** sono classi contenti informazioni che descrivono qualcos’altro.
Possono essere utilizzati per mantenere informazioni che andrebbero altrimenti perse con la cancellazione di un classe.
![[Pasted image 20230419222959.png|500]]

Puó essere necessario aggiungere una classe descrizione nei seguenti casi:
- Quando è necessaria una **descrizione** di **classi** concettuali **indipendentemente** dalla loro **esistenza**.
- Quando l’**eliminazione** delle istanze degli oggetti che descrivono causerebbe una **perdita** di **informazioni** che é invece **necessario conservare**, ma che sono state erroneamente associate all’oggetto eliminato.
- Quando si vogliono **ridurre** le informazioni **ridondanti**.


![[Pasted image 20230419192600.png|500]]

##### Generalizzazioni
La **generalizzazione** è un’**astrazione** basata sull’**identificazione** di **caratteristiche comuni** tra classi concettuali.
Essa porta a definire una relazione tra
- una **superclasse**, ovvero un concetto piú generale
- una **sottoclasse**, ovvero un conceto piú specifico

> Una sottoclasse deve essere **completamente compatibile** con una superclasse, ma puó contenere caratteristiche aggiuntive.

![[Pasted image 20230420123521.png]]

Tutti i membri dell'insieme di una sottoclasse concettuale sono membri dell'insieme della corrispondente superclasse.

Una potenziale sottoclasse deve essere conforme a: 
- Regola del **100%** (conformità della definizione) 
	- Il **100%** delle **definizioni**(attributi e associazioni) della **superclasse** concettuale sono **applicabili** alla **sottoclasse**
- Regola **Is-a** (conformità dell’appartenenza insiemistica).
	- Tutti i membri dell’insieme di una sottoclasse devono essere membri dell’insieme della relativa superclasse


#### Trovare le associazioni
Un’**associazione** rappresenta una **relazione** tra due o più **classi** che indica una connessione significativa tra le istanze di quelle classi.

Le associazioni che è **utile mostrare** sono solitamente quelle che **implicano** la conoscenza di una **relazione** che deve essere **memorizzata** per una certa **durata** di **tempo**.

> tra quali oggetti è necessaria una certa memoria di una relazione?

È bene evitare di inserire troppe associazioni in un modello di dominio, e ricordare solo quelle importanti, poiché quelle in eccesso possono rendere meno leggibile il digaramma.

Un’associazione è rappresentata da una **linea** che **collega** le classi partecipanti.

![[Pasted image 20230419224206.png|500]]

> La freccia della direzione di lettura non ha significato in termini di modello, aiuta solo nella lettura del modello.

##### Nomi delle associazioni
Il **nome** di un’associazione ha l’**iniziale maiuscola**, poiché, in UML, un’associazione rappresenta un **classificatore** di **collegamenti** tra istanze, e questi devono iniziare con una lettera maiuscola.

I due formati validi sono quindi:
- Upper camel case (*NomeVariabile*)
- Kebab Case (*Nome-Variabile*)

##### Molteplicitá di un'associazione
La **molteplicità** di un ruolo definisce **quante istanze** di una classe possono essere **associate** a **un’istanza** di un’**altra classe**. 

Queste sono correlate da un valore, che comunica quante istanze possono essere asscciato a un'altra.

![[Pasted image 20230608231356.png|450]]

> In un diagramma delle classi UML, è possibile che due classi siano collegate da più di un’associazione.

![[Pasted image 20230608231425.png]]

Talvolta è utile mostrare il **nome** dei **ruoli** di un’associazione, che identifica un’estremità di associazione e descrive idealmente il ruolo svolto dagli oggetti nell’associazione. Puó essere utile soprattutto quando il ruolo di un'oggetto non é chiaro. Questo inizia sempre con una lettera minuscola.

![[Pasted image 20230608231447.png]]

> Una classe può avere anche un’**associazione** con **se stessa**(*riflessiva*).

![[Pasted image 20230608231502.png|300]]

##### Aggregazione e composizione
L’**aggregazione** è, in UML, un tipo di **associazione** che suggerisce, in modo vago e approssimativo, una **relazione intero-parte**(es: automobile-ruote)

>Seguendo il consiglio dei creatori di UML, non ci si scomodi a usare l’aggregazione in UML; piuttosto, si usi la composizione quando è opportuno.

La **composizione** è un tipo **forte** di **aggregazione intero-parte** che implica che:
- ciascuna istanza della parte appartiene a una sola istanza del composto alla volta
- ciascuna parte deve sempre appartenere a un composto
- la vita delle parti è limitata da quella del composto:
	- le parti possono essere create dopo il composto (ma non prima) 
	- possono essere distrutte prima del composto (ma non dopo)

Puó essere utile mostrare una composizione quando:
- c’è un ovvio gruppo fisico o logico intero-parte
- sussiste una dipendenza di creazione-cancellazione della parte dall’intero
- alcune proprietà del composto si propagano alle parti
- le operazioni applicate al composto si propagano alle parti

> Nel dubbio, é meglio tralasciarle

![[Pasted image 20230419225917.png|400]]

#### Trovare gli attributi
Un **attributo** di una classe rappresenta un **valore** degli oggetti di quella classe.
Sono mostrati nella seconda sezione del rettangolo per una classe, con la seguente sintassi:
<p style="text-align:center;">visibility name : type multiplicity = default {property string}</p>
> Gli attributi sono privati, a meno che non venga specificato diversamente.

È possibile usare una molteplicità per indicare la presenza opzionale per un valore, o il numero di oggetti che possono appartenere a un attributo collezione.
Gli **attributi** in un modello di dominio devono **preferibilmente** essere di **tipi di dato**(booleani, stringhe, date, numeri,$\dots$). Inoltre questi sono solitamente immutabili.

![[Pasted image 20230419232355.png|500]]

> Talvolta un attributo può essere calcolato o derivato da altri elementi presenti nel modello di dominio.

> Se nel mondo reale non pensiamo a un concetto X come a un numero, un testo o a un valore di un tipo di dato, allora probabilmente X è una classe concettuale, non un attributo.

> Gli attributi non dovrebbero essere usati per correlare classi concettuali nel modello di dominio. NON esistono chiavi esterne.

###### Quando creare un nuovo tipo di dato
**Rappresentare** nel modello di dominio come una **nuova** classe **tipo di dato** ciò che inizialmente può essere considerato un numero o una stringa se: 
- È composto da sezioni separate;
- Ci sono operazioni a esso associate
- Ha altri attributi
- È una quantità con un’unità di misura
- È un’astrazione di uno o più tipi con alcune di queste qualità

### Esempio di modello di dominio illustrato
![[Pasted image 20230419190715.png]]

