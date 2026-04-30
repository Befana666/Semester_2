>[!definition]- Definition 1: Modifizierte Differenz (S.50)
>___
>Für natürliche Zahlen $x,\ y$ sei $$x-y\stackrel{\text{def}}{=}md(x,\ y)\stackrel{\text{def}}{=}\begin{cases}x-y, &falls\ x\gt y\\ 0&sonst\end{cases}$$ 
>Bedeuted:
>- $x-y$ wird in der Funktion md($x$, $y$) berechnet. 
>- die Funktion md($x$, $y$) rechnet und returns $x-y$ wenn $x\gt y$ ist.

^1e3839

>[!definition]- Definition 2: RAM-Berechenbarkeit (S.57)
>___
>Eine Funktion $f:\mathbb{N}^n\rightarrow\mathbb{N}$ mit $n\geq0$ heißt von einer RAM M berechnet, falls für beliebige $x1,\ x2,\ ....,\ x_n \in \mathbb{N}$ gilt:
>$$f(x1,\ x2,\ ....,\ x_n) = \begin{cases}\text{ letzter Inhalt von R0}, &\text{falls M beim Start mit} \\ & [BR]=0 \\ & [R_0] =\text{ x1,...} \\ & [R(n-1)]=x_n \\ & [Ri]=0 \text{ für }i\geq n \\ & \text{nach endlich vielen Schritten hält} \\ \text{nicht definiert }&sonst\end{cases}$$
>
>Eine Funktion $f:\mathbb{N}^n\rightarrow\mathbb{N}$ mit $n\geq0$ heißt RAM-berechenbar, wenn es eine RAM gibt, die $f$ berechnet.
>
>RAM$\stackrel{\text{def}}{=}\{f:f \text{ ist RAM-berechenbar} \}$.

^a72847

>[!definition]+ Definition 3: RAM definiert Funktion
>___
>Sei $M$ eine Random-Access-Machine. Dann sei $f_M:\mathbb{N}\rightarrow\mathbb{N}$ diejenige Funktion, für die gilt: 
>$$f_M(x)=\begin{cases}y, &\text{falls } M \text{ auf die Eingabe }x\text{ mit dem Ergebnis }y\text{ hält} \\ \text{nicht definiert} & \text{sonst}\end{cases}$$

^b63ff6

