# Classi

Una classe é un blueprint di un'oggetto in cui ne vengono definiti gli attributi, modificabili attraverso dei metodi.

Ogni classe contiene anche un oggetto **degenere** null privo di attributi e di informazioni, lo stesso per tutte le classi.

Una classe è eseguibile solo se contiene un main, altrimenti può solo essere utilizzata come libreria da altre classi.

La visibilità di una classe varia in base alla dichiarazione:

Dichiarazione classe | Visibilitá Classe
-----------------|-----------------
class Classe | Solo file nella stessa cartella (Package)
public class Classe | Qualsiasi package puó importare la classe

## Accesso a variabili e metodi

Solitamente gli attributi di una classe vengoni dichiarati privati per limitarne l'accesso
```java
private int Integer;
```
Per modificarne i valori vengono quindi utilizzati dei metodi pubblici che medificano o ritornano ció di cui abbiamo bisogno.

```java
//Getter
public int getInteger(){
	return Integer;
}
//setter
public int setInteger(int Integer){
	this.Integer=Integer;
}
```
### Chiamate a variabili e metodi
Per la chiamata a metodi e variabili pubbliche si usa la sintassi
```java
Classe.Attributo;
//oppure
Classe.Metodo();
```
## Costruttori
Quando andiamo a scrivere 
```java
new Integer();
```
viene costruito un nuovo oggetto di classe Integer con tutti gli attributi inizializzati ai rispettivi valori di default:

Tipo Variabile | Valore di default
--|--
byte|0
short|0
int|0
long|0L
float|0.0f
double|0.0d
char|'\u0000'(é zero)
String|null
boolean|false

(Questo ovviamente non avviene per le variabili locali)

É quindi possibile creare dei costruttori personalizzati all'interno della classe di riferimento, con il quale assegnamo i valori agli attributi della classe, utilizzando gli argomenti del metodo.

Nel caso di ambiguitá tra i nomi dei costruttori verrá usato quello di default.
```java
public Integer(int I){
	this.Integer=I;
}
```
## Confronto tra oggetti
Nel caso si decidano di confrontare due oggetti, per esempio:
```java
x==y
```
dove entrambi sono oggetti, l'alias viene ignorato e si controlla l'area di memoria occupata, quindi anche se i due oggetti hanno tutti i parametri uguali ma occupano aree di memoria diverse(per esempio sono stati creati in 2 parti diversi del codice) il risultato sará **false**.

Se si vogliono quindi confrontare i valori é necessario creare un metodo manulmente(per esempio un metodo equals):
```java
public boolean equals(int y){
	return this.Integer==y;
}
```
E chiamato poi in una maniera simile:
```java
x.equals(y.getInteger());
```
## Array di Oggetti
É possibile definire un array di oggetti 
```java
Oggetto[] ArrayOggetti;
```
definendo poi ogni suo valore con la chiamata al costruttore.
## Tipo esatto
Il tipo esatto di un oggetto è quello con cui viene istanziato
```java
B obj = new A();
```
In questo caso *obj*, essendo istanziato con il costruttore di A avrá **A** come tipo esatto.

## Tipo apparente
Il tipo esatto di un oggetto è quello con cui viene istanziato
```java
B obj = new A();
```
In questo caso *obj*, essendo dichiarato con B avrà lo stesso come tipo apparente.
## Tipi Generici
In java una classe definisce il tipo, é quindi possibile dichiarare variabili di classe con la dichiarazione della classe all'iterno delle parentesi angulate:
```java
class Classe<T>{
	T Variabile;
	
	public Classe(T Variabile){
		this.Variabile=Variabile;
	}
}
```
Quando si richiama il costruttore bisogna peró fare attenzione alla dichiarazione del tipo:
```java
new Classe<Integer>(x);
// la variabile x assumerá classe Integer quindi
```
Se non si specifica Java assume che il generico abbia tipo **Object**.
Notiamo inoltre che i tipi primitivi int,bool e double non sono classi, Java quindi ci fornisce i wrapper Integer, Double e Boolean.
## Estensioni di classi
Le estensioni consentono di aggiungere, riutilizzare, rendere pubblici metodi e attributi, oltre che sovrascrivere metodi.

Per estendere una classe scriviamo:
```java
class Class2 extends Class1{
	private int Class2;
}
```
e nel costruttore aggiungeremo la chiamata al costruttore della sovraclasse(o super):
```java
public Class2(int Class2,int Class1){
	super(Class1);
	this.Class2=Class2;
}
```
in mancanza di questa clausola verra chiamato il costruttore di default 
```java
super();
```
É comunque possibile chiamare il metodo della sovraclasse nonostante questo sia stato sovrascritto(override):
```java
super.metodo();
```

### Attributi protetti
In molti casi quando si estende una classe, si cambia **private** con **protected** per consentirne l'accesso all'interno del package e nelle sue sottoclassi, ma in nessun altro caso.
```java
protected Attributo;
```
### Overriding di un metodo
Dal momento che una classe child **eredita** i metodi di una classe parent, può presentarsi il caso in cui entrambe le classi hanno lo stesso metodo(stessa signature).

In questo caso si parla di **overriding** di un metodo. L'oggetto invocante del metodo eseguirà il metodo *più vicino*, gerarchicamente, alla classe dell'oggetto stesso.
## Binding di un metodo
Per Binding si intende "collegare" una chiamata del metodo al "corpo del metodo" vero e proprio
```java
A obj = new A();
obj.abc();
```
Ad esempio, in questo caso, il Binding si riferisce al trovare l'esatto corpo del metodo **abc()**.
### Static Binding
Il Binding Statico viene effettuato in fase di compilazione.
I metodi Final, Static e Private vengono "vincolati" staticamente, rendendo impossibile l'*override*, quindi andrá in esecuzione il metodo della sovraclasse.
Lo Static Binding migliora inoltre le performance del programma.
### Dinamic Binding
Il Binding Dinamico avviene al momento dell'esecuzione(run-time), poiché in fase di compilazione il programma non conosce il tipo esatto dell'oggetto, rendendo possibile l'override.

Nel caso di metodi statici 
#### Esempi di Binding dinamico e statico
###### Binding Statico
```java
class Parent{
	public static void print(){
		System.out.println("I'm a static parent method :D");
	}
}

class Child extends Parent{
	public static void print(){
		System.out.println("I'm a static child method :D");
	}
}

public class Main{
	public static void main(String[] args){
		Parent a = new Parent();
		Parent b = new Child();
		a.print();
		b.print();
	}
}
```
Output:
```text
I'm a static parent method :D
I'm a static parent method :D
```
###### Binding Dinamico
 ```java
class Parent{
	public void print(){
		System.out.println("I'm a non-static parent method :D");
	}
}

class Child extends Parent{
	public void print(){
		System.out.println("I'm a non-static child method :D");
	}
}

class Main{
	public static void main(String[] args){
		Parent a = new Parent();//Oggetto di tipo Parent
		Parent b = new Child();//Oggetto di tipo Child
		a.print();
		b.print();
	}
}
```
Output:
```text
I'm a non-static parent method :D
I'm a non-static child method :D
```
### Upcasting
Rifacendoci all'esempio di prima, ogni oggetto di Tipo Class2 sará anche considerato come di tipo Class1, ma non viceversa.
Questo é possibile perché Class2 ha tutti gli attributi di Class1 piú i suoi attributi. Per ignorare gli attributi di una sottoclasse si fá un'operazione definita **upcasting**, trattando un'oggetto di una sottoclasse come se fosse un oggetto del suo tipo base(viene fatto in automatico da Java).
### Downcasting
Il downcasting é l'operazione inversa all'upcasting, ed é consentita solo se c'é una possibilitá che abbia successo. Se il downcast fallisce genera una **ClassCastException** e termina il programma.
#### Esempi di Downcasting
```java
Object o = getSomeObject(),
String s = (String) o;
```
Questo é possibile perché** o** potrebbe riferisi ad una stringa.
```java
Object o = new Object();
String s = (String) o;
```
Questo fallisce perché **o ** fa riferimento ad un oggetto.
```java
Object o = "a String";
String s = (String) o;
```
Questo é permesso perché **o** fa riferimento ad una stringa.
## Classi Astratte
Una classe astratta é una classe attraverso la quale non é possibile creare oggetti.

Si definisco nella seguente maniera:
```java
abstract class Classe{}
```
e possono contenere al proprio interno metodi astratti, senza corpo quindi:
```java
public abstract void Metodo();
```
Una classe astratta puó contenere metodo concreti, ma una classe concreta **non** puó contenere metodi astratti.

Se una classe ne estende una astratta, quella deve sovrascrivere tutti i medodi al suo interno.

Se si chiama un metodo della classe astratta, prenderá il primo metodo utilizzabile(di una classe concreta che la implementa).
### Interfacce
Un'**interfaccia** é una classe astratta, con metodi astratti senza alcuna implementazione né attributi.

Un'interfaccia é definita nella seguente maniera:
```java
interface Interfaccia{}
```
ed é estesa in quest'altra:
```java
interfaccia2 implements Interfaccia{}
```
Per implementare un'interfaccia é necessario sovrascrivere tutti i suoi metodi astratti con altri concreti.
Una classe java puó estenderne al massimo un'altra, ma puó implementarne quante ne vuole:
```java
Interfaccia implements A,B,C,D{}
```
Questo é possibile perché le interfacce non forniscono versioni concrete dei metodi, evitando qualsiasi conflitto di ereditarietá.

Se una classe Astratta implementa un'interfaccia, questa non é tenuta a fornire un'implementazione per tutti i metodi di un'interfaccia.
## Generi vincolati
Quando una classe con un tipo generico estende una classe o un'interfaccia, come ad esempio:
```java
class Estesa<T extends I>{}
```
potremmo usare i metodi di I, ma dovremmo implementarli tutti.
Diremo quindi che T é un genere vincolato.
## Eccezioni
Una eccezione in Java è un oggetto della classe Exception e viene usato per segnalare una situazione che il programma non sa gestire.
Essi possono essere causati da errori **interni** , come ad esempio la *ArrayIndexOutOfBOundException*, dette non controllate, **esterni**, come il *FileNotFoundException*, dette controllate.

Ci sono poi gli **errori**, che sono eccezioni particolarmente gravi, come quelle generate da un **assert**.

In generale le eccezioni seguono la seguente gerarchia:
![Exceptions1](https://www.tutorialspoint.com/java/images/exceptions1.jpg)

## Cose inutili che non servono all'esame ma sono interessanti

### Blocchi d'istanza
Sono dei blocchi di codice quando un oggetto viene creato, e viene invocato prima del costruttore.
```java
{
	System.out.println("Istance block")
}
```
Assomigliano un pó ad un cavaliere senza testa e la loro utilitá mi é ancora sconosciuta, un pó come la Ricorsione per Peter, o Peter per Peter.

### Blocchi statici
Sono dei blocchi di codice definiti in una classe che vengono eseguiti quando la classe viene caricata sulla JVM
```java
static{
	System.out.println("Static Block");
}
```
(Stesso commento di sopra)
#### Esempio di implementazione delle cose sopra citate
```java
class Test{
	{
		System.out.println("Istance block");
	}
	static{
		System.out.println("Static Block");
	}
	Test(){
		System.out.println("ciao");
	}
}
class Main{
	public static void main(String\[\] args) {
		Test A = new Test();
		Test B = new Test();
	}
}
```
Output:
```text
Static Block
Istance block
ciao
Istance block
ciao
```
### Variabili statiche 
Quando si dichiara uan variabile statica all'interno di una classe, anche se si creano piú oggetti dello stesso tipo, punteranno sempre alla setssa locazione della variabile anziché crearne una nuova in memoria
```java
static int A=0;
```
### Unicode come caratteri
In java si possono usare caratteri Unicode come lettere vere e proprie, usando una sequenza predefinita:
* Un backslash
* Una 'u' o piú(opzionali)
* Un numero esadecimale a 4 cifre
Es: *\u0021*
Si possono anche dichiare variabili con questo standard
```java
char ch = '\utea';
```
### Divisione per 0
In Java, se dividiamo un doble, un float o un long per 0 otteniamo Infinity se quyesto é positivo o -Infinity se questo é negativo.

Se proviamo a dividere un integer per 0 otteniamo NaN(Not a Number), oppure un java.lang.ArithmeticException.
### Stringhe e heap
Quando creiamo una nuova varibile di tipo String con le doppie virgolette, viene controllato in automatico se lo stesso valore é presente nella costant pool delle Stringhe, se viene trovata ritorna un riferimento altrimenti ne mette una copia nella pool delle costanti.
### strictfp
In java non si puó usare la parola strictfp perché viene usata come modificatore per il calcolo dei numeri in virgola mobile.
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

# Metodi node Prefatti
## Included
Verifica se un elemento é incluso in una lista
### Iterativo
```java
public boolean Included(Node n,int x){
	while(n!=null){
		if(n.getElem()==x){
			return true;
		}
		n=n.getNext();
	}
	return false;
}
```
### Ricorsivo
```java
public static boolean IncludedRec(Node n,int x){
	if(n.getNext()==null){
		return n.getElem()==x;
	}else{
		return n.getElem()==x || IncludedRec(n.getNext(),x);
	}
}
```
## DeleteFirst 
```java
public static Node DeleteFirstIstance(Node n,int x){
        Node prev=null;
        Node act=n;
        while(act!=null){
            if(act.getElem()==x&&prev!=null){
                prev.setNext(act.getNext());
                prev=act;
                act=act.getNext();
                return n;
            }else if(act.getElem()==x&&prev==null){
                n=n.getNext();
                act=act.getNext();
                return n;
            }else{
                prev=act;
                act=act.getNext();
            }
            
        }
        return n;
    }
```
## Delete All Istances
Cancella tutte le istanze di un numero x da una lista
```java
public static Node DeleteAllIstances(Node n,int x){
	Node prev=null;
	Node act=n;
	while(act!=null){
		if(act.getElem()==x&&prev!=null){
			prev.setNext(act.getNext());
			prev=act;
			act=act.getNext();
		}else if(act.getElem()==x&&prev==null){
			n=n.getNext();
			act=act.getNext();
		}else{
			prev=act;
			act=act.getNext();
		}
	}
	return n;
}
```
## DeleteLast
Cancella l'ultima istanza di un interto x
```java
public static Node DeleteLastIstance(Node n,int x){
        assert Included(n,x);
        Node flag=n;
        Node act=n;
        Node prev=null;
        Node prev_last=null;
        while(act!=null){
            if(act.getElem()==x&&prev!=null){
                prev_last=prev;
            }else if(act.getElem()==x&&prev==null){
                flag=act;
            }
            prev=act;
            act=act.getNext();
        }
        if(prev_last==null){
            return flag.getNext();
        }else{
            prev_last.setNext(flag.getNext());
        }
        return n;
    }
```
## CountIstances
Conta tutte le istanze di un intero
### Iterativo 
```java
public static int CountIstances(Node n, int x){
        int c=0;
        while(n!=null){
            if(n.getElem()==x){
                c++;
            }
            n=n.getNext();
        }
        return c;
    }
```
### Ricorsivo
```java
public static int CountIstancesRec(Node n, int x){
        if(n==null){
            return 0;
        }else{
            if(n.getElem()==x){
                return 1+CountIstances(n.getNext(), x);
            }else{
                return 0+CountIstances(n.getNext(),x);
            }
        }
    }
```
## Union Lists
```java
public static boolean Union(Node n, Node p){
        if(n!=null){
            while(n.getNext()!=null){
                n=n.getNext();
            }
            n.setNext(p);
            return true;
        }
        return false;
    }
```
## Add After
Inserisce dopo un intero x un'altro intero y
```java
public static Node InsertAfter(Node n,int x, int y){
        Node Act=n;
        while(Act!=null){
            if(Act.getElem()==x){
                Act.setNext(new Node(y,Act.getNext()));
            }
            Act=Act.getNext();
        }
        return n;
    }
```
## Reverse
Ritorna una lista inversa ripetto a quella della chiamata
```java
public static Node reverseRec(Node n){
        if(n==null){
            return null;
        }else{
            Node c=null;
            for(c=n;c.getNext()!=null;c=c.getNext()){}
            return new Node(c.getElem(),reverseRec(n.getNext()));
        }
    }
```
## Translate
Trasla una lista di **t** posizioni 
```java
public static Node translate(Node n, int t){
        Node head =n;
        Node NewHead=null,prevNewHead=null;
        for(int c=t;c!=0;c--){
            prevNewHead=n;
            n=n.getNext();
            if(n==null){
                n=head;
            }
        }
        NewHead=n;
        while(n.getNext()!=null){
            n=n.getNext();
        }
        n.setNext(head);
        if(prevNewHead!=null){
            prevNewHead.setNext(null);
        }   
        return NewHead;
    }
```
# Metodi List
## Delete con .equals(x)
```java
public void delete(int x) {
        Node<T> tmp = first;
        Node<T> prev = null;
		while (tmp != null) {
            if (tmp.getElem().equals(x) {
                if (prev == null) {
                    this.first = first.getNext();
                } else {
                    prev.setNext(tmp.getNext());
                }
            } else {
                prev = tmp;
            }
            tmp = tmp.getNext();
        }
    }
```
# Santino sul binding
- Se una classe astratta implementa un'interfaccia, questa non deve fornire un'implementazione dei metodi per forza
-  Il controllo sulla presenza di metodi avviene prima sul controllo della classe apparente, se questo é presente viene controlla la classe effettiva, altrimenti questa viene ignorata
 - Il casting cambia il tipo apparente
 - Nel caso di classi astratte che implementano interfacce,I controlli dei metodi vengono effettuati anche nelle superclassi
 - Non si possono istanziare oggetti astratti o interfacce
 - Il tipo apparente puó essere una classe astratta o pure un'interfaccia
 - Tipo esatto e Apparente devono avre una qualche correlazione(Estensione o implementazione, anche a catena)
 - Negli argomenti di un metodo, se é possibile viene effettuato un casting automatico che non permane(temporaneo), osservando il tipo apparente
 - This fa riferimento al tipo apparente
 - Object é l'oggetto generico padre