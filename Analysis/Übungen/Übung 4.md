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
>[!Note]
>die Variable (hier:$a_j$) sitzt untem im Bruch da durch wird das ergebnis kleiner und kleiner je größer die Variable wird $\Rightarrow$ Fallend

Daher muss $a{j}$ einen Grenzwert(GW) $a\geq \sqrt{5}$ besitzen.
Wir wenden den Grenzwert auf die Rekursionsgleichung an.

$$\lim_\limits{j \to \infty} a_{j+1}= \lim_\limits{j \to \infty} \frac{1}{2}(a_{j}+\frac{5}{a_{j}})$$
$$a=\frac{1}{2}(a+\frac{5}{a})\Rightarrow a^2=5$$

>[!Warning] Grenzwert
>Um den Grenzwert zu berechnen, nehme ich die Gleichung die hinter dem Limes steht. Setze die mit einer Variabel z.B. x (hier:a) gleich. Verschiebe alle Zahlen die an Variabeln gebunden sind rüber. Was übrig bleibt ist der Grenzwert. Vorsicht falsche ergebnisse möglich wenn kein Grenzwert existiert.


#### Aufgabe 2: Grenzwerte und -rechenregeln von Folgen
Gegeben seien die Folgen $b_n = \frac{-2n}{n+1}$ und $d_n= \frac{2n+(-1)^n*n+1}{n}$. Geben Sie die Grenzwerte der folgenden Folgen an.

###### a)
>[!secret]- $b_n+d_{2n-1}$
>
>Ersetze alle n in $d_n$ mit den $2_{2n-1}$ Binde mit Klammern
>$d_{2n-1}= \frac{2*(2n-1)+(-1)^{2n-1}*(2n-1)+1}{2n-1}$
>
>vereinfache die gleichung:
>Löse die Klammern auf.
>>[!Note] -1 hoch ungerade zahl ist -1. 2*x-1 ist immer ungerade
>$d_{2n-1}= \frac{4n-2+(-1)*(2n-1)+1}{2n-1}$
>noch mal klammern auflösen
>$d_{2n-1}= \frac{4n-2+(-2n)+1+1}{2n-1}$
>sortiere
>$d_{2n-1}= \frac{4n+(-2n)-2+1+1}{2n-1}$
>verrrechne
>$d_{2n-1}= \frac{2n}{2n-1}$
>
>Trage alles zusammen
>$b_n+d_{2n-1}= \frac{-2n}{n+1}+\frac{2n}{2n-1}$
>Nun für den Grenzwert den Limes schreiben
>$\lim_\limits{n \to \infty}(b_n+d_{2n-1})\frac{-2n}{n+1}+\frac{2n}{2n-1}$
>Rechnung mit n Gleichsetzen
>$\lim_\limits{n \to \infty}(b_n+d_{2n-1})\frac{-2n}{n+1}+\frac{2n}{2n-1}$
>Du darfst die Terme durch n nehmen um die Variabeln raus zu kürzen. !Vorsicht funktioniert so nur beim grenzwert wo $\frac{1}{n}=0$ ist.
>$\lim_\limits{n \to \infty}(b_n+d_{2n-1})\frac{-2}{1+\frac1n}+\frac{2}{2-\frac1n}$
>$n=\frac{-2}{1+0}+\frac{2}{2-0}$
>$n=-2+1$
>$n=-1$
>Der Grenzwert ist -1.

>[!secret]- $b_n*d_{2n-1}$
>Setzt 2n in $d_n$ ein
>$d_{2n}= \frac{2(2n)+(-1)^{(2n)}*(2n)+1}{(2n)}$
>Ausklammern
>$d_{2n}=\frac{4n+2n+1}{2n}$
>Verrechnen
>$d_{2n}=\frac{6n+1}{2n}$
>Setzte beides Zusammen
>$b_n*d_{2n}= \frac{-2n}{n+1}*\frac{6n+1}{2n}$
>In den Limes setzen
>$\lim_\limits{n \to \infty}(b_n*d_{2n}) \frac{-2n}{n+1}*\frac{6n+1}{2n}$
>n rauskürzen
>$\lim_\limits{n \to \infty}(b_n*d_{2n}) \frac{-2}{1+\frac1n}*\frac{6+\frac1n}{2}$
>x/n mit 0 ersetzen
>$= \frac{-2}{1}*\frac{6}{2}$
>Brüche lösen
>$= -2*3$
>Ergebnis:
>$= -6$

>[!secret]- $\frac{d_{2n}}{b_n}$
>Setzt 2n in $d_n$ ein
>$d_{2n}= \frac{2(2n)+(-1)^{(2n)}*(2n)+1}{(2n)}$
>Ausklammern
>$d_{2n}=\frac{4n+2n+1}{2n}$
>Verrechnen
>$d_{2n}=\frac{6n+1}{2n}$
>Setzte beides Zusammen
>$\frac{d_{2n}}{b_n}= \frac{\frac{6n+1}{2n}}{\frac{-2n}{n+1}}$
>Mit kehrwert Multiplizieren um doppel bruch zu entfernen ($\frac{\frac ab}{\frac cd} = \frac ab*\frac dc$)
>$\frac{d_{2n}}{b_n}= \frac{6n+1}{2n}*\frac{n+1}{-2n}$
  Limes einsetzen
>$\lim_\limits{n \to \infty}(\frac{d_{2n}}{b_n})  \frac{6n+1}{2n}*\frac{n+1}{-2n}$
>Durch n teilen
>$\lim_\limits{n \to \infty}(\frac{d_{2n}}{b_n})  \frac{6+\frac1n}{2}*\frac{1+\frac1n}{-2}$
>Ersetze $\frac1n$ mit 0
>$= \frac{6}{2}*\frac{1}{-2}$
>Verrechnen
>$ = -1.5$
	  	
###### b)

>[!secret]- $\frac{2n^2-3}{n^2+n+1}$
>Nur die Zahlen mit der höchsten Potenz zählen hier
>$\lim_\limits{n \to \infty}\frac{2n^2}{n^2}$
>Teile durch $n^2$
>$=\frac{2}{1}$
>Verrechnen
>=2$

>[!secret]- $\frac{-5n+1}{4n^2-7}$
>Nur die höchste Potenz ist wichtig
>$\lim_\limits{n \to \infty}\frac{-5n}{4n^2}$
>Da die Potenz unten höher ist als oben läuft es gegen 0
>$=0$

###### c)
>[!secret]- $\sqrt[n]{5}*(\frac n{n+1})$
>Jede Positive Zahl gegen nte Wurzel $\rightarrow$ 1
>$\lim_\limits{n \to \infty} 1*(\frac n{n+1})$
>Nun kann man den rest durch n Teilen. (Darf man wegen Grenzwert Produktregeln)
>$\lim_\limits{n \to \infty} 1*(\frac 1{1+\frac1n})$
>Nun die gegen null laufenden $\frac1n$ austauschen
>$= 1*(\frac 1{1+0})$
>Verrechnen
>$= 1$

>[!Warning]
>$$e=(1+\frac1n)^n$$ Special Term, Irrationale Number, 2,718281828... ohne Pattern weiter

>[!secret]- $(\frac13)^n+(1+\frac1n)^n$
>Setzen wir zuerst e ein
>$\lim_\limits{n \to \infty} (\frac13)^n+e$
>Da der $(\frac13)^n$ immer kleiner wird je größer n wird geht der teil gegen 0 für den Grenzwert
>$= 0+e$
>Somit ist der Grenzwert hier e
>$= e$



#### 3.Aufgabe: Häufungspunkte 1
Untersuchen Sie die folgenden Folgen $(a_n)_n\in\mathbb{N}_0$ auf die Existenz von Häufungspunkten und geben Sie ggf. alle Häufungspunkte und die dazugehörigen Teilfolgen an.

###### a) $(-1)^n*\frac{3n^2+2n+1}{2-5n^2}$
Denn Grenzwert von dem "Ruhigenteil" lösen oder einem klaren teil (höchste Potenz)
$(-1)^n*\frac{3n^2}{5n^2}$
Durch $n^2$ Teilen
$(-1)^n*\frac{3}{5}$
Dann  beachten wir den Vorderenteil $(-1)^n$ switched das Vorzeichen hin und her, demnach sind 
die Häufungspunkte {$\frac35$, $-{\frac35}$}.

###### b) $\frac{1}{2\sqrt{n}(\sqrt{n+1}-\sqrt{n})}$
