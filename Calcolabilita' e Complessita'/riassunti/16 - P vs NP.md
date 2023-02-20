## $P$ vs $NP$
**P** é la classe di linguaggi decidibili in tempo polinomiale in una TM a singolo nastro deterministica, mentre **NP** é la classe di linguaggi per cui l'appartenenza puó essere varificata in tempo polinomiale.

Per quanto i problemi $P$ e $NP$ abbiano definizioni diverse, non e' stato ancora possibile provare che esiste un singolo linguaggio in $NP$ che non sia $P$.

Se le due classi fossero uguali allora ogni problema verificabile in tempo polinomiale sarebbe quindi decidibile in tempo polinomiale.

Quindi il problema $P=NP$ rimane ad oggi un problema senza soluzione.

> La maggior parte dei ricercatori credono che le due classi non siano equivalenti poiché non é stato possibile trovare un'algoritmo di tempo polinomiale per i problemi in $NP$. 

Rimangono quindi due possibilitá:
- $P$ é contenuto in $NP$
- Le due classi sono equivalenti

![[Pasted image 20221114092559.png]]

Peró visto che il miglior algoritmo per decidere un problema **NP** impiega la forza bruta, e quindi termina in tempo esponenziale, possiamo afformare che **NP** é un sottoinsieme di **EXPTIME**.
