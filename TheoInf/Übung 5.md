1.Es sei die Menge Q def = {x : Mx hält auf Eingabe x und x ≤ 2 1000} gegeben. Ist Q entscheidbar? Begründen Sie Ihre Antwort!

Mx hält auf eingabe x ist das halte problem $\Rightarrow$ nicht entscheidbar.
Der hintere teil ist eine entscheidbare Schranke 
dadurch ist für diese eine Funktion das problem ist entscheidbar


2.Im Moodle finden Sie bei Übungsblatt 1 noch das Programm für die TM add1.tm. Wir nennen dies TM für diese Aufgabe ADD1. 
(a) Geben Sie tADD1(18) an! Begründen Sie Ihre Antwort! 
O(1) schritte sind immer eingabe
oder
11 Takte


(b) Geben Sie eine Funktion t : N → N an, so dass ADD1 in Zeit t läuft!
>[!Note]+ Laufzeitfunktion
>Für eine TM M definieren wir die Funktion tM : $\mathbb{N}\rightarrow\mathbb{N}$ wie folgt: tM(x) def 
Anzahl der Takte, bis M hält, falls M auf x hält tM(x) def = ∞, falls M auf x nicht hält.

t(n)=2n+1

3.Geben Sie eine möglichst kleine Funktion ℓ : N → N an, so dass für alle x ∈ N gilt: ℓ(x) ≥ |x| (idealerweise soll sogar: ℓ(x) = |x| gelten). Die Funktion soll als berechenbare Formel angegeben werden (z.B. also so etwas wie ℓ(x) = x 3 (dieses Beispiel löst die Aufgabe nicht richtig ;))). Hinweis 1: |x| def = Länge der Binärdarstellung (ohne führende 0-en) von x. Hinweis 2: Sie dürfen die Gauß-Klammern benutzen. Für ein x ∈ R ist dabei ⌊x⌋ die größte ganze Zahl y mit y ≤ x und ⌈x⌉ ist die kleinste ganze Zahl z mit z ≥ x. Hinweis 3: Möglichst kleine Funktion heißt: Möglichst kleine Funktionswerte für alle Eingaben.

