### Esercizi
Lista delle differenze 

L'unico elemento ereditato e' $L.e$

$S\to n\{L.e=n.v\}\{S.v=L.s\}$
$L\to \epsilon\{L.s=[]\}$
$L\to ;n\{L_1.e=L.e\}L_1\{L.s=n.v-L.e||L_1.s\}$
```java
//procedura L
static List<int> L(int e){
	switch(peek()){
		case '$': //L -> epsilon
			return [];// ritorno una lista vuota
		case ';': 
			match(';');
			int v = peek()-'0';
			match(peek());
			int s=L(e);
			return v-e||s;
		default:
			trown exception();
	}
}
```
### Traduzione on the fly
Un attributo sintetizzato si dice principale se:
1. Il suo valore **include una concatenzazione ** dei valori dello stesso attributo, cioe' il corpo delle variabili di ogni produzione 
2. La concatenazione rispetta sempre l'ordine di comparsa delle variabili nel corpo della produzione 

$E\to E_1+T\{E.post=E_1.post||T.post||"T"\}$

Si possono eliminare gi attributi post poiche' sono di interesse sono gli operatori 