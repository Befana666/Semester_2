#### Aufgabe 24
Beweisen Sie folgende Aussagen durch formales Nachprüfen der Definition der Landauschen Symbole aus der Vorlesung oder widerlegen Sie die Aussage durch Angabe eines Gegenbeispiels (mit Begründung, warum dies ein Gegenbeispiel ist): 
##### a) $u(n) \in O(n^2) \text{ und } v(n) \in O(n) \Rightarrow u(n)+v(n)*n \in O(n^2)$

Voraussetzung:
$$u(n) \in O(n^2) \text{ und } v(n) \in O(n) \Leftrightarrow \lim_\limits{n \to \infty} \frac{u(n)}{n^2}\leq c_1\in \mathbb{R}^+ \text{ und } \lim_\limits{n \to \infty} \frac{v(n)}{n}\leq c_2\in \mathbb{R}^+$$
Behauptung:
$$
	u(n)+v(n)*n\in O(n^2) \Leftrightarrow \lim_\limits{n \to \infty} \frac{u(n)+v(n)*n}{n^2}\leq c\in \mathbb{R}^+
$$
Beweis:
$$
\lim_\limits{n \to \infty} \frac{u(n)+v(n)*n}{n^2}=\lim_\limits{n \to \infty} \frac{u(n)}{n^2}+ \lim_\limits{n \to \infty} \frac{v(n)*n}{n^2}
$$

##### b) $u(n) \in \Omega(n^3) \Rightarrow v(n) = u(n)*n\in \Omega(n^4)$

Voraussetzung:
$$u(n) \in \Omega(n^3) \Leftrightarrow v(n)= \lim_\limits{n \to \infty} \frac{u(n)}{n^3}\geq c\in \mathbb{R}^+ $$
Behauptung:
$$
	u(n)\in \Omega(n^3) \Leftrightarrow \lim_\limits{n \to \infty} \frac{u(n)*n}{n^4}\geq c\in \mathbb{R}^+
$$
Beweis:
$$
\lim_\limits{n \to \infty} \frac{u(n)*n}{n^4}\geq c\in \mathbb{R}^+
$$
#### Aufgabe 25
In der Vorlesung wurde eine Implementierung des ADT Tabelle mit Hilfe eines arrays des Datentyps \<TR> vorgestellt. Implementieren Sie folgende öffentlich sichtbaren Schnittstellenfunktionen mit Hilfe einer doppelt verketteten Liste:

```
#pragma once

template <class ItemType>
class Tabelle
{
public:
	Tabelle(); // kreiert leere Tabelle
	~Tabelle(); // gibt von der Tabelle belegten Speicherbereich frei
	bool insert(item_type r);// fügt neuen Record vor dem aktuellen Record ein
	bool append(item_type r);// fügt neuen Record am Ende der Liste ein
	bool first(); // erster Record wird zum aktuellen Record
	bool last(); // letzter Record wird zum aktuellen Record
	bool next(); // der dem aktuellen Record folgende Record wird zum neuen aktuellen Record
	bool previous(); // der dem aktuellen Record vorausgehende Record wird zum neuen aktuellen Record
	bool delete_node(); // löscht aktuellen Record
	bool get_node(item_type& r); // liefert aktuellen Record in der Recordvariablen r
	bool set_node(item_type& r); // ersetzt aktuellen Record durch Recordvariable r
};
```

>[!code]- table.h
>```
>#pragma once
>#include <iostream>
>using namespace std;
>
>template <class item_type>
>class Tabelle
>{
>	struct node {
>		item_type item;
>		node* nodeHead;
>		node* nodeTail;
>	};
>
>private:
>	node* tail;
>	node* iterator;
>	node* head;
>
>public:
>	Tabelle(); // kreiert leere Tabelle
>	~Tabelle(); // gibt von der Tabelle belegten Speicherbereich frei
>	bool insert(item_type r);// fügt neuen Record vor dem aktuellen Record ein
>	bool append(item_type r);// fügt neuen Record am Ende der Liste ein
>
>	bool first(); // erster Record wird zum aktuellen Record
>	bool last(); // letzter Record wird zum aktuellen Record
>
>	bool next(); // der dem aktuellen Record folgende Record wird zum neuen aktuellen Record
>	bool previous(); // der dem aktuellen Record vorausgehende Record wird zum neuen aktuellen Record
>
>	bool delete_node(); // löscht aktuellen Record
>	bool get_node(item_type& r); // liefert aktuellen Record in der Recordvariablen r
>	bool set_node(item_type& r); // ersetzt aktuellen Record durch Recordvariable r
>	void show(); 
>};
>```

>[!code]- table.cpp
>```
>#include "Tabelle.h"
>
>template<class item_type>
>Tabelle<item_type>::Tabelle()
>{
>	tail = nullptr;
>	iterator = nullptr;
>	head = nullptr;
>}
>
>template<class item_type>
>Tabelle<item_type>::~Tabelle()
>{
>	while (head != nullptr) {
>		delete_node();
>	}
>}
>
>template<class item_type>
>bool Tabelle<item_type>::insert(item_type r)
>{
>	//Lege neue Node an
>	node* temp = new node;
>	temp->item = r; // setze item zu r
>		
>	temp->nodeTail = iterator;
>
>	//Falls ein Iterator schon existiert
>	if (iterator != nullptr) {
>		//Check ob vor dem Iterator schon ein Item Existiert
>		//Wenn ja, Speicher den Vorgänger und gebe den Vorgänger als nodeTail die temp Node
>		//Gib der temp node als nodeHead den Vorgänger
>		if (iterator->nodeHead != nullptr) {
>			node* beforeActuell = iterator->nodeHead;
>			temp->nodeHead = beforeActuell;
>			beforeActuell->nodeTail = temp;
>		}
>		else { 
>			// Falls noch kein Item vor dem Iterator existiert
>			//Setze nodeHead vom temp auf nullptr
>			//Setze head auf unser Temp
>			temp->nodeHead = nullptr;
>			head = temp;
>		}
>		//setze vom Iterator das nodeHead auf unsere neue Node
>		iterator->nodeHead = temp;
>	}
>	else {
>		//Falls noch kein Iterator Existiert AKA tabelle == Emtpy
>		//Setze temp->nodeHead auf nullptr
>		//Gebe dem Head und dem Iterator
>		temp->nodeHead = nullptr;
>		iterator = temp;
>		head = temp;
>		tail = temp;
>
>		cout << "Created an iterator....\n";
>	}
>	cout << "Inserted Item before Iterator....\n";
>
>
>	return true;
>}
>
>template<class item_type>
>bool Tabelle<item_type>::append(item_type r)
>{
>	if(tail!=nullptr)
>	{
>		node* temp = tail;
>
>		node* appendTemp = new node;
>		appendTemp->item = r;
>		appendTemp->nodeHead = temp;
>		appendTemp->nodeTail = nullptr;
>
>		temp->nodeTail = appendTemp;
>		tail = appendTemp;
>	}
>	cout << "Appended Item before Iterator....\n";
>
>	return false;
>}
>
>template<class item_type>
>bool Tabelle<item_type>::first()
>{
>	iterator = head;
>	cout << "Move Iterator to Head... Iterator is now at item: " << iterator->item<<"\n";
>	return false;
>}
>
>template<class item_type>
>bool Tabelle<item_type>::last()
>{
>	iterator = tail;
>	cout << "Move Iterator to Tail... Iterator is now at item: " << iterator->item << "\n";
>	return false;
>}
>
>template<class item_type>
>bool Tabelle<item_type>::next()
>{
>	if (iterator->nodeHead != nullptr) {
>		iterator = iterator->nodeHead;
>		cout << iterator->item << "\n";
>	}
>	else {
>		cout << "ERROR!!! ERROR!!!  ITERATOR IS ALREADY ON HEAD!!!! ERROR!!! ERROR!!!";
>	}
>	return false;
>}
>
>template<class item_type>
>bool Tabelle<item_type>::previous()
>{
>	if (iterator->nodeTail != nullptr) {
>		iterator = iterator->nodeTail;
>		cout << iterator->item << "\n";
>
>	}
>	else {
>		cout << "ERROR!!! ERROR!!!  ITERATOR IS ALREADY ON TAIL!!!! ERROR!!! ERROR!!!";
>	}
>	return false;
>}
>
>template<class item_type>
>bool Tabelle<item_type>::delete_node()
>{
>	node* temp = iterator;
>
>	cout << "Deleting "<< temp->item<<"....\n";
>
>	if(temp->nodeTail!=nullptr)
>	{
>		node* tempHead = iterator->nodeHead;
>
>		iterator = temp->nodeTail;
>
>		iterator->nodeHead = tempHead;
>		if(tempHead!=nullptr)
>			tempHead->nodeTail = iterator;
>		if (iterator->nodeTail == nullptr) {
>			tail = iterator;
>		}
>	}
>	else if (temp->nodeHead != nullptr) {
>
>		iterator = temp->nodeHead;
>
>		iterator->nodeTail = nullptr;
>		if (iterator->nodeHead == nullptr) {
>			head = iterator;
>		}
>	}
>	else{
>		head = nullptr;
>		tail = nullptr;
>		iterator = nullptr;
>	}
>
>	
>	delete temp;
>
>	return true;
>}
>
>template<class item_type>
>void Tabelle<item_type>::show()
>{
>	if(head!= nullptr)
>	{
>		node* temp = head;
>		cout << "\n";
>		cout << "\n";
>		cout << "|                                         |\n";
>
>		cout << "|-----------------------------------------|\n";
>		cout << "|                                         |\n";
>
>		cout<< "Head Item: " << temp->item << "\n";
>		if (temp->nodeTail != nullptr)
>			cout << "Head previous Item:" << temp->nodeTail->item << "\n";
>
>		while (temp->nodeTail != nullptr) {
>			cout << "-------------------------------------------\n";
>			temp = temp->nodeTail;
>			cout << "Item before: " << temp->nodeHead->item << "\n";
>			cout << "Item: " << temp->item << "\n";
>			if (temp->nodeTail != nullptr)
>				cout << "Item after: " << temp->nodeTail->item << "\n";
>
>		}
>	}
>}
>
>template<class item_type>
>bool Tabelle<item_type>::get_node(item_type& r)
>{
>	//cout << "Iterator points to " << iterator->item << " \n";
>	r = iterator->item;
>	return true;
>}
>
>template<class item_type>
>bool Tabelle<item_type>::set_node(item_type& r)
>{
>	iterator->item = r;
>	return false;
>}
>```

>[!code]- main.cpp
>```
>// Exercise_7.cpp : This file contains the 'main' function. Program execution begins and ends there.
>//
>
>#include <iostream>
>#include "Tabelle.cpp"
>
>int main()
>{
>	Tabelle <int> tr;
>	tr.insert(3);
>	tr.show();
>	tr.insert(4);
>	tr.show();
>	tr.insert(5);
>	tr.next();
>	tr.first();
>	tr.next();
>
>
>	tr.append(2);
>	tr.show();
>	tr.previous();
>	int r = 100;
>	tr.set_node(r);
>	cout << r;
>	tr.show();
>	tr.last();
>	tr.previous();
>}
>
>// Run program: Ctrl + F5 or Debug > Start Without Debugging menu
>// Debug program: F5 or Debug > Start Debugging menu
>
>// Tips for Getting Started: 
>//   1. Use the Solution Explorer window to add/manage files
>//   2. Use the Team Explorer window to connect to source control
>//   3. Use the Output window to see build output and other messages
>//   4. Use the Error List window to view errors
>//   5. Go to Project > Add New Item to create new code files, or Project > Add Existing Item to add existing code files to the project
>//   6. In the future, to open this project again, go to File > Open > Project and select the .sln file
>```

Tragen Sie die Resultate der Zeigeroperationen in die unten stehende Skizze ein. Achten Sie dabei auf Sonderfälle (leere Tabelle, iterator=0, iterator=head/tail,….)

![[Algo/Attachment/Übung7_Aufgabe25.md#^group=Dwnl008y]]

![[Algo/Attachment/Übung7_Aufgabe25.md#^frame=RBEwXHtn]]
![[Algo/Attachment/Übung7_Aufgabe25.md#^frame=SFXJuRRp]]
![[Algo/Attachment/Übung7_Aufgabe25.md#^frame=pQUyMefy]]

#### Aufgabe 26
Welche Aufwände entstehen bei den Methoden **find, delete, insert, append** in Aufgabe 22. Von welcher Komplexitätsklasse sind diese Aufwände? Vergleichen Sie die Aufwände im Falle einer Implementierung mit Hilfe eines arrays und mit Hilfe der doppelt verketteten Liste.
[https://www.happycoders.eu/de/algorithmen/stack-implementieren-linked-list](Linked List)
[https://www.happycoders.eu/de/algorithmen/o-notation-zeitkomplexitaet/#O1_-_konstanter_Aufwand](Konstanter Aufwand)

---

**Liste:**
*find*
-> O(n) linear 

*delete*
-> O(1) konstant 

*insert*
-> O(1) konstant

*append*
-> O(1) konstant

---

**Array**
*find*
-> O(n) linear

*delete*
-> O(n) linear

*insert*
-> O(n) linear

*append*
-> O(1) konstant

---

find
-> gleich

delete
-> doppelt verkettete Liste 

insert
-> doppelt verkettete Liste 

append
-> Je nach Implimentierung der liste ist sie schneller/schlechter, sonst gleich