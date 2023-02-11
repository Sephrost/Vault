### 3SAT
Sia 
$$3SAT=\{<\phi>|\phi\;é\;una\;formula\;soddisfacibile\;della\;forma\;normale\;3\;congiuntiva\}$$
dove una formula é della forma normale congiuntiva se ogni clausola é connessa da un *AND*($\land$) e ogni suo letterale é connesso da or($\lor$), ed é della normale 3 congiuntiva se inoltre ogni clausola é composta da 3 letterali in or logico($\lor$).

> Se l'assegnamento é soddisfatto almeno un letterale per clausola deve essere vero.

## Dimostrazione
$3SAT\in NP$ poiché una *TM* non determinisca polinomiale puó generare un'assegnamento per una formula booleana $\phi$ e accettare se lo soddisfa.