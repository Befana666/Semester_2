
#### What is it?

Eine Turingmaschine besteht aus:
- einer Steuereinheit
	- in einem Zustand der endlichen Zustandsmenge $\mathbb{Z}$
	- einem Programm $f$
	- Startzustand $s$, Endzustand $e$ //freiwählbar
	
- einem Lese und Schreibkopf
	- kann ein Feld lesen und beschreiben
	- sich nach ein Feld bewegen oder stehen bleiben
	
- einem Magnetband
	- ist in Felder unterteilt in dem ein Symbolsteht
	- ist in beide seiten unendlich
	- Leersymbol ist $\square$ 
	
![[TheoInf/Attachments/Turingmaschine.md#^clippedframe=ISc5rKnF]]
Die Turingmachine arbeitet in Takten.

---
#### Programmieren in einer Turingmachine

Jedes Program besteht aus mehreren Zeilen.
Jede zeile ist wie folgt Aufgebaut.

| Wenn Zustand | und Symbol ist |               | ändere Zustand zu | schreib zeichen | bewege in Richtung |                                                                                                            |
| ------------ | -------------- | ------------- | ----------------- | --------------- | ------------------ | ---------------------------------------------------------------------------------------------------------- |
| z            | 1              | $\rightarrow$ | x                 | 0               | L/R/N              | Wenn der Zustand Z ist und das Symbol 1, dann ändere den Zustand zu x schreib 0 und gehe Links/Recht/Nicht |

Die Reihenfolge der Befehle sind egal es wird immer erst auf den Zustand geschaut dann auf das Symbol.
##### Beispiel:

| Wenn Zustand | und Symbol ist |               | ändere Zustand zu | schreib zeichen | bewege in Richtung |                          |
| ------------ | -------------- | ------------- | ----------------- | --------------- | ------------------ | ------------------------ |
| s            | 0              | $\rightarrow$ | s                 | 0               | R                  | geh rechts               |
| s            | 1              | $\rightarrow$ | s                 | 1               | R                  |                          |
| s            | $\square$      | $\rightarrow$ | c1                | $\square$       | L                  | Übertrag 1               |
| c1           | 0              | $\rightarrow$ | c0                | 1               | L                  | Übertrag 0               |
| c1           | 1              | $\rightarrow$ | c1                | 0               | L                  |                          |
| c1           | $\square$      | $\rightarrow$ | e                 | 1               | N                  | $\stackrel{\text{1}}{=}$ |
|              |                |               |                   |                 |                    |                          |
| c0           | 0              | $\rightarrow$ | c0                | 0               | L                  | $\stackrel{\text{2}}{=}$ |
| c0           | 1              | $\rightarrow$ | c0                | 1               | L                  |                          |
| c0           | $\square$      | $\rightarrow$ | e                 | $\square$       | R                  | $\stackrel{\text{3}}{=}$ |
$\stackrel{\text{1}}{=}$ Wenn die Zahl links mit einem Übertrag verlassen wird: 1 Schreiben $\rightarrow$ fertig
$\stackrel{\text{2}}{=}$ kein Übertrag $\rightarrow$ nach links laufen
$\stackrel{\text{3}}{=}$ am Ende einen Schritt nach Rechts, so das der Kopf auf dem ersten Zeichen der Ausgabe steht

![[TheoInf/Definitionen#^6c8843]]

----
##### Beispiel:

$f_3:\{a,b\}^* \rightarrow \{a,b\}^*$ mit //$f_3$ hat die Eingabewerte a und b und davon so viele wie man will
$$f_3(x) = \begin{cases} a^nz& \text{, falls } x = a^bz \text{ für ein } z\in\{a,\}*\\ x & \text{, falls x kein b entält}\end{cases}
$$


>[!Info] Erklärung
>- Das Wort x besteht aus Zeichen a und b.
>- Falls irgendwo ein erstes bbb vorkommt, wird dieses erste b entfernt.
>- Alles davor ($a^n$) und alles danach (z) bleibt erhalten.
>- Wenn gar kein b vorkommt, bleibt das Wort unverändert

//ToDo if asked add programm

---
