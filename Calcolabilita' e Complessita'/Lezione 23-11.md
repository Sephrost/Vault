#### Esercizion 7.13
Sia 
$$MODEXP=\{<a,b,c,p>|a,b,c,d\;sono\;binari\;interi\;positivi\;tali\;che\;a^b\equiv c(mod\;p)\}$$

mostriamo che $MODEXP\in P$.

Poiche' il numero massimo di passi conosciuti e' $<10^{100}$= $1$ google, allora l'operazione richiederebbe un numero maggiore di passi.

Quando $b$ e' potenza di $2$, allora
$$A1=a^2mod\,p$$
$$A2=a1^2=(a^2)^2=a^4mod\,p$$
$$A_n=a^{(2^n)}mod\,p$$

abbiamo calcoltato quindi $a^b$ in $n$ passi.


