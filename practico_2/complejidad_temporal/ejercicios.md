# Parte 1: Análisis de eficiencia temporal

__Ejercicio 1__
Calcular la eficiencia de los siguientes procedimientos, mostrando la justificación del cálculo.  

a.
```
Metodo_1(var conjunto[1...n], int n) { 
    bool variableCond = calcularCondicion(conjunto);
    Si(variableCond) {
        procesar(Conjunto)
        Metodo_1(conjunto, n/3)
    } si no {
        Metodo_1(conjunto, n/3);
    }
    fin si no
}
```
**Condiciones iniciales**  
- `calcularCondicion()` es O(log n)
- `procesar()` es O(n)


1. **Variable de Entrada**

    `n`  

2. **Estructura del código**

    T(n) <- `recursión`

3. **Fórmula de la estructura**

    `T(n) = aT(n/b) + p(n^k)` <- se aplicará el método por división.

4. **Fórmula resultante**

    _a_ = 1 <- se llama una sola vez a la recursión  
    _b_ = 3 <- cantidad en que se divide la variable de entrada
    _k_ = 1 <- polinomio de grado 1 correspondiente a procesar() que pertenece a O(n)

    Dado que a < b^k  y por definición vista en clase  
    `T(n) = n^k`  
    `T(n) = n^1`  
    `T(n) = n`  

5. **Solución**  
    Dado que `T(n) = n` es un polinomio de orden 1 y es la complejidad mayor del algoritmo entonces,
    T metodo_1 (n) pertenece a O(n)

___

b. 
```
Metodo_2(var conjunto[1...n], int n) { 
    bool variableCond = calcularCondicion(conjunto);
    Si(variableCond) {
        procesar(Conjunto)
    } si no {
        Metodo_1(conjunto, n/2)
        Metodo_1(conjunto, n/2);
    }
    fin si no
}
```
**Condiciones iniciales**  
- `calcularCondicion()` es constante
- `procesar()` es constante


1. **Variable de Entrada**

    `n`  

2. **Estructura del código**

    T(n) <- `recursión`

3. **Fórmula de la estructura**

    `T(n) = aT(n/b) + p(n^k)` <- se aplicará el método por división.

4. **Fórmula resultante**

    _a_ = 2 <- se llama una sola vez a la recursión  
    _b_ = 2 <- cantidad en que se divide la variable de entrada  
    _k_ = 0 

    Dado que a > b^k  y por definición vista en clase  
    `T(n) = n^[log_b(a)]`  
    `T(n) = n^[log_2(2)]`  
    `T(n) = n^1`  
    `T(n) = n`  

5. **Solución**  
    Dado que `T(n) = n` es un polinomio de orden 1 entonces, T metodo_2 (n) pertenece a O(n)

___

c.
```
Metodo_3(var conjunto[1...n], int n) { 
    int val = calcularValor(n);
    mientras(val < n){
        procesar(conjunto)
    }
    Metodo_3(conjunto, n-1)
    Metodo_3(conjunto, n-1)
}
```
**Condiciones iniciales**  
- `calcularCondicion()` es constante
- `procesar()` es n log n


1. **Variable de Entrada**


2. **Estructura del código**


3. **Fórmula de la estructura**


4. **Fórmula resultante**

    _a_ = 
    _b_ =   
    _k_ = 

5. **Solución**  

___

__Ejercicio 2__  
Dado el siguiente algoritmo DyC y conociendo que su costo es de O(n), ¿Qué orden tiene el método P?  

```
DyC(V[inicio..fin])
    si(fin>inicio)
        mitad = (inicio+fin) / 2
        DyC(V[inicio..mitad])
        DyC(V[mitad+1..fin])
        P(V)
    finsi
finDyC
```
**Solución**

Definición de complejidad para estructuras recursivas:

 `2T(n/2) + p(n^k)`  

_a_ = 2  
_b_ = 2  
_k_ = ?  

si k = 0 entonces
    2 > 2^0  
    2 > 1  
    
`T(n) = a > b^k` => `T(n) = n^[log_2(2)]` => `T(n) = n^1` => `T(n) = n`, entonces P(V) es constante
y T DyC(n) pertenece a O(n) y se cumple la condición previa.

si k = 1 entonces
    
    2 = 2^1
    2 = 2  
    a = b  

`T(n) = n^k log n` => `T(n) = n^1 log n` => `T(n) = n log n`, entonces P(V) es polinomio de grado 1
 y T DyC(n) pertenece a O(n log n) y no se cumple la condicón previa.

si k > 1 entonces  
`T(n) = n^k` entonces T DyC(n) no pertenece a O(n)

