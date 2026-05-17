#### Aufgabe 27
In der Vorlesung wurde eine Implementierung für die Sortierroutine Insertionsort vorgestellt. Es sei folgendes Feld gegeben: $a[9]={0, 10, 20, 1, 11, 21, 2,12, 22}$ 
##### a) Wenden Sie das Sortierverfahren Insertionsort auf dieses Feld an und geben Sie die Zwischenergebnisse für jeden Schleifendurchlauf innerhalb der äußeren Schleife an.

>[!code]- main.cpp
>```
>int* insertSort(int* unsortedList, int length) {
>    int j, tmp;
>    int countCompare = 0;
>    for (int i = 0; i <= length - 2; i++) {
>
>        j = i + 1;
>        tmp = unsortedList[j];
>
>        while (j > 0 ) {
>            countCompare++;
>
>            if (tmp < unsortedList[j - 1]) {
>                unsortedList[j] = unsortedList[j - 1];
>                j--;
>            }
>            else {
>                break;
>            }
>        }
>        unsortedList[j] = tmp;
>        cout << "List sofar: [";
>        for(int z = 0; z < length; z++) {
>            cout << unsortedList[z];
>            if (z < length - 1) {
>                cout << ", ";
>            }
>        }
>        cout << "];\n";
>    }
>    cout << "Comparisions made: " << countCompare << "\n";
>    return unsortedList;
>}
>```
##### b) Wie viele Vergleiche werden benötigt? 
17
#### Aufgabe 28
In der Vorlesung wurde eine Implementierung für die Sortierroutine Selectionsort vorgestellt. Es sei folgendes Feld gegeben: $a[9]={0, 10, 20, 1, 11, 21, 2,12, 22}$
##### a) Wenden Sie das Sortierverfahren Selectionsort auf dieses Feld an und geben Sie die Zwischenergebnisse für jeden Schleifendurchlauf innerhalb der äußeren Schleife an. 

>[!code]- main.cpp
>```
>void selectionSort(int* unsortedList, int length) {
>    int minIndex = 0;
>    int countCompare = 0;
>
>    for (int j = 0; j < length - 1;j++) {
>        minIndex = j;
>        for (int i = j + 1; i < length; i++) {
>            countCompare++;
>            if (unsortedList[minIndex] > unsortedList[i]) {
>                minIndex = i;
>            }
>        }
>        swap(unsortedList[j], unsortedList[minIndex]);
>        listPrint(unsortedList, length);
>    }
>    cout << "Comparisions made: " << countCompare << "\n";
>
>}
>```

##### b) Wie viele Vergleiche werden benötigt? 
36

#### Aufgabe 29
In der Vorlesung wurde eine Implementierung für die Sortierroutine Exchangesort vorgestellt. Es sei folgendes Feld gegeben: $a[9]={0, 10, 20, 1, 11, 21, 2,12, 22}$ 

##### a) Wenden Sie das Sortierverfahren Exchangesort auf dieses Feld an und geben Sie die Zwischenergebnisse für jeden Schleifendurchlauf innerhalb der äußeren Schleife an. 

>[!code]- main.cpp
>```
>void exchangeSort(int* unsortedList, int length) {
>
>    int minIndex;
>    int maxIndex;
>    int countCompare = 0;
>
>    for (int j = 0; j < length - 1;j++) {
>        minIndex = j;
>        maxIndex = length-1-j;
>        for (int i = j + 1; i < length; i++) {
>            countCompare++;
>            if (unsortedList[j] > unsortedList[i]) {
>                swap(unsortedList[j], unsortedList[i]);
>            }
>        }
>
>   
>       
>        listPrint(unsortedList, length);
>    }
>    cout << "Comparisions made: " << countCompare << "\n";
>}
>```
##### b) Wie viele Vergleiche werden benötigt?
36
