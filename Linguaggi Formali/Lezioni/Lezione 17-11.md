# Traduzione 
## Definizioni dirette dalla sintassi 

Vogliamo produrre informazioni aggiuntive al riconoscimento, per far cio' associamo ad ogni nodo dell'albero associamo degli attributi che ci permettano di capire il valore delle sottoespressioni corrispondente ad un certo sottoalbero.

![[pngs/2021-11-17--1637146792_386x307_scrot.png]]

Una **Definizione Diretta dalla Sintassi ** (o SDD, da
*Syntax-Directed Definition*) è una grammatica le
cui produzioni sono associate a zero o più **regole
semantiche** che specificano come calcolare il
valore degli attributi associati ai nodi degli alberi
sintattici della grammatica.

![[pngs/2021-11-17--1637148207_206x149_scrot.png]]

dove $n.v$ e' il valore del numero, e $E.v|T.v|F.v$ e' il valore di $E|T|F$.

%%e' riferita all'immagine sopra%%

### Attributi
Un **attributo** e' una **coppia** *nome,valore* che rappresenta una qualunque **informazione** associata ad un **nodo** di un'albero sintattico.

### Albero sintattico annotato 
Un albero sintattico annotato e' un'albero sintattico in cui ogni noto puo' essere annotato con zero o piu' attributi.

#### Albero sintetizzato 
Un attributo di un nodo $N$ in un'albero annotato si dice **sintetizzato** se il suo **valore** dipende da quello degli **attributi e dei figli ** di $N$ ed eventualmente dagli attributi di $N$ **stesso**.

Il valore di un attributo sintetizzato per da un nodo $N$ e' determinato da una regola semantica associata ad una sua produzione.

Anche gli attributi possono essere sintetizzati.

#### Attributi ereditati
Un attributo di un nodo $N$ in un albero annotato si dice **ereditato** se il suo valore dipende da quello degli attributi del padre e dei fratelli.



