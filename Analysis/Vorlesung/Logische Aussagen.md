#### Ziele:
- Aussagen lesen und aufstellen
- eigenständig mit Wahrheitstafeln arbeiten
- Quantoren und Prädikate arbeiten

##### Beispiele Aussagen:
- Der Mars ist blau
- 36 ist eine Primzahl und 4 teilt 36.

#### Why:
- mathematische Sachverhalten formulieren
- Sprachliche Ungenauigkeiten beseitigen
- Wahrheitsgehalt untersuchen
- Mathematische Beweise lassen sich klar und präzise führen

>[!definition]- Definition 1: Aussagen
>___
>Eine Aussage ist ein <span style="color:red">Satz</span>, der entweder <span style="color:red">wahr</span> oder <span style="color:red">falsch</span>, niemals aber beide zugleich ist.
>
>Wahren Aussagen ordnen wir den Wahrheitswert *w* zu, falschen Aussagen den Wahrheitswert *f*.

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

#### Wahrheitstafeln

>[!definition]- Definition 2: Wahrheitstafel ODER
>___
>
>| A | B | A$\lor$B |
>| --- | --- | --- |
>|f|f|f|
>|f|w|w|
>|w|f|w|
>|w|w|w|

>[!definition]- Definition 3: Wahrheitstafel AND
>___
>
>A|B|A$\land B$
>--|--|--
>f|f|f
>f|w|f
>w|f|f
>w|w|w

>[!definition]- Definition 4: Wahrheitstafel NOT
>___
>
>A|$\lnot A$
>--|--
>f|w
>w|f

>[!definition]- Definition 5: Wahrheitstafel IMPLIKATION
>___
>
>A|B|A$\Rightarrow B$
>--|--|--
>f|f|w
>f|w|w
>w|f|f
>w|w|w
>
>A$\Rightarrow$B: Wenn A gilt, dann gilt auch B.
>
>Wenn A falsch ist, ist die Aussage Irrelevant von B wahr.
>Wenn A wahr ist, entscheiden B ob die Aussage wahr oder falsch ist.
>
>Ursache-Wirkung Beziehung
>Zeitliche Beziehung
>Räumliche Beziehung...

>[!definition]- Definition 6: Wahrheitstafel ÄQUIVALENZ
>___
>
>A|B|
>--|--|--
>f|f|
>f|w|
>w|f|
>w|w|
>
>Wenn A = B ist, ist die Aussage wahr.

>[!definition]- Definition 7: Wahrheitstafel XOR
>___
>
>A|B|A $\oplus$ B
>--|--|--
>f|f|f
>f|w|w
>w|f|w
>w|w|f

>[!definition]- Definition 8: logische Äquivalent
>___
>
>Zwei beliebige logische Aussagen oder Ausdrücke heißen <span style="color:red"> gleich </span> oder <span style="color:red"> logisch äquvalent</span>, wenn für jede beliebige Wahrheitsfunktion $\phi$ die Wahrheitswerte gleich sind.
>$$A=B: \Leftrightarrow\phi(A) = \phi(B)$$
>für alle Wahrheitsfunktionen $\phi$.
>
>Wir können die Gleichheit mit einer Wahrheitstafel oder KNF/DNF nachweisen.

#### Übung 1: 

$A \Rightarrow B = \lnot A\lor B$

| A   | B   | $\lnot A$ | $\lnot A \lor B$ | $A \Rightarrow B |
| --- | --- | --------- | ---------------- | ---------------- |
| 0   | 0   | 1         | 1                | 1                |
| 0   | 1   | 1         | 1                | 1                |
| 1   | 0   | 0         | 0                | 0                |
| 1   | 1   | 0         | 1                | 1                |
