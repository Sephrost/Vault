### Parsing ricorsivo discendente
Per realizzare un parse basato sulla **ricorsione** usiamo la pila del linguaggio di programmazione per **ricordare** il **suffisso** della forma sentenziale sinistra da riconoscere.

#### Elementi chiave
- Il parser ha una **procedura**(metodo) per ogni **variabile** della grammatica
- La procedura $A$ nel parser riconsoce le stringhe generate da $A$ nella grammatica
- La procedura $A$ usa il **simbolo** corrente e gli **insiemi guida** per scegliere la produzione da usare per riscrivere $A$
- Per ogni **simbolo** $X$ trovato nel corpo della produzione:
	- Se è un simbolo **terminale**, il metodo **controlla** che il simbolo corrente sia proprio $X$ e fa **avanzare** il **lexer** al simbolo successivo. In caso contrario, il metodo segnala un errore di sintassi.
	- Se é una **variabile**, il metodo invoca la **procedura** $X$


##### Esempio: Parser per il linguaggio $A^nB^n$
###### Grammatica
$S\to aSb|\epsilon$
###### Insiemi guida
$Guida(A\to aSb)=\{a\}$
$Guida(A\to \epsilon)=\{b,\$\}$
###### Codice del parser
```java
public class AnBn extends Parser { 
	protected void S() { 
		switch (peek()) { 
			case 'a': // S → aSb 
				match('a'); 
				S(); 
				match('b'); 
				break; 
			case 'b': // S → ε 
			case '$': 
				break; 
			default: throw error(); } 
	} 
}
```

