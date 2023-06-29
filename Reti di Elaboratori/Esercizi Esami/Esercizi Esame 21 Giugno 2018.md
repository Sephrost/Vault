#### Esercizio 1
Facendo riferimento allo scenario delineato nella seguente figura, illustrate il funzionamento di un router che implementala funzione di NAT.
![[Pasted image 20230626153513.png]]

Nella figura sono indicati gli indirizzi degli host sulla rete locale e i due indirizzi del router, quello sulla rete locale e quello sulla rete pubblica (indirizzo 138.76.29.7). 
In particolare, fare riferimento alla sequenza di eventi:
1. l’host con indirizzo 10.0.0.1 invia un pacchetto di livello transport (es. un segmento TCP) ad un’applicazione in esecuzione sull’host con indirizzo 128.119.40.186 (esterno alla rete) porta 80, 
2. l’applicazione identificata dalla coppia 128.119.40.186 / porta 80 invia una risposta all’host mittente.

Rispondere ai seguenti quesiti
###### Specificare gli indirizzi mittente e destinatario e le porte locale e remota relativamente al pacchetto TCP (e datagram IP) che viene spedito dall’host 10.0.0.1.
Source: 10.0.0.1, 10000
Destination: 128.119.40.186:80
###### Quale è il primo hop del pacchetto?
Il pacchetto viene inviato al router, che modificherá l'indirizzo e la porta di origine
###### Come viene “riscritto” dal router NAT il pacchetto?
Sovrascriverá l'indirizzo di origine 10.0.0.1 con il proprio e la porta di origine con una nuova appena assegnata(es:3301)
###### Cosa viene riportato nella tabella del NAT?
Nella tabella NAT verrá riportata una righa con valori Indirizzo lato WAN 10.0.04:3301 e indirizzo lato LAN 10.0.0.4:10000
###### Specificare gli indirizzi mittente e destinatario e le porte locale e remota relativamente al pacchetto TCP di risposta (e datagram IP) che viene inviato dall’host 128.119.40.186.
Mittente: 128.119.40.186:80
Destinatario: 10.0.0.4:3301
###### Come viene riscritto dal router NAT tale pacchetto di risposta?
Il router sostituisce l'indirizzo di destinazione con quello indicato nella tabella di traduzione, stessa cosa per la porta di destinazione

#### Esercizio 2
Si consideri l’invio di un datagramma di 3500 bytes su un collegamento con MTU pari a 1000 bytes. 
Si supponga che il datagramma originale abbia come identificatore il numero 422 (campo Identifier del datagram). 
###### In quanti frammenti verrà scomposto il datagramma? 
Poiché sul collegamento si possono trasmettere al massimo 1000 bytes per volta , il datagramma deve essere frammentato in $\lceil3500/1000\rceil=4$ frammenti 
###### b) Indicare i valori nei vari campi di ciascun frammento generato (fare riferimento solo ai campi che sono in relazione con il processo di frammentazione)
I campi d'intestazione utilizzati nel processo di frammentazione IP sono 3:
- identificatore 
- flag
- offset di frammentazione
frammento 1: 1,1,0
frammento 2: 1,1,1
frammento 3: 1,1,2
frammento 3: 1,0,3

#### Esercizio 3