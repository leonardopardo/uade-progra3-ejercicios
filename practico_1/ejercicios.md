# ANÁLISIS Y DISEÑO DE ALGORITMOS I
## Práctico Nº 1. Análisis de eficiencia de algoritmos
### Segunda Parte

## Estructuras
___

__Concatenación__

 `T1(n) + T2(n) + ... + Tk(n) <= (c1 + c2 + ... + ck) * ( max( f(n), g(n), ..., z(n) ) )`

__Selección__

 `T(n) pertenece O(max(f(n), g(n))`

__Iteración__

 `T(n) = tc + (tc + ts) * iteraciones`

___

__Ejercicio 1__

- Ejercicio __a__
```
void Calculo (double a, double b, double c) {
    double resultado;
    resultado = a + b + b*c + (a+b-c)/(a+b) + 4.0;
    cout << resultado << endl;
}
```
1. Variable de Entrada
2. Estructura del código (concatenación | selección | iteración)
3. Fórmula de la estructura
4. Fórmula resultante
5. Solución 

___

- Ejercicio __b__
```
float Suma (float arreglo[ ], int cantidad) {
    float suma= 0;
    
    for (int i = 0; i < cantidad; i++)
        suma += arreglo [i];
    
    return suma;
}
```
1. Variable de Entrada

    Se identifica a "cantidad" como variable de entrada.
    `cantidad = n`

2. Estructura del código (concatenación | selección | iteración)

    T(n) <- `Estructura iterativa`

3. Fórmula de la estructura

    `T(n) = tc + (tc + ts) * iteraciones`

4. Fórmula resultante

    `T(n) = 1 + (1 + 4) * n`

    'suman = 0' se suman al primer termino, entonces

    `T(n) = 2 + 5n`

    `T(n) = 5n + 2`

5. Solución 

    Dado que `T(n) = 5n + 2` es una función líneal, despojandodola de sus constantes y factores, 
    y por el principio de invariaza tenemos que `T(n) pertenece O(n)`

___

- Ejercicio __c__
```
unsigned int Fibonacci (unsigned int i) {
    int Fi_1 = 1, Fi_2 = 1, Fi= 1;
    for (int j = 2; j <= i; j++){
        Fi= Fi_1 + Fi_2;
        Fi_2 = Fi_1;
        Fi_1 = Fi;
    }
    return Fi;
}
```
1. Variable de Entrada

    Se identifica como variable de entrada a `i`

    `i = n`

2. Estructura del código (concatenación | selección | iteración)

    T(n) <- `Estructura iterativa`

3. Fórmula de la estructura

    `T(n) = tc + (tc + ts) * iteraciones`

4. Fórmula resultante

    `T(n) = 1 + (1 + 5) * (n - 2)`
    
    `T(n) = 1 +  6(n - 2)`
    
    `T(n) = 1 +  6n - 12`

    Por la trible asignación antes del for __int Fi_1 = 1, Fi_2 = 1, Fi= 1;__  le sumo 3 unidades en el primer termino, entonces

    `T(n) = 3 + 6n -12`
    
    `T(n) = 6n - 9`


5. Solución 
    
    Dado que `T(n) = 6n - 9` es una función líneal, despojandodola de sus constantes y factores, y por el principio de invariaza tenemos que `T(n) pertenece O(n)`
___

- Ejercicio __d__
```
void Transpuesta (int Matriz [][SIZE]) {
    for (int i = 0; i < SIZE; i++)
        for (int j = i+1; j < SIZE; j++){
            int aux= Matriz [i][j];
            Matriz [i][j]= Matriz [j][i];
            Matriz [j][i]= aux;
        }
}
```
1. Variable de Entrada

    Se identifica como variable de entrada SIZE

    `SIZE = n`

2. Estructura del código (concatenación | selección | iteración)
    
    T1(n), T2(n) <- `Estructura Iterativa`

3. Fórmula de la estructura

    `T(n) = tc + (tc + ts) * iteraciones`

4. Fórmula resultante

    __T1(n)__

    `T1(n) = 1 + (1 + 8) * (n - 1)`
    
    `T1(n) = 1 + 9 * ( n - 1)`
    
    `T1(n) = 1 + 9n - 9`
    
    `T1(n) = 1 + 9n - 9`

    __T2(n)__

    `T2(n) = 1 + [ 1 + ( 1 + 9n - 9 ) ] * n`
    
    `T2(n) = 1 + [ n + n( 1 + 9n - 9 ) ]`
    
    `T2(n) = 1 + [ n + n + 9n^2 - 9n ]`
    
    `T2(n) = 1 - 7n + 9n^2` ; 

5. Solución
    Dado que __`T2(n) = 1 - 7n + 9n^2`__ es un polinomio de grado 2, despojandodolo de sus constantes y factores, 
    y por el principio de invariaza tenemos que `T2(n) pertenece O(n^2)`
___

- Ejercicio __e__
```
void productoMatricesCuadradas (double a[N][N], double b[N][N], double c[N][N]) {
    for (int i= 0; i < N; i++){
        for (int j= 0; j < N; j++) {
            c[i][j] = 0.0;
            for (int k= 0; k < N ; k++)
                c[i][j] += a[i][k] * b[k][j];
        }
    }
}
```

1. Variable de Entrada

    Se identifica la variable de entrada `N`

    `N = n`

2. Estructura del código (concatenación | selección | iteración)

    T1(n), T2(n), T3(n) <- `Estructura Iterativa`

3. Fórmula de la estructura

    `T(n) = tc + (tc + ts) * iteraciones`

4. Fórmula resultante

    __T1(n)__

    `T1(n) = 1 + ( 1 + 7 ) * n`

    Le sumo 2 unidades al primer termino por el acceso y la asignación del termino __`c[i][j] = 0.0;`__ y una unidad más por `j++`

    `T1(n) = 4 + ( 1 + 7 ) * n`

    __T2(n)__
    
    `T2(n) = 1 + { 1 + [ 4 + ( 1 + 7 ) * n ] } * n`

    Le sumo 1 unidad al primer termino por `i++`

    `T2(n) = 2 + { 1 + [ 4 + ( 1 + 7 ) * n ] } * n`

    __T3(n)__

    `T3(n) = 1 + [ 1 + ( 2 + { 1 + [ 4 + ( 1 + 7 ) * n ] } * n ) ] * n`

    `T3(n) = 1 + [ 1 + ( 2 + { 1 + [ 4 + 8n ] } * n ) ] * n`

    `T3(n) = 1 + [ 1 + ( 2 + { 1 + 4 + 8n } * n ) ] * n`

    `T3(n) = 1 + [ 1 + ( 2 + 1n + 4n + 8n^2 ) ] * n`

    `T3(n) = 1 + [ 1 + 2 + 1n + 4n + 8n^2 ] * n`

    `T3(n) = 1 + [ 3 + 5n + 8n^2 ] * n`

    `T3(n) = 1 + 3n + 5n^2 + 8n^3`

5. Solución 

    Dado que __`T3(n) = 1 + 3n + 5n^2 + 8n^3`__ es un polinomio de grado 3, despojandodolo de sus constantes y factores, 
    y por el principio de invariaza tenemos que `T3(n) pertenece O(n^3)`
___

- Ejercicio __f__
```
void CaminosMinimos (float costos[][SIZE],float A[][SIZE]) {
    for (int i = 0; i < SIZE; i++)
        for (int j = 0; j < SIZE; j++)
            A[i] [j] = costos [i] [j];
    
    for (int k = 0; k < SIZE; k++)
        for (int i = 0; i < SIZE; i++)
            for (int j = 0; j < SIZE; j++)
                if(A[i][j] > A[i][k] + A[k][j])
                    A[i][j] = A[i][k] + A[k][j];
} 
```
1. Variable de Entrada

     Se identifica la variable de entrada `SIZE`

    `SIZE = n`

2. Estructura del código (concatenación | selección | iteración)

    
    T1(n) pertenece O(max(f(n), g(n)) <- `Estructura de selección`

    ```
    if(A[i][j] > A[i][k] + A[k][j])
                    A[i][j] = A[i][k] + A[k][j];
    ```
    
    T2(n), T3(n), T4(n) <- `Estructura de iteración`

    ``` 
    for (int k = 0; k < SIZE; k++) <- T4(n)
        for (int i = 0; i < SIZE; i++) <- T3(n)
            for (int j = 0; j < SIZE; j++) <- T2(n)
    ```
       
    T5(n), T6(n) <- `Estructura de iteración`

    ```
    for (int i = 0; i < SIZE; i++) <- T6(n)
        for (int j = 0; j < SIZE; j++) <- T5(n)
            A[i] [j] = costos [i] [j];
    ```
    
3. Fórmula de la estructura

    `T(n) pertenece O(max(f(n), g(n))`

    `T(n) = tc + (tc + ts) * iteraciones`

4. Fórmula resultante

    __T1(n)__

    **10 OE, acceso a memoria *6, operación de suma *2, operación de asignación *1, operación de comparación *1 ***
  
   __T2(n)__

    `T2(n) = 1 + ( 1 + 1 + T1(n) ) * n`

    `T2(n) = 1 + ( 1 + 1 + 10 ) * n`

    `T2(n) = 1 + 12n`

    __T3(n)__

    `T3(n) = 1 + [ 1 + ( 1 + T2(n)) ] * n`

    `T3(n) = 1 + [ 1 + 1 + 1 + 12n ] * n`

    `T3(n) = 1 + [ 3 + 12n ] * n`

    `T3(n) = 1 + 3n + 12n^2`

    __T4(n)__
    
    `T4(n) = 1 + [ 1 + ( 1 + T3(n)) ] * n`

    `T4(n) = 1 + [ 1 + 1 + 1 + 3n + 12n^2 ] * n`

    `T4(n) = 1 + [ 3 + 3n + 12n^2 ] * n`
    
    `T4(n) = 1 + 3n + 3n^2 + 12n^3`

    
    __T5(n)__

    `T5(n) = 1 + ( 1 + 4 ) * n`

    `T5(n) = 1 + 5n`

    
    __T6(n)__

    `T6(n) = 1 + [ 1 + ( 1 + T5(n) ) ] * n`

    `T6(n) = 1 + [ 1 + ( 1 + 1 + 5n ) ] * n`

    `T6(n) = 1 + [ 1 +  1 + 1 + 5n  ] * n`

    `T6(n) = 1 + [ 3 + 5n  ] * n`

    `T6(n) = 1 + 3n + 5n^2 `

5. Solución 


___

- Ejercicio __g__
```
# include <iostream>

using namespace std;

const int m = 100000000;

const int m1 = 10000;

const int b = 31415821;

int a;

int mult (int p, int q) {
    
    int p1, p0, q1, q0;
    
    p1 = p / m1; 
    
    p0 = p % m1; // el operador binario “%” es el módulo, % calcula el resto de la división entera.
    
    q1 = q / m1; 
    
    q0 = q % m1;
    
    return (((p0 * q1 + p1 * q0) % m1) * m1 + p0 * q0) % m;
}

int random (){
    a= (mult (a,b) + 1) % m;
    return a;
}

void random_1 (){
    cin >> a;
    for (int i= 1; i <= 1000000; i++)
        cout << random() << endl;
}

void random_2 (){
    int i, N;
    cin >> N >> a;
    for (i= 1; i <= N; i++)
        cout << random() << endl;
}

int main (){
    random_1();
    random_2();
    return 0;
}
```

1. Variable de Entrada


2. Estructura del código (concatenación | selección | iteración)


3. Fórmula de la estructura


4. Fórmula resultante


5. Solución 

___

- Ejercicio __h__
```
int BusquedaBinariaIterativa( int Numeros[], int inicio, int fin, int numeroBuscado ) {
    
    // Números es un arreglo de enteros ordenados de menor a mayor
    while (inicio <= fin) {
        
        int pos = (inicio + fin) / 2;
        
        if (numeroBuscado < Numeros[pos])
            fin = pos - 1;
        else
            if (numeroBuscado > Numeros[pos])
                inicio = pos + 1;
            else
                return pos;
    }
    return -1;
}
```
1. Variable de Entrada

    `n = fin - inicio`

2. Estructura del código (concatenación | selección | iteración)

    T1(n) <- `Estructura de selección`

    T2(n) <- `Estructura de selección`

    T3(n) <- `Estructura de iteración`

3. Fórmula de la estructura

    `T(n) pertenece O(max(f(n), g(n)))` <- Selección
    
    `T(n) = tc + (tc + ts) * #iteraciones` <- Iteración

4. Fórmula resultante

    __T1(n)__

    ```
    if (numeroBuscado > Numeros[pos])
        inicio = pos + 1;
    else
        return pos;
    ```

    ```
    if (numeroBuscado > Numeros[pos])
        inicio = pos + 1;
    ```
    **4 OE <- comparación, acceso a memoria, suma, asignación**

    ```
    else
        return pos;
    ```
    0 OE

    __T2(n)__

    __T3(n)__

5. Solución 
___

- Ejercicio __i__
```
int Contar (int n, int m){
    
    int j, contadorSentencias = 0,  i = 1;
    
    while (i <= m) {
        
        j = n;
        
        while (j != 0){
            j = j / 2; 
            contadorSentencias ++;
        }
        
        i++;
    }

    return contadorSentencias;
}
```
1. Variable de Entrada

    Dado que la primera iteración depende de `n` y la segunda iteración depende de `m`
    las variables de entrada seran `m, n`

2. Estructura del código (concatenación | selección | iteración)

    __T1(n)__
    ```
    while (j != 0){
        j = j / 2; 
        contadorSentencias ++;
    }
    ```

    __T2(m, n)__
    ```
    while (i <= m) {
        
        j = n;
        
        T1(n)
        
        i++;
    }
    ```

3. Fórmula de la estructura

    __T1(n)__
    
    `T1(n) = ln n`

    __T2(m, n)__
    
    `T2(m, n) = 1 + ( 1 + 2 T1(n)) * m`

    `T2(m, n) = 1 + ( 1 + 2 ln n) * m`

    `T2(m, n) = 1 + m + 2m ln n`

    `T2(m, n) = 1 + m ( 2 ln n)`

4. Fórmula resultante

    ???

5. Solución 

    Dado que __`T2(m, n) = 1 + m ( 2 ln n)`__ es un polinomio, despojandodolo de sus constantes y factores, 
    y por el principio de invariaza tenemos que `T2(m, n) pertenece O(m log n)`
___

- Ejercicio __j__
```
j. void par_impar (int k) {
    int i, j, contadorSentencias = 0;
    for (i= 1; i <= k; i++) {
        for (j= 1; j <= i; j++)
            contadorSentencias++;
        if (i % 2 == 0)
            for (j= i; j <= k; j++)
                contadorSentencias++;
    }
}
```

- Ejercicio __k__
```
void Contador (int n) {
    int x, m, cuenta;
    for (m = 2; m <= n; m++) {
        cuenta = 0;
        x = 2;
        while (x <= m) {
            x = 2*x;
            cuenta++;
        }
        cout << cuenta;
    }
}
```
1. Variable de Entrada
2. Estructura del código (concatenación | selección | iteración)
3. Fórmula de la estructura
4. Fórmula resultante
5. Solución 

___

__Ejercicio 2__

Codifique en C++ los problemas que se listan a continuación y determine la complejidad temporal en notación Big-Oh:

__a)__ Dado un arreglo de números enteros, escribir una función en C++ que verifique si un valor determinado pertenece o no al arreglo.
```
 // code here ...
```

__b)__ Escribir una función que reciba como parámetro un arreglo de N números naturales, busque el elemento “mayoría” y retorne si existe el elemento mayoría y, en caso positivo, la cantidad de veces que aparece en el arreglo. El elemento mayoría es aquel que aparece más de N/2 veces en el arreglo.
```
 // code here ...
```

__c)__ Escribir en C++ una función que calcule la potencia de un número entero, sin utilizar funciones de bibliotecas.
```
int Potencia(int base, int exponente)
{
    // escriba aquí su código
}
```

__d)__ Dado un arreglo de enteros implementar en C++ las siguientes funciones:
```
void Ordenamiento_Seleccion (double arreglo [], int n)
{
    // escriba aquí su código
}

void Ordenamiento_Burbuja (double arreglo [], int n)
{
    //
}
```

