# Soluciones a los problemas: Clase 0.1 – Números y operaciones aritméticas elementales

## 📝 [Problemas: Clase 0.1 – Números y operaciones aritméticas elementales](https://www.hackerrank.com/contests/campamento-urbano-dia-1/challenges)

## [Kilómetros a metros](https://www.hackerrank.com/contests/campamento-urbano-dia-1/challenges/kilometros-a-metros)

```python
# Leemos la distancia en kilómetros
km = int(input())
# Un kilómetro tiene 1000 metros
metros = km * 1000
print(metros)
```

## [Expresar horas y minutos en minutos](https://www.hackerrank.com/contests/campamento-urbano-dia-1/challenges/expresar-horas-y-minutos-en-minutos)

```python
# Leemos la hora en formato hh:mm y separamos horas y minutos
hh, mm = map(int, input().split(':'))
# Cada hora tiene 60 minutos
print(hh * 60 + mm)
```

## [Centígrados a Fahrenheit](https://www.hackerrank.com/contests/campamento-urbano-dia-1/challenges/convertir-grados-centigrados-a-grados-fahrenheit)

```python
# Leemos la temperatura en grados centígrados
c = int(input())
# Aplicamos la fórmula F = 9/5 * C + 32
f = 9 / 5 * c + 32
# El formato {:.5f} ya redondea a 5 decimales, no hace falta round()
print("{:.5f}".format(f))
```

## [Distancia Manhattan](https://www.hackerrank.com/contests/campamento-urbano-dia-1/challenges/distancia-manhatan/problem)

```python
# Leemos las coordenadas de los dos puntos
x1, y1 = map(int, input().split())
x2, y2 = map(int, input().split())
# Distancia Manhattan: |x1 - x2| + |y1 - y2|
print(abs(x1 - x2) + abs(y1 - y2))
```

## [Área del triángulo](https://www.hackerrank.com/contests/campamento-urbano-dia-1/challenges/area-del-triangulo-conocidos-los-tres-lados)

```python
# Leemos los tres lados
a, b, c = map(int, input().split())
# Semiperímetro
s = (a + b + c) / 2
# Fórmula de Herón
area = (s * (s - a) * (s - b) * (s - c)) ** (1 / 2)
# Mostramos la parte entera del área
print(int(area))
```

## [Suma los dígitos](https://www.hackerrank.com/contests/campamento-urbano-dia-1/challenges/suma-los-digitos-de-los-extremos-y-el-del-centro/problem)

```python
# Leemos el número como texto para acceder a cada dígito
s = input()
primero = int(s[0])
centro = int(s[1])
ultimo = int(s[2])
# Número formado por los extremos (por ejemplo 2 y 7 -> 27) más el centro
print(primero * 10 + ultimo + centro)
```

## [Número incluido](https://www.hackerrank.com/contests/campamento-urbano-dia-1/challenges/numero-incluido)

### Solución 1: recorriendo los caracteres

```python
# Convertimos cada carácter del número en un dígito y los sumamos
print(sum(map(int, input().strip())))
```

### Solución 2: usando cociente y resto

```python
n = int(input())
suma = 0
while n > 0:
    # n % 10 es el último dígito
    suma += n % 10
    # n // 10 elimina el último dígito
    n //= 10
print(suma)
```
