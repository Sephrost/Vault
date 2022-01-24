## Traduzione
Un **parser** ci permette solo di capire se un'espressione é corretta sintatticamente,

Per valutare le espressioni vogliamo produrre **informazioni** aggiuntive al riconoscimento, per far cio' **associamo** ad ogni **nodo** dell'albero associamo degli **attributi** che ci permettano di capire il valore delle sottoespressioni corrispondente ad un certo sottoalbero.

![[Pasted image 20220110143220.png]]


### Definizioni dirette dalla sintassi

#### Prefazione

Un **attributo** è una **coppia** (nome, valore) che rappresenta una qualunque **informazione** associata ad un **nodo** di un albero sintattico.

Un **albero** sintattico **annotato** è un albero sintattico in cui ogni **nodo** può essere annotato con **zero o più attributi**.

#### Definizione

Una **Definizione Diretta dalla Sintassi ** (o SDD, da
*Syntax-Directed Definition*) è una grammatica le
cui produzioni sono associate a zero o più **regole
semantiche** che specificano come calcolare il
valore degli attributi associati ai nodi degli alberi
sintattici della grammatica.

Il **valore** di eventuali **attributi** associati ai simboli terminali è fornito dal **lexer**.

###### Esempio

![[Pasted image 20220110143834.png]]

#### Attributi sintetizzati 
Un attributo di un nodo $N$ in un'albero annotato si dice **sintetizzato** se il suo **valore** dipende da quello degli **attributi e dei figli ** di $N$ ed eventualmente dagli attributi di $N$ **stesso**.

Il valore di un attributo sintetizzato per da un nodo $N$ e' determinato da una regola semantica associata ad una sua produzione.

###### Esempio

![[Pasted image 20220110144420.png]]

Il valore dell'attributo sintetizzato $s$ associato alla variabile $A$ in una sua produzione $A\to X_1X_2..X_n$ é indicato nella seguente maniera:

- $A.s=f(X_1.a_1,X_2.a_2,...,X_n.a_n)$

#### Attributi ereditati 

Un **attributo** di un nodo $N$ in un albero annotato si dice **ereditato** se il suo valore dipende da quello degli attributi del padre e dei fratelli.

###### Esempio

Il valore dell'attributo $e$ associato alla vairabile $A$ per una produzione $B\to X_1X_2..A..X_n$ é indicato nella seguente maniera:

- $A.e=f(B.a,X_1.a_1,X_2.a_2,...,X_n.a_n)$


### Ordine ddi valutazione degli attributi

#### Grafo delle dipendenze

Se il **calcolo** di un'**attributo** sintetizzato (es:$A.a$) richieda di **conoscere** il valore di un'**altro attributo** (es:$B.b$), allora scriviamo

$A.a=f(..,B.b,..)$

Per indicare ció introduciamo un **grafo delle dipendenze**, che attraverso l'utilizzo di <i style="color:red;">frecce rosse tratteggiate</i>, ci permette di indicare le **dipendenze** per la sintesi di un'attributo.

Se il grafo delle dipendenze contiene dei **cicli**, **non** é possibile trovare un'**ordine** di valutazione degli attributi.

#### Definizione S-attribuita
Una SDD si dice **S-attribuita** se contiene **solo** attributi **sintetizzati**.

#### Definizione L-attribuita
Una SDD si dice **L-attribuita** se per ogni **produzione** $A\to X_1X_2...X_n$ ed ogni **attributo ereditato** $X_i.e$, la **regola** semantica che definisce i valori di $X_i.e$ **dipende** solo da
- gli **attributi ereditati** da $A$
- gli **attributi sintetizzati** ed **ereditati** dal corpo della produzione ma a **sinistra** di $X_i$

##### Osservazioni
- Ogni SDD é sia S-attribuita che L-attribuita
- Ogni SDD L-attribuita ha un grafo delle dipendenze aciclico