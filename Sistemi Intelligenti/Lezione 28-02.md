# Risoluzione automatica di problemi

Non sempre la soluzione ad un problema é ovvia.

Possiamo rappresentare i passi necessari per la risoluzione di un problema come un **insieme** di **stati**, e la **soluzione** come il cammino che porta da uno stato iniziale ad uno stato di risoluzione.

Chiamiamo quindi questi agenti **risolutori**, e il processo comutazionale per trovare una soluzione **ricerca**.

## Problemi
Un problema di ricerca é compoststo da:
- un'insieme di **stati**, che rappresentano l'insieme di tutti le possibili condizioni in cui si trova l'ambiente
- uno stato **iniziale**
- un'insieme di stati obiettivo
- un'insieme finito di azioni applicabili dall'agente
- una **funzione successore**, che descrive il risultato di ogni azione prendendo in input stato attuale e azione
- una **funzione costo**, che associa un'azione al proprio costo, ovvero al consumo di risorse

L'insieme di stati puó essere rappresentato come un **grafo**, dove i vertici sono gli stati e gli archi sono le azioni.

### Soluzione di un problema

Una sequenza di azioni forma un cammino, e quindi una **soluzione** é un **cammino** dallo stato iniziale ad un qualsiasi stato obiettivo.

Il costo di una soluzione é quindi la somma di tutte le azioni individuali compiute dall'agente.

Una soluzione é **ottima** se ha il costo minimo tra tutte le soluzioni.

