# Introduzione
Inizialmento gli elaboratori venivano programmati fornendo delle istruzioni in codice macchina, che il processore poteva eseguire direttamente, ma scrivere istruzioni risultava difficile.

Naque quindi la necessita' di usare dei linguaggi di programmazione per scrivere programmi a livello piu' alto. 

Il compilatore si pone quindi tra il linguaggio umano a quello macchina, traducendo il programma scritto dall' utente e riscriverlo in un programma equivalente a linguaggio macchina.

## Fasi di un compilatore
- Analisi Lessicale 
- Analisi Sintatica 
- Generazione del codice intermedio

## Alfabeto 
Un alfabeto e' un'inseme finito e non vuoto di simboli:

- Utlizziamo $\sum$ per indicare l'alfabeto generico 
- utilizziamo $a,b,c..$  per indicare generici simboli

## Stringhe
Una **stringa** su un alfabeto $\sum$ e' una sequenza **finita** di simboli in $\sum$
- Usiamo $u,v,w...$ per indicare stringhe generice
- Usiamo $\epsilon$ per indicare una **stringa vuota**  composta da *0 simboli*
### Operazioni su stringhe 
La **lunghezza** di una stringa $u$ e' il numero di simboli di cui e' costituita e si indica con $|u|$ .

La **concatenazione** di $u$ e $v$ e' indicata con $uv$, attacando la sequenza di $u$ dopo la sequenza di $v$. 

- La concatenazione é **neutra** rispetto alla **stringa vuota** ($u\epsilon=u$), **associtativa** ($u(vw)=(uv)w$), ma **non commutativa** ($uv\ne vu$)

La **lunghezza** della concatenzione sara' uguale alla somma della lunghezza delle sue stringhe.

Un **suffiso** di una stringa se la concatenazione di essa con un'altra stringa e' uguale ad un'altra.

L'**inverso** ($w^{R}$) di una stringa $w$ e' una stringa che constiene gli stessi suffissi ma in ordine inverso($w=a_1,a_2,..,a_n$ e $w^R=a_n,..,a_2,a_1$).

Una stringa e' **palindroma** se una stringa e' uguale al suo inverso ($w=w^{R}$)

La **potenza** di una stringa ($u^{n}$)e' la stringa che otteniamo concatenando la stessa $n$ volte.

## Linguaggio
Un linguaggio $L$ e' un'alfabeto $\sum$ di un qualunque insieme di stringhe su $\sum$

- Usiamo $\sum^{*}$ per indicare l'insieme di tutte le stringhe su $\sum$, inclusa quella vuota ($\epsilon$)
- Usiamo $\sum^{+}$ per indicare tutte le stringhe non vuote su $\sum$

 
$L=0$ e' un linguaggio vuoto, che non contiene la stringa vuota $\epsilon$

### Operazioni sui linguaggio

|Operazione|Definizione|
---|---
Unione|$L_1\cup L_2$
Intersezione|$L_1\cap L_2$
Complemento(not)|$L=\sum^{*}-L$
Concatenzazione|$L_1L_2=\{uv\| u\in L_1,v\in L_2\}$
Potenza|$L^0=\{\epsilon\}$ e $L^{n+1}=LL^n$
Chiusura di Kleene(Arbitrarie)|$L^*=L^0\cup L^1\cup L^2 \cup ...$ 
Chiusura transitiva(non la stringa vuota)|$L^+=L^1\cup L^2 \cup ...$