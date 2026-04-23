#### Aufgabe 1
In der Vorlesung wurde die Collatz-Folge vorgestellt. Implementieren Sie einen Algorithmus in C++, der die Collatz-Folge für beliebige Anfangswerte berechnet so lange, bis der Wert 1 erreicht wird:

```
#include <iostream>
using namespace std;

int main()
{
    int collatz;
    while (true) {
        cout << "Input number\n";
        cin >> collatz;
        cout << collatz;
        while (collatz > 1) {
            cout << " - ";
            if (collatz % 2 == 0) {
                collatz /= 2;
            }
            else {
                collatz = (3 * collatz) + 1;
            }
            cout << collatz;
        }
        cout << "\n";
    }
}
```
##### a) Berechnen Sie die Collatz-Folge für die Anfangswerte n=27, n=37 und n=42

n=27
	27 - 82 - 41 - 124 - 62 - 31 - 94 - 47 - 142 - 71 - 214 - 107 - 322 - 161 - 484 - 242 - 121 - 364 - 182 - 91 - 274 - 137 - 412 - 206 - 103 - 310 - 155 - 466 - 233 - 700 - 350 - 175 - 526 - 263 - 790 - 395 - 1186 - 593 - 1780 - 890 - 445 - 1336 - 668 - 334 - 167 - 502 - 251 - 754 - 377 - 1132 - 566 - 283 - 850 - 425 - 1276 - 638 - 319 - 958 - 479 - 1438 - 719 - 2158 - 1079 - 3238 - 1619 - 4858 - 2429 - 7288 - 3644 - 1822 - 911 - 2734 - 1367 - 4102 - 2051 - 6154 - 3077 - 9232 - 4616 - 2308 - 1154 - 577 - 1732 - 866 - 433 - 1300 - 650 - 325 - 976 - 488 - 244 - 122 - 61 - 184 - 92 - 46 - 23 - 70 - 35 - 106 - 53 - 160 - 80 - 40 - 20 - 10 - 5 - 16 - 8 - 4 - 2 - 1
	
n=37, 
	37 - 112 - 56 - 28 - 14 - 7 - 22 - 11 - 34 - 17 - 52 - 26 - 13 - 40 - 20 - 10 - 5 - 16 - 8 - 4 - 2 - 1
	
n=47, 
	47 - 142 - 71 - 214 - 107 - 322 - 161 - 484 - 242 - 121 - 364 - 182 - 91 - 274 - 137 - 412 - 206 - 103 - 310 - 155 - 466 - 233 - 700 - 350 - 175 - 526 - 263 - 790 - 395 - 1186 - 593 - 1780 - 890 - 445 - 1336 - 668 - 334 - 167 - 502 - 251 - 754 - 377 - 1132 - 566 - 283 - 850 - 425 - 1276 - 638 - 319 - 958 - 479 - 1438 - 719 - 2158 - 1079 - 3238 - 1619 - 4858 - 2429 - 7288 - 3644 - 1822 - 911 - 2734 - 1367 - 4102 - 2051 - 6154 - 3077 - 9232 - 4616 - 2308 - 1154 - 577 - 1732 - 866 - 433 - 1300 - 650 - 325 - 976 - 488 - 244 - 122 - 61 - 184 - 92 - 46 - 23 - 70 - 35 - 106 - 53 - 160 - 80 - 40 - 20 - 10 - 5 - 16 - 8 - 4 - 2 - 1
##### b) Ist der Algorithmus terminierend?

Ja er ist terminierend da er aufhört wenn er denn Wert 1 erreicht.

#### Aufgabe 2
Betrachten Sie folgende Beschreibung des „Kaffekochens“: „Kaffee kochen“ Der gesamte Prozess kann man in mehrere Aufgaben unterteilt werden: 
- Wasser in die Kaffeemaschine füllen
- Filtertüte in den Filter legen
- Kaffeepulver hineinfüllen
- Kaffeemaschine anschalten
- Tasse herausholen
- Kaffee einfüllen
- Kaffee trinken
- Kaffeemaschine ausschalten 
##### a) Handelt es sich bei dieser Arbeitsanweisung laut Definition um einen Algorithmus?
Ja, es ist wiederholbar, termenierend, räumt hintersich auf, gibt mit valid input einen Valid output
##### b) Präzisieren Sie einzelne Schritte, falls notwendig.
Man könnte noch einen Schritt hinzufügen bei dem das Programm ausgewählt wird.

#### Aufgabe 3
Entwerfen Sie einen Algorithmus für „Spaghetti kochen“. Achten Sie auf eine möglichst genaue und eindeutige Beschreibung der einzelnen Schritte.

- Topf aus dem schrank hohlen
- Wasser reinfüllen bis 2 cm unter dem Rand
- Wasser salzen bis es nach meer schmeckt
- topf auf den herd stellen
- herd anschalten
- auf max stufe stellen
- nudeln abwiegen
- warten bis wasser kocht falls noch nicht kochend
- herd runter drehen auf max 5
- nudeln reinwerfen 
- 8 minute warten 
- gabel aus schrank hohlen
- nudel auf picksen
- nudel testen 
- wenn nudel fertig continue here wenn nicht warte ne minute und versuchs nochmal
- sieb raus hohlen 
- sieb am guss auf hängen
- topf vom herd nehmen 
- topf zur spüle bringen wasser und nudeln ins sieb giesen 
- sieb in den topf hängen
- herd ausschalten
- nudeln in box packen
