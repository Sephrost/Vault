### Indecidibilitá
Ci sono alcune categorie di problemi irrisolvibili da un computer, per esempio verifica di un software.

Il primo problema che andiamo ad osservare é il problema dell'accettazione per le *TM*.

#### Accettazione per le *TM* (versione veloce)
Sia 
$$A_{TM}=\{<M,w>|\,M\;é\;una\;TM\;che\;accetta\;w\}$$
Dimostriamo che $A_{TM}$ é indecidibile.

Osserviamo che il problema é **decidibile positivamente**, ma perché un problema sia decidibile deve terminare su tutti gli input. 
Costruiamo quindi la *TM* $U$, che riconosce $A_{TM}$
$U$ = Dati in input $<M,w>$, dove $M$ é una *TM* e $w$ é una stringa
1. Simuliamo $M$ con input $w$
2. Se $M$ entra in uno stato di accettazione, $accetta$, se $M$ non entra in uno stato di rifiuto, $rifiuta$

$U$ peró entra in loop su input $<M,w>$ se $M$ entra in loop su $w$.
Proprio per questo motivo $U$ **non decide** $A_{TM}$.

> Se l'algoritmo potesse individuare se $M$ non termina su $w$, allora potrebbe entrare in stato di rifiuto peró questo non é possibile per un algoritmo.

#### Metodo della diagonalizzazione
> E' usato per controllare se due insiemi contengono lo stesso numero di elementi

Assumiamo che esistano due insiemi $A$ e $B$ e una funzione $f$, che assegna un valore di $A$ ad uno e un solo valore di $B$. Diciamo quindi che $f$ e' una funzione di **corrispondenza**.

> In una corrispondenza ad ogni valore di $A$ corrisponde ad un unico valore di $B$, e per ogni valore di $B$ esiste solo un valore di $A$ a cui corrisponde.

Introduciamo inoltre il concetto di insiemi numerabili e piu' che numerabili.

> Un'insieme e' numerabile se e' finito o ha al piu' grande come $N$

> Un'insieme e' piu' che numerabile se non e' infinito o comunque piu' grande di $N$ (es:$R$)

##### Esempio di metodo della diagonalizzazione
Dimostraimo che l'insieme $Q=\{\frac{m}{n}|m,n\in N\}$ e $N$ sono entrambi numerabili.

Per dimostrarlo basta mostrare che esiste una corrispondenza tra i loro elementi.

Un modo semplice per farlo e' elencare tutti gli elementi di $Q$ e accoppiare ad ognuno di essi un elemento di $N$, assicurandoci che ogni elemento di $Q$ appaia una sola volta nella lista.

Costruiamo quindi una *matrice infinita* contenente tutti i numeri razionali, dove la $i$-esima riga contiene solo elementi con numeratore $i$ e la colonna $j$-esima contiene solo elementi con denominatore $j$ .

> Il numero $\frac{i}{j}$ comparira' quindi una sola volta nella posizione $matr[i][j]$

Ora dobbiamo traformare la matrice in una lista, le righe e le colonne sono infinite, quindi elenchiamo tutti gli elementi sulle diagonali, iniziando dall'angolo.

Usando questa tecnica e' possibile pero' ottenere ripetizioni nella corrispondenza, quindi ignoriamo semplicemente l'elemento che casuserebbe la ripetizione, come in foto

![[Pasted image 20221108150626.png]]
###### Corollario
Poiche' non tutti i linguaggi sono numerabili, esistono linguaggi che non sono ne' decidibili ne' decidibili positivamente, poiche' i linguaggi sono piu' che numeraili mentre le *TM* sono numerabili.

> Ci sono piu' linguaggi che *TM*, quindi alcuni linguaggi non sono riconosciuti da alcuna *TM*

#### Dimostrazione dell'indecidiblita' dell'accettazione
Sia di nuovo
$$A_{TM}=\{<M,w>|\,M\;é\;una\;TM\;che\;accetta\;w\}$$

Assumiamo per assurdo che $A_{TM}$ sia decidibile.
Supponiamo che $H$ sia un decisore per $A_{TM}$, su input $<M,w>$, dove $M$ e' una *TM* e $w$ e' una stringa, allora

$$H\{<M,w>\}=\Big\{^{accetta\,se \;M\;accetta\,w}_{rifiuta\,se\;M\;non\;accetta\;w}$$
Costruiamo quindi una *TM* $D$ con $H$ come subroutine, $D$ chiama quindi $H$ per determinare cosa fa $M$ quando gli fornisci la sua stessa descrizione $<M>$, ma fa l'opposto, quindi 
$$D\{<M>\}=\Big\{^{accetta\,se\;M\;non\;accetta\;<M>}_{rifiuta\,se\;M\;accetta\;<M>}$$
ora proviamo a passare $D$ a se stessa, otteniamo quindi
$$D\{<D>\}=\Big\{^{accetta\,se\;D\;non\;accetta\;<D>}_{rifiuta\,se\;D\;accetta\;<D>}$$
ma quetsa e' una contraddizione, quindi ne' $H$ ne $D$ possono esistere in quanto $H$ non e' un decisore.

#### Dimostrazione dell'indecidibilita' dell'accettazione attaverso la diagonalizzazione

Riprendiamo la definizioni di $A_{TM}$,$H$ e $D$ di prima.

Costuiamo quindi una tabella che ha come righe le *MT*, e le loro descrizioni sulle colonne ponendo nella entry $Matr[M_x][<M_x>]$ se $M_x$ accetta o rifiuta $<M_x>$.

![[Pasted image 20221109112101.png]]

Poiche' $H$ e' una *TM*, e quindi lo e' anche $D$, questa deve essere presente nella lista di tutte le *TM*. 

![[Pasted image 20221109142326.png]]

Notiamo pero' che nella entry $Matr[D][<D>]$ si presenta una contradfdizione, poiche' D dovrebbe accettare $<D>$ (e quindi presentare il risultato opposto come da definizione), ma una macchiana deve poter accettare se' stessa, e quindi ne' $D$ ne $H$ possono esistere.

##### Pattern di dimostrazione dell'indecidibilita'
Una strategia per poter dimostrare che un problema e' indecidibile e' la riconduzione del problema stesso ad $A_{TM}$.