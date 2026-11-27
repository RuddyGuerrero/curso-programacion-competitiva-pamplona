# Recursividad

Una **función recursiva** es aquella que se llama a sí misma. Por ejemplo:

```python
def contador(num):
    if num < 0:
        return
    print(num)
    contador(num - 1)

contador(3)
# 3
# 2
# 1
# 0
```

Con un pequeño cambio conseguimos que la función cuente hacia arriba:

```python
def contador(num):
    if num < 0:
        return
    contador(num - 1)
    print(num)

contador(3)
# 0
# 1
# 2
# 3
```

Ahora cuenta hacia arriba porque la función se llama recursivamente hasta que `num` vale `-1` sin imprimir nada, y después, al ir **volviendo** de las llamadas anteriores, se ejecutan los `print`.

### Caso base de la recursión

> **📝 Nota:** la línea `if num < 0: return` evita que la función se llame a sí misma infinitas veces. Sin ella se desbordaría la **pila de llamadas** (*stack*), que es donde se guarda a qué punto debe volver el programa después de cada llamada. El caso en el que paramos la recursión (`num < 0`) se llama **caso base**.

> **⚠️ Límite de recursión:** Python limita la profundidad de recursión (por defecto, unas 1000 llamadas). Si un problema necesita más, se puede subir con `sys.setrecursionlimit(...)` o, mejor, reescribir la solución con un ciclo.

---

## Retornar valores

Las funciones recursivas también pueden retornar valores, y eso se aprovecha para hacer cálculos. Por ejemplo, el **factorial**, el producto de los `n` primeros números naturales:

```python
def factorial(n):
    if n == 0:
        return 1
    return n * factorial(n - 1)

print(factorial(5))  # 120
```

Y los **números de Fibonacci**:

```python
def fibonacci(n):
    if n <= 2:
        return 1
    return fibonacci(n - 1) + fibonacci(n - 2)

print(fibonacci(5))  # 5
```

> **⚠️ Ojo:** esta versión recalcula los mismos valores una y otra vez, y su tiempo crece de forma exponencial. Guardando los resultados ya calculados (**memoización**) se vuelve lineal; lo verás en la solución del ejercicio y, en profundidad, en la [Clase 11](../modulo-3-programacion-dinamica-basica/11-introduccion-a-la-programacion-dinamica.md).

---

## Obtener combinaciones

Estos ejemplos son sencillos y se pueden programar con ciclos, sin recursividad. De hecho, casi todo lo que se hace con recursividad se puede hacer con ciclos y viceversa, pero no siempre es igual de fácil plantearlo de una manera u otra.

Un caso en el que la recursividad es más natural es cuando queremos **generar todas las combinaciones** posibles de algo. Por ejemplo, imprimir todas las palabras formadas por las letras `a` y `b` de una longitud dada:

```python
def generar(s, n):
    if n == 0:
        print(s)
    else:
        generar(s + 'a', n - 1)
        generar(s + 'b', n - 1)

generar('', 3)
# aaa  aab  aba  abb  baa  bab  bba  bbb
```

---

## 📝 [Problemas: Clase 0.4 – Recursividad](https://www.hackerrank.com/contests/recursividad/challenges)
