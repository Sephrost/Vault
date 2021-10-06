# Espressioni regolari 
Rispetto ad un alfabeto $\sum$ di riferimento, le espressioni regolari sono definite come segue:
- $0$ r $\epsilon$ nono espressioni regolari 
- se $a \in \sum$, allora $a$ e' un'espressione regolare
- se E ed F sono espressioni regolari, E+F ed EF sono espressioni regolari 
- se $E$ e' un'espressione regolare, **$E^{*}$** e' un'espresione regolare

## Convenzioni
- Per quanto riguarda la priorita', si una come convenzione la seguente priorita': + < concat < *
- Usiamo le parentesi per rendere disambigua la struttura

Forma|Significato
-|-
$L(0)=0$|Linguaggio vuoto
$L(\epsilon)=${$\epsilon$}|{$\epsilon$}
$L(a)=${$a$}|Simbolo dell'afabeto
$L(E+F)=L(E)\cup L(F)$|unione
$L(EF)=L(E)L(F)$|concatenazione
$L(E^{*})=L(E)^{*}$|chiusura di Kleene

Diciamo che $E$ ed $F$ sono equivalenti se $L(E)=L(F)$

### Esempio 
Il linguaggio generato da $(a+b)^{*}$ e' 
$L(a+b)^{*}$
$(L(a)\cup L(b))^{*}$
$(${$a$}$\cup${$b$}$)^{*}$
{$a,b$}$^{*}$
{$\epsilon,a,b,aa,bb,ab,ba,...$}

Il linguaggio generato da $(ab)^{*}$
$(L(a)L(b))^{*}$
({$a$}{$b$})$^{*}$
{$ab$}$^{*}$
{$\epsilon,ab,abab,abababa,...$}

## Proprieta' 
### Unione
Proprieta'|Esempio
-|-
Commutativita'|$E+F=F+E$
Associativita'|$E+(F+G)=(E+F)+G$
Idempotenza|$E+E=E$
Identita'|$E+0=0+E=E$
### Concatenazione
Proprieta'|Esempio
-|-
Associativita'|$E(FG)=(EF)G$
Identita'|$E\epsilon=\epsilon E=E$
Assorbimento|$E0=0E=0$
Distributivita' sinistra|$E(F+G)=EF+EG$
Distributivita' destra|$(E+F)G=EG+FG$
### chiusura di Klenee
Proprieta'|Esempio
-|-
Idempotenza|$(E^{*})^{*}=E^{*}$
Casi banali|$\epsilon=0^{*}=\epsilon$

## Espressione regolare -> $\epsilon-NFA$
Data un'espressione regolare $E$, esiste un $\epsilon$-NFA $A$ tale che $L(A)=L(E)$, con esattamente uno stato finale.
### Caso 0(Linguaggio vuoto)
In questo caso lo stato finale e quello inizale non sono cllegati in alcun modo

![[2021-10-06--1633512145_199x67_scrot.png]]
### Caso $\epsilon$(Solo stringa vuota)
L'unisca transizione e' rappresentata dalla sola stringa vuota

![[2021-10-06--1633512590_185x64_scrot.png]]
### Caso a(Linguaggio che contiene solo a)
L'unica transizione e' rappresentata dalla sola stringa "a".

![[2021-10-06--1633512759_171x60_scrot.png]]
### Caso unione 
In questo casi si analizzano gli automi singolarmente, per poi ottenere un automa che riconosce il linguaggio generato dall'unione dei linguaggi.

![[2021-10-06--1633512920_376x175_scrot.png]]
### Caso concatenzione
Si analizzano gli automi singolarmente, per ottenere un automa che parte dallo stato inizale del primo automa per arrivare allo stato finale del secondo automa, riconoscendo tutte le concatenazioni possibili.

![[2021-10-06--1633513037_411x112_scrot.png]]
### Chiusura di Kleene
![[2021-10-06--1633513055_387x126_scrot.png]]

## Esempi
- stringhe di a, b e c che iniziano con due a e finiscono con due b
	$aa(a+b+c)^{*}bb$
- stringhe di 0 e 1 la cui lunghezza è un multiplo di 3
	$((0+1)(0+1)(0+1))^{*}$
- stringhe di 0 e 1 con un numero pari di 0
	$(1^{*}01^{*}0)^{*}1^{*}$
- stringhe di a, b e c che non contengono la sottostringa ab
- costanti numeriche binarie pari senza 0 inutili a sinistra (es. 0, 10, ma non 010 o 11)
- costanti numeriche decimali con virgola facoltativa (es. 42, .5, 12.3, 12. ma non .)
## Chiusura dei linguaggi regolari
### Unione e concatenazione
Dati due linguaggi regolari $L_{1}$ e $L_{2}$, essi ono chiusi rispetto all'unione e alla concatenzazione.

### Complemento
Dato un linguaggio regolare $L$, esso e' chiuso rispetto al complento poiche $\overline{L}=L(B)$.
### Intersezione
Dati due linguaggi regolari $L_{1}$ e $L_{2}$, $L_{1}\cap L_{2}$ e' un linguaggio regolare, poiche' per le leggi di de morgan: $L_{1}\cap L_{2}=\overline{\overline{L_{1}\cap L_{2}}}=\overline{\overline{L_{1}}\cup\overline{L_{2}}}$.
### Differenza
Dati due linguaggi regolari $L_{1}$ e $L_{2}$,  sono chiusi per la differenza poiche' $L_{1}-L_{2}=L_{1}\cup\overline{L_{2}}$ e questi sono chiusi per intersezione e complemento.
### Inversione
I linguaggi regolari sono chiusi per inversione.
