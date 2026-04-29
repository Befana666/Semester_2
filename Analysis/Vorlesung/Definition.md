>[!definition]+ Definition 1: Aussagen
>___
>Eine Aussage ist ein <span style="color:red">Satz</span>, der entweder <span style="color:red">wahr</span> oder <span style="color:red">falsch</span>, niemals aber beide zugleich ist.
>
>Wahren Aussagen ordnen wir den Wahrheitswert *w* zu, falschen Aussagen den Wahrheitswert *f*.

^2f0e99

>[!definition]+ Definition 2: Wahrheitstafel OR (Disjunktion)
>___
>
>| A | B | A$\lor$B |
>| --- | --- | --- |
>|f|f|f|
>|f|w|w|
>|w|f|w|
>|w|w|w|

^4d7e66

>[!definition]+ Definition 3: Wahrheitstafel AND (Konjunktion)
>___
>
>A|B|A$\land B$
>--|--|--
>f|f|f
>f|w|f
>w|f|f
>w|w|w

^129143

>[!definition]+ Definition 4: Wahrheitstafel NOT
>___
>
>A|$\lnot A$
>--|--
>f|w
>w|f

^21a45f

>[!definition]+ Definition 5: Wahrheitstafel IMPLIKATION
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

^fcda15

>[!definition]+ Definition 6: Wahrheitstafel ÄQUIVALENZ
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

^7b8f0e

>[!definition]+ Definition 7: Wahrheitstafel XOR
>___
>
>A|B|A $\oplus$ B
>--|--|--
>f|f|f
>f|w|w
>w|f|w
>w|w|f

^647e37

>[!definition]+ Definition 8: logische Äquivalent
>___
>
>Zwei beliebige logische Aussagen oder Ausdrücke heißen <span style="color:red"> gleich </span> oder <span style="color:red"> logisch äquvalent</span>, wenn für jede beliebige Wahrheitsfunktion $\phi$ die Wahrheitswerte gleich sind.
>$$A=B: \Leftrightarrow\phi(A) = \phi(B)$$
>für alle Wahrheitsfunktionen $\phi$.
>
>Wir können die Gleichheit mit einer Wahrheitstafel oder KNF/DNF nachweisen.

^f6456a
>[!definition]+ Lemma 1: Regeln von de Morgan
>___
>Seien A und B zwei Aussagen. Dann gilt:
>
>$$\begin{aligned}(\lnot A)\lor (\lnot B) = \lnot (A\land B) \\ (\lnot A)\land (\lnot B) = \lnot (A\lor B)\end{aligned}$$

^c7852c

>[!definition]+ Definition 9: Tautologie
>___
>Eine logische Aussage, die immer wahr ist.
>
>$A\lor \lnot A$

^131516


>[!definition]+ Definition 10: Kontradiktion
>___
>Eine logische Aussage, die immer falsch ist.
>
>$A\land \lnot A$

^8eab43
