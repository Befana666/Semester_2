![[Uebungsblatt4_Vererbung.pdf]] sd

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