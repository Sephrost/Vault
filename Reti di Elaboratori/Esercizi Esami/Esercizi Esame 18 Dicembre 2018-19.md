### Domanda 1
Protocollo IP e frammentazione.
![[Pasted image 20230627201238.png|500]]
Articolare la risposta rispondendo ai seguenti punti. 
1. Spiegare brevemente (8/9 righe al massimo) la tecnica della frammentazione dei datagram IP elencando i campi del datagram coinvolti. 
2. Nell'ipotesi che il datagram, originato da un host collegato ad una rete con MTU uguale a 1500 Byte, debba attraversare una rete con MTU uguale a 800 Byte determinare la dimensione dei frammenti e specificare il contenuto dei campi OFFSET, TOTAL LENGHT e FLAG per ciascuno dei segmenti prodotti (avvertenza: ricordatevi della lunghezza dell'header, sia dei segmenti che del datagram originale).
#### Risposta
Poiché il un datagramma deve avere dimensione inferiore alla MTU del collegamento, se il pacchetto presenta dimensione maggiori é necessario frammentarlo in datagrammi piú piccoli, per poi essere riassemblati dall'host di destinazione. I campi utilizzati a questo scopo sono:
- identification: identificatore di un datagramma nello stream, se piú segmenti hanno lo stesso identificatore fanno parte dello stesso datagramma
- flag: utilizzato segnalare la fine dei frammenti, viene posto a zero sull'ultimo, mentre sugli altri é posto ad uno
- fragment offset: serve a ordinere i frammenti per potergli riassemblare nel datagramma originale

Se un datagramma partito da un colelgamento ethernet deve attraversare un collegamento con MTU 800 byte allora bisogna suddividere il payload in due datagrammi, supponendo quindi una lunghezza dell'intestazione di 20 byte il primo pacchetto avrá un campo data di dimensione totale 800 byte mentre il secondo 720 

OFFSET|TOTAL LENGTH|FLAG
--|--|--
0|800|1
1|720|0

### Domanda 2
Si consideri lo scenario illustrato nella figura sottostante dove due reti (una con indirizzo di rete 10.0.0.X/24 e l’altra con indirizzo di rete 130.192.22.X/24) sono collegate mediante un gateway che ha come indirizzi 10.0.0.1 e 130.192.22.1. 
Assumere che: 
- tutti gli host della rete 10.0.0.X/24 hanno come default gateway 10.0.0.1 mentre gli host della rete hanno come default gateway 130.192.22.1;
- tutti gli host in entrambe le reti hanno comunicato precedentemente con vari host/gateway e quindi hanno nella rispettive cache ARP tutte i binding necessari (in altre parole non è necessario richiamare il protocollo ARP)
![[Pasted image 20230627201318.png|500]]

Completare i frame/datagram con le informazioni relative agli indirizzi mittente/destinatario MACAddress/IP-Address per i seguenti casi:
1. si assuma che l’host con indirizzo 10.0.0.4 mandi un datagram all’host 10.0.0.5 e che l’host 10.0.0.5 risponda con un altro datagram.
2. si assuma che l’host con indirizzo 10.0.0.4 mandi un datagram all’host 130.192.22.20 e che l’host 130.192.22.20 risponda con un altro datagram.

#### Risposta

Messaggio|Source Mac|Destination Mac|Source IP|Destination IP
--|--|--|--|--
10.0.0.4 $\to$ 10.0.0.5|AB:C0:DE:A1:00:8B|01:CA:D3:E1:0E:9A|10.0.0.4|10.0.0.5
10.0.0.5 $\to$ 10.0.0.4|01:CA:D3:E1:0E:9A|AB:C0:DE:A1:00:8B|10.0.0.5|10.0.0.4
10.0.0.4 $\to$ 10.0.0.1|AB:C0:DE:A1:00:8B|1C:03:4E:E5:2E:0A|10.0.0.4|130.192.22.20 
130.192.22.1 $\to$ 130.192.22.20|AE:12:3E:5D:0D:4A|0A:A4:0E:E8:A7:40|10.0.0.4|130.192.22.20
130.192.22.20 $\to$ 130.192.22.1|0A:A4:0E:E8:A7:40|AE:12:3E:5D:0D:4A|130.192.22.20|10.0.0.4
10.0.0.1 $\to$ 10.0.0.4|1C:03:4E:E5:2E:0A|AB:C0:DE:A1:00:8B|130.192.22.20|10.0.0.4

### Domanda 3
La figura schematizza uno scenario in cui sull’host con indirizzo 128.10.2.3 sono in esecuzione un server http (registrato sulla porta 80) e un server ftp (registrato sulla porta 21) e da un host con indirizzo 130.190.1.5 vengono eseguiti due client http ed un client ftp che richiedono servizi ai server in esecuzione sull’host 128.10.2.3. 
Specificare le informazioni Indirizzi-locali/Indirizzi-remoti e Portalocale/porta-remota per ognuna delle tre istanze di client in esecuzione sull’host 130.190.1.5?
![[Pasted image 20230627201445.png|500]]
#### Risposta
Prima connessione 
- Local IP: 130.190.1.5
- Local Port: 10000
- Remote Ip: 128.10.2.3
- Remote Port: 80
Seconda connessione 
- Local IP: 130.190.1.5
- Local Port: 10001
- Remote Ip: 128.10.2.3
- Remote Port: 80
Terza Connessione
- Local IP: 130.190.1.5
- Local Port: 10002
- Remote Ip: 128.10.2.3
- Remote Port: 21
### Domanda 4
Facendo riferimento allo scenario delineato nella seguente figura, illustrate il funzionamento di un router che implementala funzione di NAT.
![[Pasted image 20230627231757.png|500]]
Nella figura sono indicati gli indirizzi degli host sulla rete locale e i due indirizzi del router, quello sulla rete locale e quello sulla rete pubblica (indirizzo 138.76.29.7).
In particolare, fare riferimento alla sequenza di eventi 
1. l’host con indirizzo 10.0.0.1 invia un pacchetto di livello transport (es. un segmento TCP) ad un’applicazione in esecuzione sull’host con indirizzo 128.119.40.186 (esterno alla rete) porta 80, 
2. l’applicazione identificata dalla coppia 128.119.40.186 / porta 80 invia una risposta all’host mittente. 

Rispondere ai seguenti quesiti: 
1. Specificare gli indirizzi mittente e destinatario e le porte locale e remota relativamente al pacchetto TCP (e datagram IP) che viene spedito dall’host 10.0.0.1. 
2. Quale è il primo hop del pacchetto? 
3. Come viene “riscritto” dal router NAT il pacchetto? 
4. Cosa viene riportato nella tabella del NAT? 
5. Specificare gli indirizzi mittente e destinatario e le porte locale e remota relativamente al pacchetto TCP di risposta (e datagram IP) che viene inviato dall’host 128.119.40.186. 
6. Come viene riscritto dal router NAT tale pacchetto di risposta?
#### Risposte
1. Dati
	1. Indirizzo mittente: 10.0.0.1
	2. Porta mittente: 10000
	3. Indirizzo Destinatario: 128.119.40.186
	4. Porta Destinatario: 80
2. Il pacchetto viene instradato verso il router
3. Sovrascrive l'indirizzo di origine con il suo e la porta di origine con una nuova appena generata
4.  Inserisce nella colonna Indirizzo lato WAN l'entry "138.76.29.7,3000" e nella colonna indirizzo lato LAN "10.0.0.1:10000"
5. Dati
	1. Indirizzo mittente: 128.119.40.186
	2. Porta mittente: 80
	3. Indirizzo Destinatario: 138.76.29.7
	4. Porta Destinatario: 3000
6. Il router sostituisce l'indirizzo di destinazione con quello riportato nella seconda colonna della entry, cosí come la porta di destinazione

### Domanda 5
TCP e gestione della congestione: 
- In cosa consiste la fase di Congestion Avoidance di TCP? 
- Quali sono gli eventi che portano TCP in questa fase e quali quelli che fanno uscire TCP da questa fase?

La fase di congestion avoidance una fase di gestione della congestione nella quale dsi puó trovare una connessione TCP. Poiché la connessione é giá uscita per la prima volta dalla fase di slow start, anziché incrementare in maniera esponenziale la congestion window si attua un'incremento piu conservativo.
Si esce da questa fase in due casi
- timeout, riportando la connessione nella fase di slow start, portando la cwnd a 1 MSS e impostando sstresh a cwnd/2 
- se si utilizza TCP reno e si ricevono 3 ack duplicati, entrando nella fase di fast recovery, impostando cwnd a sstresh+3MSS e impostando ssthres a cwnd/2

### Domanda 6
Considerare una rete rappresentata mediate un grafo.
![[Pasted image 20230627232034.png|500]]
Utilizzando l’algoritmo di Dijkstra 
1. determinare i percorsi di costo minimo tra il nodo u e tutte le altre destinazioni; 
2. fornire la tabella di forwarding del nodo u.

### Domanda 7
Che cosa vuol dire che il protocollo http è stateless? Cosa rappresenta lo stato ? Che rilevanza hanno i cookie in questo contesto?
####  Risposta
Il protocollo HTTP é stateless, ovvero non mantiene informazioni sulle sessioni precedenti a quella corrente. Lo stato é rappresentato dalle informazioni necessarie per il tracciamento degli utenti. 
I cookie permettono di mantenere queste informazioni, assegnando un'identificativo all'inizio della sessione con l'header set-cookie che poi il client fornirá ad ogni richiesta. In questa maniera é possibile tracciare gli utenti.

### Domanda 8
DNS: cosa sono i resource record di tipo MX?
Una RR di tipo MX identifica il nome canonico di un mail server.