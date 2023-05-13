Il cifrario **Advanced Encryption Standard**(*AES*) é un cifrario simmetrico a blocchi pubblicato dal NIST nel 2001 per poter sostituire DES, diventando il cifrario simmetrico piú diffuso.

Il cifrario prende in input un **messaggio** in chiaro di **128 bit** e una **chiave** di **128**,**192 o 256** **bit** per produrre un messaggio cifrato di 128 bit. Il messaggio é considerato come un **blocco unico**, rappresentato attraverso una matrice $4\times 4$ di byte.

![[Pasted image 20230511115941.png|600]]

## Struttura del cifrario
Il cifrario consiste in $N$ round, dipendenti dalla lunghezza della chiave(10 per 128 bit, 12 per 192 e 14 per 256).
Inizialmente il messaggio passa per una funzione di trasformazione **AddRoundKey**. I round, ad esclusione dell'ultimo, consistono in 4 funzioni di trasformazione:
- **SubBytes**: Usa una **s-box** per effettuare le sostituzioni byte a byte del blocco
- **ShiftRows**: una semplice permutazione
- **MixColumns**: una sostituzione che usa
- **AddRoundKey**: uno XOR binario del blocco con una parte della chiave espansa
![[Pasted image 20230511173215.png]]
Nell'ultimo round ne vengono usate soltanto 3(SubBytes,ShiftRows e AddRoundKey).
Tutte queste funzioni agiscono su byte piuttosto che su bit, trattando il messaggio come un'unico blocco di 16 byte e agendo su di esso come se fosse una matrice $4\times 4$.

### Note su $GF(2^8)$
Poiché AES agisce sui byte piuttosto che sui bit, le operazioni su di essi sono definiti nel nel campo finito $GF(2^8)$. Infatti tutti i $2^8$ possibili byte ne sono membri.

> Un campo é un'insieme nel quale é possibile svolgere le operazioni basilari(addizione,sottrazione,$\dots$) senza lasciarlo.
> Alcune esempi di campi sono $N$ e $Z$.

Le operazioni definite per $GF(2^8)$ sono
- l'addizione, attraverso uno XOR binario.
-  prodotto, in modo tale che il risultato sia sia sempre un byte.

### SubBytes
In questa fase ogni byte viene sostituito con un'altro equivalente attraverso una tabella di ricerca chaimata **s-box**, una matrice $16\times 16$ che contiene tutte le permutazioni di tutti e 256 i valori rappresentabili con un byte.
Ogni byte ha un corrispondente nella s-box: i **4 bit** piú **significativi** vengono usati per indicizzare la **riga** e i **4** bit **meno significativi** per la **colonna**.
![[Pasted image 20230511175747.png|400]]

La s-box viene generata calcolando l'inverso moltiplicativo del byte nel campo finito $GF(2^8)$ e altre operazioni. É inoltre progettatta per essere resistente agli attacchi di crittoanalisi, cercando di mantenere piccola la correlazione tra l'input e l'output e la non linearitá tra questi.

Per decifrare il messaggio viene usata una matrice inversa alla s-box, chiamata **s-box inversa**.

### ShiftRows
In quetsa fase, la matrice del messaggio viene alterata facendo scorrere circolarmente a sinistra i bit. Lo spostamento per la prima prima riga é nullo, per la seconda di 1 byte, la terza di 2 e la quarta di 3. 
Questo assicura che i 4 byte della prima colonna siano distribuiti su righe diverse.

![[Pasted image 20230511182607.png|400]]

Per decifrare il messaggio viene compiuta l'operazione inversa, chiamata **inverse ShiftRows**.

### MixColumns
In questa fase la matrice ottenuta dalla funzione precedente viene moltiplicata, in $GF(2^8)$, con una matrice costante(illustrata in foto).
![[Pasted image 20230511184030.png|500]]

MixColumns è la parte che crea diffusione in AFS. I coefficenti della matrice garantiscono un buon mixing dei byte in ogni colonna

Per invertire Mixcolumns si moltiplica la matrice prodotto per un'altra che permette di ottenere la matrice identitá, ovvero quella originale.

### AddRoundKey
In questa fase si effettua lo XOR logico tra il risultato della funzione precedente con la chiave del round. 
Se é l'utimo round il risultato é il messaggio cifrato, altrimenti é l'input del round successivo.

Per invertire quetsa operazione basta semplicemente ripetere l'operazione, poiché l'inverso dello XOR é lo XOR stesso..

### Algoritmo di espansione della chiave
L'algoritmo di espansione della chiave prende in input una chiave da 16 byte e ne produce una da 176 bytes, abbastanza da produrre una chiave di 16 byte per ogni round e l'AddRoundKey iniziale.

L'algoritmo funziona nella seguenta maniera: la chiave viene copiata nei primi 4 byte, mentre ogni byte aggiuntivo $w[i]$ dipende dal byte immediatamente precedente($w[i-1]$) e quallo alla quarta posizione precedente($w[i-4]$). Per calcolare $w[i]$ viene di solito usata una semplice funzione di XOR, ma per i byte in ogni posizione multipla di 4 ne viene usata una piú complessa.
```c
KeyExpansion (byte key[16], word w[44]) 
{ 
word temp
for (i = 0; i < 4; i++) 
	w[i] = (key[4*i], key[4*i+1], key[4*i+2], key[4*i+3]);
	
for (i = 4; i < 44; i++) { 
	temp = w[i − 1]; 
	if (i mod 4 = 0) 
		temp = SubWord (RotWord (temp)) ⊕ Rcon[i/4]; 
	w[i] = w[i−4] ⊕ temp 
} 
}
```