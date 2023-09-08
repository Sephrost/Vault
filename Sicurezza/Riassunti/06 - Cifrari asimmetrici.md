Il dover condividere la proria chiave privata e la mancanza di una firma digitale che assicuri la non disconoscibilitá del messaggio rendono inutile la ricerca sistemi di crittografia simmetrica completamente sicuri.

I **cifrari asimmetrici** riescono a risolvere entrambi questi problemi.
Essi si basano sull'utilizzo di **una chiave** per la **cifratura** e **una diversa** ma **correlata** per la **decrittazione**.

Questi sistemi si basano su un'importante proprietá: **non** é possibile **determinare** la **chiave** di **decrittazione** conoscendo solo l'algoritmo crittografico e la chiave di cifratura.
## Struttura di un cifrario a chiave pubblica
Un cifrario simmetrico é composto da **6 elementi**:
- un **messaggio** in **chiaro**
- un'**algoritmo** di **ciratura**
- Una **chiave pubblica** e una **privata**
	- se una é usata per cifrare,l'altra é usata per decrittare
- Il **messaggio cifrato**, prodotto dall'algoritmo a partire da quello in chiaro
- Un'**algoritmo** di **decrittazione**
#### Funzionamento generale
I passi essenziali sono i seguenti:
1. ogni **utente** **genera** una **coppia di chiavi** da usare per la cifratura e la decrittazione del messaggio.
2. ogni utente **condivide** **una** delle due **chiavi**(chiave pubblica) e tiene invece l'altra(chiave privata).
3. se un'utente $B$ invia una messaggio a un'altro utente $A$, allora cifra il messaggio usando la chiave pubblica di $A$.
4. Quando l'utente $A$ riceve il messggio cifrato, lo decifra usando la propria chiave privata.

![[Pasted image 20230513125518.png|500]]

In questo modo **tutti** gli **utenti** hanno **accesso** alle **chiavi pubbliche**, senza dover distribuire quelle private, mantenendo la comunicazione sicura.
### Requisiti di un cifrario asimmetrico
1. É **computazionalmente facile generare** una coppia di **chiavi**
2. La **cifratura** e la **decrittazioni** sono **computazionalmente facili**
3. É **computazionalmente infattibile determinare** la **chiave privata** conoscendo la chiave pubblica
4. É **computazionalmente infattibile recuperare** il **messaggio** in chiaro conoscendo la chiave pubblica e il messaggio cifrato

Questi sono requisiti molto stringenti, infatti ad oggi sono conosciuti pochi algoritmi a chiave pubblica.

> Con computazionalmente infattibile, intendiamo che gli algoritmi conosciuti impiegano tempo piú che polinomiale(**NP**), mentre con computazionalmente facile intendiamo le funzioni che impiegano tempo polinomiale(**P**).