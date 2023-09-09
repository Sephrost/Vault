Su una **LAN** possono presentarsi **vari problemi**:
- Intrusioni di utenti non autorizzati
- Virus e altri programmi critici per la sicurezza
- **Sniffing**, **Spoofing**
- Spamming, Flooding e denial of service
per i quali sono stati presentati **varie soluzioni**:
- Controllo di accesso su ogni calcolatore
- Firewall (filtro pacchetti e/o proxy)
- Limitare o evitare collegamenti esterni 
- Logging accurato di sessioni interne e esterne, analisi centralizzata dei log
- Programmi di rilevamento delle intrusioni (intrusion detection systems – IDS, intrusion prevention systems - IPS)

Inoltre nelle parti precedenti abbiamo dato per scontato che soltanto la rete in cui passano i dati é insicura, ma non é quasi mai cosí: un **computer manomesso** puó rendere tutti i **meccanismi** di sicurezza che abbiamo trattato **inutili**.

É possibile **limitare** i **danni** introdotti da programmii esterni in diverse maniere:
- **Probire l’installazione** di software eseguita direttamente dall’utente, evitare l’esportazione di dati critici (data loss prevention – DLP)
- Installare programmi **antivirus** e di **endpoint detection and response** (EDR)
- Inserire **filtri antimalware** sui firewall 
- Mantenere **backup** sistematico, prevedere se opportune disaster recovery / business continuity

## Sniffing
Lo **sniffing** è un’operazione che consente, all’interno di una intranet, ad una persona non autorizzata di leggere pacchetti non diretti a lui, ovvero di **intercettare il traffico**.

Esso é:
- Possibile su LAN aziendale o rete locale(in caso di switch diventa piú difficile)
- Possibile ma non comune su rete geografica, infatti bisogna aver accesso alle infrastrutture di rete
### Semplice esempio di sniffing
Immaginiamo una rete connessa tramite ethernet tramite un bus. La particolaritá di ethernet é la comunicazione tramite **brodcast**: i pacchetti vengono inviti in broadcast e scartati a livello fisico dalle schede di rete nel caso l'indirizzo di questi non combacia.

Quindi un avversario é in grado di connettersi alla rete rimuovere il filtro impostando la scheda di rete in **modalitá promisqua**, accettando quindi ogni pacchetto.
### ARP poisoning
Le reti moderno non sono peró collegate unicamente da un bus: sono composte anche da switch, rendendo le comunicazione point-to-point.

> **Funzionamento di ARP**
> Gli **switch** sono dispositivi a livello di collegamento, che dialogano attraverso **indirizzi MAC**, mentre i **router** sono dispositivi a livello di rete, che dialogano attraverso **indirizzi IP**. 
> Quando un pacchetto IP deve essere incapsulato dentro un pacchetto ethernet, lo switch deve saper dove instradarlo, quindi si utilizza ARP per la risolvere l'indirizzo: se é presente nella **cache ARP** si utilizza quello, altrimento lo si richiede attraverso una **ARP request**.

L'**APR poisoning** é una tecnica di sniffing per la quale un **dispositivo**, vedendo arrivare una richiesta ARP che dovrebbe risolvere un'altro indirizzo, **risponde** con il proprio, "**avvelenando**" la **cache** dello switch.

Questo permette di **reindirizzare** il **traffico** verso un'altro dispositivo a se. Successivamente il dispositivo malevolo reindirizzerá i pacchetti al destinatario originale, effettuando l'arp poisoning anche sulla cache del destinatario.

Il dispositivo malevole agisce quindi come uno switch.

Per evitare che tutto questo accada è possibile effettuare dei controlli sui calcolatori ma anche sugli switch in modo da impedire che uno stesso MAC sia associato a più IP.
### Contromisure allo sniffing su LAN
- Usare reti con **switch** (non hub)
- **Cifrare** a livello **applicativo**
- **Cifrare** a livello di **trasporto**
- **Cifrare** a livello **IP** su ogni calcolatore 
- Routing livello 2
	- **ARP statico**
	- **DHCP statico** 
	- rilevamento indirizzi hardware non validi per indirizzo IP
### Contromisure sniffing all'esterno
- Cifrare a livello applicativo
- Cifrare a livello di trasporto
- Cifrare a livello IP su router o firewall 
- Impedire collegamento diretto da rete non controllata
### Spoofing
Lo **spoofing** é la falsificazione di un indirizzo.
In base all'indirizzo specificato, gli attacchi si spoofing si dividono in:
- **MAC Spoofing**: falsificazione di indirizzi fisici(indirizzi MAC) 
- **IP Spoofing**: falsificazione di indirizzi IP 
	- Possibile su rete locale anche con TCP
	- Possibile su rete geografica con UDP
	- In generale impossibile con TCP su WAN
- **DNS Spoofing**: falsificazione di indirizzi simbolici tramite la manomissione di DNS.
	- Configurando i calcolatori con l’indicazione di un DNS server che è possibile controllare
- **Web Spoofing**: falsificazione di indirizzi URL.
	-  inserendo contenuti arbitrari per la URL che è possibile controllare

> Possiamo dire che lo spoofing é necessario per lo sniffing
## Attacchi DOS - Denial of Service
Una applicazione dell’IP spoofng molto usata sono gli attacchi DoS.

Il concetto è quello di **bombardare un server di richieste** in modo che non sia più in grado di svolgere il suo servizio. Esistono anche attacchi DoS che non sfruttano IP spoofing.

Esso puó essere effettuato:
- **saturando** le **risorse** dell'**host**(es: syn flooding)
- **saturando** le **risorse** della **rete**

L'attacco DOS non é di per sé particolarmente pericoloso: lo é se sotto attacco sono servici critici che dovrebbero essere sempre disponibili.
#### DDos - Dos distribuito
In generale, il Dos non é in grado di effettuare grossi danni, poiché il numero di richieste eseguibili é collegato alle risorse a disposizione del dispositivo dell'attaccante.

Un miglioramento puó essere quindi l'utilizzo di **piú dispositivi** distribuiti, attraverso un'attacco **Dos distribuito** o **DDos**.

Solitamente prevedono l'utilizzo di dispositivi zombies, ovvero macchine infettate che compongono una botnet, rendendo l'attacco molto piú efficace.

Ne esistono **due tipi**:
- **diretto**: l'attaccante usa una botnet sotto il suo controllo per inviare richieste alla vittima attraverso gli zombie
- **con reflector**: l'attaccante usa una botnet sotto il suo controllo per inviare richieste a una componente di terze parti che amplifica le richieste inviate tramite esso
#### Syn flooding
É una **variante** di attacco **Dos** che sfrutta il protocollo TPC e in particolare il **three-way handshake**. Esso prevede l'invio di 3 pacchetti TCP con cit SYN posto ad uno.
![[Pasted image 20230903125506.png]]
Ma se il terzo passo dell'handshake non viene portato a termine, il server ha allocato le risorse ma é in attesa di risposta dal client. Facendo molte richieste di connessione TCP al server facendo IP spoofing si é infatti in grado di saturare le risorse del server.
#### ICMP echo request
É un'altra **variante** dell'attacco **Dos** che mira a **saturare** le **risorse di rete** di un host.

Si basa sull'invio di un gran  numero di **echo request** verso un host **reflector**, con un indirizzo IP sorgente falsificato e uguale a quello della vittima. 
Il reflector invierá l'enorme mole di risposte ICMP alla vittima, saturnandone le risorse di rete.
##### Smurf attack
É un caso particolare dell'attacco sopra trattato. 

Consiste nell'**invio** di una **richiesta ICMP echo** alla **sottorete** della vittima, impostando come indirizzo di origine l'indirizzo spoof della vittima.
In questa maniera tutti gli host nella sottorete invieranno la risposta alla vittima, staurandone le risorse di rete.