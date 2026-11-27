# Soluciones a los problemas: Clase 0.3 – Trabajo con listas

## 📝 [Problemas: Clase 0.3 – Trabajo con listas](https://www.hackerrank.com/contests/trabajo-con-listas/challenges)

## [Promedio de una matriz](https://www.hackerrank.com/contests/trabajo-con-listas/challenges/promedio-de-una-matriz)

```python
n, m = map(int, input().split())
total = 0
for i in range(n):
    # Sumamos cada fila a medida que la leemos
    total += sum(map(int, input().split()))
# Sumar 0.5 y truncar redondea hacia arriba los valores .5
# (válido para promedios no negativos; con negativos habría que redondear distinto)
print(int(total / (n * m) + 0.5))
```

## [Matriz identidad 1](https://www.hackerrank.com/contests/trabajo-con-listas/challenges/matriz-identidad-1)

```python
n, m = map(int, input().split())
for i in range(n):
    for j in range(m):
        # En la diagonal principal la fila y la columna coinciden
        if i == j:
            print("1 ", end="")
        else:
            print("0 ", end="")
    print()
```

## [Máximo de la matriz](https://www.hackerrank.com/contests/trabajo-con-listas/challenges/maximo-de-la-matriz)

```python
n, m = map(int, input().split())
a = []
for i in range(n):
    a.append(list(map(int, input().split())))

# Empezamos con el primer elemento: así funciona aunque todos sean negativos
maximo = a[0][0]
x, y = 0, 0
for i in range(n):
    for j in range(m):
        # Con > estricto nos quedamos con la primera aparición (menor fila y columna)
        if a[i][j] > maximo:
            maximo = a[i][j]
            x, y = i, j
print(x, y)
```

## [Número por matriz](https://www.hackerrank.com/contests/trabajo-con-listas/challenges/numero-por-matriz)

```python
x = int(input())
n, m = map(int, input().split())
a = []
for i in range(n):
    a.append(list(map(int, input().split())))

# Multiplicamos cada elemento por x
for i in range(n):
    for j in range(m):
        a[i][j] *= x

for i in range(n):
    for j in range(m):
        print(a[i][j], end=" ")
    print()
```

## [Multiplicación de matrices 1](https://www.hackerrank.com/contests/trabajo-con-listas/challenges/multiplicacion-de-matrices-1)

### Solución 1: aplicando la fórmula directamente

```python
a = []
for i in range(2):
    a.append(list(map(int, input().split())))
# Línea vacía que separa las dos matrices
input()
b = []
for i in range(2):
    b.append(list(map(int, input().split())))

print(a[0][0] * b[0][0] + a[0][1] * b[1][0], a[0][0] * b[0][1] + a[0][1] * b[1][1])
print(a[1][0] * b[0][0] + a[1][1] * b[1][0], a[1][0] * b[0][1] + a[1][1] * b[1][1])
```

### Solución 2: con ciclos (sirve para cualquier tamaño)

```python
a = []
for i in range(2):
    a.append(list(map(int, input().split())))
# Línea vacía que separa las dos matrices
input()
b = []
for i in range(2):
    b.append(list(map(int, input().split())))

for i in range(2):
    for j in range(2):
        # El elemento (i, j) es la fila i de a por la columna j de b
        x = 0
        for k in range(2):
            x += a[i][k] * b[k][j]
        print(x, end=" ")
    print()
```
