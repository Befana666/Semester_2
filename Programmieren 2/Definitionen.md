>[!definition]+ Deklarationen 
>___
>Führen Entitäten in einem Programm ein und spezifizieren ihren Datentypen.
>
>---
>Du erstellst eine Variable aber gibst ihr noch keine Werte.

^2edd57

>[!definition] Funktionen 
>___
>
>Funktionen spezifizieren die Operationen eines nutzerdefinierten Prozesses.
>- Eine Funktion muss <span style ="color:red; font-weight:bold ">deklariert</span> sein, um aufgerufen zu werden aka <span style ="color:red; font-weight:bold ">Funktionsprototyp</span>
>Die Deklaration besteht aus:
>- <span style ="color:red; font-weight:bold ">Rückgabetyp</span> der Funktion (void, wenn es keinen Rückgabewert gibt)
>- <span style ="color:red; font-weight:bold ">Name</span> der Funktion
>- Anzahl und Typen der <span style ="color:red; font-weight:bold ">Argumente</span>, die beim Funktionsaufruf übergeben werden müssen
>---
>
>Wie bei den Klassen, damit kannst du die Ordnung der Funktionen ein bisschen loser gestallten sollange die Deklaration über der Funktion steht sollte es funktionieren selbst wenn die Funktion selbst wo anderst steht

^93d643

>[!definition] Objektübergaben
>___
>Als <span style ="color:red; font-weight:bold ">Objektübergabe</span> wird die Zuweisung des Werts eines Objekts auf ein anderes Objekt bezeichnet
>
>Ein Objekt kann grundsätzlich auf zwei verschiedene <span style ="color:red; font-weight:bold ">Arten</span> übergeben werden
>- <span style ="color:red; font-weight:bold ">Call-by-value</span>: Der Wert des Objekts (=value) wird direkt übergeben und dabei kopiert (``` text(1);```)
>- <span style ="color:red; font-weight:bold ">Call-by-reference</span>: Der Wert des Objekts wird indirekt über eine Referenz übergeben (``` text(int & var);```)
>
>In C++ wird die Art der Objektübergabe immer explizit definiert und ist von keinen Compilerregeln abhänig!!
>  
>  Vergleich Java, Python, ..., Call by value where value could be a reference.
>  ---
>  
>  Du gibst Werte/Variabeln an eine Funktion weiter. 
>  Oder einen Wert einer Variable an eine andere Variable

^5eddb9

>[!definition] Scope 
>___
>
>Ein Gültigkeitsberiech (=Scope) wird mit geschweiften Klammern definiert.
>- Es braucht keine vorhergehende Anweisung oder Deklaration
>- Ein Objekt/Variable ist nur in ihrem **umschließenden Scope** gültig
>
>Unter einer Anweisung (z.B. IF) definieren sie den Inhalt der Anweisung.
>
>---
>Also die Geschweiftenklammern nach if's for und ähnlichem aber auch die Geschweiftenklammern nach nach dem Funktionsnamen und ähnlichen.
>Zählen alle da rein, und makieren einen Scope

^02342e

>[!definition] Lebenszeit
>___
>Unter <span class="redHigh">Lebenszeit</span> eines Objekts wird betrachtet, wie lange ein Objekt **nach seiner Erzeugung** existiert.
>
>Entscheidend für die Lebenszeit ist der <span class="redHigh">Speicherbereich</span>, in dem ein Objekt beheimatet ist
>
>Unterschieden wird zwischen 5 Arten der <span class="redHigh">Speicherdauer</span>(storage durations)
>- <span class="redHigh">automatisch</span>: Das Objekt lebt so lange, wie es in seinem umschließenden Scope gültig ist (Standart)
>- <span class="redHigh">dynamisch/manuell</span>: Das Objekt lebt so lange, bis es manuell drch den Programmierenden gelöscht wird
>- <span class="redHigh">statisch</span>: Das Objekt lebt so lange, bis das gesamte Programm beendet wird

^fb4660

