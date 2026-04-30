#### Rekursive:
>[!code]+ main.cpp
>```
>long fibonacci(int n)
>{
>    if (n <= 2)
>        return 1;
>    else
>        return fibonacci(n - 1) + fibonacci(n - 2);
>}
>```

^429058

#### Iterative
>[!code]+ main.cpp
>```
>int fibo_iterativ(int n)
>{
>    int* afib;
>    afib = new int[n + 1];
>    afib[1] = 1;
>    afib[2] = 1;
>    for (int i = 3; i <= n; i++)
>        afib[i] = afib[i - 1] + afib[i - 2];
>    return afib[n]; 
>}
>```

^b7c330
