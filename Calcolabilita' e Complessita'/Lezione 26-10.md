### Linguaggio risultante dall'unione
Siano $L_1,L_2$ positivamente decidibili -> $L_1\cup L_2$ e' decidibile.

Supponiamo di avere $M_1$ decisore di $L_1$ e $M_2$ decisore di $L_2$, entrambi decisori positivi.

Sia inoltre $M_1|M_2$ la composizione parallela di $M_1$ e $M_2$ modificata come segue, accetto se $M_1$ o $M_2$ accettana e rifiuto se seia $M_1$ che $M_2$ rifiutano(*disgiunzione parallela*). La macchiana risultante e' anch'essa un decisore positivo.

Il linguaggio risultante sara' quindi chiuso per l'unione, la stessa cosa vale quindi per i linguaggi negativamente decidibile.

### Linguaggio risultante dall'insersezione
Vale lo stsso ragionamento dell'unione.

Acetto se $M_1$ ed $M_2$ accettano e rifiuto se $M_1$ o $M_2$ rifiutano.