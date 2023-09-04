Gli accorgimenti di sicurezza non si devono peró fermare al livello applicativo, ma devono coprire anche le azioni dell'utente.

Per valutare queste problematiche utilizziamo la classifica **OWASP**(classifica dei problemi di sicurezza piú gravi).
## 1. Injection
Invio di codice arbitrario all'applicazione, che viene eseguito lato server.

Alcuni esempi tra i piú noti sono l'sql injection e il buffer overflow.

É possibile peró evitare attacchi di questo tipo "sanificando" l'input dell'utente.
## 2. XSS - Cross site scripting
Uno script può essere eseguito sul Browser della vittima, facendo in modo che i parametri del Browser relativi al sito target (in particolare I cookies) vengano intercettati.

Si dividono in due categorie: 
- **reflected XSS**: quello sopra descritto
- **stored XSS**: quando un'applicazione riceve un'input malevolo e lo include nelle risposte HTTP future in una faniera non sicura[1](https://portswigger.net/web-security/cross-site-scripting/stored)
## 3. Broken Authentication & session management
**Broken autentication**: l’autenticazione utente viene resa vana, ovvero un utente non autorizzato riesce ad autenticarsi.
**Broken Session management**: un utente non autorizzato riesce ad inserirsi all’interno di una sessione di un utente autorizzato.
## 4. Insecure direct object references(IDOR)
Un tipo di vulnerabilitá sul controllo degli accessi che sorge quando un'applicazione usa un'input utent per accedere agli oggetti direttamente.

Per esempio la pagina del proprio profilo utente, visualizzabile dopo l'autenticazione
``` https://insecure-website.com/customer_account?customer_number=132355``` 
effettua un riferimento diretto al database di backend, e questo rende accessibili i profili di altri utenti semplicemente modificando i valore del campo `customed_id`.
## 5. Cross site request forgery
É una vulnerabilitá che permette ad un attaccante di indurre azioni ad un utente che non aveva intenzione di compiere.

Un sito permette operazioni critiche agli utenti autorizzati previa autenticazione, durante la stessa sessione.
Lo stesso utente autorizzato apre una pagina fraudolenta in un’altra scheda, che lo porta ad richiedere una diversa operazione, all’interno della sessione autenticata:

Permette di bypassare la same-origin policy, che evita che piú pagine interferiscano tra di esse, per esempio sfruttando iframe collegati a siti malevoli.
## 6. Security Misconfiguration
Ad esempio:
1. Il framework di sviluppo non è aggiornato
2. Installo un pacchetto lato server ma non cambio gli utenti di default (es. user admin, password admin)
3. Directory listing in Apache
## 7. Insecure cryptographic storage
Ad esempio:
- Dati riservati sono memorizzati in chiaro, oppure la chiave è memorizzata in chiaro, sul server o sui backup
- Password e chiavi crittografiche deboli rispetto a guessing e cracking
- Password “unsalted”
## 8. Failure to restrict URL access
Un utente é in grado di raggiungere pagine di un sito che richiederebbero autenticazione senza autenticarsi.
## 9. Insufficient transport layer protection
- SSL solo su alcune delle pagine o componenti riservate.
- Certificati scaduti o con CA non riconosciute.
- In generale, possibilità di intercettare il traffico (es. Arp / DNS spoofing)
## 10. Unvalidated redirects and forwards
L’utente prevede delle pagine che ridirezionano l’utente verso una URL ottenuta a partire da un parametro – l’utente può cliccare su un link che lo porta al sito, ma poi lo ridireziona su un sito pericoloso.

Stessa cosa per i forward interni
## Altre vulnerabilitá
- **DOS** (OWASP top ten – entry A9 – nel 2004), es.:
	- syn flooding
	- “smurf”
- **Insufficient Anti-automation**, es.: 
	- biometrics
	- captcha
- **Phishing**
- Metodi di **autenticazione** per online banking
	es.:
	- one time passwords
	- password dispositive
	- SSL client authentication
	- autenticazione con firma elettronica
## Metologia OWASP
La top ten di OWASP viene sviluppata basandosi su questa tabella:
![[Pasted image 20230904220337.png]]

Chiaramente non è possibile trovare un threat agent né un business impact poiché sono dipendenti dalla situazione in cui ci troviamo. 

Tutte le altre variabili sono invece definite solamente dal tipo di vulnerabilità: 
- **Attack vectors**: **quanto** è **facile** **effettuare** un attacco sfruttando quella vulnerabilità. 
- **Weakness prevalence**: **quanto** è **diffusa** la vulnerabilità. 
- **Weakness detectability**: **quando** è **facile** **scoprire** la vulnerabilità. 
- **Tech impact**: **quali** sono gli **impatti tecnologici** a fronte di un attacco sfruttando quella vulnerabilità.