## Schemi di traduzione 
Uno** schema di traduzione** é una grammatica in cui nel corpo delle produzione posso inserire dei frammenti di codice detti aziomi semantiche che vengono eseguiti nel momento in cui tutti i simboli alla loro sinistra sono stati riconosciuti

Produzione|Produzione+Azioni
--|--
$A\to BC$|$A\to BC\{code\}$
$A\to \epsilon$|$A\to \{Code\}$

Differenze tra regole e azioni semantiche

Regole Semantiche|Azioni Semantiche
--|--
Specificano come determinare i valori degli attributi|Solitamente specificano come determinare il valore degli attributi, ma non possono contenere codice arbitrario
Sono valutate in un ordine implicito determinato dal grafo delle dipendenze|Sono eseguite in un ordine esplicito determinato dalla loro posizione nel corpo dei produttori
Poiché valutare in un ordine arbitrario, richiedono la costruzione dell'albero sintattico annotato|

### Conversione da SDD L-attribute a SDR
Dato una SDD  L-attribuita,prendo in considerazione ogni produzione della grammatica:
1. Prima di di una variabile aggiungo un'azione semantica che calcola il valore degli attributi ereditati da esso.
2. In fondo alla produzione aggiungo una regola semantica che calcolail valore degli attributi sintetizzati della variabile in testa alla produzione