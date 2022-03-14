##### Operatore di proiezione
Dato una relazione e un'insieme di attributi tutti appartenenti ad A, l'operatore di proiezione $\Pi_{A_i,A_j,\dots,A_k}(r(A))$ produce come risultato una relazione con 
- schema :$\{A_i,A_j,\dots,A_k\}$
- Istanza tutte le tuple della relazione argomento A, ma solo rispetto ai campi $A_i,A_j,\dots,A_k$
$\Pi$

TL;DR: Seleziona le colonne, creeando una tabella a partire dal "nome" degli attributi

###### Cardinalita' della proiezione
La cardinalita' della proiezione e' un numero compreso tra 0 e la cardinalita' di $r(A)$, poiche' l'operatore escude le ripetizioni.

###### Proprieta' della proiezione
Se gli attributi proiettati formano una superchiave, allora la cardinalita' della proiezione e' uguale alla cardinalita' della relazione di input.

#### Composizione degli operatori 
L'algebra relazionale è composizionale, ovvero si possono costruire espressioni di algebra relazionale componendo insieme operatori.

##### Risultato della composizione 
Il risultato e' una relazione che ha come schema quello della proiezione e come isanza solo le tuple che soddisfano il predicato.

#### Correttezza sintattica
Per verificare che l'espressione algebrica sia sintatticamente corretta bisogna verificare che gli operatori algebrici siano coerenti o consistenti con gli argomenti.

#### Operatori insiemistici
- Operatore unione $\cup$
- Operatore differenza - 

Gli operatori insiemistici richiedono per definizione che gli schemi delle relazioni argomento siano identici, ovvero che abbaino le stesse caratteristiche(schema).

Il risultato dell'operatore insiemistico sulle relazioni
argomento $r_1 (A)$ ed $r_2 (A)$ è una relazione che ha lo schema delle relle relazioni argomento e come istanza l'unione o la differenza delle tuple di $r_1$ ed $r_2$.

##### Cardinalita' dell'unione 
La cardinalita' dell'unione e' un numero compreso tra 0 e la somma delle cardinalita' delle due relazioni.

L'unione esclude le ripetizioni.

##### Cardinalita' della differenza 
La cardinalita' della differenza e' un numero compresto tra 0 e la cardidnalita' della prima relazione presa come argomento.

##### Proprieta' della differenza 
La differenza non gode della proprieta' commutativa

#### Operatore intersezione
E' definito su relazioni aventi lo stesso schema. Produce una relazione con lo stesso schema delle relazioni argomento e con istanza $r_1\cap r_2$, ovvero le tuple di $r_1$ contenute anche in $r_2$.

#### Operatore di ridenominazione
Ha come argomento una relazione, di cui ne cambia il nome degli attributi(una parte o tutti).

Esso produce una relazione copia virtuale $r'(A')$, mantenendo invariata la base di dati.

E' possibile ridenominare pure uno schema.

##### Esercizi
Elencare il codice dei pazienti che non sono mai stati ricoverati.

$\Pi_{COD}(Pazienti)-\rho_{COD<-PAZ}(\Pi_{PAZ}(Ricoveri))$

Elencare le città in cui risiedono sia medici che pazienti

$\Pi_{Residenza}(Pazienti)\cap \Pi_{Residenza}(Medici)$

#### Prodotto cartesiano
Date due relazione disgiunte, il loro prodotto cartesiano $r_1(A)\times r_2(B)$ produce una relazione $r'$ con schema composto dall'unione degli schemi e con istanza la combinazione di tutte le tuple di $r_1(A)$ con tutte le tuple $r_2(B)$.

Questo operatore non ha un'utilizzo diretto ma sara' utile nella difinizione di altri operatori.

##### Proprieta' del prodotto cartesiano
Il prodotto cartesiano gode della proprieta' commutativa

Il prodotto cartesiano ha cardinalita' $|r_1(A)|\times|r_2(B)|$

#### Operatore di join $⋈_0$
L'operatore di teta-join serve a costruire informazioni estratte da piu' relazioni.

Serve a mettere in correlazione informazioni di una relazione con informazioni di un'altra relazione.

Date due relazioni $r_1(A)$ ed $r_2(B)$ che non hanno attributi in comune e una condizione di join, da intendersi come una congiunzione di confronti tra attributi del tipo $A_i φ B_j$ dove $φ=\{<,>,=,\ne,\ge,\le\}$
Il theta-join e' definito come $r_1(A)⋈_0 r_2(B)=\sigma_0(r_1(A)\times r_2(B))$

Il Θ-join considera congiunzioni di qualsiasi tipo di confronti.

##### Cardinalita' del Θ-join
La cardinalita' del Θ-join e' 
$$0\le |r_1(A)⋈_Θr_2(B)|\le |r_1(A)|\times |r_2(B)|$$

#### Dot notation
L'operatore di ridenominazione appesantisce  la lettura delle espressioni algebriche, quindi quando ho attributi con stesso nome su relazioni diverse, posso considerare il nome dell'attributo specificando la tavola a cui appartiene.

###### Esercizio
Trovare cognome e nome del primario del reparto in cui è stato ricoverato il paziente Missoni Luigi

$$\Pi_{Cognome,Nome}((\sigma_{Cognome='Missone'\land Nome='Luigi'}(Pazienti)⋈_{Cod=Pz}Ricoveri)⋈_{Reparto=reparti.COD}Reparti)⋈_{Primario=MATR}Medici$$