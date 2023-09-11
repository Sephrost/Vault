Le **VPN** sono un oggetto del livello di rete con lo scopo di **collegarsi** ad una **rete privata** pur non trovandosi fisicamente in loco.

Si utilizza una VPN per soddisfare diversi requisiti:
- Avere la stessa sicurezza che avremmo con un un’unica rete locale
- Permettere anche traffico da e verso reti esterne, se necessario attraverso un Firewall
- Non introdurre ritardi significativi
- Non richiedere operazioni di riconfigurazione agli utenti (trasparenza)

## Modi per fare una VPN
Esistono due modi diversi con cui comunicare tramite VPN.
### Tunneling
Il **tunneling** è la versione più adottata poiché tipica dell’ambiente lavorativi.

Sfruttiamo due oggetti chiamati **terminatori VPN** che effettuano la connessione VPN e, come un NAT, modificano l’indirizzo IP sorgente del pacchetto con un proprio indirizzo IP.

![[Pasted image 20230904165418.png|500]]
Il traffico è sicuro sulla rete geografica ma non sicuro sulla rete locale(non protegge da sniffing/spoofing su rete locale).
Abbiamo però il vantaggio che questa tecnica è trasparente (l’utente non sa nulla e non deve installare nulla) e che è molto efficiente.

Riassumendo:
- Non protegge da sniffing/spoofing su rete locale
- Nasconde gli indirizzi dei singoli computer mittente e destinatario, non nasconde gli indirizzi della rete mittente e destinazione
- É trasparente all'utente singolo
- Veloce, prodotti affidabili per router/firewall
### Transport
Questa tecnica inserisce il pacchetto direttamente in VPN nel momento della trasmissione sulla rete, e quindi sul computer mittente e destinatario.
![[Pasted image 20230904170229.png|500]]

Per ottenere questo approccio ogni utente deve avere la VPN installata sulla propria macchina. 
Abbiamo però il vantaggio che non è possibile effettuare nessun tipo di spoofing/sniffing del messaggio, neanche in rete locale.

> Le VPN possono essere annidate per una maggiore sicurezza

Riassumendo:
- Protegge da sniffing/spoofing su rete locale
- Rende visibile su Internet gli indirizzi mittente e destinatario
- Richiede una speciale configurazione del computer utente (non trasparente)
- Necessario per traffico da postazione mobile
## IPsec
**IPsec** é è uno **standard** per le reti con l'obiettivo di ottenere **connessioni sicure** su **reti IP**.
L'**header** ipsec viene aggiunto **dopo** quello **IP**, mantenendo il pacchetto IP perfettamente valido nonostante la payload(PDU) sia stata cifrata e/o autenticata.

Esso permette di aggiungere le funzionalitá(servizi) di **cifratura** e **autenticazione** ad un traffico di rete(in questo caso della VPN).
L'autenticazione viene effettuata tramite un **Authentication Header** mentre la cifratura tramite un sistema chiamato **ESP**.

> Sia la cifratura che l'autenticazione sono simmetrici.
### AH - Authentication Header
Serve per **autenticare** il traffico IP, normalmente tra due LAN private, per **evitare modifiche** e **falsificazioni**.
![[Pasted image 20230904174911.png|600]]

Esso contiene:
- **Next Header**(*8bit*): identificativo del protocollo di livello superiore in IPv4, o il next header in IPv6 
- **Lenght**(*8bit*): lunghezza dell'header, poiché puó essere variabile
- **Reserved**(*16bit*): riservato per il futuro e attualmente non usato
- **SPI**(*32bit*): indice dell'algoritmo di hash utilizzato e della chiave simmetrica
- **Authentication Data**(*multiplo di 32bit*): Codici di autenticazione (MAC) riferiti a tutto il pacchetto.

Il **MAC** viene calcolato su **header IP**,**header AH** e **PDU**.

I campi variabili(TTL,checksum e MAC non ancora calcolato), vengono posti temporaneamente a 0 durante il calcolo del MAC.
### ESP - Encapsulating Security Payload
Serve per cifrare il traffico IP, normalmente tra due LAN private, per evitare intercettazioni.

> ESP è molto “particolare” poiché lavora sul datagram transport/application pur vivendo a livello IP.

Ancora una volta, esso viene aggiunto dopo l'header IP, poiché esso innesterá il pacchetto a livello di trasporto e applicativo.
![[Pasted image 20230904182644.png]]
#### Modalitá tunnel
Nella modalità Tunnel, ESP introduce un header ed un trailer incapsulando IP in nuovo Header IP, cifrando:
- L’header IP originale
- l’header TCP ed il payload

Inoltre autentica:
- L’header IP originale
- l’header TCP ed il payload

Infine, aggiunge un HMAC in coda.
![[Pasted image 20230908195837.png|600]]
#### Modalitá transport
Nella modalità transport viene sempre aggiunto un Header/Trailer ESP ma cambia il perimetro di cifratura ed autentificazione.
Viene autenticato:
- ESP Header/Trailer, 
- Header TCP 
- Payload
mentre vengono cifrati
- TCP
- Payload
![[Pasted image 20230908195558.png|600]]

É composto da:
- **SPI**: analogo all'autentication header, scritto in chiaro
- **Sequence Number**: misura anti-replay, ovvero duplecazione di pacchetti. Viene utilizzata una **sliding-window**, lunga $W$,configurabile,come bit-vector dove tengo traccia dei pacchetti arrivati o no, settando a 1 i pacchetti arrivati. Quando arriva un pacchetto, controllo il sequence number, controllo il bit-vector e se è già stato contrassegnato come 1 lo scarto(**anti-replay**). Ogni pacchetto(e non byte come in TCP), viene numerato.
- Eventuale header IP incapsulato
- PDU cifrata
- Padding
- Padding length
- Next Header

