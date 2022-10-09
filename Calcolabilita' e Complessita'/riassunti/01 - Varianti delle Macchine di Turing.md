## Macchina di Turing multi-registro
Una **macchina di Turing multi-registro** e' una macchina di Turing con diversi nastri, ognuno dei quali ha una propria testina, e puo' essere letto e scritto.

### Funzione di Transizione
La funzione di transizione diventa la seguente
$$δ: Q\times Γ^k\to Q\times Γ^k\times\{L,R,S\}^k$$
dove $k$ é il numero di nastri.

### Equivalenza con le Macchine di Turing a nastro singolo
É possibile dimostrare che una macchina a piu' registri ne ha una a singolo equivalente.

> Due macchine sono equivalenti se riconoscono lo stesso linguaggio

Per convertire una TM $M$ multinastro ad una a nastro singolo $S$ é sufficiente partizionare il nastro in $k$(il numero di nastri di $M$) partizioni separate dal delimitatore **#**,  

![[Pasted image 20220921101942.png]]

Immaginando che il dato di partenza sia una sringa $w=w_1\dots w_s$ partizioniamo il nastro usando i simbolo # come separatore.

Avremo quindi una posizione iniziale del tipo

![[Pasted image 20220921102125.png]]

> Gli asterischi indicano il valore attuale del segmento di nastro(memoria)

> Le macchine a singolo nastro sono molte piu' lente poiche per accedere alle diverse aree di memoria dovremo spostare l'intero nastro, questo pero' non intocca la decidibilita' della macchina.

## Macchine di Turing non deterministiche

Una **Macchina di Turing non deterministica** é una TM che, in ogni momento della computazione, puó decidere tra diverse possibilitá.

### Funzione di Transizione
La funzione di transizione diventa la seguente
$$\delta:Q\times\Gamma\to P(Q\times\Gamma\times\{L,R\})$$
dove $P$ rappresenta l'insieme di stati producibili da una data configurazione.

### Computazione di una ndTM
La computazione di una macchina di Turing non deterministica é un'**albero**, con i rami che rappresentano le diverse possibilitá prodotte dalla macchina.

Se un ramo porta allo stato di accettazione, la macchina accetta l'input.

### Equivalenza con le Macchine di Turing deterministiche

## Enumeratori
sono un modo di classificare i problemi.

Un'enumeratore e' una macchina di Turing a singolo nastro collegata ad una stampante(che rappresentai il secondo nastro) che puo' usare per stampare delle stringhe.

![[Pasted image 20220928090856.png]]

Essa restituisce un flusso infinito di dati.

L'enumerator stampa tutte le stringhe con radice intera. Puo' inoltre generare ripetizioni, e le stringhe possono essere generate in qualunque ordine.

