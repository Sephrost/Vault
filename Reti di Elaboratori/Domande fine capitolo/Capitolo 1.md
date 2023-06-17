## Paragrafo 1.1
###### Qual è la differenza tra host e sistema periferico? Elencate i tipi di sistemi periferici. Un web server è un sistema periferico?
Un host e un sistema periferico sono la stessa.
Un sistema periferico é un dispositivo collegati ad internet quindi un webserver é un sistema periferico.
###### Perché gli standard sono importanti nei protocolli?
Gli standard sono importanti nei protocolli perché senza di essi non sarebbe possibile la comunicazione, infatti uno standard definisce il formato e l'ordine dei messaggi scambiati. Senza di essi la comunicazione sarebbe caotica.
### Paragrafo 1.2
###### Qual'é la velocitá di trasmissione di una lan ethernet?
Una lan ethernet puó trasportare dati a 10mbs, 100mbs,1gbs e 10gbs
### Paragrafo 1.3
###### Supponete di avere un solo commutatore di pacchetto tra un host di invio e uno di ricezione. La velocità di trasmissione tra l’host d’invio e il commutatore e tra il commutatore e l’host di ricezione sono rispettivamente R1 e R2 . Nell’ipotesi che il commutatore adotti la commutazione di pacchetto store-and-forward, qual è il ritardo totale da un capo all’altro per inviare un pacchetto di lunghezza L? Si ignorino i ritardi di accodamento, di propagazione e di elaborazione.
Il ritard é dato da $R_{elab}+R_{acc}+R_{Transm}+R_{prop}$, ci viene chiesto di ignorare 3 di questi quindi $R_{end-to-end}=R_{trasm}$ ,che é il tempo necessario a immetere un pacchetto da l collegamento di uscita sul mezzo di trasmissione. $R_{trasm}=\frac{L}{R}$. Inoltre il pacchetto dovrá essere ricevuto per intero prima dall'host $R_1$ prima di essere ritrasmesso a $R_2$ quindi $R_{tot}=\frac{L}{R_1}+\frac{L}{R_2}$.

###### Quale vantaggio presenta una rete a commutazione di circuito rispetto a una a commutazione di pacchetto? Quali vantaggi ha TDM rispetto a FDM in una rete a commutazione di circuito?
Una rete a commutazione di pacchetto non é in grado di garantire una velocitá di trasmissione costante, a differenza della commutazione di circuito.
Col multiplexing a divisione di tempo permette l'utilizzo per piú trasmissioni sullo stesso circuito, riducendo i momenti in cui non vengono passate informazioni su di esso rispesso al multiplexing a divisione di frequenza. 

##### Supponete che gli utenti condividano un collegamento a 2 Mbps e che ciascun utente richieda 1 Mbps quando trasmette, ma che ciascuno trasmetta solo il 20% del tempo
###### a. Quando si usa la commutazione di circuito, quanti utenti vengono supportati?
Se si usa la commutazione di circuito su un collegamento di 2Mbps e ciascuno richiede 1Mbps, allora si potranno avere al massimo $\frac{2Mbps}{1Mbps}=2$ connesioni contemporanee
###### b. Per il resto del problema supponete di usare la commutazione di pacchetto. Perché non vi è essenzialmente ritardo di accodamento prima del collegamento, se due utenti o meno trasmettono contemporaneamente? Perché si verifica un ritardo di accodamento se gli utenti che trasmettono contemporaneamente sono tre?
Poiché ogni bandwidth richiesta da un utente per trasmettere é 1Mbps, allora due utenti utilizzerebero l'intero collegamento senza doversi accodare, mentre se un terzo utente richiedesse la connesione allora eccederebbe le risorse disponibili e quidni dovrá accodarsi.  
###### c. Calcolate la probabilità che un dato utente stia trasmettendo.
Un utente sta trasmettendo solo il 20% del tempo, quindi la probabilitá che stia trasmettendo é sempre 20%
###### d. Supponete che vi siano tre utenti: trovate la probabilità che, in ogni istante, tutti i tre utenti trasmettano contemporaneamente e trovate le frazioni di tempo durante le quali la coda cresce.
Un'utente trasmette con probabilitá 20%, quindi la probabilitá che 3 utenti stiano trasmettendo contemporaneamento in ogni istante é $0.2^3=0,008$. La coda creqsce quando i 3 utenti trasmettono contemporaneamente, quindi lo 0,8% del tempo. 

### Paragrafo 1.4
###### Considerate l’invio di un pacchetto da un host a un altro lungo un percorso fisso ed elencate le componenti di ritardo nel ritardo complessivo. Quali sono costanti e quali variabili?
Le componenti di ritardo lungo un percorso sono il accodamento, trasmissione e propagazione, il ritardo di accodamento é variabile e dipende dal traffico sulla rete mentre gli altri due sono costanti.
###### Quanto tempo impiega un pacchetto di lunghezza di 1000 byte per propagarsi su un collegamento lungo 2500 km, con velocità di propagazione di 2,5 × 108 m/s e velocità di trasmissione di 2 Mbps? Più in generale, quanto tempo impiega un pacchetto di lunghezza L a propagarsi su un collegamento lungo d, con velocità di propagazione v e velocità di trasmissione di R bps? Questo ritardo dipende dalla lunghezza del pacchetto? Dalla velocità di trasmissione?
Il pacchetto impiegherá $\frac{25\times 10^4}{2,5\times 10^8}=0,001$ secondi. Il ritardo di propagazione é indipendnete dalla lunghezza del pacchetto ma direttamente proporzionale alla distanza fra i due sistemi periferici e inversamrnte proporionale alla velocitá del collegamento, quindi $\frac{d}{v}$.

##### Supponete che l’Host A voglia inviare un file voluminoso all’Host B. Il percorso tra l’Host A e l’Host B ha tre collegamenti con frequenze R1 = 500 kbps, R2 = 2 Mbps e R3 = 1 Mbps, rispettivamente
###### a. Assumete che non vi sia altro traffico nella rete: qual è il throughput per il trasferimento del file?
Il troughput per il collegamento dei file é 500kbps, poiché il collegamento R1 fa da collo di bottiglia.
###### b. Supponete che il file sia di 4 milioni di byte. Dividendo tale grandezza per il throughput, approssimativamente quanto tempo occorrerà per trasferire il file all’Host B?
Il file impiegherá $\frac{4\times 10^3\times 8kb}{5\times 10^2kbps}=64 sec$ 
###### Ripetete (a) e (b) con R2 ridotto a 100 kbps.
Poiché R2<R1, il troughtput diventa 100kbps,  impiegando $\frac{4\times 10^3\times 8 kb}{1\times 10^2kbps}=320sec$.

### Paragrafo 1.5
###### Quali sono i cinque livelli della pila di protocolli Internet? Quali sono i loro principali compiti?
I cinque strati sono 
- livello apllicativo: sede degli applicativi di rete e dei loro protocolli
- livello di trasporto: si occupa di trasferire segmenti dal livello applicativo a livwello di rete
- livello di rete: si occupa di trasferire  i datagrammi da un'hostad un'altro
- livello di collegamento: si occupa dell'instradamento di un datagramma attraverso una serie di router
- livello fisico: si ocupa di trasferire i bit del frame da un nodo a quello successivo

## Problemi
###### L’Equazione 1.1 ($R_{end-to-end}=N(\frac{L}{R})$) fornisce una formula per calcolare il ritardo end-to-end quando si invia un pacchetto di grandezza L su N collegamenti con velocità R. Si generalizzi tale formula nel caso si inviino P pacchetti uno dietro l’altro sugli N collegamenti.
A tempo $N(\frac{L}{R})$ il primo pacchetto ha raggiunto l'ultimo host, e visto che é possibile trasmettere solo uno alla volta il secondo é nell'host precedente e cosí via. A tempo $N(\frac{L}{R})+\frac{L}{R}$ il secondo pacchetto ha raggiunto l'host di destinazione e il terzo pacchetto é nell'host precedente. 
Turri i pacchetti raggiungeranno la destinazione a tempo $N(\frac{N}{R})+(P-1)(\frac{L}{R})$.

###### Considerate un’applicazione che trasmetta dati a velocità costante (per esempio, un’unità di dati da N bit ogni k unità di tempo, dove k è piccolo e fissato). Inoltre, una volta avviata, l’applicazione continuerà a funzionare per un periodo di tempo relativamente lungo. Rispondete alle seguenti domande, motivando sinteticamente le vostre affermazioni. 
###### (a) Per questa applicazione sarebbe più appropriata una rete a commutazione di pacchetto o a commutazione di circuito? Perché? 
Poiché la velocitá di trasmissione é costante e l'applicazione funzionerá per un periodo di tempo piuttosto lungo, per l'applicazione sarebbe appropriata una rete a commutazione di circuito, in quanto i ltrasmission rate é noto e costante, permettendo di dividere la larghezza di banda sulle connessioni.

###### (b) Si supponga di utilizzare una rete a commutazione di pacchetto e che il solo traffico in questa rete provenga dall’applicazione descritta sopra. Inoltre, si assuma che la somma delle velocità di generazione dei dati sia inferiore alla capacità di ogni collegamento. È richiesta una forma di controllo della congestione? Perché?
Poiché la velocitá di generazione dei pacchetti é inferiore alla capacitá del collegamento, significa che anche se tutti gli host trasmettessero contemporaneamente, avrebbero abbastanza bandwidth ciscuno, rendendo non necessario il controllo di congestione.

##### Considerate la seguente rete a commutazione di circuito , ricordando che ci sono 4 circuiti su ogni collegamento. Denominate i 4 commutatori con le lettere A, B, C e D in senso orario.
![[Pasted image 20230615160408.png]]
###### (a) Qual è il massimo numero di connessioni contemporanee attive in un dato istante in questa rete?
Se tutte le connessioni sono attive, e ogni circuito ha 4 collegamenti, allora le connessioni attive contemporaneamente sono 16.
###### (b) Si supponga che tutte le connessioni avvengano tra A e C. Qual è il numero massimo di connessioni simultanee in corso?
Se tutte le connessioni avvengono da A a C, allora possono avvenire attraverso due cicuiti: ABC e ADC. Ogni circuito impiega 4 collegamenti quindi il massimo numero di collegamenti utilizzati é 8.
###### (c) Si supponga di voler effettuare 4 connessioni tra A e C e altre 4 tra B e D. Possiamo instradare queste chiamate sui 4 collegamenti in modo da effettuare tutte e otto le connessioni?
Per poter istradare 4 connessioni da A a C possiamo instradare 2 connessioni attraverso B e le altre 2 attraverso D, mentre per effettuare 4 connessioni da B a C possiamo instradarnme due attraverso A, che ha 2 cicuiti liberi sul collegamento AB e e altri due attraverso C.

##### Consideriamo due host, A e B, collegati da una singola connessione con velocità di R bps. Supponiamo che i due host siano separati da m metri e che la velocità di propagazione lungo il collegamento sia di v m/s. L’Host A sta per inviare un pacchetto di L bit all’Host B.
###### (a) Esprimete il ritardo di propagazione, $d_{prop}$, in funzione di m e v
Il ritardo di propagazione é direttamente proporzionale alla distanza tra i collegamenti e inversamente proporzionale alla velocitá di porpagazione del mezzo di trasmissione, quindi $d_{prop}=\frac{m}{v}$.
###### (b) Determinate il tempo di trasmissione del pacchetto, $d_{trasm}$, in termini di L e R
Il ritardo di trasmissione é direttamente proporzionale alla lunghezza del pacchetto e inversamente proporzionale alla velocitá della connessione, quindi $d_{trasm}=\frac{L}{R}$
###### (c) Tralasciando i ritardi di elaborazione e di accodamento, ricavate un’espressione del ritardo end-to-end.
Il ritardo end-to-end é uguale a alla somma dei ritardi sui nodi, tralasciando ritardo di elaborazione e accodamento otteniamo $d_{end-to-end}=d_{trasm}+d_{prop}=\frac{m}{v}+\frac{L}{R}$ 
###### d) Supponete che l’Host A cominci a trasmettere il pacchetto all’istante t = 0. All’istante t = $d_{trasm}$ dove si trova l’ultimo bit del pacchetto?
All'istante $d_{trasm}$ il pacchetto é stato trasmesso per intero dall'interfaccia di uscita al collegamento, quidni é appena stato immesso su di esso.
###### (e) Supponete che $d_{prop}$ sia maggiore di $d_{trasm}$. All’istante $d_{trasm}$ dove si trova il primo bit del pacchetto?
Pouché il tempo di propagazione é inferiore al tempo di trasmissione, questo significa che il primo bit ha raggiunto l'host B.
###### (f) Supponete che $d_{prop}$ sia minore di $d_{trasm}$. All’istante t = $d_{trasm}$ dove si trova il primo bit del pacchetto?
A differenza del caso precedente, il tempo di propagazione é maggiore del tempo di trasmissione, quindi quando l'ultimo bit del pacchetto é stato immesso sul collegamento, il primo bit non ha ancora raggiunto la destinazione
###### (g) Supponete che $v = 2,5\times 10^8 m/s$, $L = 120 bit$ e $R = 56 kbps$. Determinate la distanza $m$ tale per cui $d_{prop}$ sia uguale a $d_{trasm}$.
$$
\begin{eqnarray}
d_{prop}=d_{trasm}\\
\frac{m}{v}=\frac{L}{R} \\
m=\frac{L}{R}v\\
m=\frac{120bit}{56kbps}(2,5\times10^8)=535,71m
\end{eqnarray}
$$
###### Nel seguente problema prendete in considerazione una trasmissione di voce in tempo reale dall’Host A all’Host B su una rete a commutazione di pacchetto (VoIP). L’Host A converte al volo la voce in un flusso digitale di bit a 64 kbps. Poi raggruppa i bit in pacchetti da 56 byte. Tra A e B esiste un solo collegamento, con velocità di trasmissione 1 Mbps e ritardo di propagazione di 10 millisecondi. Non appena l’Host A compone un pacchetto lo invia all’host B. Quando quest’ultimo riceve un intero pacchetto, lo converte in un segnale analogico. Quanto tempo intercorre dall’istante in cui un bit viene creato (a partire dal segnale analogico originario nell’Host A) al momento in cui il bit viene decodificato (come parte del segnale analogico nell’Host B)?
L'host A deve prima generare un pacchetto prima di trasmetterlo, ció impiegherá 
$$\frac{56\times 8}{64\times10^3}=0,007sec=7m sec$$
successivamente lo invierá all'host B, trasmettendolo sul collegamento, dal quale si propagherá fino a raggiungere il destinatario.
Il ritardo di trasmissione é pari a $d_{trasm}=\frac{L}{1Mbps}=\frac{56\times 8}{1\times 10^6}=0,448msec$, il ritardo di propagazione a $10msec$ quindi 
$$7msec+0,448msec+10msec=17,448msec$$

##### Supponete che alcuni utenti condividano un collegamento da 3 Mbps, e che ciascuno richieda 150 kbps quando trasmette, ma che ogni utente trasmetta solo per il 10% del tempo.
###### (a) Quando si utilizza la commutazione di circuito, quanti utenti si possono supportare?
Si possono supportare contemporaneamente $\frac{3000kbps}{150kbps}=20$ connessioni contemporanee
###### (b) Per il resto del problema, si supponga l’adozione della commutazione di pacchetto. Determinate la probabilità che un certo utente stia trasmettendo
Un utente trasmette con probabilitá 10%, poiché trasmette solo il 10% del tempo.

### Esercizi lezione
###### Si ipotizzi di volere effettuare il trasferimento di un file di L byte dalla Francia agli Stati Uniti. Assumere che il collegamento abbia capacità C=10 Gbit/s e sia realizzato attraverso un cavo transatlantico in fibra ottica di lunghezza d=5000 km. Quale deve essere la dimensione del file affinché quando il primo bit del file giunge alla destinazione negli Stati Uniti l’ultimo bit del file viene trasmesso dal mittente in Francia?
Per ottere ció $r_{trasm}=r_{elab}$, quindi 
$$
\begin{eqnarray}
r_{trasm}=r_{elab}\\
\frac{d}{v}=\frac{L}{R}\\
L=\frac{d}{v}R=\frac{5\times 10^6}{2\times 10^8}(1\times 10^{10})=
\end{eqnarray}
$$


### Esercizi Sito
[Sito](https://gaia.cs.umass.edu/kurose_ross/interactive/index.php)
#### Esecizio 1
Consider the figure below, with three links, each with the specified transmission rate and link length.
![[Pasted image 20230616150316.png]]
Assume the length of a packet is 8000 bits. 
The speed of light propagation delay on each link is $3\times 10^8$ m/sec.
Round your answer to two decimals after leading zeros.

###### What is the transmission delay of link 1?
$d_{trasm}=\frac{L}{R}=\frac{80\times 10^2}{10\times 10^7}=0,08ms$
###### What is the propogation delay of link 1?
$d_{prop}=\frac{d}{v}=\frac{1000}{3\times 10^8}=3.33\mu sec$
###### What is the total delay of link 1?
$d_{L1}=d_{trasm}+d_{prop}=0.08+0.00333=0.08333ms$
###### What is the transmission delay of link 2?
$d_{trasm}=0,08ms$
###### What is the propogation delay of link 2?
$d_{prop}=\frac{50\times 10^4}{3\times 10^8}=1,7ms$
###### What is the total delay of link 2?
$d_{L2}=0.08+1.7=1,78ms$
###### What is the transmission delay of link 3?
$d_{trasm}=\frac{8000}{10\times 10^6}=0,8ms$
###### What is the propogation delay of link 3?
$d_{prop}=\frac{3000}{3\times 10^8}=10\mu sec$
###### What is the total delay of link 3?
$d_{L3}=0,08+0,001=0,081ms$
###### What is the total delay?
$d_{tot}=0.083+1,78+0,081=1,944ms$

#### Esecizio 2
Consider the scenario shown below, with four different servers connected to four different clients over four three-hop paths. 
The four pairs share a common middle hop with a transmission capacity of R = 100 Mbps. 
The four links from the servers to the shared link have a transmission capacity of $R_S$ = 30 Mbps. Each of the four links from the shared middle link to a client has a transmission capacity of $R_C$ = 10 Mbps.
![[Pasted image 20230616154012.png|550]]
###### What is the maximum achievable end-end throughput (in Mbps) for each of four client-to-server pairs, assuming that the middle link is fairly shared (divides its transmission rate equally)?
Se il collegamento R é diviso equamente e sono presenti quattro connessioni, allora ciascuna avrá a disposizione un troughput di $100/4=20mbs$. Tutte le connessioni $R_c\to R$ hanno troughput di 10Mbps e e quelle $R_S\to R$ 30Mbps. Il massimo trouoghtput end-to-end ottenibile é quindi 10Mbps.
###### Which link is the bottleneck link? Format as $R_c$, $R?s$, or $R$
$R_c$, é quello con troughput minore.
###### Assuming that the servers are sending at the maximum rate possible, what are the link utilizations for the server links ($R_S$)?
$10:30=x:100\to 33\%$
###### Assuming that the servers are sending at the maximum rate possible, what are the link utilizations for the client links ($R_C$)? Answer as a decimal
$100\%$
###### Assuming that the servers are sending at the maximum rate possible, what is the link utilizations for the shared link ($R$)? 
$40\%$

