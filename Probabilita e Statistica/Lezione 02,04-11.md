#### Variabili aleatorie discrete note
##### Variabile aleatoria geometrica
Svolgiamo prove ripetute di tipo bernulliano (ripetiamo in maniera identica una prova che ha un'esito dimocotomico, che puo' essere descritto con due etichette(Successo e Fallimento)), fino a quando non otteniamo il primo successo.

$\Omega=\{\{successo\},\{fallimento,successo\},\{fallimento, fallimento,successo\}...\}=\{n-1 fallimenti,successo\}$

Definiamo X come contantore  delle prove eseguite:
- X=$\{F,F,S\}=x=3$

Questa ci permette di stimarle l'immagine che e' infinita($N$\0).

$Px(1)$->{$successo$}
con P che indica la probabilita' di successo nella singola prova

$Px(2)$->{$fallimento,successo$}->P(2)=$(1-p)^1$ x $p$ 

$Px(K)$=Probabilita' della stringa di lungezza $K$=$(1-p)^{K-1}$ x $p$

##### Variabile aleatoria Passon
Osservo il  verificarsi di un evento di interesse raro (a bassa frequenza) in una data finestra temporale o spaziale


#### Media e Varianza di variabili aleatorie discrete
Sono oggeti che compattano cio' che e' contenuto nella pmf, rendendola piu' comprensibile.

##### Media
Diciamo media dellla variabile aleatoria $x$ la seguente quantita':
$E(x)=\sum{}x$
