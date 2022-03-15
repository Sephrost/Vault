## Problemi computazionali
Un **problema computazionale** é una **collezione** di **domande** simili tra loro, dette **istanze** o casi particolari, per cui sia stabilito un **criterio** astratto per riconoscere le **risposte corrette**.

###### Esempi
- Moltiplicazione
- Fattorizzazione
- Sorting
- Shortest path


Un **problema** é una relazione **binaria** istanza/risposta, valida se la relazione individua una possibile risposta.
La relazione é sempre **univoca** a meno di permutazioni tra istanze.

### Algoritmo
Un **algoritmo** é un **metodo meccanico** per risolvere un problema computazionale

 É una **procedura** che **termina** per **ogni ingresso** ammissibile e in un tempo finito **produce** una **risposta**.
 
Un algoritmo è **deterministico** se eseguito più volte sullo stesso input, fornisce sempre lo **stesso output**.
Ad ogni algoritmo deterministico è associata una **funzione** dagli ingressi alle uscite.

#### Procedura
Una **procedura** é una sequenza finita di operazioni meccanicamente eseguibili per produrre univocamente un'uscita a partire da certi ingressi.

#### Algoritmo corretto
Un algoritmo é **corretto** rispetto ad un problema computazionale $R$ se **associa** ad ogni **istanza** del problema una **uscita** che soddisfi il criterio di correttezza imposto dal problema.

Inoltre un algoritmo é **corretto** rispetto ad un problema se esiste una risposta corretta per ogni input.

#### Determinismo di un algoritmo
Un algoritmo é **deterministico** se eseguito piú volte sullo **stesso input**, forniscono sempre lo **stesso output**.

#### Algoritmi e Programmi
- Un **programma** puó contenere **diversi algoritmi**, cosó come un algoritmo puó contenere diversi algoritmi
- Un **programma** é scritto in un **specifico linguaggio** di programmazione
- In un **programma** occorre specificiare ed **implementare** opportune **strutture dati**

<center><b>Programma=Algoritmi+Strutture_Dati</b></center>

### Problemi insolubili
Non basta che un problema ben definito perché sia risolubile.

Infatti alcuni problemi computazionali **non** ammettono una soluzione **algoritmetica**.

Es:*Problema dell'halt* -> Algoritmo per sapere prima un programma terminerá dato un determinato input

### Problemi intrattabili 
Problemi che anche se risolvibili **non** hanno un **tempo** di **elaborazione accettabile**, e quindi polinomiale.

Es:*Torri di Hanoi* -> Dati $n$ dischi richiede tempo $2^n-1$ 

### Problemi NP-Completi
Problemi tali che **tutti** o **nessuno** ammettono una **soluzione** in tempo **polinomiale**.

Es:*Cammino hamiltoniano* -> Un cammino in un grafo, orientato o non orientato, è detto hamiltoniano se esso tocca tutti i vertici del grafo una e una sola volta