# HTML
> Hyper text Markup Language

E' un linguaggio di **markup**, e non di programmazione.

Serve a **descrivere** il **contenuto** e la **struttura** dell'informazione racchiusa nella pagina web.

La presentazione della pagina non e' compito dell'HTML, ma del **browser**, il quale riceve il documento e ne **interpreta** la formattazione in maniera sequenziale.

Il documento puo' contenere comunque informazioni strutturali.

I caratteri di *spaziatura* sono quasi sempre non significativi all’interno di un documento HTML, vengono quindi ricompattati o *ignorati*.

Essendo un linguaggio di markup consiste in una **serie di tag** memorizzati in una pagina `.html` o `.htm` (versione obsoleta).

## Struttura di base
![[Pasted image 20220920152456.png]]

### Approfondimento sui tag
Un tag puo' avere dopo il proprio nome una serie di attributi che ne specificano le modalita' della sua azione
```html
	<!-- Sinstassi <element attribute1="value1" attribute2="value2">  -->
	<a href="page.html">Next Page</a>
```
Alcuni tag non richiedono terminatore e si dicono vuoti
```html
	<!-- Esempio -->
	<hr> <!-- Riga orizzonale -->
	<img src="bunny.jpg" alt="pic from Easter">
```
### Link \<a>
i link si specificano con il tag `<a>` come nella seguenta maniera
```html
	<a href="http://www.google.com/">Google</a> 
	<a href="lectures.html">Lecture Notes</a>
```
dove l'attributo **href** spefica l'url di destinazione. Puo' essere assoluto o relativo.
#### Link interni (ancore)
![[Pasted image 20220920154616.png]]

Per i link interni si deve usare nell’attributo href il nome scelto come valore dell’attributo name, preceduto dal simbolo `#`
```html
	<a href="#art1">Articolo1</a>
	<a href="#art2">Articolo2</a>
	<a href="#art3">Articolo3</a>
```

L'ancora e' identificabile con l'attributo *name*.

