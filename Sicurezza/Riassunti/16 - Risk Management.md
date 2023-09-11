In quest’ultima lezione parleremo di **Risk Management** (Gestione del Rischio) in ambito di sicurezza che fa parte di un concetto più grande quale il **GRC** - **Governance RiskManagament & Compliance**. 

Tutto ciò ha portato oggi le aziende ad investire in ambito di cybersicurezza.

## Rischio informatico
Il **rischio informatico** è definito come la **probabilità** che un certo **evento** rilevante per un certo insieme di **sistemi ICT** (perimetro) **accada**: tale evento avrà un **effetto negativo** (impact) sul **business** o sui **beni** di una **organizzazione**.

La natura dell’impatto e probabilità del verificarsi dell’evento determinano la gravità del rischio:
$$Gravità\;del\;rischio = Probabilità(evento)\times Peso(impact)$$
## ISO 27001
L'**ISO 27001** è lo **standard** e la **certificazione** per la gestione della sicurezza delle informazioni. Esso **Indirizza** le **gestione** del **rischio informatico** nel **contesto** generale della gestione dei **rischi aziendali**. Mira perciò alla **creazione** di **sistema di gestione** come già in altri standard(es: qualitá(ISO 9001)).


Nel caso dell’ISO 27001 parliamo di un **ISMS** - **Information Security Management System** del quale lo standard si prefigge l’obiettivo di dare i requisiti e le tecniche per mantenerlo secondo un approccio per processi.
## ISMS - Information Security Management System
É un sistema di gestione della sicurezza mirato a implementare controlli di sicurezza adeguati all’organizzazione e al perimetro individuato.

Ha in **input** i **requisiti di sicurezza** e produce in **output** i **risultati attesi** attraverso processi e azioni necessarie.

Il sistema ISMS viene **continuamente migliorato** attraverso un **modello PDCA** (*Plan-Do-Check-Act*).

![[Pasted image 20230904224416.png]]
### Termini chiave
- **Asset**: **qualunque bene** o entità che può avere un **valore** per l’**organizzazione** (es. beni fisici, persone, applicazioni informatiche).
- **Sicurezza delle informazioni**: la **protezione** delle caratteristiche di **confidenzialità**, **integrità**.
- **Controlli**: **mezzi** per **gestire** e **limitare** il **rischio** (organizzativi o tecnici).
- **Minacce** (threats): **evento** possibile, **con** un **impatto**
### Plan
La fase di **plan** è la più impegnativa poiché consiste nell’**analisi dei rischi** e nello **studio dei trattamenti** per i rischi individuati (ma non solo).

Consiste nel:
1. **Definire** il **perimetro**:
	- Perimetro fisico (edifici, risorse)
	- Anagrafica degli asset
	- Risorse tecnologiche (es. server, reti, servizi esterni)
2. **Scrivere** una «**Politica dell’ISMS**» (parte della security policy) che:
	- definisca **principi** **strategici** generali
	- tenga conto degli obblighi contrattuali e di vincoli specifici dell’organizzazione rispetto al perimetro
	- si integri con il sistema di gestione dei rischi (anche non informatici) dell’organizzazione
	- definisca i criteri per la valutazione dei rischi 
3. **Analizzare** e **valutare** il **rischio**:
	- si identificano gli asset e loro responsabili
	- si identificano le minacce (threats)
	- si identificano le contromisure esistenti (controls)
	- si identificano le vulnerabilità sfruttabili dalla minacce (vulnerabilities)
	- si identificano le tipologie di conseguenze degli incidenti
4. Trattare il rischio: 
	- applicare ulteriori controlli
	- inserire il rischio in una lista di rischi ‘accettati’
	- trasferire i rischi (es. con una assicurazione)

> Una volta conclusa questa fase sarà necessario **valutare** il **rischio residuo** **ripetendo** il **punto precedente**, ovvero si capisce quanto le nuove misure siano state utili.

5.  Ottenere **approvazione** dalla **direzione**:
	- per l’**accettazione** del **rischio residuo**
	- per l’**implementazione** dei **controlli selezionati**
6. Redigere lo «**Statement of Applicability**», con:
	- **Documento dettagliato** sull’**applicazione** dei **controlli** di sicurezza e la loro pertinenza rispetto a uno standard o una norma specifica
	- Controlli esistenti
	- Controlli aggiuntivi, selezionati in base al piano di riduzione dei rischi
	- Selezione dei controlli che verranno effettivamente attuati e delle tempistiche di attuazione, motivando tali scelte sulla base della politica dell’ISMS.
### Do 
In pratica abbiamo solo pianificato e non fatto niente(approccio a cascata).
In questa fare si procede con l'implementazione di quanto definito in precedenza:
- **Definire** un **piano di impementazione**
- **Realizzare** i **controlli** selezionati
- **Misurare** l’**efficacia** dei **controlli** realizzati
- **Attuare** un **piano** di **formazione**
- **Gestire** l’**operatività** dei **controlli** e la loro **manutenzione** ed evoluzione ordinaria
### Check
Chiaramente è necessario vedere se quanto appena implementato funziona secondo quanto stabilito in precedenza e se i livelli di rischio sono davvero diminuiti oppure no. 
Questa fase è a “lungo termine”, quasi passiva.

1. **Monitoraggio** per **rilevare** **problemi**
	- **Rilevare errori** nei sistemi informatici e in particolare in quelli modificati dai controlli implementati
	- **Identificare** gli **incidenti** di **sicurezza**
	- Verificare se le azioni intraprese per risolvere un incidente sono state efficaci
2. **Riesame proattivo**
	- **Audit di sicurezza** (es. Pentest, Assessment, interviste)
	- **Misurazione** dell’**efficacia** dei **controlli**
	 - Verifica dell’attuazione requisiti di sicurezza contenuti nelle politiche
3. **Riesame della valutazione dei rischi residui**
### Act
Sulla base di quanto scoperto nel check si apportano i miglioramenti necessari all’ISMS. Dopodiché si verifica che tali miglioramenti siano efficaci (anche qui, senza fare nulla). 

Dopo qualche anno si renderà necessario ripetere da capo tutte le fasi poiché i sistemi cambiano così come il mondo dell’informatica.
### Ottenere la certificazione
Una volta sviluppato il proprio ISMS bisogna comunicare con un organismo di certificazione, fornire il proprio statement of applicability ed illustrare l’ISMS e solo a questo punto si potrà ottenere la certificazione.

Gli organismi di certificazione sono a loro volta governati da un ente unico: **Accredia**.
La certificazione è a pagamento.