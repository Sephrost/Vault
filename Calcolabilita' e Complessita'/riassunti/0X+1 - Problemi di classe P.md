> Tutti i modelli computazionali deterministici ragionevolmente complessi sono **polinomialmente equivalenti**, ovvero uno puó simulare un'alto con una crerscita del tempo di esecuzione polnomiale

## Definizione
**P** é la classe di linguaggi decidibili in tempo polinomiale in una TM a singolo nastro deterministica.

$$P=\bigcup\limits_{k}TIME(n^k)$$
Notiamo inoltre che:
- **P** é un'invariante per tutti i modelli computazionali polinomialmente equivalente ad una *TM* deterministica a singolo nastro, ed àe quindi una **classe** matematica **robusta**, non condizionata dalle particolarità dei singoli modelli
- **P** corrisponde alla classe di problemi risolvibili realisticamente da un computer, e quindi esite un modo di risolverlo in tempo $n^k$ per qualche costante $k$ 