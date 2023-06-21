#### Domande libro
###### Che cosa si intende per piano di controllo basato sul controllo per  router? Inquesti casi, quando diciamo che il piano di controllo della rete e il piano dei dati sono implementati “monoliticamente,” che cosa intendiamo?
Il piano di controllo svolge il compito di instradamento di cui é responsabile il livello di rete. Per far ció ogni router collabora per fornire un trasferimento host -to-host, eseguendo l'algoritmo di instradamento.
Per implementazione monolitica intendiamo che il piano dei dati é implementato in maniera indipendente dal piano di controllo.

###### Che cosa si intende per piano di controllo basato sul controllo logicamente centralizzato? In questi casi, il piano dei dati e il piano di controllo sono implementati all’interno dello stesso dispositivo o in dispositivi separati? Perché?
Si intende che le tablle di inoltro/flusso, vengono calcolate in maniera centralizzata da un controller remoto e distribuite ai vari router. In questa maniera il piano di controllo e quello di dati sono implementati su dispositivi separati: il primo é implementato su un server centrale mentre i lsecondo su ogni altro router.