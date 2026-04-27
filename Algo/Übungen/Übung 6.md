#### Aufgabe 20

In der Vorlesung wurde eine mögliche Implementierung des ADT Stack mit Hilfe eines arrays vorgestellt.

##### a) Implementieren Sie den ADT Stack mit Hilfe einer verketteten Liste. Folgende Schnittstelle soll zur Verfügung gestellt werden:

>[!Note]- ADT Stack
>Liste mit eingeschränkten Operationen
>- es kann nur am anfang was eingefügt werden
>- Last-In-First-Out = LIFO
>  
>  s.top - liefert oberstes element
>  s.pop - entfernt oberstes Element
>  s.push - legt element auf den Stack

Good Explanation how stacks are normally used IF we dont have to fing write it ourself(Or all the websites i read to understand this bs): 

[[https://www.geeksforgeeks.org/cpp/stack-in-cpp-stl/|GeekForGeeks Stack in C++]]
[[https://www.happycoders.eu/de/algorithmen/stack-implementieren-linked-list/|Happy Coding]]
[[https://www.geeksforgeeks.org/dsa/implement-a-stack-using-singly-linked-list/|GeekForGeeks Verkettete Liste]]

Last in first out
scheiben auf nem turm
__ neues eleement, 1 alt, 2 alt ,3 alt ,4 alt ....

```
template <class item_type>

class Stack
{
    struct node
        {
            item_type item;
            node *next;
        };

    private:
        node *tail;
        int anz_items;

    public:
        Stack();
        ~Stack();
        void push(item_type &r);
        item_type pop();
        item_type top();
        int length();
        bool empty();
}
```

##### b) Ergänzen Sie folgende Skizze für die Operationen push und pop. Was passiert bei einer leeren Liste?

  ![[Übung 6.canvas]]
#### Aufgabe 21

In der Vorlesung wurde ein Algorithmus zur Konvertierung eines Ausdrucks von Infix- in Postfixnotation mit Hilfe eines Stacks angegeben. Implementieren Sie diesen Algorithmus mit Hilfe der Schnittstellenfunktionen des ADT Stack aus Aufgabe 20.

#### Aufgabe 22

In der Vorlesung wurde ein Algorithmus zur Auswertung eines Ausdrucks in Postfixnotation mit Hilfe eines Stacks angegeben. Implementieren Sie diesen Algorithmus mit Hilfe der Schnittstellenfunktionen des ADT Stack aus Aufgabe 20.

#### Aufgabe 23

#### a) Folgender Postfix-Ausdruck sei gegeben:
$$𝑎𝑏 ∗ 𝑏 + 𝑎𝑐/+$$ Wandeln Sie den Ausdruck in die Infix-Schreibweise um und berechnen Sie das Ergebnis für $𝑎 = 4,\ 𝑏 = 8 \ und \ 𝑐 = 2$

 1. ab* $\Rightarrow$ a*b = d
 2. db+ $\Rightarrow$ d+b = e
 3. ac/ $\Rightarrow$ a/c = f
 4. ef+ $\Rightarrow$ e+f

$=4*8+8+4/2$
= 32+8+2
= 42
#### b) Welche Paare aus Postfix-Notationen liefern dasselbe mathematische Ergebnis?

- $ab \ + \ c \ +$ und $abc++$
	- $a+b+c$ und $a+b+c$
	- Wahr
- $xb \ - \ c *$ und $xb \ * \ c \ -$
	- $(x-b)*c$ und $x*b-c$
	- Falsch
- $bc \ - \ x \ *$ und $bx \ * \ cx\ * \ -$
	- $(b-c)*x$ und $(b*x)-(c*x)$
	- Wahr


  
  

