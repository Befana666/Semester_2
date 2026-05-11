#### 5.1 Klassenbeziehungen definieren
In der Abbildung sind die Klassen eines E-Mail Programms als UML-Klassen dargestellt. 

Das E-Mail Programm besteht aus den Klassen: 
- AddressBook: Ein Adressbuch, das Personen verwaltet.
- Person: Eine Person mit ihrem Vor- und Nachnamen.
- Mailbox: Ein Postfach, das E-Mails verwaltet.
- Mail: Eine E-Mail mit Sender, Empfänger und Inhalt (body).

![[Exercise5 Abbildung1]]

Einige der Klassen stehen in Beziehung zueinander. 

>[!Cheatsheet]- UML
>![[UML Beziehungesrichtungen]]
##### a) Überlege, welche Art der Beziehung (Abhängigkeit, Assoziation, Aggregation, Komposition) nach folgender Beschreibung am passendsten ist und ob die Beziehung gerichtet oder ungerichtet ist. Begründe, warum Du dich für die entsprechende Beziehung und gegen die anderen Beziehungen entschieden hast.
###### i. Ein Adressbuch enthält eine beliebige Anzahl von Personen (auch keine). Personen kennen ihr Adressbuch nicht. 
	Eine Gerichtete Beziehnung, da nur das Addressbuch die Personen enthalten aber die Personen das Addressbuch nicht kennen. Das Addressbuch hat eine 0...* beziehung.
###### ii. Ein Postfach enthält eine beliebige Anzahl von E-Mails (auch keine). E-Mails kennen ihr Postfach nicht. 
	Die selbe Beziehung wie oben.
###### iii. Eine E-Mail hat genau einen Absender und mindestens einen Empfänger. Personen kennen E-Mails, in denen sie Absender oder Empfänger sind, nicht. iv. Eine Person kann eine beliebige Anzahl von Freunden haben (auch keine).  
Email 1 zu absender 1. Email 1 zu Empfänger 1...*. 
	Da die Personen die Email nicht kennen geht der pfeil immer in richtung der email.
	Freunde sind Bidirektional 0...*.

##### b) Trage die Beziehungen in UML-Notation in die Abbildung ein. Trage nur Beziehungen ein, keine Attribute oder Methoden. Beschrifte die Beziehungen wenn möglich mit Stereotypen, Rollennamen und Multiplizitäten. 
siehe c
##### c) Überlege, ob neben den beschriebenen Beziehungen noch weitere Abhängigkeiten zwischen den Klassen bestehen könnten und trage diese ebenfalls in die Abbildung ein. 
![[Drawing 2026-04-28 13.11.35.excalidraw]]
##### d) Betrachte die Abbildung. Hier wurde das String-Attribut ”body“ der Klasse ”Mail“ entfernt und durch eine Assoziation zu einer neuen Klasse ”MailBody“ ersetzt. Betrachte diese neue Architektur und beantworte die folgenden Fragen: 
![[Drawing 2026-04-28 14.09.51.excalidraw]]
###### i. Um welche Art von Klasse handelt es sich bei ”MailBody“ und was zeichnet solche Klassen aus? 
Es ist eine Interface Klasse. Interface klassen können erweitert und realisiert werden.
![[Interface Klassen#^9a86d2]]
###### ii. Welche Vorteile hat die neue Architektur gegenüber der alten Architektur mit dem String- Attribut? 

Man muss sich nicht strikt an den string type halten sonder kann den body auch mit sachen wie z.B. HTML inhalten füllen weitere Arten können einfach weitere kind klassen implementiert werden.
###### iii. Was ist die Aufgabe der Klassen ”PlainText“ und ”HtmlMarkup“ und warum müssen diese die Methode ”getContent()“ überschreiben?
Da bei PlainText der Inhalt nur als string verarbeitet wird aber beim HTMLMarkup der als HTML interpretiert werden muss.

>[!Warning] 
>Als realisierende Klassen der Schnittstellenklasse müssen die Klassen ”PlainText“ und ”HtmlMarkup“ die Methode ”getContent()“ überschreiben und implementieren. Würden
sie dies nicht tun, würden sie die Schnittstellenklasse nicht vollständig implementieren (sondern
erweitern) und könnten nicht instanziiert werden.

#### 5.2 Klassenbeziehungen implementieren

In der Abbildung ist ein UML-Klassendiagramm eines Verwaltungssystems einer Universität dargestellt. Das System besteht aus den Klassen: 
- Address: Postanschrift eines Gebäudes, bestehend aus Straße, Stadt und Land.
- Person: Eine Person mit Vor- und Nachnamen. 
- University: Eine Universität mit Namen. 
- Faculty: Eine Fakultät mit Namen.
Die Beziehungen zwischen den Klassen sind bereits in UML-Notation in der Abbildung festgelegt. 

![[Drawing 2026-04-28 14.17.11.excalidraw]]
##### a) Erstelle ein neues Projekt und implementiere die vier Klassen aus dem Diagramm mit ihren Attributen. Die Attribute sollen über einen Konstruktor initialisiert werden und über public Getter-Methoden zugänglich sein. 
##### b) Implementiere die Kompositionen von Person und University aus Address. Stelle bei der Implementierung sicher, dass die komponierten Objekte nicht ohne ihr Kompositionsobjekt existieren können. 
##### c) Implementiere die Aggregation zwischen University und Faculty. Stelle sicher, dass sich Instanzen beider Klassen gegenseitig erreichen können (ungerichtet / bidirektional). Implementiere Multiplizitäten größer eins als Array fester Größe, das an nicht-genutzten Indices mit Nullpointern gefüllt ist. 
##### d) Implementiere die Assoziationen von University und Faculty zu Person. Implementiere Multiplizitäten größer eins als Array fester Größe, das an nicht-genutzten Indices mit Nullpointern gefüllt ist. 
##### e) Implementiere die Methoden in University um Fakultäten hinzufügen und entfernen zu können und in Faculty um Professoren und Studenten hinzuzufügen und entfernen zu können. 
##### f) Erstelle ein Testprogramm (main()-Methode), in dem Du Instanzen der Klassen erstellst und miteinander verknüpfst. Du kannst z.B. die Hochschule Kempten abbilden.
- Erstelle den Präsidenten der Universität / Hochschule als Person-Instanz mit Namen und Adresse.
- Erstelle eine Universität / Hochschule mit Namen, Adresse und dem Präsidenten.
- Erstelle mindestens zwei Fakultäten mit Namen und verknüpfe sie mit der Universität / Hochschule.
- Erstelle mindestens einen Professor und einen Studenten (jeweils mit Namen und Adresse) und verknüpfe sie mit einer Fakultät. 

Gib dann auf Basis des Universitätsobjekts die Attribute der Universität (Name) und die ver- knüpften Objekte mit dieser (Adresse, Präsident, Fakultäten mit Professoren und Studenten) in der Konsole aus.

#### 5.3 Code-Organisation 
Diese Aufgabe befasst sich mit der Programmstruktur von C++-Programmen und resultierenden Besonderheiten, auf die bei der Implementierung von Klassen und deren Beziehungen geachtet werden muss. Nutze zur Bearbeitung der Aufgaben die Vorgabe mit den Dateien Game.h, Item.h, Player.h, Enemy.h und Exercise5 3 Vorgabe.cpp, die dem Übungsblatt beiliegt. Diese definieren typische Objekte einer Game-Engine. 
##### a) Erstelle ein neues Projekt und binde die oben genannten Quelldateien darin ein. Beim Versuch das Projekt zu kompilieren, kommt es zu dem Fehler ”Nicht deklarierter Bezeichner“/”undeclared identifier“. Kannst Du diesen Fehler durch Vertauschen der Headerinkludierungen im Hauptprogramm (.cpp-Datei in der sich die main()-Funktion befindet) lösen? Wenn ja: wie? Wenn nein: warum nicht? 
##### b) Erstelle in den Headerdateien Vorausdeklarationen, sodass es bei derer Inkludierung zu keinen undefinierten Typen/Bezeichnern mehr kommt. Verändere die Reihenfolge, in der die Headerdateien im Hauptprogramm inkludiert werden und überprüfe ob sich alle Kombinationsmöglichkeiten kompilieren lassen. Inkludiere insbesondere den Game.h Header einmal zu Beginn und einmal zuletzt. 
##### c) Könnten die vorausdeklarierten Klassen auch ohne Zeiger oder Referenzen an Methoden übergeben und direkt als Membervariablen abgespeichert werden? Begründe deine Antwort. 
##### d) Die Klassen sollen nun in Namensräumen organisiert werden. Definiere dazu einen Namensraum ”MyGameEngine“ und die Unternamensräume ”Core“ und ”Objects“, die dem MyGameEngine Namensraum untergeordnet sind. Die Klassen sollen sich wie folgt in den Namensräumen befin- den: :: MyGameEngine Core Game Objects Item Player Enemy 

>[!Note]- Hinweis: 
>Bei der Einführung von Namensräumen müssen auch die Vorausdeklarationen den jeweiligen Namensräumen untergeordnet sein, in denen sich die vorausdeklarierten Klassen befinden. Ist das nicht der aktuelle Namensraum der Definitionen, müssen die Vorausdekla- rationen separat in ihrem Namensraum angegeben werden. 
##### e) Die Header und das Hauptprogramm inkludieren einen Header der Standardbibliothek mehr- fach. Erstelle einen vorkompilierten Header und inkludiere Bibliotheksheader dort, statt in den einzelnen Header- und Quelldateien. Erstelle auch für jeden Klassenheader eine .cpp-Datei, die den vorkompilierten Header nutzt.

Überprüfe ob die Compiler-Einheit des vorkompilierten Headers vor allen anderen Compiler- Einheiten kompiliert wird und ob sich das Projekt nach den änderungen noch problemlos kompilieren lässt. 

>[!Note]- Hinweis: 
>Um vorkompilierte Header zu nutzen, sind neben der Erstellung neuer Dateien auch änderungen an den Projekteinstellungen nötig. Informiere dich dazu online, wie vor- kompilierte Header bei deinem Compiler / deiner Entwicklungsumgebung umgesetzt werden können.