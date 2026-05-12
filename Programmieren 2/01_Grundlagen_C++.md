
C++ hat zum großteil die selbe Syntax als C hat, bietet aber bessere und sichere Funktionalitäten zu Verfügung.


### Objekte & Variablen

![[Programmieren 2/Definitionen#^2edd57]]

- **Datentyp** definiert die möglichen Werte.
	int, float, string, char, bool, ...

- **Objekt** ist ein Speicherbereich, der den Wert eines Datentyps enthält

- **Wert** Menge an Bits die entsprechend dem Datentyp interpretiert werden (Der Wert den du in einer Variable Speicherst)

- **Variable** ist ein bennantes Objekt (Das gesamte Packet)

Elementare Datentypen haben eine feste Größe.

| Datentyp  | Bits |
| --------- | ---- |
| char      | 8    |
| short     | 16   |
| int       | 16   |
| long      | 32   |
| long long | 64   |
Das ist allerdings nur die Mindestgröße. 
Je nach dem welchen Compiler (das ding das den Code ausführt) du hast haben die Elementaren Datentypen unterschiedliche Größen

Damit der Datentyp eine feste Größe hat (benötigt bei Kommunikation/Serialisierung) kann man die Größen mit Hilfe von \<cstdint> festlegen. (Binde über include ein falls nötig)

Beispiele: 
	signed ( Bedeuted die eine hälfte sind minus zahlen die andere Plus)
		int8_t //8 Bit
		int16_t //16 Bit
		int32_t //32 Bit
		int64_t //64 Bit

	unsigned (also keine Vorzeichen)
		uint8_t //8 Bit
		uint16_t //16 Bit
		uint32_t //32 Bit
		uint64_t //64 Bit

Weitere solcher Befehle existieren zu <span style="color:red">Optimierung, Performanz und Speichergrößen</span> zu verbessern. (int_fast8_t für performance, int_least8_t für kleinstmögliche)


---
#### SizeOf
sizeof(Variable) gibt die die Größe einer Variablen in Bytes dar, der Rückgabewert hat den Datentypen size_t. Du kannst es verwenden um die Länge von Arrays, Zeigern und ähnlichem berechnen.
```
//Anzahl der Elemente in einem Array = Größe des gesamten Arrays / Größe eines Elementes eines Arrays
auto lengthOfArray = sizeOf(Array)/sizeOf(Array[0])
```
Das geht aber natürlich nur bei Arrays und ähnlichem wo alle werte die selbe größe haben.

---
#### ptrdiff_t

Speichert einen Integer der die max Größe für den Compiler haben kann.

---
#### Initialisieren

Das erste Zuweisen von Daten/Werten zu einer Variable.
Man kann das beim Objekt erstellen machen oder später.

Dabei können implizierte Datenumwandlungen durchgeführt werden.

Mögliche wege Variabeln zu Initialisieren.
```
int idk;
idk=0; // ist trotzdem eine Initialisierung

int idk2{2}; // Saved theoretisch Speicher kann aber bei c++11 zu fehlern führen

int idk3 = 3; // "Standartweg"

int idk4 = 7.8 // hier wird die .8 abgeschnitten da die Gleitkommazahl zu Int geändert wird

int idk5 {4.5} //Schmeißt einen Fehler da der Typ nicht umgewandelt wird
```

Die geschweiften Klammern hier heißen eine Initialisierungsliste.

>[!Warning]+ Best Practice
>---
>Variabeln sollten immer initialisiert werden. Sonst kann es später zu Programmierfehlern kommen.

---

#### auto (The lazy Way)

Ist ein Variablentyp der sich automatisch anpasst an den Wahrscheinlichstentyp den der Wert haben kann.

Aber nur einmalig bei der Initialisierung später ist auto ==Typ-sicher==.
Bedeuted er kann seinen Typen dann nicht mehr ändern.

auto Typen müssen bei der Deklaration immer initialisiert werden sonst kommen fehler. (Er hätte sonst quasi keinen Typen)

>[!Warning]+ Best Practice
>---
>
>Durch die automatisch Typ-Auflösung können Programmierfehler vermieden werden.
>
>Auch das erzwingen eine Variable zu initialisieren ist von Vorteil um *undefined behavior* zu vermeiden.

---

#### decltype (declaration type)

Ist eine Funktion die dir den Datentyp eines Objektes zurückgibt.
Sie wird vom Compiler vor dem Programstart ausgeführt.

Ist kinda wie auto aber das du musst eine Variable übergeben die dann den Datentyp der neuen Variabel bestimmt.

```
int a = 5;
double b = 5.5;

decltype(a) c= 10; //decltype returns int und setzt dann den typen von c zu int
decltype(b) d = 10.5; //decltype returns double und setzt dann den typen von d zu double
```

Man kann auch den Datentyp von ganzen Ausdrücken/Rechnungen ermitteln.
```
int a = 5;
double b = 5.5;

decltype(a+b) result; //deklariert Variable result und setze typ auf double da a+b einen wert vom type double erzeugt
result = a +b;
```
---
#### Zusammenfassung


>[!recap]
>Eine <span style ="color:red; font-weight:bold ">Variable</span> ist ein Speicherbereich (Objekt) mit einem bestimmten Datentyp und enthält einen Wert
	>- Wert und benötigte Bitgröße hängen vom Datentyp ab
>
>Elemtare Datentypen haben einen <span style ="color:red; font-weight:bold ">Mindestwertebereich</span>
	>- Tastsächliche Bitgröße ist Compilerabhänig, kann aber mit Typen des \<cstding> Headers einheitlich festgelegt werden
>
>Das Setzen eines Werts einer Variablen kann eine <span style ="color:red; font-weight:bold ">Initialisierung</span> oder <span style ="color:red; font-weight:bold ">Zuweisung</span> darstellen
	>- <span style ="color:red; font-weight:bold ">Initialisierung</span>: Setzen des Werts bei der Objekterstellung
	>- <span style ="color:red; font-weight:bold ">Zuweisung</span>: Setzen des Werts eines bereits vorhandenen Objekts
	>  
>  C++11 BS:
>  Das Keyword <span style ="color:purple; font-weight:bold ">auto</span> kann anstelle eines Datentyps verwendet werden und entspricht dem Typ des zugewiesenen Werts
>  - Die Initialiserung eines Objekts wird erzwungen, wodurch Programmierfehler vermieden werden können.
>    
>    Mit der <span style ="color:purple; font-weight:bold ">decltype</span> Compilerfunktion kann der Datentyp einer (anderen) Variable oder eines Ausdrucks angegeben werden

##### Verständnisfragen

PIN: 469452

[<img src="Qr-Code Objekte&Variabeln.png" width="300">](https://poll.hs-kempten.de/poll)

### Funktionen & Objektübergaben

![[Programmieren 2/Definitionen#^93d643]]

```
//Deklaration/Prototypen
Element* next_element(); // Funktion ohne Argumente; Gibt einen Pointer auf Element zurück 
void exit(); // Funktion ohne Argumente; Gibt nichts zurück 

double square(double); // Nimmt ein Double als Argument; Gibt ein Double zurück 

//Definition 
double square(double d) { return d * d; } 

//Aufruf 
double s2 = square(2); // Ruft square() mit dem Argument double{2} auf 
double s3 = square("three"); // FEHLER: Argument vom Typ "const char*" ist mit Parameter vom Typ "double" inkompatibel 
```