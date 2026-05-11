Heutzutage immer noch super aufwendig 25% der kommerziell verbrauchten Rechenzeit besteht aus sortieren.

#### Sortierproblem

>[!definition]+ Sortierproblem 
>___
>Gegeben ist eine Folge von Datensätzen $a_1, a_2,....,a_n$
>Jeder Datensatz $a_i$ hat einen Schlüssel $a_i$ key
>Gesucht ist eine Permutation p der Zahlen von 1 bis n derart, dass die Umordnung der Sätzte gemäß p die Schlüssel in aufsteigender Reihenfolge widergibt:
>$$a_1.key \Leftarrow a_2.key \Leftarrow ... \Leftarrow a_n.key$$
>---
>Schlüssel sind ganzzahlig
>Datensätze können auserdem Schlüssel weitere Daten enthalten

Man hat 2 Teilprobleme:
1. Der eigentliche Vergleich zweier Schlüssel
	ist Schlüssel a $\geq$ b oder a $\lt$ b

2. Und das Verschieben / Tauschen der Daten
- Vertauschen benachbarter oder beliebiger Werte
- Verschieben einzelner Sätze um x Werte
- Platzier Satz an eine bestimmte stelle

#### Sortierverfahren

- Einfügen
- Auswählen
- Austauschen
benötigen keinen nennenswerten zusätzlichen Speicher
Für die Komplexitätsanalyse:
- Anzahl der Schlüsselvergleiche C(n)
- Anzahl der Recordbewegungen M(n)

##### Elementare Sortierverfahren (direktes Sortieren)

Komplexität: O($n^2$)
Beispiele: 
- Exchangesort(Bubblesort)
- Insertionsort
- Selectionsort

---
##### Schnelle Sortierverfahren

Komplexität: O(nlogn)