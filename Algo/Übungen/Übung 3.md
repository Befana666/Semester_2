#### Aufgabe 8
Gegeben sei die harmonische Reihe ℎ𝑛 = 1 + $\frac12 +\frac13 + \frac14 +. . . + \frac1𝑛$.
##### a) Schreiben Sie ein Programm zur rekursiven Berechnung von ℎ𝑛. 
>[!code]- main.cpp
>```
>#include <iostream>
>using namespace std;
>
>double harmonicRec(double n) {
>    if (n != 1)
>        return 1 / n + harmonicRec(n - 1);
>    else
>        return 1;
>}
>
>int main()
>{
>    cout << "Harmonische Reihe Rekursive mit 4:\n";
>    cout << harmonicRec(4)<<"\n";
>}
>```

##### b) Schreiben Sie ein Programm zur iterativen Berechnung von ℎ𝑛. 
>[!code]- main.cpp
>```
>#include <iostream>
>using namespace std;
>
>double harmonicIt(double n) {
>    double harmonic;
>    for (double i = 1; i <= n; i++) {
>        if (i == 1)
>            harmonic = 1.0;
>        else
>            harmonic = harmonic + 1 / i;
>    }
>    return harmonic;
>}
>
>int main()
>
>    cout << "Harmonische Reihe Iterative mit 5:\n";
>    cout << harmonicIt(5) << "\n";
>}
>```

#### Aufgabe 9 
Die Kreiszahl Pi lässt sich auch durch folgende unendliche Reihe berechnen: 
$$𝜋 = 2 ∗ (1 + \frac13 ∗ (1 + \frac25 ∗ (1 + \frac37 ∗ (… ))))\\ bzw.$$ $$𝜋 = 2 ∗ 𝐹(1) $$
##### a) Erkennen Sie die Gesetzmäßigkeit und formulieren Sie anschließend, wie 𝐹(𝑛) mit 𝐹(𝑛 + 1) zusammenhängt. 
Die obere Zahl erhöht sich immer um 1, die untere um 2. Demnach ist der Bruch $\frac n {2n+1}$.
Es ist $1+F(n)*F(n+1)$.

##### b) Schreiben Sie eine Funktion double piRecursive(), die 𝜋 berechnet. Denken Sie bei der Implementierung an eine Abbruchbedingung! Rufen Sie die Funktion anschließend in main()wie folgt auf:
```
void main() 
{ 
	double pi = 2 * f(1);
	printf("Die ersten Stellen von Pi: %.10lf", pi); 
} 
```
>[!code]- main.cpp
>```
>#include <iostream>
>using namespace std;
>
>double pi(double n) {
>   
>    if (n == 1) {
>        return (1.0 + 1/3.0);
>    } 
>    return 1.0 + (n / (2 * n + 1.0)) * pi(n - 1);
>}
>
>int main()
>{
>    cout << "PI:\n";
>    cout << 2.0 * pi(3) << "\n";
>}
>```

#### Aufgabe 10 
Beweisen oder widerlegen Sie folgende Aussagen durch Nachprüfen der in der Vorlesung gegebenen Definition der Landauschen Symbole (limes-Definition benutzen!) 
##### a) Falls 𝑘 > 0 gilt: $𝑓(𝑛) = 𝑘𝑛^5 + 𝑛^4 \in \Omega(𝑛^5)$
Wahr

##### b) $𝑓(𝑛) = 𝑛^2 + 𝑛 \in \Theta(𝑛^3)$ 
Falsch
##### c) $𝑓(𝑛) = 9𝑛^6 + 3𝑛^3 \in O(𝑛^3)$ 
Falsch
##### d) $𝑓(𝑛) = 𝑛^3 + 𝑛^2 \in o(𝑛^3)$ 
Falsch
##### e) $𝑓(𝑛) = 𝑛 ∗ log\ 𝑛 \in o(𝑛^2)$ 
Falsch
##### f) $𝑓(𝑚) = − \frac3 2*𝑚^2 + 𝑚 − 7 \in \Omega(2𝑚)$ 
Wahr
##### g) $𝑓(𝑛) = 4 ∗ 2^𝑛 + 5𝑛^2 \in O(2𝑛)$ 
Falsch

#### Aufgabe 11 
##### a) Ist die Funktion 𝑓(𝑛) = √𝑛 in der Menge 𝑜(𝑛) enthalten? Begründen Sie Ihre Angabe durch Nachprüfen der formalen Definition von 𝑜(𝑛). (limes-Definition benutzen!) 
Wahr
$\frac{\sqrt n}{n} = \frac{1}{\sqrt n} \Rightarrow 0$
##### b) Ist die Funktion 𝑓(𝑛) = √𝑛 in der Menge 𝒪(𝑛) enthalten? Begründen Sie Ihre Angabe durch Nachprüfen der formalen Definition von 𝒪(𝑛). (limes-Definition benutzen!)
Wahr
$\frac{\sqrt n}{n}\leq 1 für n \leq 1$

##### c) Ist die Funktion 𝑓(𝑛) = √𝑛 in der Menge 𝜃(𝑛) enthalten? Begründen Sie Ihre Angabe durch Nachprüfen der formalen Definition von 𝜃(𝑛). (limes-Definition benutzen!) 
Falsch
$\frac{\sqrt n}n\Rightarrow 0$

#### Aufgabe 12 
##### a) Definieren Sie die Menge $\Omega$(n). 
$f(n) \in \Omega(n)\Leftrightarrow \exists c \gt,\ n_0:\ f(n) \geq c*n\ \  \forall n \geq$

##### b) Ist die Funktion f(n)=2n-3 in der Menge $\Omega$(n) enthalten? Begründen Sie Ihre Antwort durch formales Nachprüfen der Limes-Definition. 
Wahr
$f(n) = 2n-3\in\Omega(n)$
$\frac{1n-3}n=2-\frac3n\Rightarrow 2\gt0$

##### c) Welche Funktionen sind in der Menge L= $\Theta$(n) $\cap$ O(n) enthalten? 
$L=\Theta(n)$

##### d) Welche Funktionen sind in der Menge L= $\Omega$(n) $\cup$ O(n) enthalten? 
$L=\Omega(n)\cup O(n)$
$\rightarrow$ Enthält alle Funktionen
##### e) Welche Funktionen sind in der Menge L= $\Omega$(n) $\cup\ \Theta$(n) enthalten?
$L=\Omega(n)$
