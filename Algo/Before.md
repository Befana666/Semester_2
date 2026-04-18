> [!Algorithmus]
> - eindeutige, endliche Beschreibung eines Verfahrens um ein Problem zu lösen
> - Beschreibung erfolgt in einem Formalismus
> - muss nur für zulässige Eingaben funktionieren

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
c_{n+1} = \begin{cases}\frac{c_n}{2}\\ 3*c_n+1\end{cases}
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

>o(g(n))
>
>Menge aller Funktionen f(n), wachsen langsamer als g(n)
>
>$$\lim_{n->\infty}\begin{pmatrix}\frac{f(n)}{g(n)}\end{pmatrix} = 0$$