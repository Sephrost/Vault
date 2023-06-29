I problemi di ricerca fono ad ora affrontati prevedono che un solo agente interagisca con l'ambiente, ma non puó essere sempre cosí: ci possono essere degli **ambienti competitivi** sui quali interagiscono piú agenti con obiettivi contrastanti.

## Teoria dei giochi
I contesti in cui operano piú agenti con obiettivi conflittuali sono chiamati giochi.
I giochi possono essere a informazione
- **perfetta**, se gli stati del gioco sono conusciuti da tutti gli agenti
- **imperfetta**, se sono parzialmente conosciuti

### Giochi a somma zero
I giochi a somma zero sono giochi **deterministici** a turni con due giocatori aventi informazioni perfetta.
In questi giochi il guadagno di un giocatore é compesato da una perdita per l'altro.

I due giocatori sono chiamati **min** e **max**, dove max muove per primo. I giocatori alternano i propri turni finché non si raggiunge uno 
Un gioco puó essere definito da:
- un'**insieme di stati**, di cui uno iniziale
- una **funzione utilitá**, che assegna un valore numerico ad un giocatore *p* quando il gioco termina in uno stato *s*
- un **modello di transizione**, che definisce gli stati risultati dall'effettuare una mossa in uno stato

L'insieme delle azioni e dei loro risultati possono essere modellati come un grafo, a cui possiamo di nuovo un albero di ricerca.

### Minimax
Max vuole quindi trovare una sequenza d'azioni che gli permettano di vincere, cosa che Min non vuole. La funzione utilitá si puó applicare solo alle foglie, ovvero alla conclusione del gioco. É possibile calcolare peró l'utilitá per Max, misurata attraverso il **valore minimax**. 

$Minimax(s)$ puó essere calcolato come segue:
- sé il nodo é terminale $\to\;Utility(s,Max)$
- sé il nodo non é terminale e muove Max $\to\; max_{a\in Actions(s)}Minimax(s,a)$
	- Il massimo tra i valori minimax 
- sé il nodo non é terminale e muove Min $\to\; min_{a\in Actions(s)}Minimax(s,a)$
	- Il minimo tra i valori minimax

Partendo da ció é possibile definire un'algoritmo di ricerca che permetta di cercare la miglior mossa per Max, provando tutte le disponibili e cercando quella con valore Minimax maggiore.

![[Pasted image 20230612214500.png]]

É un'algoritmo di ricerca ricorsivo in profonditá.
Se l'albero é profondo $d$ e ci sono $b$ mosse legali allora
- Complessitá spaziale $O(b^d)$
- Complessitá temporale $O(bd)$

La complessitá esponenziale rende minimax non pratico per i giochi complessi, ma un pó per tutti i giochi.

#### Potatura Alpha-beta 
Come appena detto, le soluzioni di forza bruta richiedono **risorse eccessive**.
Peró é possibile **calcolare** il corretto valore **minimax** **senza esaminare ogni stato**, tagliando larghe porzioni di un'albero senza impattare sul risultato. Esaminiamo una tecnica chiamata **potatura alpha-beta**

> Questa tecnica si basa sull'osservazioni che l'esplorazione di porzioni dell'albero non avrebbero impattato sul valore restituito, a prescindere. Queste possono essere quindi "potate" . 

La potatura alpha-beta prevede l'aggiunta di due parametri aggiuntivi:
- $\alpha$, il valore della scelta migliore che abbiamo trovato finora sul cammino per Max, ovvero il valore piú alto
	- $\alpha$="almeno"
- $\beta$, il valore migliore che abbiamo trovato su un cammino per Min
	- $\beta$="al piú"

Se, ad un qualche punto della ricerca, i valori si invertono, possimo interrompere la ricerca, poiché non trovermo mai valori piú piccoli di $\beta$ e maggiori di $\alpha$.

![[Pasted image 20230612221139.png]]

L'ottimalitá di questo approccio é peró dipendente dall'ordine in cui gli stati vengono esaminati.
Se fatto ottimalmente otterremmo complessitá spaziale $O(b^{\frac{d}{2}})$.
#### Giochi con piú di due giocatori
Molti giochi hanno **piú di due giocatori**.
É possibile estendere l'idea di minimax rimpiazzando il valore di ogni nodo con un **vettore di valori** $<v_a,v_b,v_c,\dots>$(negli stati terminali sono l'utilitá per ciascuno dei giocatori).
