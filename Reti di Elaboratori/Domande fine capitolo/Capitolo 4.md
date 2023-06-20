### Domande fine capitolo
######  Qual è il nome di un pacchetto a livello di rete? Qual è la differenza fondamentale tra router e switch di livello di collegamento?
Un pacchetto a livello di rete é chiamato datagramma.
Un router inoltra i pachcetti in base all'indirizoz di destinazione, mentre uno switch a livello di collegamento in base all'indirizzo mac.

###### Abbiamo visto che le funzionalità del livello di rete possono essere divise in funzionalità del piano dei dati e funzionalità del piano di controllo. Quali sono le principali funzioni del piano dei dati? Quali sono le principali funzioni del piano di controllo?
La funzione principale del piano di dati é l'inoltro mentre la funzione principale del piano di controllo é l'insradamento.

###### Abbiamo fatto una distinzione tra la funzione di inoltro e la funzione di instradamento effettuate nel livello di rete. Quali sono le differenze chiave tra instradamento e inoltro?
L'inoltro é la funzione che permette ad un pacchetto di passare da un collegamento di ingresso ad uno di uscita al collegamento di uscita corrispondente secondo la tabella di inoltro, mentre l'instradamento é la funzione attraverso la quale viene deciso il percorso che dovrá seguire il pacchetto per giungere all'indirizzo di destinazione. I'inoltro é un'operazione molto veloce, della grandezza dei millisecondi, ed é quindi implementata in hardware, mentre l'instradamento richiede piú tempo, ed é quindi inplementato a livello software

###### Qual è il ruolo della tabella di inoltro in un router?
La tabella di inoltro associa un collegamento di uscita ad un pacchetto presente su un collegamento di ingresso, secondo uno o piú criteri.

###### Un router consiste di porte di ingresso, porte di uscita, struttura di commutazione e processore di instradamento. Quali di questi sono implementati in hardware e quali in software? Perché? Tornando alla nozione del piano dei dati e del piano di controllo nel livello di rete, quali sono implementati in hardware e quali in software? Perché?
le porte e la struttura di commutazione sono implementate in hardware, perché devono svolgere operazioni molto veloci non attuabili a livello software alla stessa velocitá, mentre il processore di intradamento é implementato a livello hardware.
Il piano dei dati é implementato in hardware per i requisiti di velocitá di cui necessita, mentre il piano di controllo é implementato in software.

###### Perché nelle porte di ingresso di un router ad alta velocità è memorizzata una copia della tabella di inoltro?
Perché leggere una copia salvata in memoria sarebbe un'operazione troppo dispendiona a livello di tempo, causando accodamenti.

###### Che cosa si intende per inoltro basato sulla destinazione? Come differisce dall’inoltro generalizzato (quale dei due approcci viene adottato nelle SDN)?
L'inoltro basato sulla destinazione associa ad un pacchetto un'interfaccia di uscita basandoli solamente sull'indirizzo di destinazione.
L'inoltro generalizzato invece puó utilizzare diversi criteri per l'associazione.
L'approccio utilizzato su SDN é il secondo.

###### Supponiamo che un pacchetto in entrata abbia corrispondenza con due o più occorrenze nella tabella di inoltro di un router. Quale regola applica un router per determinare la porta di uscita nell’inoltro tradizionale basato sulla destinazione?
La regola utilizzata in presenza di piú corrispondenze sulla forwarding table é il longest matching prefix, che prevede, a paritá di match, di scegliere l'interfaccia di uscita secondo la regola associata al prefisso piú lungo.

###### Descrivete sinteticamente i tre tipi di struttura di commutazione. Quale fra questi, se esiste, può inviare più pacchetti in parallelo attraverso la struttura di commutazione?
É possibile inoltrare i pacchetti dalle porte di ingresso alle porte di uscita attraverso la struttura di commutazione secondo 3 modalitá:
- Commutazione in memoria: i pacchetti vengono scritti nella memoria centrale del processore, il quale di occuperá di scriverli sul buffer delle porte di uscita. Le operazioni di I/O rendono questa modalitá impratica peró a causa della lentezza
- Commutazione tramite bus: tutte le porte di ingresso sono collegate a tutte le porte di uscita da un bus. Al pacchetto viene aggiunto un header che indica a quale porta di uscita é designata per un pacchetto, la quale lo accoderá mentre gli altri lo scarteranno. Puó causare comuqnue accodamenti poiché una sola porta di ingresso puó immetere un pacchetto sul bus alla volta
- commutazione tramite rete di collegamenti.  si utilizza una  matrice di commutazione per collegare le porte di ingresso alle porte di uscita. In questa maniera un pacchetto non viene bloccato a meno che non esista un'altro pacchetto in via di inoltro verso la stessa.

###### Spiegate come si può verificare la perdita di pacchetti alle porte di ingresso di un router e come questo fenomeno possa essere eliminato (senza utilizzare buffer infiniti).
La perdita di pacchetti sulle porte di ingresso si verifica quando il traffico sul collegamento é intenso, quindi i pacchetti in entrata su una porta eccedono quelli trasferiti sulle porte di uscita attraverso la struttura di commutazione. Se questo si protrae nel tempo i buffer sulle porte di ingresso si riempio, causando overflow e perdendo quindi dei pacchetti.
Questo fenomeno é evitabile se la struttura di commutazione é almeno n volte piú veloce della coda di ingresso, dove n é il numero di porte di ingresso.

###### Descrivete come si può verificare perdita di pacchetti alle porte di uscita di un router. Si può evitare tale perdita aumentando la velocità della struttura di commutazione?
La perdita di pacchetti sulle code di ingresso puó essere causata sempre da un buffer overflow, causato da un numero di pacchetti in ingresso eccessivo,o pari,m rispetto alla velocitá di trasmissione della porta. Questo non é quindi causato dalla struttura di commutazione. 

###### Che cos’è il blocco HOL? Si verifica sulle porte di ingresso o di uscita?
Il blocco Head of Line, o HOL, é un blocco che si verifica sulle linee di ingresso, causato dall'attesa che si liberi spazio sul buffer della porta di destinazione di un pacchetto. Ció causa un'attesa di tutti i pacchetti in coda sulla stessa porta di ingresso.

###### Abbiamo trattato diversi scheduling dei pacchetti: FIFO, con priorità, Round Robin (RR) e WFQ. Quali di questi garantisce che i pacchetti partano nello stesso ordine in cui sono arrivati?
FIFO

###### Fornite un esempio che mostri perché un operatore di rete dovrebbe voler dare priorità a una classe di pacchetti rispetto a un’altra classe di pacchetti.
Suppenendo di avere accodati presso una stessa porta di uscita due classi di pacchetti: alcuni contenenti dei pacchetti audio e altri contenenti delle mail SMTP. Le mail SMTP non hanno particolare urgenza di essere ricevute nel minor tempo possibile, mentre un'attesa su una comunicazione audio puó portare ad alcuni problemi.

###### Qual è la differenza essenziale tra lo scheduling dei pacchetti RR e WFQ? Esiste un caso in cui si comportano esattamente allo stesso modo?
Lo scheduling di paccheti Round Robin prevedono accodamento l'invio basato su classi non prioritario, mentre lo scheduling WFQ, o accodamento medio ponderato,divide il servizio su tutte le classi, mentre con RR tutte le classi sono trattate alla stessa maniera.

###### Supponete che l’Host A mandi all’host B un segmento TCP incapsulato in un datagramma IP. Come può sapere il livello di rete dell’Host B di dover passare il segmento (ossia il payload del datagramma) a TCP anziché a UDP o a un altro protocollo di livello superiore?
Attraverso il campo dell'intestazione Protocollo di bit. Ogni protocollo a livello superiore ha assegnato un numero.

###### Quale campo nell’intestazione IP può essere utilizzato per garantire che il pacchetto non venga inoltrato per più di N router?
TTL, time to live

###### Ricordate che la checksum di Internet viene usata sia nei segmenti a livello di trasporto sia nei datagrammi a livello di rete. Considerate ora un segmento a livello di trasporto incapsulato in un datagramma IP. Le checksum dell’intestazione del segmento e del datagramma sono calcolate su qualche bit comune nel datagramma IP? Motivate la risposta.
No, la checksum di un datagramma IP viene calcolata esclusivamente sull'intestazione, mentre quella di un secmento TCP o di un datagramma UDP viene calcolata sull'intero pacchetto.

###### Quando un datagramma grande viene frammentato in datagrammi più piccoli, questi ultimi dove vengono riassemblati in un unico datagramma?
Se sono dei datagrammi 
Soltanto sugli host di invio e destinazione

###### I router hanno indirizzi IP? Se sì, quanti?
Sí, una per interfaccia.

###### Qual è l’equivalente binario dei 32 bit dell’indirizzo IP 223.1.3.27?
11011111.00000001.00000011.00011011

###### Ipotizzate che ci siano tre router tra un host sorgente e uno di destinazione. Ignorando la frammentazione, quante interfacce attraverserà un datagramma IP? Quante tabelle di inoltro saranno consultate per recapitare il datagramma?
1 uscita dall'host di invio+ 2 per ogni router intermedio + 1 interfaccia di ingresso dell'host di destinazione= 8 interfacce
Saranno consultate invece 3 tabelle di inoltro, una per ogni router.

###### Supponete che un’applicazione generi blocchi di 40 byte di dati ogni 20 ms e che i blocchi siano incapsulati in un segmento TCP e poi in un datagramma IP. Quale percentuale di datagramma sarà costituita da overhead e quale da dati applicativi?


#### Esercizi Sito
##### Esercizio 1
Consider a datagram network using 8-bit host addresses.  
Suppose a router uses longest-prefix matching, and has the following forwarding table:
![[Pasted image 20230621000601.png]]

###### Suppose a datagram arrives at the router, with destination address 10101101. To which interface will this datagram be forwarded using longest-prefix matching?
5
###### Suppose a datagram arrives at the router, with destination address 11110010. To which interface will this datagram be forwarded using longest-prefix matching?
2
###### Suppose a datagram arrives at the router, with destination address 00010011. To which interface will this datagram be forwarded using longest-prefix matching?
3

##### Esercizio 2
Consider the router and the three attached subnets below (A, B, and C). The number of hosts is also shown below. The subnets share the 23 high-order bits of the address space: 192.168.52.0/23
![[Pasted image 20230621000948.png]]
Assign subnet addresses to each of the subnets (A, B, and C) so that the amount of address space assigned is minimal, and at the same time leaving the largest possible contiguous address space available for assignment if a new subnet were to be added. Then answer the questions below.

###### Is the address space public or private?