Abbiamo appurato in precedenza che la rete all'esterno della LAN puó essere, e lo é, insicura, e un solo dispositivo manomesso all'interno della rete locale puó avere conseguenze considerevoli sul resto della rete. 
Inoltre le reti non sono state progettate con la sicurezza come prioritá, infatti i router e gli switch indirizzano i pacchetti dall'interno della rete all'esterno in maniera del tutto trasparente, senza applicare filtri, lasciando quindi gli host esposti. 

Ma anziché controllare il traffico da tutti i dispositivi verso l'esterno, e vice versa, é sicuramente piú facile avere un'**unico punto di accesso controllato**.

Il **firewall** è un **dispositivo hardware** che viene installato nelle reti locali per **filtrare** i **pacchetti** che arrivano dall’esterno (ma anche quelli dall’interno verso l’esterno) in modo da **fornire** una **protezione** agli host sulla LAN (e alla rete stessa).
Svolge inoltre una funzione di **log** del **traffico** complessivo e delle **azioni** dei singoli utenti.

![[Pasted image 20230903175444.png]]

### Topologie di firewall
Esistono diverse topologie di reti con firewell, adattabili in base alle esigenze.
#### Screening router
La soluzione più semplice è quella di installare un **router più intelligente** che **effettua** alcune operazioni di **filtro**. 

Questa soluzione é adatta per le **reti domestiche**.
![[Pasted image 20230903180030.png]]
#### Dual homed gateway
Un firewall puó anche essere una macchina Linux. Il router instraderá quindi il traffico al firewall, il quale, dopo l'operazione di filtro, instraderá i pacchetti agli host della sottorete.

Il **firewall** ha quindi **due schede di rete**, una collegata al router e l'altra alla rete interna.
![[Pasted image 20230903181407.png]]
#### Screened host gateway
In questo caso il **firewall** é sempre un componente a sé stante, ma presenta **una sola scheda di rete**: il traffico viene instradato verso il firewall che li instreaderá secondo i suoi criteri.

![[Pasted image 20230904121911.png]]
#### DMZ - De-Militarized Zone
É una **parte** della **rete** dove passa il traffico diretto verso i **servizi pubblici** offerti dall'organizzazione.

Rappresenta quindi un ulteriore livello di sicurezza: un host appartenente ad una rete esterna puó accedere solo ai servizi messi a disposizione, senza quindi mettere a rischio l'intera rete.
#### Screened Subnet
Il **traffico** verso una rete locale viene **instradato** in **maniera differente** in base alla **destinazione**: 
- Se é diretto verso **host esterni alla DMZ**, allora deve essere **filtrato** dal firewall 
- **altrimenti** puó **anche** essere **instradato direttamente** verso i server che forniscono il servizio
##### 1 firewall single homed
Caso 1
![[Pasted image 20230904125903.png|600]]
Caso 2
![[Pasted image 20230904125929.png|600]]
##### 1 firewall dual homed
![[Pasted image 20230904125947.png|600]]
##### 1 firewall 4 interfacce
![[Pasted image 20230904130016.png|600]]
##### Firewall a cascata
![[Pasted image 20230904130636.png|600]]
### High Availability
Le topologie sopra mostrate(ad eccezione dell'ultima) presentano peró un difetto: sono *single-point-of-fail*, ovvero se un solo firewall si rompe alcuni sistemi smettono di funzionare di conseguenza.

Per **ovviare** a questro **difetto**, si collegano piú **firewall a cascata**, che funzionano in parallelo. Questi comunicano costantemente tramite **ping applicativi**, per poter verificare il corretto funzionamento di tutte le macchine.
In questa maniera, se un firewall si rompesse, potrebbe essere sostituito con un'altro.

Questo permette di soddisfare il requisito di **high availability**, che prevede che, anche se una macchina si rompe, il sistema complesso deve continuare a funzionare.
![[Pasted image 20230908192829.png|600]]
### Tipologie di firewall
Non abbiamo un tipo unico di firewall ma a seconda delle esigenze ne abbiamo di tipologie diverse:
- **packet filter**: un router che filtra pacchetti a **livello di rete**
- **application proxy**: un calcolatore attraverso il quale il traffico passa e viene filtrato e registrato a **livello applicativo**
#### Packet filter
É un **router** che lavora a **livello di rete** ma **anche trasporto**.

Esso **filtra** i **paccheti** in base a:
- **Direzione** del **pacchetto** 
- **Direzione** della **connessione TCP** 
- Indirizzo **IP sorgente e destinazione **
- **Porta** sorgente e destinzazione(servizio)

Il **packet filter** è **stateless**, ovvero **non ha memoria** dei pacchetti precedenti, in quanto analizza soltanto l’header IP e TCP.
A causa di ciò,non riesce a prendere decisioni su di un traffico di pacchetti che è legato al traffico precedente: non riesce a contestualizzare la connessione.

La **frammentazione IP** rappresenta un **problema** per il firewall: se un pacchetto viene frammentato in **pezzi** talmente **piccoli** da non contenere nemmeno l’header tcp, allora **possono bypassare** la regola di **filtro** sulle porte. 
Di solito tuttavia i firewall hanno delle regole che scartano a priori dei pacchetti più piccoli di una certa quantità di byte
##### ACL - Access Control List
I firewall hanno al proprio interno una **serie di regole** che vengono **controllate sequenzialmente**, detta Access control List(*ACL*).
Nel caso di **match** di una **regola** per un **pacchetto** questa viene applicata.

Un'esempio di ACL puó essere il seguente

action|protocol|scr_addr|scr_p|dst_addr|dst_p|flags
--|--|--|--|--|--|--
allow|TCP|130.192.239.\*|\*|\*|80| \*
allow|TCP|\*|80|130.192.239.\*|\*|ACK
deny|TCP|\*|\*|\*|\*|\*

che permette il traffico HTTP dalla rete con maschera 130.192.239 verso l'esterno. 

Le regole vengono controllate in ordine sequenziale, in questa maniera é possibile ottenere risultati parecchio sofisticati.
##### Blocco del traffico con Source Routing
Il **source routing** é la possibilitá di **specificare** il **percorso** che un pacchetto deve seguire, in termini di routing.

In caso di **spoofing** su connessione TCP, una attaccante $A$ utilizzerá un'indirizzo falso $IP_s$ per inviare pacchetti ad un host con IP $IP_v$.
Il pacchetto contiene inviato da $A$ contiene quindi il suo numero di sequenza, mentre la risposta conterrá il sumero di sequenza dell'altro host. A causa dell'ip falsificato peró il pacchetto andrá instradato verso $IP_s$ e non il vero indirizzo dell'attaccante, e quindi $A$ non verrá a conoscenza del numero di sequenza corretto, e non potrá comporre nuovi pacchetti.

Ma con il source routing $A$ é in grado di specificare che il pacchetto deve passare per il suo host, ottenendo cosí i dati necessari a concludere l'handshake.

Per questo é importante **bloccare** i pacchetti con l'opzione di source routing.
##### Il problema di FTP
**FTP** é un **protocollo** a **livello applicativo**, che é uno dei motivi per cui vengono usati altri firewall oltre ai packet filter.

Il protocollo ha il seguente funzionamento:
- le **richieste** vengono inviate tramite la **porta 21** 
- i **trasferimenti di file** avvengono sulla **porta 20**
Utilizza quindi **due connessioni differenti**.

![[Pasted image 20230904144120.png|500]]

Dal punto di vista della sicurezza questo puó **generare** dei **problemi**:
per la configurazione della **porta 21 non ci sono problemi**

action|protocol|scr_addr|scr_p|dst_addr|dst_p|flags
--|--|--|--|--|--|--
allow|TCP|130.192.239.0|\*|\*|21|\* 
allow|TCP|\*|21|130.192.239.0|\*|ACK

ma sulla configurazione della **porta 20** sorge il **problema** sul **campo flag**

action|protocol|scr_addr|scr_p|dst_addr|dst_p|flags
--|--|--|--|--|--|--
allow|TCP|130.192.239.0|\*|\*|20|\*
allow|TCP|\*|20|130.192.239.0|\*|?

- se mettiamo **ACK**, allora **FTP non potrá funzionare**, poiché deve aprire una comunicazione sulla porta del client
- **altrimenti** permettiamo l'**avvio** di una **connessione a chiunque** sulla **porta 20** del client

Possiamo quindi:
- vietare FTP, o qualsiasi protocollo custom con funzionamento analogo
- filtro 'application aware'(stateful) :ricorda la porta dati lato client e permette la connessione solo su quella porta e su quell’indirizzo)

> Queste limitazioni del Packet Filter, lo rendono semplice e veloce poiché leggono il pacchetto “on fly” e senza conservare nulla in memoria (stateless) ma che è comunque potente

##### Vantaggi e svantaggi del packet filter
###### Vantaggi
- Nessuna modifica alle applicazioni (**trasparenza**) 
- Economico (realizzato su router) 
- Alte prestazioni
###### Svantaggi
- Difficoltà con alcuni protocolli 
- Non selettivo rispetto agli utenti 
- Non mantiene log 
- Difficile monitorare gli attacchi mentre avvengono
#### Firewall di livello applicativo
I **firewall applicativi** lavorano a livello applicativo e quindi sono in grado di **leggere** tutto il **pacchetto** e di estrapolare informazioni utili allo scopo del firewall. 

Vi sono **tre tipologie** di firewall applicativi.
##### Proxy Applicativo
É un **firewall** che funge da **proxy** per l'esterno per i pacchetti della sottorete.

Un client che vuole instaurare una connessione verso l'esterno la instaura attraverso il proxy, che dialogherá con il server esterno.

Ogni **connessione** quindi viene **sdoppiata**:
- una dal client al proxy
- una dal proxy al server

Il proxy mantiene quindi una **tabella** contenente le **corrispondenze** **porta** del **client**/ **porta** del **proxy**, cosí da poter poi instradare i pacchetti verso il client(in maniera simile al NAT).

Tutto il traffico che non passa per il firewall dovrà essere bloccato.
##### Vantaggi e svantaggi
###### Vantaggi
- Non trasparente
- Richiede un host dedicato 
- Prestazioni medie
###### Svantaggi
- Sicuro
- É in grado di riferire il traffico agli utenti
- Mantiene log sofisticati
##### Packet filter application aware
I **packet filter application aware** sono una sorta di **packet filter particolarmente avanzati** che sono in grado di **implementare** alcune **funzionalità** relative alle **connessioni**. 

Ad esempio possono gestire ftp ma mancano ancora del concetto di utenza.
##### Transparent proxy
Si vuole ovviare al problema riscontrato con il proxy applicativo.
Disponiamo di un firewall che svolge anche le funzioni di un router ovvero è in grado di instradare i pacchetti.
A questo punto, quando A invia un pacchetto non lo invierà indicando il MAC del router bensì il MAC del firewall (ma lasciando inalterato l’IP del destinatario, così da non dover impostare il proxy per ogni browser della rete).
#### Firewall personali
Sono i firewall istallati dal suingolo utente sulla propria macchina.

Rimane comunque utile installare un firewall sulla propria macchina poiché permette di avere una protezione direttamente “in loco” e quindi da qualsiasi connessione la macchina usi.

