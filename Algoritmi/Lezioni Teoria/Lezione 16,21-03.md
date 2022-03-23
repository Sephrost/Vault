### Relazioni di ricorrenza 
> Il costo di tempo di una chiamata ricorsiva e' la funzione stesso che sto definendo

%%Aggiungere immagine%%

$$T(n)=\{^{c_1+c_2if(n<2)}_{T(n-1)+c_3if(n\ge 2)}$$

#### Forma generale della forma di ricorrenza
%%Dicono che sul libro e' fatto bene%%
1. Srotolo la funzione x volte, quelle necessarie per potersi ricavare la generica formula
2. Ricavo la formula generale
###### Esempio
Sapendo che 
$T(n)=T(n-1)+d$ con $d$ costante
allora
$T(n)=T(n-k)+kd$ dove $k\le n$
dove $k$ e' il contatore delle volte che ho applicato la legge.

Questa funzione non e' quindi definita quindi per valori negativi, in modo da evitare ricorsioni infinite.

Nel caso in cui $k=n$ avro'
$T(n)=T(0)+nd\in O(n)$ se $T(0)\in O(1)$
permettendo di applicare l'algebra di O, di conseguenza possiamo ignorare la costante $d$.

###### Teorema
Se $c>0,\beta \ge 0,a=\sum_{1\le i\le h}a_i$ allora$\{^{T(n)\in O(n^\beta +1)}_{T(n)\in O(a^n n^\beta)}$



