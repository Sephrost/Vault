## Linguaggi non regolari
Data una proprieta' **$P$** soddisfatta da un linguaggio regolare, allora un **Linguaggio non Regolare** e' un linguaggio che **non soddisfa** $P$, detta **pumpling lemma**.

Esistono linguaggi non regolari per il quale vale il pumpling lemma.
### Pumpling lemma per i linguaggi regolari
Per ogni linguaggio regolare $L$, esiste un numero naturale $n$ per cui $|w|\ge n$ con $w\in L$,ed esistono $x, y$ e $z$ t.c $w=xyz$ con queste caratteristiche:
- $y$ non puo' essere la stringa vuota ($y\ne \epsilon$)
- La lunghezza del segmento $xy$ ha una lunghezza non superiore ad $n$ ($|xy|\le n$)
- Tutte le stringhe della forma $xy^{k}z$ appartengono al linguaggio $L$, per qualunque $k\ge0$

Quindi se prendiamo un linguaggio regolare, prese delle stinghe sufficientementemente lunghe di questo linguaggio, sono sempre in grado di individuare una parte "centrale" replicabile con regolaritá, generando stringhe sempre appartenenti al linguaggio.

##### Esempio di dimostrazione
Il linguaggio $L=${$a^{k}b^{k}|k\geq0$}(k $a$ seguite da k $b$) non e' regolare.

Considero una stringa $w=a^nb^n$ appartenente al linguaggio $L$ con $|w|=2n\ge n$,allora devono esistere $x$,$y$ e $z$ tali che $w=xyz$ e che soddisfano le 3 proprietá del pumpling lemma.

Sappiamo che:
- Per la prima proprietá $y$ non deve essere nulla, quindi conterrá almeno una $a$,o una $b$
- Per la seconda proprietá $xy$ conterrá solo a, poiché se contenesse anche delle b allora supererebbe $n$
- Per la terza condizione $xz\in L$

Dovendo esserci lo stesso numero di $a$ e $b$, allora la proprietá non é verificata poiché ci possono essere arbitrarie $a$ dovute ad $y^k$.