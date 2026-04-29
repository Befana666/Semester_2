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

3.Geben Sie eine möglichst kleine Funktion ℓ : N → N an, so dass für alle x ∈ N gilt: ℓ(x) ≥ |x| (idealerweise soll sogar: ℓ(x) = |x| gelten). Die Funktion soll als berechenbare Formel angegeben werden (z.B. also so etwas wie ℓ(x) = x 3 (dieses Beispiel löst die Aufgabe nicht richtig ;))). 
Hinweis 1: |x| def = Länge der Binärdarstellung (ohne führende 0-en) von x. 
Hinweis 2: Sie dürfen die Gauß-Klammern benutzen. Für ein x ∈ R ist dabei ⌊x⌋ die größte ganze Zahl y mit y ≤ x und ⌈x⌉ ist die kleinste ganze Zahl z mit z ≥ x. 
Hinweis 3: Möglichst kleine Funktion heißt: Möglichst kleine Funktionswerte für alle Eingaben.

### Kurz gesagt (Intuition):

- Binärlänge zählt, wie oft man durch 2 teilen kann, bis man bei 1 ist
- Logarithmus zur Basis 2 misst genau das
- Abrunden + 1 gibt die exakte Bitlänge


4.Es sei die Funktion f : N → N für alle x ∈ N wie folgt definiert: f(x) def = 2^x − 1 
(a) Skizzieren Sie eine Turingmaschine M, die f berechnet! Es ist nicht nötig, M auszuprogrammieren! Vielmehr sollen Sie die Arbeitsweise der Maschine in Worten beschreiben (und aufschreiben!), so dass einem Leser das Funktionsprinzip der Maschine klar wird. 

>[!Note]- erste idee
>gehe nach rechts wenn du eine 1 triffts replace mit x (oder platzhalter) gehe bis keine 1 oder platzhalter schreibe anderen platzhalter y gehe back bis du x triffst und repeat bis keine 1 mehr vorhanden ist und replace alle platzhalter mit 1 lösche die erste 1.

>[!Note]- zweite idee
>hat 2 band maschine 1 eingabe in binäre (0100) 
>dann wenn nicht alles null 
>füge im 2.band eine 1 ein
>und - rechne im ersten band binär eine 1
>rins and repeat bis 1. band leer
>0100
>1
>0011
>11
>0010
>111
>0001
>1111 
>Binär substrahier
>gehe von rechts nach links bis zur ersten 1änder die auf 0
>gehe nach links und ändere 0 auf 1
>1000
>0111

0101 5
1 1010 26
31
011111
1010
4=15
1111




(b) Geben Sie eine möglichst kleine, totale Funktion s : N → N an, so dass gilt: M berechnet f in Raum s. 

(c) Geben Sie eine möglichst kleine, totale Funktion t : N → N an, so dass gilt: M berechnet f in Zeit t. 

Hinweis: Beachten Sie bei Ihrer Lösung unbedingt die Definitionen 18 und 19, sowie 6 aus der VL. Insbesondere denken Sie bitte daran, dass Ein- und Ausgabe der TM in Binärdarstellung erfolgen müssen!

Definition 18 Seien f, t : N → N Funktionen auf N und t total. Eine TM M berechnet f in Zeit t, falls f von M berechnet wird und für jedes x ∈ N gilt: tM(x) ≤ t(|x|)

Definition 19 Sei s : N → N eine totale Funktion. Eine TM M berechnet eine Funktion f : N → N in Raum s, falls f von M berechnet wird und für alle x ∈ N gilt: sM(x) ≤ s(|x|)

Definition 6 Eine Funktion g : N n → N mit n ≥ 0 heißt von einer TM M = (Σ, Z, f) berechnet, falls für beliebige x1, . . . , xn ∈ N gilt: ▶ Zu Beginn der Berechnung steht nur bin(x1) ∗ bin(x2) ∗ · · · ∗ bin(xn) auf dem Arbeitsband, der Kopf von M steht auf dem linkesten Symbol von bin(x1) und M befindet sich im Zustand s. ▶ Die Maschine hält im Zustand e, auf dem Arbeitsband steht nur bin(g(x1, . . . , xn)) und der Kopf von M steht auf dem linkesten Symbol von bin(g(x1, . . . , xn)) . Es sei TM def = {g : g kann von einer TM berechnet werden}.