### Domande
#### Paragrafi 3.1-3.3
###### Consideriamo una connessione TCP tra gli Host A e B. Supponiamo che i segmenti TCP in viaggio tra A e B abbiano numero di porta di origine x e numero di porta di destinazione y. Quali sono i numeri di porta di origine e destinazione per i segmenti che viaggiano dall’Host B ad A?
I segmenti che viaggiano dall'host B ad A avranno porta di origine *y* e porta di destinazione *x*.

###### Descrivete perché lo sviluppatore di una applicazione potrebbe scegliere di fare uso di UDP anziché di TCP
Perché potrebbe non essere necessario il servizio di trasferimento affidabile implementato da TCP, ppure si vuole avere maggior controllo sul quando un datagramma UDP viene inviato, cosa non possibile a causa del controllo di congestione TCP.

###### Perché nell’odierna Internet il traffico voce e video viene spesso inviato su TCP piuttosto che su UDP?
Nonostante il traffico voce e video possa tollere un certo grado di packet loss e reagisca male al controllo della congestione, si utilizza solitamente TCP se il tasso di perdita di pacchetti é basso e perché alcune istruzioni UDP bloccano il traffico.

###### È possibile che un’applicazione che fa uso di UDP ottenga un trasferimento dati affidabile? Come?
Certo, UDP é un protocollo che non aggiunge praticamente nulla rispetto al traferimento di dati end-to-end offerto dal livello di collegamento, quindi é possibile ottenere un trasferimento dati affidabile applicando i sistemi di controllo, quali handshake e acknowledgement, implementati da TCP.

###### Supponete che un processo in un host C abbia una socket UDP con un numero di porta 6789. Supponete che entrambi gli host A e B mandino ciascuno un segmento UDP all’host C con numero di porta di destinazione 6789. Entrambi questi segmenti saranno diretti alla stessa socket dell’host C? Se sì, come il processo sull’host C saprà che questi due segmenti hanno origine da due host diversi?
Sí, una socket UDP é identificata da un'indirizzo e da un numero di porta, quindi i pacchetti provenienti dai due host sono indirizzati alla stessa socket. É possibile distinguere i pacchetti provenienti da due host differenti grazie al numero di porta e l'indirizzo di origine.

###### Supponete che un web server sia in esecuzione sull’host C sulla porta 80. Supponete che questo web server usi le connessioni persistenti e stia al momento ricevendo richieste da due diversi host, A e B. Tutte le richieste vengono inviate attraverso la stessa socket sull’host C? Se vengono fatte passare attraverso socket diverse, entrambe hanno la porta 80? Discutete e spiegate questa situazione.
No, le richieste sono indirizzate verso lo stesso processo ma saranno indirizzate per socket diverse. Se si usano connessioni persitenti si usa sicuramente una connessione TCP, e una socket TCP é identificata da una quadrupla <indirizzo di origine,porta di origine, indirizzo di destinazione, porta di destinazione>. Poiché due host diversi non possono avere sia indirizzo di origine che porta di origine uguali allora la connessione fará riferimento a socket diverse. Solitamente un processo é solito a creare thread per gestire le richieste TCP su socket diverse, creando una socket per ogni connessione persistente.

##### Vero o falso?
###### (a) L’Host A sta trasmettendo a B un file di grandi dimensioni su una connessione TCP. Ipotizziamo che B non abbia dati da inviare ad A;quindi non manderà acknowledgment a quest’ultimo, dato che non li può portare “sulle spalle” (piggyback) di pacchetti di dati.
Falso, l'host B deve sempre mandare Ack per i l'ultimo pacchetto ricevuto in ordine.
###### (b) La dimensione di rwnd in TCP non cambia mai per tutta la durata della connessione.
falso, il campo rwnd puó cambaire durante la durata della sessione.
###### (c) Supponiamo che l’Host A stia trasmettendo a B un file di grandi dimensioni su una connessione TCP. Il numero di byte inviati da A e che non hanno ricevuto acknowledgment non può superare la dimensione del buffer di ricezione.
vero
###### (d) Supponiamo che l’Host A stia trasmettendo a B un file di grandi dimensioni su una connessione TCP. Se il numero di sequenza di un segmento di questa connessione è m, allora il numero di sequenza del segmento successivo sarà necessariamente m + 1.
falso
###### (e) I segmenti TCP presentano nella propria intestazione un campo per rwnd.
vero
###### (f) Supponiamo che l’ultimo SampleRTT di una connessione TCP valga un secondo. Allora il valore corrente di TimeoutInterval per la connessione è necessariamente maggiore o uguale a un secondo.
Falso, $TimeoutInterval=EstimatedRTT+4\times DevRTT$ 
###### (g) Supponiamo che su una connessione TCP l’Host A stia trasmettendo a B un segmento con numero di sequenza 38 e 4 byte di dati. In questo stesso segmento il numero di acknowledgment è necessariamente 42.
Falso, il numero di acknowledgement é il numero del prossimo byte di cui si attende l'ack da B

##### Supponiamo che l’Host A stia trasmettendo a B due segmenti su una connessione TCP. Il primo segmento ha numero di sequenza 90 e il secondo 110.
###### (a) Quanti dati si trovano nel primo segmento?
$110-90=20byte$
###### (b) Supponiamo che il primo segmento vada perso, ma il secondo arrivi a B. Quale sarà il numero di acknowledgment che B manda ad A?
90

###### Supponiamo che due connessioni TCP stiano utilizzando lo stesso collegamento da R bps che è per loro il collo di bottiglia. Entrambe le connessioni hanno un grosso file da trasmettere (nella stessa direzione) sul collegamento. Le trasmissioni dei file iniziano allo stesso istante. Qual è la velocità trasmissiva che TCP vorrebbe assegnare a ciascuna delle connessioni?
Vorrebbe poter dividere l'intera velocitá del collegamento in egual misura tra le die connessioni, quindi $\frac{R}{2}$

###### Consideriamo il controllo di congestione di TCP. Quando il timer del mittente scade, il valore della soglia ssthresh viene dimezzata. Vero o falso?
Falso, quando si verifica un'evento di timeout sstresh viene impostato a $\frac{cwnd}{2}$

#### Problemi
###### Supponete che un ricevente UDP calcoli il checksum Internet per il segmento UDP ricevuto e trovi che corrisponda al valore trasportato nel campo checksum.
No,il checksum serve a controllare che non vi sia stata corruzione del messaggio durante il trasferimento. Se il checksum del messaggio é uguale al checksum calcolato dal destinatario allora siginifica che ci sono stati sicuramente deli errori durande l'inoltro.


#### Esercizi Sito
##### Esercizio 1 (Checksum)
Consider the two 16-bit words (shown in binary) below
Compute the Internet checksum value for these two 16-bit words:
11110100 00000111
00000110 00111001
###### What is the sum of these two 16 bit numbers?
11111010 01000000
###### Using the sum from question 1, what is the checksum?
00000101 10111111

##### Esercizio 4 (TCP sequence and ACK numbers, with segment loss)
Consider the figure below in which a TCP sender and receiver communicate over a connection in which the sender->receiver segments may be lost.
The TCP sender sends an initial window of 3 segments.

Suppose the initial value of the sender->receiver sequence number is 454 and the first 3 segments _each_ contain 768 bytes.
The delay between the sender and receiver is 7 time units, and so the first segment arrives at the receiver at t=8.

As shown in the figure below, 1 of the 3 segment(s) are lost between the segment and receiver.
![[Pasted image 20230619181915.png|500]]

###### Give the sequence numbers associated with each of the 3 segments sent by the sender.
454,1222,1990
###### Give the ACK numbers the receiver sends in response to each of the segments. If a segment never arrives use 'x' to denote it.
x,454,454
> Quá il terzo pacchetto inviato doveva essere quello con SN 454, dalla foto sarebbe arrivato e avremmo avuto ACK 1222

##### Esercizio 5(COMPUTING TCP'S RTT AND TIMEOUT VALUES)
Suppose that TCP's current estimated values for the round trip time (_estimatedRTT_) and deviation in the RTT (_DevRTT_) are 330 msec and 34 msec.

Suppose that the next three measured values of the RTT are 210 msec, 290 msec, and 280 msec respectively.

Use the values of $α = 0.125$, and $β = 0.25$.

![[Pasted image 20230619182935.png]]

###### What is the Timeout after the first RTT?
$DevRTT=(1-0,25)\times DevRTT + 0,25 \times |EstimatedRTT-SampleRTT|=0,75\times 34 + 0,25\times |330-210|=55,5$
$EstimatedRTT=(1-0,125)\times 330 + 0,125\times SampleRTT=0,875\times330+0,125\times210=315$
$Timeout= 315 + 55,5 \times 4=537$

###### What is the Timeout after the second RTT?
$DevRTT=0,75\times 55,5+0,25\times |315-290|=47,88$
$EstimatedRTT=0,875\times 315+0,125\times 290=311,88$
$Timeout=311,88 +4\times 47,88=503,4$

###### What is the Timeout after the third RTT?
$DevRTT=0,75\times 47,88+0,25\times |311,88-280|=43,88$
$EstimatedRTT=0,875\times 311,88+0,125\times 280=307,89$
$Timeout=307,89 +4\times 43,88=483,41$

##### Esercizio 7(TCP RETRANSMISSIONS (RELIABLE DATA TRANSMISSION WITH ACK LOSS))
Consider the figure below in which a TCP sender and receiver communicate over a connection in which the segments can be lost.
The TCP sender wants to send a total of 10 segments to the receiver and sends an initial window of 5 segments at t = 1, 2, 3, 4, and 5, respectively.

Suppose the initial value of the sequence number is 43 and every segment sent to the receiver each contains 305 bytes.

The delay between the sender and receiver is 7 time units, and so the first segment arrives at the receiver at t = 8, and an ACK for this segment arrives at t = 15.
As shown in the figure, 3 of the 5 segments is lost between the sender and the receiver, but _one_ of the ACKs is lost.
Assume there are no timeouts and any out of order segments received are thrown out.
![[Pasted image 20230619194433.png]]

###### What is the sequence number of the segment sent at t=1?
43
###### What is the sequence number of the segment sent at t=2?
$43+305=348$
###### What is the sequence number of the segment sent at t=3?
$348+305=653$
###### What is the sequence number of the segment sent at t=4?
$653+305=958$
###### What is the sequence number of the segment sent at t=5?
$958+305=1263$
###### What is the value of the ACK sent at t=8?
348
###### What is the value of the ACK sent at t=9?
653
###### What is the value of the ACK sent at t=10,t=11,t=12?
Non arriva
###### What is the sequence number of the segment sent at t = 15?
1568

##### Eservizio 6(SLOW START, CONGESTION AVOIDANCE, AND FAST RETRANSMIT)
Consider the figure below, which plots the evolution of TCP's congestion window at the beginning of each time unit (where the unit of time is equal to the RTT).
![[Pasted image 20230620130521.png]]

In this problem, you are asked to reconstruct the sequence of events (ACKs, losses) that resulted in the evolution of TCP's _cwnd_ shown below.
The initial value of _cwnd_ is 1 and the initial value of _ssthresh_ (shown as a red +) is 8.

###### Give the times at which TCP is in slow start.
La connesione sará in slow start dal momento in cui viene instaurata, duplicando la cwnd quando viene ricevuto un'ACK e ripartendo da cwnd=RTT quando si verifica un'evento di congestione, ovvero un timeout o 3 ACK duplicati. 

### Esercizi Slides
#### Esercizio 1
Si consideri un canale via satellite della capacità di 1 Mb/s. Considerando che il tempo di propagazione attraverso un satellite geostazionario richiede 250 ms, si chiede di dimensionare la minima finestra di trasmissione di un protocollo Go-BACK-N (con time-out) in modo che sia consentita la massima efficienza temporale del canale quando vengano trasmesse dei frame di 2000 bit. Si suppongano gli ACK trascurabili. Si calcoli poi la massima efficienza trasmissiva che si avrebbe nel caso in cui il meccanismo fosse di tipo STOP and WAIT semplice.