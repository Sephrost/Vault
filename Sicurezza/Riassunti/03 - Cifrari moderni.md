## Macchine a rotori

> Prima dell'introduzione di DES, erano piú importente implementazione dell'applicazione di piú strati di cifratura per incrementare la sicurezza

Una **macchina a rotori** consiste in un'insieme di cilindri ruotanti, uno per lettera dell'alfabeto.
Ciascun cilindro ha un pin di **input** e uno di **output**. Ciascun pin di input é collegato ad un solo pin di output, esclusivo ad esso.

![[Pasted image 20230315111025.png]]

Ogni cilindro rappresenta quindi una sostituzione monoalfabetica, poiché associamo ad ogni coppia di pin i/o una lettera dell'alfabeto.

### Esempio di funzionamento
Prendiamo come esempio una macchina ad un cilindro.

Dopo aver ricevuto una chiave in input, il cilindro ruota di una posizione, quindi le connessioni vengono spostate di conseguenza.

Quindi viene usato una soltituzione monoalfabetica ogni volta, ma dopo 26 iterazioni il cilindro tornerá nella configurazione iniziale.

### Livello di sicurezza
La sicurezza di questo sistema é racchiusa nel fatto che é possibile usare pú cilindri in sequenza, collegando il pin di output di un cilindro al pin di input di un'altro.

Questo permette di mitigare in parte il riutilizzo dei cifrari di sostituzione, garantendo $l^c$ sostituzioni monoalfabetiche diverse prima che il sistema si ripeta, dove $l$ é il numero di lettere dellálfabeto e $c$ é il numero di cilindri.

Questo rende quasi impossibili gli attacchi di crittoanalisi statistica, in quanto la quantitá di testo cifrato necessaria sarebbe eccessiva.

## Cifrari a flusso
Un **cifrario a flusso** é un cifrario che cifra un flusso di dati digitali **un bit** alla volta.

> Esempi di cifrari a flusso sono i cifrari di Vigenére e Vernam.

![[Pasted image 20230318154323.png]]

## Cifrari a blocchi
> Molti cifrari moderni si basano sul cifrario a blocchi di Feistel.

Un **cifrario a blocchi** é un cifrario in cui dei **blocchi** di messaggio in **chiaro** vengono usati per **produrre** **blocchi** di messaggio cifrato di **uguale lunghezza**.

> Solitamente vengono utlizzati blocchi di 64 o 128 bits.

![[Pasted image 20230318154408.png]]

Quindi per ogni dimensione $n$ del blocco sono possibili $2^n$ blocchi di testo in chiaro, ammettendo che la cifraturatura produca un output univoco e che sia quindi revertibile.Sono inoltre possibili $2^n!$ traformazioni revertibili.

Inoltre se viene usata una dimensione dei blocchi troppo piccola, il cifrario é equivalente ad un cifrario a sostituzione classico, e vulnerabile quindi alla crittoanalisi statistica.

Se invece il blocco é sufficentemente grande ed é possibile revertire una sostituzione arbitraria, allora le caratteristiche del testo in chiaro vengono mascherate e le tecniche di crittoanalisi statistica diventano infattibili.

## Cifrario di Feistel

Il cifrario di Feistel mostra come é possibile **approssimare** la **dimensione ideale** del **blocco** usando il concetto di **cifrario prodotto**.

Il cifrario prodotto corrisponde all'**esecuzione** di due o **piú cifrari in sequenza** allo stesso messaggio in chiaro. In questo caso particolare vengono concatenati cifrari a sostituzione permutazione

### Diffusione e confusione
Durante gli attacchi di crittoanalisi statistica viene utilizzata una qualche conoscenza del messaggio in chiaro per dedurne la chiave. Questo é possibile perché una qualche informazione sul messaggio viene manteuta dopo la cifratura, come la distribuzione di frequenza dei caratteri.

Poiché il cifrario a sostituzione arbitraria non é molto pratico, soprattuto dal punto di vista delle performance, una soluzione accettabile é rendere piú difficile la crittoanalisi.

Esistono due metodi per far ció.
- **Diffusione**
	- La struttura statistica del messaggio in chiaro viene dissipata lungo tutto l'alfabeto del cifrario
	- La frequenza delle lettera sará quindi piú unifrome, come della deli digrafi.
- **Confusione**
	- Si cerca di rendere la relazione tra le statistiche del messaggio cifrato e il valore della chiave di crifratura il piú difficile possibile da scoprire.
	- Si puó ottenere ció usando algoritmi di sostituzione complessi.

### Struttura del cifrario
L'input dell'algoritmo é un blocco di di testo in chiaro di $2w$ bits e una chiave  $k$.

Il blocco é diviso in due metá, $LE_0$ e $RE_0$, su ognuna delle quali vengono eseguiti $n$ processamenti per poi combinare i risultati delle due sequenze.
Ogni processazione ha come input l'output dell'iterazione precedente, oltre ad una sottochiave $k_i$, derivata da $k$. Ognuna di queste sottochiave é diversa sia da $k$ che da ogni altra.

Durante ogni processazione viene eseguita una sostituzione sulla parte sinistra dei dati, applicando la funzione **di arrotondamento** $F$ alla metá destra dei dati ed eseguendo uno **xor** tra l'output di $F$ e la metá sinistra.

Dopo di che viene eseguita una permutate le due metá, scambiandole. Durante l'ultima iterazione, questa operazione viene disfatta, ripetendola.

![[Pasted image 20230315130058.png|600]]

### Configurazione del cifrario
L'esatta implementazione del cifrario dipende quindi dai seguenti parametri:
- **Dimensione del blocco**
	- Un blocco grande incrementa la sicurezza a scapito della velocitá
	- Un blocco di 64 bit é considerato un buon compromesso
- **Dimensione della chiave**
	- Una chiave grande icrementa la sicurezza a scapito della velocitá
	- La dimensione piú comune é 128 bit, dimensioni piú piccole possono essere inadeguate
- **Numero di iterazioni**
	- Il tipico numero di iterazioni é 16
- **Algoritmo di generazione delle sottochiavi**
	- Un'algoritmo complesso rende difficile la crittoanalisi
- **Funzione di approssimazione $F$**
	- Un'algoritmo complesso rende piú difficile la crittoanalisi

#### Funzioni cifratura di Feisel
Consideriamo $LE_i$ la porzione sinistra $i$-esima iterazione della cifratura $E$, e $LE_i$ la porzione destra alla medesima iterazione,per ogni iterazione eccetto l'ultima abbiamo:
$$
\begin{cases}
LE_i=RE_{i-1}\\
RE_i=LE_{i-1}\oplus F(RE_{i-1},K_i)
\end{cases}
$$
mentre per l'ultima:
$$
\begin{cases}
LE_i=RE_{i-1}\\
RE_i=LE_{i-1}
\end{cases}
$$
#### Funzione di decrittazione di Feisel
Consideriamo $LD_i$ la porzione sinistra $i$-esima iterazione della funzione di decrittazione $D$, e $RD_i$ la porzione destra alla medesima iterazione.Per ogni iterazione eccetto l'ultima abbiamo:
$$
\begin{cases}
LD_i=RD_{i-1}\\
RD_i=LD_{i-1}\oplus F(RD_{i-1},K_i)
\end{cases}
$$
dove $LD_i=RE_{n-i}$ e $RD=LE_(n-i)$, dove $n$ é il numero di iterazioni di cifratura.
Per l'ultima iterazione si ha
$$
\begin{cases}
LD_i=RD_{i-1}\\
RD_i=LD_{i-1}
\end{cases}
$$
## Data Encryption Standard(DES)
> Prima dell'introduzione di AES era il cifrario piú usato.

Il cifrario prevede il classico input chiava/messaggio, ma in questo caso specifico il **messaggio** deve essere di **64 bit** e la **chiave** di **56**.

Il messaggio viene cifrato in **3 fasi**:
1. Il **messaggio** in chiaro viene **permutato**, e i bit in eccesso della chiave vengono scartati.
	1. Viene scartato il bit meno significativo di ogni byte della chiave
2. Vengono effettuate **16 round** di cifratura, in maniera analoga al cifrario di Feistel
	1. Ad ogni iterazione, la chiave viene divisa in **due parti** di **28 bit** ciasuna, sulle quali viene eseguito uno **shift** circolare a **sinistra**. Vengono poi **selezionati 48 bit** per essere usati come **chiave** di ciascun **round**, in modo da utilizzare una chiave diversa per ciascuno.
	2. Il messaggio viene diviso in due metá di **32 bit** ciascuna. La metá destra $R$ viene quindi espansa attraverso una **permutation box(p-box) ad espansione**, in modo da ottenere una metá da 48 bit che combacia con la lunghezza della chiave.
	3. Viene effettuato lo **xor logico** tra $R$ e la chiave
	4. Il risultato viene quindi fatto elaborare da una serie di **substitution box**(*s-box*). Questo permette di struttare il principio di confusione.
	5. Il risultato delle s-box viene permutato, ottenendo $R'$
	6. In maniera anagola a Feistel $L_i=R_{i-1}$ e $R_i=L_{i-1}\oplus R'$

![[Pasted image 20230318164941.png]]

Il cifrario DES sfrutta inoltre l'**effetto valanga**, infatti un cambiamento anche solo di un bit del messaggio o della chuave produce una variazione di diversi bit sul messaggio cifrato corrispondente.