#### Ziele:
- Aussagen lesen und aufstellen
- eigenständig mit Wahrheitstafeln arbeiten
- Quantoren und Prädikate arbeiten

#### Beispiele Aussagen:
- Der Mars ist blau
- 36 ist eine Primzahl und 4 teilt 36.

#### Why:
- mathematische Sachverhalten formulieren
- Sprachliche Ungenauigkeiten beseitigen
- Wahrheitsgehalt untersuchen
- Mathematische Beweise lassen sich klar und präzise führen

![[Definition#^2f0e99]]

Es gibt Sätze die keine Aussagen sind und auch Sätze die weder ja oder nein sind.

#### Wahrheitswertbestimmung
1. Der Wahrheitswert <span style="color:lightgreen">atomarer Aussagen</span> wird festgelegt. $\Rightarrow$[[Extra#^e9fe84|Atomare Aussagen]]
2. Eine <span style="color:lightgreen">Wahrheitsfunktion $\phi$</span> definiert für jede atomare Aussage einen Wahrheitswert 
	aus {*w*,*f*}; die Wahrheitsfunktion $\phi$ ist dann vom jeweiligen Anwendungsbereich abhänig.
3. Atomare Aussagen bilden zusammen mit sog. <span style="color:lightgreen">Junktoren</span> zusammengesetzer Aussagen. $\Rightarrow$[[Extra#^d48538|Junktoren]]
4. Der Wahrheitswert zusammengesetzter Aussagen ergibt sich aus den Wahrheitswerten der atomaren Aussagen und festen Regeln für die Junktoren.


Gegeben: Menge der Wahrheitswerte {*w*,*f*}

W: immer wahre Aussage
F: immer falsche Aussage

Menge atomarer Aussagen {W, F, A, B, C, ....} Wahrheitsfunktion
$$\phi:\{W,\ F,\ A,\ B,\ C,\ ...\}\rightarrow\{w,\ f\},\ \ \ \ X\rightarrow\phi(X)\in\{w,\ f\}$$
	Bedeuted: Für eine Menge $\phi$ die nur die Werte w oder f annehmen kann. Ist X ein Element dieser Menge das nur w oder f sein kann.

- Eine Wahrheitsfunktion auf der Menge der <span style="color:lightgreen">atomarer Aussagen</span> liefert eine <span style="color:lightgreen">Belegung (Interpretation)</span> der atomaren Aussagen mit Wahrheitswerten.
- Aussagen- und Prädikatenlogik liefern Grundgesetze und Regeln, die die Bestimmung des Wahrheitswertes einer zusammengesetzten Aussage erlauben. 
---
#### Wahrheitstafeln

![[Definition#^4d7e66]]

![[Definition#^129143]]

![[Definition#^21a45f]]

![[Definition#^fcda15]]

![[Definition#^7b8f0e]]

![[Definition#^647e37]]

![[Definition#^f6456a]]

##### Übung 1: 

$A \Rightarrow B = \lnot A\lor B$

| $A$ | $B$ | $\lnot A$ | $\lnot A \lor B$ | $A \Rightarrow B$ |
| --- | --- | --------- | ---------------- | ----------------- |
| 0   | 0   | 1         | 1                | 1                 |
| 0   | 1   | 1         | 1                | 1                 |
| 1   | 0   | 0         | 0                | 0                 |
| 1   | 1   | 0         | 1                | 1                 |

---
#### Regeln von de Morgan

![[Definition#^c7852c]]

##### Übung 2: Regeln von de Morgan

$$(\lnot A) \lor (\lnot B) = \lnot (A\land B)$$
| $A$ | $B$ | $\lnot A$ | $\lnot B$ | $(\lnot A) \lor (\lnot B)$ |     | $A\land B$ | $\lnot (A\land B)$ |
| --- | --- | --------- | --------- | -------------------------- | --- | ---------- | ------------------ |
| 0   | 0   | 1         | 1         | 1                          |     | 0          | 1                  |
| 0   | 1   | 1         | 0         | 1                          |     | 0          | 1                  |
| 1   | 0   | 0         | 1         | 1                          |     | 0          | 1                  |
| 1   | 1   | 0         | 0         | 0                          |     | 1          | 0                  |

#### Normalformen

Für jeden logischen Ausdruck, lässt sich mit einer Wahrheitstabelle ein logisch äquivalenter Ausdruck ableten, der nur aus atomaren [[Extra#^e9fe84|Atomare Aussagen]], Konjunktion, Disjunktionen und Negationen aufgebaut ist. [[Extra#^d48538|That was?]]

>[!Extra]+ Disjunktive Normalform (DNF)
>---
>Ausdruck ist Disjunktion aus Konjunktionen und Negationen.
>
>Beispiel: $(A\land \lnot B) \lor (A \land \lnot B\land C) \lor (B \land C) \lor D$


>[!Extra]+ Konjunktive Normalform (KNF)
>---
>Ausdruck ist Disjunktion aus Konjunktionen und Negationen.
>
>Beispiel: $(A\lor B\lor C) \land (A \lor B\lor \lnot C) \land (\lnot A \lor B \lor C) \land (\lnot A \lor \lnot B \lor C)$

---
#### [[Extra#^0f932c|Axiome]] der Aussagenlogik

1. **Assoziativegesetz** $$\begin{aligned}(A\lor B) \lor C = A \lor (B \lor C) \\ (A\land B) \land C = A \land (B \land C)\end{aligned}$$
2. **Kommutativgesetze**$$\begin{aligned}A \lor B = B\lor A \\ A\land B = B \land A\end{aligned}$$
3. **Distributivegesetz**$$\begin{aligned} A\lor (B\land C) = (A\lor B)\land (A\lor C) \\ A\land (B\lor C) = (A\land B)\lor (A\land C)\end{aligned}$$
4. **Absorptionsgesetze**$$\begin{aligned} A\lor (A\land B) = A \\ A\land (A\lor B) = A\end{aligned}$$
5. **Idempotenzgesetze**$$\begin{aligned}A\lor A=A\\ A\land A = A\end{aligned}$$
6. **Ausgeschlossener Dritter** $$\begin{aligned}A\lor (\lnot A) = W \\ A\land (\lnot A)= F \end{aligned}$$
7. **De Morgansche Regeln** $$\begin{aligned}(\lnot A)\lor (\lnot B) = \lnot (A\land B) \\ (\lnot A)\land (\lnot B) = \lnot (A\lor B)\end{aligned}$$
8. **Gesetze für W und F** $$\begin{aligned}A\land F= F\ \ \ \ \ \ \ \ \ \   A\lor F = A\\ sowie\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \\A\land W = A \ \ \ \ \ \ \ \ \ \ A\lor W = W\end{aligned}$$
9. **Negation** $$\begin{aligned}\lnot W = F \\ \lnot F = W\end{aligned}$$
10. **Doppelte Negation**$$\lnot (\lnot A)=A$$
#### Tautologien und Kontradiktionen

![[Definition#^131516]]

![[Definition#^8eab43]]

##### Übung 3: Beweise $(\lnot A \land B) \lor (A\land B) \Leftrightarrow B$
Beweisen Sie mit Hilfe einer Wahrheitstafel$$(\lnot A \land B) \lor (A\land B) \Leftrightarrow B$$

| A   | B   | $\lnot A \land B$ | $A\land B$ | $(\lnot A \land B) \lor (A\land B)$ | $(\lnot A \land B) \lor (A\land B) \Leftrightarrow B$ |
| --- | --- | ----------------- | ---------- | ----------------------------------- | ----------------------------------------------------- |
| 0   | 0   | 0                 | 0          | 0                                   | 0                                                     |
| 0   | 1   | 1                 | 0          | 1                                   | 1                                                     |
| 1   | 0   | 0                 | 0          | 0                                   | 0                                                     |
| 1   | 1   | 0                 | 1          | 1                                   | 1                                                     |

#### Aussageformen

![[Definition#^d76148]]

##### Beispiele
- A(x) = "x ist größer als 4" //einstelliges Prädikat
- B(x) = "x ist eine Amsel"
- C(x,y) "x ist kleiner als y" //zweistelliges Prädikat
- D(x, y, z)= "x ist kleiner als 0.3 und y ist größer als -0.5 und z ist gleich x+y" // dreistelliges Prädikat


#### Quantoren

Um Prädikate exakt quantifizieren zu können, verwendet man <span style="color:red">Quantoren</span>.

|                  |            |                              |
| ---------------- | ---------- | ---------------------------- |
| All-Quantor      | $\forall$  | Für alle ...                 |
| Existenz-Quantor | $\exists$  | Es gibt (mindestens) ein ... |
|                  | $\exists!$ | Es gibt genau ein ...        |

##### Beispiele
- Die Gleichung $x^2=4$ besitzt eine Lösung in $\mathbb{R}$.
	- $\exists x \in \mathbb{R} : x^2=4$
- Die gleichung $x^2=4$ besitzt genau eine Lösung in $\mathbb{N}$.
	- 
