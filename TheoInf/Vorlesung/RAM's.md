#### Was ist eine RAM
Random Access Machines = Registermaschinen

Register enthalten eine natürliche Zahl
Steuereinheit hat das Programm gespeichert

| Reale Rechner         | RAM                            |
| --------------------- | ------------------------------ |
| endliche Register     | unendliche Register            |
| begrenzte Anzahl Bits | Unbegrenzte anzahl von bits    |
|                       | auf jedem Register rechnen     |
|                       | Speicher und Programm getrennt |

- Eine RAM arbeitet *taktweise*.
- Programm = durchnummerierte endliche liste von Befehlen
- 1 Takt = 1 Befehl (steht im Befehlsregister $BR$)
- *Startet* immer bei 0
- *Stoppt* bei stop befehl oder kein Befehl
- Kann nur mit positiven ganzen Zahlen ($\mathbb{N}^+$)

#### RAM Programmieren

![[TheoInf/Definitionen#^1e3839]]

>[!Info]- RAM-Syntax
>$R_i$ = Direkte Adresse
>$RR_i$ = Indirekte Adresse $\Rightarrow$ Adressiert das Register das die selbe nummer hat wie in diesem Register gespeichert ist.
>
>Setze $R_i$ auf $R_j, k, RR_j,\ etc$
>
>\[$R_i$\] = Zahl, die im Register $R_i$ steht
>\[$BR$\] = Zahl, die im Befehlsregister $BR$ steht

| Befehle                  | Wirkung                                                                                  | Für normal Sterbliche                                                                 |
| ------------------------ | ---------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| Transportbefehle         |                                                                                          |                                                                                       |
| $R_i\leftarrow R_j$      | $[R_i]\stackrel{\text{def}}{=}[R_j]$                                                     | Setze Wert von $R_i$ auf den Wert von $R_j$                                           |
| $R_i\leftarrow RR_j$     | $[R_i]\stackrel{\text{def}}{=}[R[R_j]]$                                                  | Setze Wert von $R_i$ auf den Wert von dem Register auf das der Wert von $RR_j$ zeigt. |
| $RR_i\leftarrow R_j$     | $[R[R_i]]\stackrel{\text{def}}{=}[R_j]$                                                  | Setzt den Wert von dem Register auf das $RR_i$ zeigt auf den Wert von $R_j$           |
| Arithmetische Befehle    |                                                                                          |                                                                                       |
| $R_i\leftarrow k$        | $[R_i]\stackrel{\text{def}}{=}k$                                                         | Setze Wert von $R_i$ auf den Wert auf k                                               |
| $R_i\leftarrow R_j+R_k$  | $[R_i]\stackrel{\text{def}}{=}[R_j]+[R_k]$                                               | Setze Wert von $R_i$ auf den Wert von $R_j+R_k$                                       |
| $R_i\leftarrow R_j-R_k$  | $[R_i]\stackrel{\text{def}}{=}[R_j]-[R_k]$                                               | Setze Wert von $R_i$ auf den Wert von $R_j-R_k$                                       |
| Sprungbefehle            |                                                                                          |                                                                                       |
| $GOTO\ m$                | $[BR]\stackrel{\text{def}}{=}m$                                                          | Gehe zur Zeile $m$                                                                    |
| $IF\ R_i = 0\ GOTO\ m$   | $BR\stackrel{\text{def}}{=}\begin{cases}m,&falls\ [R_j]=0 \\ [BR]+1 &sonst\end{cases}$   | Gehe zur Zeile m wenn $R_i$ genau 0 ist                                               |
| $IF\ R_i \gt 0\ GOTO\ m$ | $BR\stackrel{\text{def}}{=}\begin{cases}m,&falls\ [R_j]\gt0 \\ [BR]+1 &sonst\end{cases}$ | Gehe zur Zeile m wenn $R_i$ größer 0 ist                                              |
| Stoppbefehl              |                                                                                          |                                                                                       |
| $STOP$                   |                                                                                          | Ende der Berechnung                                                                   |

---
##### Übung 1: Multiplikation mit einer RAM ($x*y$) (S.53)

Ausgangssituation:    $[R0]=x,\ [R1]=y, [R_i]=0\ für\ i\geq2$ 
				 - Jedes Register nach den Ersten 2 ist 0
Endsituation:              $[R0]=x*y$
Idee:                           $x*y=\underbrace{x+x+x+....+x}_{y-mal}$
Hilfsregister:               $[R2] =\ Zwischensumme,\ [R3] = 1$ 
                - Zwischensumme da rechnest du alles zusammen
                - R3 damit du runterzählen kannst
    
>[!code]+ Programm:
>---
>
>|0|      R3 $\leftarrow$ 1 |//Set R3 to 1|
>|--|--|--|
>|1|      IF R1 = 0 GOTO 5 |  //If R1 is exactly 0 also 0$*$y Jump to line 5|
>|2    | R2 ← R2 + R0   |    //Set Add to R2 the Value of R0|
>|3    | R1 ← R1 − R3   |    //R3-1 to count backwards|
>|4    | GOTO 1         |       // Jump to line 1 here a loop|
>|5    | R0 ← R2        |       // Set the final number to R0|
>|6    | STOP           |         //Stop the Program|

#### RAM-berechenbar

![[TheoInf/Definitionen#^a72847]]

---
##### Übung 2: $f(x,\ y,\ z)\stackrel{\text{def}}{=}x+y+z$ ist berechenbar?

Die Funktion $f(x,\ y,\ z)\stackrel{\text{def}}{=}x+y+z$ ist im RAM-berechenbar, weil die folgende RAM diese Funktion berechnet:

>[!code]+ Programm
>0|$R0\leftarrow R0+R1$|//adds x+y=xy
>--|--|--
>1|$R0 \leftarrow R0+R2$| //adds xy+z
>3|STOP
>
>3-stellige Funktion

---
##### Übung 3:

>[!code]+ Programm
>---
>0|$R0\leftarrow R0+R1$|//Bildet eingabe auf sich selbst ab
>--|--|--
>2|STOP
>
>Diese 1-stellige Funktion id:$\mathbb{N}\rightarrow \mathbb{N}$ mit $id(x)$ für alle $x \in \mathbb{N}$ wird auch <span style="color:red"> Identitätsfunktion</span> gennant. Sie bildet Ihr einzigstes Argument auf sich selbst ab.

Jede RAM berechnet unendlich viele Funktionen für jedes $n\geq 0$.

Durch jede RAM wird auch eine Funktion definiert.

---
#### Funktionen

$$RAM \stackrel{\text{def}}{=} \{f:f \text{ist RAM-berechenbarß\}}$$

Die Menge $RAM$ ist eine Menge von Funktionen $f$ die es eine Random-Access-Machine gibt, die $f$ berechnet.

Am besten stellt man sich eine Funktion vor als eine Tabelle den Eingabe und Ausgabe werten.

| Eingabe x | Ausgabe f(x) |
| --------- | ------------ |
| 0         | 5            |
| 1         | 6            |
| 2         | 9            |
| 3         | 14           |
| 4         | 21           |
| 5         | 30           |
| ...       | ...          |

Jede Random-Access-Machine definiert auch eine Funktion.

![[TheoInf/Definitionen#^a94a52]]
![[TheoInf/Definitionen#^b63ff6]]

>[!Note]+ Totalen Funktionen
>haben für jede Eingabe auch eine Ausgabe 

>[!Note]+ Partiellen Funktionen
>haben Eingaben für die keine Ausgaben definiert sind.

Eine Partielle Funktion wäre zum Beispiel das folgende Program/RAM:

| BR  | Program               | Kommentar          |
| --- | --------------------- | ------------------ |
| 0   | $R1\leftarrow 4$      | R1 = 4             |
| 1   | $R2\leftarrow R1-R0$  | R2 = 4 - X         |
| 2   | $IF\ R2\gt0\ GOTO\ 5$ | //Endlos für X < 4 |
| 3   | $R0 \leftarrow R0+R0$ |                    |
| 4   | $STOP$                |                    |
| 5   | $GOTO\ 5$             | //Endlos loop      |

Dieses Ram Programm berechnet die partielle Funktion M

| x   | $f_M(x)$        |
| --- | --------------- |
| 0   | nicht definiert |
| 1   | nicht definiert |
| 2   | nicht definiert |
| 3   | nicht definiert |
| 4   | 8               |
| 5   | 10              |
| 6   | 12              |
| ... | ...             |

siehe Definition below:

- $E_{f_M}= \mathbb{N}$ //Die Eingabemenge sind die Natürlichen Zahlen
- $D_{f_M}= \mathbb{N}-\{0,1,2,3\}$ //Definitionsmenge sind alle Zahlen kleiner 4 bei 4 Endlossschleife
- $W_{f_M} = \{y:y \text{ ist eine gerade Zahl größer gleich 8}\}$ //Das Ergebnis das das Programm ausgibt

---
![[TheoInf/Definitionen#^de852c]]

---
