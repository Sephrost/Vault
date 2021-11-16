#### Esercizio
$S\to if$ $E$ $then$ $SS'fi|skip$
$S'\to elseS |\epsilon$
$E\to true|false$
$S$,$S'$ed $E$ sono variabili e $if,then..$ sono simboli terminali.

$Null(S')$
$FIRST(S)=\{if,skip\}$
$FIRST(S')=\{else\}$
$FIRST(E)=\{true,false\}$
$\$\in Follow(S)$
$then\in Follow(E)$
$else,fi\in Follow(S)$
$fi\in Follow(S')$
$Follow(S')\subseteq Follow(S)$

Var|Follow
--|--
S|$\$,else,fi$
S'|$fi$
E|$then$

$GUIDA(S\to if$ $E$ $then$ $SS'fi|skip)=\{if,skip\}$
$GUIDA(S'\to elseS |\epsilon)=\{else\}$
$GUIDA(E\to true|false)=\{true,false\}$

#### Esercizio

Il simbolo inizale e' $D$
$A\to \epsilon |AdC$
$B\to DA$
$C\to B$
$D\to Eb$
$E\to aA$

Calcoliamo first e follow di ogni variabile 

#### Esercizio

Il simbolo iniziale e' C
$B\to \epsilon|EaE$
$C\to BD$
$D\to acd$
$E\to \epsilon$

#### Esercizio

Il simbolo iniziale e' D
$A\to Ab|\epsilon$
$C\to Eab$
$D\to C|\epsilon$
$E\to Aa$

#### Esercizio
LA gramamtica delle stringhe della forma $a^nb^nc^m$
- $S\to XC$
- $X\to \epsilon|aXb$
- $C\to \epsilon|cC$

$Null(S),Null(X),Null(c)$
$First(C)=\{c\}$
$First(S)=\{a,c\}$
$First(X)=\{a\}$

$\$\in Follow(S)$
$c\in Follow(X)$
$Follow(S)\subseteq Follow(X)$
$Follow(S)\subseteq Follow(C)$
$b\in Follow(X)$

Var|Follow
--|--
S|$\$$
X|$\$,b,c$
C|$\$$

$Guida(S\to XC)=\{a,c,\$\}$
$Guida(X\to \epsilon)=\{\$,b,c\}$
$Guida(X\to aXb)=\{a\}$
$Guida(c\to \epsilon)=\{\$\}$
$Guida(C\to \epsilon)=\{c\}$

```java
procedura S(){
	switch(peek()){
		case 'a':
		
		case 'c':
		
		case '$': //S->XC
			X();
			C();
			break;
		default:
			eccezione(errore sintattico);
		
	}
}
```

```java
procedura X(){
	switch(peek()){
		case '$','c','b':
			break;
		case 'a':
			match('a');
			X();
			match
	}
}
```

## Grammatiche fattorizzabili e ricorsive a sinistra
Molte gramamtiche utili per descrivere linguaggi di programmazione non sono LL(1).

I problemi sono:
### Fattorizzazione
Produzione dove nel corpo individuiamo un prefisso comune a 2 produzioni

$A \to \alpha \beta_1|\alpha \beta_2$

dove 

$Guida(A\to\alpha \beta_1)\cap Guida(A\to \alpha \beta_2)\ne 0$


Possiamo quindi fattorizzare il prefisso in comune $\alpha$ introducendo una nuova variabile $A'$:

$A\to \alpha A'$ e $A'\to \beta_1|\beta_2$

a patto che,cosi' facendo, le produzioni degli insiemi guida siano disgiunti

### Ricorsione immediata a sinistra

La variabile in testa di una produzione e' anche il primo di una produzione.

Per esempio una grammatica con le produzioni

$A\to A\alpha|\beta$

e' detta immediatamente ricorsiva a sinistra in quanto la produzione $A\to A\alpha$ ha $A$ come primo simbolo del corpo.

Possiamo risolvere il problema introducendo una variable per spostare la ricorsione da sinistra a destra:

$A\to \beta A'$ e $A'\to \epsilon|\alpha A'$