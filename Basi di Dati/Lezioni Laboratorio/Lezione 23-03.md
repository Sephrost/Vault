#### Sematica di Codd del valore nullo
Il valore nullo indica che per una tupla non e' possibile associare valori diversi da quello nullo.

E' un vero e proprio valore che appartiene a tutti i domini

Puo' avere diversi significati:
- Informazione esistente ma mancante
- Informazone inesistente
- Assenza di informazione

Il modello relazionale non distingue i diversi casi.

La semantica di Codd del valore nullo è il comportamento formale di una interrogazione a fronte di tuple che contengono valori nulli.

##### Null=Costante
Quando il valore della tupla, in corrispondenza dell'attributo $A_i$ è nullo, il valore di verità del confronto di un attributo con la costante è **sconosciuto**.

Passiamo quindi da una logica a 2 valori(Vero/Falso) ad una a **3 valori**(Vero(**T**)/Falso(**F**)/Sconosciuto(**U**))

###### Casi possibili
1. Costante/Costante
2. Costante/Null
3. Null/Costante
4. Null/Null

In caso sia presente un valore nullo, il valore di verita' sara' sempre sconosciuto.

##### Valori nulli con espressioni algebriche

%%Ricopiare tabelle%%

In caso di And, otteniamo vero solo se entrambi gli operandi sono veri.

In caso di Or, otteniamo vero solo se uno degli operandi e' vero.

##### Funzione di collasso

Non sapendo se la tupla soddisfa il predicato se da esito Sconosciuto, la considero solo se la funzione di collasso e' Vero.

p(t)|c(p(t))
--|--
F|F
U|F
T|T

##### Ricerca di un valore nullo

PEr cercare una tupla che ha(o non ha) valore nullo in corrispondenza di un attrinuto, posso usare le clausole
- IS NULL
- IS NOT NULL

#### Join Esterni
Distinguiamo 3 tipi di outer join
- Left Join
- Right Join
- Full Join

L'outer join e' un theta join qualsiasi.

Sono dei join che mettono ben in evidenza alcune
informazioni (esempio, visualizzare contemporaneamente clienti che sono anche direttori e clienti che non lo sono).

##### Left Join
Il left join(⟕)
- Vengono prese in ocnsiderazione tutte le tuple dell'operando sinistro
- Verifico se le tuple del secondo operando sono in join col primo
- Qualora una tupla del primo operando non faccia join con nessuna tupla del secondo  operando, si inseriscono valori nulli in cirrispondenza degli attributi della seconda tavola


#### Gruppi di proprieta'
##### Proprieta' 