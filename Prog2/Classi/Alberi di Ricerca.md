# Alberi binari di ricerca
Sono una struttura dati dinamica e che consentono un accesso veloce alle informazioni necessarie.

Un'albero puó essere vuoto, e quindi essere un'oggeto di tipo Leaf(Estensione di Tree), oppure essere un'oggetto non vuoto di tipo Branch(sempre estensione di Tree).

Un brach puó inoltre rappresentare la radice dell'albero, con un brach sinistro e destro(detti anche childs).

Inoltre in un'albero non ci sono nodi ripetuti.
## Classe astratta di base
Tutti i metodi sono dinamici poiché ad ogni modifica cambiamo la struttura dell'albero.
```java
public abstract class Tree { 
	public abstract boolean empty();
	public abstract int max(); 
	public abstract boolean contains(int x);
	public abstract Tree insert(int x);
	public abstract Tree remove(int x);
	protected abstract String toStringAux(String prefix, String root, String left, String right);
	public String toString(){ return toStringAux("","\_\_\_","   ","   ");}
}
```

## Sottoclasse Leaf
La sottoclasse Leaf rappresenta un albero vuoto, senza attributi, this sará quindi un oggetto di tipo Leaf, vuoto anch'esso.

Poiché la foglia é considerato un albero vuoto il suo costruttore non assegna niente
```java
public Leaf(){}
```
e anche gli altri metodi di controllo seguono lo stesso principio:
```java
public boolean empty(){
	return true; //una foglia é sempre un albero vuoto
}
public int max(){
	assert false; //É sbagliato chiedere il massimo di un albero vuoto
	return 0;
}
public boolean contains(int x){
	return false; //un'oggetto vuoto non contiene nulla
}
public Tree remove(int x){
	return this; //non c'é nulla da rimuovere
}

```
Metodo ausiliario di Branch.Insert
```java
public Tree insert(int x){
	return new Branch(x, this, this);//usiamo this per non creare altri oggetti vuoti
}
```

## Sottoclasse Branch


```java
private int elem; 
private Tree left; 
private Tree right; 

public Branch(int elem, Tree left, Tree right){
	this.elem = elem;
	this.left = left; 
	this.right = right;
}
```
A differenza delle foglie, un branch non sará mai vuoto:
```java
public boolean empty(){ 
	return false;
}
```
Il metodo restituisce il numero piú grande presente nella struttura, se il right child é vuoto vuol dire che la radice é il max, altrimenti continua a scorrere l'albero
```java
public int max(){
	return right.empty() ? elem : right.max(); //operatore ternario
}
```
Il metodo contains cotrolla se un integer x é presente nella struttura,il controllo avviene su elem, se é falso guarda se é piú grande o piú piccolo, e decide se proseguire verso sinistra o destra:
```java
public boolean contains(int x){
	if (x == elem){	// x é elem
		return true;
	} 
	else if (x < elem){	//x é piú piccolo di elem
		return left.contains(x);
	}else{
		return right.contains(x);	//x é piú grande di elem
	} 

 }
```
Il metodo insert permette di inserire un nuovo oggetto di Tipo Branch nella struttura, ancdo a scorrere innanzitutto l'albero fino a trovare la posizione adatta, che peró é una Leaf, ma Leaf.Insert chiama il costruttore di Branch, ritornando il riferimento all'oggetto, 
```java
public Tree insert(int x){ 
	if (x < elem){
		left = left.insert(x);
	}else if (x > elem){
		right = right.insert(x);
	} 
	return this;
}
```
Il metodo remove
```java
public Tree remove(int x){
	if (x == elem){ 
		if (left.empty()){
			return right;
		}else if (right.empty()){
			return left;
		}else{
			elem = left.max();
			left = left.remove(elem); 
			return this;
			}
	}else if (x < elem) {
		left = left.remove(x); 
		return this;
	}else{
		right = right.remove(x); 
		return this;
	}
}
```

