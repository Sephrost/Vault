### Decidabilita'
Il problema della decidibita'e' risolubile solo positivamente.

Nel caso di automi finiti, rappresentata come un grafo, basta dimostrare che esiste un cammino che porta in uno stato di accettazione.

Per gli automi a stati finiti quindi e' sempre possibile dimostrarne la decidibilita', ma questo non e' possibile per le macchian di Turing.

![[Pasted image 20221005093257.png]]

#### Indecidibilita'(Problema della Fermata)
Se un linguaggio e' Turing-Completo, il problema della fermata e' indecidibile.

##### Un linguaggio indecidibile
Supponiamo che $H$ sia una macchina di turing dove

$$H(<M,w>)=\{^{accept\, se \,M \,accetta \,w}_{refuse \,se \, M \, non\,accetta\,w}$$

$D$ = On input $<M>$, where $M$ is a Mecchina di Turing:
1. Run $H$ on input $<M, <M>>$ -> dove $<M>$ e' la descrizione della macchina stessa, quindi applica $M$ a se stessa
2. Output the opposite of what $H$ outputs. That is, if H accepts, reject ; and if H rejects, accept .

Riassumento
$$D\{<M>\}=\{^{accept \, se M\, non\,accetta\,<M>}_{reject\,se\,M\,accetta\,<M>}$$