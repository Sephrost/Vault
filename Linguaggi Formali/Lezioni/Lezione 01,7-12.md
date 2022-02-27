### Esercizi
#### Esercizio 1
Calcolare il codice generato per l' espressione $x\times x+2\times x+1$
![[2021-12-01--1638354907_195x306_scrot.png]]
```java
ILOAD x
ILOAD x
IMUL 
LDC 2
ILOAD x
IMUL
IADD
LDC 1
IADD
```
#### Esercizio 2,3
Scrivere le regole semantiche per tradurre la negazione $E\to -E_1$,l'accesso all'array $E\to E_1[E_2]$,$E\to x=E_1$,$E\to x++$

###### Negazione 
$\{E.code=E_1.code||ineg\}$, oppure
$\{E.code=ldc 0||E_1.code||isub\}$,oppure
$\{emit("ineg")\}$
###### Accesso all'array
$\{E.code=E_1.code||E_1.code||iaload\}$
###### Assegnamento
$\{E.code=E_1.code||dup||istore-x\}$
###### Post incremento
$\{E.code=iload-x||dup||ldc-1||iadd|istore-x\}$

	