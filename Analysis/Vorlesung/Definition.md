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
>[!definition]+ Definition 11: Aussageformen
>___
>Sprachliche Konstrukte mit Variablen, die nach Ersetzung der Variablen durch Objekte zu logischen Aussagen werden, heißen <span style="color:red">Aussageformen</span>.
>
>Aussageformen bezeichnet man synonym auch als <span style="color:red">Prädikate</span>.
>- - -
>
>Prädikate mit einer Variable nennt man <span style="color:red">einstellige Prädikate</span>, Prädikate mit $n$ Variabeln nennt man <span style="color:red">n-stellige Prädikate</span>(n=Ordnung, Stelligkeit). 

^d76148
>[!definition] Definition 1: Natürliche Zahlen ([[02_Vorlesung.pdf#page=4|Seite 6]])
>___
>Es sei $\mathbb{N}$ eine Menge mit den folgenden Eigenschaften:
>1. 1 $\in$ $\mathbb{N}$
>2. Für jedes $n \in \mathbb{N}$ existiert ein von $n$ verschiedenes $Nf(n)\in \mathbb{N}$, das wir als <span class="redHigh">Nachfolger </span>von n bezeichnen.
>3. Für alle $n,\ m \in \mathbb{N}$ mit $n \not= m$ gelte $Nf(n) \not= Nf(m)$.
>4. Für alle $n \in \mathbb{N}$ gelte $Nf(n) \not = 1$
>5. Für jede Teilmenge $A\subset \mathbb{N}$ gilt: Falls $1\in A$ und falls zudem für alle $n \in A$ gilt $Nf(n) \in A$, dann ist $A = \mathbb{N}$.
>
>Die auf diese Weise definierte Menge ist die Menge der natürlichen Zahlen $\mathbb{N} = {1,2,3,...}$
>
>----
>1. 1 ist in den Natürlichen Zahlen
>2. Für jede Zahl in den Natürlichen zahlen existiert eine andere Zahl die wir als Nachfolger bezeichnen
>3. Wenn m ungleich n ist ist auch eine Funktion einmal mit n eingesetzt und einmal mit n eingestetzt ungleich
>4. Der Nachfolger einer Zahl kann nicht 1 sein
>5. Für eine Teilmenge A der Natürlichen Zahlen die 1 beinhaltet wo auch jeder nachfolger einer zahl in A mit drin ist, ist A gleich der Natürlichen Zahlen

^bec9bb
>[!definition] Definition 2: Vollständige Induktion ([[02_Vorlesung.pdf#page=6|Seite 6]])
>___
>Einen Induktionsbeweis strukturiert man in der Regel in folgender Weise:
>
>1. Induktionsanfang: $A_1$ ist wahr
>
>2. Induktionsannahme: $A_n$ gelte für $n \in \mathbb{N}$
>   
>3. Induktionsschritt (von $n$ nach $n+1$):
>Ist für beliebiges $n\in\mathbb{N}$ die Aussage $A_n$ wahr, so ist auch $A_{n+1}$ wahr   
>
>---
>Nehme an das $A_1$ wahr ist durch den 5. Peanosche Axiom würde dadurch auch die Aussage $A_{n+1}$ wenn jedes $n$ in $\mathbb{N}$ ist.

^0a1cda

>[!definition] Definition 3: (Abelsche) Gruppen [[02_Vorlesung.pdf#page=10|Seite 10]]
>___
>Die Menge $\mathbb{Z}$ der ganzen Zahlen bildet bzgl. der Addition + eine sog. kommutative (oder: Abelsche) Gruppe, denn es gilt für alle $a,b,c \in \mathbb{Z}$:
>
>1. Abgeschlossenheit: $a+b\in \mathbb{Z}$
>2. Assoiativität: $(a+b)+c = a+(b+c)$
>3. Existenz eines neutralen Elements: $a+0=0$
>4. Existenz eines inversen Elements: $a+(-a) = 0
>5. Kommutativität: a+b= b+a
>
>Wir sagen kurz: ($\mathbb{Z},+) ist eine Abelsche Gruppe.

^d27f63



