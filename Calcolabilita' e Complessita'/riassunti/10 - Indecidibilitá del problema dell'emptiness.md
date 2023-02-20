### Indecidibilita' del problema dell'emptiness
Sia 
$$E_{TM}=\{<M>|\,M\;e'\;una\;TM\;e\;L(M)=\emptyset\}$$
dimostriamo che $E_{TM}$ e' indecidibile.

Assumiamo per assurdo che $E_{TM}$ sia decidibile, allora esiste una *TM* $R$ che decide il problema.

Sia inoltre $M_1$ una *TM* che ha una stringa $w$ nella sua descrizione, e opera nella seguente maniera
$$M_1\{x\}=\Big\{^{se\;x\ne w,\;rifiuto}_{se\;x=w,eseguo\;M\;con\;w\;e\;accetto\;se\;M\;accetta}$$
> $M_1$ esegue il controllo sulle stringhe un carattere alla volta

Usiamo ora $R$ per costruire una *TM* $S$ che decide $A_{TM}$ nella seguente maniera:
$S$ = Dati in input $<M,w>$
1. Usiamo la descrizione di $M$ e la stringa $w$ per costruire $M_1$
2. Eseguiamo $R$ con input $M_1$
3. Se $R$ accetta, $rifiuto$, se $R$ rifiuta, $rifiuto$

> $S$ e' in gradi di costruire $M_1$ perche' deve solo aggiungere stati aggiuntivi per implementare l'eguaglianza fra stringhe

Quindi se $R$ potesse decidere $E_{TM}$, allora $S$ dovrebbe poter decidere $A_{TM}$, ma un decisore per $A_{TM}$ non puo' esistere quindi neanche $R$ puo' esistere