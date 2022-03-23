#### Interrogazioni con conteggi 
L'algebra relazionale non prevede alcun operatore di conteggio, cosa che in SQL e' invece presente.

E' possibile al massimo fare confronti rispetto ad un'attributo(Es: Piu tuple nella stessa relazione generata attravero operatori di join).

###### Esercizi
Elencare cognome e nome dei pazienti ricoverati più di una volta
$\Pi_{Nome,Cognome}(\rho_{Ricoveri1<-Ricoveri}(Ricoveri ⋈_{Cod=Paz} Pazienti)⋈_{Ricoveri1.Paz=Ricoveri2.paz}\rho_{Ricoveri2<-Ricoveri}(Ricoveri))$

Elencare nome e cognome dei pazienti residenti in città in cui risiede almeno un medico

$\Pi_{Pazienti.Cognome,Pazienti.Nome}(Pazienti ⋈_{Pazienti.Residenza=Medici.Residenza\and }Medici)$

#### Casi particolari di join
In alcuni casi si può cercare di limitare l'ampiezza del
range della cardinalità, ma bisogna specificare meglio il Θ-join, ovvero abbandonare la generalità del Θ.

##### Equi-join
E' un caso particolare di Θ-join dove le conizioni sono tutte di eguaglianza.

In questo caso il $Θ_e$-join e' da indersi come una congiunzionei egualianza.

###### Sottocasi
- $r_1$ con partecipazione completa la join
	- Ad ogni tupla di $r_1$ trova almeno una corrispondenza in $r_2$
- $r_1$ con equi-join con $r_2$ in corrispondenza della chiave principale di $r_2$
	- Per ogni tupla di $r_1$ , si troverà al più una corrispondenza con $r_2$ , altrimenti sarebbe violato il vincolo di chiave primaria