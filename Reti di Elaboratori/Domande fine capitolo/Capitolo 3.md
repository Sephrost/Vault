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