I GoF sono piú degli “schemi di progettazione avanzata” che “principi” (come nel caso di GRASP). Ciascun design pattern descrive una soluzione progettuale comune a un problema di progettazione ricorrente

I design pattern GoF sono classificati in base al loro scopo:
- **creazionali**
	- riguarda la **creazione** di uno o più **oggetti**
- **strutturali**
	- riguarda la **rappresentazione** di **informazioni** in termini della composizione di classi e oggetti
- **comportamentali**
	- si occupa dell’interazione tra classi e oggetti per ottenere un certo comportamento

## GoF Creazionali
### Abstract factory
###### Problema
Come creare famiglie di classi correlate che implementano un’interfaccia comune?
###### Soluzione
Definire un'interfaccia factory, detta abstract factory, e una classe factory concreta per ciascuna famiglia di elementi da creare.

Opzionalmente, definire una vera classe astratta che implementa l’interfaccia factory e fornisce servizi comuni alle factory concrete che la estendono.
###### Struttura del pattern
![[Pasted image 20230609221834.png|550]]

###### Esempio 
Si supponga di gestire un negozio HI-FI,dove si vendono famiglie di prodotti con due tipi di supporti: **tape** e **CD**.
Non é possibile usare la stessa interfaccia per riprodurre entrambi.

Iniziamo definendo un'intefaccia *maker* **media** per identificare i supporti di interazione e le interfacce Player e Recorder. 
Queste rappresentano gli **Abstract products**.
![[Pasted image 20230609222640.png]]
```java
public interface Media { } 

public interface Player { 
	public void accept( Media med ); 
	public void play( ); 
} 
public interface Recorder { 
	public void accept( Media med ); 
	public void record( String sound ); 
}
```

S’implementano le classi concrete che costituiscono i prodotti delle famiglie, prima quelle su Tape
```java
public class Tape implements Media { 
	private String tape= "";
	
	public void saveOnTape(String sound) {
	    tape = sound;
	}
	public String readTape() {
	    return tape;
	}
}

public class TapeRecorder implements Recorder {
    Tape tapeInside;
    
    public void accept(Media med) {
        tapeInside = (Tape) med;
    }
    public void record(String sound) {
        if (tapeInside == null)
            System.out.println("Error: Insert a tape.");
        else
            tapeInside.saveOnTape(sound);
    }
}

public class TapePlayer implements Player {
    Tape tapeInside;
    
    public void accept(Media med) {
        tapeInside = (Tape) med;
    }
    public void play() {
        if (tapeInside == null)
            System.out.println("Error: Insert a tape.");
        else
            System.out.println(tapeInside.readTape());
    }
}
```
e successivamente quelle riguardanti i CD
```java
public class CD implements Media {
    private String track = "";
    
    public void writeOnDisk(String sound) {
        track = sound;
    }
    public String readDisk() {
        return track;
    }
}

public class CDRecorder implements Recorder {
    CD cdInside;
    
    public void accept(Media med) {
        cdInside = (CD) med;
    }
    public void record(String sound) {
        if (cdInside == null)
            System.out.println("Error: No CD.");
        else
            cDInside.writeOnDisk(sound);
    }
}

public class CDPlayer implements Player {
    CD cDInside;
    public void accept(Media med) {
        cDInside = (CD) med;
    }
    public void play() {
        if (cDInside == null)
            System.out.println("Error: No CD.");
        else
            System.out.println(cDInside.readDisk());
    }
}
```
Questi sono le classi che verranno prodotte dalla factory.


### Singleton
###### Problema
E consentita (o richiesta) esattamente una sola istanza di una classe.Gli altri oggetti hanno bisogno di un punto di accesso globale e singolo a questo oggetto.
###### Soluzione
Definisci un metodo statico (di classe) della classe che restituisce l’oggetto singleton.
###### Struttura del pattern
![[Pasted image 20230609234718.png]]
###### Implementazione 
```java
public class Singleton {
    private static Singleton instance;
    
    private Singleton() {}
    public static Singleton getInstance() {
        if (instance == null) {
            instance = new PrinterSpooler();
        }
        return instance;
    }
}
```

## GOF strutturali
### Adapter
###### Problema
Come posso gestire interfacce incompatibili?
###### Soluzione
Converti l’interfaccia originale di un componente in un’altra interfaccia, attraverso un oggetto adattatore intermedio.

###### Struttura del pattern
![[Pasted image 20230609235236.png|550]]

###### Esempio
Si vuole sviluppare un’applicazione per lavorare con oggetti geometrici, gestiti tramite interfaccia polygon. 
Si ha disposizione una classe Rectangle  che si vorrebbe riutilizzare.

![[Pasted image 20230609235349.png]]

Si puó gestire nella seguente maniera:
![[Pasted image 20230609235427.png|550]]

```java
public class Rectangle { 
private float x0, y0; 
...
}
```

```java
public interface Polygon {
    public void define(float x0, float y0, float x1, float y1,
        String color);
    public float[] getCoordinates();
    public float getSurface();
    public void setId(String id);
    public String getId();
    public String getColor();
}
```

```java
public class RectangleClassAdapter extends Rectangle implements Polygon {
    public void define(float x0, float y0, float x1, float y1,
        String color) {
        float a = x1 - x0;
        float l = y1 - y0;
        setShape(x0, y0, a, l, color);
    }
    public float getSurface() {
        return getArea();
    }
    public float[] getCoordinates() {
        float aux[] = new float[4];
        aux[0] = getOriginX();
        aux[1] = getOriginY();
        aux[2] = getOppositeCornerX();
        aux[3] = getOppositeCornerY();
        return aux;
    }
    public void setId(String id) {
        name = id;
    }
    public String getId() {
        return name;
    }
}
```

### Composite
###### Problema
Come trattare un gruppo o una struttura composta di oggetti (polimorficamente) dello stesso tipo nello stesso modo di un oggetto non composto (atomico)?
###### Soluzione
Definisci le classi per gli oggetti composti e atomici in modo che implementino la stessa interfaccia

###### Struttura del pattern
![[Pasted image 20230609235846.png|550]]
###### Esempio
Dato il seguente schema:
![[Pasted image 20230610000059.png|550]]
Si puó dare la seguente implementazione
```java
public abstract class Component {
    public String name;
    public Component(String aName) {
        name = aName;
    }
    public abstract void describe();
    public void add(Component c) throws SinglePartException {
        if (this instanceof SinglePart)
            throw new SinglePartException();
    }
    public void remove(Component c) throws SinglePartException {
        if (this instanceof SinglePart)
            throw new SinglePartException();
    }
    public Component getChild(int n) {
        return null;
    }
}
```

```java
public class SinglePart extends Component {
    public SinglePart(String aName) {
        super(aName);
    }
    public void describe() {
        System.out.println("Component: " + name);
    }
}
```

```java
public class CompoundPart extends Component {
    private Vector children;
    public CompoundPart(String aName) {
        super(aName);
        children = new Vector();
    }
    public void describe() {
        System.out.println("Component: " + name);
        System.out.println("Composed by:");
        System.out.println("{");
        int vLength = children.size();
        for (int i = 0; i < vLength; i++) {
            Component c = (Component) children.get(i);
            c.describe();
        }
        System.out.println("}");
    }
    public void add(Component c) throws SinglePartException {
        children.addElement(c);
    }
    public void remove(Component c) throws SinglePartException {
        children.removeElement(c);
    }
    public Component getChild(int n) {
        return (Component) children.elementAt(n);
    }
}
```

### Decorator
###### Problema
Come permettere di assegnare una o piú responsabilitá addizionali ad un oggetto in maniera dinamica ed evitare il problema della relazione statica?
###### Soluzione
Inglobare l’oggetto all’interno di un altro(wrapper) che aggiunge le nuove funzionalitá
###### Struttura del pattern
![[Pasted image 20230610000544.png|550]]

### GOF comportamentali
#### Observer
###### Problema
Diversi tipi di oggetti subscriber (abbonato) sono interessati ai cambiamenti di stato o agli eventi di un oggetto publisher (editore). Ciascun subscriber vuole reagire in un suo modo proprio quando il publisher genera un evento.
###### Soluzione
Definisci un’interfaccia subscriber o listener (ascoltatore). Gli oggetti subscriber implementano questa interfaccia. Il publisher registra dinamicamente i subscriber che sono interessati ai suoi eventi, e li avvisa quando si verifica un evento.
###### Struttura del pattern

![[Pasted image 20230610001623.png|550]]
#### State
###### Problema
Il comportamento di un oggetto dipende da suo stato e i suoi metodi contengono logica condizionale per casi che riflette le azioni condizionali che dipendono dallo stato. C’é un’alternativa alla logica condizionale?
###### Soluzione
Crea delle classi stato per ciascuno stato, che implementano un’interfaccia comune. Delega le operazioni che dipendono dallo stato dall’oggetto contesto all’oggetto stato corrente corrispondente. Assicura che l’oggetto contesto referenzi sempre un oggetto stato che riflette il suo stato corrente.
###### Struttura del pattern
![[Pasted image 20230610001557.png|550]]
