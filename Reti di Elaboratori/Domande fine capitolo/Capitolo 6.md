### Domande Libro
###### Se tutti i collegamenti Internet fornissero un servizio di consegna affidabile, quello offerto da TCP risulterebbe ridondante? Perché?
Si, é vero che la perdita di pacchetti avviene al livello di rete e questi possono comunque essere corrotti durante la trasmissione su un link, peró potrebbe essere ridondante.

###### Quali servizi può offrire un protocollo di collegamento al livello di rete? E quali tra questi hanno servizi corrispondenti in IP? E in TCP?
Alcuni  servizi che i protocolli a livello di possono offrire al livello superiore sono: trasferimento dati affidabile, framing, rilevazione degli errori e accesso al collegamento.
I servizi corrispondenti in IP sono il rilevamento degli errori, mentre in TCP il traferimento dati affidabile e il rilevamento delgi errori.

###### Supponete che due nodi inizino a trasmettere nello stesso istante un pacchetto di lunghezza L su un canale broadcast con tasso trasmissivo R. Indichiamo il ritardo di propagazione fra quei due nodi con $d_{prop}$. Ci sarà collisione se $d_{prop}$ < L/R? Perché?
Se il ritardo di trasmissione é inferiore al ritardo di propagazione ci puó essere comunque collisione perché é possibile che quando un nodo sta inviando dei pacchetti ne stia anche ricevendo sullo stesso collegamento.

###### Nel Paragrafo 6.3 abbiamo elencato quattro utili caratteristiche dei canali broadcast. Quali sono quelle possedute dallo slotted ALOHA? E quali dal “token passing”?
Le buone caratteristiche dei canali broadcast sono:
1. quando un solo nodo sta trasmettendo, puó utilizzare l'intera velocitá di trasmissione del collegamento
2. Quando N nodi devo trasmettere contemporaneamente, ciascuno di essi ha troughput medio di R/D
3. Il protocollo é decentralizzato
4. Il protocollo é semplice
Slotted ALOHA presenta la prima, seconda e quarta caratteristica, mentr token passing tutte e 4.

###### In CSMA/CD, dopo la quinta collisione, qual è la probabilità che un nodo scelga K = 4? Il risultato K = 4 corrisponde a un ritardo di quanti secondi su una Ethernet a 10 Mbps?
CSMA/CD utilizza l'algoritmo binary exponential backoff to determinare quanto tempo deve attendere quando si verifica una collisione. Alla quinta collisione K é compreso nel range \[0,...,15\], quindi la probabilitá che scelga k=4 é $\frac{1}{32}$. Il tempo richiesto a trasmettere un bit a 10Mbps é $10^{-7}$ secondi, quindi il tempo necessario é $512\times 4 \times 10^-7=204\mu sec$.

###### Quanto è grande lo spazio degli indirizzi MAC? E quello di IPv4 e di IPv6?
Mac: $2^{48}$
IPv4: $2^{32}$
IPv6: $2^{128}$

###### Supponete che i nodi A, B e C siano connessi alla stessa LAN broadcast (attraverso le loro schede di rete). Se A invia migliaia di datagrammi IP a B, ciascuno incapsulato in un frame destinato all’indirizzo MAC di B, la scheda di rete di C elaborerà questi frame? E in tal caso, passerà i datagrammi IP in essi contenuti al livello di rete di C? La risposta cambierebbe se A inviasse i frame con l’indirizzo MAC broadcast?
La scheda di rete elaborerá i frame provenienti da A, si accorgerá che l'indirizzo di destinazione non é il suo e quindi li scarterá.
Se invece l'indirizzo di destinazione é quello brodcast allora non lo scarterá e lo passerá al proprio livello di rete.

###### Perché si inviano le richieste ARP all’interno di un frame broadcast? Perché il frame contenente una risposta ARP ha uno specifico indirizzo MAC di destinazione?
Il protocollo ARP svolge il conpito di conversione di un indirizzo a livello di rete ad uno di livello di collegamento. Per scoprire l'indirizzo MAC corrispondente ad uno IP, se questo non é presente nella tabella ARP dello switch si invia in brodcast a tutta la sottorete per interrogare tutti gli altri nodi della sottorete, e il nodo con indirizzo IP corrispondente invierá al mittente un pacchetto ARP contenente il proprio indirizzo MAC(non in broadcast poiché non é necessario, l'indirizzo del mittente é noto quando arirva il primo messaggio ARP)

###### Nella rete in figura il router ha due moduli ARP, ciascuno con la propria tabella ARP. È possibile che lo stesso indirizzo MAC compaia in entrambe le tabelle?
![[Pasted image 20230625141833.png]]


###### In che cosa differisce la struttura dei pacchetti Ethernet 10Base-T, 100Base-T e Gigabit Ethernet?
Hanno struttura dei frame identica.

###### 


### Esercizi Libro
###### Supponete che un pacchetto contenga la stringa 1110 0110 1001 e che sia utilizzato uno schema di parità dispari. Quale sarebbe il valore del campo checksum per uno schema di parità bidimensionale? La vostra risposta dovrebbe essere tale da imporre una lunghezza minima al campo checksum.
![[Pasted image 20230624163826.png|200]]

###### Mostrate come il controllo di parità bidimensionale possa rilevare e correggere un singolo bit errato. Fate un esempio di doppio errore nei bit che possa essere rilevato, ma non corretto.
Prediamo come esempio un pacchetto con stringa uguale a 0000 0000 0000 e supponiamo che il controllo di paritá bidimensionale avvenga nella seguente maniera
![[Pasted image 20230624164236.png|200]]
Supponiamo che un bit venga corrotto nella seguente maniera
![[Pasted image 20230624164406.png|200]]
é allora possibile individuare con precisione l'indice della riga e della colonna sulla quale é evvenuta la corruzione ed é quindi possibile correggere l'errore, riportando il bit a 0.
> Con questa stringa non é possibile, peró un doppio errore su una colonna non permette di terminare la riga alla quale si é verificato un errore.

###### Considerate un codice CRC con un generatore a sette bit G =10011 e supponete che D abbia il valore 1010101010. Qual è il valore di R?
Per calcolare il valore di R dobbiamo trovare il resto della divisione D/R, poiché \<D+R>%2=0.
Effettuiamo quindi lo shift a sinistra di D di 4 byte poiché la lunghezza di R é la lunghezza di G-1, e calcoliamo il resto della divisione usando le operazioni di XOR
![[Pasted image 20230625221619.png|400]]

##### Considerate il problema precedente, ma supponete che D abbia valore: 
###### (a) 1001010101
0000
> Non prendeva la foto

##### Supponete che due nodi, A e B, siano in competizione per accedere a un canale che usa slotted ALOHA, che A abbia più dati da trasmettere di B e che la probabilità di ritrasmissione di A, $p_A$, sia più grande di quella di B, $p_B$. 
###### (a) Calcolate l’espressione del valore medio del throughput di A. Qual è l’efficienza totale del protocollo con questi due nodi? 
Un nodo puó trasmettere solo se nessun altro nodo sta trasmettendo.
Il troughput medio per A é $p_A(1-p_B)$, mentre l'efficenza totale é $p_B(1-p_A)+p_B(1-p_A)$
###### (b) Se $p_A$ = $2p_B$, il throughput medio di A è il doppio di quello di B? 
Allora il troughput medio di A diventa $2p_B(1-p_B)\ne 2p_B(1-2p_B)$
###### (c) Supponete di avere in generale N nodi, tra cui A con probabilità di ritrasmissione $p_A$ e gli altri con probabilità p. Calcolate l’espressione del valore medio del throughput di A e degli altri nodi.
Il valore medio del throughput per i nodi N é $p_N(1-p)^{N-1}$

##### Supponete che quattro nodi attivi A, B, C e D siano in competizione per accedere a un canale che usa slotted ALOHA. Assumete che ciascun nodo abbia un numero infinito di pacchetti da inviare. Ciascun nodo tenta di trasmettere in ogni slot con probabilità p. Il primo slot è indicato con 1, il secondo con 2 e così via.
###### (a) Qual è la probabilità che il nodo A abbia successo al primo tentativo di trasmettere nello slot 5?
Un nodo trasmette se tutti gli altri non trasmettono, la probabilitá che un nodo no strasmetta é $(1-p)$, quindi la probabilitá che A trasmetta é $P(A)=p(1-p)^3$

###### (b) Qual è la probabilità che un nodo abbia successo per trasmettere nello slot 4?
Tutti i nodi trasmettono con la stessa proprietá, che é quella indicata sopra

###### (c) Qual è la probabilità che il primo successo si verifichi nello slot 3?
Per far avvenire il primo successo nel terzo slot, nei primi due nessun nodo deve aver trasmesso con successo, di conseguenza due o piú nodi devono aver provato a trasmettere.
Quidni la probabilitá che un nodo trasmetta con successo solo al terzo tentativo é la probabilitá che nessun nodo trasmetta al primo e secondo slot e che uno trasmetta la terzo.

###### (d) Qual è l’efficienza di questo sistema con quattro nodi?
$4p(1-p)^3$

###### Considerate un canale broadcast con N nodi e un tasso di trasmissione di $R bps$. Supponete che: (a) il canale broadcast utilizzi il protocollo polling (con l’aggiunta di un nodo di controllo) per l’accesso multiplo; (b) il tempo da quando un nodo completa l’invio a quando quello successivo può trasmettere (cioè, il ritardo di polling), sia $d_{poll}$; (c) all’interno di un ciclo di polling, a un dato nodo sia consentita la trasmissione di un massimo di Q bit. Qual è il massimo volume di dati (throughput) del canale broadcast?
Iniziamo calcolando la lunghezza di un rouund di polling
(\frac{Q}{R}+d_poll)




### Esercizi Sito
###### Esercizio 1(ERROR DETECTION AND CORRECTION: TWO DIMENSIONAL PARITY)
Suppose that a packet’s payload consists of 10 eight-bit values shown below. (Here, we have arranged the ten eight-bit values as five sixteen-bit values):

_Figure 1_    
00110100 10111010  
00011011 01001111  
01101010 11001011  
10111010 01001011  
00101111 00010011


*Figure 2*
Both the payload and parity bits are shown. One of these bits is flipped.

10101111 10111000 0  
01011011 10100111 0  
11000100 00000110 1  
00101111 01011010 1  
00010010 10100000 0  
00001101 11101011 0 %%parity%%

_Figure 3_  
Both the payload and parity bits are shown; Either one or two of the bits have been flipped.

11001000 00000001 1  
11010101 00000110 0  
00101000 00110011 0  
00111011 01001000 1  
10110101 01010111 0  
10111011 01101011 1

###### For figure 1, compute the two-dimensional parity bits for the 16 columns. Combine the bits into one string
Colonne: 11010000 01100110 
###### For figure 1, compute the two-dimensional parity bits for the 5 rows. Combine the bits into one string
Righe: 01110
###### For figure 1, compute the parity bit for the parity bit row from question 1. Assume that the result should be even.
1
###### For figure 2, indicate the row and column with the flipped bit (format as: x,y), assuming the top-left bit is 0,0
12,5

##### Esercizio 5(LINK LAYER (AND NETWORK LAYER) ADDRESSING AND FORWARDING)
Consider the figure below. The IP and MAC addresses are shown for nodes A, B, C and D, as well as for the router's interfaces.
![[Pasted image 20230626144148.png]]
Consider an IP datagram being sent from node B to node D.
###### What is the source mac address at point 3?
F2-58-84-8D-80-0D
###### What is the destination mac address at point 3?
DA-1E-49-65-5F-43
###### What is the source IP address at point 3?
128.119.186.156
###### What is the destination IP address at point 3?
128.119.176.93
###### Do the source and destinaton mac addresses change at point 4?
Sí, il source MAC diventa quello dell'interfaccia della sottorete piú a destra e il MAC di destinazione diventa l'indirizzo dell'host D
###### What is the source mac address at point 4?
AA-4A-27-88-F7-38
###### What is the destination mac address at point 4?
1E-5F-B6-C4-CE-9A
###### Do the source and destinaton mac addresses change at point 5? Answer with yes or no.
No, i router sono discpositivi a livello 3, quindi non utilizzano gli indirizzi MAC per effettuare le loro operazioni.