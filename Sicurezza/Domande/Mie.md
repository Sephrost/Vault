## Introduzione
###### Che cosa si intende con sicurezza di un calcolatore
Con sicurezza di un calcolatore intendiamo i sistemi di sicurezza applicati ad un sistema informatico per garantire la confidenzialitá, la disponibilitá e l'integritá delle risorse del sistema
###### Che cosa indica l'acronimo C.I.A? Spiegare brevemente le varie componenti
L 'acronimo CIA é l'inglese per Confidenzialitá, integritá e disponibilitá.

Con Confidenzialitá intendiamo che la confidenzialitá delle informazioni(ovvero che le informazioni private debbano essere accessibili solo a soggetti autorizzati) e la privacy degli utenti(ovvero la possibilitá che questi possano controllare chi ha accesso ai propri dati sensibili e decidere da chi possano essere diffusi) debbano essere rispettati.

Con integrtá intendiamo che l'integritá delle informazioni(ovvero che le informazioni possano essere modificate solo da soggetti autorizzati e in maniera controllata) e dei sistemi(ovvero che i sistemi informatici debbano svolgere i compiti per i quali sono stati programmati senza manipolazioni volontarie o accidentali ) debbano essere garantite.

Con disponibilitá intendiamo che i sistemi debbano essere prontamente funzioannti.

Questi sono gli obiettivi della sicurezza informatica
## Cifrari simmetrici
###### Fornire una definizione di cifrario simmetrico e elencare gli elementi che lo compongono
Un cifrario simmetrico é un cifrario nel quale sia il mittente che il destinatario condividono una stessa chiave(privata), che viene utilizzata per le operazioni di cifratura e decrittazione.

É composto da:
- una chiave simmetrica, condivisa damittente e destinatario
- un messaggio in chiaro, da cifrare
- una messaggio cifrato, ottenuto dopo la cifratura
- un'algoritmo di cifratura, per cifrare il messaggio
- un'algoritmo di decrittazione, per decifrare il cyphertext
###### Quali sono le caratteristiche di un cifrario sicuro? E uno incodizionatamente sicuro? É sempre possibile lo sia?
Un sistema crittografico  é consideratosicuro se rispetta tre requisiti:
- sia il mittente che il destinatario mantengono le chiavi in maniera sicura
- anche se in possesso dell'algoritmo, un'attaccante non deve essere in grado di poter decifrare un messaggio senza chiave(resistenza alla forza bruta)
- anche se in possesso di una grande quantitá di messaggi in chiaro e del loro corrispettivo cifrato, un'attaccante non deve esssere in grado di decifrare un messaggio senza chiave(resiste alla crittoanalisi statistica)

Un cifrario si dice quindi incondizionatamente sicuro se un messaggio cifrato, ottenuto tramite esso, non contiene abbastanza informazioni per determinare in maniera univoca un messaggio dal corrispettivo cifrato, indipendentemente dal tempo a disposizione dell'attaccante.

Poiché questo non é sempre possibile, un cifrario computazionalmente sicuro, e quindi utilizzabile deve rispettare almeno uno dei due criteri:
- il valore del messaggio che cifra é minore del costo necessario a violarlo
- il costo richiesto, in termini di tempo, per rompere il cifrario eccede il tempo per il quale l'informazione é utile.
###### Quali sono i possibili attacchi ad un sistema crittografico? Come vengono compiuti?
Un avversario puó attaccere un cifrario in due modi:
- provando ad indovinare la chiave, attraverso un'attacco di forza bruta
	- richiede solitamente di provare almeno la metá del dominio delle chiavi
- analizzando il messaggio cifrato e provando a dedurrre  sfruttando le regolaritá del linguaggio di partenza e quello che si conosce del messaggio in hciaro e dell'algoritmo di cifratura
###### Qual'é il primo cifrario simmetrico conosciuto? Descrivere brevemente il suo funzionamento, problematiche e soluzioni
Il piú antico cifrario conosciuto é sicuramente quello di cesare, che prevede la sostituzione di ogni lettera del messaggio in chiaro con la n-esima lettera successiva dell'alfabeto(ciclico).

Il dominio delle chiavi é uguale al numero di lettere dell'alfabeto $n$, quindi se questo é piccolo(come nel caso dell'alfabeto italiano) si possono effettuare degli attacchi di forza bruta molto semplicemente. Per risolvere questa falla si puó aumentare il dominio delle chiavi, per esempio, permutando l'alfabeto, incrementando cosí il dominio a $n!$.

Inoltre poiché si utilizza sempre la stessa regola di sostituzione e il linguaggio di partenza é regolare, e ció si rifflette sul messaggio cifrato, si é comunque vulnerabili ad attacchi di crittoanalisi statistica neanche troppo sofisticati, anche dopo l'espansione del dominio.
###### Descrivere brevemente il cifrario di Vigenére, il suo funzionamento e le sue falle.
Il cifrario di Vigenére é un cifrario a sostituzione polialfabetico, utilizza quindi piú regole di sostituzione, decise dalla chiave.

Avendo quindi una chiave $K=k_0,\dots,K_{n-1}$ e un messaggio in chiaro $P=p_0,\dots,p_{m-1}$ come una sequenza di lettere, su un alfabeto di $a$ lettere e considerando questi 3 elementi una lista di lettere, il messaggio viene cifrato secondo la seguente regola $c_i=(p_i+k_i\mod n)\mod a$.


## Cifrari Asimmetrici
###### Fornire una definizione di cifrario asimettrico
Un cifrario asimettrico é un cifrario nel quale si utilizzano una coppia di chiavi, diverse ma correlate, per le operazioni di cifratura e decrittazione.

Esso é composto da sei elementi:
- Un messaggio in chiaro
- un corrispettivo cifrato
- Una coppia di chiavi, una per la cifratura e l'altra per la decrittazione
- un algoritmo di cifratura e uno di decrittazione
###### Quali sono le caratteristiche di un cifrario asimmetrico sicuro?