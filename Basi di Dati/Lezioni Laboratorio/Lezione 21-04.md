## Normalizzazione 
Alcuni schema logici possono presentare criticita' e anomalie, per poter minimizzare le anomalie occore trasformare le relazioni.

Questo e' possibile attraverso un processo di normalizzazione.

### Approccio interamente teorico
1. Si parte dallo schema logico di una base di dati relazionale
	- Facciamo riferimento quindi al modello relazionale
2. Si effettua un'analisi dello schema secondo le metodologie della normalizzazione
3. Questa analisi ci permette di trasformare lo schema inziale della base di dati in uno schema normalizzato

La normalizzazione e l'ER sono complementari poiche' la normalizzazione permette di capire meglio il funzionamento dell'ER e della progettazione logica.

### Dipendenza funzionale
Data una relazione $r(A)$, un sottoinsieme $X$ di attributi di $A(x\subseteq A)$, un altro sottinsieme $Y$ di attributi di $A$

Il vincolo di dipendenza funzionale $X\to Y$ se e solo se 

$$\forall t_1,t_2\in r(t_1[X]=t_2[X]\to t_1[Y]=t_2[Y])$$

quindi se le due tuple coincidono sugli attributi di $X$ coincidono anche sulle tuple di $Y$ per ogni coppia di tuple.