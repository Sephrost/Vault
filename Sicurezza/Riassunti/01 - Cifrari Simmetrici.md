## Glossario dei termini
Un messaggio é definito **in chiaro**(*plaintext*) prima dell'operazione di cifratura(*encryption*), che lo renderá un **messaggio cifrato**(*ciphertext*). É possibile riconvertire un messaggio cifrato ad uno in chiaro attraverso la **decrittazione**(*decryption*). Un **cifrario**(*cypher*) é quindi uno schema(algoritmo) usato per la cifratura e la decrittazione.
## Cifrari Simmetrici
Un **cifrario simmetrico** é uno **schema** nel quale il **mittente** e il **destinatario** usano la **stessa chiave** per la cifratura e la decrittazione.

Uno schema a cifrario simmetrico é composto da **5 elementi**:
- Un **messaggio in chiaro**, da cifrare
- Un'**algoritmo di cifratura**, che cifra il messaggio in chiaro
- Una **chiave segreta**, usata per cifrare il messaggio
	- La chiave é indipendente dal messaggio
	- L'algoritmo produrrá un'output diverso in base alla chiave, poiché le modifiche dipendono da essa
- Un **messaggio cifrato**, prodotto dall'algoritmo
- Un'**algoritmo di decrittazione**, che esegue l'algoritmo di cifratura al contrario

![[Pasted image 20230221163628.png]]
### Caratteristiche di un cifrario simmetrico sicuro
- Un'algoritmo di cifratura sicuro
	- Idealmente questo deve rendere il messaggio impossibile da decrifrare o scoprire la chiave anche a chi ha accesso all'algoritmo, anche se in possesso di diversi testi in chiaro e il loro corrispettivo cifrato
- Che sia il mittente che il destinatario tengano una copia della chiave in maniera sicura

Quindi é necesssario tenere segreta solo la chiave, e non l'algoritmo. Ed é questo il motivo per il quale questi cifrari sono molto diffusi, poiché sono economici da utilizzare.
## Attacchi ai sistemi crittografici
Solitamente l'obiettivo di un'attacco ad un sistema crittografico é scoprire la chiave per decifrare un messaggio.
Esistono due approcci per attaccare un cifrario: 
- Provare a **dedurre** una **chiave** partendo **dall'algoritmo** **e** da quello che si sá dal **messaggio in chiaro**, anche detta **crittoanalisi**(*cryptanalysis*)
- **Provare ogni singola chiave** su un messaggio cifrato finché non si ottiene un messaggio leggibile, detto anche **attacco a forza bruta**(*brute-force attack*)

> Se uno dei due attacchi riesce a recuperare la chiave gli effetti possono essere catrastofici.

Il successo di una crittoanalisi dipende dalla quantitá di informazioni in possesso dell'attaccante e dalla possibilitá che la stuttura del messaggio in chiaro possa essere mantenuta dopo la cifratura.

Il successo di un attacco di forza bruta dipende solo dalla fortuna: in media bisogna provare **metá** delle **chiavi** possibili. Inoltre deve esistere un modo per riconoscere che un messaggio é stato decrittato correttamente.
## Cifrari incondizionatamente sicuri
Uno schema di cifratura si dice **incondizionatamete sicuro** se il **messaggio** cifrato dal cifrario **non** contiene **abbastanza informazioni** per determinare in maniera univoca il messaggio, indipendentemente dalla quantitá di messaggi cifrati a disposizione.

Quindi i messaggi cifrari sono sicuri, indipendentemente dal termpo a disposizione dell'attaccante.

> Ad eccezione dei crifrari one-time pad(OTP), esistono algoritmi di cifratura incondizionatamente sicuri.
## Cifrari computazionalmente sicuri
Poiché la maggioranza dei cifrari non sono incondizionatamente sicuri, un cifrario per considerarsi utilizzabile, e quindi computazionalmente sicuro, deve rispettare **almeno uno** di questi criteri:
- il valore del messaggio é minore del costo necessario per violare il cifrario
- il costo richiesto per romper il cifrario eccede il tempo per cui l'informazione é considerabile utile
