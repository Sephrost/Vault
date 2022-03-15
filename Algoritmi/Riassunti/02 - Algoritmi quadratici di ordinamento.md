## Algoritmi quadratici di ordinamento
La ricerca in un vettore di $n$ elementi richiede $n$ confronti nel caso peggiore, mentre se un vettore é ordinato é possibile usare algortimi come la ricerca dicotomica per impiegare meno tempo.
### Insert Sort
É un algoritmo efficiente per ordinare un piccolo numero di elementi.

Questo algoritmo opera nello stesso modo in cui molte persone ordinano le carte da gioco.

I numeri da ordinare sono anche detti **chiavi**.

L'algoritmo prende come parametro un array $A[1 ..n]$ contenente una sequenza di lunghezza $n$ che deve essere ordinata 

###### Pseudocodice
```c
INSERTION-SORT(A) 
1 for j ← 2 to lunghezza[A] do 
2 		chiave ← A[j] 
3 		✄ Inserisce A[j] nella sequenza ordinata A[1 ..j − 1]. 
4 		i ← j − 1 
5 		while i > 0 and A[i] > chiave do 
6 			A[i + 1] ← A[i] 
7 			i ← i − 1 
8 		A[i + 1] ← chiave
```