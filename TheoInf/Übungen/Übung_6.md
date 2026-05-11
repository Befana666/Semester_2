Das SOS-Problem ist wie folgt definiert: 
		**Problem:** Sum-of-Subset (SOS)
		**Eingabe:** Natürliche Zahlen $a1, . . . , a_n$ sowie eine weitere natürliche Zahl $b$ 
		**Frage:** Gibt es eine Menge I ⊆ {1, . . . , n}, so dass $\sum\limits_{i \in I }^{\infty} {a_i}$= b? 
		       Mit anderen Worten: Gibt es Zahlen aus $\{a1, . . . , an\}$, die sich zu $b$ aufsummieren (wobei jedes ai höchstens einmal als Summand auftreten darf)?
		       
![[Extras#^b1c353|]]
#### 1. 
##### (a) Schreiben Sie in C++ eine Funktion mit dem Kopf
```
bool isGoodSolutionForSOS(int n, int* a, int b, int solutionSize, int* solution)
```
die entscheidet, ob ein gegebener Lösungskandidat einer Instanz des SOS-Problems die Instanz tatsächlich löst. 
Die SOS-Instanz ist dabei durch die Parameter $n$, $a$ und $b$ gegeben, wobei n angibt, wie viele Elemente sich in dem durch a gegebenen Array befinden. Die Potentielle Lösung ist durch solutionSize und solution gegeben, wobei solution Indizes von Elementen von $a$ enthält. Die Frage, die die Funktion beantworten soll ist, ob die Summe der Elemente aus $a$, deren Indizes in solution stehen, gerade gleich $b$ ist. 

>[!code]- main.cpp
>```
>#include <iostream>
>using namespace std;
>
>/*
>n = how many Element in Array a
>a = Array with Values
>b = Sum
>solution = subset;
>*/
>bool isGoodSolutionForSOS(int n, int* a, int b, int solutionSize, int* solution) {
>    bool isInSub = false;
>    int sum = 0;
>
>    /*Loop throught the subset array.*/
>    for (int i = 0; i < solutionSize;i++) {
>        cout << "-----------------------" << "\n";
>        cout << "-----------------------" << "\n";
>        int valueInSubset = solution[i];
>        cout << "Value i: " << valueInSubset << "\n";
>
>        /*Loop throught the Mengen array.*/
>        for (int j = 0; j < n;j++) {
>            int valueInArray = a[j];
>            cout<<"Value j: " << valueInArray << "\n";
>
>            /*Checks if the Value is inside the Mengen Array
>            if yes change value of isInSub and breaks the loop.*/
>            if (solution[i] == a[j]) {
>                cout << "It's inside the array.\n";
>                isInSub = true;
>                break;
>            }
>        }
>        /*Checks via isInSub if the Value existed inside the 
>        Mengen array 
>            if no return false its not a valid solution
>            if yes add value to sum*/
>        if (isInSub == false) {
>            return false;
>        }
>        else {
>            sum += solution[i];
>            isInSub = false;
>        }
>        cout << sum;
>    }
>    /*Check if the sum is equal b*/
>    if (sum == b) {
>        return true;
>    }
>    else {
>        return false;
>    }
>    
>}
>
>int main()
>{
>    int a[6] = {5,10,12,13,15,18};
>    int solution[2] = {12,18};
>
>  
>
>    if (isGoodSolutionForSOS(6, a, 30, 2, solution)) {
>        cout << "true";
>    }
>    else {
>        cout << "false";
>    }
>}
>```
##### (b) Schätzen Sie die Laufzeit Ihrer Funktion in Abhängigkeit von n nach oben ab! Geben Sie also eine Funktion $f: \mathbb{N} \rightarrow \mathbb{N}$ an, so dass die Anzahl der Elementaroperationen, die ausgeführt werden, wenn Ihre Funktion mit maximal $n$ Elementen in $a$ aufgerufen wird, nie $f (n)$ überschreitet. Bleiben Sie konservativ bei Ihrer Abschätzung, machen Sie also f nicht unnötig groß! Zu den Elementaroperationen bitte den Text am Ende der Aufgabenliste beachten! 
$$f(n) = n^2 \text{ or } O(n^2)$$
#### 2. 
##### (a) Schreiben Sie in C++ eine Funktion mit dem Kopf 
```
bool SOS(int n, int* a, int b)
```
Die Funktion soll genau dann true zurückgeben, wenn sich Elemente aus a finden, die sich gemäß der Definition von SOS zu b aufsummieren lassen und false sonst. Im Moodle findet sich eine Datei SOSTests.cpp, die eine Reihe Funktionen enthält, die Sie zum Testen Ihrer Lösung benutzen können. 

>[!code]- main.cpp
>```
>/*
>Look if a valid Subset exists
>*/
>bool SOS(int n, int* a, int b) {
>   
>    //loop through first array
>    for (int i = 0; i < n;i++) {
>        cout << "-----------------" << "\n";
>        int counter = 1; //counts upwards so we can skip values
>        int sum = a[i];
>
>        //loop through the array again till either
>        //Sum is bigger than target
>        //reached end of array
>        //or sum is equal target
>        for (int j = i + counter; j < n; j++) {
>            cout << "counter: " << counter << "\n";
>            int a2 = a[j];
>           
>            cout << sum << " + " << a2 << " = " << sum + a2 << "\n";
>            sum += a2;
>            if (sum == b) {
>                return true;
>            }
>            else if (sum > b) {
>                cout << "-----------------" << "\n";
>                if (i + counter < n) {
>                    j = i + counter;
>                    counter++;
>                }
>                sum = a[i];
>            }
>        }
>    }
>    return false;
>}
>
>int main()
>{
>    int a[6] = {5,10,12,13,15,18};
>    int solution[2] = {12,18};
>
>    if (SOS(6, a, 30)) {
>        cout << "true";
>    }
>    else {
>        cout << "false";
>    }
>}
>```
##### (b) Bestimmen Sie, analog zur 1. Aufgabe, die Laufzeit der von Ihnen programmierten Funktion in Abhängigkeit von $n$. Sie dürfen Ihre Abschätung in O-Notation angeben. 

iterative: $O(n^2)$
recursice: $O(2^n)$

Als Elementaroperationen zählen: 
- Wertzuweisungen 
- Arithmetische oder logische Operationen 
- Vergleichsoperationen
- Das return-Statement (da dort implizit eine Wertzuweisung versteckt ist) 
- Funktionsaufrufe: 
	Jedes in einem Funktionsaufruf übergebene Element impliziert eine Wertzuweisung und zählt daher ebenfalls als Elementaroperation. Diese Elementaroperationen werden am Ort des Aufrufs der Funktion gezählt, nicht in der aufgerufenen Funktion. Für die Abschätzung der Laufzeit der Funktion isGoodSolutionForSOS muss also z.B. der „Kopf“ der Funktion nicht mitgezählt werden. Wird aber z.B. diese Funktion in SOS (Aufgabe 2) aufgerufen (was nicht zwangsläufig sein muss!), so gehen alle Elementaroperationen, die sich aus dem Funktionsaufruf ergeben, in die Berechnung mit ein. (nächste Seite beachten :))
- Der Einfachheit wegen verzichten wir darauf Operationen zur Speicherverwaltung (etwa Variablendeklarationen oder Anlegen eines neuen Arrays mit new) mitzuzählen. Derlei Operationen benötigen zwar auch Zeit, sie mitzuzählen verkompliziert die Aufgabe aber unnötig.