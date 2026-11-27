# Soluciones a los problemas: Clase 0.4 – Recursividad

## 📝 [Problemas: Clase 0.4 – Recursividad](https://www.hackerrank.com/contests/recursividad/challenges)

## Factorial 2

Imprimir el último dígito distinto de cero de `n!`.

```python
def factorial(n):
    # Caso base: 0! = 1
    if n == 0:
        return 1
    return n * factorial(n - 1)

n = int(input())
fact = factorial(n)
# Quitamos los ceros del final
while fact % 10 == 0:
    fact //= 10
# El último dígito es el resto de dividir entre 10
print(fact % 10)
```

## Números de Fibonacci

```python
# memo[i] guarda fibonacci(i) una vez calculado (-1 = todavía no calculado)
memo = [-1] * 101

def fibonacci(n):
    # Caso base
    if n <= 2:
        return 1
    # Si ya lo calculamos, lo devolvemos sin repetir el trabajo
    if memo[n] != -1:
        return memo[n]
    memo[n] = fibonacci(n - 1) + fibonacci(n - 2)
    return memo[n]

n = int(input())
print(fibonacci(n))
```

## Mínimo común múltiplo 2

```python
def mcd(a, b):
    # Algoritmo de Euclides recursivo: MCD(a, b) = MCD(b, a % b)
    if a % b == 0:
        return b
    return mcd(b, a % b)

a, b = map(int, input().split())
# MCM = a * b / MCD(a, b)
print(a * b // mcd(a, b))
```
