#### Aufgabe 13
##### a) In der Vorlesung wurden 2 Varianten zur Implementierung der Fibonacci- Zahlen vorgestellt. Implementieren Sie zunächst diese beiden Varianten (rekursiv und iterativ) und messen Sie auf Ihrem Praktikumsrechner, welches maximale n Sie mit der Funktion fib bzw. fib2 in ungefähr
- 1 Sekunde,
- 10 Sekunden und 
- 1 Minute berechnen können. 

>[!code]- main.cpp
>```
>#include <iostream>
>using namespace std;
>
>int64_t fibRec(int64_t  n) {
>	if (n <= 2) {
>	    return n + 1;
>    }
>    return fibRec(n - 1) + fibRec(n - 2);
>}
>
>int64_t  fibIt(int64_t  n) {
>   
>    int64_t  sum = 1;
>    int64_t  lastSum = 1;
>    int64_t  temp;
>    for (int64_t  i = 1; i <= n;i++) { //i=1 
>        temp = lastSum + sum; // sum 2
>        lastSum = sum;
>        sum = temp;
>    }
>    return sum;
>}
>
>int main()
>{
>	int timeInSec=10;
>	auto diff = 0;
>	chrono::steady_clock::time_point begin;
>	chrono::steady_clock::time_point end;
>	int64_t fib;
>	int64_t fibEnd;
>	int iEnd;
>	auto diffEnd = 0;
>	long iRec = 0;
>	cout << "Recursive: For " << timeInSec << " Second: \n";
>	for (; diff < 1; iRec++) {
>		begin = chrono::steady_clock::now();
>	    fib = fibRec(iRec);
>	    end = chrono::steady_clock::now();
>	    diff = std::chrono::duration_cast<std::chrono::seconds>(end - begin).count();
>	    if (diff <= timeInSec) {
>			fibEnd = fib;
>	        diffEnd = diff;
>	    }
>    }
>    cout << "Recursive: With " << iRec << " calculations the Program runs " << diffEnd << " seconds and returns " << fibEnd << "\n";
>	
>    diffEnd = 0;
>    iRec = 0;
>    diff = 0;
>	long iIt = 0;
>	fib=0;
>	
>    cout << "Itterative: For " << timeInSec << " Second: \n";
>
>    for (; diff < timeInSec; iIt++) {
>	    begin = chrono::steady_clock::now();
>        fib = fibo_iterativ(iIt);
>        end = chrono::steady_clock::now();
>        diff = std::chrono::duration_cast<std::chrono::seconds>(end - begin).count();
>        cout << fib<<"\n";
>        if (diff <= timeInSec) {
>            fibEnd = fib;
>            iEnd = iIt;
>	        diffEnd = diff;
>        }
>    }
>    cout << "Itterative: With " << iIt << " calculations the Program runs " << diffEnd << " seconds and returns " << fibEnd << "\n";
>}
>```
##### b) Implementieren Sie eine 3. Variante zur Berechnung der Fibonacci-Zahlen in iterativer Form, die nur 3 zusätzliche Speicherplätze benötigt. 
>[!code]- main.cpp
>```
>#include <iostream>
>using namespace std;
>
>int fibo_iterativ(int n)
>{
>    int* afib;
>    afib = new int[n + 1];
>    afib[1] = 1;
>    afib[2] = 1;
>    for (int i = 3; i <= n; i++)
>        afib[i] = afib[i - 1] + afib[i - 2];
>    return afib[n];
>}
>
>int main()
>{
>	int timeInSec = 10;
>	auto diff = 0;
>    chrono::steady_clock::time_point begin;
>    chrono::steady_clock::time_point end;
>    int64_t fib;
>    int64_t fibEnd;
>    int iEnd;
>    auto diffEnd = 0;
>    long iIt = 0;
>    
>    cout << "Itterative: For " << timeInSec << " Second: \n";
>
>    for (; diff < timeInSec; iIt++) {
>        begin = chrono::steady_clock::now();
>        fib = fibo_iterativ(iIt);
>        end = chrono::steady_clock::now();
>        diff = std::chrono::duration_cast<std::chrono::seconds>(end - begin).count();
>        if (diff <= timeInSec) {
>            fibEnd = fib;
>            iEnd = iIt;
>            diffEnd = diff;
>        }
>    }
>    cout << "Itterative: With " << iIt << " calculations the Program runs " << diffEnd << " seconds and returns " << fibEnd << "\n";
>}
>```

##### c) Geben Sie die Zeit- und Speicherkomplexität der 3 verschiedenen Varianten an. 
- Recursive: O(2^n) speicher O(n) (wieviele enden hat der baum)
- Itterative: O(n)  speicher: O(1)
- Itterative(Array): O(n) speicher O(n)

#### Aufgabe 14 
In der Vorlesung wurde der Algorithmus der binären Suche behandelt. 
##### a) Implementieren Sie eine Routine bin_suche nach dem Prinzip der Binärsuche in dem u.a. ADT Vektor implementiert ist: 
```
class Vektor 
{
private: int dimension;
	int *daten;
	public: 
	Vektor(int dim);
	virtual ~Vektor();
	void set(int i, int val);
	int get(int i);
	int bin_suche(int sw);
};
int Vektor::bin_suche(int sw)
{
	int l_u=0,l_o=dimension-1; // untere und obere Grenze des Sucharrays 
	while (l_u<=l_o)
	……. 
}
```

 >[!code]- vector.h
>```
>#include <iostream>
>using namespace std;
>class Vektor
>{
>private:
>	int dimension;
>	int* daten;
>public:
>	Vektor(int dim) 
>		:dimension(dim){}
>	virtual ~Vektor() {}
>	void set(int i, int val) {}
>	int get(int i) {}
>	int bin_suche(int sw) {
>		int lowerBorder = 0;
>		int upperBorder = dimension - 1; // untere und obere Grenze des Sucharrays
>		int mid;
>		while (lowerBorder <= upperBorder) {
>			mid = lowerBorder + (upperBorder - lowerBorder) / 2;
>
>			if (get(mid) > sw) {// ^1 2 3 4  5
>				upperBorder = mid - 1;
>			}
>			else if (get(mid) < sw) {
>				lowerBorder = mid + 1;
>			}
>			else {
>				return mid;
>			}
>
>			cout << "Not found";
>			return -1;
>		}
>	}
>};
>```
##### b) Welche Komplexität ergibt sich für den Algorithmus im schlechtesten Fall 
- Falls der Array die Länge 2𝑘 − 1 hat? 
	- Im ungünstigsten Fall genau k aufrufe
- Bei anderen Arraylängen?
	- Allgemein kann man sagen das im Üngünstigsten Fall log2(n) Vergleiche gemacht werden müssen
#### Aufgabe 15
𝑇(𝑛) sei eine Funktion, die durch folgende Rekursionsgleichung bestimmt ist: T(𝑛) = 𝑛 ∗ 𝑇(𝑛 − 1) + 𝑛 Als Startwert soll 𝑇(1) = 1 gewählt werden. 
##### a) Schreiben Sie ein C++-Programm für die rekursive Berechnung der Funktion 𝑇(𝑛) und berechnen Sie die Werte von 𝑇(𝑛) bis 𝑛 = 10. 

>[!code]- main.cpp
>```
>#include <iostream>
>using namespace std;
>
>int recCus(int n) {
>    if (n == 1) {
>        return 1;
>    }
>    return n * recCus(n - 1) + n;//3 
>}
>
>int main()
>{
>    cout << recCus(10)<<"\n";
>}
>```

Output: 9864100
##### b) Schreiben Sie ein C++-Programm für die iterative Berechnung der Funktion 𝑇(𝑛) und berechnen Sie die Werte von 𝑇(𝑛) bis 𝑛 = 10. 

>[!code]- main.cpp
>```
>#include <iostream>
>using namespace std;
>
>int recItt(int n) {
>    int sum{ 1 };
>    for (int i = 2; i <= n; i++) {
>       
>        sum = i * sum + i;// 3
>    }
>    return sum;
>}
>
>int main()
>{
>	cout << recItt(10);
>}
>```
Output: 9864100
##### c) Von welcher Ordnungsklasse ist das Wachstumsverhalten der Funktion 𝑇(𝑛)? 

	
##### d) Wie viele rekursive Aufrufe benötigt die Berechnung von 𝑇(𝑛)? e) Von welcher Ordnung ist die Anzahl der rekursiven Aufrufe?