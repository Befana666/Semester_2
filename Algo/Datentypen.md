>[!definition]+ Datentypen
>___
>- Legt die Eigenschaften einer Variablen fest und bestimmt die Werte oder Wertemengen die die Variablen annehmen kann.
>- Anzahl und Arten von zulässigen Operationen

>[!definition]+ Datenstruktur
>___
>- Beschreibung der Eigenschaften der Daten und der zur Verfügung stehenden Zugriffsoperationen dieser Daten
>- Menge + Operationen
>- Implementierung kann verschieden sein


#### Standardtypen

- int
	- unsigned int, signed int , long int
	- Ganze zahlen bei Operationen mit Int muss das Ergebnis abgeschnitten werden (10/3=3)
	
	```
	 int imAnInteger = 1;
	```
	 
	
- float
	- double, long double
	- Gleitkommzahlen

```
	 float imAnFloat = 1.12;
```
	
- char
	- Ein einzelnes zeichen, Zahl, Buchstabe
	- speichert es intern als Integer
	```
	 char imAChar = 'a';
	```
	
- Aufzähltyp (enum)
	- Abstrakterer Datentyp
	- Speichert die eingegebenen werte als Zahl (similar array Index)
	- enum figure{Rechteck, Quadrat,Ellipse,Kreis}
```
	 enum Weekdays = {
	 KillMeDay,
	 Tuesdays,
	 NoPlsNoTheo,
	 Thursday,
	 NearlyWeekend,
	 Saturday
	 DeathOfTheWeekend};
```
	
- Zeigertyp (Pointer)
	- \* Dereferenzierungsoperator 
		- Verweißt auf ein anderen Datentypes Speicher
		
	- \& Addressoperator
		- Gibt dir die Speicheraddresse eines Daten types
		
		```
		 int imAnInteger = 1;
		 int * imAPointer = &imAnInteger; //Speichert die Addresse
		 cout << &imAnInteger; //Returns Speicheraddresse
		 cout << imAPointer; //Returns the Value
		```
		
- Array
	- Fasst Daten mit den selben Datentypen "zusammen"
	- int array, string array, char array !Do not mix!
	- Zugriff über ganzzahligen Index (Starte bei 0)
	- konstante oder variable Dimensionierung aka die Größe der Arrays

	```
	int intArray[3] = {1,2,3};
	```

- Structs
	- fasst komponente beliebieger Datentypen zusammen
	- fasst 1 to 1 wie eine Klasse (unterschied daten standart public)
		```
		 struct Visitenkarte{
		 string vorname;
		 string nachname;
		 int age;
		 }
		```

#### Dynamische Datenstrukturen

Arrays and Structs, die durch Zeiger verbunden sind.

Anlegen und löschen eines neuen Objekts vom Typ t durch:
	- new t;
	- delete t;

Zugriff nur über * und -> Operationen möglich

##### Einfach verkettete Liste


>[!Info]+
>___
>- Hat einen Pointer zum nächsten Knoten
>- FIFO (First in First out)
>- Der  neuste Knoten zeigt auf einen nullptr
>- Das älteste Objekt ist der tail

>[!code]+ main.cpp
>```
>Stack<item_type>::Stack() {
>	itemCount = 0;
>	//There is no other
>	tail = nullptr; // Shows technically the newest item so the name is confusing
>}
>```

![[DatenTypenExcalidraw#^frame=YpKOU6KC]]
##### Insert

>[!code]+ main.cpp
```
template <class item_type>
void Stack<item_type>::push(item_type& r) {
	node* temp = new node; //Create a new Node
	temp->item = r; //set Value for Node
	tail->nextItem = item; // Set Pointer from the Previous Node to this Node
	tail = temp; //Save the new Node as top most

	itemCount += 1;
}
```

![[Algo/Attachment/DatenTypenExcalidraw.md#^frame=EinfachInsert]]

>[!Warning]- zu Übung 6
>mir viel gerade auf das ich bei der 6. Übung die Pointer in die Falsche richtung habe zeigen lassen zumindest im Vergleich zu der Grafik

##### Delete