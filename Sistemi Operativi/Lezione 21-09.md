# Sistema operativo
Programma reattivo che media tra il codice scritto dall'utente e l'hardware, permettendo di usarne le risorse

Controlla che inoltre l'esecuzione del codice avvenga correttamente

[Todo]: Ricopiare appunti
### Evento
E' la notifica che e' occorsa qualcosa
- Eventi Hardware (Interrupt)
- Eventi Software (Trap)

Per ciascuna tipologia e' associato un **handler**, che vengono inseriti in una coda di eventi.

#### Vettore delle interruzione
Permette l'accesso all'handler, contiene i riferimenti alle istruzioni che implementano gli handler per ogni interruzione.

Ongi tipo di interruzione e' codificato con un numero, l'indice della posizione contenente l'handler necessario.

Questa porzione del sistema operativo e' chiamata **Dispatcher**.

 ## Anni 50 - IBM
 
## Anni 60 - Terminali
I terminali sono postazioni I/O, che permettono di accedere ad un elaboratore piu' potente
- Un esempio sono i thin client
### Time Sharing
Quando diventa successivamente necessario distribuire le risorse tra persone diverse non basta piu' il **SSBCS**

Permette una distribuzione delle risorse equa mantenendo il concetto di parallellismo virtuale

### File
Nasce la necessita' di rendere i dati accessibili direttamente all'utente finale

Analogamente nasce anche il concetto di **Directory**

## Anni 70 - Personal Computer
Il computer diventa accessibili a molte piu' persone, rendendo necessaria un semplificazione del SO per renderlo adatto all'uso individuale

## Avvio di un sistema operativo
Il sistema operativo viene avviato dal **Bootstrap** : Ogni processo ne avvia un'altro 

BIOS(Basic I/O System)$\to$Bootloader(Localizza il sistema operativo)$\to$Sistema Operativo

