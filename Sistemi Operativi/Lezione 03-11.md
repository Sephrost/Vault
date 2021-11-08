##### Gestione delle richieste 
[riscrivere meglio]
Un processo $p_j$ fa' una richiesta, $n$ e' il numero di risorse, quindi possiamo rappresentare una richiesta come una array di interi con $m$ componenti, una per ciascun tipo di risorse, mettendo 1 se la risorsa e' richiesta, 0 altrimenti. 
```text
//necessarie[n][m]->necessarie[j]->pj
//disponibili[m]
if(richieste<=necessarie[j]){
	if(richieste<=disponibili){
		//ipotizza lo stato di assegnazione
		disponibili=disponibili-richieste;
		assegnate[j]=assegnate[j]+richieste;
		necessarie[j]=necessarie[j]-richieste;
		if(sicuro){
			//assegna sul serio
		}else{
			//ripristino valori precedenti
			//pj viene messo in waiting
		}
	}else{
		aspetta;
	}
}else{errore}
``` 

#### Algoritmi di rilevazione del deadlock
```text
//m=numero tipi risorse
//n=processi
//disponibili[m]
//assegnate[n][m]
//richieste[n][m]
lavoro[m];
boolean fine[n];
lavoro=disponibili;
for c in range([i;n]){
	if(assegnate[i]={0,..,0}){
		fine[i]=true;
	}else{
		fine[i]=false;
	}
}
while(esiste(i)||fine[i]==false&&richieste[i]<=lavoro){
	lavoro=lavoro+assegnate[i];
	fine[i]=true;
}
for c in range[i;n]{
	if(fine[i]==false){
		deadlock;
	}
}
```
##### Grafi di assegnazione delle risorse
###### Grafi di attesa

Puo; essere costruite a partire da un grafo di assegnazione:

quando un processo aspetta una risorsa sssegnata ad un'altro processo,[aggiungere foto]

# Ram
