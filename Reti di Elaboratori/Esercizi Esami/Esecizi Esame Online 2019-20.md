### Domanda 1
Un Access Point invia frame beacon ogni 150ms. Un host associato a questo AP impiega 500 microsecondi per attivare la propria interfaccia WiFi, e un millisecondo per ricevere un frame beacon. Se l’host non ha dati da trasmettere/ricevere, quale frazione di energia, in percentuale, può essere risparmiata utilizzando la modalità di risparmio energetico, rispetto al caso in cui non la si adotti?

### Domanda 2
TCP e finestra per il controllo di flusso. 
Si assuma che la figura evidenzi lo stato della finestra di controllo di flusso di TCP. Specificare il significato dei tre puntatori che TCP utilizza per gestire la finestra. Cosa rappresentano e come vengono gestiti? In particolare, quali sono gli eventi che incrementano i tre contatori (quello di sinistra, quello centrale, e quello a destra)?
![[Pasted image 20230627170416.png|500]]
#### Risposta
A partire da sinistra, i 3 contatori rappresentano:
- la variabile **send base**, utilizzata per identificare il pacchetto con numero di sequenza piú basso di cui non si é ancora ricevuto l'acknowledgement
- la variable next-seq-num, che indica i numeri numeri di sequenza utilizzabili(quelli nell'intervallo tra il secondo e il terzo puntatore)
- L'ultimo puntatore é send base + l'ampiezza della finestra(N), usata per delimitare il numero di pacchetti massimo inviati di cui si aspetta l'ACK
Queste variabili vengono utilizzate per implementare il pipelining in TCP.

Quando si riceve l'ack del pacchetto indicato da send base, significa che il pacchetto piú vecchio "in flight" é stato ricevuto correttamente e é quidni possbile fare slittare la finestra, incrementado il il primo e l'ultimo puntatore.
Quando si vuole inviare un pacchetto nuovo, se il next-seq-num é minore dell'ultimo, allora lo invia e incrementa il puntatore, altrimenti dovrá aspettare prima di essere inviato.


### Domanda 3
TCP e gestione della congestione: supponete che l’evoluzione della finestra di un TCP lato mittente sia evidenziata dal seguente diagramma
![[Pasted image 20230627170445.png|500]]
Spiegare quali sono i fenomeni che si sono verificati in corrispondenza dei round evidenziati dalle etichette A, B, C e  D (dovete fornire 4 risposte!).

#### Risposta
1. Fino al punto A, la sessione TCP si trova nella fase Slow Start, nella quale cerca di scoprire la larghezza di banda disponibile in maniera veloce, incrementando in maniera esponensziale la variabile cwnd, inizializzata a 1 MSS
2. Tra il punto a e il punto B, il valore di cwnd ha raggiunto il valore di sstresh, entrando nella fase di congestion avoidance. Al punto B si verifica un'evento di perdita, si pone sstresh=cwnd/2 e cwnd a 1MSS e si rientra nella fase di slow start
3. Al punto 4 cwnd ha raggiunto o superato il valore sstresh e rientra nella fase di congestion avoidance

### Domanda 4
Descrivete i principi e il funzionamento del protocollo ARP.
#### Risposta
ARP, o Address Resolution Protocol, é un protocollo a livello applicativo utilizzato per la traduzione di indirizzi IP a livello di rete in indirizzi MAC a livello di collegamento. Senza  di esso non sarebbe possibile conoscere l'indirizzo dell'interfaccia di rete verso la quale instradare il frame.

ARP funziona nella seguente maniera:
- Ogni scheda mantiene di memoria una tabella ARP, che associa un indirizzo IP ad un indirizzo MAC
- Quando una scheda riceve dal livello di rete un datagramma, questa controlla se é presente l'entry corrispondente all'indirizzo di destinazione
	- Se é presente, allora effettua l'incapsulamento e pone l'indirizzo MAC della entry 
	- Altrimenti, per conoscere l'indirizzo di destinazione invia un messaggio ARP in brodcast nella sottorete, e riceverá risposta dall'host con l'indirizzo MAC richiesto
	- Nel caso l'indirizzo IP non faccia parte della sottorete, allora verra instradato verso il router per poterlo instradare verso il router di gateway sella sottorete di destinazione, che eventualmente risponderá al router
- Se si ricever una risposta ARP, si inserisce inoltre la risposta nella tabella, con un TTL

### Domanda 5
Descrivere sinteticamente come lo standard 802.1Q permette di realizzare Virtual Local Area Networks (VLANs)

### Domanda 6
Un nodo su Ethernet a 10 Mbit/s, dopo aver subito molteplici collisioni, estrae il valore $K=5$. Dopo quanto tempo, in microsecondi, proverà a ritrasmettere sul canale?
#### Risposta
> Suppongo si parli di CSMA/CD

Il tempo di attesa é il tempo necessario a inviare 512 bit k volte, quindi 
$5\times(\frac{512}{10^7})=256\mu sec$.

### Domanda 7
Protocollo ICMP e controllo della congestione.
Articolare la risposta rispondendo ai seguenti punti.

1. Quali sono le possibili cause della congestione.
2. In quali casi ICMP può aiutare a risolvere/mitigare problemi di congestione?
3. Con quale messaggio ICMP collabora alla gestione della congestione?
#### Risposta
1. Le possibile cause della congestione sono una larghezza di banda insufficiente a supportare le connessioni e accodamento nei buffer.


### Domanda 8
Considerate la rete della figura seguente.
![[Pasted image 20230627170630.png|500]]
1. Supponete che i datagrammi tra A e D siano instradati tramite il router R3, mentre quelli tra B e C tramite il router R4. Quale è il throughput massimo teorico fra A e D e quello fra B e C?
2. Supponete ora che A e B siano client e C e D siano server. Supponete che A invii richieste a D di lunghezza pari a 3 KB e riceva risposte pari a 3 KB, e altrettanto faccia B con C. Quale è il ritardo minimo dovuto alla latenza di rete con cui i client ricevono la risposta, supponendo trascurabili la lunghezza dei link, il tempo di attesa in coda sui router e il tempo di elaborazione dei router e dei server?  
#### Risposta
1. Il troughput massimo tra A e D é 1Mbps, lo stesso tra B e C.
2. Ignorando il ridardo di elaborazione, accodamento e trasmissione siano ininfluenti, il ritardo end-to-end é dettato solo dal delay di trasmissione, quindi $d_{trasm}A\to D=(\frac{24000}{1,5\times 10^6}+\frac{24000}{3/2\times 10^6}+\frac{24000}{10^6}+\frac{24000}{2\times 10^6}\times 2)\times 2=0,08\times 2=0,16$  

### Domanda 9
Nello scenario descritto nella figura seguente, in cui sono presenti due reti, una 130.192.22.X (quella di sinistra) e l'altra 150.0.0.X (di destra) che comunicano mediante un router. Per ciascuno degli host (e per il router) sono riportati sia gli indirizzi IP e sia gli indirizzi MAC.
Si consideri l'invio di un datagram IP da parte dell'host con indirizzo 150.0.0.5 verso l'host con indirizzo 130.192.22.20. Nella figura vengono evidenziati i due fame generati (che incapsulano il datagram) da tale evento (uno etichettato con **A** e l'altro **B**).

![[Pasted image 20230627170712.png|500]]
Facendo riferimento al frame etichettato come frame **A** (ripeto solo al frame **A**) e al datagram incapsulato in tale frame, rispondere alle seguenti domande:  
1. Source MAC address (del frame A)
2. Destination MAC address (del frame A)
3. Source IP address (del datagram incapsulato nel frame A)
4. Destination IP address (del datagram incapsulato nel frame A)
#### Risposta
1. 01:CA:D3:E1:0E:9A
2. 1C:03:4E:E5:2E:0A
3. 150.0.0.5
4. 130.192.22.20

### Domanda 10
![[Pasted image 20230627170735.png]]
Si consideri la rete mostrata in figura, dove inizialmente le cache ARP di tutti i nodi sono vuote. Si supponga che l’host con indirizzo IP 111.111.111.111 invii un pacchetto IP all’host 222.222.222.222. 
Descrivere il contenuto delle cache ARP di tutti i nodi al termine di questa comunicazione, sotto forma di entry (indirizzo IP, indirizzo MAC)
#### Risposta
###### 111.111.111.111

IP|MAC
--|--
111.111.111.110|E6-E9-00-17-BB-4D
###### 111.111.111.110

IP|MAC
--|--
111.111.111.111|74-29-E8-FF-55

###### 222.222.222.220

IP|MAC
--|--
111.111.111.110|E6-E9-00-17-BB-4B

###### 222.222.222.222

IP|MAC
--|--
222.222.222.220|1A-23-F9-CD-06-9B

111.111.111.112 e 222.222.222.221 contengono solo l'entry con il corrispettivo router

### Domanda 11
Supponete di dover trasmettere i bit 101001, e di usare un CRC con generatore 1110. Quali sono i bit trasmessi sul canale?
#### Risposta
101001100

### Domanda 12
DNS: risoluzione iterativa dei nomi.  
Supponete che in uno scenario descritto dalla figura seguente
![[Pasted image 20230627170816.png|500]]
l'host _cis.poly.edu_ debba contattare l'host _gaia.cs.umass.edu_ e per questo necessita dell'indirizzo IP di quest'ultimo. Questo indirizzo può essere ottenuto effettuando una query di tipo A al DNS. Assumere che la query sia effettuata usando la modalità iterativa (secondo lo schema descritto nella figura).

Rispondere alle **due** domande seguenti:  

1. Quale è la query che il _local DNS_ invia al _TLD DNS server_ e che risposta riceve (frecce etichettate come 4 e 5 nella figura)?
2. Quali sono gli host/server che, per effetto della query, apprendono l'associazione (nome=_gaia.cs.umass.edu_, _indirizzo_IP_di___gaia.cs.umass.edu_)?

### Domanda 13
**Dijkstra's Link State Algorithm (per il calcolo dei cammini di costo minimo)**

Si consideri la rete con sei nodi con relativi costi di attraversamento dei link, mostrata in figura. Rispondere alle **due** domande seguenti (inserendo le risposte nella casella di testo sottostante)
![[Pasted image 20230627170858.png|500]]
1. Utilizzando l'algoritmo di Dijkstra, trovare il cammino di costo minimo dal nodo sorgente u verso tutte le altre destinazioni (Nota: Descrivere la risposta specificando l'albero dei cammini minimi. Es. u-to-_node i1_, u-to-_node i2_, _node i1_-to-_node i3_, ..., ...)
2. Specificare la tabella di next-hop per il nodo (Nota: Descrivere la risposta specificando la tabella di next hop in questo modo con delle triple con il seguente significato "_u, destination_node, next_hop_node_")
#### Risposte

Node|Cost|Path
--|--|--
v|1|$u\to v$
x|7|$u\to v\to x$
w|5|$u\to w$
y|9|$u\to w\to y$
z|12|$u\to w \to y\to z$

Partenza|Destinazione|Next Hop
--|--|--
u|v|v
u|x|v
u|w|w
u|y|w
u|z|w

### Domanda 14
Quali di queste affermazioni sono vere?

Scegli una o più alternative:
- [ ] La rete conosce ad ogni istante la cella in cui si trova l’utente mobile
- [ ] L’anchor MSC viene attraversato dal traffico diretto verso un utente che si sposta sotto un’altro MSC
- [ ] Nelle reti cellulari si utilizza la modalità di instradamento indiretta
- [ ] Il Visitor Location Register (VLR) viene aggiornato quando il dispositivo di un utente abbonato viene acceso
- [ ] L’Home Location Register (HLR) non conosce l’MSC che gestisce attualmente l’utente mobile

### Domanda 15
Indirizzi di rete speciali. 
Spiegare quando si utilizzano (e perché) i seguenti indirizzi speciali:
1. indirizzo di 32 bit uguali a zero:
2. indirizzo di 32 bit uguali a uno;
3. indirizzo diviso in due parti (netid, hostid) con la parte di hostid con tutti bit uguali a zero;
4. indirizzo diviso in due parti (netid, hostid) con la parte di hostid con tutti bit uguali a uno;
5. indizizzo del del tipo 127.0.0.1 (o 127.x.y.z).
#### Risposta
1. Si puó utilizzare nei messaggi DHCP, specificia che un'host non ha indirizzo IP
2. Indirizzo di brodcast
3. Si utilizzano per identificare una maschera di sottorete, che identifica la sottorete, e indica che tutti gli indirizzi con prefisso net-id fanno parte della sottorete
4. 