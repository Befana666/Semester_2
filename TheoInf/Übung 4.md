>[!Warning]-
>Hinweise: Nicht jede Aufgabe, die schwer scheint, benötigt auch eine schwere Lösung! Sie müssen mit den Definitionen arbeiten, die in der Vorlesung vorgestellt wurden. Wenn Sie die nicht verstanden und im Kopf haben, können Sie die untigen Aufgaben auf keinen Fall lösen! Fragen Sie keine Chatbots! 

#### 1. Aufgabe
Es sei die folgende, einstellige Funktion f : $\mathbb{N}$ → $\mathbb{N}$ gegeben: 
$$f(x)\stackrel{\text{def}}{=}\begin{cases}1&,falls&M_{x}&auf&Eingabe&x&hält&an\\0&sonst\end{cases}$$
x= 5 läuft weiter und gibt 0 aus bis er irgendwann 5 erreicht dann stopt er
###### (a) Geben Sie Wf an! Begründen Sie Ihre Antwort! 

>[!Note] $W_f$
>Die Menge der möglichen Ausgaben von f heißt Wertemenge von f. Wir kürzen diese mit $W_f$ ab.

$W_f$ = {0,1}
###### (b) Geben Sie Df an! Begründen Sie Ihre Antwort!
>[!Note] $D_f$
>Die Menge der Eingaben x, auf denen f definiert ist, für die also die Ausgabe f(x) existiert, heißt Definitionsmenge von f. Wir kürzen diese mit $D_f$ ab.

$D_f = \mathbb{N}$

#### 2. Aufgabe
Zeigen Sie: Ist A der Wertebereich einer totalen, berechenbaren, monoton wachsenden einstelligen Funktion, so ist A entscheidbar.

>[!Note] Total
> - f heißt total, falls klar ist, dass $E_f \stackrel{\text{def}}{=}D_f$. (S.69)

>[!Note] Entscheidbar
>- Eine Teilmenge von $\mathbb{N}$ heißt entscheidbar, wenn ihre charakteristische Funktion berechenbar ist. (S.154)
>- Wenn man sich über die Berechenbarkeit von Funktionen unterhält, genügt es, sich mit charakteristischen Funktionen zu beschäftigen. (S.121)
>- Für jede Menge A ⊆ $\mathbb{N}$ gilt: A ist genau dann entscheidbar, wenn $\overline A$ 
>entscheidbar ist. (S. 126)
>
>Entscheidbar und aufzählbar sind "gegensätze"
>aufzählung ist semi entscheidbar
>der Reihenach listen


#### 3. Aufgabe
Eine Menge A ⊆ $\mathbb{N}$ heißt aufzählbar, falls A = ∅ gilt oder eine totale, berechenbare Funktion f : $\mathbb{N}$ → $\mathbb{N}$ existiert, so dass A = {f(0), f(1), f(2), . . . }. 
##### (a) Man zeige: Das spezielle Halteproblem K ist aufzählbar. 

>[!Note] Halteproblem K
>Die Menge $K \stackrel{\text{def}}{=}$ {i : $M_i$ hält auf Eingabe i} heißt spezielles Halteproblem.

Wenn es einen deterministischen Algo für k gibt ist k aufzählbar

##### (b) Man zeige: Ist A ⊆ $\mathbb{N}$ eine unendlich große, aufzählbare Menge, so gibt es ein ein B ⊆ A, das unendlich und entscheidbar ist.

B ist unendlich und entscheidbar da wir sagen können ob ein element von A in B ist oder nicht in B ist.

#### 4. Aufgabe
Wir gehen von einer Gödelisierung M0, M1, M2, . . . aller Turingmaschinen aus und ordnen M$_i$ jeweils f$_i$  zu, so dass f$_i$  die einstellige Funktion ist, die von M$_i$  berechnet wird. Damit erhalten wir eine Aufzählung f0, f1, f2, . . . von Funktionen. 

Zeigen Sie, dass es zweistellige, totale und berechenbare Funktionen r, s gibt, so dass gilt:

###### a) $f_{r(i,j)}=f_i\circ f_j$

###### b) $f_{s(i,j)} = f_i + f_j$

Dabei sei
- $(f_i\circ f_j)(x)\stackrel{\text{def}}{=} f_i(f_j(x))$
- $(f_i+f_j)(x)\stackrel{\text{def}}{=}f_i(x)+f_j(x)$

für alle x$\in\mathbb{N}$

