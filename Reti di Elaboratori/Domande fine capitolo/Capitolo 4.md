### Domande fine capitolo
######  Qual è il nome di un pacchetto a livello di rete? Qual è la differenza fondamentale tra router e switch di livello di collegamento?
Un pacchetto a livello di rete é chiamato datagramma.
Un router inoltra i pachcetti in base all'indirizoz di destinazione, mentre uno switch a livello di collegamento in base all'indirizzo mac.

###### Abbiamo visto che le funzionalità del livello di rete possono essere divise in funzionalità del piano dei dati e funzionalità del piano di controllo. Quali sono le principali funzioni del piano dei dati? Quali sono le principali funzioni del piano di controllo?
La funzione principale del piano di dati é l'inoltro mentre la funzione principale del piano di controllo é l'insradamento.

###### Abbiamo fatto una distinzione tra la funzione di inoltro e la funzione di instradamento effettuate nel livello di rete. Quali sono le differenze chiave tra instradamento e inoltro?
L'inoltro é la funzione che permette ad un pacchetto di passare da un collegamento di ingresso ad uno di uscita al collegamento di uscita corrispondente secondo la tabella di inoltro, mentre l'instradamento é la funzione attraverso la quale viene deciso il percorso che dovrá seguire il pacchetto per giungere all'indirizzo di destinazione. I'inoltro é un'operazione molto veloce, della grandezza dei millisecondi, ed é quindi implementata in hardware, mentre l'instradamento richiede piú tempo, ed é quindi inplementato a livello software

###### Qual è il ruolo della tabella di inoltro in un router?
La tabella di inoltro associa un collegamento di uscita ad un pacchetto presente su un collegamento di ingresso, secondo uno o piú criteri.