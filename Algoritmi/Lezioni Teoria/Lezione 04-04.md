## Programmazione dinamica
Sia la programmazione ricorsiva che il divide-et-impera si basano sulla scomposizione ricorsiva di un problema in sottoproblemi.

Se i sottoproblemi sono indipendenti tra loro, il divide-et-impera e' efficiente, altrimenti produce tempi di elaborazione esponenziale, cosa che la programmazione dinamica evita producendo tempi polinomiali.

### Condizioni di applicabilita'
1. Sottostruttura della soluzione 
2. Sottoproblemi ripetuti

### Fasi
1. Caratterizzazione della struttura di un soluzione
2. Definizione ricorsiva della soluzione
3. Eliminare le ripetizioni mediante annotazione dei risultati semplici
	1. Puo' capitare di ripetere chiamate semplici, quindi salvo gli esisti in una struttura dati apposita(memoization) 
4. Sviluppo di un approccio bottom-up e quindi iterativo
		1. Costruisco un albero di ricorsione a partire dal basso(dal caso baso al generico), e memorizzo solo i valori di interesse