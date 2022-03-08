### identificatori delle entita'
Son strumenti per l'identificazione univoca delle occorrenze di un'entita'

Possono essere costituite da 
- Attributi dell'entita'(anche tutti): Identificatori interni
- Entita' esterne collegate attraverso una relazione:Identificatori esterni

Si rapprentato graficamente attraverso l'annerimento dei pallini degli attributi.

Oni entita' deve possedere almeno un'identificatore, ma puo' averne piu' di uno.

Un identificatore deve avere cardinalita' 1:1.

Un'identificazione esterna puo' coinvolgere entita' a loro volte identificate esternamente, purche' non vengano generati cicli.

#### Generalizzazioni
Un generalizzazione mette in relazioni delle entita' $E_1,E_2,\dots,E_n$ con un'altra entita' $R$, che le comprende come casi particolari 

$E$ e' quindi generalizzazione di $E_1,E_2,\dots,E_n$, e queste sono anche specializzazioni,o sottotipi, di $E$.

Ogni proprieta'(atributi,relazioni,...) della generalizzazione e' significativa, e quindi ereditata, per le sue specializzazione, ed ogni occorrenza delle specializzazioni e' anche occorrenza della generalizzazione di queste.

##### Tipi di generalizzazioni
Una generalizzazione puo' essere 
- totale
	- se ogni occorrenza dell'entita' genitore e' occorrenza di almento una delle entita' figlie
- Esclusiva
	- Se ogni occorrenza dell'entita' genire e' occorrenza di al piu' una delle entita' figlie.
