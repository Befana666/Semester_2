
>[!code]+ main.cpp
>```
>lin_suche(item_type suchwert)
>{
>    int l_u = 0;
>    int l_o = dimension - 1;
>    int suchindex = -1;
>    for (int i = l_u; i <= l_o; i++) {
>        if (daten[i] == suchwert)
>            return i; // suchindex
>    }
>    return suchindex;
>}
>```

^c5a91e
