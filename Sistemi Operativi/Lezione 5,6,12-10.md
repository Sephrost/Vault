## Prelazione
Meccanismo che permette al sistema operativo di sottrarre una risorsa(cpu) ad un processo running.

Richiede un supporto hardware, quindi l'architettura deve fornire degli strumenti per consentirne il funzionamento.

### Riassegnazione

E' possibile riassegnare le risorse quando:
- Un processo **running** diventa **waiting**
- Il **running** viene riportato a **ready**
- Un processo **waiting** diventa **ready**
- Il processo running **termina**

Il primo e il quarto caso non prevedono prelazione, in quanto eseguono una sistem call , ed e' quindi volontario, quindi solo il secondo e terzo caso la prevedono.

## Inizio e terminazione dei processi

Un processo viene generato da un'altro processo, attraveso un' operazione di **fork**(sistem call), che crea una copia identica del processo parent.

Dopo la generazione il processo nuovo andra' ad eseguire il codice del nuovo processo.

La relazione parent/child viene immagazzinata del sistema, all'interno dell'**albero dei processi**, che presenta una struttura gerarchica, con un processo **init** che ne rappresenta la radice.

Un processo termina il suo nodo all'interno dell'abero viene rimosso, quando i processi child sono gia' terminati come avviene di solito.

Il process control block rimane poiche contiene le informazioni relative alla terminazione del processo,(exit,abort,...),comunicando l'informazione al processo genitore, poiche' possa ispezionarlo attraverso opportune system call, facendo diventare il processo child un processo zombie. Al termine dell'ispezione le informazioni vengono rimosse dalla ram.

Se un processo parent termina prima del processo child viene "adottato" dal processo init, senza accorgersi enanche che il vecchio parent e' terminato, preservando la struttura ad albero.


### Organizzazione della pipeline
Un sistema software puo' quindi essere articolato in tanti processi, organizzandoli in una pipeline.

I processi possono quindi essere:
- cooperanti, ovvero condividono le risorse
	Le informazioni vengono comunicati tra processi, passando i dati, senza controllare cosa avviene a questi. Questo risulta in un'elaborazione piu' veloce, appesantendo pero' il sistema.
- competitivi, ovvero competono per le risorse

#### Modelli di comunicazione
In generale sono 2:
- a memoria condivisa
	Si assegna un'**area di memoria condvisa** sulla ram su cui vari processi esguono operazioni di read/write.
- a scambio di messaggi
 	Puo' essere:
	- diretta, se si conosce il PID, utilizzando un **buffer**, con una quantita' di messaggi che puo' contenere finita
		Si distinguono 3 tipi di buffer:
		- A capacita' 0, se non puo' contenere alcun messaggio, in questo caso il send e' quindi sempre sincrono.
		- A capacita' limitata, se puo' contenere al piu' $n$ messaggi. Se si ricevono messaggi a buffer pieno il caso viene gestito in base al send, se e' sincrono il processo aspetta che si liberi il buffer.
		- A capacita' limitata
	- indiretta, se inviata dalla mailbox
### Send
L'invio dei messaggi tra processi puo' avvenire secondo 2 modalita':
- Sincrona, se il proccesso mittente tiene il messaggio fino a quando questo non viene recapitato al processo ricevente, rimanendo bloccato.
- Asincrona, se il messaggio viene depositato nella mailbox 

### Receive
La ricezzione del messaggio avviene attraverso 2 modalita':
- Sicrona, se il processo sospende l'esecuzione fino alla ricerzione del messaggio
- Asincrona, se si utilizza un meccanismo di polling, ovvero si controlla periodicamente la ricezione del messaggio

### Rendevouz
Il meccanismo per il quale si utilizza una send sincrona e una receive anch'essa sincrona.

Il primo processo ad effettuare l'operazione attende l'altro.

### Implementazione dello scambio di messaggi
#### Socket
E' un sistema Client-Server, ovvero l'interzione tra i due estremi del canale di comunicazione, permettendo ai messaggi di circolare tra i 2 socket.

#### Remote Procedure Call(RPC)
Le procedure(metodi) vengono richieste dai processi richiedenti su macchine diverse.
 Il server esegue il codice, restituendo il risultato.
 
 Con questo metodo i messaggi sono strutturati.
##### Stub
Un codice che permette di trovare la porta "listening" su un web-server.
Questa puo' essere hard coded, ovvero critto del codice, altrimenti passa attraveso un servizio intermediario chiamato **Matchmaker**.

#### Pipe
Possono essere di 2 tipo:
- **Anonima**
	E' un canale di comunicazione **simplex**(in un'unica direzione), nella quale i messaggi vengono accodati e smaltatiti dal processo listen in ordine FIFO.
	
	Un processo crea la pipe anonima, crea un processo figlio e usa la pipe anonima per comunicare con child.
	
	La pipe anonima viene rimossa quando termina il processo creatore.
- **Con nome**
	La comunicazione puo' andare in entrambe le direzioni.
	
	
	
	Al termine del processo creatore la pipe sorpavvive, dovendo disallocarle manulmente quando terminano di utilita'.
	
## Thread
Sono **articolazioni** nell'esezione dei processi, che permettono di velocizzarne l'esecuzione.

Ogni thread **condivide** il codice da eseguire del processo e le sue variabili globali, permettendo di modificarle.

E' composto da: 
- Un TID, un'identificatore del thread
- Uno stack
- Un program counter

Se un processo ha a disposizione piu' cpu possiamo far eseguire in parallelismo reale porzioni diverse dello stesso processo,cedendo l'utilizzo ai vari thread.

Se i thread sono gestiti dal SO si chiamano **thread kernel**, se invece sono generati dall'utente(quindi non privilegiati)si dico **thread utente**, poiche' gestiti da un Process Control Block.

I thread utente non permettono un parallelismo reale, ma permettono di usare i thread su qualunque sistema operativo e implementare meccanismi si **scheduling diversi**, risultando quindi piu' adattabile.Inoltre i  all'interno di uno stesso processo avvengono piu' rapidamente poiche' non e' necessario un interact.D'altro canto, se un thread compie un'azione sosprensiva il processo intero si blocca, in quanto il sistema operativo non visualizza i thread, cosa che non avviene con i thread kernel.

Quando si devono gestire piu' thread, questi si possono **accodare** alla terminazione di un'altro, facendo convergere l'esecuzione.

- 1 ad 1:
	Per ogni thread utente assegno un' unita' di computazione, ovvero un thread kernel
- 1 a molti
	Tanti thread utente vengono assegnati ad un'unica unita' di computazione
- molti a molti

