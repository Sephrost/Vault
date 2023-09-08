A causa della nota vulnerabilitá di DES ad attacchi di forza bruta, é stato necessario sostituirlo cercando schemi piú resistenti. Questo é avvenuto secondo due linee di pensiero:
- creare un nuovo algoritmo resistente sia alla crittoanalisi che agli attacchi di forza bruta(AES)
- mantenere DES e cifrare piú volte usando piú chiavi diverse
### Cifratura a due fasi
La forma piú semplice di cifratura a piú fasi ne ha esattamente due, e utilizza quindi due chiavi, una per ciascuna fase.

Dato il messaggio in chiaro $P$, le chiavi $K_i$ e il cifrario $E$, il messaggio cifrato $C$ si ottiene nella seguente maniera.
$$C=E(K_2,E(K_1,P))$$
![[Pasted image 20230512153012.png]]

L'utilizzo di una cifratura a piú fasi assicura inoltre una mappatura $P\to C$ che non é equivalente a DES a singola fase(quindi non esiste una coppia di valori $K_1$ e $K_2$ tale per cui $E(K_2,E(K_1,P))=E(K_3,P)$).

#### Attacco Meet-in-the-middle
Nonostante possa sembrare piú resistende di single phase-DES, in realtá non lo é: rimane infatti possibile una tipologia di attacco basato sulla forza bruta che funziona su ogni cifrario a blocchi.

Questo attacco, chiamato **meet-in-the-middle**, si basa su una semplice osservazione: se il messaggio viene cifrato in due fasi, allora il risultato della cifratura della prima fase $X$ é uguale alla decrittazione della seconda($X=E(K_1,P)=D(K_2,C)$).

Data una coppia di messaggio in chiaro e il corrispondente cifrato ($P,C$), l'attacco avviene nella seguente maniera:
1. si cifra $P$ con tutte le $2^{56}$ possibili chiavi $K_1$, salvando i risultati $X$ in una tabella ordinata
2. si decifra $C$ con tutte le $2^{56}$ possibili chiavi $K_2$, controllando se il risultato é presente nella tabella del primo passo
3. se é presente una corrispondenza, allora provo le chiavi su una nuova coppia $(P',C')$
4. se producono il messaggio cifrato nascosto, allora le chiavi sono corrette

Poiché per ogni possibile messaggio $P$ ci sono $2^{64}$ possibili messaggi cifrati, e $2^{112}$ chiavi possibili, visto che double DES usa effetivamente una chiave da $112$ bit, allora il numero massimo di chiavi $C$ che possono produrre un determinato messaggio cifrato é $2^{112}/2^{64}=2^{48}$, che é anche il numero di chiavi da provare prima di trovare quella corretta nel caso peggiore.
### DES a 3 fasi
Una soluzione ovvia agli attacchi meet-in-the-middle é l'utilizzo di 3 stage, al posto di 2. Ci si riferisce di solito a DES a tre fasi con il nome 3DES, o Triple Data Encryption Algorithm(*TDEA*).

É un'alternativa molto popolare a DES, infatti attualmente non sono conosciuti attacchi di crittoanalisi efficaci, visto il costo esponenzialmente crescente, e il costo di un'attacco di forza bruta é dell'ordine di $2^{112}$

Solitamente si usano due chiavi, avendo quindi $K_1=K_3$, ma é possibile anche aggiungere una terza chiave, garantendo comunque una conmpatibilitá con DES tradizionale.
### Modalità di cifratura dei cifrari a blocchi
Un cifrario a blocchi prende un blocco di testo di lunghezza fissa($b$ bits) e una chiave come input e produce messaggio cifrato sempre di $b$ bit.
Se é necessario aumentare la lunghezza del messaggio é possibile quindi dividerlo in piú blocchi di $b$ bit e cifrarli uno ad uno. MA questo provoca una serie di problemi di sicurezza.

Per applicare i cifrari a clocchi per piú applicazioni sono state definite quindi 5 **modalitá di cifratura**, ovvero delle **tecniche** per **migliorare** gli effetti dell'algoritmo crittografico o **adattarlo** a piú casi d'uso.
#### Electronic Codebook
La modalitá di cifratura piú semplice é l'**Electronic Codebook**(*ECB*), nella quale il **messaggio** in chiaro viene gestito **un blocco** alla **volta**, cifrandoli con la **stessa chiave**.

Se il messaggio é **piú lungo** dei $b$ bit che compongono un blocco, questo viene **diviso** in **piú blocchi** e viene **aggiunto** del **padding** all'ultimo se necessario. Le decrittazione avviene sempre un blocco alla volta, usando la stessa chiave.

Questa modalitá presenta peró alcuni problemi, soprattuto per messaggi piú lugnghi. 
Innanzitutto se uno stesso blocco di messaggio in chiaro si ripete in $P$, allora produce lo stesso risultato. lasciando trasparire informazioni sul messaggio originale. Inoltre se il messaggio é abbastanza strutturato, é possibile la crittoanalisi dello stesso sfruttando le regolaritá del messaggio.
#### Chiper Block Chaining
In questa modalitá, detta anche **CBC**, l'input della funzione di cifratura dell'algoritmo é lo **XOR logico** fra il blocco di **messaggio** in **chiaro** e il **messaggio** **cifrato** prodotto dal blocco precedente. Per il primo blocco si utilizza invece un **vettore di inizializzazione IV** per l'operazione di XOR.
Questo permette di ottenere blocchi cifrati diversi da uno stesso blocco di input.

![[Pasted image 20230512175413.png]]

Si utilizza la stessa chiave per ogni blocco.
IV deve essere inoltre conosciuta sia dal mittente che dal destinatario e impredicibile da chiunque altro, oltre che protetto da cambiamenti non autorizzati, che renderebbero il messaggio indecifrabile.

#### Chiper Feedback
Questa modalitá, detta anche **CFB**, permette di trasformare un cifrario a blocchi in uno a flusso, eliminando la necessitá di aggiungere il padding se necessario.

Per cifrare un messaggio in questa modalitá, l'input del funzione di cifratura é un registro a scorrimento di $b$-bit, inizializzato per un qualche vettore di inizializzazione IV. Si effettua quindi lo XOR logico tra gli $s$ bit piú significativi dell'output della funzione di cifratura e il primo segmento di messaggio in chiaro $P_1$ per produrre la prima porzione di messaggio cifrato $C_1$, che viene quindi trasmesso.Successivamente si scorre il registro di $s$ bit e si inserisce $C_1$ nei bit meno significativi.
Questo processo si ripete fino a quanod il messaggio non é stato interamente cifrato.

![[Pasted image 20230512183440.png]]

#### Output Feedback
La modalitá **Output Feedback**(*OBF*) é simile a quella CFB.
Permette di trasformare un cifrario a blocchi in uno a flusso, eliminando la necessitá di aggiungere il padding se necessario.

In questa modalitá l'output della funzione di cifratura diventa l'input del blocco successivo. OBF opera quindi su interi blocchi di messaggio cifrato piuttosto che su un sottoinsieme di $s$ bit.

![[Pasted image 20230512184749.png]]

Lavorando su blocchi interi un'errore non si proroga sui blocchi successivi. 