### Rilocabilita' del codice 
E' un problema relativo alla collocazione del codice all'interno della ram.

Il programma per essere eseguito viene caricato all'interno della ram, dipendentemente dalla porzione libera e all'algoritmo di collocazione.

Se la cpu non e' in gradi di capire la collocazione del codice gli indirizzi vanno caricati esattamente come indicato. Quando invece e' in grado di capire gli indirizzi dove e' locato il codice si dice che questo e' **rilocabile**.
 
 #### Programma sorgente
 Necessita della compilazione, che trasforma il programam sorgente in uno equivalente ma scritto in maniera diversa.
 
 Questa fase puo' produrre degli indirizzi assoluti in alcuni casi, piu' recente produce pero' dei **moduli oggetto**, dove gli indirizzi sono **rilocabili**.
 Questi vengono mandati al **linker**, che ci consente di comporre i vari moduli in un'**unico** eseguibile chiamato **modulo rilocabile**, caricato successivamente dal **loader** sulla ram, insieme alle eventali librerie di sistema.
 Dopo queste fasi otteniamo finalmente un **modulo eseguibile **
 
 ##### Memory management Unit (MMU)
 In una sua versione semplificata un'indirizzo logico entra all'interno dell'mmu e viene composto con un registro di rilocazione, e generando un'indirizzo fisico.
 ##### Linking dinamico
 
 ### Allocazione della ram ai processi 
 [chiedere a Miriam gli appunti]
 #### Allocazione contigua 
 
 #### Paginazione 
 #### Segmentazione 
 