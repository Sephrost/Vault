#### Paragrafo 2.1
###### Elencate cinque applicazioni di Internet non proprietarie e i protocolli a livello di applicazione che utilizzano.

Applicativo|Protocollo
--|--
Posta Elettronica|SMTP,POP3,IMAP
Trasferimento File|FTP,SFTP
Paghine Web|HTTP
Streaming Video|HTTP
Accesso a terminali remoti|SSH

###### Qual è la differenza tra l’architettura di una rete e l’architettura di un’applicazione?
L'architettura di rete all'organizzazione stratificata delle del processo di comuncazione, mentre la struttura dell'applicazione fa rifermento al design della stessa.

###### In una sessione di comunicazione tra una coppia di processi, chi è il client e chi il server?
Il server é l'host che invia i dati richiesti dal client, mentre il client é l'host che li riceve e che inizia la connessione.

###### Per le applicazioni P2P, siete d’accordo con l’affermazione “Non esiste la nozione di lato client e server in una sessione di comunicazione”? Perché?
In una rete client/server la divisione tra client é host e marcata, a differenza di una rete p2p: tutti gli host sono sullo stesso piano, e possono sia inviare i dati richiesti da un'altro host(peer) che ricevere dati. Quindi i concetti di lato client e server esistono, ogni host é sia client che server.

###### Quali informazioni usa un processo in esecuzione su un host per identificare un processo di un altro host?
Indirizzo di destinazione e numero di porta, che identificano il socket dell'applicativo di destinazione.

###### Supponete di voler fare una transazione da un client remoto a un server il più velocemente possibile. Usereste TCP o UDP? Perché?
TCP offre una serie di servizi, come il trasferimento dati affidabile, che rendono il servizio di trasporto piú lento. Se si necessita di un servizio di trasferimento il piú veloce possibile si usa invece UDP, velcoe ma che non garantisce che il pacchetto sia arrivi a destinazione.

###### Elencate le quattro grandi classi di servizi che può fornire un protocollo di trasporto e per ciascuna indicate se TCP o UDP o entrambi forniscono quel tipo di servizio.

Servizio|Protocollo di Trasporto
--|--
Trasferimento dati affidabile|TCP
Troughput minimo garantito|Nessuno
Sicurezza|Nessuno
Ricezione Entro un tempo limite|Nessuno

###### Ricordiamo che TCP può essere arricchito con SSL per fornire un servizio di sicurezza tra processi, compresa la cifratura. SSL funziona a livello di trasporto o applicativo? Se uno sviluppatore vuole che TCP sia arricchito con SSL, che cosa deve fare?
SSL funziona a livello applicativo, é in grado di garantire la confidenzialitá attraverso la cifratura del pacchetto a livello di applicazione. Se si vuole aggiungere SSL a un'applicazione questa lo deve implementare.


#### Paragrafi 2.2 - 2.4
###### Che cosa si intende per protocollo che fa uso di handshaking?
Un protocollo che fa uso di handshaking é uno che invia dei pacchetti per assicurarsi che la connesione si stata instaurata con successo.

###### Perché HTTP, SMTP e POP3 fanno uso di TCP e non di UDP?
Perché utilizzano il trasporto dati affidabile applicato da TCP, che UDP non implementa.

###### Prendete in considerazione un sito di commercio elettronico che vuole mantenere traccia degli acquisti di ciascun cliente. Descrivete come sia possibile farlo utilizzando i cookie
Quando l'utente visita per la prima volta il sito o effettua un login il server crea un'id per l'utente e chiede all'user agent dell'utente di impostarlo come cookie.
Ogni richiesta(e acquisto) da parte dell'utente sará quindi associato al cookie ed é possibile tracciare la navigazione.

###### Descrivete il modo in cui il web caching riduce il ritardo di ricezione di un oggetto richiesto. Questo si verificherà per tutti gli oggetti richiesti o solo per alcuni? Perché?
Una webcache svolge il ruolo di server intermedio: le richieste vengono indirizzate verso di questa piuttosto che al server contente la risorsa richiesta. Se questa é salvata nella cache, alllora verrá restituita con un tempo di accesso minore rispetto a quello richiesto per la risposta dal server. Se invece non é salvata, sará la cache a richiederlo al server di destinazione, salvando una copia in locale prima di restituirla al richiedente. Il tempo di accsso sará peró minore su tutte le richieste, poiché riduce anche il traffico su una rete.

###### Supponete che Alice, con un account di posta elettronica basato sul Web invii un messaggio a Bob che accede alla propria casella sul proprio server usando POP3. Descrivete come il messaggio giunge dall’host di Alice a quello di Bob. Assicuratevi di elencare la serie di protocolli a livello di applicazione usati per trasferire il messaggio tra i due host.
Per prima cosa lo user agent di Alice invia la mail al proprio server SMTP utilissizzando il protocollo Push SMTP, appunto. Una volta nella coda di invio del server, questo proverá ad instaurare una connesisone col server SMTP del destinatario ogni 30 minuti circa, fino a quando questa non viene recapitata, utilizzando il protocollo di trasporto TCP. Il server SMTP del destinatario salverá quindi la mail ricevuta in memoria, in particolare nella casella di destinazione di Bob. SMTP é un protocollo push e non pull, quindi lo user agent di Bob non gli consentirá di accedere alle mail in casella, per questo utilizza il semplice protollo POP3 per ottenere le mail a Bob destinate. POP3 é un protocollo stateful non persistente, quindi tiene traccia delle mail lette attraverso lo UA e al termine della sessione le cancella tutte oppure le mantiene in memoria.

###### Dal punto di vista dell’utente, qual è la differenza tra le modalità “scarica e cancella” e “scarica e mantieni” in POP3?
Una sessione POP3 un modalitá "scarica e cancella" cancella le mail scaricate al termine della stessa, mentre in modalitá "scarica e mantieni" le mail vengono tenute in memoria anche dopo il termine della sessione. La modalitá scarica e cancella é scomoda nel caso l'utente provi ad accedere alle mail da piú user agent, poiché non vengono mantenute in memoria.

###### È possibile che il web server e il mail server di un’azienda abbiano esattamente lo stesso sinonimo di un hostname (per esempio, foo.com)? Quale sarebbe il tipo di RR che contiene l’hostname del server di posta?
Si, é possibile se il server autoritativo di foo.com contiene un record di tipo MX usato per indicizzare l'indirizzo ip del mail server a partire da un'hostname.

######  Si consideri un’e-mail inviata da un utente con indirizzo e-mail che termina con .edu. Sarebbe possibile determinare dall’intestazione l’indirizzo IP dell’host da cui è stata inviata l’e-mail? E se il messaggio fosse stato inviato da un account Gmail?
No, poiché sarebbe solo possibile recuperare l'indirizzo ip del server SMTP del mittente attraverso una query dns, non l'indirizzo dello user agent.
> Questa domanda non si capisce, non é spiegata nel libro

### Paragrafo 2.5
###### Supponete che Alice fornisca in BitTorrent chunk di un file a Bob durante tutto un intervallo di 30 secondi. Bob ricambierà necessariamente il favore inviando ad Alice dei chunk nello stesso intervallo? Spiegate perché.
Se Bob é in un torrent, allora potrá cottraccambiare se Alice é nella lista dei 4 host che stanno passando pacchetti a Bob a velocitá piú elevata, lista aggiornata ogni 10 secondi, mentre ogni 30 secondi sceglié un'host in piú da aggiungere casualmente alla lista.

###### Considerate un nuovo peer, Alice, che entra a far parte di BitTorrent senza aver nessun chunk. Senza chunk, non può diventare uno dei quattro peer unchoked di qualcuno degli altri peer, in quanto non ha nulla da inviare. Come fa Alice a ottenere il suo primo chunk?
Alice, appena entrata in un torrent, non possiede chunk da condividere, quindi non puó entrare nella lista degli peer unckocked a cui gli altri peer stanno inviando i chunk a meno che entri grazie alle selezione casuale dell'host "optimistically unchoked" selezionato ogni 30 secondi.

### Paragrafo 2.6
###### Le CDN adottano in generale due diversi approcci per la dislocazione dei server. Elencateli e descriveteli brevemente.
I due approcci per la dislocazione dei CDN sono enter deep, che prevede il posizionamento il piú vicino possibile agli utenti finali: nei punti d'ingresso degli ISP al fine di ridurre i ritardi e incrementare il troughput, e bring home, che prevede il posizionamento in pochi punti strategici per ridurre i costi di manutenzione e gestione.

###### Oltre alle considerazioni legate alla rete, come ritardi, perdite e prestazioni di banda, ci sono molti altri fattori importanti che intervengono nella scelta della strategia di selezione dei cluster. Quali sono?
Principalmente una questione di costi

### Problemi
#### Vero o falso?
###### (a) Quando un utente richiede una pagina web costituita da testo e tre immagini, il client invia un messaggio di richiesta e riceverà quattro messaggi di risposta.
Falso, é possibile inviare solo un messaggio di risposta a seguito di una richiesta.quindi verrá inviata solo la pagina e dovrá richiedere le immagini con altre richieste.
###### (b) Due pagine web distinte (per esempio, www.mit.edu/research.html e www.mit.edu/students.html) possono essere inviate sulla stessa connessione persistente.
Sí,poiché la connessione é stata instaurata con lo stesso server mit.edu
###### (c) Con connessioni non persistenti tra browser e server di origine, un singolo segmento TCP può portare due diversi messaggi di richiesta HTTP.
Falso, é possibile inviare una sola richiesta attraverso TCP.
###### (d) L’intestazione Date: nel messaggio di risposta HTTP indica quando è stato modificato per l’ultima volta l’oggetto nella risposta.
Falso, l'header date indica il momento nel quale é stato prelevato l'ogetto dal server e inserito nel messaggio di risposta.
###### e) I messaggi di risposta HTTP non possono avere il corpo del messaggio vuoto.
Falso, i messaggi di risposta tipo moved o not found hanno corpo vuoto.

###### Considerate un client HTTP che voglia recuperare un documento web da un determinato URL e che l’indirizzo IP del server HTTP non sia noto inizialmen- te. In questo scenario, oltre a HTTP, quali protocolli a livello di trasporto e di applicazione sono richiesti?
Il protocollo attraverso il quale é possibile venire a conoscenza dell'indirizzo IP del server di destinazione é il protoollo DNS(domain name system), il quale utilizza UDP come protocollo di connessione di livello inferiore. HTTP utilizza invece connessioni TCP.

##### Considerate la seguente stringa di caratteri ASCII catturata da Wireshark quando il browser ha inviato un messaggio HTTP GET (cioè questo è l’effettivo contenuto del messaggio HTTP GET).  Rispondete alle seguenti domande, indicando dove, nel messaggio HTTP GET seguente, trovate le risposte.
```http
GET /cs453/index.html HTTP/1.1
Host: gaia.cs.umass.edu
User-Agent: Mozilla/5.0 (Windows;U; Windows NT 5.1; en-US; rv:1.7.2) Gecko/20040804 Netscape/7.2 (ax) 
Accept:ext/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5
Accept-Language: en-us,en;q=0.5
Accept-Encoding: zip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 300
Connection:keep-alive
```
###### (a) Qual è la URL del documento richiesto dal browser?
L'url richiesto dal browser é gaia.cs.umass.edu/cs453/index.html
###### (b) Qual è la versione di HTTP che sta usando il browser?
La versione di HTTP utulizzata é 1.1
###### (c) Il browser richiede una connessione persistente o non persistente?
Il browser sta richiedendo una connessione persistente
###### (d) Qual è l’indirizzo IP dell’host sul quale è in esecuzione il browser?
L'indirizzo IP del mittente non é conosiuto poiché é noto dai datagrammi IP e non dai messaggi HTTP
######  (e) Che tipo di browser invia il messaggio? Perché è necessario che in un messaggio di richiesta HTTP ci sia il tipo di browser?
Lo user agent dal quale é statta inviata la richiesta é Firefox su un'host che usa SO Windows. Questo é necessario poiché il browser puó inviare versioni diverse dello stesso oggetto in base allo user agent.

###### Supponete di selezionare, all’interno del browser, un collegamento ipertestuale per ottenere una pagina web. L’indirizzo IP dell’URL relativo non si trova nella cache del vostro host locale, e dunque è necessaria una ricerca DNS per ottenerlo. Supponiamo di visitare $n$ DNS server prima di ricevere l’indirizzo IP dal DNS. Le visite successive incorrono in un RTT di $RRT_1,\dots,RTT_n$. Supponete inoltre che la pagina web associata al collegamento contenga un solo oggetto consistente in una piccola quantità di testo HTML. Chiamiamo $RTT_0$ il valore di RTT tra l’host locale e il server contenente l’oggetto. Supponendo nullo il tempo di trasmissione dell’oggetto, quanto tempo intercorre tra l’attimo del clic sul collegamento e la ricezione dell’oggetto presso il client?
Il tempo necessario a conoscere l'indirizzo IP attraverso query DNS é $\sum^{n}_{1}RTT_n$.
Il tempio imppiegato per instaurare la connessione e mandare la richiesta attraverso l'handshake a 3 vie é $2RTT$. Il tempo richiesto a trasmettere la risposta con l'oggetto é nullo quindi $T_{tot}=\sum^{n}_{1}RTT_n+2RTT$.

##### In riferimento al Problema precedente, supponete che il file HTML referenzi otto oggetti molto piccoli sullo stesso server. Ignorando il tempo di trasmissione, quanto tempo intercorre con
###### (a) HTTP non persistente e senza connessioni TCP parallele?
Con connessioni non persistenti e tempo di trasmissione ininfluente allora si impiegherá
$\sum^{n}_{1}RTT_n+2RTT+2RTT\times 8$ per ricevere tutti gli oggetti.
###### (b) HTTP non persistente e il browser configurato per gestire 5 connessioni TCP parallele?
Potendo contare su 5 connessioni parallele $\sum^{n}_{1}RTT_n+2RTT+2RTT\times ceil(8/5)$ 
###### (c) HTTP persistente?
Se la connessone é persistente allora $\sum^{n}_{1}RTT_n+2RTT+8RTT$

###### Qual è la differenza tra MAIL FROM: in SMTP e From: nel messaggio di posta elettronica stesso?
Mail from é un comando utilizzabile durante l'invio della mail attraverso protocollo SMTP, mentre il campo From d una Mail é un campo dell'intestazione

###### Come si indica la fine del corpo del messaggio in SMTP? E in HTTP? Può HTTP usare lo stesso metodo di SMTP? Perché?
La fine del corpo di un messaggio é delimitata da una riga contenente soltanto un punto.
HTTP utilizza l'header content-length per delimitarne la lunghezza, e non potrebbe utilizzare lo stesso metodo perché HTTP puó trsportare dati binari mentre SMTP é vincolato dalla formattazione in ASCII 7bit.

##### Considerate l’accesso alla vostra posta elettronica tramite POP3.
###### (a) Supponete che il vostro client di posta sia configurato per operare in modalità “scarica e cancella”. Completate la seguente transazione:
```POP3
C: list
S: 1 498
S: 2 912
S: .
C: retr 1
S: bla bla ...
S: ..........bla
S: .
? C: dele 1
? C: quit
```

###### (b) Supponete che il vostro client di posta sia configurato per operare in modalità “scarica e mantieni”. Completate la seguente transazione:
```POP3
C: list
S: 1 498
S: 2 912
S: .
C: retr 1
S: bla bla ...
S: ..........bla
S: .
? C: quit
? S: OK
```

###### (c) Ipotizzate che il vostro client di posta sia configurato per operare in modalità “scarica e mantieni”. Usando i risultati del punto (b), supponete che voi recuperiate i messaggi 1 e 2, usciate dal POP e cinque minuti più tardi vi accediate ancora per scaricare nuovi messaggi di posta elettronica. Immaginate che in tale intervallo non vi sia stato inviato alcun messaggio. Producete una trascrizione di questa seconda sessione POP.
```POP3
C: list
S: 1 498
S: 2 912
S: .
C: retr 1
S: bla bla ...
S: ..........bla
S: .
C: retr 2
S: bla bla ...
S: ..........bla
S: .
C:quit
```

###### Supponete di poter accedere alla cache del DNS server locale del vostro dipartimento. Sapreste indicare un modo per determinare sommariamente quali sono i web server esterni più popolari tra gli utenti del vostro dipartimento? Spiegate tale metodo.
Possiamo osservare i record presenti nella cache DNS, prendendo piú snapshot e osservando se sono presenti dei record in comune. 

###### Supponete che il vostro dipartimento abbia un DNS server locale per tutti i computer del dipartimento. Voi siete un utente ordinario, non un amministratore i rete o di sistema. Potreste determinare se un sito web esterno è stato probabilmente visitato un paio di secondi fa da un computer del dipartimento? Come?
É possibile misurando il tempo impiegato a ottenere l'indirizzo IP dato un'hostname attraverso comandi come Dig e nslookup oppure richiedendo un'oggetto attraverso una richiesta HTTP. Se ci inpiegamo un tempo molto basos probabilmente un record di tipo A riferito all'hostname era nella cache DNS e quindi era statovisitato di recente.

### Esercizi Sito
#### Esercizio 1
Imagine that you are trying to visit www.enterprise.com, but you don't remember the IP address the web-server is running on.  
  
Assume the following records are on the TLD DNS server:
- (www.enterprise.com, dns.enterprise.com, NS)
- (dns.enterprise.com, 146.54.250.21, A)

Assume the following records are on the enterprise.com DNS server:
- (www.enterprise.com, west3.enterprise.com, CNAME)
- (west3.enterprise.com, 142.81.17.206, A)
- (enterprise.com, mail.enterprise.com, MX)
- (mail.enterprise.com, 247.29.130.191, A)

![[Pasted image 20230618155053.png]]

###### What transport protocol(s) does DNS use: TCP, UDP, or Both?
Both
> 	UDP utilizza primariamente UDP, non só dove c'é scritto che utilizza anche TCP.
###### What well-known port does DNS use?
53
###### In the above example, how many unique type of Resource Records (RR) are there at the authoritative enterprise.com DNS server?
3
###### Can you send multiple DNS questions and get multiple RR answers in one message? Answer with Yes or No
Yes, a DNS message allaws for multiple answers and questions
###### To which DNS server does a host send their requests to? Answer with the full name
Local DNS Server
###### Which type of DNS server holds a company's DNS records? Answer with the full name
Authoritative DNS server
###### In the example given in the problem, what is the name of the DNS server for enterprise.com?
dns.enterprise.com
###### When you make the request for www.enterprise.com, your local DNS requests the IP on your behalf. When it contacts the TLD server, how many answers (RR) are returned?
2
###### In the previous question, there were two responses, one was a NS record and the other an A record. What was the content of the A record? Answer with the format: "name, value"
dns.enterprise.com, 146.54.250.21
###### Assume that the enterprise.com website is actually hosted on west3.enterprise.com, what type of record is needed for this?
CNAME
###### Now imagine we are trying to send an email to admin@enterprise.com, and their mail server has the name mail.enterprise.com. What type of record will contain the name of the enterprise.com domain and the name of its mailserver(s)?
MX
###### In that MX record, what are the contents? Answer with the format: "name, value"
enterprise.com,mail.enterprise.com
###### Does your local DNS server take advantage of caching similar to web requests? Answer with Yes or No
Yes

#### Esercizio 2
Assume that a user is trying to visit gaia.cs.umass.edu, but his browser doesn't know the IP address of the website. In this example, examine the difference between an iterative and recursive DNS query.
![[Pasted image 20230618163938.png|600]]

##### Domande route Iterativa
###### Between steps 1 and 2, where does the Local DNS server check first?
DNS Root
###### Between steps 2 and 3, assuming the root DNS server doesn't have the IP we want, where does the response link?
TLD DNS server
###### Between steps 4 and 5, assuming the TLD DNS server doesn't have the IP we want, where does the response link?
Authoritative DNS
###### Between steps 6 and 7, the authoritative DNS server responds with the IP we want. What type of DNS record is returned?
A

#### Problema 3
Suppose within your Web browser you click on a link to obtain a Web page. 
The IP address for the associated URL is **not cached** in your local host, so a DNS lookup is necessary to obtain the IP address. 
Suppose that only one DNS server, the local DNS cache, is visited with an with an RTT delay of $RTT_0 = 1 msecs$. Initially, let's suppose that the Web page associated with the link contains exactly one object, consisting of a small amount of HTML text. 
Suppose the RTT between the local host and the Web server containing the object is $RTT_{HTTP} = 78 msecs$.
![[Pasted image 20230618164724.png]]

###### Assuming zero transmission time for the HTML object, how much time (in msec) elapses from when the client clicks on the link until the client receives the object?
Il tempo di trasmissione dell'oggetto é 0, e bisogna interrogare un solo server dns quindi 
$$t_{tot}=RTT_0+2RTT=1+78\times2=157msec$$
###### Now suppose the HTML object references 7 very small objects on the same server. Neglecting transmission times, how much time (in msec) elapses from when the client clicks on the link until the base object and all 7 additional objects are received from web server at the client, assuming non-persistent HTTP and no parallel TCP connections?
Abbiamo 7 oggetti da recuperare oltre all'oggetto che li referenzia, quindi 
$$t_{tot}=RTT_0+2RTT\times 8=1249msec$$
###### Suppose the HTML object references 7 very small objects on the same server, but assume that the client is configured to support a maximum of 5 parallel TCP connections, with non-persistent HTTP.
$$t_{tot}=RTT_0+2RTT+2RTT\times ceil(7/5)=469msec$$
###### Suppose the HTML object references 7 very small objects on the same server, but assume that the client is configured to support a maximum of 5 parallel TCP connections, with persistent HTTP.
$$t_{tot}=RTT_0+2RTT+RTT\times ceil(7/5)=313msec$$
###### What's the fastest method we've explored: Nonpersistent-serial, Nonpersistent-parallel, or Persistent-parallel?
Persistent-parallel

#### Problema 6
Consider an HTTP server and client as shown in the figure below. 
Suppose that the RTT delay between the client and server is 10 msecs;
the time a server needs to transmit an object into its outgoing link is 0.5 msecs; 
and any other HTTP message not containing an object has a negligible (zero) transmission time. 

Suppose the client again makes 80 requests, one after the other, waiting for a reply to a request before sending the next request.

![[Pasted image 20230618170723.png]]

Assume the client is using HTTP 1.1 and the IF-MODIFIED-SINCE header line. 
Assume 40% of the objects requested have NOT changed since the client downloaded them (before these 80 downloads are performed)

###### How much time elapses (in milliseconds) between the client transmitting the first request, and the completion of the last request?
Il file non é stato modificato durande queste 80 richieste, inoltre quindi 
$$T_{tot}=(2RR+0.5)\times 80=(10+0.5)\times 80=$$
824