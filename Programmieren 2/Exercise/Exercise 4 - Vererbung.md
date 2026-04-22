

#### Aufgabe 1
In dieser Aufgabe findest Du mehrere Code-Ausschnitte, die Vererbung, Polymorphismus und Typumwandlungen thematisieren. Für alle Code-Ausschnitte sollen die folgenden Aufgaben gelöst werden: 

- VTable analysieren: Zeichne für die relevanten Klassen einen Virtual Table. 
- Ablauf erklären: Beschreibe, welche Konstruktoren, Destruktoren und Methoden in welcher Reihenfolge aufgerufen werden.
- Konsolenausgabe vorhersagen: Gib die Konsolenausgaben an, die bei der Ausführung entstehen. 

Tabelle 1: Beispiel für VTable für Klasse Ogre 

| Index | Funktionsname | Funktion       |
| ----- | ------------- | -------------- |
| 0     | attack        | Ogre::attack() |
| 1     | bribe         | Ogre::bribe()  |

###### a) Konstruktoren, Destruktoren und virtuelle Methoden 
```
# include < iostream > 

class Animal { 
	public : 
		Animal () 
		{
			std :: cout << " Animal created \ n " ; 
		}
		virtual ~ Animal () 
		{
			std :: cout << " Animal destroyed \ n " ; 
		}
		virtual void makeSound () const 
		{
			std :: cout << " Animal sound \ n " ; 
		}
};

class Dog : public Animal {
	public :
		Dog () 
		{ 
			std :: cout << " Dog created \ n " ; 
		}
		
		~ Dog () override 
		{
			std :: cout << " Dog destroyed \ n " ; 
		}
		
		void makeSound () const override 
		{
			std :: cout << " Woof \ n " ; 
		}
};

int main () 
{
	Animal * a = new Dog () ;
	a - > makeSound ();
	delete a;
	return 0;
} 
```

Dog:

| Index | Funktionsname | Funktion         |
| ----- | ------------- | ---------------- |
| 0     | ~Dog          | Dog::~Dog()      |
| 1     | makeSound     | Dog::makeSound() |

Animal:

| Index | Funktionsname | Funktion            |
| ----- | ------------- | ------------------- |
| 0     | ~Animal       | Animal::~Dog()      |
| 1     | makeSound     | Animal::makeSound() |

Ablauf:
1. Konstruktor Animal
2. Konstruktor Dog
3. Make sound Dog
4. Dekonstruktor Dog
5. Dekonstruktor Animal

Output:
1. Animal created
2. Dog created
3. Woof
4. Dog destroyed
5. Animal destroyed

###### b) Typumwandlung mit static cast und dynamic cast
```
# include < iostream > 
class Animal
{
public:
	virtual ~Animal() {};

	virtual void makeSound() const
	{
		std::cout << " Animal sound \ n ";
	}
};

class Dog : public Animal
{
public:
	void makeSound() const override
	{
		std::cout << " Woof \ n ";
	}
	void fetch() const {
		std::cout << " Fetching stick \ n ";
	}
};
class Cat : public Animal { 
public: 
	void makeSound() const override 
	{
		std::cout << " Meow \ n ";
	}
}; 

int main() 
{
	Animal* a = new Dog();
	a -> makeSound();
	Dog* d1 = static_cast <Dog*>(a);
	d1 -> fetch();
	Dog* d2 = dynamic_cast <Dog*>(a);
	if (d2)
		d2 -> fetch();
	Cat* c = dynamic_cast <Cat*>(a);
	if (c)
		c -> makeSound();
	else
		std::cout << " Dynamic cast to Cat failed \ n ";
	delete a;
	return 0;
}
```

Cat

| Index | Funktionsname | Funktion          |
| ----- | ------------- | ----------------- |
| 0     | ~animal       | Animal::~animal() |
| 1     | makeSound     | Cat::makeSound()  |
Ablauf:
1. Konstruktor Animal
2. makeSound dog
3. static cast da objekt dog succes 
4. fetching
5. dynamic cast success
6. fetching
7. Dynamic cast failed
8. deconstruct animal

Output:
1. woof
2. fetch
3. fetch
4. failed

###### c) Virtuelle und nicht-virtuelle Methoden
```
#include <iostream>

namespace Aufgabe4_1c {

    class Animal {
    public:
        virtual void makeSound() const { std::cout << "Animal sound\n"; }
        void sleep() const { std::cout << "Animal sleeping\n"; }
    };

    class Dog : public Animal {
    public:
        void makeSound() const override { std::cout << "Woof\n"; }
        void sleep() const { std::cout << "Dog sleeping\n"; }
    };

    void run() {
        Animal* a = new Dog();
        a->makeSound();
        a->sleep();
        delete a;
    }

}
```

Animal:

| Index | Funktionsnamen | Funktion            |
| ----- | -------------- | ------------------- |
| 0     | makeSound      | Animal::makeSound() |

Dog

| Index | Funktionsnamen | Funktion         |
| ----- | -------------- | ---------------- |
| 0     | makeSound()    | Dog::makeSound() |

Abblauf
1. create Dog mit animal pointer (standart konstrukter)
2. run make sound dog
3. run sleep animal
4. deconstruct dog

Output:
Woof
animal sleep

###### d) Nicht-virtuelle Destruktoren
```
#include <iostream>

namespace Aufgabe4_1d {

    class Animal {
    public:
        Animal() { std::cout << "Animal created\n"; }
        ~Animal() { std::cout << "Animal destroyed\n"; }
    };

    class Dog : public Animal {
    public:
        Dog() { std::cout << "Dog created\n"; }
        ~Dog() { std::cout << "Dog destroyed\n"; }
    };

    void run() {
        Animal* a = new Dog();
        delete a;
    }

}
```

no Vtabels

Ablauf:
1. Create animal
2. create dog
3. delete dog

Output:
1. Animal created
2. Dog created
3. animal destroyed

###### e) Virtuelle Methoden mit Basisklassenzeigern
```
#include <iostream>
#include <vector>

namespace Aufgabe4_1e {

    class Animal {
    public:
        virtual ~Animal() {};
        virtual void makeSound() const { std::cout << "Animal sound\n"; }
    };

    class Dog : public Animal {
    public:
        void makeSound() const override { std::cout << "Woof\n"; }
    };

    class Cat : public Animal {
    public:
        void makeSound() const override { std::cout << "Meow\n"; }
    };

    void run() {
        std::vector<Animal*> animals;
        animals.push_back(new Dog());
        animals.push_back(new Cat());

        for (const Animal* a : animals)
            a->makeSound();

        for (Animal* a : animals)
            delete a;
    }

}
```

Animal

| Index | Funktionsnamen | Funktion            |
| ----- | -------------- | ------------------- |
| 0     | ~Animal        | Animal::~Animal()   |
| 1     | makeSound      | Animal::makeSound() |
Dog

| Index | Funktionsname | Funktion         |
| ----- | ------------- | ---------------- |
| 0     | makeSound     | Dog::makeSound() |

Cat

| Index | Funktionsname | Funktion         |
| ----- | ------------- | ---------------- |
| 0     | makeSound     | Cat::makeSound() |
Ablauf
1. Create Animal
2. Create dog
3. Create Animal
4. Create Cat
5. make sound
6. make sound
7. destroy dog
8.  destroy cat

Output:
1. Woof
2. Miao



###### f) Rule of 5 und Vererbung
```
#include <iostream>

namespace Aufgabe4_1f {

    class Base {
    private:
        int* m_data;

    public:
        // Konstruktor
        Base(int value) : m_data(new int(value)) {
            std::cout << "Base constructed\n";
        }

        // Destruktor
        virtual ~Base() {
            delete m_data;
            std::cout << "Base destroyed\n";
        }

        // Copy-Konstruktor
        Base(const Base& other) : m_data(new int(*other.m_data)) {
            std::cout << "Base copy-constructed\n";
        }

        // Copy-Zuweisungsoperator
        Base& operator=(const Base& other) {
            if (this != &other) {
                delete m_data;
                m_data = new int(*other.m_data);
                std::cout << "Base copy-assigned\n";
            }
            return *this;
        }

        // Move-Konstruktor
        Base(Base&& other) noexcept : m_data(other.m_data) {
            other.m_data = nullptr;
            std::cout << "Base move-constructed\n";
        }

        // Move-Zuweisungsoperator
        Base& operator=(Base&& other) noexcept {
            if (this != &other) {
                delete m_data;
                m_data = other.m_data;
                other.m_data = nullptr;
                std::cout << "Base move-assigned\n";
            }
            return *this;
        }
    };

    class Derived : public Base {
    private:
        int* m_extraData;

    public:
        // Konstruktor
        Derived(int value, int extraValue)
            : Base(value), m_extraData(new int(extraValue)) {
            std::cout << "Derived constructed\n";
        }

        // Destruktor
        ~Derived() override {
            delete m_extraData;
            std::cout << "Derived destroyed\n";
        }

        // Copy-Konstruktor
        Derived(const Derived& other)
            : Base(other), m_extraData(new int(*other.m_extraData)) {
            std::cout << "Derived copy-constructed\n";
        }

        // Copy-Zuweisungsoperator
        Derived& operator=(const Derived& other) {
            if (this != &other) {
                Base::operator=(other);
                delete m_extraData;
                m_extraData = new int(*other.m_extraData);
                std::cout << "Derived copy-assigned\n";
            }
            return *this;
        }

        // Move-Konstruktor
        Derived(Derived&& other) noexcept
            : Base(std::move(other)), m_extraData(other.m_extraData) {
            other.m_extraData = nullptr;
            std::cout << "Derived move-constructed\n";
        }

        // Move-Zuweisungsoperator
        Derived& operator=(Derived&& other) noexcept {
            if (this != &other) {
                Base::operator=(std::move(other));
                delete m_extraData;
                m_extraData = other.m_extraData;
                other.m_extraData = nullptr;
                std::cout << "Derived move-assigned\n";
            }
            return *this;
        }
    };

    void run() {
        Derived d1(10, 20);
        Derived d2 = d1;
        Derived d3 = std::move(d1);
        d3 = d2;
        d2 = d2;
        d2 = std::move(d3);
    }

}
```

VTables:

	Base
	
	| Index | Funktionsname | Funktion      |
	| ----- | ------------- | ------------- |
	| 0     | ~Base         | Base::~Base() |
	
	Derived
	
	| Index | Funktionsname | Funktion           |
	| ----- | ------------- | ------------------ |
	| 0     | ~Derived      | Derived::Derived() |


Ablauf:
	1. Derived d1 constructed
	2. d1 wird auf d2 zugewiesen
	3. d1 wird auf d3 gemoved
	4. d2 wird auf d3 zugewiesen
	5. d2 wird auf d2 zugewiesen
	6. d3 wird auf d2 gemoved

Output:
	1. Base constructed
	2. Derived constructed
	3. Base Copy-assigned
	4. Derived Copy-assigned
	5. Base move-assigend
	6. Derived move-assigend
	7. Base Copy-Assigned
	8. Derived Copy-Assigned
	9.  Base Move-Assigend
	10.  Derived Move-Assigend
	11. Base Destroyed
	12. Derived Destroyed
	13. Base Destroyed
	14. Derived Destroyed
	15. Base Destroyed
	16. Derived Destroyed


#### Aufgabe 2

In dieser Aufgabe soll eine kleine Verwaltungssoftware für eine Bibliothek erstellt werden. Dazu soll eine abstrakte Klasse Publication implementiert werden, von der die Klassen Book und Magazine erben. Die Klassen besitzen die folgenden Mindestanforderungen: 
- Jede Publikation soll mit Titel, Herausgeber und Erscheinungsjahr instanziiert werden und entsprechende Funktionen geben, um diese Werte zurückzugeben.
- In jeder Publikation soll gespeichert sein, ob sie zur Zeit ausgeliehen ist oder nicht, und die Funktionen borrow() und giveBack() existieren, um sie auszuleihen oder zurückzugeben.
- Ein Buch muss zur Identifizierung mit einer ISBN instanziiert werden, ein Magazin mit einer ISSN.
- Die abstrakte Klasse Publication soll eine rein virtuelle Funktion getIdentification() deklarieren, welche von den Kindklassen implementiert wird.
- Für Bücher soll eine Enumeration Genre existieren, welche einem Buch ein Genre ”fiction“, ”nonfiction“, ”periodical“, ”biography“ oder ”children“ zuordnet. Der Konstruktor für das Buch soll diese Zuordnung bereits ermöglichen. 
###### a) Trage in dem UML-Diagramm aus Abbildung 1 die gegebenen Mindestanforderungen ein. Die Enumeration Genre darf dabei als Datentyp verwendet werden. Die Konstruktoren, Getter und Setter werden bis auf die virtuelle Funktion nicht eingetragen. 

![[Pasted image 20260421125118.png]]

###### b) Implementiere die Klassen und erfülle die gegebenen Mindestanforderungen.

>[!Warning] Enum
>Das Enum musst du außerhalbt der Klassen deklarieren


>[!Warning] include
>Was du inlcudesd ist wichtig ich hatte main auf cpp auf header das hat diese Hässlichen Fehler erzeugt. Also nur Header einbinden



```
library.h

#pragma once
#include <iostream>
using namespace std;

enum Genre {
	fiction,
	nonfiction,
	periodical,
	biography,
	children
};

class Libary
{
protected:
	const string title;
	const string publisher;
	const int releaseYear;
	bool isBorrowed;

public:
	Libary(string title, string publisher, int releaseYear);

	const string& getTitle() const;

	const string& getPublisher() const;

	const int& getReleaseYear() const;

	bool getBorrowed();

	void borrow();
	void giveBack();

	virtual const string& getIdentification() const = 0;

	virtual ~Libary();

};

class Book:public Libary {
private:
	const string isdn;
	
public:
	
	Book(string title, string publisher, int releaseYear, const string isdn, Genre genre);

	const string& getIdentification() const override;

	virtual ~Book();
private:
	Genre genre;
};

class Magazin :public Libary {
private:
	const string issn;
public:
	Magazin(string title, string publisher, int releaseYear, const string issn);

	const string& getIdentification()  const override;

	virtual ~Magazin();
};
```

```
library.cpp

#pragma once
#include "Libary.h"

#include <iostream>
using namespace std;

Libary::Libary(const string title,const string publisher,const int releaseYear)
	:title(title), publisher(publisher), releaseYear(releaseYear), isBorrowed(false)
{
	cout << "Created new Media\n";
}

const string& Libary::getTitle() const {
	return title;
}

const string& Libary::getPublisher () const {
	return publisher;
}

const int& Libary::getReleaseYear() const {
	return releaseYear;
}

bool Libary::getBorrowed() {
	if (isBorrowed)
		cout << "Book is borrowed out\n";
	else
		cout << "Book is not borrowed out\n";
	return isBorrowed;
}

void Libary::borrow() {
	if (isBorrowed)
		cout << "Book cant be borrowed\n";
	else {
		isBorrowed = true;
		cout << "You borrowed the book\n";
	}
}

void Libary::giveBack() {
	if (isBorrowed) {
		cout << "You gave the book back\n";
		isBorrowed = false;
	}
	else {
		cout << "How did you do that? This book was never borrowed out!!\n";
	}
}

Libary::~Libary(){
	cout << "U DESTROYED IT\n";
}

Book::Book(const string newTitle,const string newPublisher, const int newReleaseYear, const string newIsdn, Genre newGenre)
	:Libary(newTitle, newPublisher, newReleaseYear), isdn(newIsdn), genre(newGenre)
{
	cout << "Created new Media with issn: " << isdn << title << publisher << releaseYear << "\n";
}

const string& Book::getIdentification() const{
	return isdn;

}

Book::~Book() {
	cout << "You burned THE book\n";
}

Magazin::Magazin(const string title, const string publisher,const int releaseYear, const string issn)
	:Libary(title, publisher, releaseYear), issn(issn)
{
	cout << "Created new Media with isdn: " << issn << "\n";
}

const string& Magazin::getIdentification() const {
	cout << "The ISDN is " << issn << "\n";
	return issn;
}

Magazin::~Magazin() {
	cout << "You burned THE magazin\n";
}
```

```
main.cpp just a snipped

#pragma once
#include "Libary.h"

#include <iostream>
using namespace std;

int main()
{
	Book book1{ "test", "me", 2026, "19284637", fiction };



	return 0;

}
```
###### c) Füge der Klasse Publication Operatorüberladungen für den == Operator und den != Operator hinzu, bei denen die Identifikation zweier Publikationen verglichen wird. Überlade außerdem den << Operator, um Titel, Herausgeber und Erscheinungsjahr einer Publikation in der Konsole auszugeben.

>[!Note] 
>Please ask me not wieso alles const ist. Ich hatte es am anfang oben alles ohne const aber das ging gar nicht. auch das Book book1{} hatte ich am anfang als Library book1 = new book .... das ging auch schief und wieso override am ende der get identification funktion needed ist. (well maybe ask me so i have to check why idk im confused)

```
Libary.h
ostream& operator<<(ostream& os, const Libary& book);

bool operator==(const Libary& book1, const Libary& book2);
bool operator!=(const Libary& book1, const Libary& book2);
```

```
Libary.cpp
ostream& operator<<(ostream& os, const Libary& book) {
	return os	<< "The Book Title is " << book.getTitle() << ".\n"
				<< "It's been published in the year " << book.getReleaseYear() << ""
				<< " by " << book.getPublisher() << ".\n"
				<< "The ISDN/ISSN is " << book.getIdentification() << ".\n";
}

bool operator==(const Libary& book1, const Libary& book2)
{
	return (book1.getIdentification() == book2.getIdentification());
}

bool operator!=(const Libary& book1, const Libary& book2)
{
	return (book1.getIdentification() != book2.getIdentification());

}
```
###### d) Erstelle geeignete Beispiele, um die implementierten Klassen mit ihren Funktionalitäten zu testen.

Well kinda the same as above just use the code u wrote idk.

```
main.cpp

Book book1{ "test", "me", 2026, "19284637", fiction };
cout << "\n";

Book book2{ "test", "me", 2026, "19284637", fiction };
cout << "\n";

Book anotherBook{ "test2", "me", 2026, "192846dsaf37", nonfiction };
cout << "\n";

Magazin magazin{ "sience", "notme", 2020, "sdjfiji" };
cout << "\n";

cout << "\n";
cout << book1;
cout << "\n";

cout << anotherBook;
cout << "\n";

cout << magazin;
cout << "\n";


cout << (book1 == book2);
cout << (book1 != anotherBook);
cout << "\n";
book1.borrow();
book1.borrow();
book2.giveBack();
book1.giveBack();
```