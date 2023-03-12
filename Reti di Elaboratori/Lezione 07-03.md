#### BGP - Border Gateway Protocol
> Serve a scambiare informazioni tra AS.

I pacchetti non vengono instradati secondo uno specifico indirizzo, ma piuttosto verso prefissi CIDR che rappresentano una sottorete, o un'insieme di sottoreti.

Ogni sessione TCP viene detta **sessione BGP**.
Esse possono essere
- **sessione BGP interna (iBGP)**
	- Se la sessesione coinvolge router nello stesso AS
- **sessione BGP esterna (eBGP)**
	- Se la sessione coinvolge due sistemi autonomi

> Esistono anche sessioni BGP interne tra router interni ai sistemi autonomi.

#### Istradamento hot potato
Viene scelto il percors che ha il costo totale minore per uscire dall'autonomous system.


### Piano di controllo SDN
