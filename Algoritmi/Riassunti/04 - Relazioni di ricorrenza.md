## Relazioni di ricorrenza
Nel caso di chiamate ricorsive, il tempo di esecuzione puo' essere descritto come uan ricorrenza.

Una **ricorrenza** è un’equazione o disequazione che descrive una funzione in termini del suo valore con input più piccoli.

###### Esempio 
il tempo di esecuzione T (n) nel caso peggiore della procedura *merge-sort* può essere descritto dalla ricorrenza

$$T(n)=\{^{Θ(1)\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;se\,n=1}_{2T(n/2)+Θ(n)\,se \;\;n>1}$$
%%Fixare parentesi graffa,deve essere gigante%%
la cui soluzione e' $T(n)=Θ(n\log n)$

Possiamo distinguere quindi due casi di chiamate ricorsive 
- se la chiamata ricorsiva diminuisce la dimensione dell'input di una dimensione costante si ottiene una una **relazione di ricorrenza a partizione costante**
- sel la chiamata ricorsiva diminuisce la dimensione dell'input di un certo fattore si ottiene una **relazione di ricorrenza a partizione bilanciata**

### Metodo dell'iterazione
Per poter trovare una soluzione ad una relazione di ricorrenza si puo' sviluppare la ricorrenza fino ad intuirne la soluzione 

###### Esempio
$$T(n)=\{^{c}_{}$$