#### Aufgabe 16 
Beweisen Sie folgende Aussagen durch formales Nachprüfen der Definition der Landauschen Symbole aus der Vorlesung oder widerlegen Sie die Aussage durch Angabe eines Gegenbeispiels (mit Begründung, warum dies ein Gegenbeispiel ist): 
###### a) u(n) $\in$ o($n^{1/2}$) $\Rightarrow$ u(n)$*$u(n) $\in$ O(n) 
	wahr 

Behauptung$$ u(n)*u(n)\in O(n) lim u(n)*(un)/n \leq c \in R$$
Beweis:
$$\lim_\limits{n \to \infty} \frac{u(n)*u(n)}{n} = \lim_\limits{n \to \infty} \frac{u(n)*u(n)}{\sqrt n *\sqrt n} = \lim_\limits{n \to \infty}\frac{u(n)}{\sqrt n} * \lim_\limits{n \to \infty}\frac{u(n)}{\sqrt n} = 0*0$$
###### b) u(n) $\in$ O($n^2$ ) und v(n) $\in$ $\Theta$( $n^2$ ) $\Rightarrow$ u(n)+v(n) $\in$ O($n^2$)
	wahr
Voraussetzung:

Behauptung:
$$u(n)+v(n)\in O(n^2)\Leftrightarrow \lim_\limits{n\to\infty}\frac{u(n)+v(n)}{n^2}\leq c\in \mathbb{R}^+$$
Beweis:
$$\lim_\limits{n\to\infty}\frac{u(n)+v(n)}{n^2} = \lim_\limits{n\to\infty}\frac{u(n)}{n^2}+\lim_\limits{n\to\infty}\frac{v(n)}{n^2}\leq c_1+c_2 \in\mathbb{R}^+$$
#### Aufgabe 17 
Beweisen Sie folgende Aussagen durch formales Nachprüfen der Definition der Landauschen Symbole aus der Vorlesung oder widerlegen Sie die Aussage durch Angabe eines Gegenbeispiels (mit Begründung, warum dies ein Gegenbeispiel ist): 

###### a) u(n) $\in$  O($n^3$) , v(n) $\in$  O($n^2$) $\Rightarrow$ u(n)+n$*$v(n) $\in$  O($n^3$) 

Voraussetzung:
$$u(n)\in O(n^3) \ und\  v(n)\in O(n^2) \Leftrightarrow \lim_\limits{n \to \infty} \frac{u(n)}{n^3}\leq c_1 \in \mathbb{R}^+ \ und \ \lim_\limits{n \to \infty} \frac{v(n)}{n^2}\leq c_2 \in \mathbb{R}^+$$
 Behauptung:
 $$u(n)+v(n)\in O(n^3)\Leftrightarrow\lim_\limits{n\to\infty}\frac{u(n)+n*v(n)}{n^3}\leq c\in\mathbb{R}^+$$
 Beweis:
 $$\lim_\limits{n\to\infty}\frac{u(n)+n*v(n)}{n^3}=\lim_\limits{n\to\infty}\frac{u(n)}{n^3}+\lim_\limits{n\to\infty}\frac{v(n)}{n^2}\leq c_1+c_2\in\mathbb{R}^+$$

###### b) u(n) $\in$  Ω(n) und v(n) $\in$  $\Theta$(n) $\Rightarrow$ u(n)+v(n) $\in$  Ω(n)
wahr
Voraussetzung:
$$u(n)\in\Omega(n) \ und\  v(n)\in \Theta(n) \Leftrightarrow \lim_\limits{n \to \infty} \frac{u(n)}{n}\geq c_1 \in \mathbb{R}^+ \ und\ \lim_\limits{n \to \infty} \frac{v(n)}{n}\geq c_2 \in \mathbb{R}^+
 $$
 Behauptung:
 $$u(n)+v(n)\in\Omega(n)\Leftrightarrow\lim_\limits{n\to\infty}\frac{u(n)*v(n)}{n}\geq c\in\mathbb{R}^+$$
 Beweis:
 $$\lim_\limits{n\to\infty}\frac{u(n)+v(n)}{n}=\lim_\limits{n\to\infty}\frac{u(n)}{n}+\lim_\limits{n\to\infty}\frac{v(n)}{n}\geq c_1+c_2\in\mathbb{R}^+$$
#### Aufgabe 18
In der Vorlesung wurde die rekursive Berechnung der Fakultätsfunktion behandelt. 

```
int fact( int n) 
{ if (n<=1) return 1;
 else return n * fact (--n); // rekursiver Aufruf 
 } 
```

###### a) Bestimmen Sie die Anzahl der Multiplikationen als Funktion von n, die nötig sind, um fact(n) zu bestimmen. 

O(n-1) multiplikationenen ($5*4*3*2*1$)

###### b) Bestimmen Sie die Anzahl an Speicherplätzen, die zur Berechnung von fact(n) nötig sind. 

O(n) (n = 5,4,3,2, return 1) 

###### c) Von welcher Ordnung sind die Funktionen aus a) und b)
sind beide von der linearen ordnung(O(n))

#### Aufgabe 19
Schreiben Sie eine Fuktion fact_it, die die Fakultätsfunktion iterativ berechnet. 
```
#include <iostream>

//Berechnet Fakultät Itterative
int fact_it(int n) {

	//setzt ergebnis auf 1 (nicht null wie ichs mal wieder versucht hab)
    int fac = 1;
    
    //loop bis i die größe von n erreicht hat und multipliziere das ergebnis damit
    for (int i = 2; i <= n; i++) {
        fac = fac * i;
    }
    return fac;
}

int main()
{
    std::cout << fact_it(5);
}
```
###### a) Bestimmen Sie die Anzahl der Multiplikationen als Funktion von n, die nötig sind, um fact_it(n) zu bestimmen.

n-1
###### b) Bestimmen Sie die Anzahl an Speicherplätzen, die zur Berechnung von fact_it(n) nötig sind. 
3 Speicheplätze sind benötigt O(1)
###### c) Von welcher Ordnung sind die Funktionen aus a) und b)
a) O(n) aka linear und b) ist von der ordnung O(1) aka Konstanten Ordnung