### Problema dell'accettazione di Post
E' un problema indecidibile.

Supponiamo di avere un'insieme di domino del tipo $[\frac{a}{ab}]$, ognuno contenete 2 stringhe.

Dobbiamo creare una lista(ripetizioni incluse) cosi' che la stringa dei caratteri superiori sia la stessa di quelli inferiori, chiamando il risultato **match**.

## Riducibilita' 
Una riduzione e' un modo di convertire un problema in un'altro in modo che la soluzione del secondo problema puo' essere usato per risolver il primo problema.

Quindi applichiamo l'immagine della prima macchina alla seconda, se questa l'accetta, ed e' un problema calcolabile, allora l'accettera' anche la prima($w\in A\to f(w)\in B$).

![[Pasted image 20221010100649.png]]

### Problema della fermata 
definiamo 
$$HALT_{tm}=\{<M,w>|M\;is\;a\; TM \;and\;M\;halts\;on\;input\;w\}$$
$HALT_{tm}$ e' indecidibile

