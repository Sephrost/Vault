#### Problemi classici di sincronizzazione
##### Problema dei produttori-consumatori
I messaggi vengono scambiati attraverso un buffer di grandezza limitata. 

Il produttore produce i dati e li inserisce nel buffer, quindi deve avere uan cella vuota nel quale inserirli, altrimenti aspetta che si liberi, rimanendo sospeso.

Il consumatore quando legge il dato libera la cella, estraendolo. Il consumatore si sospende quando il buffer e' vuoto.

###### Soluzione
Utilizziamo: 
- un semaforo di mutua esclusione (**mutex**), inizializzato ad 1
- 2 semafori contatori (**liberate** e **occupate**) che indicano le risorse a disposizione 
	- Il liberate viene inzializzato alla grandezza del buffer, mentre l'occupate a 0, poiche' in origine il buffer e' vuoto 

Produttore|Consumatore
--|--
forever{<br>*produci un elemento*<br>P(Liberate)->si assicura che la cella sia libera<br>P(Mutex)->assicura la mutua esclusione<br>V(mutex)<br>V(occupate)<br>}|forever{<br>P(occupate)<br>P(mutex)<br>*estrezione elemento*<br>V(mutex)<br>V(liberate)<br>}
##### Problema dei lettori-scrittori
In questo caso il buffer e' illimitato, poiche' cresce dinamicamente, grazie a questo i lettori non tolgono dati dalla memoria poiche' non e' necessario e gli scrittori possono sempre scrivere.

La mutua esclusione viene imposta soltanto agli scrittori, quindi e' l'unico processo che puo' accedere ad una data cella di memoria mentre scrive.

###### Soluzione 
Utilizziamo:
- un sermaroro **mutex**, inizializzato ad 1.
- Un semaforo **scrittura**, sempre di mutua esclusione.
- Una variabile intera considivisa **Num_Lettori**, inizializzata a 0.

Scrittore|Lettore
--|--
forever{<br>P(Scrittura)<br>*scrive*<br>V(scrittura)<br>}|forever{<br>P(mutex)->Garantisce la mutua esclusione nell'accesso a Num_Lettori<br>Num_Lettori++<br>if(Num_Lettori\==1){<br>P(scrittura)<br>}<br>V(mutex)<br>*legge*<br>P(mutex)<br>Num_Lettori--<br>if(Num_Lettori==0){<br>v(Scrittura)<br>}<br>V(mutex)<br>}

##### Problema dei 5 filosofi
[copiare da ale]