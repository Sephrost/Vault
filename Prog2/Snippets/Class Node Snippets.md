# Class Node Snippets
## Scorrimento Nodi
```java
Node<T> Prev=null;
Node<T> Act=first;
while(Act!=null){
	Prev=Act;
	Act=Act.getNext();
}
```
## Rimuovere un elemento
```java
//Controllo su Act
//Il precedente(Prev) sará collegato al successivo di Act
Prev.setNext(Act.getNext());
```
## Confronto tra Act e il suo successivo
```java
if(Act.getNext()!=null&&Act.getElem()>Act.getNext().getElem())
```


