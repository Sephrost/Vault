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
Una sessione POP3 un modalitá "scarica e cancella" cancella le mail scaricate al termine della stessa, mentre in modalitá "scarica e mantieni" le mail vengono tenute in memoria anche dopo il termine della sessione. 