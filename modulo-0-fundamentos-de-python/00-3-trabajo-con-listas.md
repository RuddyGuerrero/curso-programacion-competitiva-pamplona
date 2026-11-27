# Trabajo con listas

## Listas unidimensionales

Las listas en Python permiten almacenar datos de cualquier tipo. Son **mutables** y **dinámicas**, que es su principal diferencia con las tuplas. Si vienes de otros lenguajes, se parecen a los *arrays*.

### Crear listas

Una lista se crea con `[]`, separando sus elementos con comas:

```python
lista = [1, 2, 3, 4]  # lista con los elementos 1, 2, 3 y 4
print(lista)           # [1, 2, 3, 4]
```

También se puede crear con `list`, pasándole un iterable:

```python
lista = list("1234")  # lista con los caracteres '1', '2', '3' y '4'
print(lista)          # ['1', '2', '3', '4']
```

Una lista puede almacenar datos de tipos distintos:

```python
lista = [1, "Hola", 3.67, [1, 2, 3]]
print(lista)  # [1, 'Hola', 3.67, [1, 2, 3]]
```

Propiedades de las listas:

- Son **ordenadas**: mantienen el orden en que se definieron.
- Pueden contener **tipos arbitrarios**.
- Se pueden **indexar** con `[i]`.
- Se pueden **anidar**: una lista dentro de otra.
- Son **mutables**: sus elementos se pueden modificar.
- Son **dinámicas**: se pueden añadir o eliminar elementos.

### Acceder y modificar listas

Accedemos a los elementos con corchetes y un índice, que va desde `0` hasta `n - 1`, siendo `n` el tamaño de la lista:

```python
a = [90, "Python", 3.87]
print(a[0])  # 90
print(a[1])  # Python
print(a[2])  # 3.87
```

Los índices negativos cuentan desde el final: `[-1]` es el último elemento y `[-2]` el penúltimo:

```python
a = [90, "Python", 3.87]
print(a[-1])  # 3.87
print(a[-2])  # Python
```

Para modificar un elemento basta con asignarle un nuevo valor:

```python
a = [90, "Python", 3.87]
a[2] = 1
print(a)  # [90, 'Python', 1]
```

Para eliminar un elemento por su índice se usa `del`:

```python
lista = [1, 2, 3, 4, 5]
del lista[1]
print(lista)  # [1, 3, 4, 5]
```

### Leer una lista desde la entrada

En programación competitiva lo más habitual es leer una línea con números separados por espacios:

```python
# Entrada: 5 3 8 1
a = list(map(int, input().split()))
print(a)  # [5, 3, 8, 1]
```

---

## Listas bidimensionales (matrices)

Una **matriz** de `n` filas y `m` columnas se representa como una lista de listas: cada fila es una lista.

```python
matriz = [
    [1, 2, 3],
    [4, 5, 6],
]
print(matriz[0])     # [1, 2, 3]  --> primera fila
print(matriz[1][2])  # 6          --> fila 1, columna 2
```

### Leer una matriz desde la entrada

Normalmente primero se leen `n` y `m`, y después `n` líneas con `m` números cada una:

```python
# Entrada:
# 2 3
# 1 2 3
# 4 5 6
n, m = map(int, input().split())
matriz = []
for i in range(n):
    matriz.append(list(map(int, input().split())))
```

### Crear una matriz vacía

Para crear una matriz de `n × m` llena de ceros:

```python
n, m = 2, 3
matriz = [[0] * m for _ in range(n)]
print(matriz)  # [[0, 0, 0], [0, 0, 0]]
```

> **⚠️ Cuidado:** `[[0] * m] * n` **no** funciona como esperas: crea `n` referencias a la **misma** fila, así que al modificar una fila se modifican todas.
>
> ```python
> mal = [[0] * 3] * 2
> mal[0][0] = 1
> print(mal)  # [[1, 0, 0], [1, 0, 0]]
> ```

### Recorrer una matriz

Con dos ciclos anidados: el exterior recorre las filas y el interior las columnas:

```python
matriz = [[1, 2, 3], [4, 5, 6]]
for i in range(len(matriz)):
    for j in range(len(matriz[i])):
        print(matriz[i][j], end=' ')
    print()
# 1 2 3
# 4 5 6
```

### Operaciones con matrices

Sumar todos los elementos:

```python
matriz = [[1, 2, 3], [4, 5, 6]]
total = sum(sum(fila) for fila in matriz)
print(total)  # 21
```

Multiplicar cada elemento por un número:

```python
matriz = [[1, 2, 3], [4, 5, 6]]
x = 2
resultado = [[x * valor for valor in fila] for fila in matriz]
print(resultado)  # [[2, 4, 6], [8, 10, 12]]
```

---

## 📝 Ejercicios propuestos

1. **Promedio de una matriz.** Dada una matriz de `n` filas y `m` columnas, calcula el promedio de sus elementos.
   [Ver problema en HackerRank](https://www.hackerrank.com/contests/trabajo-con-listas/challenges/promedio-de-una-matriz)

2. **Matriz identidad 1.** Una matriz identidad es aquella cuyos elementos de la diagonal principal (de la forma `M[i][i]`) valen uno y el resto valen cero. Construye una matriz identidad de `n` filas y `m` columnas.
   [Ver problema en HackerRank](https://www.hackerrank.com/contests/trabajo-con-listas/challenges/matriz-identidad-1)

3. **Máximo de la matriz.** Determina la posición (fila y columna) del valor máximo de una matriz de `n` filas y `m` columnas. Si hay varios, imprime el de menor fila y, después, el de menor columna.
   [Ver problema en HackerRank](https://www.hackerrank.com/contests/trabajo-con-listas/challenges/maximo-de-la-matriz)

4. **Número por matriz.** Lee una matriz y un número, y devuelve la matriz que resulta de multiplicar cada elemento por ese número.
   [Ver problema en HackerRank](https://www.hackerrank.com/contests/trabajo-con-listas/challenges/numero-por-matriz)

5. **Multiplicación de matrices 1.** Dadas dos matrices de `2 × 2`, calcula su producto:

   ```text
   | a00 a01 |   | b00 b01 |   | a00·b00 + a01·b10   a00·b01 + a01·b11 |
   | a10 a11 | × | b10 b11 | = | a10·b00 + a11·b10   a10·b01 + a11·b11 |
   ```

   [Ver problema en HackerRank](https://www.hackerrank.com/contests/trabajo-con-listas/challenges/multiplicacion-de-matrices-1)

## 📝 [Problemas: Clase 0.3 – Trabajo con listas](https://www.hackerrank.com/contests/trabajo-con-listas/challenges)
