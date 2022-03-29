## Ottimizzazione delle espressioni algebriche 
Ottimizzare un'espressione algebrica, in riferimento ad un'interrogazione di una base di dati, significa fare in modo che l'implementazione dell'interrogazione risulti più veloce possibile.

Il DBMS lavora in memoria centrale, cosi' come l'applicazione che lavora sui dati.

Il DBMS dialoga con le periferiche di storage attraverso il gestore del buffer (gestisce pagine di memoria).

Quando un'applicazione richede un'informazione viene richiesta d DBMS, Il DBMS deve trasferire una pagina dalla periferica di storagealla memoria centrale (buffer), e solo in quel momento potra' essere elaborata.

Se i DBMS vogliono minimizzare i tempi di risposta devono minimizzare il trasferimento di pagine.

L'obiettivo dell'ottimizzatore del DBMS è di minimizzare il trasferimento di pagine da e verso la memoria centrale.

%%Rivedere WOL%%

### Ottimizzazione Logica

Questa fase e' indipende dalle strutture di memorizzazione.

L'ottimizzazione logica prende in input un'albero sintattico scritto dall'utente e ne genera uno equivalente sfruttando le proprieta' dell'algebra relazionale.

Per ottimizzare l'interrogazione, l'ottimizatore logico tendta di ridurre la massa di tuple concettualmente coinvolte dall'interrogazione.

### Ottimizzazione Fisica 

L'ottimizzatore fisico pende in input l'albero generato dall'ottimizzatore logico e, conoscendo le strutture di memorizzazione, prende in esame i nodi dell'albero sintattico e sceglie l'agoritmo di ottimizzazione ottimale per eseguirli.

