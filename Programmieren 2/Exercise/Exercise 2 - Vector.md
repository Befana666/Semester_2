
In dieser Aufgabe soll eine Klasse Vector implementiert werden, in der mehrere Elemente vom Datentyp double gespeichert werden können. Die Elemente sollen in einem Array gespeichert werden und die Klasse soll Größe des Arrays verwalten, sodass auch während der Laufzeit eine Änderung der Größe ermöglicht wird. Die einzelnen Teilaufgaben führen Dich dabei Schrittweise durch die Erstellung der Klasse hindurch und fügen der Klasse weitere Funktionalitäten hinzu. 

Schreibe für alle implementierten Funktionalitäten passende Anwendungsbeispiele.

>[!Warning]-
>Die const kannst du theoretisch vermutlich weglassen dann aber überall. Mit dem const verhindert es das man die werte von außen ungewohlt ändern kann aka es ist sicherer.

###### a)
>[!Info]- 
>Erstelle einen Standardkonstruktor, der die Größe des Arrays auf 0 festlegt und noch keinen Speicherplatz allokiert. Zusätzlich soll ein Konstruktor vorhanden sein, mit dem die Größe des Arrays initial festgelegt werden kann.

Wichtig hierbei der nullpointer, eigentlich würde [0] auch ein Array ohne Speicher belegen anlegen aber nicht in jeder Situation/Schreibweise. Der Nullpointer legt es aber immer ohne Speicherreserviereung an.

In der Lösung ist der Vector array ein double nicht ein Int.

```
Vector.h

#pragma once
#include <cstring>

using namespace std;

class Vector
{
private:
	//Variablen Deklaration
	unsigned size;
	double* array;
public:

	//Standartkonstruktor
	Vector(unsigned arraySize);

	//Konstruktor
	Vector();
};
```

```
Vector.cpp

#include "Vector.h";
#include <iostream>

//Standartkonstrukter: ruft er auf wenn keine Parameter mitgegeben wurden
Vector::Vector()
	:size{ 0 }, array{ nullptr }
{
	
}
//Konstrukter den er aufruft wenn du ihm eine Größe mitgibst
Vector::Vector(unsigned newSize)
	: array{ new double[newSize] }
	, size{ newSize }
{
	// Schreibe eine Null in jedes der Felder des Angelegten Arrays
	for (unsigned i = 0; i < size; ++i)
		array[i] = 0.0;	
}
```
###### b)
> [!Info]- 
Erstelle einen Destruktor, der den allokierten Speicherplatz wieder freigibt.

Der delete[] braucht die Eckigen Klammern da das new auch [] klammern hatte. Es löscht quasi alle Elemente des Arrays/das Array.

```
Vector.h

#pragma once
#include <cstring>

using namespace std;

class Vector
{
private:
	
public:
	//Dekonstruktor
	~Vector();
};
```

```
Vector.cpp

#include "Vector.h";
#include <iostream>

//Deletes Array am ende der Lebenszeit
Vector::~Vector() {
	delete[] array;
}
```
###### c)
>[!Info]- 
>Erstelle Getter und Setter für die Größe des Arrays und sorge dafür, dass bei einer Änderung der Größe neuer Speicherplatz allokiert, die gespeicherten Elemente an den neuen Speicherplatz kopiert und der alte Speicherplatz freigegeben wird.

```
Vector.h

#pragma once
#include <cstring>

using namespace std;

class Vector
{
private:

public:
	//Set the Size of Vector
	void setSize(unsigned arraySize);

	//Get the Size of the Vector - Const so no one could use
	//That function to change the size
	unsigned getSize() const;
};
```

```
Vector.cpp

#include "Vector.h";
#include <iostream>

//Set Vector Size
void Vector::setSize(unsigned newArraySize) {

	//Get the smallest Vector
	int minSize = std::min(newArraySize, size);

	//Creates a temp to save Values in it
	auto tempArray = new int[size];
	for (int i = 0; i < size; i++)
	{
		tempArray[i] = array[i];

	}

	//Overwrite old array with new one Sized
	array = new double[newArraySize];

	//Write the saved Values back into the Vector
	for (unsigned i = 0; i < newArraySize; i++)
	{
		if (minSize > i)
		{
			array[i] = tempArray[i];
		}
		else array[i] = 0;
	}

	//Set Vector size to the new Size
	size = newArraySize;

	//Deletes tempArray - Prevent Memory Leak
	delete[] tempArray;

}

//Returns Vector size
unsigned Vector::getSize() const {
	return size;
}
```
##### d)
 
> [!Info] 
> Überschreibe den Indizierungs-Operator [], um Zugriff auf Elemente im Array zu ermöglichen. Dabei soll nicht überprüft werden, ob der angegebene Index im Bereich vom Array liegt.

Honestly ich bin mir nicht ganz sicher wieso wir das extra überladen vielleicht ist es einfach zur Übung.


Die Const Variante braucht man später, ich glaub in f), ich füg sie aber schon mal hier ein.
Da es nicht in der Aufgabenstellung steht.

```
Vector.h

#pragma once
#include <cstring>

using namespace std;

class Vector
{
private:

public:
	//Overloads the [] of an Array
	double& operator[](unsigned index);
	double& operator[](unsigned index) const;
};
```

```
Vector.cpp

#include "Vector.h";
#include <iostream>

//Overloads the [] of an Array
double& Vector::operator[](unsigned index) {
	return array[index];
}

//Overwrites the [] of an Array, does the same but returns a const Value
double&Vector::operator[](unsigned index) const{
	return array[index];
}
```
##### e)
>[!Info]- 
>Die Funktion at() soll dieselbe Funktionalität wie der Indizierungs-Operator ermöglichen und
zusätzlich überprüfen, ob der angegebene Index gültig ist. Sollte der Index außerhalb des Bereiches
liegen, soll das erste Element des Arrays zurückgegeben werden. Überlege dir Vor- und
Nachteile für ein derartiges Vorgehen.

Ich hab noch weniger ne Ahnung wieso wir das Implementieren sollen.
Die Sache ist hier hast du etwas das einen Ungültigen Wert als index abfängt was natürlich das Programm sicherer macht. Allerdings braucht ja jeder weitere check mehr rechenleistung (hier neglectable)

Hier ungefähr hatte ich alle size von Int auf unsigned umgestellt, da er das so in der Lösung hat.
Der Vorteil ist du musst nur checken ob der Index nicht größer als das Array ist.

```
Vector.h

#pragma once
#include <cstring>

using namespace std;

class Vector
{
private:

public:
	//Does pretty much the same but checks if the index is valid
	double at(unsigned index);
};
```

```
Vector.cpp

#include "Vector.h";
#include <iostream>

//Does the same as [] but checks if the index is valid
double Vector::at(unsigned index) {
	if (index > size)
	{
		return array[0];
	}
	return array[index];
}


```

##### f)
>[!Info] 
Überlege dir eine beliebige Möglichkeit, wie zwei Instanzen der Klasse miteinander verglichen werden und in eine Reihenfolge gebracht werden können. Überlade die Vergleichsoperatoren für deine Klasse entsprechend deinen Überlegungen.

>[!Tip] <=> Operator
>Honestly, der <=> Operator ist nicht nur dein Albtraum. Ich bin mir immer noch nicht ganz sicher was er macht. Wenn ich es aber richtig verstanden habe überprüft er ob links gleich rechts ist, wenn nein dann checked er ob eine Seite größer als die andere ist, und gibt 1 oder -1 zurück.
>Falls beide Seiten gleich groß sind gibt er 0 zurück.
>
>Zumindest ist so die Überladung geschrieben.


> [!Warning] Achtung
> Vorsicht diese Funktion ist nicht in der Klasse da es nicht etwas ist das nur ein Objekt der Klasse Betrifft.


```
Vector.h

#pragma once
#include <cstring>

using namespace std;

class Vector
{
private:

public:
	
};

//Compares 2 Vectors and returns -1 0 1 depending 
// which one is larger or if they are the same size
int operator<=>(const Vector& v1, const Vector& v2);
```

>[!Info]- (y>x) ? 1 : -1
>Diese Schreibweise ist ein kurzes If-Else auch ternäre Operator (ternary operator) gennant in C++. *Meiner Meinung nach Pain to Read but apperantly only my Opinion.* 
>
>|   "Normal If"  |  Tenäre If   |
>| --- | --- |
>|  if (x>y)   |   (x>y)  |
>|  return 1;   |   ? 1  |
>|  else return -1;   |   ? -1  |


```
Vector.cpp

#include "Vector.h";
#include <iostream>

int operator<=>(const Vector& v1, const Vector& v2)
{
	//Get the Length of both Vektors
	auto v1Length = v1.getSize();
	auto v2Length = v2.getSize();

	//Checking if both Vectors have the same Length
	if (v1Length != v2Length)
	{
		//if no return 1 or -1 depending on which on is larger
		return (v1Length < v2Length)
			? 1
			: -1;
	}
	//if they have the same length compare the individuel items
	for (int i = 0; i < v1Length; i++)
	{
		if (v1[i] != v2[i])
		{
			//return 1 or -1 if one is larger
			return (v1[i] < v2[i])
				? 1
				: -1;
		}
	}

	//If we reach this the Cectors are the same
	return 0;
}
```

##### g)
>[!Info]- 
>Überlade den Output- und Input-Operator, um eine Ausgabe der Elemente des Array und eine
Eingabe über die Konsole zu ermöglichen. Was soll passieren, wenn bei der Eingabe mehr/weniger
Elemente eingegeben werden als im Array bisher gespeichert sind? Implementiere in diesem
Fall ein Verhalten deiner Wahl und füge der Funktion Kommentare hinzu, die dieses Verhalten
einem möglichen Nutzer erläutern.

```
Vector.h

#pragma once
#include <cstring>

using namespace std;

class Vector
{
private:

public:
	
};
//cout
ostream &operator<<(ostream& os, const Vector& v);

//cin
istream& operator>>(istream& is, Vector& v);
```

```
Vector.cpp

#include "Vector.h";
#include <iostream>

//Cout Overload
ostream& operator<<(ostream& os, const Vector& v)
{
	unsigned size = v.getSize();

	os << "(";
	for (unsigned i = 0; i < size; i++)
	{
		if (i + 1 != size)
			os << v[i] << ", ";
		else
			os << v[i];
	}
	return os << ")\n";
}

istream& operator>>(istream& is, Vector& v) {
	
	for (int i = 0; i < v.getSize(); i++)
	{
		//Counts as input enters if if value cant be assinged
		if (!(is >> v[i]))
		{
			cout << "Data has the wrong type";
			break;
		}

		if (is.peek() == '\n')
		{
			is.ignore();
			break;
		}
	}
	return is;
}
```

##### h)
>[!Info]- 
>Erstelle eine Funktion push back(), die dem Nutzer ermöglicht, ein einzelnes Element dem
Array an dessen Ende hinzuzufügen und damit die Größe des Arrays um eins zu erhöhen.

```
Vector.h

#pragma once
#include <cstring>

using namespace std;

class Vector
{
private:

public:
	void push_back(double value);
};
```

```
Vector.cpp

#include "Vector.h";
#include <iostream>

void Vector::push_back(double value) {
	setSize(size + 1);
	array[size - 1] = value;

}
```

##### i)
>[!Info]- 
>Überlade die Operatoren +, - und * mit einem sinngerechten Verhalten für zwei Instanzen der
Klasse (sinngerecht bedeutet, der + Operator soll z.B. nicht auf einmal Elemente dividieren).
Füge den Funktionen auch hier Kommentare hinzu, die das Verhalten der Operatoren erklären,
besonders auch, wenn die Instanzen zwei unterschiedlich große Arrays besitzen.

```
Vector.h

#pragma once
#include <cstring>

using namespace std;

class Vector
{
private:

public:
	
};
//Returns a vector where all values are muliplied by each other or 1 if one vector is smaller
Vector operator*(Vector& v1, Vector& v2);

//Returns a vector where all values are additon by each other or 1 if one vector is smaller
Vector operator+(Vector& v1, Vector& v2);
//Returns a vector where all values are substracted by each other or 1 if one vector is smaller
Vector operator-(Vector& v1, Vector& v2);
```

```
Vector.cpp

#include "Vector.h";
#include <iostream>

//Substract one Vector from another
Vector operator-(Vector& v1, Vector& v2){
	unsigned v1Length = v1.getSize();
	unsigned v2Length = v2.getSize();
	unsigned maxLength;
	unsigned minLength;

	if (v1Length >= v2Length)
	{
		maxLength = v1Length;
		minLength = v2Length;
	}
	else
	{
		maxLength = v2Length;
		minLength = v1Length;
	}

	Vector diff(maxLength);

	for (unsigned i = 0; i <= maxLength - 1; i++)
	{
		if (i < minLength)
			diff[i] = v1[i] - v2[i];
		else if (v1Length == maxLength)
			diff[i] = v1[i];
		else
			diff[i] = -v2[i];
	}
	return diff;

}

Vector operator+(Vector& v1, Vector& v2) {
	unsigned v1Length = v1.getSize();
	unsigned v2Length = v2.getSize();
	unsigned maxLength;
	unsigned minLength;

	if (v1Length >= v2Length)
	{
		maxLength = v1Length;
		minLength = v2Length;
	}
	else
	{
		maxLength = v2Length;
		minLength = v1Length;
	}

	Vector diff(maxLength);

	for (unsigned i = 0; i <= maxLength - 1; i++)
	{
		if (i < minLength)
			diff[i] = v1[i] + v2[i];
		else if (v1Length == maxLength)
			diff[i] = v1[i];
		else
			diff[i] = v2[i];
	}
	return diff;

}

Vector operator*(Vector& v1, Vector& v2) {
	unsigned v1Length = v1.getSize();
	unsigned v2Length = v2.getSize();
	unsigned maxLength;
	unsigned minLength;

	if (v1Length >= v2Length)
	{
		maxLength = v1Length;
		minLength = v2Length;
	}
	else
	{
		maxLength = v2Length;
		minLength = v1Length;
	}

	Vector diff(maxLength);

	for (unsigned i = 0; i <= maxLength - 1; i++)
	{
		if (i < minLength)
			diff[i] = v1[i] * v2[i];
		else if (v1Length == maxLength)
			diff[i] = v1[i];
		else
			diff[i] = v2[i];
	}
	return diff;

}
```

##### j)
>[!Info]- 
>Erstelle weitere Operator¨uberladungen zum Beispiel f¨ur die +=, -= und *= Operatoren sowie f¨ur Berechnungen zwischen der Klasse und einem einzelnen Double-Wert.

```
Vector.h

#pragma once
#include <cstring>

using namespace std;

class Vector
{
private:

public:
	void operator-=(Vector& otherV);
	void operator+=(Vector& otherV);
	void operator*=(Vector& otherV);

	void operator-=(double value);
	void operator+=(double value);
	void operator*=(double value);
};
```

```
Vector.cpp

#include "Vector.h";
#include <iostream>

void Vector::operator-=(Vector& otherV)
{
	unsigned minLength = min(size, otherV.getSize());

	for (unsigned i = 0; i <= minLength - 1; i++)
	{
		array[i] = array[i] - otherV[i];
	}

}
void Vector::operator+=(Vector& otherV){
	unsigned minLength = min(size, otherV.getSize());
	for (unsigned i = 0; i <= minLength - 1; i++)
	{
		array[i] = array[i] + otherV[i];
	}
}
void Vector::operator*=(Vector& otherV){
	unsigned minLength = min(size, otherV.getSize());
	for (unsigned i = 0; i <= minLength - 1; i++)
	{
		array[i] = array[i] * otherV[i];
	}
}

void Vector::operator-=(double value)
{
	for (unsigned i = 0; i <= size - 1; i++)
	{
		array[i] = array[i] * value;
	}
}
void Vector::operator+=(double value)
{
	for (unsigned i = 0; i <= size - 1; i++)
	{
		array[i] = array[i] * value;
	}
}
void Vector::operator*=(double value)
{
	for (unsigned i = 0; i <= size - 1; i++)
	{
		array[i] = array[i] * value;
	}
}
```