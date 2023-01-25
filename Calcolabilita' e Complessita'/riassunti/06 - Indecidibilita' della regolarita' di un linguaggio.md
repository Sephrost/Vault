### Indecidibilità della regolarità di un linguaggio
Definiamo il problema di determinare se una *TM* ha un'automa a stati finiti equivalente.

Sia 
$$REGULAR_{TM}=\{<M>|M\;e'\;una\;TM\;e\;L<M>\;e'\;un\;linguaggio\;regolare\}$$
dimostriamo che e' indecidibile.

Assumiamo che $REGULAR_{TM}$ sia decidibile, allora deve esiste una *TM* $R$ che lo decide. Definiamo quindi anche la *TM* $S$ che decide $A_{TM}$, prendendo in input $<M,w>$, con $M$ una *TM* e $w$ una stringa.

> Idea chiave: $S$ modifica $M$ in modo da fargli riconoscere un linguaggio regolare solo se $M$ accetta $w$

La *TM* $S$ funziona come segue:
Dati in input $<M,w>$, con $M$ *TM* e $w$ una stringa:
1. $S$ costruisce una *TM* $M_2$ come segue
	- $M_2$ = su input $x$
		 1. se $x$ e' della forma $0^n1^n$, $accetto$
		 2. se $x$ non e' della froma sopra indicata, eseguo $M$ con input $w$ e accetto solo se $M$ accetta $w$
2. Eseguo $R$ con input $<M_2>$
3. Se $R$ accetta, $accetto$, se $R$ rifiuta, $rifiuto$

> Notare che il linguaggio $\{0^n1^n|n\ge 0\}$ **non** e' regolare

Fondamentalmente $M_2$ controlla se $w$ appartiene ad un lingnuaggio non regolare, se non vi appartiene allora controllo se appartiene invece al linguaggio regolare $\Sigma^*$ , nel caso $M$ accettasse, e quindi anche $R$ accettasse, significherebbe che $S$ decide $A_{TM}$, ma questo non e' possibile, quindi $R$ non puo' decidere $REGULAR_{TM}$.

