### OSPF - Instradamento all'interno di sistemi autonomi
Gli algoritmi di instradamento visti interpretyano la reta come un'insieme di router interconnessi, dove ciascun router é indistinguibile da un'altro.

Questa visione risulta troppo riduttiva per due motivi:
- **Scalabilitá** : ad un'incremento di numero di router il tempo richiesto dagli algoritmi di instradamento cresce polinomialmente(che é comunque troppo)
- **Autonomia Amministrativa**: internet é una rete di reti, dove ognuna é diversa dall'altra

#### Sistemi Autonomi

Questi problemi possono essere risolti organizzando i router come **sistemi autonomi**(*autonomous systems*).

Questi sono composti da grouppi di router posti sotto lo stesso **controllo amministrativo**.

> Ogni AS é identificato da un numero di sistema autonomo univoco, assegnati da ICAAN

I router in un Sistema autonomo eseguono tutti lo stesso algoritmo di instradamento.

#### OSPF 
OSPF é un protocollo link state utilizzante il flooding di informazioni riguardo lo stato dei collegamenti e l'algoritmo di Dijkstra per determianre il percorso di costo minimo.

Un router costituisce una **grafo** dell'intero AS per eseguire in locale l'algoritmo per determinare l'albero di percorsi minimi verso tutte le sottoreti.

> Il router rappresenta la radice dell'albero.

> OSPF non impone una politica per la scelta dei pesi dei collegamenti.

Le tabelle di routing vengono aggiornate secondo due modalitá:
- Periodicamente: ogni 30 minuti
- Non periodica: Ogni qualvosta che si verifica un cambiamento dello stato di collegamento(variazione del costo,$\dots$)

Gli annunci OSPF sono contenuti in messaggi OSPF che vengono trasportati direttamente da IP, quindi é responsabilitá di OSPF l'implementazione le funzionalitá di trasporto affidabile e il broadcast dello stato dei collegamenti.

##### Vantaggi
- Sicurezza: gli scambi tra router OSPF possono essere autenticati
- Percorsi con lo stesso costo
- Supporto integrato per l’instradamento unicast e multicast
- Supporto alle gerarchie in un dominio di instradamento


%%Aggiungere parte su RIP%%

### Instradamento Intra-ISP
Per determinare i percorsi tra sorgente e destinazione che interessano piú AS é necessario un protocollo di instradamento intra-ISP, che coordini piú AS.

