### Problema della corrispondenza di Post
Vengono dati dei tipi domino non ruotabilli e ripetibili illimitatamente del tipo: 

![[Pasted image 20221024091722.png]]

L'obiettivo e' metterli in ordine in modo che sulla parte superiore ed inferiore sia preente la stessa stringa.
#### indecidibilita' del problema
definiamo $PCP=\{hP i| P is an instance of the Post Correspondence Problem with a match\}$, definiamo ora come una regola per cui il domino inizi con il primo domino $[\frac{t_1}{b_1}]$
$$MPCP = \{<P>\,|\,P\,is\,an instance of the Post Correspondence Problem
with a match that starts with the first domino\}$$
per nasconderci una macchina universale $M$.

Il construttore inizia quindi nella seguente maniera
![[Pasted image 20221024094138.png]]
