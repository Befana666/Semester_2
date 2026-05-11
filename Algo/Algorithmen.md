> [!Algorithmus]+ Algorithmus
> - eindeutige, endliche Beschreibung eines Verfahrens um ein Problem zu lösen
> - Beschreibung erfolgt in einem Formalismus
> - muss nur für zulässige Eingaben funktionieren

^1da272

Eigenschaften eines Guten Algorithmus:
- schnell
- wenig Speicherbedarf
- einfach und leicht verständlich


>[!Terminierung]-
> - etwas ist terminierend wenn es bei jeder erlaubten Einigabe nach endlich vielen Schritten abbricht
> 
> _Kann nachgewiesen werden mit:_
> - Spezielle Algorithmen
> - Klassen von Algorithmen
> - Programstrukturen (Schleifen)
> 
>   

##### Collatz- Funktion
$$
c_{n+1} = \begin{cases}\frac{c_n}{2}, &falls\ c_n\  gerade\\ 3*c_n+1, &falls\ c_n\ ungerade\end{cases}
$$
   
- $c_n = 1$ ist Rekursionsende
- endet immer auf 4,2,1
- bis heute nicht wiederlegt

##### Halteproblem:
>	Gibt es  ein Verfahren, mit dem man für jeden Algorithmus entscheiden kann ob dieser terminiert?

Nicht berechenbar/entscheidbares Problem


>[!Determinismus]-
>
>Definition:
>1. ...hat eine eindeutige Schrittfolge
>2. ... wenn bei vorgegebener Eingabe immer ein eindeutiges Ergebnis berechnet wird.
>3. Nichtdeterministische Algorithmen mit determiniertem Ergebnis
heißen determinierter Algorithmus.

>[!Korrektheit]-
>
>Definition: 
>1. wenn für zulässige eingaben immer zulässige Ergebnisse erzeugt werden
>2. zulässige Eingaben werden über Spezifikationen definiert
>
>Verifikation:
>- Theoretisch
>- über ausreichend viele Testfälle

### Darstellungsformen
>[!Verbale Darstellungsform]-
>
>Ausgeschrieben oder Ausgesprochen in Alltagssprache/schreibweise:
>
>Auszugeben ist der Mittelwert von N einzulesenden positiven Zahlen

> [!Pseudo Code Darstellungsform]-
> 
>```
>read N
Zähler = 1
Summe = 0
while (Zähler <= N) do
read Zahl
if (Zahl > 0)
then
Summe = Summe + Zahl
Zähler = Zähler + 1
end-if
end-while
Schnitt = Summe/(Zähler-1)
write Schnitt
> ```
> 
> Beispiele:
> Adele:
> - an Pascal angelehnt
>   
>Jana:
>- Java angelehnt

#### Struktogramme
Tool: Structorizer

![[Pasted image 20260413150228.png]]


#### UML (Unified Modelling Language)
- Aktivitätsdiagramm
- Sequenzdiagramm
![[Pasted image 20260413150328.png]]


### Schnelligkeit eines Algorithmus

>[!Info]-
>abhänig von:
>- Eingabedaten
>- Qualität des Compilers
>- Hardware/OS

### Komplexitätsanalyse

Berücksichtigt nur die Abhängigkeit von den gewählten Eingabedaten:

- Größe der Eingabedaten
- Struktur der Eingabedaten

### Big-O-Notation

**Big-O-Notation = Landausche Symbole**
f(n) und g(n) sind positive monoton wachsende Funktionen

---

>**O(g(n))**
>
>Menge aller Funktionen f(n), wachsen gleich schnell oder langsamer als g(n)
>
>$$
	\lim_{n->\infty} \begin{pmatrix}\frac{f(n)}{g(n)} \end{pmatrix}\leq c
$$

>$\Theta(g(n))$ 
>
>Menge aller Funktionen f(n), wachsen gleich schnell g(n)
>$$\lim_{n->\infty}\begin{pmatrix}\frac{f(n)}{g(n)}\end{pmatrix}=c$$

>$\Omega(g(n))$
>
>Menge aller Funktionen f(n), wachsen gleich schnell oder schneller g(n)
>
$$
\lim_{n->\infty}\begin{pmatrix}\frac{f(n)}{g(n)}\end{pmatrix}\geq c
$$>oder $\frac{f(n)}{g(n)}$ wächst unbeschränkt für $n->\infty$ 

> o(g(n))
>
>Menge aller Funktionen f(n), wachsen langsamer als g(n)
>
>$$\lim_{n->\infty}\begin{pmatrix}\frac{f(n)}{g(n)}\end{pmatrix} \lt 0$$

>[!warning]+ 
>c= Natürliche Zahlen

#### Komplexitätsklassen

| Symbol           | Name          | Beispiel                          | 1 sec   | n=1mio.             |
| ---------------- | ------------- | --------------------------------- | ------- | ------------------- |
| $O(1)$           | konstant      | elementarer Befehl                |         |                     |
| $O(log(log\ n))$ |               | doppelt logarithmisch             |         |                     |
| $O(log\ n)$      | logarithmisch | Binärsuche                        |         |                     |
| $O(n)$           | linear        | lineare Suche                     | 1000000 | 1 sec               |
| $O(n\ log\ n)$   | überlinear    | schnelles Sortierverfahren        | 10000   | 4 sec               |
| $O(n^2)$         | quadratisch   | einfaches Sortierverfahren        | 1000    | 12 Tage             |
| $O(n^3)$         | kubisch       | Matrizen-Inersion                 | 100     | 31710 Jahre         |
| $O(n^k)$         | polynomiell   | vom Grad k lineare Programmierung | 20      | $10^{300000}$ Jahre |
| $O(2^n)$         | exponentiell  | Türme von Hanoi                   |         |                     |
| $O(n!)$          | Fakultät      | Traveling Salesman Problem        |         |                     |
| $O(n^n)$         |               |                                   |         |                     |
#### Komplexität von Funktionen berechnen

###### Übung 1: 
$$\begin{aligned}&f(n)=5n^2+2n+13\\ &g(n)=n^2=O(n^2)\\ &f(u) \in O(n^2)?\\ &=\lim_\limits{n \to \infty}\frac{5n^2+2n+13}{n^2}=\lim_\limits{n \to \infty}\frac{5n^2}{n^2}+\lim_\limits{n \to \infty}\frac{2n}{n^2}+\lim_\limits{n \to \infty}\frac{13}{n^2}\\ & =5+0+0=5 \leq c \in \mathbb{R}^+\\& \Rightarrow f(n)=5n^2+2n+13 \in O(n^2)
\end{aligned}$$
###### Übung 2:
$$\begin{aligned}
&f(n)=1000n+100\\
&g(n)=n^2\\
&\lim_\limits{n \to \infty}\frac{1000n+100}{n^2}=\lim_\limits{n \to \infty}\frac{1000n}{n^2}+\lim_\limits{n \to \infty}\frac{100}{n^2}\\
&0+0=0\leq c \in \mathbb{R}^+\\
&f(n)=1000n+100\in O(n^2)
\end{aligned}$$
Für mehr Beispiele sieh0e: [[Big-O-Notation Notizen.pdf#page=2|LV_Notizen_2303, page 2]]

### Lineares Suchen

Lineare Suche in einem unsortiertem Array
![[Lineare Suchen#^c5a91e]]

Falls Element y in der Liste vorhanden ist, tue .....

| Best Case   | Average Case       | Worst Case   |
| ----------- | ------------------ | ------------ |
| 1 Vergleich | (n+1)/2 Vergleiche | n Vergleiche |
Siehe hier für Komplexität: [[Lineare Suche Notizen.pdf#page=1|LV_Notizen_2303b, page 1]]
### Typen von Algorithmen

- Iterative Algorithmen
	- fixe Anzahl von Schleifendruchläufen
- Greedy
	- suche lokalem Optimum
- Rekursion
	- Funktion die sich selbst aufruft
	- kann in iterative umgewandelt werden
	- oft nicht wert den Rechenaufwand
- Divide and Conquer - Algorithmen
	- Zerlegund der Teilprobleme
	- Zusammensetzung der Teillösungen zu einer Gesamtlösung

#### Iterative Algorithmen

![[Vector Addition#^62d5b5]]

![[Vektor-Addition]]

---
#### Greedy
- Einfacher und schneller Algo für Optimierungs probleme
	- Bestimmt lokale optimale Lösung
	- "Nimm immer Größtes" (greedy)

| Vorteile                                                                  | Nachteile                                 |
| ------------------------------------------------------------------------- | ----------------------------------------- |
| - nur polynomiale Komplexität                                             | globales Optimum wird i.a. nicht gefunden |
| - alle möglichen Pfade absuchen: <br>           exponentielle Komplexität |                                           |
| Lokales Optimum oft ausreichend                                           |                                           |
##### Beispiele:
- Wechselgeldalgorithmus
- Scheduling von Prozessen auf Prozessoren
- Minimalpfad in einem Graphen (Routenoptimierung)

More: [[Greedy-Algorithmen Notizen.pdf]]

---


#### Rekursion

- Funktion ruft sich selbst auf
- Terminationsbedingung verhindert Endlos-Schleife

![[Facultät#^67eb38]]

>[!Warning]+ Warning
>- Anzahl der rekursiven Funktionsaufrufe muss überschaubar bleiben (Speicherverbrauch)
>- Algorithmus soll durch Rekursion einfacher zu formulieren sein
>- Komplexität der Rekursion sollte von derselben Ordnung sein wie ohne

##### Rekursionauflösung

![[Fibonacci#^429058]]

- Umdrehen der Berechnung (von unten nach oben)
- Abspeichern der Zwischenresultate auf stack oder array

![[Fibonacci#^b7c330]]

##### Rekursionstiefe
- Rekursive Form:
	- Anzahl der Vergleiche = Anzahl der rekursiven Aufrufe:
		$$T_{n+1}\begin{cases}T(n)=1, &falls\ n\leq 2\\ T(n-1)+T(n-2)+1, &falls\ n\geq 3\end{cases}$$
	- n Speicherplätze im Stack nötig
- Aufgelöste Form
	- n+1 Speicherplätze nötig
	- n-1 Schleifendurchläufe mit jeweils
		- 1 Addition
		- 1 Vergleich 
		- 1 Inkrement

Dynamische Programmieren
	- rekursive Form, die Neuberechnung von bekannten Werten vermeidet
	- O(n) Vergleiche

![[Fibonacci#^2c7b4d]]

##### Beispiele

Rucksackproblem
	- Dieb raubt Safe aus
	- Safe enthält N Typen von Gegenständen
	- Gegenstände haben unterschiedlichen Wert und Größe
	- Rucksach hat bestimmtes Fassungsvermögen
	- Gesamtwert soll maximiert werden

- Ordne Wertstücke nach möglichst leicht und Wertvolle
- Ergibt lokales aber nicht globales Optimum
- SCHNELL!!

![[Rucksackproblem#^044660]]

More: -[[Rekursion Notizen.pdf]]
	  -[[Rucksack-Problem Notizen.pdf]]
#### Divide and Conquer (DAQ)

1. Zerlege in kleinere Teilprobleme (divide)
2. Löse Teilprobleme
3. Setze Teile zur Gesamtlösung zusammen

Beispiele:
- Binäre Suche
- Mergesort, Quicksort, ...

##### Binäre Suche in einem sortierten Array
- Beispiel für  Anwendung von DAQ
- geg.: sortiertes Array a, Suchwert sw
- ges.: Suchindex si mit a\[si\] =sw
- Vorgehensweise:
	- funktioniert nur im sortierten Array
	- Sucharray ist Ausgangsarray
	- Solange Sucharray größer als Einitrag ist 
		- Aufteilung des Sucharrays in 2 Teilfelder
		- Falls sw im rechten Teilfeld setzte Sucharray auf das rechte Teilfeld, sonst auf das linke Teilfeld
	- Rückgabe des Index (=si) des einzigen Elements im Sucharray
More: [[Binäre Suche Notizen.pdf]]

|               | Lineare Suche      | Binäre Suche                       |
| ------------- | ------------------ | ---------------------------------- |
| best case:    | 1 Vergleich        | 1 Vergleich                        |
| average case: | (n+1)/2 Vergleiche | $log_2(n)$ Vergleiche              |
| worst case:   | n Vergleiche       | $\frac 1 2(1+log_2(n))$ Vergleiche |
