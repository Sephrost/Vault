## Contratti delle operazioni di sistema
I **contratti** sono lo **strumento** utilizzato per **descrivere** in **modo dettagliato** come i cambiamenti **rischiesti** per compiere un'**operazione** di sistema senza descrivere come questi debbano essere ottenuti.

Essi sono parte del Modello dei casi d'uso, poiché forniscono maggiori dettagli sull'effetto delle operazioni di sistema relative ad un caso d'uso. Infatti usano pre e post condizioni per **descrivere** i **cambiamenti** agli **oggetti** un modello di dominio.

### Schema di un contratto
![[Pasted image 20230419155530.png]]

### Operazione di sistema
Sono le operazioni che il sistema offre nella sua interfaccia pubblica.
Esse hanno un **nome** univoco che le contraddistingue e una **serie** di **parametri** necessari al sistema per compiere le operazioni richieste.

### Post-condizioni
Le post-condizioni **descrivono** i **cambiamenti** nello stato degli oggetti nel modello di dominio. 
Sono un'**osservazione** sullo stato degli oggetti al termine dell'operazione, e non descrivono come questi cambino durnate essa.

le post-condizioni rientrano nelle seguenti **categorie**:
- **Creazione** o **cancellazione** di **oggetto** (ovvero, dell’istanza di una classe).
- **Formazione** o **rottura** di **collegamento** (istanza di un’associazione).
- **Cambiamento** del **valore** di un attributo.

> Le post-condizioni di cancellazione di oggetto sono le più rare.

Le post-condizioni **SEMPRE** vanno espresse con un **verbo al passato**.

### Aggiornamento del modello di dominio
Durante la creazione di contratti é possibile che sia necessario modificare il modello di nominio, aggiungendo classi, attributi e associazioni. É importante ricordare che tutti gli elaborati sono parziali nei metodi iterativi ed evolutivi ed é quindi possibile effettuare le modifiche necessarie.

### Scrivere i contratti
Scaletta per scrivere i contratti:
1. **Identificare** le **operazioni** di sistema dagli SSD
2. **Creare** un **contratto** per le operazioni di sistema complesse o i cui effetti sono probabilmente sottili, o che non sono chiare dai casi d’uso.
3. Per descrivere le post-condizioni si utilizzino le seguenti categorie:
	1. **creazione** o **cancellazione** di oggetto (o istanza)
	2. **formazione** o **rottura** di **collegamento**
	3. **modifica** di **attributo**

Si ricordi inoltre che:
- Le post condizioni vanno scritte in **maniera dichiarativa**, in forma verbale al passato e passiva(*é stato*)
- Ci si ricordi di **stabilire** i **collegamenti** necessari tra oggetti esistenti o con quelli appena creati
	- Questo é l'errore piú comune, prestare particolare attenzione.