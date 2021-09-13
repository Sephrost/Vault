# Delete con .equals(x)
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
