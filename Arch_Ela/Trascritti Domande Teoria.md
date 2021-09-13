#### Qual'é la massima ampiezza di un salto condizionato in ijvm, e da  cosa é determinata?
Essendo un operando composto da 2 byte, lo spiazzamento che possiamo rappresentare é limitato dalla sua rappresenzazione in complemento a 2 con 16 bit $[2^{16-1};2^{16-1}-1)$

#### Se dovessi implementare una nuova istruzione IJVM con codice operativo x(dove x indica il valore numerico dell'opcode), quali sono i valori di x che potreste utilizzare?

Per scegliere un nuovo codice operativo dobbiamo:

- Scegliere un codice operativo che non sia strato giá utilizzato per le istruzioni precedentemente implementate e compreso tra 0 e 255
- Un codice operativo che non corrisponda ad una parola utilizzata da un pezzo di microprogramma di un'altra istruzione isa

####  Si descriva in generale il concetto di località spaziale e temporale

Con localitá spaziale si intente il concetto secondo il quale ,in un programma, dopo aver effettuato l'accesso ad una locazione di memoria, tenderá ad accedere a locazioni di memoria contigue, di conseguenza in presenza di una memoria cache quando si memoriazza una parola al suo interno, vengono caricate anche quelle a lei vicine nella memoria principale
Con locaitá temporale si intende invece il concetto secondo il quale si tende ad accedere a locazioni di memoria utilizzate di recente, di conseguenza in presenza di una memoria cache, queste verrebbero caricate su di essa per consentire un accesso piú veloce
![[Pasted image 20210711162019.png]]
- Primo caso: l'accesso in memoria avviene in locazioni contigue, ripetiamo piú volte l'accesso alla variabile i

#### Si descriva il meccanismo di passaggio dei parametri ad una procedura IJVM chiamata con  INVOKEVIRTUAL, e il meccanismo con cui una procedura rende il valore di ritorno al programma  chiamante n
Per permettere il passaggio dei parametri durante INVOKEVIRTUAL é necessario caricare sullo stack l'oggetto di riferimento,seguito dai parametri che si intende passare. Per quanto riguarda invece il valore da ritornare é necessario lasciare il valore in cima allo stack ed eseguire IRETURN
#### Quali registri vengono salvati sullo stack durante l'esecuzione di invokevirtual?
LV del chiamante e il PC del chiamante, poiché saranno quelli che andremo ad alterare durante l'esecuzione del metodo
#### Si descriva il modello di memoria di IJVM e il ruolo dei registri Mic-1 utilizzati per indicare la base di alcune aree di memoria 
La memoria dell'IJVM é divisa in :
- L'area delle costanti ,caricata dalla memoria quando il programma viene eseguito e che rimane invariata per tutta l'esecuzione. 
- Lo stack di esecuzione, dove allocare le variabili locali dopo la chiamata di un metodo. 
- Lo stack degli operandi, allocato subito sopra il blocco delle variabili locali.
- L'area dei metodi, dove risiede il codice
La JVM non rende disponibili esplicitamente gli indirizzi assoluti di memoria delle variabili,rendendo quindi necessario l'uso dei puntatori, implementati nel mic-1 attraverso dei registri

#### Qual é il massimo numero di variabili locali di una procedura IJVM, e perché?
Essendo la memoria della IJVM composta da 4GB, é possibile allocare fino a $\frac{4*2^{32}}{4}$ variabili locali, poiché ogni parola é composta da 4 byte