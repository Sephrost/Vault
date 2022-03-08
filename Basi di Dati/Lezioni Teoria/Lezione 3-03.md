### Modello relazionale 
#### Relazione 
Una relazione e' una coppia definita da:
- uno schema di una relazione
- delle istanze(o stati) della relazione
#### Attributo
Un attributo di una relazione e' definito da una coppia $A_i:T_i$, dove:
- $T_i$ e'e il tipo dell'attributo
- $A_i$ e' il nome dell'attributo

##### Tipi di un'attributo
Il tipo di un dominio e' caratterizzato da:
- $T_i$: nome identificativo del tipo
- $D_i$: dominio di valore(int -> Naturali)
- Collezione di operazioni abilitati ad agire sul dominio(+,-,...)
- Operazioni di confronto(<,>,<=,...)

Il tipo di una relazione puo' essere:
- Standard
	- *Integer,Real,String,Char,Date,Boolean*
- Utente
	- *Enumerativo*
###### Dominio di un attributo

Un tipo e' sempre associato ad un dominio, ovvero l'insieme di valori

$$D_i=dom(A_i)$$

#### Valore nullo 
Quando non si conosce il valore di un attributo, e' possibile utilizzare il valore nullo(o NULL), presente in tutti i domini.

$$\forall T_i, NULL\in D_i$$

In alternativa si puo' utilizzare un valore di default(soluzione sconsigliata).
##### Schema di una relazione
Lo schema di una relazione e' un insieme di attributi con la seguente notazione:

$$\{A_1:T_1,A_2:T_2,\dots,A_n:T_n\}$$

Una relazione puo' essere senza nome, ovvero essere composta solo dall'insieme dei suoi attributi.

Una relazione con nome presenta la seguente notazione:

$$R(A_1:T_1,A_2:T_2,\dots,A_n:T_n)$$

dove $R$ è un generico nome di relazione.

In uno shcema di relazione tutti i nomi devono essere distinti:
$$\forall i,j A_i\ne A_j$$

Possono esistere invece tipi uguali all'interno della stessa relazione.

Inoltre l'ordine delgi attributi e' irrilevante.

###### Notazione semplificata

E' possibile semplificare una relazione omettendo il tipo, ma nei DBMS il tipo va' sempre specificato.

###### Notazione generale
Dato l'insieme degli attributi $A:\{A_1:T_1,A_2:T_2,\dots,A_n:T_n\}$

si puo' usare la notazione $R(A)$ , dove R e' il nome dello schema per indicare la relazione.

##### Grado di una relazione
LA cardinalita' $|A|$ di uno schema di relazione e' il numero di attributi dello schema A, ed e' detto gradi un a relazione.

Il grado di una relazione deve essere almeno uguale ad 1:
$$|A|\ge 1$$

##### istanza di una relazione
Dato uno schema ordinato
$$A:{A:1,T_1,\dots,A_n:T_n}$$

definiamo istanza l'insieme di tuple 

$$<V_1,v_2,\dots,v_n>$$

per cui vale la proprieta' 
$$\forall i,v_i \in dom(A_i)$$

##### Cardinalita' di una relazione
LA cardinalita' $|r|$ dell'istanza di una relazione$r$ e' il numero di tuple appartenenti alla relazione. E' anche detta cardinalita' di una relazione.

La cardinalita' di una relazione puo' essere vuota
$$|r|\ge 0$$

##### Notazioni ibride
Utilizziamo le lettere maiuscole quando ci riferiamo ad una relazione

Utilizziamo le lettere minuscole per riferirmi all'istanza di una relazione.

##### Relazione

Una relazioen e' def

##### Tupla 
Data una relazione $r$, per indicare la singola tupla utilizzo la notazione
$$t=<v_1,v_2,\dots,v_n>$$

dove t prende i valori all'interno della relazione $r$

###### Valori di una tupla

Per indicare il valore di una tupla $t$ in corrispondenza di un attributo $A_i$, utilizziamo la notazione $t[a_i]$, quindi
$$t[A_i]=v_i$$

E' possibile indicare piu' attributi di una tupla:
$$t[A_i,A_j,A_k]$$

Non essendo importante l'ordine degli attributi, la tupla non è altro che una funzione che fa corrispondere ad ogni attributo un valore del suo dominio

###### Tupla compatibile con uno schema
Una tupla e' compatile con uno schema di una relazione se: 
- e' una funzione totale su A
- ogni valore prodotto dalla dupla appartiene al dominio 
- vale il vincolo $\forall a_i,t[A_i]\in dom(A_i)$
#### vincoli locali
I vincoli locali sono caratterizzazioni dei valori possibili delle tuple in modo che i valori rispettino la realta' che volgiamo rappresentare.

##### Vincoli locali di dominio
Per ogni attributo ho un'insieme ben definito(anche infinito) di valori possibili.

Qualsiasi valore del dominio e' atomico, ma un attributo il cui valore e' una relazione non e' atomico.

##### Relazione in prima forma normale

Una relazione e' in prima forma normale quand otutti gli attributi sono abbinati ai domini di valori atomici.


##### Vincolo di identificazione
L'identificazione nel modello rlazionale si attua attraverso il vincolo di chiave relazionale.

E' il contesto applicativo che suggerisce la nozione di vincolo di chiave relazionale.

LE chiavi relazionali possono essere composti da piu' valori.

##### Superchiave

Data una relazione r(A), un sottoinsieme di attributo $sk\subseteq A$ e' una superchiave se:
$$\forall i,j(t_i[sk]=t)j[sk])\to(t_j[A]=t_j[A])$$