## Macchine a rotori

> Prima dell'introduzione di DES, erano piú importente implementazione dell'applicazione di piú strati di cifratura per incrementare la sicurezza

Una **macchina a rotori** consiste in un'insieme di cilindri ruotanti, uno per lettera dell'alfabeto.
Ciascun cilindro ha un pin di **input** e uno di **output**. Ciascun pin di input é collegato ad un solo pin di output, esclusivo ad esso.

![[Pasted image 20230315111025.png]]

Ogni cilindro rappresenta quindi una sostituzione monoalfabetica, poiché associamo ad ogni coppia di pin i/o una lettera dellálfabeto.

### Esempio di funzionamento
Prendiamo come esempio una macchian ad un cilindro.

Dopo aver ricevuto una chiave in input, il cilindro ruota di una posizione, quindi le connessioni vengono spostate di conseguenza.

Quindi viene usato una soltituzione monoalfabetica ogni volta, ma dopo 26 iterazioni il cilindro tornerá nella configurazione iniziale.

### Livello di sicurezza
La sicurezza di questo sistema é racchiusa nel fatto che é possibile usare pú cilindri in sequenza, collenando il pin di output di un cilindro al pin di input di un'altro.

Questo permette di mitigare in parte il riutilizzo dei cifrari di sostituzione, garantendo $l^c$ sostituzioni monoalfabetiche diverse prima che il sistema si ripeta, dove $l$ é il numero di lettere dellálfabeto e $c$ é il numero di cilindri.

Questo rende quasi impossibili gli attacchi di crittoanalisi, in quanto la quantitá di testo cifrato necessaria sarebbe eccessiva.

## Cifrario di Feistel
> Se il blocco ha dimension i troppo piccole é vulnerabile ad attachci di crittoanalisi statistica.

Il cifrario di Feistel mostra come é possibile **approssimare** la **dimensione ideale** del **blocco** usando il concetto di **cifrario prodotto**.

Il cifrario prodotto corrisponde all'esecuzione di due o piú cifrari in secuenza allo stesso messaggio in chiaro. In questo caso particolare vengono concatenati cifrari a sostituzione permutazione

### Diffusione e confusione
Durante gli attacchi di crittoanalisi statistica viene utilizzata una qualche conoscenza del messaggio in chiaro per dedurne la chiave. Questo é possibile perché una qualche informazione sul messaggio viene manteuta dopo la cifratura, come la distribuzione di frequenza dei caratteri.

Poiché il cifrario a sostituzione arbitraria non é molto pratico, soprattuto dal punto di vista delle performance, una soluzione accettabile é rendere piú difficile la crittoanalisi.

Esistono due metodi per far ció.
- **Diffusione**
	- La struttura statistica del messaggio in chiaro viene dissipata lungo tutto l'alfabeto del cifrario
	- La frequenza delle lettera sará quindi piú unifrome, come della deli digrafi.
- **Confusione**
	- Si cerca di rendere la relazione tra le statistiche del messaggio cifrato e il valore della chiavedi crifratura il piú difficile possibile da scoprire.
	- Si puó ottenere ció usando algoritmi di sostituzione complessi.

### Struttura del cifrario
L'input dell'algoritm é un blocco di di testo in chiaro di $2w$ bits e una chiave  $k$.

Il blocco é diviso in due metá, $LE_0$ e $RE_0$, su ognuna delle quali vengono eseguiti $n$ processamenti per poi combinare i risultati delle due sequenze.
Ogni processazione ha come input l'output dell'iterazione precedente, oltre ad una sottochiave $k_i$, derivata da $k$. Ognuna di queste sottochiave é diversa sia da $k$ che da ogni altra.

Durante ogni processazione viene eseguita una sostituzione sulla parte sinistra dei dati, applicando la funzione **di arrotondamento** $F$ alla metá destra dei dati ed eseguendo uno **xor** tra l'output di $F$ e la metá sinistra.

Dopo di che viene eseguita una permutate le due metá, scambiandole. Durante l'ultima iterazione, questa operazione viene disfatta, ripetendola.

![[Pasted image 20230315130058.png]]

### Configurazione del cifrario
L'esatta implementazione del cifrario dipende quidni dai seguenti parametri:
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

