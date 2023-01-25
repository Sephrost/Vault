### Teorema di Post
Il teorema di Post enuncia che 
un linguaggio é **decidibile** se é sia **Decidibile Positivamente** che **Decidibile negativamente**.

## Dimostrazione
Se un **linguaggio** $A$ fosse **decidibile**, possiamo osservare che sia il linguaggio stesso che il suo complemento sono *riconoscibili*, poiché ogni linguaggio decidibile é anche riconoscibile, e il complemento di un linguaggio decidibile é a sua volta decidibile.

Se invece sia $A$ che il suo complemento $\overline A$ sono *turing-recognizable*, definiamo allora un riconoscitore $M_1$ per $A$ e un'altro $M_2$ per $\overline A$. 
Definiamo allora un decisore per $M$ per $A$, che su input $w$:
1. Simula sia $M_1$ che $M_2$ su $w$ in parallelo
2. Se $M_1$ accetta, *accetta*, se $M_2$ rifiuta, *rifiuta*

$M$ ha quindi due nastri per poter simulare $M_1$ e $M_2$ in parallelo, e per far ció alterna le esecuzioni, un passo ciascuno fino all'accettazione.

Poiché ogni stringa é in $A$ oppure nel suo complemento, $w$ deve essere accettata da $M_1$ o $M_2$, e $M$ termina quando una delle due *TM* termina, allora é un decisore per $A$, poiché termina sempre ed é in grado di decidere se $w\in A$.