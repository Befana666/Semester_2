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

>[!code]- stack.h
>```
>#pragma once
>
>#include <iostream>
>using namespace std;
>
>template <class item_type>
>
>class Stack {
>	struct node {
>		item_type item;// thats 3 aber müsste das dann nicht auch node sein
>		node* nextItem;//thats 2
>	};
>private:
>	//shows the earliest aka last item
>	node* tail;//thats 3
>	int itemCount;
>
>public: 
>	Stack();
>	~Stack();
>
>	//Adds new item to stack
>	void push(item_type&r);
>	item_type pop();
>	item_type top();
>	int length();
>	bool empty();
>};
>```

>[!code]- stack.cpp
>```
>#pragma once
>
>#include "stack.h";
>
>template <class item_type>
>
>Stack<item_type>::Stack() {
>	/*
>	* So technically the naming here is very confusing.
>	* itemCounter counts the items we Created set to 0 here cuz no items on stack
>	* tail is set to nullptr, tail is here technically the head it shows the top most item
>	*/
>	itemCount = 0;
>	//There is no other
>	tail = nullptr;
>}
>
>template <class item_type>
>Stack<item_type>::~Stack() {
>	/*
>	* Here we just call pop till the empty method
>	* returns true
>	*/
>	while (!empty()) {
>		pop();
>	}
>}
>
>template <class item_type>
>void Stack<item_type>::push(item_type& r) {
>
>	/*
>	*This one gave me grey hairs.
>	* First we create a temp node
>	* and assing the new value to it.
>	* then we set the nextItem value to the tail 
>	* and tail gets the temp node in total assigned
>	*/
>	node* temp = new node;
>	temp->item = r;
>	temp->nextItem = tail;
>	tail = temp;
>
>	itemCount += 1;
>
>}
>
>template <class item_type>
>item_type Stack<item_type>::pop() {
>	/*
>	* If its not empty 
>	* we again make a temp node 
>	* set tail to temps next item 
>	* and then we delete temp but 
>	* before we do that we save the value
>	* of temp to return it
>	*/
>	if (!empty()) {
>		node* temp = tail;
>		tail = temp->nextItem;
>		itemCount -= 1;
>		item_type value = temp->item;
>		delete temp;
>		return value;
>	}
>
>}
>
>template <class item_type>
>item_type Stack<item_type>::top() {
>	/*
>	* by far the easiest just returns top
>	*/
>	if (!empty()) {
>		return tail->item;
>	}
>}
>
>template <class item_type>
>int Stack<item_type>::length() {
>	/*
>	* lied this is easier just return itemCount
>	*/
>	return itemCount;
>}
>
>template <class item_type>
>bool Stack<item_type>::empty() {
>	/*
>	* this also pretty easy
>	*/
>	if (itemCount == 0)
>		return true;
>	else
>		return false;
>}
>```

>[!code]- main.cpp
>```
>#include "stack.cpp"
>
>int main()
>{
>    Stack <int> st;
>
>    for (int j = 0; j < 5;j++)
>        st.push(j);
>
>    //Tests pop Method
>    cout << "Return of pop: " << st.pop() << "\n";
>
>    //Tests top Method
>    cout << "Return of top: " << st.top() << "\n";
>}
>```

##### b) Ergänzen Sie folgende Skizze für die Operationen push und pop. Was passiert bei einer leeren Liste?

  ![[Übung 6.canvas]]
#### Aufgabe 21

In der Vorlesung wurde ein Algorithmus zur Konvertierung eines Ausdrucks von Infix- in Postfixnotation mit Hilfe eines Stacks angegeben. Implementieren Sie diesen Algorithmus mit Hilfe der Schnittstellenfunktionen des ADT Stack aus Aufgabe 20.

>[!code]- main.cpp
>```
>int prio(char op) {
>    if (op == '+' || op == '-') return 1;
>    if (op == '*' || op == '/') return 2;
>    return 0;
>}
>
>void infixToPostfix() {
>    Stack <char> inToPost;
>
>    cout << "\nWrite (4*8)+8+(4/2) as Postfix Notation. \n";
>    string infix = "(4*8)+8+(4/2)";
>    string postfix;
>
>    for (auto letter : infix) {
>        if (isdigit(letter)) {
>            postfix = postfix + letter;
>        }
>        else if (letter == '(') {
>            inToPost.push(letter);
>        }
>        else if (letter == ')') {
>            while (inToPost.top() != '(') {
>                if (inToPost.top() != ')') {
>                    postfix = postfix + inToPost.pop();
>                }
>            }
>            inToPost.pop();
>
>        }
>        else {
>            while (prio(letter) >= prio(inToPost.top()) && inToPost.length() != 0) {
>                if (inToPost.top() == '(') {
>
>                    break;
>                }
>                else {
>                    postfix = postfix + inToPost.pop();
>
>                }
>            }
>            inToPost.push(letter);
>
>        }
>    }
>    while (!inToPost.empty())
>        postfix = postfix + inToPost.pop();
>    cout << "Postfixnotation is " << postfix << "\n";
>}
>```
#### Aufgabe 22

In der Vorlesung wurde ein Algorithmus zur Auswertung eines Ausdrucks in Postfixnotation mit Hilfe eines Stacks angegeben. Implementieren Sie diesen Algorithmus mit Hilfe der Schnittstellenfunktionen des ADT Stack aus Aufgabe 20.

>[!code]- main.cpp
>```
>void postfixToInfix()
>{
>    Stack <int> postToIn;
>
>    string postfix = "48*8+42/+";
>    string infix;
>
>    for (auto letter : postfix) {
>        if (isdigit(letter)) {
>            int number = letter - '0';
>
>            postToIn.push(number);
>        }
>        else {
>            cout << letter;
>
>            int num2 = postToIn.pop();
>            int num1 = postToIn.pop();
>
>            int num3;
>
>            if (letter == '+')
>            {
>                num3 = (num1 + num2);
>            }
>            else if (letter == '-')
>            {
>                num3 = (num1 - num2);
>
>            }
>            else if (letter == '*')
>            {
>                num3 = (num1 * num2);
>
>            }
>            else if (letter == '/')
>            {
>                num3 = (num1 / num2);
>            }
>            else {}
>            postToIn.push(num3);
>        }
>    }
>    cout << "Ergebnis: " << postToIn.pop();
>}
>```
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


  
  

