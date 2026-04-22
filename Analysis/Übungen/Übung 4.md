#### Aufgabe 1: Heron Verfahren 

Untersuchen Sie die Bedeutung und den Grenzwert der rekursiv definierten Folge (bj )j∈N durch:
$$b_1 = a,\space b_{j+1} = \frac{1}{2} ( b_j + \frac{a}{b_j} ) $$
für ein  a ∈ $\mathbb{R}_{>0}$, indem Sie die Schritte aus der Vorlesung logisch übertragen. Konvergiert die Folge und wenn ja, gegen welchen Grenzwert?

>[!Note]- Herons-Verfahren
>![[Pasted image 20260421190901.png]]
>https://studyflix.de/mathematik/heron-verfahren-8229

a=5
$b_1$=5
a=$b_1$
$$a_2=\frac{1}{2}(5+1)=3$$
$$a_3=\frac{1}{2}(3+\frac{5}{3})=2.\overline{33}$$
$$m$$

Ich will zeigen da $b_n$ gegen $\sqrt{5}$  konvergiert.
Man sieht leicht: $a_j\gt0$  $\forall j\in\mathbb{N}$ 
Es gilt sogar
	$a_j\geq\sqrt{5}$   $\forall j\in\mathbb{N}$ 

>[!Note]
>$a_{j}^2-5 = 0$


Es gilt: (Die minus 5 kommen von der zahl die wir als a/$b_1$ gewählt haben)
	$$a_j^2-5=\frac{1}{2}^2*(a_{j-1}+\frac{5}{a_{j-1}})^2-5$$
	Binomische Formel: $(a+b)^2$ = $a^2+2*a*b+b^2$ ![[Pasted image 20260421200906.png]]
$$a_j^2-5=\frac{1}{4}*(a_{j-1}^2+25+\frac{10}{a_{j-1}^2})-5$$
Nun hohlen wir die 5 in die Klammer in dem wir sie mal 4 nehmen ($20*\frac{1}{4}=5$)
$$a_j^2-5=\frac{1}{4}*(a_{j-1}^2+10-20+\frac{25}{a_{j-1}^2})$$
Umgekehrte binomische formeln
$$a_j^2-5=\frac{1}{4}*(a_{j-1}-\frac{5}{a_{j-1}})^2$$
								$\geq0$
$\Rightarrow a_{j}^2\geq0\Rightarrow a_{j}^\geq\sqrt{5}$

$a_{j}$ ist monoton fallend, denn
$a_{j}-a_{j-1} = a_{j}-\frac{1}{2}a_{j}-\frac{5}{2a_{j}}=\frac{1}{2_a{j}} (a_{j}^2-5)\geq0\Rightarrow a_{j}\geq a{j+1}$

Daher muss $a{j}$ einen Grenzwert(GW) $a\geq \sqrt{5}$ besitzen.
Wir wenden den Grenzwert auf die Rekursionsgleichung an.

$$\lim_\limits{j \to \infty} a_{j+1}= \lim_\limits{j \to \infty} \frac{1}{2}(a_{j}+\frac{2}{a_{j}})$$
$$a=\frac{1}{2}(a+\frac{5}{a})\Rightarrow a^2=5$$




#### Aufgabe 2: Grenzwerte und -rechenregeln von Folgen