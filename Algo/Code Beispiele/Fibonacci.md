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

Dynamisch Rekursive 
>[!code]+ main.cpp
>```
>int fibo_dynamic(int n)
>{
>    static int known_fib[100];
>    known_fib[1] = 1;
>    known_fib[2] = 1;
>    int result;
>    if (known_fib[n] != 0)
>        result = known_fib[n]; // Ergebnis bereits bekannt 
>    else
>    {
>        result = fibo_dynamic(n - 1) + fibo_dynamic(n - 2);
>        known_fib[n] = result;
>    }
>    return result;
>}
>```

^2c7b4d
