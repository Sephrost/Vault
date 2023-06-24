#### Domande libro
###### Che cosa si intende per piano di controllo basato sul controllo per  router? Inquesti casi, quando diciamo che il piano di controllo della rete e il piano dei dati sono implementati “monoliticamente,” che cosa intendiamo?
Il piano di controllo svolge il compito di instradamento di cui é responsabile il livello di rete. Per far ció ogni router collabora per fornire un trasferimento host -to-host, eseguendo l'algoritmo di instradamento.
Per implementazione monolitica intendiamo che il piano dei dati é implementato in maniera indipendente dal piano di controllo.

###### Che cosa si intende per piano di controllo basato sul controllo logicamente centralizzato? In questi casi, il piano dei dati e il piano di controllo sono implementati all’interno dello stesso dispositivo o in dispositivi separati? Perché?
Si intende che le tablle di inoltro/flusso, vengono calcolate in maniera centralizzata da un controller remoto e distribuite ai vari router. In questa maniera il piano di controllo e quello di dati sono implementati su dispositivi separati: il primo é implementato su un server centrale mentre i lsecondo su ogni altro router.

###### Confrontate le proprietà degli algoritmi di instradamento centralizzati e distribuiti e fornite esempi di protocolli che li utilizzano.
Gli algoritmi di instradamento centralizzati necessitano di una conoscenza totale della struttura della rete, in quanto le decisioni sui costi e il percorso che un pacchetto deve seguire vengono processati in maniera centralizzata da un'unico server, mentre quelli distribuiti vengono eseguiti su ogni router in maniera distribuita, iterativa e asincrona, senza una conoscenza totale della rete iniziale.
Un esempio di algoritmo centralizzato é OSPF, mentre un'algoritmo di instradamento distribuito é BGP.

###### Qual è il problema del “conteggio all’infinito” negli algoritmi distance-vector?
Il problema del conteggio all'infinito si presenta negli algoritmi di routing distance-vector, che si presenta quando il costo di un collegamento incrementa. Gli algoritmi distance-vector convergono naturalmente, ma le buone notizie, ovvero le riduzioni di costo associati ai collegamenti, si propagano velocemente, mentre le cattive molto lentamente.
Prendiamo per esempio la seguente rete
![[Pasted image 20230622173843.png|300]]
Per instradare un pacchetto da A a C si ha un costo minimo di $4+1$ passando per B, che é lo stesso per instradare un pacchetto da C ad A.
Se il costo del collegamento A-B passasse da 4 a 60, il nodo Y rileverebbe il cambiamento, ma calcolerebbe un costo per instradare un pacchetto verso X errato, poiché Z, non essendo a conoscenza del nuovo costo, gli ha promesso di essere in grado di instradarlo attraverso di esso con costo 6 totale 6.
Quindi Y instrada per X verso Z ma Z instrada per X su Y, ottenendo un'instradamento ciclico. I vettori delle distanze di aggiorneranno, ma aggiungendo soltanto 1 al costo alla volta, richiedendo cosí molte iterazioni prima di ottenere il costo corretto.

###### È necessario che ogni sistema autonomo utilizzi lo stesso algoritmo di instradamento intra-AS? Perché o perché no?
No, ogni Sistema autonomo puó implementare un'algoritmo di instradamento Intra-AS diverso, poiché possiede autonomia amministrativa su di esso.

###### Perché i protocolli inter-AS e intra-AS utilizzati in Internet sono diversi?
I protocolli intra e inter AS sono diviersi per alcuni motivi: il primo é la scalabilitá, essendo internet una rete molto grande la scalabilitá é di fondamentale importanza, ma non cosí tanto all'interno degli AS, infatti se uno di questi diventa troppo esteso si puó sempre dividere, il secondo riguarda le politiche tra AS, come evitare l'instradamento attraverso un particolare AS, queste sono meno importanti all'interno di un AS, dove si ha completo controllo. Il terzo sono le performance, infatti nell'instradamento intra-AS dominano le politiche, non presentando neanche la nozione di costo, mentre le politiche in un AS sono meno importanti permettendo quindi di ottimizzare le performance.

###### Vero o falso: quando un percorso OSPF invia le sue informazioni sullo stato dei collegamenti, le invia solo ai nodi direttamente a esso collegati. Motivate la risposta
Falso, OSPF é un protocollo di instradamento link state che fa uso di flooding per la condivisione delle informazioni ed elabora il cammino minimo grazie all'algoritmo di Dijkstra, quindi ogni nodo deve avere una mappa topologica dell'intera rete.

###### Che cosa si intende per “area” in un sistema autonomo OSPF? Perché tale concetto è stato introdotto?
Con area si intende l'estensione di un AS come l'insieme dei router che lo compongono.

###### Definite e paragonate i seguenti termini: sottorete, prefisso e rotta BGP.
- Sottorete: Una porzione di una rete piú grande che non contiene un router
- Prefisso: una porzione di un'indirizzo che identifica una o piú sottoreti
- Rotta bgb: l'insieme di un prefisso e dei suoi attributi, tra cui AS-path e NEXT-HOP

###### Come usa BGP gli attributi NEXT-HOP e AS-PATH?
L'attributo AS-PATH indica la lista degli AS attraverso i quali il messaggio eBGP é passato, mentre il messaggio NEXT-HOP referenzia l'interfaccia del primo router referenziato da AS-PATH . L'AS-PATH viene utilizzato per evitare loop all'interno delle informazioni di raggiungibilitá mentre NEXT-HOP viene utilizzato perconviguare le tabelle di inoltro.

###### Vero o falso: un router BGP, quando riceve l’annuncio di un percorso da un suo vicino, deve aggiungere la propria identità e quindi inviare tale nuovo percorso a tutti i suoi vicini. Motivate la risposta
No, invia il messaggio eBGP solo agli AS non inclusi nell'AS-PATH e inoltre puó scegliere di non aggiungersi alla lista AS-PATH.


#### Problemi Libro
###### Considerate la rete della figura illustrata di seguito. Con i costi per collegamento indicati, utilizzate l’algoritmo di Dijkstra per calcolare il percorso più breve da x a tutti i nodi della rete.
![[Pasted image 20230623180708.png]]

Passo|N'|D(y),p(y)|D(z),p(z)|D(v),p(v)|D(w),p(w)|D(u),p(u)|D(t),p(t)
--|--|--|--|--|--|--|--
0|x|6|8|3|6|$\infty$|$\infty$
1|x,v|6|8||6|6|7
2|x,v,y||8||6|6|7
3|x,v,y,w||8|||6|7
4|x,v,y,w,u||8||||7
5|x,v,y,w,u,t||8||||

###### Esaminate la rete mostrata di seguito e assumete che ciascun nodo inizialmente conosca il costo dei suoi archi incidenti. Considerate l’algoritmo distance-vector e mostrate le righe della tabella delle distanze presso il nodo z.
![[Pasted image 20230623182119.png]]

$\dots$ |u|v|x|y|z
--|--|--|--|--|--
z|$\infty$|6|2|$\infty$|0
v|$\infty$|$\infty$|$\infty$|$\infty$|$\infty$
x|$\infty$|$\infty$|$\infty$|$\infty$|$\infty$

$\dots$ |u|v|x|y|z
--|--|--|--|--|--
z|
v|1|0|6|
x|




### Esercizi Sito
#### Esercizio 1 (DIJKSTRA'S LINK STATE ALGORITHM)
Consider the 6-node network shown below, with the given link costs.
![[Pasted image 20230621154601.png]]
Using Dijkstra's algorithm, find the least cost path from source node U to all other destinations and answer the following questions

###### Fare la tabella delle distanze(non una domanda)

Passo|N'|D(v),p(v)|D(x),p(x)|D(w),p(w)|D(y),p(y)|D(z),p(z)
--|--|--|--|--|--|--
0|u|6,u|6,u|2,u|$\infty$|$\infty$
1|u,w|6,u|6,u||3,w|10,w
2|u,w,y|6,u|6,u|||6,y
3|u,w,y,v||6,u|||6,y
4|u,w,y,v,x|||||6,y
5|u,w,y,v|||||


###### What is the shortest distance to node x and what node is its predecessor? Write your answer as n,p
6,u
###### What is the shortest distance to node z and what node is its predecessor? Write your answer as n,p
6,y
###### What is the shortest distance to node w and what node is its predecessor? Write your answer as n,p
2,u

#### Esercizio 3(BELLMAN FORD DISTANCE VECTOR ALGORITHM)
Consider the 6-node network shown below, with the given link costs:
![[Pasted image 20230621184325.png]]

###### When the algorithm converges, what are the distance vectors from router 'W' to all routers? Write your answer as u,v,w,x,y

###### What are the initial distance vectors for router 'U'? Write your answer as u,v,w,x,y and if a distance is ∞, write 'x'
0,9,x,x,x

###### The phrase 'Good news travels fast' is very applicable to distance vector routing when link costs decrease; what is the name of the problem that can occur when link costs increase?
Conteggio all'infinito.
