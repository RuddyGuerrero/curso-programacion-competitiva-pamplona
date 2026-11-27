# Soluciones a los problemas: Clase 0.2 – Ciclos for y while

## 📝 [Problemas: Clase 0.2 – Ciclos for y while](https://www.hackerrank.com/contests/ciclos-for-y-while/challenges)

## [Suma de los n primeros números de Fibonacci](https://www.hackerrank.com/contests/ciclos-for-y-while/challenges/suma-de-los-n-primeros-numeros-de-la-sucesion-de-fibonacci)

```python
n = int(input())
# a y b son dos términos consecutivos de la sucesión
a, b = 1, 1
suma = 0
for _ in range(n):
    suma += a
    # Avanzamos un término: el siguiente es la suma de los dos anteriores
    a, b = b, a + b
print(suma)
```

## [Número de términos](https://www.hackerrank.com/contests/ciclos-for-y-while/challenges/numero-de-terminos)

```python
x = int(input())
i = 0
suma = 0
# Sumamos cuadrados mientras la suma no supere a x
while suma <= x:
    i += 1
    suma += i * i
print(i)
```

## [Forma de diamante](https://www.hackerrank.com/contests/ciclos-for-y-while/challenges/forma-de-diamante)

```python
n = int(input())
# Posición (empezando en 1) de la fila y columna centrales
centro = (n + 1) // 2
for i in range(1, n + 1):
    fila = []
    for j in range(1, n + 1):
        # Distancia Manhattan de la celda (i, j) al centro
        d = abs(i - centro) + abs(j - centro)
        # Las celdas cercanas al centro forman el diamante
        fila.append('*' if d < (n + 1) / 2 else ' ')
    # Separamos las celdas con un espacio
    print(' '.join(fila))
```

## [Números perfectos 3](https://www.hackerrank.com/contests/ciclos-for-y-while/challenges/numeros-perfectos-3-1)

```python
a, b = map(int, input().split())
for n in range(a, b + 1):
    # Sumamos los divisores de n buscando solo hasta su raíz cuadrada: O(√n)
    suma = 1 if n > 1 else 0
    i = 2
    while i * i <= n:
        if n % i == 0:
            suma += i
            # n // i es el divisor "pareja" de i, si es distinto
            if i != n // i:
                suma += n // i
        i += 1
    if suma == n:
        print(n, end=' ')
```

> 👉 Esta optimización con la raíz cuadrada se explica en la [Clase 4](../modulo-1-matematicas-y-fundamentos-basicos/04-numeros-perfectos-abundantes-y-deficientes.md).

## Mínimo común múltiplo 2

```python
def mcd(a, b):
    # Algoritmo de Euclides
    while a != 0:
        a, b = b % a, a
    return b

a, b = map(int, input().split())
# MCM = a * b / MCD(a, b)
print(a * b // mcd(a, b))
```

## [Conjetura de Ullman](https://www.hackerrank.com/contests/ciclos-for-y-while/challenges/conjetura-de-ullman)

```python
n = int(input())
pasos = 0
while n > 1:
    if n % 2 == 0:
        n //= 2
    else:
        n = n * 3 + 1
    pasos += 1
print(pasos)
```
