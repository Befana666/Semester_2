>[!definition] Definition 1: Modifizierte Differenz ([[Folien.pdf#page=51|S.50]])
>___
>Für natürliche Zahlen $x,\ y$ sei $$x-y\stackrel{\text{def}}{=}md(x,\ y)\stackrel{\text{def}}{=}\begin{cases}x-y, &falls\ x\gt y\\ 0&sonst\end{cases}$$ 
>Bedeuted:
>- $x-y$ wird in der Funktion md($x$, $y$) berechnet. 
>- die Funktion md($x$, $y$) rechnet und returns $x-y$ wenn $x\gt y$ ist.

^1e3839

>[!definition] Definition 2: RAM-Berechenbarkeit ([[Folien.pdf#page=58|S.57]])
>___
>Eine Funktion $f:\mathbb{N}^n\rightarrow\mathbb{N}$ mit $n\geq0$ heißt von einer RAM M berechnet, falls für beliebige $x1,\ x2,\ ....,\ x_n \in \mathbb{N}$ gilt:
>$$f(x1,\ x2,\ ....,\ x_n) = \begin{cases}\text{ letzter Inhalt von R0}, &\text{falls M beim Start mit} \\ & [BR]=0 \\ & [R_0] =\text{ x1,...} \\ & [R(n-1)]=x_n \\ & [Ri]=0 \text{ für }i\geq n \\ & \text{nach endlich vielen Schritten hält} \\ \text{nicht definiert }&sonst\end{cases}$$
>
>Eine Funktion $f:\mathbb{N}^n\rightarrow\mathbb{N}$ mit $n\geq0$ heißt RAM-berechenbar, wenn es eine RAM gibt, die $f$ berechnet.
>
>RAM$\stackrel{\text{def}}{=}\{f:f \text{ ist RAM-berechenbar} \}$.

^a72847

>[!definition] Definition 3: RAM definiert Funktion ([[Folien.pdf#page=67|S.66]])
>___
>Sei $M$ eine Random-Access-Machine. Dann sei $f_M:\mathbb{N}\rightarrow\mathbb{N}$ diejenige Funktion, für die gilt: 
>$$f_M(x)=\begin{cases}y, &\text{falls } M \text{ auf die Eingabe }x\text{ mit dem Ergebnis }y\text{ hält} \\ \text{nicht definiert} & \text{sonst}\end{cases}$$
>---
>hält mit dem Ergebis $y$ wenn es $x$ als input bekommt ansonsten ist das verhalten nicht definiert (Endlosloop)

^a94a52

^b63ff6
>[!definition] Definition 4 Partielle Funktion ([[Folien.pdf#page=70|S.69]])
>___
>Sei $f$ eine Funktion:
>- Die Menge der möglichen Eingaben für eine Funktion heißt <span class="redHigh">Eingabemenge</span> von $f$. Wir kürzen diese mit $E_f$ ab.
>
>- Die Menge der Eingaben $x$, auf denen $f$ definiert ist, für die also die Ausgabe $f(x)$ existiert, heißt <span class="redHigh">Definitionsmenge</span> von $f$. Wir kürzen diese mit <span class="redHigh">$D_f$</span> ab.
>
>- Die Menge der möglichen Ausgaben von $f$ heißt <span class="redHigh">Wertemenge</span> von $f$. Wir kürzen mit $W_f$ ab.
>
>- Wir nennen jede Funktion $f$ in der Informatik <span class="redHigh">partiell</span>, solange nicht klar ist, ob $E_f=D_f$ ist oder nicht.
>  
>- $f$ heißt <span class="redHigh">total</span>, falls klar ist, dass $E_f=D_f$

^de852c

>[!definition] Definition 5: Überführungsfunktion ([[Folien.pdf#page=82|S.81]])
>___
>Eine <span class="redHigh">Turing-Maschine</span> ist ein Dreitupel ($\sum , Z,f$) mit:
>
>- $\sum$ ist ein Alphabet (das <span class="redHigh">(Arbeits-)Alphabet)</span> mit $\square \in \sum$
>- $Z$ ist eine endliche Menge (die <span class="redHigh">Zustandsmenge</span>) mit $\{s,e\}  \subseteq Z$.
>- $f:(Z/\{e\})\times \sum \rightarrow Z\times \sum\times \{L,N,R\}$ ist eine totale Funktion (die <span class="redHigh">Überführungsfunktion</span>).
>  
>  ---
> Die Funktion f ordnet jedem Paar aus einem Zustand (außer dem Endzustand e) und einem Bandsymbol genau ein neues Tupel zu, bestehend aus einem neuen Zustand, einem zu schreibenden Bandsymbol sowie einer Bewegungsrichtung des Lesekopfes — links (L), keine Bewegung (N) oder rechts (R).
> Aka. Es ist genau die Zeilen aus denen eine Turingmaschine aufgebaut ist.

^6c8843
>[!definition] Definition 6: von Turingmaschine berechnet
>___
>