#### Aufgabe 1
Es sei die Menge 
$$Q \ \stackrel{def}{=} \{ x \ : \ Mx \ haelt \ auf \ Eingabe \ x \ und \ x \ \leq \ 2^{1000}\}$$ gegeben. Ist $Q$ entscheidbar? Begründen Sie Ihre Antwort!


$$Q \subseteq \{ 0, 1, 2, 3, .... 2^{1000}(,x)\}$$

$$Q(x) = \begin{cases}1, &Mx \ haelt \ auf \ Eingabe \ x \ und \ x \leq 2^{1000} \\0,&sonst\end{cases} $$

Ja, $Q$ ist eine endliche Menge welche anhält sobald entweder $Mx$ = Eingabe $x$ ist oder x $\leq 2^{1000}$. Daher ist es ein endliche Menge, welche eine charakteristische Funktion hat. Durch die Beschränkung der Menge von $\leq 2^{1000}$  wird das Halteproblem "ausgehebelt" und die Menge ist entscheidbar.

$\rightarrow$ Wir werden vermutlich nicht in endlicher Zeit das Q und ihre Funktion nicht bestimmen, es seiden jedes x und M(x) wird angesehen und anstelle von ausrechnen wird es versucht nach zu vollziehen.
$\rightarrow$ Kennen die Lösung und gibt eine Lösung nicht das  selbe!
nicht Q = {x : x > 2^1000} u {x : M(x) hält nicht auf x und x $\leq$ 2^1000}



#### Aufgabe 2
Im Moodle finden Sie bei Übungsblatt 1 noch das Programm für die TM add1.tm. Wir nennen dies TM für diese Aufgabe ADD1. 
##### (a) Geben Sie tADD1(18) an! Begründen Sie Ihre Antwort! 

```
start x       // Definition des Startzustands x
end e         // Definition des Endzustands e

x 0 -> x 0 R  // Solange im Zustand x, laufe ans rechte Eingabeende
x 1 -> x 1 R
x _ -> y _ L  // Am rechten Ende angekommen, gehe in Zustand y über
        
y 0 -> z 1 L  // y steht für: Übertrag 1 aufaddieren und nach links laufen
y 1 -> y 0 L  
y _ -> e 1 N  // wird das linke Wortende mit Übertrag erreicht, 
              // so wird der Übertrag 1 ans linke Wortende geschrieben
        
z 0 -> z 0 L  // im Zustand z ist kein Übertrag mehr vorhanden und es
z 1 -> z 1 L  // wird nur noch ans linke Wortende gelaufen
z _ -> e _ R  // linkes Wortende erreicht: Kopf zurück auf Ausgabestart setzen
```

$18_{10}$ = $10010_2$ 
$|w| = 5;\ w= 10010$

$$t_M(10010) \leq t(|5|)$$
$$ 2 \ * \  n \ + \ 1 \ + \ 1 $$
$$= 2 * 5 +1 \ (1. Zeiger zuruecksetzten) +1 \ (2. Zeiger zuruecksetzten) $$
$$= 12 $$
Im schlimmsten Fall geht man zweimal über die zahlen drüber und dann einen Schritt mehr. Am ende wird zeiger wieder zurück gesetzt 
##### (b) Geben Sie eine Funktion $t :\mathbb{N} → \mathbb{N}$  an, so dass ADD1 in Zeit t läuft!
$$t(n)\ = \ 2 (n + 1)$$

#### Aufgabe 3
Geben Sie eine **möglichst kleine Funktion** $l :\mathbb{N} → \mathbb{N}$ an, so dass für alle $x ∈ \mathbb{N} \ gilt: l(x) ≥ |x|$ (idealerweise soll sogar: $l(x) = |x|$ gelten). Die Funktion soll als berechenbare Formel angegeben werden 
(z.B. also so etwas wie $l(x) = x^3$ (dieses Beispiel löst die Aufgabe nicht richtig ;))). 

**Hinweis 1:** 
						$$|x| \stackrel{def}{=}\ Laenge \ der \ Binaerdarstellung\ (ohne \ fuehrende\ 0-en) \ von \ x.$$ 
	(aka umgedacht um zu zählen we oft durch 2 geteilt werden kann bis man bei 1 ist, ist $log_2$)

**Hinweis 2:** 
Sie dürfen die Gauß-Klammern benutzen. Für ein  ist dabei ⌊x⌋ die größte ganze Zahl y mit y ≤ x und ⌈x⌉ ist die kleinste ganze Zahl z mit z ≥ x. 
$$x ∈ R \Rightarrow ⌊x⌋ =\ größte \ ganze\ Zahl\ y \ mit \ y \leq x \ $$
$$x ∈ R \Rightarrow  ⌈x⌉  =\ kleinste \ ganze\ Zahl\ z \ mit \ z \geq x$$
⌊x⌋ = Abrundung
⌈x⌉  = Aufrundung

![[ITSysteme (Unedited).pdf#page=37|ITSysteme (Unedited), page 37]]


**Hinweis 3:** 
Möglichst kleine Funktion heißt: Möglichst kleine Funktionswerte für alle Eingaben.

$$|x| = ⌊log_2 \ (x)⌋ \ + \ 1  $$
$$(x ≥ 1)$$
$$l(x)=⌊log_2​(x)⌋+1$$
>[!Note]- log() erklärt
Man soll eine funtion angeben, die die länge der binärdarstellung der eingabe ausgibt
Das ist ja der exponent der größten zweierpotent, die in x reinpasst +1 (weil man ja mit 2^0 anfängt)
log_2(x) gibt einem exakt den exponenten, mit dem man 2 potenzieren muss, um x auszukriegen
Wenn x aber keine zweierpotenz ist, wird der wert ein bisschen größer, deswegen flooren wir das, weil uns ja nur sie zweierpotenz interessiert. Bis zur nächst größeren hat es ja keinen einfluss auf die länge, ob die zahl ein bisschen größer is oder nich

Abgerundet gibt das größte was in die zweier Potenz passt.

Für x $\in$ $[ 2^{k-1}, 2^k-1 ]$
gilt: l(x) = k

=> (log_2(x)) + 1 $\leq$ l(x) $\leq$ (log_2 (x + 1))




#### Aufgabe 4
Es sei die Funktion $f \ : \ \mathbb{N} → \mathbb{N} \ fuer \ alle \ x ∈ \mathbb{N}$ wie folgt definiert:
$$f (x) \stackrel{def}{=} 2^x − 1$$
##### (a) Skizzieren Sie eine Turingmaschine M , die f berechnet! Es ist nicht nötig, M auszuprogrammieren! Vielmehr sollen Sie die Arbeitsweise der Maschine in Worten beschreiben (und aufschreiben!), so dass einem Leser das Funktionsprinzip der Maschine klar wird. 

$2^x \rightarrow$ Binärschreibweise;   
-1 $\rightarrow$ macht es immer ungerade, verhindert Overflow 


$\Rightarrow$ er druckt nur Einsen bzw. er druckt den angegeben wert für x als die Anzahl der Einsen am Ende.

x = 4; $2^4 -1 = 16 - 1 = 15_{10} \rightarrow 15:2 = 1111_{2}$
x = 5; $2^5 -1 = 32 - 1= 31_{10} \rightarrow 31:2 = 11111_2$

>[!Note]- Idee
>hat 2 band maschine 1 eingabe in binäre (0100) 
>dann wenn nicht alles null 
>füge im 2.band eine 1 ein
>und - rechne im ersten band binär eine 1
>repeat bis 1. band leer
>
>0100
>1
>0011
>11
>0010
>111
>0001
>1111 
>---------
>Binär substrahier
>gehe von rechts nach links bis zur ersten 1änder die auf 0
>gehe nach links und ändere 0 auf 1
>1000
>0111 = 7 = $2^3-1$


##### (b) Geben Sie eine möglichst kleine, totale Funktion $s :\mathbb{N} → \mathbb{N}$  an, so dass gilt: M berechnet f in Raum s. 

s(n) = n+1 + 2^n +1 = 2^n + n +2 


##### (c) Geben Sie eine möglichst kleine, totale Funktion $t :\mathbb{N} → \mathbb{N}$  an, so dass gilt: M berechnet f in Zeit t. Hinweis: Beachten Sie bei Ihrer Lösung unbedingt die Definitionen 18 und 19, sowie 6 aus der VL. Insbesondere denken Sie bitte daran, dass Ein- und Ausgabe der TM in Binärdarstellung erfolgen müssen!

t(n) = n + 1 + (2n+1) * 2^n +  2 ^n (2^n +1) * 2 
$\leq$ 2^n +2^n * 2^n + 2^n (2^n + 2^n ) * 2
$\leq$ c * 2^{2^n} für ein c $\in$ $\mathbb{N}$ 
$\in$ O(2^{2^n})