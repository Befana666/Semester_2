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

![[Definitionen#^1e3839]]

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

![[Definitionen#^a72847]]

##### Übung 2: $f(x,\ y,\ z)\stackrel{\text{def}}{=}x+y+z$ ist berechenbar?

Die Funktion $f(x,\ y,\ z)\stackrel{\text{def}}{=}x+y+z$ ist im RAM-berechenbar, weil die folgende RAM diese Funktion berechnet:

>[!code]+ Programm
>0|$R0\leftarrow R0+R1|//adds x+y=xy
>--|--|--
>1|R0 \leftarrow R0+R2| //adds xy+z
>3|STOP

