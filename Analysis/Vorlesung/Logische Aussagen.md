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

^2c90da

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

| Name             | Symbol     | Beschreibung                 | Negierung                     | Negierung Beschreibung                |
| ---------------- | ---------- | ---------------------------- | ----------------------------- | ------------------------------------- |
| All-Quantor      | $\forall$  | Für alle ...                 | $\exists x\in G:\lnot A(x)$   | Es gibt mindestens 1 das es nicht ist |
| Existenz-Quantor | $\exists$  | Es gibt (mindestens) ein ... | $\forall x \in G: \lnot A(x)$ | Alle sind nicht in A                  |
|                  | $\exists!$ | Es gibt genau ein ...        |                               |                                       |
##### Negation 

1. Ersetze alle Existenz-Quantoren durch All-Quantoren!
2. Ersetze alle All-Quantoren durch Existenz-Quantoren!
3. Negiere alle Prädikate!

##### Beispiele
- Die Gleichung $x^2=4$ besitzt eine Lösung in $\mathbb{R}$.
	- $\exists x \in \mathbb{R} : x^2=4$
- Die Gleichung $x^2=4$ besitzt genau eine Lösung in $\mathbb{N}$.
	- $\exists! x\in \mathbb{N}: x^2=4$
note: wenn ich 2 beliebige zahlen aus n nehme so das beide ^2 gleich 4 sind sind beide zahlen gleich 
- Die Gleichung $x^2=4$ besitzt genau zwei Lösungen in $\mathbb{R}$.
	- $\exists! (x,4) \in \mathbb{R}*\mathbb{R}, x\lt:yx^2=y^2=4$
	- Genau zwei lösungen da das Tupel als 1 objekt gilt also das $\exists!$ erfüllt aber auch 2 Values hat.
- Alle Lösungen der Ungleichung $x^2 \gt 5.4$ in $\mathbb{N}$ sind größer als 2.
	- $\forall x \in \mathbb{N} : (x^2\gt 5.4) \Rightarrow (x\gt2)$
- Jeder Spieler der Nationalmannschaft hat einen Vereinstrainer.
	- V: alle Vereinstrainer 
	- N: alle Spieler der Nationalmannschaft 
	- P(x, y): x ist der Vereinstrainer von y
	- $\forall y \in N\ \ \ \exists x \in V: P(x, y)$
	- Alle Nationalspieler haben den selben Vereinstrainer.
- Alle Hunde sind schwarz.
	- Menge aller Hunde H
	- Prädikat S(x): "x ist schwarz"
	- $\forall x \in H:S(x)$
- Es gibt mindestens einen Hund, der nicht schwarz ist.
	- $\exists x \in H : \lnot S(x)$

#### Mengen

Besitzen alle Elemente einer Menge A in einem Universum G eine bestimme Eigenschaft E und besitzen alle Elemente, die nicht zu A gehören diese Eigenschaft nicht, dann können wir die Menge A mittels der Eigenschaft E charakterisieren.

$x\in G$: x ist ein Element von G
E(x): x mit der Eigenschaft E // logisches Prädikat

$A\{x\in G | E(x)\}$
Alle Elemente x der Gruppe G, haben die Eigenschaften E(x).

#### Mengenoperationen

| Name              | Symbol           | Beispiel                                     | Ausgeschrieben                                                                                                      |
| ----------------- | ---------------- | -------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| Vereinigungsmenge | $\cup$           | $A\cup B = \{x\in G \| x\in A\lor x \in B\}$ | Die Vereinigungsmenge von A und B ist: x Element der Menge G sind alle Teil der Menge A oder Teil der Menge B sind. |
| Schnittmenge      | $\cap$           | $A\cap B = \{x\in G\|x\in A\land x \in B\}$  | Die Schnittmenge von A und B ist: x Elemente der Menge G sind alle die sowohl Teil der Menge A und B sind.          |
| Komplement        | $\overline{A}^G$ | $\overline{A}^G=\{x\in G\|x \notin A\}$      | Die Menge der Elemente x in der Grundmenge G sind nicht Teil der Menge A.                                           |
| Differenzmenge    | $/$              | $A/B=\{x\in G\| x\in A\land x\notin B\}$     | Die Menge der Elemente x in der Grundmenge G, sind alle in der Teilmenge A aber nicht in der Teilmenge B.           |
##### Übung 5:
Zeigen Sie: Sind A und B zwei nichtleere Mengen aus der Grundmenge G, dann gilt:
$$A/B = \{x\in G| \lnot(x \in A \Rightarrow x \in B)\}$$
Alle Elemente x der Menge G, sind nicht, wenn x in der Teilmenge A dann ist x auch Teil der Teilmenge B. [[Logische Aussagen#^2c90da|hint]]
$$\begin{aligned}A/B &= \{x\in G| (x \in A)\land (x \notin B) \}\text{//Definition} \\ 
&=\{x\in G|(\lnot(x \notin A))\land (\lnot(x \in B)) \} \text{//doppel Negation} \\ &=\{x\in G|\lnot((x \notin A)\lor (x \in B)) \} \text{//de Morgan}\\ &=\{x\in G|\lnot((x \in A)\lor (x \in B)) \} \text{//Übung 1}
\end{aligned}$$