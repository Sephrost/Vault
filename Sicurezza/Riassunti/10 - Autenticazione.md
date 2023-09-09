L'**autenticazione di messaggi** é la **procedura** utilizzata per **verificare** che un **messaggio** ricevuto proviene dalla **fonte corretta** e **non** é stato **alterato**.

Questo é necessario perché, nonostante il sistema di cifratura sia sicuro, il canale su cui viene trasmessa una chiave puó non esserlo, come nel caso del man in the middle.

L'autenticazione puó avvenire in **diverse maniere** a seconda del **sistema** di **ciratura utilizzato**:
- **Autenticazione simmetrica**: basata su cifrari simmetrici
- **Firma digitale**: basata su cifrari asimmetrici 
### Funzione di autenticazione simmetrica
Ogni autenticazione di messaggi o firma digitale ha due livelli di funzionalitá:
- a basso livello, ha una funzione che produce un **autenticatore** usato per autenticare il messaggio
- ad alto livello, la stessa funzione viene utilizzata come **primitiva** per il **protocollo di autenticazione** che permette di verificarne l'auteticitá

Le funzioni utulizzate per produrre un autenticatore possono essere suddivise in 3 classi:
- **funzioni di hash**
- **cifratura di messaggi**
- **codici di autenticazione di messaggi(MAC)**: un codice di lunghezza fissa generato dal messaggio e da una chiave segreta
#### Autenticazione con chiave simmetrica
Supponiamo di utilizzare come autenticazione la cifratura stessa(con *chiave simmetrica*) dove un messaggio **M** viene inviato da **A** a **B**.

Se nessun altro conoscesse la chiave, allora avremmo la **confidenzialità**, infatti nessun altro potrebbe recuperare il testo in chiaro a partire dal testo cifrato.
Inoltre B è sicuro che il messaggio sia stato generato da A, in quanto solo A può averlo generato, possedendo la chiave.

B é quindi sicuro che il messaggio non é stato alterato, in quanto per alterarlo l'avversario dovrebbe conoscere la chiave, garantendo anche l'**autenticazione**. Tuttavia questo non é sempre vero.

Consideriamo di nuovo lo scenario dove **A** invia un messaggio **M** a **B**. 
B sà che se riceve un messaggio da A, è autentico in quanto solo A possiede la chiave. Ma se qualcun altro inviasse a B una **sequenza casuale**, B non avrebbe modo di determinare automaticamente se il testo cifrato in arrivo sia autentico o meno

La soluzione è quella di mettere in coda un codice, il **MAC** - Message Authentication Code, in modo da autenticare il mittente.
### MAC
É una **tecnica alternativa di autenticazione** che utilizza una **chiave sergreta**, oltre al messaggio, per generare una **checksum crittografica** di lunghezza fissa, che viene aggiunto alla fine del messaggio.

Questa tecnica assume che $A$ e $B$ condividano una chiave segreta comune. Quando il messaggio deve essere inviato viene calcolato $MAC=C(K,M)$, dove:
- $M$ é il messaggio
- $C$ é la funzione di MAC
- $K$ é la chiave segreta consivisa

Vengono quindi trasmessi il messaggio piú il MAC. Il destinatario applicherá la stessa funzione al messaggio e confronterá il MAC ottenuto con quello ricevuto. 
Assumendo che la chiave sia conoscuta solo da mittente e destinatario, e i MAC ottenuti sono uguali, allora
- Il **messaggio** **non** é stato **alterato**, poiché un'attaccante dovrebbe alterare anche il MAC, ma questo non é possibile poiché non conosce la chiave
- Il messaggio é stato mandato dal mittente, poiché nessun'altro conosce la chiave
	- Questo rende il MAC **resistente all'attacco del compleanno**, in quanto non é possibile trovare una collisione senza la chiave

Il MAC funziona quindi in maniera simile alla cifratura, con la differenza che la prima deve essere **non invertibile**.
##### MAC DES-CBC
Consiste nell’usare un cifrario DES a chiave simmetrica nella modalità CBC.

Il messaggio originale viene fatto diventare di lunghezza multipla di 64 tramite un padding e poi si procede all’esecuzione normale di CBC

Il MAC prodotto equivale all’ultimo blocco(o parte dell’ultimo blocco, dai 16 a 64 bit) prodotto dal cifrario. Il vettore di inizializzazione(IV) di solito è posto a 0.

![[Pasted image 20230831180609.png]]
### HMAC - MAC con funzione di hash
Negli ultimi anni, la creazione di un MAC derivato da una funzione di hash crittografica ha destato sempre piú interesse per due motivazioni:
1. le funzioni di hash crittografiche come MD5 vengono **eseguite piú velocemente** in software di un cifrario a blocchi simmetrico come DES
2. Le **librerie** contenenti funzioni di hash crittografiche sono **ampiamente diffuse**
#### Struttura di HMAC
Dato una messaggio $M$ e un chiave $K$, di ottiene l'HMAC nella seguente maniera:
1. Se la chiave é meno lungha di $b$(il numero di bit in un blocco),si aggiunge un padding alla chiave $K$ finchè non diventa lunga $b$ bit, dove $b$ è la dimensione dei blocchi,generando così $K^+$
	1. Se invece é piú lungha si effettua l'hash della chiave per ridurlo a $b$ bit
	2. Altrimenti la si usa cosí com'é
2. Si effettua lo XOR tra $K^+$ e una costante($0x36$ ,chiamata ipad) moltiplicata per $b/8$,producendo un blocco $S_i$ di $b$ bit
3. Si aggiunge $S_i$ in testa a $M$ e lo si effettua l'hash
4. Si effettua lo XOR tra $K^+$ e una costante($0x5C$,chiamta opad),producendo un blocco $S_o$
5. Si aggiunge $S_i$ in testa a $S_o$ e se ne esegue nuovamente l'hash
6. Il risultato, di $n$ bit é il nostro HMAC

In formule $HMAC(K,M)=H[(K^+\oplus opad)||H[K^+\oplus ipad||M]]$.
 
![[Pasted image 20230901164421.png]]
#### Sicurezza di HMAC
La sicurezza di HMAC dipende da quella della funzione di hash che implementa.
Per opportune scelte di H, HMAC è ritenuto sicuro contro attacchi con scelta dei messaggi autenticati "chosen message attacks": anche se l’avversario può scegliere molti messaggi e vederne il corrispondente valore di HMAC, non riesce a fornire un nuovo messaggio autenticato.
## Firma elettronica
La **firma elettronica** é un modo per garantire l'autenticitá del messaggio.

L'idea é molto semplice: il mittente cifra l'hashcode $h$ del messaggio $M$ che vuole inviare con la propria chiave privata, appendendo quindi la firma digitale cosí ottenuta al fondo del messaggio. 
Il destinatario invece calcolerá sempre l'hash del messaggio e proverá a decrittare la firma con la chiave pubblica del mittente, se questi coincidono allora l'autenticitá del messaggio é garantita, poiché solo il mittente possiede la propria chiave privata. Inoltre il messaggio é **non disconoscibile** per il mittente.

![[Pasted image 20230901190441.png]]

> Poiché la chiave pubblica del mittente é, appunto, pubblicamente conosciuta, la firma elettronica si dice **opponibile a terzi**: chiunque può svolgere l’operazione di verifica ( e questo rispecchia anche la realtà nel mondo reale)

La firma elettronica puó essere calcolata attraverso due tecniche:
- RSA con MD5/SHA-1
- DSA con SHA-1 (non l'abbiamo studiato)
### RSA con MD5/SHA-1
Il funzionamento é analogo a quello sopra descritto, viene calcolato l'hash del messaggio tramite SHA-1, che cifrato con la chiave privata del mittente tramite RSA genera al firma elettronica, che verrá inviata insieme al messaggio stesso.
![[Pasted image 20230902160353.png]]

Il destinatario calcolerá l'hash del messaggio sempre tramite SHA-1 e decifrerá la firma con la chiave pubblica del mittente. 
Se i due valori coincidono la firma é autentica.
![[Pasted image 20230902162554.png]]

Notiamo inoltre che per verificare la firma, B deve conoscere la chiave pubblica di A in modo certo, altrimenti è possibile fare accettare firme false, come nel caso del man in the middle.

Per cui è buona norma accertarsi che la chiave pubblica in suo possesso sia veritiera.
### Problema della distribuzione di chiavi
Il ricevente dovrà, in qualche modo, rendere nota la propria chiave pubblica, associando ad essa la propria identità. Occorre quindi una distribuzione sicura(autenticata) della corrispondenza utente-chiave pubblica.

Nella pratica si utilizzano dei **distributori** (fidati) di chiavi dei quali ottenere certificati:
1. Gli host depositano le proprie chiavi pubbliche al proprio distributore di fiducia, e ottengono da esso la chiave pubblica, appunto, del distributore.
	1. Questa viene aggiunta al messaggio 
![[Pasted image 20230902164524.png]]
2. Gli host richiedono il proprio certificato dal distributore

Ma un certificato non ha una durata eterna, infatti é possibile aggiungere al certificato un timestamp che che comprende anche un hash di tutti i dati col certificato annesso.

![[Pasted image 20230902164949.png]]