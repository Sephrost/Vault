# Sistema operativo
Programma reattivo che media tra il codice scritto dall'utente e l'hardware, permettendo di usarne le risorse

Controlla che inoltre l'esecuzione del codice avvenga correttamente

Il SO assegna le risorse ad un processo caricando i registri necessari per l'esecuzione alla cpu

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

## Gestione dei processi 
Il sistema operativo deve mandare in esecuzione il codice dei vari job, essendo qesti molteplici necessita di riconoscere gli handler contenuti nella memoria principale che permetto un cambio di contesto, salvando le informazioni relative all'esecuzione di un processo in ram(registri,...),congelandone lo stato e passando all'esecuzione di un codice differente e ripetendo il tutto fino al termine dell'esecuzione.

## Gestione della memoria principale
La cpu e' direttamente collegata alla ram, e per questo la cpu puo' accedere solo ai dati contenuti in questa, ma non i dati contenuti altrove(disco fisico,cache,...), che dovranno prima essere copiati in ram per consentirne l'accesso.

[copiare il grafico da ale]

### I Device
Con **Device** intendiamo tutto cio' che non e' ne' cpu ne' memoria.

Per interagire con i device si usano:
- controller, ovvero la parte fisica, una mini cpu dedicata
- driver, ovvero la parte software, che passa il comando al controller

Essi sono visti come risorse dalla cpu, che gli assegna.

### Archittettura
Noi lavoreremo con 1 sola cpu, cio' non preclude l'esistenza di archietetture multiprocessurali, che sfruttano il principio di parallelismo reale, affiancando quello virtuale.

L' architettura multiprocessurale ha il problema della lettura dalla memoria, che rappresenta il suo collo di bottiglia.

## Crezione di un Sistema Operativo

Oni sistema operativo deve gestire i dati in maniera efficente

### Processo 
Per poter rappresentare un processo dobbiamo innanzitutto assegnarli un idetificatore, per poter assegnare della ram od ognuno di essi, per impedire la sovrascrizione dei dati nei registri gia' assegnati ad altri.

### CPU 
Ogni cpu ha il proprio istruction set finito, che contiene le operazioni che esso e' in grado di riconoscere ed eseguire, che rappresenta il linguaggio che e' in grado di leggere.

#### Instruzioni


Le istruzioni di dividono in:
- istruzioni Utente
- istruzioni SO

##### Dual mode
Alcuni tipi di istruzione,come quella di scrittura, possono generare incosistenza dei dati oppure essere malevole, per questo si restringe le proprie possibilita' di esecuzione sono al sistema operativo. 

Quindi una parte delle istruzioni "a rischio" risulta ristretta al sistema operativo.

Per far questo si utilizza un bit detto "di modalita' ", a seconda del suo valore si puo' essere in:
- modalita' utente
- modalita' kernel

###### System Call

Per eseguire comandi a livello kernel si usa la **system call**, per far passare il bit della modalita' utente a quella di modalita' kernel ad un'istruzione.

Quanto si esegue una SC di genera un trap che causa l'esecuzione di un handler, la quale riconosce la chiamata e causa l'esecuzione di un handler specifico per la SC di riferimento.

Se la system call fallisce il processo viene reciso.

Esistono 5 tipi di system call:
- controllo dei processi
	- Terminare di un processo (exit( ))
	- Processi generati da processi (fork( ))
- gestione dei file
	- creazione file
	- lettura file 
- gestione dei device
- gestione delle informazioni
- comunicazione

[copiare whatever ha spiegato negli ultimi 20 min]