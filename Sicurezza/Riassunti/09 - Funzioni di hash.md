Una funzione di Hash accetta in input un blocco di lunghezza variabile $M$ in input e restituisce un blocco di lunghezza fissa $h=H(B)$.

![[Pasted image 20230825174036.png]]

> Una buona funzione di hash ha proprietá che, applicando ad essa un gran numero di input, gli output risultano distribuiti e apparentemente casuali.

Il sottoinsieme di funzioni di hash utilizzabili in sicurezza sono le **funzioni di hash crittografiche**, ovvero le funzioni per le qualié computazionalmente impossibile trovare 
1. l'input di partenza dato l'output(**non invertibilitá**)
	1. Dato $C$ é computuazionalmente difficile calcolare $H^{-1}(C)$
2. un messaggio $m_2$ tale per cui $H(m_1)=H_{m2}$(**non invertibilitá forte**)
3. due input che producono lo stesso output(**resistente alle collisioni**)
Queste proprietá permettono di capire se un dato é cambiato.

> Un funzione di hash resistente alle collisisoni soddisfa per forza anche gli altri due prerequisiti.

### Attacco del compleanno ad una funzione di hash
Proviamo ad immaginare come un avversario potrebbe attaccare una funzione di hash resistente ale collisioni. Vuole quindi trovare $x$ e $y$ che producono la stessa funzione di hash: $H(x)=H(y)$.

#### Paradosso del compleanno
Immaginiamo di avere in un stanza un gruppo di 23 persone. La probabilitá che due di questi abbiano lo stesso compleanno é maggiore di $1/2$. 

Possiamo osservare che la probabilitá che nessuno abbia un compleanno in comune é $P(n,c)=1-P(compleanni\; diversi)=1-\frac{365\times 364\times \dots\times (365-22)}{365^{23}}=0.4927$.

Possiamo quindi definire la formula generale che definisce la probabilitá che ci sia almeno una ripetizione in un insieme di $k$ elementi scelti tra $n$: $P(n,k)=1-(n\times (n-1)\times \dots(n-k+1))/\times n^k =1-e^{-k\times (k-1)/2n}\approx 1- e^{-k^2/2n}$

La probabilità che due persone compiano gli anni lo stesso giorno è maggiore di 1/2 quando le persone sono almeno 23, che é tantissimo.
#### Conseguenze per le funzioni di hash
Osserviamo ora il comportamento di un avversario:
Supponiamo che $|H(M)| =c$ e $H(M)=h$, é quindi possibile ottenere $2^c=n$ codici hash diversi da $H$.
L'avversario creerá invece codici hash di dimensione $|H'(M')| =m$, potendo creare quindi $2^m=k$ codici differenti da $H'$.

Vogliamo ora calcolare il limite per la quale ala probabilitá di una collisione é maggiore di un mezzo. 

Sappiamo che questo vale se $k>1,18\times \sqrt n\to 2^m>1,18\sqrt{2^c}\to 2^m>2^{\frac{c}{2}}\to m>\frac{c}{2}$.

Quindi per generare una collisione per codici di 64 bit, basta provare $2^{64/2}=2^{32}$ messaggi.

Questo ci serve a trovare una correlazione tra il messaggio $M$ e quello $M'$, ma non ci fornisce informazioni su $M$.

#### Paradosso del compleanno: altra applicazione
Riprendiamo l'esempio di prima, ma questa volta supponiamo di prendere due insiemi separati $X$ e $Y$, ognuno di $k$ elementi con $n$ possibili valori. In ciascun insieme i valori sono diversi.
Abbiamo quindi:
- $X=\{x_1,\dots,x_k\}$
- $Y=\{Y_1,\dots,Y_k\}$

Vogliamo ora calcolare la probabilitá che ci sia almeno un elemento in comune tra i due insiemi.
Sappiamo che:
- la probabilitá che il primo elemento di X sia uguale ad un'altro di Y é $P(x_1=y_1)=\frac{1}{n}$
-  la probabilitá che un elemento di X sia diverso ad un'altro di Y é $P(x_i\ne y_i)=1-\frac{1}{n}$
- La probabilità che il primo elemento di x non sia il primo elemento o il secondo in y è $P(x_1\ne y_1\lor x_1\ne y_2)=(1-\frac{1}{n})^2$ 
- La probanilitá che ogni elemento di $X$ non sia in $Y$ é $P(x_1\not \in Y)=1-P(x_1\in Y)=(1-\frac{1}{n})^k$
- La probabilitá che $X$ e $Y$ siano disgiunti é $P(X\cap Y=\emptyset)=[(1-\frac{1}{n})^k]^k$ 

Per calcolare la probabilitá che ci sia almeno un elemento in comune é quindi $P(X\cap Y\ne \emptyset)=1-(1-\frac{1}{n})^{k^2}>1-e^{-\frac{1}{n}k^2}$ ottenendo $k>0,83\times \sqrt n$.

Questo risultato ci serve a studiare l'attacco del compleanno.

#### L'attacco del compleanno(infine)
Osserviamo ora l'attacco del compleanno:
1. Alice é pronta a firmare il suo messaggio $x$ appendendo l'hashcode di $m$ bit cifrato con la propria chiave privata
2. L'avversario genera $2^{m/2}$ varianti $x'$ di $x$, aggiungendo padding o parti vuote al messaggio ma che mantiene identico il significato, salvando i messaggi e i corrispettivi valori di hash
3. Prepara inoltre un messaggio fraudolento $y$ che vorrebbe firmare con la chiave di Alice, allora fa la stessa cosa del passo precedente anche per $y$. Controlla quindi se c'é qualche corrispondenza tra i valori di $x'$ e $y'$
4. L'avversario ha quindi trovato un messaggio con singificato diverso ma con hashcode uguale a $x$, e chiede quindi ad Alice di inoltrarlo al posto del messaggio originale
5. Alice lo inoltra a Bob poiché i messaggi sono identici dal punto di vista del valore di hash
6. L'avversario é riuscito quindi ad inviare il proprio messaggio a Bob, il quale non sospetta nulla, senza conoscere la chiave di cifratura

Tutto questo funziona poiché l'avversario é certo di trovare una collisione tra $x'$ e $y'$ con probabilitá maggiore di $1/2$.

### Codici CRC
Un **controllo di ridondanza ciclica**, o crc, é un metodo di checksum che prevede l'aggiunta di un bit aggiuntivo ad una sequenza di bit di lunghezza arbitraria che serve a rendere il numero di bit impostati ad 1 pari. Questo viene calcolato effettuando lo XOR logico tra tutti i bit della sequenza.

> Per esempio la sequenza $01001$ avrá bit di paritá impostato a $0$, mentre la sequenza $01000$ avrá bit di paritá impostato ad $1$.

Questo meccanismo permette di rilevare un numero di errori dispari, ma se questo é pari non é in grado di rilevarlo.
Per ovviare al problema possiamo suddividere la sequenza in $n$ sequenze di pari lunghezza e calcolare il bit di paritá per ciascuna di esse, ottenendo quindi un **vettore di paritá**.

#### Requisiti funzioni di hash sicure
Una funzione di hash sicura deve quindi:
- produrre digest sufficentemeente lunghi
- non permettere metodi semplici per generare collisioni

### Funzioni di hash attualmente usabili
Le funzioni di hash usate attualmente funzionano in maniera simile ai cifrari in modalitá cyper block chaining, ma codificando invece che cifrando, infatti non é presente alcuna chiave.

Il messaggio viene diviso in $b$ blocchi di lunghezza fissa $k$. Poiché la lunghezza del messaggio puó essere variabile, se necessario, viene aggiunto del padding all'ultimo blocco.

La funzione di hash $F$ viene poi applicata a ciascun blocco, combinandolo al risultato del blocco procedente, ottenendo un output di lunghezza $j$. Se questo é il primo blocco viene utilizzato il vettore di inizializzazione IV. 

Il digest é il risultato dell'ultimo blocco.

A seconda della funzione di hash che stiamo utilizzando avremo valori diversi $j$ e $k$ cioè dimensioni diverse dei blocchi e dei codici: 
- MD5: k = 512, j = 128 (abbastanza per il paradigma del compleanno, anche se non il massimo) 
- SHA-1: k = 512, j = 160 (sicuro per il paradigma del compleanno) 
- SHA-256: k = 512, j = 256 (usato in ambito militare) Creare un padding Spesso parliamo di suddividere messaggi i

