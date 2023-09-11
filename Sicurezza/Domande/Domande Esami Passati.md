## Crocette
###### Un MAC (message authentication code):
- [ ] associa un messaggio ad una chiave pubblica
- [ ] associa un messaggio ad una chiave pubblica e ad una chiave privata
- [x] permette di verificare integrità e origine di un messaggio
- [ ] permette di verificare integrità e origine di una chiave simmetrica associata ad un messaggio
- [ ] permette di verificare integrità e origine di una chiave asimmetrica associata ad un messaggio
###### Una firma elettronica:
- [ ] associa un messaggio ad coppia di chiavi asimmetriche
- [x] associa un messaggio ad una coppia di chiavi simmetriche
- [x] permette di verificare integrità e origine di un messaggio, ma non ne impedisce il disconoscimento permette di verificare integrità e origine di un messaggio, e ne impedisce il disconoscimento
- [ ] permette di verificare l’integrità di un messaggio, ma non la sua origine
###### Un firewall applicativo:
- [ ] É stateless e valuta se bloccare un pacchetto IP in base al solo contenuto del suo header IP  
- [ ] É stateless e valuta se bloccare un pacchetto IP in base al solo contenuto dei suoi header IP e TCP  
- [ ] É stateless e valuta se bloccare un pacchetto IP in base al solo contenuto dei suoi header IP, UDP e TCP  
- [ ] É stateful e può analizzare il payload del pacchetto
- [ ] É stateful ma non può analizzare il payload del pacchetto
###### Un cifrario a chiave pubblica:
- [ ] Prevede l’utilizzo di una chiave condivisa tra ogni coppia di utenti
- [ ] Prevede l’utilizzo di due chiavi condivise tra ogni coppia di utenti (una privata e una pubblica)
- [x] Prevede l’utilizzo di una chiave privata e una pubblica per ogni utente  
- [ ] Prevede l’utilizzo di una chiave pubblica distribuita a tutti, e di una chiave privata condivisa con un solo altro soggetto
- [ ] Prevede uno scambio di chiavi sicuro, ma non permette di cifrare direttamente un testo
###### Il principio di Kerckhoffs:
- [ ] Richiede di ottenere sicurezza nascondendo chiavi e algoritmi  
- [x] Richiede di ottenere sicurezza nascondendo chiavi, ma mantenendo pubblici gli algoritmi  
- [ ] Richiede di ottenere sicurezza nascondendo gli algoritmi, ma mantenendo pubbliche le chiavi
- [ ] Richiede di oscurare il contenuto dei dati personali secondo la normativa GDPR  
- [ ] Suppone di ottenere sicurezza nascondendo indirizzi IP
###### L’attacco noto come XSS (Cross site scripting):
- [ ] Si basa sul riempimento di un buffer oltre il suo limite, andando a sovrascrivere la memoria adiacente
- [ ] Si basa sul riempimento di un buffer oltre il suo limite, andando a sovrascrivere il program counter  
- [ ] Si basa sull’invio di input malevolo, che sarà eseguito sul back-end di un Web server
- [x] Si basa sull’invio di input malevolo, che sarà eseguito nel Browser  
- [ ] Si basa sullo scambio di due siti con javascript, uno corretto e uno malevolo con una URL simile
###### Il sequence number utilizzato in IPSEC serve per contare
- [ ] i byte al fine di eliminare pacchetti ripetuti
- [ ] i pacchetti al fine di eliminare pacchetti ripetuti  
- [ ] le connessioni TCP al fine di bloccare collegamenti pericolosi
- [ ] i byte al fine di ritrasmettere pacchetti persi
- [ ] i pacchetti al fine di ritrasmettere pacchetti persi  
- [ ] le connessioni TCP al fine di riaprire connessioni interrotte
###### Il cifrario noto come ‘one time pad’
- [ ] è un cifrario asimmetrico completamente sicuro  
- [ ] usa chiavi asimmetriche della stessa lunghezza  
- [ ] usa chiavi asimmetriche lunghe quanto il testo da cifrare  
- [x] usa chiavi simmetriche lunghe quanto il testo da cifrare  
- [ ] usa chiavi simmetriche di qualsiasi lunghezza e da utilizzarsi una volta sola
###### Una certificate revocation list (CRL) elenca:
- [ ] i fingerprint dei certificati che sono stati revocati fino alla data attuale
- [ ] i sequence number dei certificati che sono stati revocati fino alla data attuale
- [ ] i sequence number certificati che sono stati revocati fino alla data dell’ultima modifica
- [ ] i sequence number dei certificati che sono stati revocati fino alla data della prossima modifica
- [ ] i fingerprint dei certificati che sono stati revocati fino alla data della prossima modifica
###### lo standard ISO 27001 prevede un ciclo con 4 fasi:
- [ ] Plan, Act, Check, Do
- [x] Plan, Do, Check, Act
- [ ] Plan, Verify, Check, Do
- [ ] Plan, Verify, Do, Check
- [ ] Plan, Verify, Do, Act
###### il sistema di scambio chiavi di Diffie-Hellman si basa
- [ ] sulla difficoltà di moltiplicare due numeri primi
- [ ] sulla difficoltà di fattorizzare un numero primo
- [ ] sulla difficoltà di fattorizzare il prodotto di due numeri primi
- [x] sulla difficoltà di calcolare il logaritmo discreto
- [ ] sulla difficoltà di calcolare l’inverso moltiplicativo di un numero
###### Nello standard ISO 27001 i “controlli” sono:
- [ ] Verifiche periodiche da fare sui firewall  
- [x] Verifiche periodiche da fare sui sistemi applicativi
- [ ] Le verifiche fatte dal certificatore
- [ ] Le verifiche fatte da Accredia  
- [ ] Delle misure di sicurezza da implementare
###### Il sistema di Diffie-Hellman:
- [ ] Permette di autenticare gli utenti  
- [ ] Permette di autenticare i messaggi
- [ ] Permette di scambiare chiavi simmetriche cifrandole
- [x] Permette di condividere chiavi simmetriche in modo sicuro
- [ ] Permette di scambiare chiavi simmetriche utilizzando un MAC
###### Un firewall con HA (High Availability):
- [ ] È normalmente realizzato in una configurazione con load-balancing  
- [ ] È normalmente realizzato in una configurazione con DNS round-robin
- [x] È normalmente realizzato in una configurazione con fail-over 
- [ ] È un firewall application-aware  
- [ ] È un firewall di tipo packet-filter che evita la perdita di pacchetti
###### Per effettuare un’analisi del rischio secondo la metodologia OWASP, si utilizza la formula:
- [ ] Probabilità = f(gravità del rischio, vulnerabilità)  
- [x] Gravità del rischio = f(probabilità,impatto)  
- [ ] Probabilità = f(agente della minaccia, impatto)  
- [ ] Impatto = f(impatto tecnologico, probabilità)  
- [ ] Gravità del rischio = f(impatto tecnologico, impatto di business)
###### In una VPN “tunnel”
- [ ] è tutto cifrato, tranne il MAC address  
- [ ] l’indirizzo IP del solo terminatore sorgente è cifrato  
- [ ] gli indirizzi IP di entrambi i terminatori sono cifrati  
- [ ] il reale indirizzo IP sorgente è cifrato  
- [ ] il reale indirizzo IP sorgente è in chiaro
## Diffie-Hellman
###### Discutere il paradosso del compleanno, generalizzato per un anno di N giorni e per un gruppo di K persone.
Immaginiamo che in una stanza ci siano N persone, vogliamo calcolare la probabilità che almeno due di queste abbiano lo stesso compleanno.

La probabilitá $P(no\;ripetizioni)$ che tutti abbiano compleanni diversi é
$$\frac{N}{N}\times \frac{N-1}{N}\times \dots \times \frac{N-K+1}{N}$$
La probabilitá che almeno due persone abbiano lo stesso compleanno é 1-P(no ripetizioni). Sappiamo inoltre che $1-x<e^{-x}$, quindi $1-P(no\;ripetizioni)>1-e^{P(no\;ripetizioni)}$.

$$
\begin{equation}\begin{split}
1-e^{P(no\;ripetiozioni)}&=1-e^{-(\frac{1}{n}+\frac{2}{n}+\dots + \frac{k-1}{n})}\\
&=1-e^{-\frac{1}{n}(1+2+\dots+(k+1)}\\
&=1-e^{\frac{-(k-1)k}{2n}} \approx 1-e^{\frac{-k^2}{2n}}
\end{split}\end{equation}
$$

Quindi la probabilitá che due persona abbiano lo stesso compleanno con probabilitá maggiore ad $\frac{1}{2}$ se $k>1,18\times \sqrt n$ .


###### Enunciare il Teorema di Eulero e il Piccolo Teorema di Fermat. Dimostrare che il secondo è un corollario del primo.
###### Definire il metodo di scambio di chiavi di Diffie-Hellman
Lo scambio di chiavi di diffie-hellman é una tecnica che permette lo scambio di una chiave simmetrica in maniera sicura ed é basato su operazioni di aritmetica modulare, in particolaritá la difficoltá di calcolare il logaritmo discreto.

Lo schema é cosí composto:
due soggetti conoscono due valori
- $q$: un numero primo
- $a$: la sua radice primitiva

vogliamo quindi creare una chiave condivisa tra i due utenti A e B:
- A sceglie un intero $X_A<q$ come propria chiave privata, mentre $B$ sceglie $X_B<q$
- A computa la propria chiave pubblica $Y_A=a^{X_B}\mod q$, mentre B computa $Y_B=a^{X_B}\mod q$ 
- A questo punto sia A che B possono calcolare la chiave condivisa $K$, ottenendo lo stesso risultato
	- A calcola $K=(Y_B)^{X_A}\mod q$
	- B calcola $K=(Y_A)^{X_B}\mod q$
###### Discutere, nel metodo di scambio di chiavi di Diffie-Hellman, la complessità computazionale di ciascun passo
###### Algoritmo iterativo per calcolare in modo efficiente l’esponente modulare e sua complessità
## RSA
###### Descrivere l’algoritmo iterativo per il calcolo efficiente dell’esponente modulare
###### Dato il modulo RSA n con i suoi due fattori primi p e q, e la chiave pubblica e, descrivere un metodo per calcolare la chiave privata d
###### Definire la generazione di chiavi RSA e indicare la complessità computazionale di ogni passo
## Autenticazione
###### Discutere la differenza tra una funzione di hash e un MAC (message authentication code)
Una funzione di hash é un a funzione che, dato un blocco di lunghezza variabile, restituisce un blocco di lunghezza fissa, mentre un MAC, o message autentication code, é un codice generato a partire da un messaggio utilizzando una chiave simmetrica.

Entrambi serveno a garantire che il messaggio non é stato modificato, input uguali restituiscono risultati uguali, ma il MAC serve anche a garantire che il messaggio arrivi dalla fonte corretta, garantendone l'autenticitá.

Anche se i MAC utilizzano cifrarti simmetrici ne esistono varianti che utilizzano funzioni di hash, poiché sono molto economiche da implementare.
## Network security
###### Descrivere il concetto di DDOS (distributed denial of service)
## Software security
###### Descrivere alcune possibili contromisure agli attacchi di “buffer overflow”
Il buffer overflow é un bug software che s verifica quando dei dati vengono copiati in un'area di memoria ed eccedono lo spazio a loro disposizione.

Negli anni sono stati presentati delle contromisure piú o meno efficaci:
- canarino: un valore scritto sullo stack tra il buffer e le variabili localki per rilevare i buffer overflow. Esso viene inserito durante la compilazione con l'idea che, in caso di bof, il valore verrebbe sovrascritto, e in caso di altereazione, l'esecuzione verrebbe bloccata
- ASLRL: l'address space layout randomization é un meccanismo di sicurezza che randomizza gli indirizzi di memoria utilizzati dal sistema operativo quando alloca la memoria del programma, in modo da evitare che l'intera memoria sia contigua, rendendo possibili gli attacchi.
- Separare lo spazio di Memoria del codice dai dati
- stack non eseguibile
###### Descrivere il funzionamento delle chiamate di funzione, con riferimento all’architettura IA32
Quando viene eseguita la chiamata di una funzione tramite l'istruzione `call`, viene sempre eseguito un prologo:
```asm
push ebp
move ebp,esp
sub esp,value
```
Viene pushato il base pointer sullo stack, in modo da salvarlo, per poi sostituirlo con lo stack pointer, in questa maniera possiamo referenziare l'indirizzo di inizio di un nuovo frame coem se stessimo usando l'intero stack.
Il terzo passaggio modifica lo stack pointer, decrementandolo, poiché in IA86 lo stack cresce verso il basso, per far spazio ai paramentri e variabili locali.

Al termine dell'esecuzione vengono invertiti le opeazioni compiute nel prologo, per far tornare l'esecuzione al metodo chiamante, attraverso un preambolo:
```
move esp,ebp
pop ebp
ret
```
si ripristina quindi  lo stack pointer precedente alla chiamata, si rimuove il base pointer dallo stack, per poi ritornare alla funzione chiamante, seguendo il program counter precedente.
###### Fare un esempio di codice vulnerabile rispetto ad attacchi di buffer overflow e spiegare il funzionamento dell’attacco riferito a quello specifico esempio di codice, per l’architettura IA32
Prediamo come esempio il seguente codice:
```c
in main(int argc, char* argv){
	int cookie;
	char* buffer[80];
	
	buffer = gets();
	if (cookie == 0x41424344)
		printf("you win\n")
}
```
il codice utilizza una funzione pericolosa, poiché non verifica la lunghezza dell'output prima della scrittura nel buffer. Un attaccante puó quindi inviare un'output piú lungo del buffer per eseguire un buffer overflow, tentando di sovrascrivere il cookie per ottenere l'output. Questo é possibile perché:
- non vengono effettuati controlli
- lo stack é su una posizione di memoria contigua

Per riempire completamente il buffer bastano 80 caratteri, genera 
###### Descrivere il funzionamento dello stack nell’architettura Intel IA32 e illustrare due distinti modi di modificare l’esecuzione di un programma mediante stack overflow
###### Spiegare il “bit s” nel controllo di accesso ai sistemi Unix, e perché può essere pericoloso in presenza di vulnerabilità di un eseguibile

## Firewall
###### Scrivere le ACL di un firewall che protegge la rete locale 212.32.11/24 in modo che:
1. siano permessi la navigazione web e l’accesso alla posta elettronica
2. sia raggiungibile dall’esterno il Web server 212.32.11.220

Azione|Protocol|Source-addr|Dest-Addr|Source-port|Dest-port|Flag
--|--|--|--|--|--|--
allow|TCP|\*|212.32.11.220|\*|80|/
allow|TCP|212.32.11.220|\*|80|\*|ACK
allow|TCP|212.32.11.\*|\*|\*|80|/
allow|TCP|\*|212.32.11.\*|80|\*|ACK
allow|TCP|212.32.11.\*|\*|\*|POP3-port|/
allow|TCP|\*|212.32.11.\*|POP3-port|\*|ACK
deny|\*|\*|\*|\*|\*|\*
###### Scrivere le ACL di un firewall che protegge la rete locale 135.32.10/24 in modo che:
1. siano permessa la navigazione web sia su http che su https
2. sia raggiungibile dall’esterno il Web server 135.32.10.220 sia su http che su https

Azione|Protocol|Source-addr|Dest-Addr|Source-port|Dest-port|Flag
--|--|--|--|--|--|--
allow|TCP|135.32.10.\*|\*|\*|80|\*
allow|TCP|\*|135.32.10.\*|80|\*|ACK
allow|TCP|135.32.10.\*|\*|\*|443|\*
allow|TCP|\*|135.32.10.\*|443|\*|ACK
allow|TCP|\*|135.32.10.220|\*|80|\*
allow|TCP|135.32.10.220|\*|80|\*|ACK
allow|TCP|\*|135.32.10.220|\*|443|\*
allow|TCP|135.32.10.220|\*|443|\*|ACK
deny|\*|\*|\*|\*|\*|\*
###### Scrivere le ACL per un firewall packet filter necessarie per permettere il traffico web (http, porta 80) e pop3 (porta 110), solo se generato da richieste originate da un client interno alla LAN 130.192.0.0/16, e per permettere l’accesso anche dall’esterno a 2 web server interni con IP address 130.192.157.128 e 130.192.157.158.
Azione|Protocol|Source-addr|Dest-Addr|Source-port|Dest-port|Flag
--|--|--|--|--|--|--
allow|TCP|130.192.\*.\*|\*|\*|80|\*
allow|TCP|\*|130.192.\*.\*|80|\*|ACK
allow|TCP|130.192.\*.\*|\*|\*|110|\*
allow|TCP|\*|130.192.\*.\*|110|\*|ACK
allow|TCP|\*|130.192.157.128|\*|80|\*
allow|TCP|130.192.157.128|\*|80|\*|ACK
allow|TCP|\*|130.192.157.158|\*|80|\*
allow|TCP|130.192.157.158|\*|80|\*|ACK
deny|\*|\*|\*|\*|\*|\*
###### A che cosa serve un firewall?
Un firewall  é un dispositivo hardware installato su una rete al fine di filtrare i pacchetti in ingresso e in uscita su una rete in modo da fornire un ulteriore grado di protezione. Svolge inoltre la funzione di log delle azioni degli utenti e del traffico di rete.

Di questo ne esistono due tipologie: 
- packet filter: filtra i pacchetti a livello di rete
- application filter: filtra i pacchetti a livello applicativo
entrambi con i propri limiti e le propri vantaggi.
###### Discutere i limiti di un firewall di tipo packet filter
Un packet filter é stateteless, non ha quindi memoria delle connessioni precedenti e non é quindi in grado di contestualizzare una connessione.

Questo puó causare alcuni problemi, come nel caso della frammentazione TCP, infatti se il frammento é talmente piccolo da non contenere neanche l'header TCP, allora il firewall non é in grado di effettuare i controlli secondo l'ACL,quindi solitamente i pacchetti troppo piccoli vengono scartati a priori.

Inoltre alcuni protocolli a livello applicativo, come nel caso di FTP, prevedono l'instaurazione di piú connessioni per vari motivi, e gestire l'instaurazione di queste tramite packet filter vorre poter dire che chiunque puó instaurare una connessione con un host.
## VPN
###### Descrivere il protocollo ESP di IPSEC, illustrando anche graficamente il formato del suo Header
###### Descrivere il concetto di “Reverse Proxy” e discuterne l’utilità
## Web Application Security
###### Descrivere, con l’ausilio di uno schema grafico, l’attacco XSS (cross site scripting).
Il cross site scripting(XSS) é una vulnerabilitá di un sito che perrmette ad un attaccante di far eseguire al browser di una vittima, che sta visitando una pagina compromessa, un script javascript da lui controllato.

Ne esistono due categorie principali: stored e reflected.
Andiamo ad analizzare una reflected XSS: 
## Risk management
###### Spiegare in che cosa consiste e come si può ottenere la certificazione ISO 27001
Con ISO 27001 si intendono lo standard e la certificazione per la gestione della sicurezza delle informazioni. Indirizza la gestione del rischio informatico nel contensto della gestione dei rischi aziendali.

Esso mira alla creazione di un sistema di gestione della sicurezza, l ISMS(information system management security), del quale lo standard fornisce i requisiti e le tecniche per mantenerlo secondo l'approccio a processi.

Una volta sviluppato il proprio ISMS bisogna comunicare con un organismo di certificazione, fornire il proprio statement of applicability ed illustrare l’ISMS e solo a questo punto si potrà ottenere la certificazione.
###### Descrivere il ciclo Plan-Do-Check-Act secondo lo standard ISO-27001
