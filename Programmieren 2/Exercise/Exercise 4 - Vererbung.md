![[Uebungsblatt4_Vererbung.pdf]] 

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

Animal:

| Index | Funktionsname | Funktion            |
| ----- | ------------- | ------------------- |
| 0     | ~animal       | Animal::~animal()   |
| 1     | makeSound     | Animal::makeSound() |
Dog:

| Index | Funktionsname | Funktion          |
| ----- | ------------- | ----------------- |
| 0     | ~animal       | Animal::~animal() |
| 1     | makeSound     | Dog::makeSound()  |
| 2     | fetch         | Dog::fetch()      |

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