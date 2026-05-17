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

[[LV_Notizen_1304c.pdf#page=1|LV_Notizen_1304c, page 1]]

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
	temp->nextItem = tail; // Set this nodes pointer to the previous node
	tail = temp; //Save the new Node as top most

	itemCount += 1;
}
```

![[Algo/Attachment/DatenTypenExcalidraw.md#^frame=EinfachInsert]]

>[!Warning]- zu Übung 6
>mir viel gerade auf das die Pfeile hier und wie ich es gecoded habe nicht übereinstimmen
>mir fällt aber auch kein anderer weg ein


##### Delete

>[!code]- main.cpp
>```
>item_type Stack<item_type>::pop() {
>	if (!empty()) {
>		node* temp = tail; // Temp save the node u want to delete
>		tail = temp->nextItem;
>		itemCount -= 1;
>		item_type value = temp->item;
>		delete temp;
>		return value;
>	}
>}
>```

![[Algo/Attachment/DatenTypenExcalidraw.md#^frame=Delete]]
Gefahr der Speicherfresser beim Löschen. Aka du hängst nur die Pointer um aber löscht das Item nicht.

##### Zweifach Verkettete Liste
[[LV_Notizen_2004a.pdf#page=1|LV_Notizen_2004a, page 1]]
- jeder Knoten hat 2 Zeiger einem zum vorherigen und einem zum nächsten Knoten
- man kann in beide richtungen Loopen
- Zugriff kann über head or tail passieren

![[Algo/Attachment/DatenTypenExcalidraw.md#^clippedframe=CGWhuRU1]]

#### Abstrakte Datentypen (aka. Klassen)

>[!definition]+ Abstrakte Datentypen
>___
>- sind eine Kombination von Datentypen und Funktionen
>- Daten sind standart mäßig auf private gesetzt (gekapselt)/ kein Zugriff von draußen
>- Implementierung ist nach außen hin verborgen und austauschbar

##### ADT Stack

- Liste mit einigeschränkten Operationen
	- Last-In-First-Out = LIFO

Benötigte Operationen(min)
	s.top - liefert das oberste Element
	s.pop - entfernt das oberste Element
	s.push(x) - legt ein Element auf den Stack

[[LV_Notizen_2004b.pdf#page=1|LV_Notizen_2004b, page 1]]
![[ADT Stack#^4b10d0]]

![[ADT Stack#^f91b1c]]

###### Anwendungsbeispiele

1. Zahlen auf dem Stack

![[Algo/Attachment/DatenTypenExcalidraw.md#^frame=zpxxKvIf]]
2.  Umwandlung von Infix to PostFix and vice versa
	Siehe Aufgabe: [[Algo/Übungen/Übung 6#Aufgabe 21|Übung 6]]
	[[LV_Notizen_2004c.pdf#page=1|LV_Notizen_2004c, page 1]]
>[!definition]+ Infix $\Rightarrow$ Postfix Umwandlung
>___
>
>Stapel anfangs leer
>Stapel enthält während des Algorithmus nur '(' oder Rechenoperatoren
>Durchlaufe die Eingabeelemente von links nach rechts
>Fallunterscheidung:
>1. '('
>	Klammer '(' auf den Stapel legen
>2. Zahl
>	Zahl ausgeben
>3. Operator
>	Alle Operatoren mit gleicher oder höheren Priorität vom Stabel ausgeben, bis '(' erreicht oder Stabel leer. ==Dann Operator auf Stapel legen.==
>4. ')'
>	Alle Operatoren vom Stabel bis zur ersten linken Klammer ausgeben.
>	Die erste Linke Klammer vom Stapel löschen
>
>Am Ende alle verbleibenden Operatoren vom Stapel ausgeben.

[[LV_Notizen_2004d.pdf#page=1|LV_Notizen_2004d, page 1]]
>[!definition]+ Postfix $\Rightarrow$ Infix 
>___
>Stapel anfangs leer 
>Stapel enthält während des Algorithmus nur Zahlen 
>Durchlaufe die Eingabeelemente von links nach rechts. 
>Fallunterscheidung:
> 1. Zahl: 
> 	Lege die Zahl auf den Stapel 
> 2. Operator op:
> 	- Wende den Operator op auf die beiden obersten Elemente des Stapels an
> 	- Ersetze diese beiden Zahlen durch das Ergebnis 
> 
> Am Ende steht das Rechenergebnis als einziger Wert im Stapel



##### Tabelle
LV Notizen:
- [[LV_Notizen_2704a.pdf#page=1|LV_Notizen_2704a, page 1]]
- [[LV_Notizen_2704b.pdf#page=1|LV_Notizen_2704b, page 1]]


Siehe: [[Algo/Übungen/Übung 7#Aufgabe 25|Aufgabe 25]]
- Wichtig ist das es ein KeyValue pair gibt 
	- z.b. Index und Wert in einem Array
	- Matrikelnummer (Key) und Studenten infos (Value)
	- honestly idk how he did it in his Presentation

>[!definition]+ Tabelle
>___
>Verfügbare Elementfunktionen:
>- generieren, entfernen von Tabellen
>- suche, ausgeben, ersetzen löschen von Einträgen in der Tabelle
>- Reorganisation der Tabelle
>- Sortieren der Einträge nach vorgegebenen Kriterien
>- Selektion nach vorgegebenen Kriterien
>- Typische Operation von $\rightarrow$ Datenbanken
>
>Einträge (Elements):
>- records eines Typs Tr

Siehe [[Done_2. Vorlesung.pdf#page=37|Anwendungsbeispiele]]

Tabelle als Array implementierbar: 
- feste zusammenhängende Random-Access-Struktur 
- direkter schneller Zugriff auf die Komponenten
- Suchen und Sortieren im array leicht möglich

###### Komplexität (Array Tabelle)

Reorg = O(n)
Einfügen/Löschen = O(n)
weitere = O(1)
Suchen:
- Linear: O(n)
- Binär: O($log_n$) ==Vorhersortieren!!!==


STL - Standart Template Libary 
Implementiert Tables
___
##### Datenbanken
LV Notizen:
- [[LV_Notizen_2704c.pdf#page=1|LV_Notizen_2704c, page 1]]
- [[LV_Notizen_2704d.pdf#page=1|LV_Notizen_2704d, page 1]]
- [[LV_Notizen_2704e.pdf#page=1|LV_Notizen_2704e, page 1]]

... bestehen aus Tabellen.
Eindeutiger Primärschlüssel notwendig. (Freiwählbar oder Auto gen)
Verschiedene Tabellen können miteinander verknüpft werden via Primärschlüssel

| matrikerl | name   | kursenum |
| --------- | ------ | -------- |
| 9120      | muster | 102      |

| kursnum | name | prof   |
| ------- | ---- | ------ |
| 102     | Algo | Göhner |
Hier kriegt der Student mit der Matrikelnumer 9120 den kurs 102 zugewiesen, der dann den Prof Göhner hat. Stellt somit eine Beziehung da.

Sorry Blake falls du das hier kriegst ich wusste einfach nicht was ich hier schreiben soll da wir das eigentlich alles in den Verketteten Listen hatten.
Falls du eine Frage hast schau ich es mir nochmal an und füge es hinzu.
Schreibs nur hierrein falls ich es vergesse zu sagen.