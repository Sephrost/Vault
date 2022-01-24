### Schemi di Traduzione
Uno **schema di traduzione** (o **SDT**, da Syntax-Directed Translation scheme) è una **grammatica** in cui le **produzioni** sono **arricchite** da frammenti di **codice** detti **azioni semantiche** che sono eseguite quando tutti i simboli alla loro sinistra sono stati riconosciuti.

###### Esempi
Produzione|Produzione+Azioni|Descrizione
--|--|--
$A\to BC$|$A\to BC\{code\}$|Il codice viene seguito dopo il riconoscimento di $BC$
$A\to BC$|$A\to B\{code\}C$|Il codive viene seguito dopo il riconoscimento di $B$ ma prima di quello di $C$
$A\to BC$|$A\to \{code_1\}BC\{code_2\}$|Il primo codice viene eseguito dopo la riscrittura di $A$, mentre il secondo dopo il riconoscimento di $BC$
$A\to \epsilon$|$a\to \{code\}$|Il codice viene eseguito dopo la riscrittura di $A$

#### Differenze tra regole e azioni semantiche

Regole semantiche(SDD)|Azioni semantiche(SDT)
--|--
Specificano come ottenere il valore degli attributi|Specificanono come ottenere il valore degli attributi, ma  possono contenere anche codice arbitrario
Sono valutate seguendo il grafo delle dipendenze, in ordine implicito|Sono eseguite in ordine esplicito, in base alla loro posizione nel corpo della produzione
Richiedono la costruzione di un'albero annotato, poiché valutate in ordine arbitrario|Possono essere integrato ad un parser ricorsivo discendente, poiché eseguite da destra verso sinistra 

#### Conversione da SDD L-attribuita a SDT

Data una SDD L-attribuita, si può ottenere uno SDT corrispondente nel modo seguente.

Per ogni produzione $A\to X_1X_2..X_n$ della grammatica:

- Subito prima di $X_i$, con $i>1$ si **aggiunge** un'**azione** semantica che calcola il valore degli attributi **ereditati** di $X_i$
- In **fondo** alla produzione (dopo $X_n$), aggiungo un'azione semantica che calcola il valore di **tutti** gli attributi **sintetizzati** da $A$

#### Parser ricorsivo discendente di una SDT

Per integrare una SDT in un parser ricorsivo discendente, questo deve avere una procedura per ogni variabile che riconosce le stringhe generate dalla stessa.

La procedura ha tanti argomenti quanti sono gli attributi ereditati e restituisce tanti valori quanti sono gli attributi sintetizzati.

Per ogni simbolo o azione semantica $X$ nel corpo della produzione scelta:

- Se $X$ é un **simbolo terminale**, il metodo **controlla** che sia proprio $X$, per poi far **avanzare** il **lexer** se é vero.
- Se $X$ é una **variabile**, viene invocata la **procedura** $X$, passando i suoi attributi **ereditati** come **argomenti** e raccogliendo in **variabili** locali gli attributi **sintetizzati** restituiti dalla procedura.
- Se $X$ é un'**azione semantica**, il metodo la **esegue**.

###### Esempio

![[Pasted image 20220112165148.png]]

```java
private int S() {
	switch (peek()) {
		case 'a': { // S → aSb 
			check('a'); 
			int S_n = S(); 
			check('b'); 
			return S_n + 1; } 
		case 'b': // S → ε 
		case '$': 
			return 0; 
		default: 
			throw error("S");
	} 
}
```

#### Traduzione "on-the-fly"
Un attributo sintetizzato si dice principale se:
1. Il suo valore **include una concatenzazione ** dei valori dello stesso attributo, cioe' il corpo delle variabili di ogni produzione 
2. La concatenazione rispetta sempre l'ordine di comparsa delle variabili nel corpo della produzione 

$E\to E_1+T\{E.post=E_1.post||T.post||"T"\}$

Gli attributi principali possono essere eliminati “emettendo al volo” solo gli elementi ausiliari nel punto in cui devono comparire.