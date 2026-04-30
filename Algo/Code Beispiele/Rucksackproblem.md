>[!code]+ main.cpp
>```
>int knap(int cap, int* itk)
>{
>    int i;
>    int space;
>    int max;
>    int t;
>    //N and items[i] arent defined in this function
>    for (i = 0, max = 0;i < N;i++)
>        if ((space = cap - items[i].size) >= 0)
>            if ((t = knap(space, itk) + items[i].val) > max)
>            {
>                max = t; // neues Wert-Maximum 
>                itk[cap] = i; // momentan gepacktes Wertstück 
>            };
>    return max;
>}
>```

^044660
