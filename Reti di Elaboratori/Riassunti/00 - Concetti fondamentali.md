## Internet
E' una rete che connete miliardi di dispositivi, detti **host** o *end system*.

I sistemi periferici sono connessi tra loro tramite una **rete di collegamenti** (*communication link*, di vari materiali-> es: Fibra,Rame,Onde radio $\dots$ ),con diverse velocita' di trasmissione, e commutatori di pacchetti (*packet switch*).

## Pacchetti
Quando un sistema periferico vuole inviare dati a un altro sistema periferico, **suddivide** i **dati** in sottoparti e **aggiunge** un’**intestazione** a ciascuna di esse.

L’insieme delle informazioni risultanti viene chiamato **pacchetto**.
I pacchetti sono inviati attraverso la rete alla destinazione, dove vengono riassemblati per ottenere i dati originari.
### Commutatore di Pacchetti
Un **commutatore di pacchetto**(*packet-switch*) prende un pacchetto che arriva da uno dei collegamenti in ingresso e lo ritrasmette su uno di quelli in uscita.

Esistono vari tipi di commutatori, ma i due principali nell’odierna Internet sono 
- **router** 
- **commutatori a livello di collegamento** (*link-layer switch*)
	- solitamente usati nelle reti di accesso
#### Route
La sequenza di collegamenti e di commutatori di pacchetto attraversata dal singolo pacchetto è nota come **percorso** o **cammino** (*route* o *path*) attraverso la rete.
### Transmission Rate
Collegamenti diversi possono trasmettere dati a velocità differenti.

Tale **velocità di trasmissione** (*transmission rate*) viene misurata in **bit/secondo** (*bps*).

## Internet Service Provider - ISP
L'accesso ad internet e' reso possibile dagli **Internet Service Provicer** o *ISP*, i quali offrono servizi di connettivita'.

Ciascuna rete di un ISP è gestita in modo **indipendente**, fa uso del protocollo **IP** e si **conforma** a determinate **convenzioni** riguardo a nomi e indirizzi.