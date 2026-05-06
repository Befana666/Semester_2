#### Aufgabe 1: Alternierende Reihen (I)
Die folgende Aufgabe dient der Wiederholung der Inhalte aus Folien [[04_Vorlesung.pdf#page=33|4/33]], [[04_Vorlesung.pdf#page=34|4/34]] und [[04_Vorlesung.pdf#page=35|4/35]]. 
##### a) Zeigen Sie, dass die unendliche Reihe $\sum\limits_{j = 1}^{\infty} {\frac{(-1)^j}{j}}$ konvergiert und geben Sie den Grenzwert an! Berechen Sie den Grenzwert mit einem Fehler von höchstens 0,1. [[04_Vorlesung.pdf#page=39|Siehe]]

Da die Zahl unterm bruch strich größer wird und sich die oberm bruchstrich nur das vorzeichen ändert konvergiert die Reihe zu null ohne null je zu treffen
1,-1,0.5,-0.5,0.25.-0.25,0.125,-0.125,0.0625,-0.0625
s-sn=s-$\sum\limits_{j = 1}^{\infty} {\frac{(-1)^j}{j}}$|$\leq a_n +1$
##### b) Wie viele Glieder der unendlichen Reihe aus a) mussen Sie summieren, um eine Genauigkeit von $10^{-3}$ zu erhalten? 
##### c) Geben Sie die alternierende Reihe der Kehrwerte der ungeraden natürlichen Zahlen an und begründen Sie die Konvergenz dieser unendlichen Reihe. 
#### Aufgabe 2: Alternierende Reihen (II)
Untersuchen Sie, ob die folgende alternierende Reihe konvergiert und bestimmen Sie ggf. ihren Grenzwert.
$$\sum\limits_{j = 0}^{\infty} {\frac{(-1)^j}{3^j}}$$
#### Aufgabe 3: injektiv, surjektiv und bijektiv 
##### a) Zeigen Sie: dass die Funktion $f(x)$ : $\mathbb{R}\rightarrow \mathbb{R}$, $f(x)=-x^2+10$ weder injektiv noch surjektiv ist. 
##### b) Zeigen Sie, dass jede lineare Funktion $g(x)$ :$\mathbb{R}\rightarrow \mathbb{R}$ , $g(x) \mapsto ax+b$ für $a,b \in \mathbb{R}$ mit $a\not =0$ bijektiv ist, indem Sie die nachfolgenden Schritte vollziehen: 
1) Zeigen Sie Injektivität allgemein, indem Sie die Aussage: 
	"Für $x1, x2 \in \mathbb{R}$ mit der Eigenschaft $g(x1) = g(x2)$ folgt $x1 = x2$" 
2) Zeigen Sie Surjektivität allgemein, indem Sie die Aussage:
	"Für alle $y0 \in \mathbb{R}$ gibt es ein $x0 \in \mathbb{R}$, sodass $g(x0) = y0$ gilt" 
3) Überlegen Sie, wo Sie in ihrer Beweisführung verwenden, dass $a \not = 0$ gelten muss. 
4) Folgern Sie die Bijektivität. 
#### Aufgabe 4: Definitionsbereich, Bildbereich und Beschränktheit 
Gegeben seien die beiden Funktionen $f$ : $\mathbb{R}_{\geq0},\ \ x\mapsto e^{\frac 12 x^2}$ und $g$ : $\mathbb{R} \rightarrow \mathbb{R}$, $x \mapsto \frac{x-\mu}{\sigma}$
##### a) Bestimmen Sie die Umkehrfunktionen $f^{-1}$ und $g^{-1}$. Welche Bedingungen ergeben sich für den Definitionsbereich der Umkehrfunktionen? 
##### b) Bestimmen Sie den Definitionsbereich $D_{f\circ g}$ der Komposition $(f\circ g)(x)$. 
##### c) Bestimmen Sie den Bildbereich $\mathbb{D}_{f\circ g}$ der Komposition $(f\circ g)(x)$ so, dass die Komposition surjektiv ist. Hinweis: Ist die Komposition beschränkt? 
#### Aufgabe 5: Maximaler Definitionsbereich
Geben Sie den maximalen Definitionsbereich $D\subset \mathbb{R}$ der Funktion 
$$f :D \rightarrow \mathbb{R}$$
$$x\mapsto \frac{\sqrt{x^4-4}+\frac{x+2}{x^2-4x-21}}{|x|+\omega(x)}$$
an. Dabei ist $\omega:\ \mathbb{R}\rightarrow \mathbb{R}$
$$x\mapsto \begin{cases}\sqrt[3]{x}, &x\gt0\\ 0,&x=0\\ -\sqrt[3]{-x}, &x\lt0\end{cases}$$
