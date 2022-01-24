 ### Codice intermedio
 
 Stabilito che il programma da tradurre è sintatticamente corretto, il compilatore lo deve tradurre in un programma equivalente scritto in codice intermedio.
 
 Per far ció utiliziamo il bytecode di java come codice intermedio.
 
 ![[Pasted image 20220112181117.png]]
 
 Non aggiungo la spiegazione poiché giá vista ad architettura degli elaboratori.
 
 #### Comandi
 
 Nome | Significato
---|---|
BIPUSH *Byte*| Scrive un byte in cima allo stack
DUP|Duplica la parola in cima allo stack
GOTO *offset*| Diramazione incondizionata
IADD|Somma le 2 parole in cima allo stack
IAND|Sostituisce le parole in cima allo stack con il loro AND
IFEQ *offset*| (IF EQUALS (0)) Esegue una diramazione se la parola in cima allo stack è zero
IFLT *offset*|Esegue una diramazione se la parola in cima allo stack è negativa
IF_ICMPEQ *offset*| (COMPARE EQUALS) Effettua una diramazione se le 2 parole in cima allo stack sono uguali
IINC *var* *const*| Aggiunge una costante ad una variabile locale
ILOAD *var*| Scrive una variabile locale in cima allo stack
INVOKEVIRTUAL *met*| invoca un metodo
IOR|Sostituisce le 2 parole in cima allo stack con il loro OR
IRETURN|Termina il metodo restituendo un valore intero
ISTORE *var*|Memorizza la variabile in cima allo stack come una variabile locale
ISUB|Sostituisce le 2 parole in cima llo stack con la loro differenza
LDC *index*| Scrive sullo stack una costante proveniente da una porzione di memoria
NOP|Non fa niente
POP|Rimuove l'elemento in cima allo stack
SWAP|Scambia le 2 parole in cima allo stack
INEG|Nega la parola in cima allo stack
IMUL| Moltiplicazione dei 2 valori in cima allo stack
IDIV| Divisione dei 2 valori in cima allo stack
IREM| Modulo dei 2 valori in cima allo stack
IF_ICMPNE *offset*| Salta se le 2 parole in cima allo stack non sono uguali
IF_ICMPLE| flavor con il less equal $\le$
IF_ICMPGE| flavor con il less equal $\ge$
IF_ICMPLT| flavor con il less equal $\lt$
IF_ICMPGT| flavor con il less equal $\gt$
NEWARRAY|Crea un'array della lunghezza del valore sulla pila
ARRAYLENGTH| Deposita sulla pila la lunghezza dell'array presente sulla stessa
IALOAD| Carica sulla pila la posizione della parola in cima e dell'array in seconda posizione
IASTORE| Assegna il valore in cima alla posizione i(seconda) nell'array in terza posizione