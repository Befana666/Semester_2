#### Peano-Axiome

Sind die 5 folgenden Regeln die Natürliche Zahlen beschreiben. 

![[Definition#^bec9bb]]

---
#### Vollständige Induktion

Das 5. Peanosche Axiom ermöglicht Beweise für unendlich viele Aussagen nach dem Beweisprinzip der <span class="redHigh">vollständigen Induktion</span>.


Es seien $A_n, n\in \mathbb{N}$, undendlich viele Aussagen. Sofern gilt
	1. $A_1$
	2. $A_n \Rightarrow A_{n+1}$ für alle $n\in \mathbb{N}$
dann gelten alle Aussagen $A_n,\ n\in \mathbb{N}$

>Sofern A als 1 anfängt sind auch alle $A_n$ in den natürlichen Zahlen wenn +1 gerechnet wird.

![[Definition#^0a1cda]]

##### Beweis

Wir beweisen (ausführlich) mittels vollständiger Induktion die [[Extra#^ef58da|Gaußsche Formel]]:

Für alle $n\in\mathbb{N}$ gilt

$$A_n:\sum\limits_{k = 1}^{n} {k} = \frac{n*(n+1)}{2}$$
###### 1) Induktionsanfang (IA):

$$A_1:\sum\limits_{k = 1}^{1} {k} = \frac{1*(1+1)}{2}$$

$$ \begin{aligned}&LS: \sum\limits_{k = 1}^{1} {k} = 1\\

&RS:   \frac{1*(1+1)}{2}=1\\
\\
&LS \Leftrightarrow RS\end{aligned}$$
###### 2) Induktionsvoraussetzung (IV):

$$A_n:\sum\limits_{k = 1}^{n} {k} = \frac{n*(n+1)}{2}\ \ \ \ \ \text{gilt für } n\in \mathbb{N}$$
###### 3) Induktionsschritt (IS):
$n\rightarrow n+1$ auf n folged n+1

###### 4) Induktionsbehauptung (IB):

$$A_{n+1}:\sum\limits_{k = 1}^{n+1} {k} = \frac{n+1*(n+1+1)}{2} = \frac{n+1*(n+2)}{2}$$
$$\begin{aligned}A_{n+1}:\sum\limits_{k = 1}^{n+1} {k} &= (n+1)+\sum\limits_{k = 1}^{n} {k} \\ \\
&=(n+1)+\frac{n*(n+1)}{2} \\ \\
&=(n+1)*(1+\frac{n}{2}) \ \ \ \ \ \ \ \ \text{ab+ac=a(b+c)} \\ \\
&=(n+1)*(\frac {2}{2}+ \frac{n}{2})\\ \\ 
&=(n+1)*(\frac{n+2}{2})\ \ \ \ \ \ \ \ \text{ab+ac=a(b+c)}\\\\
&= \frac{(n+1)*(n+2)}{2}\end{aligned}$$

Demnach sind beide Seiten wieder gleich Summe von n + n+1 ist gleich der Gauschen formel mit n+1.

---

#### Die Ganzen Zahlen

![[Definition#^d27f63]]
___
##### Übung: 
Warum bilden die natürlichen Zahlen $\mathbb{N}$ keine Gruppe bzgl. der Addition?

$\mathbb{N}$ ist keine Gruppe denn es:
- fehlt das neutrale Element (0 ist nicht in $\mathbb{N}$ demnach egal was du addierst die Zahl ändert sich)
- es gibt auch keine inversen Elemente $\forall n\in \mathbb{N}$ (es gibt keine Minus zahlen demnach kannst du nie 0 erreichen mit nur der Addition)
___
##### Gruppentheorie allgemein

Gegeben sein eine Menge $M$ mit (zweistelliger) Verknüpfung

$$\begin{aligned}
	&\circ:M\times M \rightarrow M && \text{(Abgeschlossenheit)} \\
	&\forall a,b,c \in M: (a\circ b)\circ c = a\circ (b\circ c)&& \text{(Assoziativität)} \\
	&\exists e \in M:a\circ e = a && \text{(Existenz des neutralen Elements)} \\
	&\forall a\in M: \exists a^{-1}\in M: \ \ \ \ \ \ a\circ a^{1}=e &&\text{(Existenz des inversen Elements)}
	
\end{aligned}$$
Die Gruppe heißt abelsch (oder kommutativ), falls
$$a\circ b = b\circ a\ \ \ \ \ \forall a,b\in M$$
Mann kann zeigen:
Jedes links-neutrale Element ist rechts-neutral.
Jedes links
