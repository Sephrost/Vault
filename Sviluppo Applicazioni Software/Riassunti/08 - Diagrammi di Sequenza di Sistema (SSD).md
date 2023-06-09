## Diagrammi di Sequenza di Sistema (SSD)
Un **diagramma di sequenza di sistema** (o ***SSD***, da *System Sequence Diagram*) è un **elaborato** che **illustra** **eventi** di input e output relativi ai sistemi in discussione.

Questo mostra per un particolare scenario di un caso d’uso:
- gli eventi generati dagli attori esterni al sistema
- il loro ordine 
- gli eventi tra sistemi

Questi vengono rappresentate con dei diagrammi UML, che permette di illustrare le interazioni tra attori e le operazioni richieste da essi.

Gli SSD permettono quindi di esaminare e definire le funzioni e il comportamento di un sistema a scatola chiusa.

> Non è opportuno creare diagrammi di sequenza di sistema per tutti gli scenari, ma solo per gli scenari scelti per l'iterazione corrente.

### Elementi di un SSD
Un SSD mostra gli **eventi** di sistema per **un solo** **scenario** di un **caso d’uso**.
Esso mostra quindi:
- L'**attore primario** di un caso d'uso
- Il **sistema** di riferimento
- I **passi** che rappresentano le **interazioni** fra di essi
	- Le interazioni iniziate dall’attore primario sono mostrate come messaggi(chiamate a funzioni), con parametri
	- Queste devono essere espresse a livello astratto, piuttosto che in relazione al dispositivo di input fisico

### Esempio di un SSD
![[Pasted image 20230608232021.png]]