# Domande di ripasso
###### 1. Dare una definizione precisa di una Macchina di Turing
Una macchina di turing é una settupla composta da:
1. Un'insieme di stati della macchina
2. Un'alfabeto della macchina
3. Un'alfabeto del nastro, che contiene il carattere di padding(blank)
4. Una funzione di transizione
5. Uno stato iniziale
6. Uno stato di accettazione
7. Uno stato di rifiuto
Lo stato di accettazione deve inoltre diverso dallo stato di rifiuto

###### 2. Cos'é la computazione di una macchina di Turing per una stringa? Quando accetta e quando rifiuta?
Una computazione per una *TM* $M$ é un'applazione passo passo della funzione di transizione di $M$ per ogni carattere della stringa $w$.

$M$ usa quindi un nastro infinito a destra sul quale é rappresentata $w$ e una testina per leggere e scrivere su questo, e la testina é in grado di muoversi liberamente su di esso, un passo alla volta.

Una macchina di Turing, a differenza di un'automa a stati finiti, accetta una stringa appena entra in uno stato di accettazione, e le rifiuta appena entra in uno stato di rifiuto. L'entrata in uno di questi stati termina quindi la computazione.

###### 3. Che differenza c'é tra non terminazione e rifiuto di una stringa? La terminazione é garantita per il calcolo di una *TM* per una stringa?
Definiamo come non terminazione la condizione per cui la computazione di una *TM* non termina a causa di un loop. Quando una *TM* é in un loop significa che non entrerá mai in uno stato di accettazione o rifiuto.

Invece una *TM* rifiuta una stringa se determina che non appartiene al linguaggio.

Inoltre la terminazione é garantita solo per i decisori, quindi quelle *TM* che sono sempre in grado di detrminare se una stringa appartiene all'alfabeto della macchina  oppure no, senza mai entrare in un loop.

###### 4. Quando un linguaggio viene riconosciuto da una *TM*?
Un linguaggio $L$ é riconosciuto da una *TM* $M$ se per ogni stringa $w$ appartenente al linguaggio di $M$, questa accetta la stringa sé e solo sé appartiene a $L$. 

###### 5. Date un'esempio di *TM* secondo la vostra definizione
Un'esempio di *TM* secondo la mia definizione é la macchina che accetta tutte le stringhe: questa macchina ha lo stato di inizio uguale allo stato di accettazione, uno stato di rifuto e una funzione di transizione che, per ogni carattere letto porta sempre allo stato di accettazione.

###### Definire la Np-Completezza per un linguaggio, spiegare il suo ruolo nella classificazione dei problemi NP e le sue proprietá piú importanti
Partiamo dalla definizione di NP.
NP é la classe dei problemi decisionali verificabili in tempo polinomiale
Un linguaggio appartiene a questa classe solo se é deciso da una macchina di turing polinomiale non deterministica.

Ora definiamo in problema come NP-completi la classe di problemi NP per i quali esiste una riduzione di tempo polinomiale da ogni problema NP ad esso.

Giocano un ruolo fondamentale nella risoluzione del problema $P=NP$ poiché se si scoprisse un algoritmo polinomiale per risolverne uno, tutti i problemi in NP potrebbero essere risolti in tempo polinomiale attraverso l’algoritmo di riduzione.

### The big 3
###### 1. Definire il problema dell'accettazione per le *TM*,enunciare la principale proprietá nota del problema e dimostrarlo.
Definiamo il problema dell'accettazione come segue:
$$A_{TM}=\{<M,w>|M\;é\;una\;TM\;che\;accetta\;w\}$$

ovvero é il problema di verificare se una *TM* accetta o no una stringa.

Sappiamo che é un noto problema indecidibile, quindi dimostriamo questa proprietá.

Supponiamo per assurdo che $A_{TM}$ sia decidibile, allora deve esistere un decisore $H$ che lo decide, che su input $<M,w>$ :
- $accetta$ se $M$ accetta
- $rifiuta$ se $M$ rifiuta

Definiamo un'altra *TM* $D$ che ha $H$ come subroutine. $D$ prendi quindi in input $M$ e prova ad eseguire $H$ per determinare cosá ritornerebbe $M$ passandogli in input la sua descrizione.
$H$ fornirá quindi in input alla *TM* presente nella sua routine $<M,<M>>$.
$D$ invece ritornerá l'oppoto di quanto restituito da $H$, quindi
- accetta se $M$ non accetta la sua descrizione
- rifiuta se $M$ accetta la sua descrizione

Peró provando ad eseguire $D$ su se stesso otteniamo che
- $D$ accetta se $D$ non accetta la sua descrizione
- $D$ rifiuta se $D$ accetta la sua descrizione
ma $D$ non puó non accettare la sua descrizione in quanto questo produrrebbe una contraddizione. Di conseguenza né $D$ ne $H$ possono esistere e di conseguenza $H$ non é un decisore di $A_{TM}$.

###### 2. Enunciare il teorema di Post e dimostrarlo
Il teorema di Post afferma che un linguaggio é decidibile se é sia positivamente che negativamente decidibile.

Proviamo a dimostrare l'enunciato.

Se un **linguaggio** $A$ fosse **decidibile**, possiamo osservare che sia il linguaggio stesso che il suo complemento sono *riconoscibili*, poiché ogni linguaggio decidibile é anche riconoscibile, e il complemento di un linguaggio decidibile é a sua volta decidibile.

Se invece sia $A$ che il suo complemento $\overline A$ sono *turing-recognizable*, definiamo allora un riconoscitore $M_1$ per $A$ e un'altro $M_2$ per $\overline A$. 
Definiamo allora un decisore per $M$ per $A$, che su input $w$:
1. Simula sia $M_1$ che $M_2$ su $w$ in parallelo
2. Se $M_1$ accetta, *accetta*, se $M_2$ rifiuta, *rifiuta*

$M$ ha quindi due nastri per poter simulare $M_1$ e $M_2$ in parallelo, e per far ció alterna le esecuzioni, un passo ciascuno fino all'accettazione.

Poiché ogni stringa é in $A$ oppure nel suo complemento, $w$ deve essere accettata da $M_1$ o $M_2$, e $M$ termina quando una delle due *TM* termina, allora é un decisore per $A$, poiché termina sempre ed é in grado di decidere se la stringa appartiene ad $A$.

###### 3. Enunciare il problema Clique e dimostrare che é NP-completo

Partendo dalla definizione di una clique come un'insieme di $k$ vertici di un grafo indiretto, per cui ogni nodo di questo insieme é connesso ad ogni altro da un'arco, definiamo il problema Clique come segue
$$CLIQUE=\{<G,k>|\,G\;e'\;un\;grafo\;indiretto\;con\;una\;k-clique\}$$
ovvero il problema di determinare se un grafo contiene una clique di dimensione $k$.

Si puó dimostrare che é NP-completo mostrando un a riduzione da $3SAT$.

Sia $\phi$ una formula booleana della forma normale 3-congiuntiva(ogni clausola ha esattamente 3 letterali) con $k$ clausole. La riduzione genera quindi la coppia $<G,k>$, dove $G$ é un **grafo indiretto** e $k$ é il numero di clausole, dette anche **triple**, poiché composte dai 3 vertici che ne rappresentano i letterali, e rappresentante una clausola di $\phi$.

Ogni vertice del grafo ha quindi un arco verso ogni altro vertice, con alcune eccezioni:
1. Non ci sono archi tra vertici di una stessa tripla
2. non ci sono archi tra vertici corrispondenti ad un letterale ed al suo negato( anche se appartengono a clausole differenti)

Dimostriamo ora che $\phi$ soddifa $3SAT$ sé e solo sé $<G,k>$ soddisfa $Clique$:
Se $\phi$ avesse un'assegnamento che lo soddisfa allora **ogni clausola** di $\phi$ ha **almeno** **un** letterale **vero**.

Prendiamo in considerazione quindi **un letterale vero** per **clausola**, i nodi selezionati corrisponderebbero a un **sottografo** rappresentante una $k-clique$, poiché ogni letterale appartiene a una tripla(clausola) diversa, e non avente vertici tra un letterale e il suo negato(per il punto $2$ delle eccezioni) mantenendo inoltre un'assegnamento valido.

Poiché ogni clausola in questo caso é soddisfatta possiamo conscludere che $\phi$ sarebbe soddisfacibile e quindi $CLIQUE$ é **NP-completo** poiché $CLIQUE\in NP$ e $CLIQUE$ é riducibile a $3SAT$, che é **NP-completo**.

