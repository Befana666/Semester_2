#### Description:

Im Moodle finden Sie einen Interpreter, der eine einfache Programmiersprache namens MJava, die den split-Befehl unterstützt, simulieren kann. Der Interpreter ist in Java geschrieben, Sie können ihn also nur benutzen, wenn Sie Java (Version 1.8 oder höher) auf Ihrem Rechner installiert haben. Der Interpreter kann von Shell/Kommandozeile wie folgt gestartet werden:
```
java -jar mjava.jar <Programm>
```

 Dabei ist \<Programm\> der Dateiname eines MJava-Programms. 
 Die Sprache MJava sollte keine großen Hürden für Menschen darstellen, die bereits C oder C++ oder Java können, da es sich um eine stark abgespeckte Variante dieser Sprachen handelt. Es handelt sich nicht um eine Objektorientierte Sprache, Klassen können also nicht definiert werden. Das komplexeste zulässige Konstrukt sind Funktionen, welche aber wie gewohnt definiert werden dürfen. (Deklarationen von Funktionen ohne zugehörige Definition ist nicht erlaubt. Es können keine externen Programmdateien (via include oder import) eingebunden werden. 
 In der Sprache ist es auch nicht möglich komplexe Datentypen zu entwerfen. 
 
 Folgende Typen sind aber zulässig:
 - int
 - long
 - float
 - double
 - String
 - boolean 
 
 Diese verhalten sich wie gewohnt. Strings können, wie in Java, unter Verwendung von + konkateniert werden. Strings können mit dem Operator + auch mit Ausdrücken eines anderen Typs konkateniert werden. Z.B. ist das Ergebnis des Ausdrucks "bla" + 7 gleich dem String "bla7" . Zur Ausgabe auf Konsole dient eine interne Funktion println (z.B.: println("Hello World!")). 
 
 Arrays über obige Datentypen sind erlaubt. Ein neues Array kann wie in Java wie folgt deklariert und initialisiert werden:
 - int\[\] a = new int\[10\]; //Erzeugt ein int-Array mit 10 Elementen, die alle mit 0 initialisiert sind
 - int\[\] a = new int\[\]{5, 6, 7}; //Erzeugt ein int-Array mit 3 Elementen, die mit den Werten 5, 6 und 7 initialisiert sind
 
 In MJava kann die Länge eines Arrays über die eingebaute Funktion length bestimmt werden. Ist also z.B. a wie oben (2. Beispiel) initialisiert, so liefert der Ausdruck length(a) den Wert 3 zurück. 
 
 In MJava gibt es die split-Anweisung, die die Berechnung auf zwei Maschinen aufteilt. Die Syntax des split-Befehls ist wie folgt: 
 
 ```
 split <Wertzuweisung1> and <Wertzuweisung2>
 ```
 
 Dabei sind \<Wertzuweisung 1\> und \<Wertzuweisung 2\> Wertzuweisungen der Form 
 
 ```
 <Variable> = <Wertausdruck> ;
 ``` 
 
 **Beispiel:**
 Der folgende Code ist eine gültige split-Anweisung: 
 
 ```
 split x = 5; and x = 7;
 ```
 
Sie bewirkt, dass nach ihrer Ausführung zwei parallele Rechenwege existieren, wobei im ersten dieser Rechenwege die Variable x den Wert 5 annimmt und im zweiten Rechenweg den Wert 7. 
Die Wirkung des split-Befehls besteht darin, dass vor Ausführung von \<Wertzuweisung 1\> und \<Wertzuweisung 2\> zwei identische Kopien der ausführenden Maschine gemacht werden (also inklusive Speicherinhalt und aktueller Zu- stand des Programms) die danach parallel weiterarbeiten wobei die eine mit <Wertzuweisung 1> und die andere mit \<Wertzuweisung 2\>. 
Mit Hilfe des split-Befehls können also mehrere parallele Berechnungspfade erzeugt werden. Ein MJava-Programm hält akzeptierend, falls die main-Methode den Rückgabetyp boolean besitzt und es mindestens einen parallelen Rechenweg gibt, der dazu führt, dass die Rückgabe der main-Methode den Wert true besitzt. In allen anderen Fällen hält ein MJava- Programm ablehnend. 
#### 1. Aufgaben:
Im Moodle finden Sie auch eine Reihe von .mjava Programmen. Sehen Sie sich das Programm easy.mjava und überlegen Sie sich was es tun und ausgeben wird. Starten Sie über Kommandozeile dieses Programm indem Sie 

```
java -jar mjava.jar easy.mjava
``` 

eingeben. Verstehen Sie die Ausgabe und wie sie mit dem Programm zusammenhängt. 
#### 2. Aufgabe:
Betrachten Sie nun das Programm counting.mjava. Überlegen Sie, was es tut und was seine Ausgabe sein wird! Lassen Sie das Programm laufen und beantworten sie folgende Fragen: 

##### (a) Warum hält das Programm ablehnend? 

Weil y kleiner 1023 ist.
##### (b) Was ist der größte Wert, den sie statt 1023 einsetzen können, so dass das Programm akzeptierend hält. Warum können Sie keinen größeren/ kleineren Wert wählen? 

>[!code] counting.mjava
>```
>boolean main() {
>
>    int x = 1;
>    int y = 0;
>    
>    for (int i = 0; i < 10; i++) {
>        split y = y; and y = y + x;
>        x = x * 2;
>    }
>    println(y);
>    return y > 1022;
>    
>}
>```

//For loop goes for 10 rounds
//0+1, 1+2, 3+4, 7+8, 15+16, 31+32, 63+64, 127+128, 255+256, 511+512

1022 ist die größte zahl für die das Program auf accepting hält, da y 1023 ist nach 10 druchläufen.

Alle werte kleiner währen acceptable. Bei keinem Wert größer würde das Programm auf accepting halten.
##### (c) Wie viele unterschiedliche Werte werden per println ausgegeben?

$n^2$ Werte werden pro println ausgegeben. Da sich die Anzahl der Pfade mit jedem Schritt verdoppeln.

![[TheoInf/Attachments/Übung 7.md#^clippedframe=BpDmURzP]]
##### (d) Erklären Sie, warum die Laufzeit des Programms nur 67 Schritte ist, obwohl über 1000 Ausgaben gemacht werden! 

//Jede Anweisung ist ein Schritt
//Es sind nur 66 Schritte

Beim allerersten durchlauf sind es 12 Steps:
	1) int x=1
	2) int y =0
	3)  for() //is worth 4 in total
	4) int i = 0
	//Ab hier wiederholt sich der code bis zum ende der for schleife
	5) i<1
	6) split 1: calc
	7) split 2: calc
	8) split 1: $x=x*2$
	9) split 2: $x=x*2$
	10) i++
	//Ende for schleife
	11) println
	12) return

Davon sind 6 immer gleich, die Anzahl ändert sich nicht basierend auf dem input.
Die restlichen 6 ist der vergleich ob i kleiner 10 ist die berechnungen und dann den +1 für i.

Wichtig er geht nicht durch jedes durch für jede for schleife sondern generiert einen neuen Wert für jede forschleife 

1) 12
2) 18
3) 24
4) 30
5) 36
6) 42
7) 48
8) 54
9) 60
10) 66

![[TheoInf/Attachments/Übung 7.md#^frame=88Fzwi1Ymj8YMi4jqSoqQ]]

Alle Schritte werden gleichzeitig durchgeführt, wobei Schritte hier misleading ist. Jede neue zeile adds die 6 neuen schritte nicht mehr nicht weniger weil alles gleichzeitig läuft.

##### (e) Wie lange müsste die Schleife mindestens laufen, damit über 64000 Ausgaben gemacht werden? 
17 Schleifendurchläufe oder bis i < 16 ist da wir ja bei 0 starten
#### Aufgabe 3:
Es sei das Problem PARTITION wie folgt definiert: 
$$
\text{PARTITION} \stackrel{\text{def}}{=}\{(c1,\ c2,\ c3,\ ....,\ cn) \text{: es gibt ein }I\subseteq \{1,\ ...,\ n\}\text{, mit } \sum\limits_{i \in I}^{} {c_i=\sum\limits_{i \not \in I}^{} {c_i}}\}
$$
// means it should split into 2 groups whose sums are equal

![[Extras#^b9b00a]]

**Beispiele:**
- (5, 3, 6, 7, 2, 8, 12, 13) ∈ PARTITION, weil für I = {2, 7, 8} gilt: 
		//die 2,7,8 sind die indexes
	$$
	\sum\limits_{i \in I}^{} {c_i} = 28 = \sum\limits_{i \not \in I}^{} {c_i}
	$$
	wobei c1 = 5, c2 = 3, c3 = 6, c4 = 7, c5 = 2, c6 = 8, c7 = 12, c8 = 13.
	
	
- (11, 12, 15, 4, 19, 8, 16, 3) $\not \in$ PARTITION, weil es kein I ⊆ {1, . . . , 8} gibt, so dass $\sum\limits_{i \in I}^{} {c_i=\sum\limits_{i \not \in I}^{} {c_i}}$

Schreiben Sie ein ein nichtdeterministisches MJava-Programm, das das PARTITION-Problem in Polynomialzeit löst! Schreiben Sie dazu am besten eine Methode mit dem Kopf 

```
boolean inPARTITION(int n, int[] a);
```

die true zurückgibt, falls sie eine Lösung für das gegebene PARTITION-Problem gefunden hat. Benutzen Sie den Nichtdeterminismus und bedenken Sie, dass sie mitunter verschiedene parallele Rechenwege am Laufen haben (falls Sie den split-Befehl einsetzen) und das es genügt auf einem der parallelen Rechenwege eine Lösung zu finden. 

Testen Sie Ihr Programm an den oben aufgeführten Beispielen! 

>[!code]- partition.mjava
>```
>boolean SOS(int n, int[] a, int b) 
>{
>    //loop through first array
>    for (int i = 0; i < n;i++) {
>        int counter = 1; //counts upwards so we can skip values
>        int sum = a[i];
>
>        //loop through the array again till either
>        //Sum is bigger than target
>        //reached end of array
>        //or sum is equal target
>        for (int j = i + counter; j < n; j++) 
>        {
>            println("counter: " +counter);
>            int a2 = a[j];
>            int test= sum+a2;
>            println(sum +" + "+ a2 +" = " +test);
>            sum =sum+ a2;
>            if (sum == b) 
>            {
>                return true;
>            }
>            else if (sum > b) 
>            {
>                println("-----------------");
>                if (i + counter < n) 
>                {
>                    j = i + counter;
>                    counter++;
>                }
>                sum = a[i];
>            }
>        }
>    }
>    return false;
>}
>
>boolean inPartition(int n, int[] a) 
>{
>    int sum = 0;
>    for (int i = 0; i < n;i++) 
>    {
>	    sum = sum+ a[i];
>    }
>	if (sum % 2 != 0) 
>    {
>        println("----------------");
>        println("Can't be a partition.");
>        println("----------------");
>		return false;
>	}
>    println("----------------");
>
>	int partSum = sum / 2;
>    println("Total Sum: " + sum); 
>    println("Part Sum: " + partSum); 
>
>    return SOS(8,a,partSum);
>}
>
>boolean main() {
>    int [] a= new int[]{5, 3, 6, 7, 2, 8, 12, 13};
>	return inPartition(8,a);
>}
>```

#### Aufgabe 4:
##### (a) Zeigen Sie: PARTITION ≤ SOS 
Partition hat On^2 und sos hat On^3 
##### (b) Zeigen Sie: SOS ≤ PARTITION
Partition hat On^2 und sos hat On^3 