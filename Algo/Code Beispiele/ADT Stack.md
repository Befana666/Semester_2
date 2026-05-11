>[!code]+ stack.h
>```
>template <class Tr>
>class Stack // Stapel für Records von beliebigem Typ Tr 
>{ 
>public: 
>	Stack(unsigned max);// leerer Stapel für max Records 
>	~Stack(); //Destruktor 
>	
>	void Push(Tr r); // legt Record r oben auf Stapel 
>	Tr Pop(); // holt obersten Record vom Stapel 
>	Tr Top(); // liefert den Wert des obersten Records 
>
>	unsigned Length(); // Anzahl der Records im Stapel 
>	boolean IsEmpty(); // true, wenn Stapel leer, sonst false 
>	boolean IsFull(); // true, wenn Stapel voll, sonst false
>
>private: 
>	unsigned m; // Arraylänge m 
>	unsigned top; // oberste array-Position im 
>	Stack Tr *a; // Zeiger auf Array 
>};
>```

^4b10d0


>[!code]+ stack.cpp
>```
>// Konstruktor: 
>// legt Speicherplatz für max Records an 
>// Setzt top auf 0 und m auf max 
>template <class Tr> 
>Stack<Tr>::Stack(unsigned max)
>{ 
>	m=max;
>	a=new Tr[m];
>	top=0; 
>}
>
>// Destruktor loescht alle Eintraege im Stack 
>template <class Tr>
>Stack<Tr>::~Stack()
>{ 
>	delete a[];
>}
>
>// oben im Stapel ablegen, Bedingung: Stapel nicht voll 
>/template <class Tr> 
>void Stack<Tr>::Push(Tr r) 
>{ 
>	if (!IsFull()) 
>	{
>		a[top]=r; top++;
>	} 
>	else 
>		printf(„Stack ist voll - Push() nicht möglich“); 
>}
>
>// obersten Record holen und entfernen, // Bedingung: Stapel nicht leer 
>template <class Tr> 
>Tr Stack<Tr>::Pop()
>{
>	Tr r;
>	if (!IsEmpty())
>	{
>		top--; r = a[top]; return r;
>	}
>	else printf(„Stack ist leer - Pop nicht möglich“);
>}
>// Wert des obersten Records im nicht leeren Stapel zurückgeben
>template <class Tr> 
>Tr Stack<Tr>::Top()
>{
>	Tr r;
>	if (!IsEmpty())
>	{
>		r = a[top - 1]; return r;
>	}
>	else printf(„Stack ist leer - Top() nicht möglich“);
>}
>
>// Anzahl der Records im Stapel zurückgeben 
>template <class Tr>
>unsigned Stack<Tr>::Length() 
>{
>	return top; 
>}
>
>// prüfen, ob Stapel leer ist 
>template <class Tr> 
>boolean Stack<Tr>::IsEmpty()
>{
>	if (top == 0)
>		return true;
>	else return false;
>} 
>
>// prüfen, ob Stapel voll ist  
>template <class Tr> 
>boolean Stack<Tr>::IsFull()
>{
>	if (top == m)
>		return true;
>	else return false;
>}
>```

^f91b1c
