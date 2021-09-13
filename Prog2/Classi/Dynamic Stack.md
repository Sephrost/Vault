# Dynamic stack
La casse ha come unico parametro il riferimento alla cima dello stack
```java
 private Node top;
```
Il costruttore inizializza la cima dello stack come null
```java
 public DynamicStack(){
 	top = null;
	}
```
Ogni valore viene aggiunto sulla cima(top), quindi controllando se é ==null consente di capire se lo stack é vuoto

```java
 public boolean empty(){
 	return top==null;	
	}
```
Push aggiunge un valore sulla cima dello stack, creando un nodo che ha come riferimento il blocco di memoria attualmente in cima. Se questo viene spostato anche il riferimento di muoverá di conseguenza.
```java
 public void push(int x) {
 	top = new Node(x,top);
	}
```	
Il metodo elimina il nodo in cima allo stack, ponendo la cima come il suo successivo. L'assert serve ad evitare una NullPointerException. Il metodo restituisce inoltre l'elemento rimosso.
```java
 public int pop(){
 assert !empty();
 int x = top.getElem();
 top = top.getNext();//eliminazione top
 return x;
 }
```
Il metodo ritorna l'elemento in cima allo stack.
```java 
 public int top(){
 assert !empty();
 int x = top.getElem();
 return x;
 }
```
```java
 public String toString(){
 Node temp = top; 
 String s = ""; 
 while (temp != null){ 
 s=s+" || "+temp.getElem()+"\n";
 temp=temp.getNext();
 }
 return s;
 }
 ```
 Costruttore Alternativo di DynamicStack, che aggiunge allo stack tutti i valori in range(1,n).
 ```java
 public DynamicStack(int n){
 top = null; int i = 1;
 while (i<=n){
 	top = new Node(i,top);i++;}
 }

```