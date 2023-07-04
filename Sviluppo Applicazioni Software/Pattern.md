# Creator
#### Problema
A quale classe creatrice B bisogna assegnare la responsabilitá di creare una nuova istanza della classe A?
#### Risposta
Assegnare alla classe B la responsabilitá se una o piú condizioni sono vere:
- B contiene o aggrega istanze della classe A
- B mantiene un riferimoento ad A dopo la creazione
- B utilizza strettamente A
- B é un expert rispetto ad A, ovvero possiede i dati necessari per l'inizializzazione di un oggetto di classe A

A paritá di condizioni vere si preferisce la classe che aggrega o contiene la classe A.


# Information Expert
#### Problema
Qual'é il principio generale per l'assegnazione delle responsabilitá agli oggetti?
#### Soluzione
Assegna la responsabilitá alla classe che contiene le informazioni necessarie per soddisfare la responsabilitá.

---

# Low Coupling
#### Problema 
Come si puó ridurre l'impatto dei cambiamenti, sostenendo una dipendenza bassa e maggiore opportunitá di riuso?
#### Soluzione
Assegno la soluzione in modo che l'accoppiamento rimanga basso, valutando le varie possibilitá.
# High Cohesion
#### Problema
Come mantenere gli oggetti focalizzati, comprensibili, gestibili e sostenere un basso accoppiamento come effetto collaterale?
#### Soluzione
Assegno le responsabilitá in maniera tale che la coesione, ovvero la misura di quanto le responsabilitá di un elemento siano concentrate e correlate, alto, valutando le varie opzioni

Con coesione intendiamo quanto fortemente sono correlate e concentrate le respondabilitá di un oggetto, se questa é alta le responsabilitá sono altamente correlate e non esegue troppo lavoro.
Una coesione alta favorisce il riuso delle classi, facilita la comprensione del progetto e spesso sostiene un'accoppiamento basso. 
# Controller
#### Problema
Qual'é il primo oggetto oltre lo strato di interfaccia utente che riceve e controlla un'operazione di sistema?
#### Soluzione
**Assegna** la **responsabilità** a una **classe** che rappresenta una delle seguenti scelte:
- Rappresenta il “sistema” complessivo, un “oggetto radice”, un dispositivo all’interno del quale viene eseguito il software, un punto d’accesso al software, o un sottosistema principale;
- Rappresenta uno scenario di un caso d’uso all’interno del quale si verifica l’evento di sistema
	- Si utilizzi la stessa classe controller per tutti gli eventi di sistema nello stesso scenario di caso d’uso. 
	- Una sessione è un’istanza di una conversazione con un attore. Le sessioni possono avere una lunghezza qualsiasi, ma spesso una sessione corrisponde a un’esecuzione di un caso d’uso (sessioni di caso d’uso).







# GOF
##



