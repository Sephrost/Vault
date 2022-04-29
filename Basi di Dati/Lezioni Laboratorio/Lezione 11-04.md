## SQL
Contiene sia il DDL(Data definition language) che il DML(Data manipulation language)

Le interrogazioni di effettuano attraverso query.

E’ il linguaggio di riferimento per tutti i DBMS
relazionali e non.

### DDL
Con il linguaggio DDL si ponno :
- Creare domini
- Creare tabelle
- Definire vincoli

#### Stringhe
E' uno dei piu' generici.
###### Caratteri
Possono avere
- Lunghezza fissa (`char(length)`)
- Lunghezza variabile(`varchar(max_length)`)
- Se la lunghezza non e' specificata si assume sia 1

#### Numeri
##### Tipi numerici esatti
- Numeri decimali(`decimal(precisione,scala)` oppure `numeric(precisione,scala)`)
	- Precisione: numero totale di cifre decimali
		- E' opzionale
	- Scala: numero di cifre decimali dopo la virgola
- Interi (`smallint,integer`)
- Tipi numerici approssimati
	- Virgola mobile con mantissa ed esponente(`float(precisione)`,`real`,`double precision`)

#### Date
- istanti temporali
	- `Date`
	- `Time`
	- `Timestamp`
- Intervalli temporali

#### Domini presonalizzati
E' possibile creare domini personalzzati

```sql
create domain NomeDominio as TipoDato
[default ValoreDefault] [Vincoli]
```
I domini personalizzati sono comunque semplici (no array, no struct, no record).

### Definizione di tabelle
```sql
create table NomeTabella (
NomeAttributo1 Dominio1 [ValoreDefault1] [Vincoli1],
NomeAttributo2 Dominio2 [ValoreDefault2] [Vincoli2],
...
NomeAttributoN DominioN [ValoreDefaultN] [VincoliN],
[AltriVincoli]
);
```

### Valori di default
Per ogni attributo deve essere specificato un valore predefinito da usare in caso di valore non specificato.

Se non si specifica il valore di default viene usato Null.

### Vincoli
I vincoli servono a definire proprietà che devono
essere verificate da ogni istanza della base di dati
per garantirne l’integrità