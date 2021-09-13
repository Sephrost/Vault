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