## Attore
É qualcosa o qualcuno dotato di comportamento, come una persona, un sistema informatico o un'organizzazione.

Ci sono diversi tipi di attori:
- **Attore primario**
	- raggiunge gli obiettivi utente utilizzando i servizi del sistema 
- **Attore di supporto**
	- offre un servizio al sistema
- **Attore fuori scena**
	- ha un interesse nel comportamento del caso d’uso
## Istanze di casi d'uso
Uno **scenario** (o **istanza di caso d’uso**) è una **sequenza** specifica di **azioni** e interazioni tra il sistema e alcuni attori.

Descrive una storia nell'uso di un sistema.

# Casi d'uso
Un caso d'uso é una **collezione** di **scenari correlati** che descrivono un attore che usa un sistema per raggiungere un obiettivo specifico.

Definiamo inoltre come **modello di caso d'uso** l'insieme di tutti i casi d'uso scritti.

> I casi d'uso sono documenti di testo.

É possibile, opzionalmente, includere un diagramma UML dei casi d'uso, che mostra il nome del caso stesso, gli attori coinvolti e le relazioni tra questi.

I casi d'uso mettono in risalto gli obiettivi degli utenti e i loro punti di vista, permettendo di evidenziare chi utilizzerá il sistema, i loro scenari tipici e i loro obiettivi.

> I casi d'uso sono quindi requisiti, funzionali o comportamentali, anche se non permettono di rappresentare tutti i requisiti.

## Formati di casi d'uso
- **Formato breve**
	- Sono un riepilogo coinciso, di un solo paragrafo.
	- Sono solitamente relativo allo scenario di successo
- **Formato informale**
	- Sono composti da piú paragrafi, scritti in modo informale, relativi ai vari scenari
- **Formato dettagliato**
	- Tutti i passi e le variazioni sono descritti nel dettaglio.
	- Includono delle sezioni di supporto, come le pre-condizioni e le garanzie di successo.
	- Vanno usati dopo che molti casi d’uso sono stati identificati e scritti in formato breve

Solo il 10% dei casi d'uso piú significativi viene scritto in formato dettagliato.

### Template di caso d'uso dettagliato
![[Pasted image 20230310122232.png|500]]
### Sezioni del caso d'uso dettagliato
#### Preambolo
Tutto ció che precede lo scenario princiale e le sue estensioni.

Contiene informazioni che é importante leggere prima degli scenari del caso d'uso.

É caratterizzato da:
- **Portata**
	- Descrive i confini del sistema in via di progettazione
- **Livello**
	- Una modo per classificare i casi d'uso
	- I possibili livelli sono:
		- **di obiettivo utente**
			- É il piú comune
			- Descrive lo scenario con cui l'attore primario raggiunge l'obiettivo
		- **di sottofunzione**
			- descrive i passi richiesti all'utente come supporto per il raggiungimento dell'obiettivo
- **Attore finale o Attore Primario**
	- L'attore finale é l’attore che vuole raggiungere un obiettivo, e questo richiede l’esecuzione dei servizi del sistema
	- L’attore primario è l’attore che usa direttamente il sistema
	- Solitamente l'attore primario coincide con l'attore finale
- **Parti interessate e interessati**
	- É l'elenco delle parti intessatee, ovvero chi ha interessi nel raggiungimento dell’obiettivo espresso dal caso d’uso in oggetto

- **Pre-condizioni**
	- descrivono che cosa deve essere sempre vero prima di iniziare uno scenario del caso d’uso
	- Queste non vengono verificate all'interno del caso d'uso, ma si **assume** che siano sempre **vere**
- Le **post-condizioni** (o *garanzie di successo*)
	- Affermano che cosa deve essere vero quando è stato completato con successo il caso d’uso
	- Deve quindi soddisfare le esigenze delle parti interessate

#### Flusso di base
É la descrizione di un percorso di **successo comune** che **soddisfa** gli interessi delle parti interessate. Viene anche detto *happy path*.

> Lo scenario principale è costituito da una sequenza di passi, che può contenere passi da ripetere più volte, ma che di solito **non** comprende alcuna condizione o **diramazione**.

Lo scenario è formato da una sequenza di passi, che possono essere di tre tipi:
- Un’**interazione** tra **attori**
	- Il sistema é da considerarsi un utente
- Un **cambiamento** di **stato** da parte del **sistema**
- Una **validazione**
	- Questa viene solitamente effettuata dal sistema

Il primo passo di un caso d’uso non sempre rientra in questa classificazione,e talvolta neanche l'ultimo passo, ma può indicare l’evento (*trigger*) che scatena l’esecuzione dello scenario.

#### Estensioni
Poiché un caso d'uso puó essere composto da molti scenari, e lo scenario principale ne descrive solo uno, le **estensioni** hanno lo scopo di descrivere gli altri scenari.

É possibile descrivere gli scenari alternativi sotto forma di **diramazioni** da uno scenario di base, quindi ogni dirazione corrisponderá ad un'esensione.

Un'estensione é composta **due parti**:
- La **condizione**
	- Questa va scritta come qualcosa che possa essere rilevato dal sistema o da un attore
- La **gestione**
	- Può essere riassunta in un unico passo, oppure può comprendere una sequenza di passi


Le estensioni possono essere usate per gestire almeno **tre** tipi di **situazioni** principali:
- L’attore vuole che l’esecuzione del caso d’uso proceda in modo diverso da quanto previsto nello scenario principale. 
- Il caso d’uso deve procedere diversamente da quanto previsto nello scenario principale, ed è il sistema che se ne accorge, mentre esegue un’azione o effettua una validazione.
- Un passo nello scenario principale descrive un’azione “generica” o “astratta”, mentre le estensioni relative a questo passo descrivono le possibili azioni “specifiche” o “concrete” per eseguire il passo. 

#### Notazione a due colonne
Non esiste un solo formato per rappresentare un caso d'uso.

Un formato é quello a **due colonne**, che enfatizza la **conversazione** tra **attori** e **sistema**.
![[Pasted image 20230310172604.png|550]]
> É il formato utilizzato dal corso.

Non esiste un formato migliore; alcuni preferiscono lo stile a una sola colonna, altri quello a due colonne.

### Nota: Casi d'uso concisi
Per facilitare la lettura dei requisiti, è opportuno scrivere i casi d’uso in modo **conciso**, e allo stesso tempo in modo **completo** (con una chiara indicazione di **soggetto** e **verbo** e di eventuali frasi subordinate).

Per esempio, è preferibile scrivere: “Il Sistema autentica l’Amministratore” anziché “L’Amministratore viene autenticato” (da chi?).

### Casi d'uso a scatola nera
I **casi d'uso a scatola nera** sono i casi d'uso piú comuni e consigliati.

Descrivono i **componenti**  del **sistema** e gli aspetti relativi al suo progetto, ma **non** il loro **funzionamento**.

Usando i casi d’uso a scatola nera per definire le responsabilità del sistema, è possibile specificare che **cosa** deve fare il sistema (*comportamento o requisiti funzionali*) **senza** decidere **come** lo farà (*progettazione*).

![[Pasted image 20230312152526.png]]

### Trovare i casi d'uso
I casi d’uso hanno come scopo quello di soddisfare gli obiettivi degli attori primari. Quindi, la procedura di base per trovarli è la seguente.
1. **Stabilire** i **confini** del sistema
	- Gli attori primari e di supporto sono estranei al sistema
	- Bisogna concentrarsi quindi sugli attori esterni
1. **Identificare** gli **attori primari**
	- Sono sempre esterni al sistema
2. Identificare gli **obiettivi** di ciascun **attore primario**
3. Definire i **casi d'uso**

### Vertificare l'utilitá dei casi d'uso
É difficile definire quaando un caso d'uso é valido, ma é possibile definire un livello utile per esprimere i casi d'uso.

Ci sono diverse regole pratiche applicabili.

#### Test del capo
Ci si domanda se il capo sará felice della risposta alla domanda 
> “Cosa avete fatto tutto il giorno?”

Se non lo é, il caso d'uso non supera il test.
Ció signifiuca che non è fortemente mirato a ottenere risultati il cui valore sia misurabile.

Ciò non significa che bisogna sempre ignorare i casi d’uso che non superano il test del capo, poiché potrebbe far tralasciare aspetti importanti.

#### Test EBP
La nozione di **Processo di Business Elementare** (*Elementary Business Process* o *EBP*) deriva dal settore dell’ingegneria dei processi di business.

>Il test EBP è simile al test del capo, soprattutto in termini di qualifica in termini di valore aziendale misurabile.

#### Test della dimensione
> Un caso d'uso solitamente include piú passi

Un errore comune nella modellazione dei casi d’uso è **definire** un caso d’uso a sé formato da un **singolo passo**, all’**interno** di una **sequenza** di passi correlati.

Se presenta le caratteristiche appena descritte non passa il test.

#### Violazioni ragionevoli dei test
> Benché la maggior parte dei casi d’uso identificati e analizzati per un’applicazione dovrebbe soddisfare i test proposti, ci sono delle eccezioni comuni.

Talvolta è utile scrivere **casi d’uso separati** a livello di sottofunzione che rappresentano attività secondarie o passi all’interno di un normale caso d’uso a livello EBP.

### Livelli dei casi d'uso
I casi d'uso possono essere descritti a livelli, con riferimento all'obiettivo che rappresentano.

I vari livelli sono:
- **livello di obiettivo utente**
	- consentono all’utente di **raggiungere** un proprio **obiettivo** di valore mediante un **singolo utilizzo** del **sistema**.
- **livello di sotto-funzione**
	- rappresentano solo una **funzionalità** nell’uso del sistema
	- vengono normalmente creati per mettere a fattor comune delle sequenze di passi condivise da più casi d’uso
- **livello di sommario**
	- mettono in evidenza i casi d'uso che riguardano obiettivi non raggiiungibili con un solo utilizzo del sistema
	- può essere utile per mostrare il contesto e l’ordine con cui vengono eseguiti casi d’uso a livello di obiettivo utente

### Diagrammi dei casi d'uso
UML fornisce una notazione dei diagrammi dei casi d’uso che consente di illustrare i nomi e gli attori dei casi d’uso, nonché le relazioni tra gli stessi.

![[Pasted image 20230312160303.png]]

Un diagramma dei casi d’uso rappresenta un ottimo quadro del contesto del sistema.
Costituisce un buon diagramma di contesto, che consiste nel mostrare i confini del sistema, ciò che giace al suo esterno e come esso viene utilizzato.

