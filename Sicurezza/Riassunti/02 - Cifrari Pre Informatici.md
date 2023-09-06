### Cifrari a sostituzione
Un cifrario a sostituzione é un cifrario nel quale i caratteri del messaggio vengono sostituiti con uno o piú caratteri.
#### Cifrari di Cesare
É il piú antico, ma anche in piú semplice, cifrario a sostituzione, inventato da Giulio Cesare.

Consiste nel sostituire una lettera dell'alfabeto con la terza lettera successiva: $a\to d,w\to z$.

> La lettera successiva alla $z$ é quindi $a$.

Possiamo inoltre formalizzare l'algoritmo come segue:
$$C=E(3,p)=(p+3)\mod {26}$$
dove $C$ é il carattero cifrato e 3 é la chiave utilizzata.

> Lo scostamento puó essere di qualunque dimensione, la formula generale é quindi $C=E(k,p)=(p+k)\mod26$, dove $k$ é un valore da 0 a 25.

> La formula per decifrare é $p=D(k,C)=(C-k)\mod 26$

Questo cifrario in particolare é molto facile da rompere con attacchi di forza bruta, poiché le chiavi sono solo 26, le lettere dell'alfabeto in modulo 26, e inoltre si conosce il linguaggio del messaggio.
### Cifrari monoalfabetici
Come abbiamo appena visto con il cifrario di cesare un **dominio** delle chiavi **troppo piccolo** puó essere un problema. 

Un modo per estenderlo mantenendo invariato l'alfabeto puó essere **permutare l'alfabeto**, ottenendo quindi un dominio di dimensione $c!$, dove $c$ é il numero di caratteri dell'alfabeto. Questo rende fondamentalmente inutili gli attacchi di forza bruta, ma non quelli di crittoanalisi.
#### Crittoanalisi di cifrari monoalfabetici
Nonostante il dominio delle chiavi sia decisamente maggiore, é possibile comunque compiere attacchi di crittoanalisi se si conosce il linguaggio del messaggio in chiaro.

É infatti possibile sfuttare le regolaritá del linguaggio di partenza, confrontando la frequenza delle lettere del messaggio cifrato con quelle dell'alfabeto del messaggio in chiaro.

> Piú il messaggio cifrato é lungo piú questa operazione é precisa e quindi sufficiente a decifrare il messaggio.

Se il messaggio non é abbastanza lungo e/o non si ottene un match esatto, si puó procedere in diverse maniere:
- possiamo provare a ipotizzare degli assegnamenti e procedere per tentativi, sostituendo i caratteri fino a quando non otteniamo una struttura delle parole accettabile
- anziché ipotizzare gli assegnamenti per ogni singolo carattere, possiamo innanzitutto analizzare la frequenza delle coppie di parole, dette **digrammi**, e ipotizzare gli assegnamenti in base a questi(es: il digramma piú comune per la lingua inglese é *th*), e successivamente ipotizzare gli assegnamenti per i singoli caratteri.
### Mitigazione delle tecniche di crittoanalisi
Nei cifrari monoalfabetici le regolaritá dell'alfabeto di partenza viene mantenute anche dopo la cifratura.

Un modo per ovviare al problema é permettere piú scelte per ogni carattere al momento della sostituzione(es: $e\to 16|74|35|21$).

Se il numero di possibili sostituzione per ogni carattere dell'alfabeto del messaggio in chiaro é direttamente proporzionare alla frequenza degli stessi nell'alfabeto, questo rende inutile l'analisi della frequenza dei caratteri per il messaggio cifrato.

Ma poiché ogni carattere del messaggio in chiaro corrisponde ad esattamente un carattere del messaggio cifrato la crittoanalisi rimane comunque possibile poiché la stuttura del primo viene mantenuta dopo la cifratura.

Per mitigare questo problema esistono due metodi:
- cifrare piú lettere alla volta(**cifrari monoalfabetici a N lettere**)
- usare piú di un alfabeto di cifratura(**cifrari polialfabetici**)
### Cifrari monoalfabetici ad N lettere
#### Cifrario Playfair
> É il miglior cifrario monoalfabetico ad N lettere conosciuto.
> Tratta i **digrafi**(coppie di caratteri) del testo in chiaro come un singolo carattere.

L'algoritmo Playfair si basa su una matrice $5\times 5$ di lettere, generata a partire da una parola.

![[Pasted image 20230226114121.png|300]]

La matrice viene creata come segue:
- si scrive la parola chiave, senza lettere duplicate, da sinistra a destra e dall'alto al basso
- si rimpie il resto con le lettere rimanenti in ordine alfabetico e sempre senza duplicati(le lettere *i* e *j* contano come una lettera sola)

Il messaggio in chiaro viene poi cifrato secondo le seguenti regole:
1. le ripetizioni di lettere nella stesso digrafo vengono separate da un carattere di riempimento, di solito "x"
	- *ballon* $\to$ *ba lx lo on* 
2. due lettere della stessa riga della matrice sono codificate con la lettera alla propria destra(considerando le righe come cicliche)
	- *ar* $\to$ *rm*
3. due lettere della stessa colonna sono codificate con la lettera sottostante(considerando la colonna come ciclica)
	- *mu* $\to$ *cm*
4. in ogni altro caso, ogni carattere viene sostituito dal carattere nella stessa riga ma nella colonna dell'altro carattere del digrafo
	- *mz* $\to$ *ru*
	- *ea* $\to$ *im*/*jm*

Questo cifrario rimane comunque **facile da rompere**, in quanto mantiene praticamente **intatta** la **struttura** del messaggio originale

> Poche centinaia di caratteri circa sono sufficienti a compiere un'attacco di crittoanalisi con successo.
### Cifrari polialfabetici
Per poter migliorare la sicurezza di un cifrario monoalfabetico, si possono usare diverse regole di sostituzione per un singolo alfabeto, ed é la chiave a determinare quale di queste verrá usato in fase di cifratura.

Un modo per applicare uan regola diversa ogni volta é sostituire il carattere in base alla sua posizione nel testo.
#### Cifrario di Vigenère
>É il miglior cifrario polialfabetico conosciuto.

In questo cifrario, l'insieme delle regole di sostituzione consiste nei 26 cifrari di cesare. La chiave é definibile quindi come $K=k_0,k_1,\dots,k_{n-1}$.

Definiamo invece il messaggio in chiaro come una sequenza di lettere $P=p_0,p_1,\dots,p_{m-1}$

> Solitamente $n<m$.

Il messaggi viene quindi cifrato in modo che alla m-esima lettera sia aggiunta la m-esima lettera della chiave, ma in modulo 26, tutto questo in modulo 26 per ottenere un carattere valido.

La formula generale per la cifratura é quindi
$$C_i=(p_i+k_{i\mod n})\mod 26$$

> Per decifrare un messaggio é possibile usare la formula $p_i=(C_i-k_{i\mod n})\mod 26$

Con questo cifrario é quindi possibili avere piú caratteri possibili(una volta cifrati) per ogni lettera in chiaro, ma rimane comunque possibile effettuare attacchi di crittonalisi, poiché sia la chiave che il messaggio condividono la stessa distribuzione di frequenza delle lettere.

Inoltre é possibile notare che due sequenza identiche di messaggio in chiaro si cifrano allo stesso modo se sono separate da una sequenza di n lettere, dove n é un multiplo della lunghezza della chiave, rendendo quindi possibile determinare la lunghezza della chiave.
#### Cifrario di Vernam
> Il miglior modo per difendersi da attacchi di crittoanalisi é scegliere una chiave lunga come il messaggio ma senza alcuna correlazione statistica.

Questo cifrario lavora coi bit piuttosto che con le lettere, applicando l'operatore di XOR tra i bit del messaggio e quelli della chiave.

Puó quindi essere espresso come segue:
$$c_i=p_i\oplus k_i$$
dove:
- $p_i$ é l'i-esimo carattere binario del messaggio in chiaro 
- $k_i$ é l'iesimo carattere binario della chiave
- $c_i$ é l'i-esimo carattere binario del messaggio cifrato
- $\oplus$ é l'operatore di **or esclusivo**(XOR)

> Per decifrare il messaggio $p_i=c_i\oplus k_i$.

Nonostante questo cifrario sia piú resistende alle tecniche di crittoanalisi degli altri visti, non ne é immune se si fornisce abbastanza testo cifrato.
#### One-Time Pad
> É un miglioramento del cifrario di Verman.

Consiste nell'usare una chiave randomica lunga quanto il messaggio, utilizzabile una sola volta.
Questo rende il cifrario sicuro perché non é correlato statisticamente al messaggio in chiaro in alcun modo.

Peró pur fornendo sicurezza assoluta, presenta due problemi:
- É difficile generare grandi quantitá di chiavi randomiche, soprattuto per sistemi molto usati.
- Per ogni messaggio é necessario fornire una chiave di uguale dimensione per cifrarlo
### Cifrari a Permutazione
Questi tipi di cifrari involvono qualche tipo di permutazione o scambio tra lettere del messaggio.
#### Alcuni esempi
Un semplice cifrario di permutazione é **rail fence**, dove il messaggio viene scritto come una sequenza di lettere diagonali.
![[Pasted image 20230301184907.png]]
- messaggio in chiaro: *meet me after the toga party*
- messaggio cifrato: *MEMATRHTGPRYETEFETEOAAT*

Uno schema piú complesso é scrivere il messaggio in forma matriciale e permutare l'ordine delle colonne:
![[Pasted image 20230301190013.png]]

Nonostante un cifrario a permutazione é facilmente riconoscibile(oltre che attaccabile), questi possono essere resi molto piú sicuri permutando piú volte il messaggio o applicando cifrari a sostituzione.
