Sia
$$HALT_{TM}=\{<M,w>|\,M\;e'\;una\;TM\;e\;M\;termina\;con\;input\;w\}$$
dimostriamo che e' indecidibile.

Assumiamo per **assurdo** che $HALT_{TM}$ sia decidibile, di conseguenza anche $A_{TM}$ e' decidibile.

Ipotizziamo che esista quindi una *TM* $R$ che decida $HALT_{TM}$. Costruiamo quindi un'altra *TM* $S$ che decida $A_{TM}$, con $S$ che opera nella seguente maniera:

Dati in input $<M,w>$, con $M$ descrizione di una *TM* e $S$ stringa:
1. Eseguiamo $R$ con input $<M,w>$
2. Se $R$ rifiuta, $rifiuto$
3. Se $R$ accetta, simuliamo $M$ su $w$ finche' non si ferma
4. Se $M$ accetta, $accetto$, altrimenti $rifiuto$

Quindi se $R$ decide $HALT_{TM}$, allora $S$ decide $A_{TM}$, ma poiche' $A_{TM}$ e' indecidibile, lo e' anche $HALT_{TM}$.
