# Sistema informativo
Con *sistema informativo* si intendono tutti gli **strumenti**,tecnologici e non, attraverso cui si gestisce l'**acquisizione** e l'**elaborazione** delle **informazioni aziendali**.

L'obiettivo del SI é diffondere conoscenza all'interno di un' organizzazione, presentando l'informazione in maniera utile.

$$Sistema\; Informativo\ne Sistema\;informatico\;\|\; Sistema Informatico\subset Sistema\;informativo$$
### Definizioni utili
##### Dato
Un dato é un **fatto** grezzo non scomponibile(*elementare*)
##### Informazione
Un'informazione é un dato corredato dal contesto.

É la **risorsa fondamentale** per il funzionamento di un'organizzazione, indispensabile per pianificare, controllare, documentare, valutare
le attività che si svolgono all’interno.

Una **buona informazione** deve essere
- Accurata
- Tempestiva
	- Arriva in un tempo utile al processo decisivo
- Rilevante
- "Just Sufficient"
	- Ne' troppa ne' troppo poca
- Merita il suo costo
	- Il costo deve bilanciare la significabilita' dell'informazione
###### Conoscenza
Una conoscenza é l'uso che si fá di un'informazione
###### Codifica
La codifica é la rappresentazione di un dato (es: binaria)
## Viste 
Tre viste rappresentano le tre dimensioni fondamentali per l’analisi di un SI:
- organizzativa (chi)
- funzionale (cosa)
- tecnologica (IT) (come)

![[Pasted image 20220924174917.png|center]]
### Modello Informatico
Descrive come il Sistema Informativo é realizzato.
All'interno di questo modello é possibile distinguere:
- Modello applicativo
- Modello tecnologico
![[Pasted image 20220927163322.png|350]]
#### Modello Applicativo
I software operativi che costituiscono il SI sono articolati su 3 strati fondamentali

![[Pasted image 20220927162204.png|350|center]]
Questi livelli sono strettamente interconessi.
##### Presentation Layer(Strato di Presentazione)
É Rappresentata dalla GUI (*Graphical User Interface*) dell'applicazione.

É finalizzata a una navigazione articolata sui dati.
##### Business Layer (Logica Applicativa)
É costituita dalle procedure secondo le quali il SI elabora i dati immessi attraverso il *Presentation Layer* 
##### Database(Strato dei Dati)
Fornisce gli strumenti per
- Strutturare le basi di dati
- Accedere alle Basi di Dati
#### Modello tecnologico
É formato da
- un'architettura di elaborazione
	- Hardware che esegue l'elaborazione di presentazione, logica applicativa e gestione dei dati
- un'architettura di rete
	- interconnessione fra i sistemi hw anche che di organizzazioni distinte
##### Architettura di Elaborazione
Specifica i ruoli con cui i sistemi hardware interagiscono al fine di compiere elaborazioni, deve essere quindi ingrado di far interagire i 3 livelli del modello applicativo.

Ci sono tre possibile architetture:
- Mainframe
- Client-Server
- Peer-to-Peer

L'architettura di elaborazione piú diffusa é l'architettura **client-server**, affermatasi negli anni novanta. Le comunicazioni tra client e server avvengono attraverso uno scambio di messaggi.

Con questa architettura é possibile suddividwere il carico di elaborazione nella maniera che si ritiene piú opportuna, ripartendo i layer tra i client e i server.

![[Pasted image 20220927172022.png]]
###### Client Server Two-Tier vs Three-Tier
![[Pasted image 20220927171832.png]]
###### Requisiti di un'architettura di elaborazione
Una rete di elaborazione deve garantire alcuni requisiti fondamentali:
- deva avere un tempo di risposta(pressione tasto->visualizzazione risposta) dell'ordine dei 2 secondi
- deve esserew scalabile
- deve essere disponibile quando necessario

##### Architettura di Rete
L'architettura di rete determina come i sistemi hardware sono connessi e interagiscono tra di loro.

Le reti possono essere classificate secondo diverse prospettive:
- Estensione fisica
	- Lan(Local Area network)
	- Man(Metropolitan Area Network)
	- Wan(Wide Area Nwetwork)
- Modalitá di Funzionamento
	- Internet
	- Intranet
	- Extranet
 
### Modello Funzionale
Il modello funzionale descrive nel dettaglio le esigenze gestionali di elaborazione dell'informazione a cui rispondono i SI.

Definisce cosa il SI deve fare, a prescindere dalla sua implementazione informatica.

Il modello integra diverse prospettive.
#### Modello per casi d'uso
> Viene utilizzato per analizzare i requisiti utente al fine di definire il contenuto funzionale delle elaborazioni

Il modello per casi d'uso descrive le elaborazioni compiute dal SI da diversi punti di vista attraverso il diagramma dei casi d'uso.
Viene quindi utilizzato per esprimere i casi d'uso individuali e le relazioni tra di essi, al fine di modellare i requisiti aziendali in base ad essi.

Una volta individuati i casi d'uso é possibile metterli in relazione con le attivitá del processo attraverso il diagramma delle linee di montaggio.
#### Modello dei Processi
> Un processo gestionale puó essere descritto copme un flusso di attivitá svolte da una o piú organizzazioni usando delle risorse s oggeti fisici o informativi per produrre prodotti o servizi.

Il modello per processi descrive per ciascuna procedura il proprio flusso di attivitá aziendali, permettendo di classificare i processi in base ad una serie di punti di vista(rilevanti per il SI):
- Complessitá
	- Rispetto al numero delle attivitá
	- Rispetto alle relazioni fra le attivitá
- Locazione
- Materialitá degli oggetti
#### Modello dei Dati
Definisce i contenuti della base di dati.
### Modello Organizzativo
