# Macchine di Turing
Una **macchina di Turing** é simile ad un automa a stati finiti, ma con memoria illimitata, rappresentata da un nastro infinito.

Inizialmente il nastro contiene soltanto la stringa di input, mentre tutto il resto é vuota. Se la macchina ne ha necessitá quindi puó scriverci sopra.

É inoltre in grado di leggere e scrivere sul nastro, attraverso i movimenti di una testina che puó muoversi a destra e sinistra, al fine di produrre un'output *accettato* o *rifiutato*. 

> Se non finisce in nessuno dei suoi stati continuerá ad elaborare per sempre.

###### Esempio
$$(q_1,a)\to(q_2,b,right)=S(q_1,a)$$

Qualsiasi cosa che puo' essere rappresentato con un calcolo puo' essere definito in questa maniera.
## Definizione
Una macchina di turing é una settupla $(Q,\Sigma,\Gamma,\delta,q_0,q_{accept},q_{reject})$
dove:
- $Q$ é un'insieme di stati
- Un' alfabeto di input $\Sigma$, che non contiene il carattere di padding (*blank*)
- Un'alfabeto del nastro $\Gamma$ contenente il carattere di padding e dove $\Sigma\subseteq\Gamma$
- Una funzione di transizione $Q\times\Gamma\to Q\times\Gamma\times\{L,R\}$
- Uno stato $q_0\in Q$ che rappresenta lo stato iniziale 
- Uno stato di accettazione $q_{accept}\in Q$
- Uno stato di rifiuto $q_{reject}\in Q$, con $q_{reject}\ne q_{accept}$

Una macchina di Turing riceve in input una stringa $w=w_1w_2\dots w_n\in\Gamma^*$ nei primi $n$ spazi del nastro(il resto é costituito da caratteri vuoti). Il primo carattere di padding rappresenta quindi la fine della stringa $w$.

#### Convenzione per la lettura di una configurazione
Una **configurazione** é una combinazione di *stato corrente*, *contenuto del nastro corrente* e *posizione della testina attuale*.

Diciamo che una configurazione $C_1$ **produce** una configurazione $C_2$ se la $M.T$ puó  legalmente passare dallo stato della configurazione $C_1$ a quello di $C_2$ in un singolo passo.

Come convenzione per la lettura di una configurazione usiamo la seguente dicitura, scrivendo il nastro e inserendo lo stato del controllo prima del prossimo carattere da leggere, nella srguente maniera:
$$0100q_71100$$
quindi la macchina prima di riconoscere il carattere 1 si trovera' nello stato $q_7$.

![[Pasted image 20220921114716.png]]

Una macchina di Turing deve poter accettare tutte le stringhe comprese nel linguaggio $L$, composto da tutte le strighe che la macchina deve riconoscere, e rifiutare tutte le altre.

### Linguaggio riconosciuto da una macchina di Turing
$$L(M)=\{w\in \Sigma^*|M\; accetta\; w\}$$
$$(M\;accetta\;w)\iff(w\in L)$$
Se $w\notin L$ e $M$ riconosce $L$ allora $M$ rifiuta $w$ oppure $M$ non termina su $w$.

## Linguaggi Decidibili Positivamente
> Un linguaggio é detto **Decidibile Positivamente** (*Turing-Recognizable*) se una qualche macchina di Turing lo riconosce

## Linguaggi Decidibili
Poiché alcuni riconoscitori possono non terminare mai, rendendo difficile distinguere una macchina che sta elaborando da una in loop, introduciamo la nozione di *decisori*.

> Un linguaggio é detto **Decidibile** (Turing-Decidable) se esiste una macchina di Turing che termina su ogni input $\in L(M)$ 

Ogni Linguaggio Decidibile é anche riconoscibile, ma non il contrario.

> Diciamo inoltre che un linguaggio é **Decidibile** se é sia positivamente che negativamente decidibile per il **teorema di Post**

### Legenda per i Linguaggi
Per ogni $w^*\in L$
|Italiano|Inglese|Accettazione($w\in L$)|Rifiuto($w\notin L$)|
|:--:|:--:|:--:|:--:|
|Decidibile|Turing Recognizable|$M$ accetta $w$|$M$ rifiuta $w$|
|Decidibile Positivamente|Turing Decidable|$M$ accetta $w$|$M$ rifiuta $w\;\lor\;M$ non termina su $w$ |
|Decidibile negativamente|Co-Turing Recognizable|$M$ accetta $w\;\lor\;M$ non termina su $w$ |$M$ rifiuta $w$|

[[01 - Varianti delle Macchine di Turing]]## Macchina di Turing multi-registro
Una **macchina di Turing multi-registro** é una macchina di Turing con diversi nastri, ognuno dei quali ha una propria testina, e puo' essere letto e scritto.

### Funzione di Transizione
La funzione di transizione diventa la seguente
$$δ: Q\times Γ^k\to Q\times Γ^k\times\{L,R,S\}^k$$
dove $k$ é il numero di nastri.

### Equivalenza con le Macchine di Turing a nastro singolo
É possibile dimostrare che una macchina a piú registri ne ha una a singolo equivalente.

> Due macchine sono equivalenti se riconoscono lo stesso linguaggio

Per convertire una TM $M$ multinastro ad una a nastro singolo $S$ é sufficiente partizionare il nastro in $k$(il numero di nastri di $M$) partizioni separate dal delimitatore **#**,  

![[Pasted image 20220921101942.png]]

Immaginando che il dato di partenza sia una sringa $w=w_1\dots w_s$ partizioniamo il nastro usando i simbolo # come separatore.

Avremo quindi una posizione iniziale del tipo

![[Pasted image 20220921102125.png]]

> Gli asterischi indicano il valore attuale del segmento di nastro(memoria)

> Le macchine a singolo nastro sono molte piú lente poiche per accedere alle diverse aree di memoria dovremo spostare l'intero nastro, questo pero' non intocca la decidibilitá della macchina.

## Macchine di Turing non deterministiche

Una **Macchina di Turing non deterministica** é una TM che, in ogni momento della computazione, puó decidere tra diverse possibilitá.

### Funzione di Transizione
La funzione di transizione diventa la seguente
$$\delta:Q\times\Gamma\to P(Q\times\Gamma\times\{L,R\})$$
dove $P$ rappresenta l'insieme di stati producibili da una data configurazione.

### Computazione di una ndTM
La computazione di una macchina di Turing non deterministica é un'**albero**, con i rami che rappresentano le diverse possibilitá prodotte dalla macchina.

Se un ramo porta allo stato di accettazione, la macchina accetta l'input.

### Equivalenza con le Macchine di Turing deterministiche
É possibile simulare ogni TM non deterministica $N$ con una TM  deterministica $D$, facendo provare a $D$ tutti i **possibili cammini** generati da $N$, e supponendo che ogni nodo sia una configurazione, dove la radice é il nodo di partenza. 

Andiamo quindo a cercare uno stato di accetazione con una $BFS$(*breadth-first search*), garantendo quindi che $D$ esplori l'intero albero finché non trova uno stato di accettazione.

###### Dimostrazione
Supponiamo che $D$ abbia 3 nastri:
- il **primo** per contenere la **stringa** di **input**, che non verrá alterata
- il **secondo** contiene una copia del nastro di $N$ per qualche ramo(durante la computazione)
- il **terzo** tiene traccia della posizione di $D$ nell'abero generato da $N$

![[Pasted image 20221016145107.png]]

Ogni nodo dell'abero puó avere al massimo $b$ figli, quindi assegnamo ad ogni nodo un **indirizzo** rappresentato da una stringa nell'alfabeto $\Gamma_b=\{1,2,\dots,b\}$ (per esempio l'indirizzo $123$ rappresenta quello raggiungibile dal cammino primo figlio $\to$ secondo figlio $\to$ terzo figlio partendo dalla radice). Se una scelta non é possibile l'indirizzo non é valido.

Il terzo nastro contiene quindi una stringa di $\Gamma_b$, che rappresenta il ramo che sta computando $N$. 

$D$ di comporta quindi nella seguente maniera:
1. Inizialmente il nastro $1$ contiene $w$, $2$ e $3$ sono vuoti
2. copiamo $1$ su $2$ e inizializziamo $3$ ad $\epsilon$ (la radice)
3. Usiamo $2$ per simulare $N$ con input $w$ su un suo ramo: prima di ogni step consulta $3$ per decidere che scelta fare tra le possibili.
	- Se non rimangono simboli su $3$ ,la scelta non-deterministica non é valida o incontriamo una configurazione rifiutata proseguiamo al punto 4
	- Se incontriamo una configurazione accettatta, accettiamo allora anche l'input
4. Rimpiazziamo la stringa in $3$ con la successiva e ritorniamo al punto 2


## Enumeratori
Un'**enumeratore** é una macchina di Turing a singolo nastro collegata ad una stampante(che rappresentai il secondo nastro) che puo' usare per stampare delle stringhe.

![[Pasted image 20220928090856.png]]

Essa restituisce un flusso infinito di dati.

L'enumerator stampa tutte le stringhe con radice intera. Puo' inoltre generare ripetizioni, e le stringhe possono essere generate in qualunque ordine.

### Decimo Problema di Hilbert
Informalmente, il decimo problema di Hilbert é la ricerca di un'algoritmo in grado di testare se un polinomio ha radici intere.

Ancora oggi non esiste un tale algoritmo, ma provare che un problema é irrisolvibile era futile al tempo, quindi la dimostrazione arrivó solo negli anni 70, dopo l'introduzione del concetto di algoritmo.

### Tesi di Church-Turing
Nel 1936 Turing e Church pubblicarono un paper nel quale veniva usata la notazione $\lambda$-calcolo per definire un'algoritmo. Turing provó inoltre che un'algoritmo, inteso come sequenza di instruzioni volte a eseguire un compito era **equivalente** al concetto di algoritmo per le *TM*. ### Indecidibilitá
Ci sono alcune categorie di problemi irrisolvibili da un computer, per esempio verifica di un software.

Il primo problema che andiamo ad osservare é il problema dell'accettazione per le *TM*.

#### Accettazione per le *TM* (versione veloce)
Sia 
$$A_{TM}=\{<M,w>|\,M\;é\;una\;TM\;che\;accetta\;w\}$$
Dimostriamo che $A_{TM}$ é indecidibile.

Osserviamo che il problema é **decidibile positivamente**, ma perché un problema sia decidibile deve terminare su tutti gli input. 
Costruiamo quindi la *TM* $U$, che riconosce $A_{TM}$
$U$ = Dati in input $<M,w>$, dove $M$ é una *TM* e $w$ é una stringa
1. Simuliamo $M$ con input $w$
2. Se $M$ entra in uno stato di accettazione, $accetta$, se $M$ non entra in uno stato di rifiuto, $rifiuta$

$U$ peró entra in loop su input $<M,w>$ se $M$ entra in loop su $w$.
Proprio per questo motivo $U$ **non decide** $A_{TM}$.

> Se l'algoritmo potesse individuare se $M$ non termina su $w$, allora potrebbe entrare in stato di rifiuto peró questo non é possibile per un algoritmo.

#### Metodo della diagonalizzazione
> E' usato per controllare se due insiemi contengono lo stesso numero di elementi

Assumiamo che esistano due insiemi $A$ e $B$ e una funzione $f$, che assegna un valore di $A$ ad uno e un solo valore di $B$. Diciamo quindi che $f$ e' una funzione di **corrispondenza**.

> In una corrispondenza ad ogni valore di $A$ corrisponde ad un unico valore di $B$, e per ogni valore di $B$ esiste solo un valore di $A$ a cui corrisponde.

Introduciamo inoltre il concetto di insiemi numerabili e piu' che numerabili.

> Un'insieme e' numerabile se e' finito o ha al piu' grande come $N$

> Un'insieme e' piu' che numerabile se non e' infinito o comunque piu' grande di $N$ (es:$R$)

##### Esempio di metodo della diagonalizzazione
Dimostraimo che l'insieme $Q=\{\frac{m}{n}|m,n\in N\}$ e $N$ sono entrambi numerabili.

Per dimostrarlo basta mostrare che esiste una corrispondenza tra i loro elementi.

Un modo semplice per farlo e' elencare tutti gli elementi di $Q$ e accoppiare ad ognuno di essi un elemento di $N$, assicurandoci che ogni elemento di $Q$ appaia una sola volta nella lista.

Costruiamo quindi una *matrice infinita* contenente tutti i numeri razionali, dove la $i$-esima riga contiene solo elementi con numeratore $i$ e la colonna $j$-esima contiene solo elementi con denominatore $j$ .

> Il numero $\frac{i}{j}$ comparira' quindi una sola volta nella posizione $matr[i][j]$

Ora dobbiamo traformare la matrice in una lista, le righe e le colonne sono infinite, quindi elenchiamo tutti gli elementi sulle diagonali, iniziando dall'angolo.

Usando questa tecnica e' possibile pero' ottenere ripetizioni nella corrispondenza, quindi ignoriamo semplicemente l'elemento che casuserebbe la ripetizione, come in foto

![[Pasted image 20221108150626.png]]
###### Corollario
Poiche' non tutti i linguaggi sono numerabili, esistono linguaggi che non sono ne' decidibili ne' decidibili positivamente, poiche' i linguaggi sono piu' che numeraili mentre le *TM* sono numerabili.

> Ci sono piu' linguaggi che *TM*, quindi alcuni linguaggi non sono riconosciuti da alcuna *TM*

#### Dimostrazione dell'indecidiblita' dell'accettazione
Sia di nuovo
$$A_{TM}=\{<M,w>|\,M\;é\;una\;TM\;che\;accetta\;w\}$$

Assumiamo per assurdo che $A_{TM}$ sia decidibile.
Supponiamo che $H$ sia un decisore per $A_{TM}$, su input $<M,w>$, dove $M$ e' una *TM* e $w$ e' una stringa, allora

$$H\{<M,w>\}=\Big\{^{accetta\,se \;M\;accetta\,w}_{rifiuta\,se\;M\;non\;accetta\;w}$$
Costruiamo quindi una *TM* $D$ con $H$ come subroutine, $D$ chiama quindi $H$ per determinare cosa fa $M$ quando gli fornisci la sua stessa descrizione $<M>$, ma fa l'opposto, quindi 
$$D\{<M>\}=\Big\{^{accetta\,se\;M\;non\;accetta\;<M>}_{rifiuta\,se\;M\;accetta\;<M>}$$
ora proviamo a passare $D$ a se stessa, otteniamo quindi
$$D\{<D>\}=\Big\{^{accetta\,se\;D\;non\;accetta\;<D>}_{rifiuta\,se\;D\;accetta\;<D>}$$
ma quetsa e' una contraddizione, quindi ne' $H$ ne $D$ possono esistere in quanto $H$ non e' un decisore.

#### Dimostrazione dell'indecidibilita' dell'accettazione attaverso la diagonalizzazione

Riprendiamo la definizioni di $A_{TM}$,$H$ e $D$ di prima.

Costuiamo quindi una tabella che ha come righe le *MT*, e le loro descrizioni sulle colonne ponendo nella entry $Matr[M_x][<M_x>]$ se $M_x$ accetta o rifiuta $<M_x>$.

![[Pasted image 20221109112101.png]]

Poiche' $H$ e' una *TM*, e quindi lo e' anche $D$, questa deve essere presente nella lista di tutte le *TM*. 

![[Pasted image 20221109142326.png]]

Notiamo pero' che nella entry $Matr[D][<D>]$ si presenta una contradfdizione, poiche' D dovrebbe accettare $<D>$ (e quindi presentare il risultato opposto come da definizione), ma una macchiana deve poter accettare se' stessa, e quindi ne' $D$ ne $H$ possono esistere.

##### Pattern di dimostrazione dell'indecidibilita'
Una strategia per poter dimostrare che un problema e' indecidibile e' la riconduzione del problema stesso ad $A_{TM}$.### Indecidibilità del problema della fermata
Sia
$$HALT_{TM}=\{<M,w>|\,M\;e'\;una\;TM\;e\;M\;termina\;con\;input\;w\}$$
dimostriamo che e' indecidibile.

Assumiamo per **assurdo** che $HALT_{TM}$ sia decidibile, di conseguenza anche $A_{TM}$ e' decidibile.

Ipotizziamo che esista quindi una *TM* $R$ che decida $HALT_{TM}$. Costruiamo quindi un'altra *TM* $S$ che decida $A_{TM}$, con $S$ che opera nella seguente maniera:

Dati in input $<M,w>$, con $M$ descrizione di una *TM* e $S$ stringa:
1. Eseguiamo $R$ con input $<M,w>$
2. Se $R$ rifiuta, $rifiuto$
3. Se $R$ accetta, simuliamo $M$ su $w$ finche' non si ferma
4. Se $M$ accetta, $accetto$, altrimenti $rifiuto$

Quindi se $R$ decide $HALT_{TM}$, allora $S$ decide $A_{TM}$, ma poiche' $A_{TM}$ e' indecidibile, lo e' anche $HALT_{TM}$.
### Indecidibilita' del problema dell'emptiness
Sia 
$$E_{TM}=\{<M>|\,M\;e'\;una\;TM\;e\;L(M)=\emptyset\}$$
dimostriamo che $E_{TM}$ e' indecidibile.

Assumiamo per assurdo che $E_{TM}$ sia decidibile, allora esiste una *TM* $R$ che decide il problema.

Sia inoltre $M_1$ una *TM* che ha una stringa $w$ nella sua descrizione, e opera nella seguente maniera
$$M_1\{x\}=\Big\{^{se\;x\ne w,\;rifiuto}_{se\;x=w,eseguo\;M\;con\;w\;e\;accetto\;se\;M\;accetta}$$
> $M_1$ esegue il controllo sulle stringhe un carattere alla volta

Usiamo ora $R$ per costruire una *TM* $S$ che decide $A_{TM}$ nella seguente maniera:
$S$ = Dati in input $<M,w>$
1. Usiamo la descrizione di $M$ e la stringa $w$ per costruire $M_1$
2. Eseguiamo $R$ con input $M_1$
3. Se $R$ accetta, $rifiuto$, se $R$ rifiuta, $rifiuto$

> $S$ e' in gradi di costruire $M_1$ perche' deve solo aggiungere stati aggiuntivi per implementare l'eguaglianza fra stringhe

Quindi se $R$ potesse decidere $E_{TM}$, allora $S$ dovrebbe poter decidere $A_{TM}$, ma un decisore per $A_{TM}$ non puo' esistere quindi neanche $R$ puo' esistere### Indecidibilità della regolarità di un linguaggio
Definiamo il problema di determinare se una *TM* ha un'automa a stati finiti equivalente.

Sia 
$$REGULAR_{TM}=\{<M>|M\;e'\;una\;TM\;e\;L<M>\;e'\;un\;linguaggio\;regolare\}$$
dimostriamo che e' indecidibile.

Assumiamo che $REGULAR_{TM}$ sia decidibile, allora deve esiste una *TM* $R$ che lo decide. Definiamo quindi anche la *TM* $S$ che decide $A_{TM}$, prendendo in input $<M,w>$, con $M$ una *TM* e $w$ una stringa.

> Idea chiave: $S$ modifica $M$ in modo da fargli riconoscere un linguaggio regolare solo se $M$ accetta $w$

La *TM* $S$ funziona come segue:
Dati in input $<M,w>$, con $M$ *TM* e $w$ una stringa:
1. $S$ costruisce una *TM* $M_2$ come segue
	- $M_2$ = su input $x$
		 1. se $x$ e' della forma $0^n1^n$, $accetto$
		 2. se $x$ non e' della froma sopra indicata, eseguo $M$ con input $w$ e accetto solo se $M$ accetta $w$
2. Eseguo $R$ con input $<M_2>$
3. Se $R$ accetta, $accetto$, se $R$ rifiuta, $rifiuto$

> Notare che il linguaggio $\{0^n1^n|n\ge 0\}$ **non** e' regolare

Fondamentalmente $M_2$ controlla se $w$ appartiene ad un lingnuaggio non regolare, se non vi appartiene allora controllo se appartiene invece al linguaggio regolare $\Sigma^*$ , nel caso $M$ accettasse, e quindi anche $R$ accettasse, significherebbe che $S$ decide $A_{TM}$, ma questo non e' possibile, quindi $R$ non puo' decidere $REGULAR_{TM}$.

### Indecidibilitá dell'eguaglianza tra linguaggi
Sia 
$$EQ_{TM}=\{<M_1,M_2>|M_1\;e\;M_2\;sono\;TM\;e\;L(M_1)=L(M_2)\}$$
dimostriamo che $EQ_{TM}$ e' indecidibile.

Supponiamo che esista una *TM* $R$ che decida $EQ_{TM}$, e che esista inoltre un'altra *TM* $S$ che decide $E_{TM}$ come segue:
$S$ = su input $<M>$, dove $M$ e' una *TM*:
1. Eseguo $R$ con input $<M,M_1>$, dove $M$ e' una *TM* che *rifiuta* tutti gli input
2. Se $R$ accetta, $accetto$, se $R$ rifiuta, $rifiuto$

Se il linguaggio di $M_1$ o $M_2$ fosse il inguaggio vuoto $\{\emptyset\}$, allora $S$ dovrebbe essere in grado di decidere $E_{TM}$, ma poiche' il problema e' indecidibile lo e' anche $EQ_{TM}$.

### Corollario Indecidibilitá assoluta di $E_{TM}$
$EQ_{TM}$ non é né positivamente né negativamente decidibile
#### Dimostrazione
Per dimostrare che non é positivamente decidibile riduciamo il complementare di $EQ_{TM}$ ad $A_{TM}$ come segue:

Per input $<M,w>$, dove $M$ é una *TM* e $w$ una stringa, costruisco $M_1$ che rifiuta ogni input ed $M_2$ che esegue $M$ su ogni input e accetta se $M$ accetta. $M$ ritornerá $<M_1,M_2>$.

Quindi se $M$ accetta $w$, allora $M_2$ accetterá ogni stringa, ma poiché $M_1$ non accetta mai le due macchine non sono equivalenti.
Viceversa, se $M$ non accetta $w$, allora neanche $M_2$ accetterá, ma in questo caso $M_1$ e $M_2$ sarebbero equivalenti. quindi $f$ riduce $A_{TM}$ a $\overline{EQ_{TM}}$. 

Per dimostrare che il complemento di $EQ_{TM}$ non é decidibile positivamente mostriamo che esiste una riduzione per il complemento del problema appena citato a $A_{TM}$, ma il complemento del complemento é il linguaggio stesso## Riducibilitá
Con riducibilita' intendiamo la possibilita' di ridurre un problema $A$ ad un problema $B$ mostrando che esiste una funzione computabile che converte le istanze del primo problema ad instanze del secondo.

> Se tale conversione e' possibile diciamo che esiste una *riduzione*.

### Funzione computabili
Una funzione $f:\Sigma^*\to \Sigma^*$ e' una **funzione computabile** se una *TM* $M$ termina con $f(w)$ per ogni input $w$.

### Definizione
Un linguaggio $A$ e' **riducibile** ad un lignuaggio $B$, ovvero $A\le_m B$ se esiste una funzione computabile $f:\Sigma^*\to \Sigma^*$ che per ogni input $w$ 
$$w\in A \iff f(w)\in B$$

![[Pasted image 20221124113905.png]]

La riducibilita' ci permette di convertire il problema dell'appartenenza ad un linguaggio $A$ all'appatenenza a $B$.

> Per verificare che $w\in A$, usiamo la riduzione per mappare $w$ a $f(w)$ e verificare se $f(w)\in B$. 

#### Decidibilitá attraverso la riduzione
Se $A\le_m B$ e $B$ e' decidibile, allora $A$ e' decidibile.

Sia $M$ un decisore per $B$ e $f$ una riduzione da $A$ ad $B$,
Allora esiste un decisore $N$ per $A$:
Per input $w$:
1. Computa $f(w)$ 
2. Esegue $M$ con $f(w)$ e restituice cosa restituisce $M$

Se $w\in A$, allora $f(w)\in B$ poiché $f$ é una riduzione da $A$ a $B$, di conseguenza $M$ accetta $f(w)$ quando $w\in A$. La riduzione é quindi valida

## Problema della corrispondenza di Post (PCP) per stringhe non vuote
### Il problema
E' possibile descrivere il problema della **corrispondenza di Post** o **PCB** come una sorta di puzzle formati da diversi domino della forma 

![[Pasted image 20221114143724.png]]

L'obiettivo e' creare una lista di questi domino, anche con ripetizioni tali per cui ci sia un **match**.

> Si ha un match quando la stringa composta dalla meta' superiore di questi domino e' uguale a quella inferiore

Un'esempio di match e' 

![[Pasted image 20221114144057.png]]

> Inoltre per alcuni insiemi non e' possibile trovare un match.

### Definizione formale del problema
Sia $P$ un'insime di domino della forma $P=\{[\frac{t_1}{b_1}],[\frac{t_2}{b_2}],\dots,[\frac{t_k}{b_k}]\}$ e un match e' una sequenza $i_1,\dots,i_t$ dove $t_{i_1},\dots,t_{i_t}=b_{i_1},\dotsb_{i_t}$ allora 
$$PCP=\{<P>|P\;e'\;un'istanza\;del\;problema\;della\;corrisppondenza\;di\;post\;con\;un\;match\}$$

### Dimostrazione dell'indecidibilita'
La dimostrazione si effettua per riduzione da $A_{TM}$ attraverso l'accettazione di storie computazionali poiche' per ogni *TM* $M$ e input $w$, possiamo costruire un'istanza $P$ dove un match e' l'accettazione di una storia computazionale.

Per far cio' iniziamo con un domino che ha nella parte inferiore la configurazione iniziale e nella superiore la stringa vuota, e aggiungiamo a $P$ dei domino la cui parte inferiore e' la configurazione successiva.

Assumiamo inoltre, per comoditá, che:
1. $M$ non provi mai a muovere la testina a sinistra su input $w$ quando si trova all'inizio del nastro
2. Se $w$ é la stringa vuota, usiamo il carattere *blank* al suo posto durante la costruzione
3. Modifichiamo **PCP** per far sí che un match debba iniziare con il primo domino

L'ultima regola ci permette di definire $MPCP$ come 
$$MPCP=\{<P>|P\;e'\;un'istanza\;di\;PCP\;con\;un\;match\;che\;inizia\;col\;primo\;domino\;e\;con\;la\;parte\;inferiore\;dei\;domino\;non\;vuota\}$$

Dati quindi $<M,w>$ costruiamo quindi $P'$ che e' un' istanza di $MPCP$ che computa come segue:

mettiamo come primo pezzo il domino che ha la prima configurazione nella storia computazionale accettante , come richiesto da $MPCP$. Questo domino avrá quindi solo il simbolo # sulla parte superiore e la stringa $\#q_0,w_1,\dots w_n\#$ sulla parte inferiore.

> Il simbolo # è un nuovo simbolo non appartenente all'alfabeto del nastro e serve come separatore

![[Pasted image 20221128143652.png]]

Per ottenere un match dobbiamo far corrispondere la parte superiore a quella inferiore aggiuggendo dei domino. 
L'aggiunta dei domino provoca l'apparizione della prossima configurazione di $M$ nella stringa inferiore forzando l'esecuzione passo-passo di $M$.

# Complessitá Temporale
Anche se un problema é decidibile potrebbe non essere risolvibile in quanto impiegherebbe troppo tempo. Per questo é necessario introdurre il concetto di complessitá temporale.

## Definizione
Sia $M$ una **TM** non deterministica che termina su tutti gli input.
La **complessitá temporale**, o *running time*, di $M$ é quindi la funzione $f:N\to N$, dove $f(n)$ é il massimo numero di passi usati da $M$ su ogni input di linghezza $n$. 

Questa definizione utilizza il concetto di **analisi nel caso peggiore**, imponendo quindi un limite asintotico a $f(n)$. 

Diciamo inoltre che $M$ termina in tempo $f(n)$, e che quindi é una TM di tempo $f(n)$.

### La notazione di O-grande
Dato che non é sempre possibile stimare con certezza il tempo di esecuzione di un algoritmo, ricorriamo all'*analisi asintotica* per studiare il suo comportamento per input molto larghi.

La notazione **O-grande** ci permette quindi di descrivere la crescita di un'algoritmo per input finito, ignorando costanti moltiplicative e solo in funzione dell'ordine maggiore dell'espressione.

#### Definizione
Siano $f$ e $g$ funzioni $f,g:N\to R^+$.
Diciamo che $f(n)=O(g(n))$ se esistono due interi positivi $c$ e $n_0$ tali per cui $n\ge n_0$.

$f(n) \in O(g(n))$ significa che $f(n)$ **cresce**, a parte un fattore costante $c$ e trascurando un numero finito di valori (quelli $\le n_0$), al massimo come la funzione $g(n)$.

### La notazione o-piccola
Se O-grande impone un limite asintotico superiore , la funzione o-piccolo impone un limite asintotico **inferiore** alla crescita di una funzione.

#### Definizione
Siano $f$ e $g$ funzioni $f,g:N\to R^+$.
Diciamo che $f(n)=o(g(n))$ se $\lim\limits_{n\to \infty}\frac{f(n)}{g(n)}=0$ , quindi $f(n)$ diventa insignificante rispetto a $g(n)$ per valori infinitamente grandi.

Questa notazione é infatti poco utilizzata in quando un vincolo inferiore é solitamente poco significativo.


## Classi di complessitá temporale
Sia $t$ una funzione $t:N\to R^+$.
Definiamo come **classe di complessitá temporali** $TIME(t(n))$ l'insieme dei linguaggli decidibili da una TM $O(t(n))$.

### Complessitá temporale fra vari modelli
Esaminiamo come varia la complessitá temporale tra 3 modelli, una TM a singolo nasto, una TM multinastro e una TM multinastro non deterministica.

#### TM a nastro singolo vs TM multinastro
Sia $t(n)$ una funzione, con $t(n)\ge n$.
Ogni TM multinastro $M$ ha una TM a singolo nastro equivalente $S$ di tempo $O(t^2(n))$.
##### Dimostrazione
> Sappiamo che $S$ usa il suo singolo nastro per rappresentare i $k$ nastri di $M$.

Inizialmente $S$ copia il contenuto dei nastri di $M$ in un formato a lui leggibile, e poi prosegue con la simulazione di $M$.

Per ogni passo di $M$, $S$ deve fare due passaggi sulla porzione attiva del nastro: il primo per ottenere le informazioni necessarie a determinare il prossimo passo e il secondo per eseguirlo.
Inoltre per determinare il costo di ogni passo é necessario sapere la lunghezza del nastro di $S$, che é uguale alla somma delle porzioni attive di tutti i $k$ nastri di $M$. 

Ogni porzione attiva dei nastri di $M$ ha lunghezza al massimo $t(n)$, in quanto in $t(n)$ mosse potrebbe usare $t(n)$ celle se si muovesse sempre a destra. Di conseguenza una scansione del nastro attivo di $S$ ha costo $O(t(n))$, che é uguale al costo di ogni operazione di $S$.

Quindi per l'inizializzazione e l'esecuzione impiega $O(n)+t(n)\times O(t(n))=O(t^2(n))$ passi.

#### TM a singolo nastro non deterministiche vs TM a singolo nastro deterministiche
Sia $t(n)$ una funzione, con $t(n)\ge n$.
Ogni TM a singolo nastro non-deterministica $N$ ha una TM deterministica a singolo nastro $D$ di tempo $2^{O(t(n))}$.
##### Dimostrazione
Su un'imput di lunghezza $n$, ogni ramo di $N$ ha lunghezza $t(n)$ al massimo, e ogni nodo puó avere al massimo lunghezza $b$, in quanto $b$ sono le scelte legali prodotte dalla funzione di transizione di $N$.

Quindi il numero **massimo** di foglie nell'albero prodotto da $N$ é $b^{t(n)}$.

La simulazione procede esplorando l'albero in ampiezza. Il numero massimo di nodi dell'albero é meno del doppio del numero massimo di foglie, ed é quindi $O(b^{t(n)})$.  
Inoltre il tempo impiegato per attraversare l'albero fino ad un nodo arbitrario é $O(t(n))$, quindi il tempo di esecuzione di $D$ é $O(t(n)b^{t(n)})=2^{O(t(n))}$. 

$D$ in questo momento ha 3 nastri, ma é possibile convertirlo in uno equivalente facendo quadrare il tempo di esecuzione, che mantiene la complessitá identica.## Problemi di classe P
> Tutti i modelli computazionali deterministici ragionevolmente complessi sono **polinomialmente equivalenti**, ovvero uno puó simulare un'alto con una crerscita del tempo di esecuzione polnomiale

## Definizione
**P** é la classe di linguaggi decidibili in tempo polinomiale in una TM a singolo nastro deterministica.

$$P=\bigcup\limits_{k}TIME(n^k)$$
Notiamo inoltre che:
- **P** é un'invariante per tutti i modelli computazionali polinomialmente equivalente ad una *TM* deterministica a singolo nastro, ed é quindi una **classe** matematica **robusta**, non condizionata dalle particolarità dei singoli modelli
- **P** corrisponde alla classe di problemi risolvibili realisticamente da un calcolatore, e quindi esite un modo di risolverlo in tempo al piú polinomiale. 

#### Esempio di problema di classe P - PATH
Voglio controllare che l' esistenza di un cammino in un grafo sia polinomiale -> $Path\in P$

Dato un gtafo $G$ controlliamo tutti i possibili cammini da due vertici $s$ e $t$. Un cammino possibile e' una sequenza di nodi di $G$, con lunghezza al massimo $m$(il numero di vertici). Ma il numero di possibili cammini e' $m^m$, che e' esponenziale.

Per ottenereun tempo polinomiale dobbiamo quindi evitare la forza bruta(*bruteforce*). Per migliorare la ricerca possiamo usare la ricerca in ampizza, marchiando i nodi raggiungibili da $s$ attraverso cammini diretti di lunghezza $1,2,\dots ,m$, limitando il tmpo a polinomiale
##### Prova
Dato un input $<G,s,t>$, dove $G$ e' un grafo e $s$ e $t$ sono vertici
1. Etichetto il nodo $s$
2. Ripetiamo il seguente passaggio fino a che tutti i nodi non sono etichettati
	1. Ogni volta che trovo un arco $<a,b>$ con $a$ etichettato, etichetto anche $b$
3. Se $t$ e' etichettato, $accetto$, altrimenti $rifiuto$

La tappa $1$ e $3$ vengono eseguiti una sola volta, mentre la subroutine 2 viene eseguita $m$ volte, quindi la complessita' dell'algoritmo e' $2n\times n^2=2n^3$.
> Il caso peggiore avviene se tutti i nodi sono connessi e il grafo e' indiretto ## Problemi di classe NP
#### Esempio: la traiettoia Hamiltoniana
$$HAMPATH=\{<G,s,t>|G\;e'\;diretto\; con\;un\;cammino\;\;hamiltoniano\;tra\;se\;t\}$$
Un cammino hamiltoniano e' un cammino che tocca tutti i punti di un grafo una sola volta.

![[Pasted image 20221109091558.png]]

Un modo semplice per risolvere il problema e' provare tutti i cammini possibili e verificare che sia una cammino di hamilton, con tempo esponenziale (dato dalla forza bruta).

La traiettoia hamiltoniana e' **polinomialmente verificabile**.
In questo caso dato un cammino posso controllare che sia un cammino di hamilton in tempo polinomiale.

> *Verificare* l'esistenza di un cammino di hamilton e' piu' facile di *determinarla*

### Verificatori 
Un verificatore per un linguaggio $A$ e' un algoritmo $V$, dove
$$A=\{w\,|\,V\;accetta\;<w,c>\;per\;qualche\;stringa\;c\}$$
Misuriamo il tempo di verifica per i soli termini di lunghezza $w$, quindi un **verificatore di tempo polinomiale** termina in tempo polinomiale per una lunghezza $w$.
$c$ rappresenta quindi una sorta di certificato, che rappresenta le condizioni aggiuntive per appartenere ad $A$.

L'algoritmo esplora inoltre $w$ un passo alla volta, come le *TM*.

> Un linguaggio $A$ e' quindi **polinomialmente verificabile** se esiste un verificatore polinomiale

###### Esempio di certificato per il cammino di Hamilton
Un certificato per la stringa $<G,s,t>\in HAMPATH$ e' un cammino di hamillton da $s$ a $t$.

### Definizione
**NP** e' la classe di linguaggi che hanno un verificatore di tempo polinomiale

Un linguaggio $A\in NP$ se e solo se é deciso da una *TM* polinomiale non deterministica.

##### Esempio di problema NP - Clique
> Un *clique* e' un insieme di $k$ vertici di un grafo indiretto, dove ogni due nodi sono connessi da un'arco

Il problema e' determinare se un grafo contiene una *clique* di una certa dimensione
$$CLIQUE=\{<G,k>|\,G\;e'\;un\;grafo\;indiretto\;con\;una\;k-clique\}$$
Dimostriamo che e' un problema di classe NP.

> Un modo per dimostrarlo e' definire la condizione di clique come certificato.

Sia quindi $V$ il verificatore per $CLIQUE$:
Su input $<<G,k>,c>$
1. Vetrifichiamo che $c$ sia un sottografo di $G$ con $k$ nodi
2. Verifichiamo che $G$ contiene tutti gli archi che collegano tutti i nodi di $c$
3. Se $1$ e $2$ sono verificati, $accetto$, atrimenti $rifiuto$

Ogni passo viene ripetuto una volta sola, e sono tutte operazioni tempo polinomiali. $V$ è termina in tmepo polinomiale, quindi $CLIQUE\in NP$.

#### Esempio di problema NP
Sia 
$$SUBSET-SUM=\{<S,t>|S=\{x_1,\dots,x_k\}\;e\;per\;qualche \;sottotineme\;di\;S\;\Sigma y=t\}$$
dimostriamo che il problema e' NP.

> Quindi il problema e' la massimizzazione 
> Un esempio e' $<\{4,11,21,27\},25>\in SUBSET-SUM$ poiche' $4+21=25$ e $t=25$

Costruiamo quindi il verificatore $V$ per $SUBSET-SUM$
Su input $<<S,t>,c>$
1. Controlliamo se $c$ e' un'insieme di numeri la cui somma sia $t$
2. Controlliamo se $S$ contiene tutti i nuemri in $c$
3. Se entrambi $1$ e $2$ sono verificati, $accetto$, altrimenti $rifiuto$
> Il certificato sara' quindi il sottoinsieme stesso.
> Inoltre il problema e' NP poiche dati $k$ elementi in $S$, abbiamo $2^k$ possibilita'

Ogni passo viene ripetuto una volta sola, e sono tutte operazioni tempo polinomiali. $V$ è termina in tmepo polinomiale, quindi $SUBSET-SUM\in NP$.## $P$ vs $NP$
**P** é la classe di linguaggi decidibili in tempo polinomiale in una TM a singolo nastro deterministica, mentre **NP** é la classe di linguaggi verificabili in tempo polinomiale.

Per quanto i problemi $P$ e $NP$ abbiano definizioni diverse, non e' stato ancora possibile provare che esiste un singolo linguaggio $NP$ che non sia $P$.

Se le due classi fossero uguali allora ogni problema verificabile in tempo polinomiale sarebbe quindi decidibile in tempo polinomiale.

Quindi il problema $P=NP$ rimane ad oggi un problema senza soluzione.

> La maggior parte dei ricercatori credono che le due classi non siano equivalenti poiché non é stato possibile trovare un'algoritmo di tempo polinomiale per i problemi in $NP$. 

Rimangono quindi due possibilitá:
- $P$ é un sottoinsieme di $NP$
- Le due classi sono equivalenti

![[Pasted image 20221114092559.png]]## NP-Complettezza
Abbiamo mostrato prima che se fosse possibile dimostrare che un'agoritmo polinomiale esiste per un qualche problema di classe $NP$, allora tutti i problemi $NP$ sarebbero essere decidibili in tempo polinomiale.

I problemi **NP-completi** sono tutti problemi decidibili in tempo polinomiale.

#### Esempio di problema NP-Completo: SAT
> E' il primo problema NP-completo trovato

Il problema e' sostanzialmente verificare se una formula booleana e' soddisfacibile

Sia
$$SAT=\{<\phi>|\phi\;e'\;una\;formula\;booleana\;soddisfacibile\}$$

> Una formula booleana e' soddisfacibile se e' possibile valutarla come vera per qualche assegnamento di valori

###### Teorema di Cook-Levin
$SAT\in P \iff P=NP$

Il teorema di Cook afferma che $SAT$ é **NP-completo**.
> Le definizioni aggiuntive utili all'esame sono l'enunciato di *SAT* e della *np-completezza*

Grazie a questo teorema é possibile dimostrare come ogni problema **NP** puó essere ridotto a $SAT$. Grazie a questo se fosse possibile trovare una soluzione di tempo polinomiale per una *TM* deterministica a singolo nastro allora $P=NP$.
#### Riducibilita' in tempo polinomiale
> Una funzione e' detta polinomialmente computabile se una qualche *TM* $M$ termina per $f(w)$ 

Un linguaggio $A$ e' **riducibile in tempo polinomiale** rispetto ad un linguaggio $B$ se esiste una funzione polinomiale $f:\Sigma^*\to\Sigma^*$ e per ogni $w$
$$w\in A \iff f(w)\in B$$
Quindi un linguaggio e' $NP-completo$ se 
1. il linguaggio e' in $NP$
2. ogni linguaggio $NP$ e' polinomialmente riducibile ad esso
#### Ruolo nella classificazione dei problemi
Giocano un ruolo fondamentale nella risoluzione del problema $P=NP$, poiché se si scoprisse un algoritmo polinomiale per risolverne uno, tutti i problemi in NP potrebbero essere risolti in tempo polinomiale attraverso l’algoritmo di riduzione.
###### La riducibilita' polinomiale preserva l'ordine polinomiale
Se $A\le_p B$ e $B\in B$, allora $A\in P$
Supponiamo che $f$ riduca polinomialmente $A$ a $B$, descriviamo l'agoritmo  di tempo polinomaiale $N$ che decide $A$ come segue:
$N =$ Su input $w$:
1. Calcoliamo $f(w)$
2. Eseguamo $M$ con input $f(w)$ e riportiamo cosa produce
Sappiamo che $w\in A$ se $f(w)\in B$, da definizione di ridubilita', allora $M$ accetta $f(w)$ per ogni $w\in A$.

Inoltre $N$ termina in tempo polinomiale.

> Se $M$ risolve $B$ in tempo $O(Q(n))$, con $Q$ polinomio, allora e' possibile verificare che $N$ risolve $A$ in tempo $O(Q(P(n)))$, con $Q(P(n))$ polinomio.#### SAT e' NP-completo
> Mostriamo che e' possibile costruire una riduzione di tempo polinomiale per ogni linguaggio a SAT.

Mostriamo innazitutto che sat e' un problema di tipi NP.

Una macchina non deterministica polinomiale puo' indovinare l'assegnamento di una formula $\phi$ e accetta se l'assegnamneto la soddisfa.

Sia quindi $N$ una *TM* non deterministica che decide un linguaggio $A$ in tempo $O(n^k)$, per qualche costante $k$.

Una **tableau** di $N$ su $w$ e' una tabella $n^k\times n^k$ dove le righe rappresentano le configurazioni del ramo della computazione di $N$ su input $w$, come in figura

![[Pasted image 20221121091519.png]]

> Assumiamo che ogni configurazione inizi con e finisca con il simbolo #, che funge da delimitatore.
> 
> Inoltre la prima righa rappresentera' la configurazione inizale di $N$ su $w$, ed ogni riga segue quella precedente secondo la funzione di transizione di $N$.

Essendo il tableau il risultato di una computazione di $N$, ogni ramo di computazione accettante corrisponde ad un tableau accettante.

> Il problema quindi si riduce dall'accettazione di $w$ su $N$ al determinare se esiste una tavola per cui $N$ accetta $w$.

Definiamo quindi una formula $\phi$, prodotta da una riduzione polinomiale $f$ da $A$ a $SAT$.

Ora definiamo come **cella** ognuna delle caselle della tabella $(n^k)^2$, che contiene un simbolo di $C = Q \cup \Gamma \cup \{\#\}$, e rappresentiamo il contenuto di ogni cella con una variabile di $\phi$. 

> Quindi per ogni $i$ e $j$ nel range $1-n^k$ e per ogni $s\in C$, abbiamo una variabile $x_{i,j,s}$.
> Inoltre $x_{i,j,s}$ assume valore $1$ se $cell[i,j]$ contiene un valore di $C$.

Per poter far corrispondere $\phi$ ad un tableau accettante di $N$ per $w$ , rappresentiamo la formula come una congiunzione logica di 4 parti: 
$$\phi_{cella}\land\phi_{start}\land\phi_{move}\land\phi_{accept}$$

Dobbiamo ora garantire la corrispondenza tra la formula e il tableau, e per far cio' ci assicuriamo che ogni cella rappresenti un assegnamento, assicurato tramite la formula $\phi_{cell}$:

$$\phi_{cell}=\bigwedge_{1\le i,j\le n^k}[(\bigvee_{s\in C}x_{i,j,s})\land(\bigwedge_{s,t\in C|s\ne t}(\overline{x_{i,j,s}}\lor \overline {x_{i,j,t}}))]$$
> Per esempio $\bigvee_{s\in C} x_{i,j,s}$ contiene $x_{i,j,s_1}\lor x_{i,j,s_2}\lor \dots \lor x_{i,j,s_t}$
> Inoltre se $cell[i,j]=s$ allora $x_{i,j,s}=1$ altrimenti $x_{i,j,s}=0$

La formula $\phi_{cell}$ contiene quindi un frammento per ogni cella del tableau. La prima parte di $\phi_{cell}$ dentro le parentesi vincola che **almeno una** delle variabili in una una cella sia vera,  mentre la seconda vincola che **non piu'** di una variabile e' **vera** per ogni cella.

> Letteralmente, per ogni cella del tableau,

La formula $\phi_{start}$ assicura che la prima riga del tableau e' la configurazione iniziale, controllando frammento per frammento:
$$\phi_{start}=x_{1,1,\#}\land x_{1,2,q_0}\land x_{1,3,w_1}\land\dots\land x_{1,n^k,\#}$$

La formula $\phi_{accept}$ assicura che **esiste** una **configurazione accettante** nel tableau:

$$\phi_{accept}=\bigvee_{1\le i,j\le n^k}x_{i,j,q_{accept}}$$

La formula $\phi_{move}$ assicura che per ogni riga del tableau corrisponde una configurazione che segue legalmente la riga precedente secondo le regole di $N$.

Per far cio' ci assicuriamo che ogni finestra $2\times 3$ ha solo **celle legali**, ovvero se non viola le azioni specificate dalla funzione di transizione di $N$. 

> La finestra ci serve per osservare il comportamento dell'esecuzione di $N$ 

Se la riga in cima al tableau e' la configurazione iniziale e ogni finestra del tableau e' legale, allora ogni riga del tableau e' una configurazione che segue legalmente la riga precedente.

> Per provare l'affermazione precedente osserviamo che se la riga superiore di una finestra non ha simboli di stato adiacenti e' la cella centrale di una finestra che non contiene simboli di stato adiacenti sulla riga superiore.
>
> Di conseguenza lo stesso simbolo si trovera' uguale nella stessa posizione ma sulla cella inferiore, poiche' non e' stato alterato dalla funzione di transizione di $N$.
>
> La presenza di un simbolo di stato nella riga superiore garantisce che la riga inferiore sia aggiornata costantemente secondo la funzione di transizione.
>
> Di conseguenza se la configurazione superiore e' una configurazione legale lo e' anche quella superiore

$\phi_{move}$ stabilisce che tutte finestre nel tableau devono essere legali., ovvero

$$\phi_{move}=\bigwedge_{1\le i\le n^k,1<j<n^k}(la\;finestra\;(i,j)-esima\;e'\;legale)$$
scrivibile anche come 

$$\bigvee_{a_1,\dots ,a_6\;e'\;una\;finestra\;legale}(x_{i,j-1,a_1}\land x_{i,j,a_2}\land x_{i,j+1,a_3}\land x_{i+1,j-1,a_4}\land x_{i+1,j,a_5}\land x_{x+1,j+1,a_6})$$

##### Stime della riduzione
Innazitutto stimiamo il numero di variabili di $\phi$:
Ogni tableau ha $n^k\times n^k$ celle, quindi $n^{2k}$, e ogni cella ha $l$ variabili associate ad essa, dove $l$ e' il numero di variabili di $C$, quindi il numero di variabili non dipende dall'input $n$ ma dalla *TM* $N$.

Di conseguanza il numero di variabili e' $O(n^{2k})$.### Clique
> Un *clique* e' un insieme di $k$ vertici di un grafo indiretto, dove ogni due nodi sono connessi da un'arco

Il problema e' determinare se un grafo contiene una *clique* di una certa dimensione é cosí definito
$$CLIQUE=\{<G,k>|\,G\;e'\;un\;grafo\;indiretto\;con\;una\;k-clique\}$$

Si puó dimostrare che é NP-completo mostrando un a riduzione da $3SAT$.
## Dimostrazione
Sia $\phi$ una formula booleana della forma normale 3-congiuntiva(ogni clausola ha esattamente 3 letterali) con $k$ clausole. La riduzione genera quindi la coppia $<G,k>$, dove $G$ é un **grafo indiretto** e $k$ é il numero di clausole, dette anche **triple**, poiché composte dai 3 vertici che ne rappresentano i letterali, e rappresentante una clausola di $\phi$.

Ogni vertice del grafo ha un arco verso ogni altro vertice, con alcune eccezioni:
1. Non ci sono archi tra vertici di una stessa tripla
2. non ci sono archi tra vertici corrispondenti ad un letterale ed al suo negato( anche se appartengono a clausole differenti)

Dimostriamo che $\phi\in3SAT\iff <G,k>\in Clique$:
Se $\phi$ avesse un'assegnamento che lo soddisfa allora **ogni clausola** di $\phi$ ha **almeno** **un** letterale **vero**.

Prendiamo in considerazione quindi **un letterale vero** per **clausola**, i nodi selezionati corrisponderebbero a un **sottografo** rappresentante una $k-clique$, poiché ogni letterale appartiene a una tripla(clausola) diversa, e non avente vertici tra un letterale e il suo negato(per il punto $2$ delle eccezioni) mantenendo inoltre un'assegnamento valido.

Poiché ogni clausola in questo caso é soddisfatta possiamo conscludere che $\phi$ sarebbe soddisfacibile e quindi $CLIQUE$ é **NP-completo** poiché $CLIQUE\in NP$ ed esiste una riduzione da ogni linguaggio $NP$ a $3SAT$ e quindi a $CLIQUE$.
### 3SAT
Sia 
$$3SAT=\{<\phi>|\phi\;é\;una\;formula\;soddisfacibile\;della\;forma\;normale\;3\;congiuntiva\}$$
dove una formula é della forma normale congiuntiva se ogni clausola é connessa da un *AND*($\land$) e ogni suo letterale é connesso da or($\lor$), ed é della normale 3 congiuntiva se inoltre ogni clausola é composta da 3 letterali in or logico($\lor$).

> Se l'assegnamento é soddisfatto almeno un letterale per clausola deve essere vero.

## Dimostrazione
$3SAT\in NP$ poiché una *TM* non determinisca polinomiale puó generare un'assegnamento per una formula booleana $\phi$ e accettare se lo soddisfa.###### 1. Dare una definizione precisa di una Macchina di Turing
Una macchina di turing é una settupla composta da:
1. Un'insieme di stati della macchina
2. Un'alfabeto della macchina
3. Un'alfabeto del nastro, che contiene il carattere di padding(blank)
4. Una funzione di transizione
5. Uno stato iniziale
6. Uno stato di accettazione
7. Uno stato di rifiuto
Lo stato di accettazione deve inoltre diverso dallo stato di rifiuto

###### 2. Cos'é la computazione di una macchina di Turing per una stringa? Quando accetta e quando rifiuta?
Una computazione per una *TM* $M$ é un'applazione passo passo della funzione di transizione di $M$ per ogni carattere della stringa $w$.

$M$ usa quindi un nastro infinito a destra sul quale é rappresentata $w$ e una testina per leggere e scrivere su questo, e la testina é in grado di muoversi liberamente su di esso, un passo alla volta.

Una macchina di Turing, a differenza di un'automa a stati finiti, accetta una stringa appena entra in uno stato di accettazione, e le rifiuta appena entra in uno stato di rifiuto. L'entrata in uno di questi stati termina quindi la computazione.

###### 3. Che differenza c'é tra non terminazione e rifiuto di una stringa? La terminazione é garantita per il calcolo di una *TM* per una stringa?
Definiamo come non terminazione la condizione per cui la computazione di una *TM* non termina a causa di un loop. Quando una *TM* é in un loop significa che non entrerá mai in uno stato di accettazione o rifiuto.

Invece una *TM* rifiuta una stringa se determina che non appartiene al linguaggio.

Inoltre la terminazione é garantita solo per i decisori, quindi quelle *TM* che sono sempre in grado di detrminare se una stringa appartiene all'alfabeto della macchina  oppure no, senza mai entrare in un loop.

###### 4. Quando un linguaggio viene riconosciuto da una *TM*?
Un linguaggio $L$ é riconosciuto da una *TM* $M$ se per ogni stringa $w$ appartenente al linguaggio di $M$, questa accetta la stringa sé e solo sé appartiene a $L$. 

###### 5. Date un'esempio di *TM* secondo la vostra definizione
Un'esempio di *TM* secondo la mia definizione é la macchina che accetta tutte le stringhe: questa macchina ha lo stato di inizio uguale allo stato di accettazione, uno stato di rifuto e una funzione di transizione che, per ogni carattere letto porta sempre allo stato di accettazione.

###### Definire la Np-Completezza per un linguaggio, spiegare il suo ruolo nella classificazione dei problemi NP e le sue proprietá piú importanti
Partiamo dalla definizione di NP.
NP é la classe dei problemi decisionali verificabili in tempo polinomiale
Un linguaggio appartiene a questa classe solo se é deciso da una macchina di turing polinomiale non deterministica.

Ora definiamo in problema come NP-completi la classe di problemi NP per i quali esiste una riduzione di tempo polinomiale da ogni problema NP ad esso.

Giocano un ruolo fondamentale nella risoluzione del problema $P=NP$ poiché se si scoprisse un algoritmo polinomiale per risolverne uno, tutti i problemi in NP potrebbero essere risolti in tempo polinomiale attraverso l’algoritmo di riduzione.

### The big 3
###### 1. Definire il problema dell'accettazione per le *TM*,enunciare la principale proprietá nota del problema e dimostrarlo.
Definiamo il problema dell'accettazione come segue:
$$A_{TM}=\{<M,w>|M\;é\;una\;TM\;che\;accetta\;w\}$$

ovvero é il problema di verificare se una *TM* accetta o no una stringa.

Sappiamo che é un noto problema indecidibile, quindi dimostriamo questa proprietá.

Supponiamo per assurdo che $A_{TM}$ sia decidibile, allora deve esistere un decisore $H$ che lo decide, che su input $<M,w>$ :
- $accetta$ se $M$ accetta
- $rifiuta$ se $M$ rifiuta

Definiamo un'altra *TM* $D$ che ha $H$ come subroutine. $D$ prendi quindi in input $M$ e prova ad eseguire $H$ per determinare cosá ritornerebbe $M$ passandogli in input la sua descrizione.
$H$ fornirá quindi in input alla *TM* presente nella sua routine $<M,<M>>$.
$D$ invece ritornerá l'oppoto di quanto restituito da $H$, quindi
- accetta se $M$ non accetta la sua descrizione
- rifiuta se $M$ accetta la sua descrizione

Peró provando ad eseguire $D$ su se stesso otteniamo che
- $D$ accetta se $D$ non accetta la sua descrizione
- $D$ rifiuta se $D$ accetta la sua descrizione
ma $D$ non puó non accettare la sua descrizione in quanto questo produrrebbe una contraddizione. Di conseguenza né $D$ ne $H$ possono esistere e di conseguenza $H$ non é un decisore di $A_{TM}$.

###### 2. Enunciare il teorema di Post e dimostrarlo
Il teorema di Post afferma che un linguaggio é decidibile se é sia positivamente che negativamente decidibile.

Proviamo a dimostrare l'enunciato.

Se un **linguaggio** $A$ fosse **decidibile**, possiamo osservare che sia il linguaggio stesso che il suo complemento sono *riconoscibili*, poiché ogni linguaggio decidibile é anche riconoscibile, e il complemento di un linguaggio decidibile é a sua volta decidibile.

Se invece sia $A$ che il suo complemento $\overline A$ sono *turing-recognizable*, definiamo allora un riconoscitore $M_1$ per $A$ e un'altro $M_2$ per $\overline A$. 
Definiamo allora un decisore per $M$ per $A$, che su input $w$:
1. Simula sia $M_1$ che $M_2$ su $w$ in parallelo
2. Se $M_1$ accetta, *accetta*, se $M_2$ rifiuta, *rifiuta*

$M$ ha quindi due nastri per poter simulare $M_1$ e $M_2$ in parallelo, e per far ció alterna le esecuzioni, un passo ciascuno fino all'accettazione.

Poiché ogni stringa é in $A$ oppure nel suo complemento, $w$ deve essere accettata da $M_1$ o $M_2$, e $M$ termina quando una delle due *TM* termina, allora é un decisore per $A$, poiché termina sempre ed é in grado di decidere se la stringa appartiene ad $A$.

###### 3. Enunciare il problema Clique e dimostrare che é NP-completo

Partendo dalla definizione di una clique come un'insieme di $k$ vertici di un grafo indiretto, per cui ogni nodo di questo insieme é connesso ad ogni altro da un'arco, definiamo il problema Clique come segue
$$CLIQUE=\{<G,k>|\,G\;e'\;un\;grafo\;indiretto\;con\;una\;k-clique\}$$
ovvero il problema di determinare se un grafo contiene una clique di dimensione $k$.

Si puó dimostrare che é NP-completo mostrando un a riduzione da $3SAT$.

Sia $\phi$ una formula booleana della forma normale 3-congiuntiva(ogni clausola ha esattamente 3 letterali) con $k$ clausole. La riduzione genera quindi la coppia $<G,k>$, dove $G$ é un **grafo indiretto** e $k$ é il numero di clausole, dette anche **triple**, poiché composte dai 3 vertici che ne rappresentano i letterali, e rappresentante una clausola di $\phi$.

Ogni vertice del grafo ha quindi un arco verso ogni altro vertice, con alcune eccezioni:
1. Non ci sono archi tra vertici di una stessa tripla
2. non ci sono archi tra vertici corrispondenti ad un letterale ed al suo negato( anche se appartengono a clausole differenti)

Dimostriamo ora che $\phi$ soddifa $3SAT$ sé e solo sé $<G,k>$ soddisfa $Clique$:
Se $\phi$ avesse un'assegnamento che lo soddisfa allora **ogni clausola** di $\phi$ ha **almeno** **un** letterale **vero**.

Prendiamo in considerazione quindi **un letterale vero** per **clausola**, i nodi selezionati corrisponderebbero a un **sottografo** rappresentante una $k-clique$, poiché ogni letterale appartiene a una tripla(clausola) diversa, e non avente vertici tra un letterale e il suo negato(per il punto $2$ delle eccezioni) mantenendo inoltre un'assegnamento valido.

Poiché ogni clausola in questo caso é soddisfatta possiamo conscludere che $\phi$ sarebbe soddisfacibile e quindi $CLIQUE$ é **NP-completo** poiché $CLIQUE\in NP$ e $CLIQUE$ é riducibile a $3SAT$, che é **NP-completo**.

Il teorema di Post enuncia che 
un linguaggio é **decidibile** se é sia **Decidibile Positivamente** che **Decidibile negativamente**.

## Dimostrazione
Se un **linguaggio** $A$ fosse **decidibile**, possiamo osservare che sia il linguaggio stesso che il suo complemento sono *riconoscibili*, poiché ogni linguaggio decidibile é anche riconoscibile, e il complemento di un linguaggio decidibile é a sua volta decidibile.

Se invece sia $A$ che il suo complemento $\overline A$ sono *turing-recognizable*, definiamo allora un riconoscitore $M_1$ per $A$ e un'altro $M_2$ per $\overline A$. 
Definiamo allora un decisore per $M$ per $A$, che su input $w$:
1. Simula sia $M_1$ che $M_2$ su $w$ in parallelo
2. Se $M_1$ accetta, *accetta*, se $M_2$ rifiuta, *rifiuta*

$M$ ha quindi due nastri per poter simulare $M_1$ e $M_2$ in parallelo, e per far ció alterna le esecuzioni, un passo ciascuno fino all'accettazione.

Poiché ogni stringa é in $A$ oppure nel suo complemento, $w$ deve essere accettata da $M_1$ o $M_2$, e $M$ termina quando una delle due *TM* termina, allora é un decisore per $A$, poiché termina sempre ed é in grado di decidere se $w\in A$.