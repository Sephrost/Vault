Anche se un problema é decidibile potrebbe non essere risolvibile in quanto impiegherebbe troppo tempo. Per questo é necessario introdurre il concetto di complessitá temporale.

## Definizione
Sia $M$ una **TM** non deterministica che termina su tutti gli input.
La **complessitá temporale**, o *running time*, di $M$ é quindi la funzione $f:N\to N$, dove $f(n)$ é il massimo numero di passi usati da $M$ su ogni input di linghezza $n$. 

Questa definizione usatilizza il concetto di **analisi nel caso peggiore**, imponendo quindi un limite asintotico a $f(n)$. 

Diciamo inoltre che $M$ termina in tempo $f(n)$, e che quindi é una TM di tempo $f(n)$.

### La notazione di O-grande
Dato che non é sempre possibile stimare con certezza il tempo di esecuzione di unálgoritmo, ricorriamo all'*analisi asintotica* per studiare il suo comportamento per input molto larghi.

La notazione **O-grande** ci permette quindi di descrivere la crescita di un'algoritmo per input finito, ignorando costanti moltiplicative e solo in funzione dell'ordine maggiore dell'espressione.

#### Definizione
Siano $f$ e $g$ funzioni $f,g:N\to R^+$.
Diciamo che $f(n)=O(g(n))$ se esistono due interi positivi $c$ e $n_0$ tali per cui $n\ge n_0$.

$f(n) \in O(g(n))$ significa che $f(n)$ **cresce**, a parte un fattore costante $c$ e trascurando un numero finito di valori (quelli $\le n_0$), al massimo come la funzione $g(n)$.

### La notazione o-piccola
Se O-grande impone un limite asintotico superiore , la funzione o-piccolo impone un limite asintotico **inferiore** alla crescita di una funzione.

#### Definizione
Siano $f$ e $g$ funzioni $f,g:N\to R^+$.
Diciamo che $f(n)=o(g(n))$ se $\lim\limits_{n\to \infty}\frac{f(n)}{g(n)}=0$ , quindi $f(n)$ diventa insignificante rispetto a $g(n)$ per valori infinitamente grandi.

Questa notazione é infatti poco utilizzata in quando un vincolo inferiore é solitamente poco significativo.


## Classi di complessitá temporale
Sia $t$ una funzione $t:N\to R^+$.
Definiamo come **classe di complessitá temporali** $TIME(t(n))$ l'insieme dei linguaggli decidibili da una TM $O(t(n))$.

### Complessitá temporale fra vari modelli
Esaminiamo come varia la complessitá temporale tra 3 modelli, una TM a singolo nasto, una TM multinastro e una TM multinastro non deterministica.

#### TM a nastro singolo vs TM multinastro
Sia $t(n)$ una funzione, con $t(n)\ge n$.
Ogni TM multinastro $M$ ha una TM a singolo nastro equivalente $S$ di tempo $O(t^2(n))$.
##### Dimostrazione
> Sappiamo che $S$ usa il suo singolo nastro per rappresentare i $k$ nastri di $M$.

Inizialmente $S$ copia il contenuto dei nastri di $M$ in un formato a lui leggibile, e poi prosegue con la simulazione di $M$.

Per ogni passo di $M$, $S$ deve fare due passaggi sulla porzione attiva del nastro: il primo per ottenere le informazioni necessarie a determinare il prossimo passo e il secondo per eseguirlo.
Inoltre per detrminare il costo di ogni passo é necessario sapere la lunghezza del nastro di $S$, che é uguale alla somma delle porzioni attive di tutti i $k$ nastri di $M$. 

Ogni porzione attiva dei nastri di $M$ ha lunghezza al massimo $t(n)$, in quanto in $t(n)$ mosse potrebbe usare t(n) celle se si muovesse sempre a destra. Di conseguenza una scansione del nastro attivo di $S$ ha costo $O(t(n))$, che é uguale al costo di ogni operazione di $S$.

Quindi per l'inizializzazione e l'esecuzione impiega $O(n)+t(n)\times O(t(n))=O(t^2(n))$ passi.

#### TM a singolo nastro non deterministiche vs TM a singolo nastro deterministiche
Sia $t(n)$ una funzione, con $t(n)\ge n$.
Ogni TM a singolo nastro non-deterministica $N$ ha una TM deterministica a singolo nastro $D$ di tempo $2^{O(t(n))}$.
##### Dimostrazione
Su un'imput di lunghezza $n$, ogni ramo di $N$ ha lunghezza $t(n)$ al massimo, e ogni nodo puó avere al massimo $b$, in quanto $b$ sono le scelte legali prodotte dalla funzione di transizione di $N$.

Quindi il numero **massimo** di foglie nell'albero prodotto da $N$ é $b^{t(n)}$.

La simulazione procede esplorando l'albero in ampiezza. Il numero massimo di nodi dell'albero é meno del doppio del numero massimo di foglie, ed é quindi $O(b^{t(n)})$.  
Inoltre il tempo impiegato per attraversare l'albero fino ad un nodo arbitrario é $O(t(n))$, quindi il tempo di esecuzione di $D$ é $O(t(n)b^{t(n)})=2^{O(t(n))}$. 

$D$ in questo momento ha 3 nastri, ma é possibile convertirlo in uno equivalente facendo quadrare il tempo di esecuzione, che mantiene la complessitá identica.