#### Aufgabe 4 
Gegeben sei folgende rekursiv definierte Funktion f:
$$
f(n)=\begin{cases}1 &falls &n\leq 2\\n*f(n-1)-f(n-2) & falls& n\gt 2\end{cases}
$$
##### a) Berechnen die Funktionswerte für n=1,2,…,5 
n1:  1
n2:  1
n3:  2
n4:  7
n5:  33

##### b) Schreiben Sie eine Funktion F_r, die f rekursiv berechnet 
>[!code]- main.cpp
>```
>#include <iostream>
>using namespace std;
>
>int F_r(int n) 
>{
>	if (n <= 2) 
>	{
>		return 1;
>	}
>	else 
>	{
>		return n * F_r(n - 1) - F_r(n - 2); // 5* (4*(3*(1))))
>	}
>}
>
>int main()
>{
>	int n = 0;
>	cout << "Input a number:\n";
>	cin >> n;
>	cout << "n" << n << ": " << F_r4(n) << "\n";
>}
>```

##### c) Schreiben Sie eine Funktion F_i, die f iterativ berechnet 
>[!code]- main.cpp
>```
>#include <iostream>
>using namespace std;
>void F_i(int n) {
>    int counter = 1;
>    int memory[10];
>    while (n >= counter) {
>     if (counter <= 2) {
>          memory[counter-1] = 1;
 >    }
 >       else {
 >           memory[counter - 1] = counter * memory[counter - 2] - memory[counter - 3];
 >       }
   >     
>        std::cout << memory[counter - 1] << "\n";
 >       counter++;
   > }
>}
>
>int main()
>{
>
>    std::cout << "Exercise 4c)\n";
>    F_i(5);
>    std::cout << "\n";
>```

#### Aufgabe 5
Gegeben sei folgende rekursiv definierte Funktion f: 
$$f(n)=\begin{cases}1,&falls\ n\leq2\\n+f(n-2)&falls\ n\gt2\end{cases}$$

##### a) Berechnen die Funktionswerte für n=1,2,,…,5. 
n1:  1
n2:  1
n3:  4
n4:  5
n5:  9
##### b) Schreiben Sie eine Funktion F_r, die f rekursiv berechnet. 
>[!code]- main.cpp
>```
>#include <iostream>
>using namespace std;
>
>int F_r(int n) {
>    if (n <= 2) {
>        return 1;
>    }
>    else {
>        return n + F_r(n - 2); // n = 5+(3+(1))
>    }
>}
>
>int main()
>{
>    int n = 0;
>    cout << "Input a number:\n";
>    cin >> n;
>    cout << "n" << n << ": " << F_r(n) << "\n";
> }
>```
##### c) Schreiben Sie eine Funktion F_i, die f iterativ berechnet. 
>[!code]- main.cpp
>```
>#include <iostream>
>using namespace std;
>
>void F_i5(int n) {
>    int counter = 1;
>    int memory[100];
>
>    while (n >= counter) {
>        if (counter <= 2) {
>            memory[counter-1] = 1;
>        }
>        else {
>          //f(n)              = n       + f     (n-2)
>            memory[counter-1] = counter + memory[counter - 3];
>        }
>        std::cout << memory[counter - 1] << "\n";
>        counter++;
>    }
>}
>
>int main()
>{
>    F_i4(5);
>    cout << "\n";
>}
>```
#### Aufgabe 6 
In der Vorlesung wurde das Problem der „Türme von Hanoi behandelt. Implementieren Sie den vorgestellten rekursiven Algorithmus in C++. Dokumentieren Sie dabei jede Scheibenbewegung durch die Ausgabe: „Lege Scheibe von Turm .... auf Turm .....“ 

>[!code]- main.cpp
>```
>#include <iostream>
>using namespace std
>
>//hanoi
>/*
> * hanoi(int layers, int start, int hilf, int target, int counter)
> * cleaner Variation of recursive Tower of Hanoi
> * using an extra Variable to store the third "tower"
> * allowing it to skipp al the checks to for which tower is the new target/ if its a valid move etc
> * counter just counts the amount of moves used
> */
>int hanoi(int layers, int start, int hilf,int target,int counter) {
>    counter++;
>    if (layers == 1) {
>        std::cout << "1 von "<< start<< " nach " << target << "\n";
>        
>    }
>    else
>    {
>        // Counts down through all layers on the first tower switches target and hilf back and forth up to the "requested" layer
>        counter = hanoi(layers - 1, start, target, hilf, counter);
>
>        // moves the layer the funktion was called with
>        std::cout <<layers<< " von " << start << " nach " << target << "\n";
>
>        // moves the rest of the layers 
>        counter = hanoi(layers - 1, hilf, start, target, counter);
>       
>    }
>    return counter;
>}
>
>int main()
>{
>	//Scheiben, start, hilf, target, counter
>    int counter = hanoi(5, 1, 2, 3, 0);
>    cout << "needed " << counter << " moves\n\n";
>}
>```

##### a) Wie viele Scheibenbewegungen werden für einen Turm der Höhe 3, 4 oder 5 benötigt? 
n3:    7
n4:  15
n5:   31

##### b) Geben Sie eine Formel für die Anzahl der benötigten Scheibenbewegungen für einen Turm der Höhe n an.
Man braucht $n^2-1$ Züge. Wobei n die Anzahl der Scheiben ist.

#### Aufgabe 7
Gegeben seien zwei ganze Zahlen a und b ; finde ihren größten gemeinsamen Teiler (ggT (a,b)). Zum ggT: Für zwei nichtnegative ganze Zahlen x und y verstehen wir unter dem ggT (x,y) die größte ganze Zahl, die sowohl x als auch y derart teilt, daß ein Rest von 0 bleibt, d.h.: 
ggT (9,15)=3, ggT (16,28)=4 und ggT (119,544)=17. 

Das Prinzip des Euklidischen Algorithmus wird auch gegenseitige Wechselwegnahme genannt. Eingangsgrößen sind zwei natürliche Zahlen a und b. Bei der Berechnung verfährt man nach Euklid wie folgt:

1. Setze m = a; n = b 
2. Ist m < n, so vertausche m und n 
3. Berechne r = m - n 
4. setze m = n, n = r 
5. ist r ≠ 0 fahre fort mit Schritt 2 

Nach Ablauf des Verfahrens hat man mit m den ggT von a und b gefunden 
##### a) Handelt es sich laut Definition um einen Algorithmus? 
Ja, da es die folgenden Regeln befolgt. 
![[Before#^1da272]]

##### b) Formulieren Sie den Algorithmus in Form eines Nassi-Shneiderman- Diagramms. Die freie Software „Structorizer“ darf dabei benutzt werden. 
![[Übung2_ggTStruktogramm.png]]
##### c) Implementieren Sie den Algorithmus in C++.

>[!code]- main.cpp
>```
>#include <iostream>
>using namespace std;
>
>//ggT
>void ggt(int a, int b) {
>    int m = a;
>    int n = b;
>    if (m < n) {
>        n = a;
>        m = b;
>    }
>    while (m != 0) {
>        if (m < n) {
>            n = n - m;
>        }
>        else {
>            m = m - n;
>        }
>
>
>    }
>    std::cout << n;
>  
>}
>int main()
>{
>	ggt(9,15);
>}
>```
