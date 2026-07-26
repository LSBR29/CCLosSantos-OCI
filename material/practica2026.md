# Práctica OCI 2026

## A. Chayotes en la feria

| | | | |
|---|---|---|---|
| Puntos | 13.69 | Límite de memoria | 256 MiB |
| Límite de tiempo (caso) | 1s | Límite de tiempo (total) | 30s |
| Entrada/Salida | Consola | Tamaño límite de entrada (bytes) | 10 KiB |

### Descripción

La abuela Carmen lleva a su nieto Matías a la famosa feria de chayotes de su pueblo. En esta feria, los chayotes se venden únicamente en paquetes de $k$ unidades cada uno. La abuela quiere comprar al menos $n$ chayotes para hacer una deliciosa sopa para toda la familia.

Como los chayotes solo se venden en paquetes completos de $k$ unidades, es posible que tenga que comprar más chayotes de los que necesita. Tu tarea es ayudar a la abuela Carmen a determinar cuál es el **menor número de chayotes** que puede comprar para tener al menos $n$ chayotes.

### Entrada

La primera línea contiene un entero $n$ ($1 \le n \le 10^9$) que representa la cantidad mínima de chayotes que necesita la abuela Carmen.

La segunda línea contiene un entero $k$ ($2 \le k \le 10^9$) que representa la cantidad de chayotes que vienen en cada paquete.

### Salida

Una línea con un único entero que indica el menor número de chayotes que puede comprar la abuela Carmen para tener al menos $n$ chayotes.

### Ejemplo

| Entrada | Salida | Descripción |
|---|---|---|
| `7`<br>`2` | `8` | La abuela necesita al menos 8 chayotes. Los paquetes vienen de 2 en 2. Para tener al menos 8 chayotes, debe comprar 4 paquetes ($4 \times 2 = 8$ chayotes). |
| `12`<br>`4` | `12` | La abuela necesita exactamente 12 chayotes. Los paquetes vienen de 4 en 4. Para tener al menos 12 chayotes, debe comprar exactamente 3 paquetes ($3 \times 4 = 12$ chayotes). |
| `15`<br>`6` | `18` | La abuela necesita al menos 15 chayotes. Los paquetes vienen de 6 en 6. Para tener al menos 15 chayotes, debe comprar 3 paquetes ($3 \times 6 = 18$ chayotes). |

### Límites

- $1 \le n \le 10^9$
- $2 \le k \le 10^9$

### Subtareas

- (30 puntos): $k = 2$.
- (40 puntos): $k \le 100$.
- (30 puntos): Sin restricciones adicionales.

*Fuente: II Eliminatoria OCI CR – 2025*

### Solución

```python
n = int(input())
k = int(input())

if n % k == 0:
    respuesta = n//k
else:
    respuesta = n//k + 1

print(respuesta * k)
```

---

## B. Colocando baldosas

| | | | |
|---|---|---|---|
| Puntos | 16.67 | Límite de memoria | 32 MiB |
| Límite de tiempo (caso) | 1s | Límite de tiempo (total) | 10s |
| Entrada/Salida | Consola | Tamaño límite de entrada (bytes) | 10 KiB |

### Descripción

José y Ana están remodelando su casa y quieren cubrir el piso de una habitación cuadrada con baldosas. El piso de la habitación tiene un lado que mide $\frac{a}{b}$ metros. Ellos quieren usar baldosas cuadradas, todas del mismo tamaño, con lado $\frac{p}{q}$ metros.

Tu tarea es ayudarles a calcular cuántas baldosas enteras pueden colocar en la habitación.

Las baldosas deben cumplir estas reglas:

- no se pueden superponer entre sí;
- cada baldosa debe quedar completamente dentro de la habitación (no se pueden cortar);
- las baldosas deben estar alineadas con las paredes de la habitación (lados paralelos).

Si no cabe ninguna baldosa, la respuesta es `0`.

### Entrada

- La primera línea contiene un entero positivo $a$ ($1 \le a \le 5 \cdot 10^4$).
- La segunda línea contiene un entero positivo $b$ ($1 \le b \le 5 \cdot 10^4$).
- La tercera línea contiene un entero positivo $p$ ($1 \le p \le 5 \cdot 10^4$).
- La cuarta línea contiene un entero positivo $q$ ($1 \le q \le 5 \cdot 10^4$).

El lado de la habitación mide $\frac{a}{b}$ y el lado de cada baldosa mide $\frac{p}{q}$.

### Salida

La salida debe consistir de una línea con un único entero: la cantidad máxima de baldosas enteras que José y Ana pueden colocar en el piso.

### Ejemplo

| Entrada | Salida | Descripción |
|---|---|---|
| `3`<br>`1`<br>`1`<br>`1` | `9` | El piso tiene lado 3 y cada baldosa tiene lado 1. José y Ana pueden colocar 9 baldosas sin superponerlas. |
| `1`<br>`2`<br>`2`<br>`3` | `0` | El piso tiene lado $\frac{1}{2}$ y cada baldosa tiene lado $\frac{2}{3}$. Como las baldosas son más grandes que el piso, no cabe ninguna. |

### Límites

- $1 \le a, p \le 5 \cdot 10^4$
- $1 \le b, q \le 5 \cdot 10^4$

### Subtareas

- (15 puntos): $1 \le a, p \le 1000$, $b = 1$ y $q = 1$
- (55 puntos): $1 \le a, p \le 1000$ y $1 \le b, q \le 1000$
- (30 puntos): Sin restricciones adicionales.

*Fuente: Examen de selección IOI CR – 2026*

### Solución

```python
a = int(input())
b = int(input())
p = int(input())
q = int(input())

# lado_habitacion = a/b
# lado_baldosa = p/q

resultado = (a * q) // (b * p)   # = a/b // p/q

print(resultado*resultado)
```

---

## C. Relojes planetarios

| | | | |
|---|---|---|---|
| Puntos | 16.86 | Límite de memoria | 32 MiB |
| Límite de tiempo (caso) | 1s | Límite de tiempo (total) | 30s |
| Entrada/Salida | Consola | Tamaño límite de entrada (bytes) | 10 KiB |

### Descripción

En el año 3025, Ana y Beto forman parte de la primera tripulación humana que visitará planetas con vida inteligente fuera del sistema solar.

Durante su exploración, descubrirán que cada planeta tiene su propio sistema de tiempo. En particular, el reloj de un planeta puede tener una **hora inicial** $p$ y una **hora final** $q$ ($0 \le p < q \le 2 \cdot 10^9$). Por ejemplo, en nuestro planeta Tierra, tenemos $p = 0$ y $q = 23$ (las horas van de 0 a 23).

Tu tarea es ayudar a Ana y Beto creando un programa que, dada la **hora actual** $h$ en un planeta ($p \le h \le q$) y una **cantidad de horas** $t$ que pasarán ($0 \le t \le 10^{12}$), calcule **cuál será la hora** en ese planeta después de que pasen $t$ horas.

### Entrada

La entrada consiste en 4 líneas:

- La primera línea contiene un número entero $p$, la hora inicial del reloj del planeta.
- La segunda línea contiene un número entero $q$, la hora final del reloj del planeta.
- La tercera línea contiene un número entero $h$, la hora actual en el planeta.
- La cuarta línea contiene un número entero $t$, la cantidad de horas a añadir.

### Salida

La salida debe consistir de una línea con un único número entero, la hora en el planeta después de que pasen $t$ horas.

### Ejemplo

| Entrada | Salida | Descripción |
|---|---|---|
| `0`<br>`23`<br>`9`<br>`18` | `3` | Al sumar 14 se llegan a las 23 horas, al sumar 15 se llegan a las 0 horas, al sumar 16 a la 1 hora, al sumar 17 a las 2 horas, y finalmente al sumar 18 se llegan a las 3 horas. |
| `10`<br>`11`<br>`10`<br>`101` | `11` | La hora inicial y final del reloj son 10 y 11, respectivamente. Partiendo de la hora 10, las siguientes horas son 11, 10, 11, 10, ..., por lo que al sumar 101 se llegan a las 11 horas. |
| `881788810`<br>`1791034590`<br>`1189518584`<br>`466084281624` | `1739960336` | |

### Límites

- $0 \le p < q \le 2 \cdot 10^9$
- $p \le h \le q$
- $0 \le t \le 10^{12}$

### Subtareas

- (35 puntos): $p = 0$, $q = 23$, $t \le 24$
- (35 puntos): $0 \le p < q \le 100$, $t \le 500$
- (30 puntos): Sin restricciones adicionales

*Fuente: Etapa Final OCI CR – 2025*

### Solución

```python
p = int(input())
q = int(input())
h = int(input())
t = int(input())

horas_totales = q - p + 1
resultado = p + ((h - p + t) % horas_totales)

print(resultado)
```

---

## D. Rango simple

| | | | |
|---|---|---|---|
| Puntos | 9.48 | Límite de memoria | 32 MiB |
| Límite de tiempo (caso) | 1s | Límite de tiempo (total) | 1m0s |
| Entrada/Salida | Consola | Tamaño límite de entrada (bytes) | 10 KiB |

### Descripción

Encontrar la cantidad de números que hay en un rango. Como entrada se tendrán N números y un rango. Lo único que debe hacer el programa es calcular la cantidad de números que hay dicho rango.

### Entrada

Leer primero N, donde `1<=N<=100`. El dato N indica la cantidad de números que se leerán desde el teclado. En las siguientes N líneas se encuentran los datos de entrada. Al finalizar se tienen dos números enteros A y B que indican el rango.

`0<=A<=B<=1000`

### Salida

Imprima la cantidad de números que existen en el rango desde A hasta B.

### Ejemplos

| Entrada | Salida |
|---|---|
| `10`<br>`1 2 3 4 5 6 7 8 9 10`<br>`0 2` | `2` |
| `5`<br>`3 25 100 23 28`<br>`20 30` | `3` |

*Fuente: LGGT*

### Solución

```python
n = int(input())
lista = list(map(int, input().split()))
a, b = map(int, input().split())

resultado = 0

for i in lista:
    if i in range(a, b + 1):
        resultado += 1

print(resultado)
```

---

## E. Ordenando las letras de la línea

| | | | |
|---|---|---|---|
| Puntos | 9.1 | Límite de memoria | 32 MiB |
| Límite de tiempo (caso) | 1s | Límite de tiempo (total) | 1m0s |
| Entrada/Salida | Consola | Tamaño límite de entrada (bytes) | 10 KiB |

### Descripción

Escribe un programa que lea una línea de texto y la imprima con sus letras ordenadas. Los caracteres no alfabéticos deben permanecer en su posición original.

### Entrada

Una línea de texto de a lo mucho 100 caracteres. Puedes suponer que la línea consiste de letras minúsculas, comas, puntos y espacios en blanco.

### Salida

La línea de texto con sus letras ordenadas

### Ejemplo

| Entrada | Salida |
|---|---|
| `hola gatito,perrito adios` | `aaad eghiii,looopr rsttt` |

*Fuente: UAM Azcapotzalco 2018*

### Solución

```python
texto = input()
resultado = ""

letras = []

for caracter in texto:
    if caracter.isalpha():
        letras.append(caracter)

letras.sort()

i = 0
for caracter in texto:
    if caracter.isalpha():
        resultado += letras[i]
        i += 1
    else:
        resultado += caracter

print(resultado)
```

---

## F. Los sonidos de la cochera

| | | | |
|---|---|---|---|
| Puntos | 17.3 | Límite de memoria | 256 MiB |
| Límite de tiempo (caso) | 1s | Límite de tiempo (total) | 45s |
| Entrada/Salida | Consola | Tamaño límite de entrada (bytes) | 100 KiB |

### Descripción

Ana y Roberto trabajan en ingeniería de sonido procesando las grabaciones de audio de las cocheras de un edificio residencial. Su tarea es limpiar las grabaciones eliminando un sonido distractor que aparece frecuentemente: la secuencia "UPE" que interfiere con la claridad del sonido.

Los sonidos están representados por una cadena de caracteres en mayúsculas sin espacios, donde cada letra del alfabeto inglés (A-Z, sin incluir la Ñ) puede aparecer en cualquier posición.

Para limpiar las grabaciones, necesitan desarrollar un programa que elimine **todas** las apariciones de la secuencia "UPE". El proceso debe ser equivalente al siguiente:

1. Buscar la **primera** aparición de "UPE" en la cadena
2. Eliminarla completamente
3. Repetir hasta que no queden más apariciones de "UPE"

Ambas personas se preguntan si se puede programar de una manera eficiente. Tu tarea es ayudarles a determinar cuál será la cadena final después de aplicar este proceso de limpieza.

### Entrada

La primera línea contiene un entero $n$ ($4 \le n \le 70000$) que representa la longitud de la cadena de audio procesada.

La segunda línea contiene una cadena $s$ de exactamente $n$ caracteres, compuesta únicamente por letras mayúsculas del alfabeto inglés. Se garantiza que la cadena contiene al menos una letra diferente de 'U', 'P' y 'E'.

### Salida

Una línea con la cadena resultante después de eliminar todas las apariciones de "UPE" siguiendo un proceso equivalente al descrito.

### Ejemplo

| Entrada | Salida | Descripción |
|---|---|---|
| `17`<br>`BUENASUPECOMOESTA` | `BUENASCOMOESTA` | BUENAS\*UPE\*COMOESTA → BUENASCOMOESTA |
| `23`<br>`VUUPEPEENDOUPEEMPANADAS` | `VENDOEMPANADAS` | VU\*UPE\*PEENDOUPEEMPAN… → V\*UPE\*ENDOUPEEMPAN… → VENDO\*UPE\*EMPANADAS → VENDOEMPANADAS |
| `9`<br>`XUPEYUEPE` | `XYUEPE` | X\*UPE\*YUEPE → XYUEPE |

### Límites

- $4 \le n \le 70000$
- $s$ contiene únicamente letras mayúsculas
- $s$ contiene al menos una letra diferente de 'U', 'P' y 'E'

### Subtareas

- (30 puntos): $n \le 20$ y se garantiza que "UPE" se debe eliminar a lo sumo una vez.
- (30 puntos): $n \le 1000$.
- (40 puntos): Sin restricciones adicionales.

*Fuente: II Eliminatoria OCI CR – 2025*

### Solución

```python
n = int(input())
texto = input()

recorrido = ""

for letra in texto:
    recorrido += letra

    if recorrido[-3:] == "UPE":
        recorrido = recorrido[:-3]

print(recorrido)
```

---

## G. Completando la secuencia

| | | | |
|---|---|---|---|
| Puntos | 17.38 | Límite de memoria | 256 MiB |
| Límite de tiempo (caso) | 1.2s | Límite de tiempo (total) | 1m0s |
| Entrada/Salida | Consola | Tamaño límite de entrada (bytes) | 10 KiB |

### Descripción

Gerardo y Elizabeth viven en un alegre pueblo cerca de la costa pacífica. Son estudiantes que frecuentan la biblioteca local para resolver acertijos que encuentran en distintos libros. Recientemente, encontraron uno con varias secuencias numéricas. Cada secuencia tiene $N$ elementos. Dado un número $K$ el objetivo es minimizar la cantidad de números a reemplazar en la secuencia de tal manera que aparezcan todos los números desde 1 hasta $K$ exactamente $N/K$ veces ($N$ es divisible por $K$).

Tu tarea es ayudar a Gerardo y Elizabeth a encontrar la mínima cantidad de números que deben ser reemplazados.

### Entrada

La primera línea contiene dos número enteros separados por espacio $N$ y $K$ ($1 \le K \le N \le 10^5$), la cantidad de elementos en la secuencia y $K$.

La segunda línea contiene la secuencia de números enteros separados por espacio $a_1, a_2, \ldots, a_N$, donde $0 \le a_i \le K + 1$ ($1 \le i \le N$).

### Salida

La línea salida deberá tener un único número entero que indica la mínima cantidad de números que deben ser reemplazados en la secuencia original.

### Ejemplo

| Entrada | Salida | Descripción |
|---|---|---|
| `2 2`<br>`2 3` | `1` | La mínima cantidad de cambios posibles es 1 para obtener una secuencia que tiene todos los números del 1 al 2. |
| `6 3`<br>`4 4 4 4 4 4` | `6` | Es necesario reemplazar 6 elementos en la secuencia para que los números del 1 al 3 aparezcan exactamente 2 veces. |
| `3 3`<br>`1 3 2` | `0` | La secuencia original cumple con lo esperado, por lo que no es necesario realizar cambios. |

### Límites

- $1 \le N \le 10^5$
- $1 \le K \le N$
- $N$ es divisible entre $K$
- $0 \le a_i \le K + 1$ ($1 \le i \le N$)

### Subproblemas

- (15 puntos): $N \le 100$.
- (85 puntos): Sin restricciones adicionales.

*Fuente: II Eliminatoria OCI CR – 2024*

### Solución

```python
n, k = map(int, input().split())
numeros = list(map(int, input().split()))
veces = n//k

cantidades_esperadas = dict()
for num in range(1, k + 1):
    cantidades_esperadas[num] = veces

cantidades_reales = dict()
for num in numeros:
    if num in cantidades_reales:
        cantidades_reales[num] += 1
    else:
        cantidades_reales[num] = 1

cambios = 0
for num, cantidad in cantidades_reales.items():
    if num not in cantidades_esperadas:
        cambios += cantidad
    elif cantidad > cantidades_esperadas[num]:
        cambios += cantidad - cantidades_esperadas[num]

print(cambios)
```

---

## H. Minimizando costos de mantenimiento

| | | | |
|---|---|---|---|
| Puntos | 18.67 | Límite de memoria | 256 MiB |
| Límite de tiempo (caso) | 2s | Límite de tiempo (total) | 36s |
| Entrada/Salida | Consola | Tamaño límite de entrada (bytes) | 10 KiB |

### Descripción

Camila es una ingeniera eléctrica que ha sido contratada para llevar a cabo trabajos de mantenimiento en el Teatro Nacional. Jonathan, por otro lado, es el encargado de las compras que se necesitan para dichos trabajos. Para ello, necesita comprar $M$ bombillas. Además, debido a los altos estándares de su trabajo, Camila insiste en que al menos $A$ de las bombillas deben ser individualmente de la máxima calidad posible que se encuentre en el mercado.

En el mercado, hay $N$ bombillas diferentes, cada una con su propio precio y calidad. Debido a las restricciones presupuestarias, Jonathan quiere encontrar la forma más económica de comprar la cantidad requerida de bombillas, cumpliendo con el requerimiento de calidad establecido por Camila.

Tu tarea es ayudar a Jonathan a determinar el costo mínimo para comprar la cantidad necesaria de bombillas que Camila necesita, asegurándose de que al menos $A$ de ellas sean individualmente de la máxima calidad posible.

### Entrada

La entrada consistirá en la siguiente información:

1. Un entero $N$ ($1 \le N \le 10^5$) que representa la cantidad de bombillas disponibles en el mercado.
2. $N$ líneas, cada una con dos enteros $P_i$ y $C_i$ ($1 \le P_i, C_i \le 10^9$; $1 \le i \le N$) que indican los precios y la calidad de cada bombilla en céntimos y en una escala del 1 al $10^9$ respectivamente. La suma total de todos los $P_i$ no superará $10^9$.
3. Un entero $M$ ($1 \le M \le N$) que representa la cantidad de bombillas que Camila necesita para su trabajo.
4. Un entero $A$ ($1 \le A \le M$) que representa la cantidad mínima de bombillas de la máxima calidad posible que se deben comprar obligatoriamente para el trabajo de Camila.

### Salida

La salida debe ser un entero que represente el costo mínimo en céntimos para comprar las cantidades $M$ de bombillas, asegurándose de que al menos $A$ de ellas sean individualmente de la máxima calidad posible.

### Ejemplo

| Entrada | Salida | Descripción |
|---|---|---|
| `5`<br>`10 10`<br>`20 20`<br>`30 30`<br>`40 40`<br>`50 50`<br>`3`<br>`2` | `100` | Para asegurar que se compran al menos 2 bombillas de la máxima calidad posible, Jonathan debería comprar las bombillas con calidades (y precios) 50, 40. La tercera bombilla debería ser la más barata posible que aún no se haya comprado, que es 10. El costo total sería $50 + 40 + 10 = 100$ céntimos. |
| `5`<br>`200 5`<br>`100 10`<br>`250 3`<br>`300 2`<br>`150 8`<br>`4`<br>`3` | `700` | Aquí, se deben comprar 4 bombillas y al menos 3 de ellas deben tener las calidades más altas posibles. Así, se comprarían las bombillas con calidades 10, 8, 5 y 3 por un costo total de $100+150+200+250 = 700$ céntimos. |
| `5`<br>`1000 90`<br>`900 100`<br>`700 80`<br>`800 85`<br>`850 90`<br>`3`<br>`2` | `2450` | Para asegurar que se compran al menos 2 bombillas de la máxima calidad posible, Jonathan selecciona la bombilla de calidad 100 (900 céntimos) y una bombilla de calidad 90 (850 céntimos que es más barata que la otra opción de calidad 90). Adicionalmente, para minimizar el costo, elige la bombilla más barata restante que es de calidad 80 (700 céntimos). El costo total es $900+850+700 = 2450$ céntimos. |

### Límites

- $1 \le N \le 10^5$
- $1 \le M \le N$
- $1 \le A \le M$
- $1 \le P_i, C_i \le 10^9$ para $1 \le i \le N$
- Los precios y las calidades son enteros positivos.

### Subtareas

- (10 puntos): $P_i = C_i$ para $1 \le i \le N$
- (25 puntos): Si $i \ne j$ entonces $C_i \ne C_j$ para $1 \le i, j \le N$.
- (65 puntos): Sin restricciones adicionales

*Fuente: II Eliminatoria OCI CR – 2023*

### Solución

```python
n = int(input())
posibles = []
for _ in range(n):
    precio_calidad = tuple(map(int, input().split()))
    posibles.append(precio_calidad)
m = int(input())
a = int(input())

total = 0

posibles.sort(key=lambda x: x[0])
posibles.sort(key=lambda x: x[1], reverse=True)

for i in range(a):
    total += posibles[i][0]

posibles = posibles[a:]

posibles.sort(key=lambda x: x[0])
for i in range(m-a):
    total += posibles[i][0]

print(total)
```

---

## I. El recorrido del colibrí

| | | | |
|---|---|---|---|
| Puntos | 20.18 | Límite de memoria | 256 MiB |
| Límite de tiempo (caso) | 1.5s | Límite de tiempo (total) | 1m0s |
| Entrada/Salida | Consola | Tamaño límite de entrada (bytes) | 10 KiB |

### Descripción

Camila y Jonathan, dos estudiantes de etología, viajan al corazón de un frondoso y vibrante bosque tropical, maravillados por la diversidad de especies. Mientras estaban en medio de su investigación, observaron a un colibrí con brillantes colores, alimentándose de néctar de diferentes flores. Este pequeño ave es conocido por su agilidad y rapidez, pero observaron una peculiaridad en su comportamiento que atrajo la atención de nuestros investigadores: cada hora se alimenta de un solo tipo de flor y no se alimenta del mismo tipo de flor dos horas consecutivas.

En este ecosistema, hay tres tipos de flores, distinguidos por su forma y color: tipo A, tipo B y tipo C. Cada vez que el colibrí visita a un grupo de flores del mismo tipo, obtiene una cierta cantidad de néctar.

Tu tarea es ayudar a Camila y Jonathan a determinar cuánto es el máximo néctar que puede recolectar el colibrí en las siguientes $N$ horas.

### Entrada

- Una línea con un entero $N$ ($1 \le N \le 10^5$), representando la cantidad de horas.
- $N$ líneas, cada una con tres enteros separados por espacio $a_i, b_i, c_i$ ($1 \le a_i, b_i, c_i \le 1000$) que representan la cantidad de néctar que el colibrí puede obtener de las flores tipo A, tipo B y tipo C respectivamente, en la hora $i$ ($1 \le i \le N$).

### Salida

- Un único entero que indica la cantidad máxima total de néctar que el colibrí puede obtener en las siguientes $N$ horas, siguiendo las restricciones mencionadas.

### Ejemplo

| Entrada | Salida | Descripción |
|---|---|---|
| `3`<br>`5 2 1`<br>`6 9 3`<br>`3 2 1` | `17` | El colibrí puede elegir el tipo A en la primera hora (5 unidades), el tipo B en el segundo turno (9 unidades) y el tipo A en el tercer turno (3 unidades). La cantidad total de néctar es 17 unidades y es el recorrido con la mayor cantidad de néctar recolectado posible. |
| `2`<br>`10 40 30`<br>`40 90 20` | `120` | El colibrí pueder optar por las flores del tipo C en la primer hora (30 unidades), el tipo B en la segunda hora (90 unidades) para un total de 120 unidades y es el recorrido con la mayor cantidad de néctar recolectado posible. |

### Límites

- $1 \le N \le 10^5$.
- $1 \le a_i, b_i, c_i \le 1000$.

### Subtareas

- (25 puntos): $N \le 10$.
- (75 puntos): Sin restricciones adicionales.

*Fuente: Etapa Final OCI CR – 2023*

### Solución

```python
n = int(input())
tabla = [[0, 0, 0] for _ in range(n)]

for i in range(n):
    a, b, c = map(int, input().split())

    if i == 0:
        tabla[0][0] = a
        tabla[0][1] = b
        tabla[0][2] = c

    else:
        mejor_anterior_A = max(tabla[i-1][1], tabla[i-1][2])   # B o C
        tabla[i][0] = a + mejor_anterior_A

        mejor_anterior_B = max(tabla[i-1][0], tabla[i-1][2])   # A o C
        tabla[i][1] = b + mejor_anterior_B

        mejor_anterior_C = max(tabla[i-1][0], tabla[i-1][1])   # A o B
        tabla[i][2] = c + mejor_anterior_C

respuesta = max(tabla[n-1][0], tabla[n-1][1], tabla[n-1][2])

print(respuesta)
```

---

## J. El camino hacia el árbol

| | | | |
|---|---|---|---|
| Puntos | 20.8 | Límite de memoria | 256 MiB |
| Límite de tiempo (caso) | 1.5s | Límite de tiempo (total) | 45s |
| Entrada/Salida | Consola | Tamaño límite de entrada (bytes) | 10 KiB |

### Descripción

Las abejas del bosque han pasado el día visitando flores para recolectar néctar y polen. Al caer la tarde, es momento de regresar a su hogar, un majestuoso árbol Enterolobium cyclocarpum. Sin embargo, el bosque es vasto y las abejas se han dispersado por todos lados, creando una red compleja de senderos entre las flores y otros puntos del bosque. Cada uno de estos puntos tiene como máximo tres senderos que se conectan a otros puntos. Cada sendero conecta exactamente 2 puntos.

Tu tarea es ayudar a las abejas a encontrar el primer paso en el camino que utilice una cantidad mínima de senderos en el regreso a su hogar desde cualquier punto del bosque.

Para cada punto en el bosque, debes determinar cuál de los senderos disponibles es parte del recorrido óptimo de regreso al Enterolobium cyclocarpum. Está garantizado que desde cualquier punto las abejas pueden regresar a su hogar.

### Entrada

- La primera entrada contiene un único número entero $N$ ($2 \le N \le 10^5$), la cantidad de puntos en el bosque.
- Las siguientes $N$ líneas inician con un número $k_i$ ($1 \le k_i \le 3$) que representa la cantidad de senderos que salen desde el $i$-ésimo punto ($1 \le i \le N$). Luego de un espacio, se encuentran $k_i$ números separados por espacio $p_{i,1}, \ldots, p_{i,k_i}$, donde el número $p_{i,j}$ ($1 \le j \le k_i$) indica que el sendero número $j$ que sale del punto $i$ conecta con el punto $p_{i,j}$.
- Finalmente, existe una línea con un único número entero $A$, que indica que el punto número $A$ es donde se encuentra el árbol Enterolobium cyclocarpum.

### Salida

La salida deberá consistir en una línea con una hilera con $N$ dígitos. El $i$-ésimo ($1 \le i \le N$) dígito de la hilera debe ser uno de los dígitos 0, 1, 2 ó 3, donde:

- **0** representa que ningún sendero disponible para el punto $i$ acerca más al árbol de destino (es decir, $i = A$).
- **1** representa que el primer sendero descrito en la entrada para el punto $i$ es parte de un camino óptimo hacia el punto $A$.
- **2** representa que el segundo sendero descrito en la entrada para el punto $i$ es parte de un camino óptimo hacia el punto $A$.
- **3** representa que el tercer sendero descrito en la entrada para el punto $i$ es parte de un camino óptimo hacia el punto $A$.

**Nota:** Es posible que haya más de una respuesta válida, en cuyo caso se permite usar cualquier respuesta correcta.

### Ejemplo

| Entrada | Salida | Descripción |
|---|---|---|
| `4`<br>`1 2`<br>`3 1 3 4`<br>`1 2`<br>`1 2`<br>`2` | `1011` | En este ejemplo, es claro que para todos los puntos donde no está el árbol (posición 2), la única y mejor opción es tomar el primer sendero descrito en su entrada. Este un ejemplo de configuración "estrella". |
| `5`<br>`1 2`<br>`2 1 3`<br>`2 2 4`<br>`2 3 5`<br>`1 4`<br>`4` | `12201` | Los puntos 2, 3 son los únicos puntos donde no está el árbol y que además tienen 2 opciones. No tomar el segundo sendero en cada uno de esos casos llevaría a un camino más largo. Este es un ejemplo de configuración "lineal". |
| `5`<br>`2 2 3`<br>`2 5 1`<br>`2 1 4`<br>`2 3 5`<br>`2 4 2`<br>`1` | `02112` | Los puntos están conectados de la forma 1-3-4-5-2-1 (para efectos ilustrativos). Este es un ejemplo de configuración de "anillo". |
| `5`<br>`3 2 3 4`<br>`2 1 3`<br>`2 2 1`<br>`2 1 5`<br>`1 4`<br>`5` | `31220` | Un último ejemplo que no se ajusta a ninguna de las configuraciones anteriores de ejemplo. |

### Límites

- $2 \le N \le 10^5$
- $1 \le k_i \le 3$ ($1 \le i \le N$)
- $1 \le A \le N$
- Ningún sendero conecta a un punto con sí mismo.
- Para todo par de puntos $P$ y $Q$ ($1 \le P, Q \le N$), existen exactamente 0 ó 1 senderos que los conectan. Además si $Q$ aparece en la descripción de los senderos de $P$, entonces $P$ también aparece en la descripción de los senderos de $Q$.
- Siempre existe un camino válido desde cualquier punto al punto $A$.

### Subproblemas

- (8 puntos) El bosque tiene una configuración "estrella". Es decir, existe un punto tal que todos los senderos lo incluyen (ver Ejemplo).
- (10 puntos) El bosque tiene una configuración "lineal", lo que significa que existen exactamente dos puntos con un solo sendero asociado a cada uno. Además, todos los demás puntos tienen exactamente dos senderos asociados. En total, hay exactamente $N - 1$ senderos en el bosque (ver Ejemplo).
- (12 puntos) El bosque tiene una configuración de "anillo". Es decir, todos los puntos tienen exactamente 2 senderos asociados a ellos y existen exactamente $N$ senderos (ver Ejemplo).
- (20 puntos) $N \le 100$.
- (50 puntos) Sin restricciones adicionales.

### Solución

```python
from collections import deque
def bfs(grafo, arbol):
    visitados = [False] * len(grafo)
    cola = deque()
    respuesta = [0] * len(grafo)
    cola.append(arbol)
    
    visitados[arbol] = True
    while cola:
        nodo = cola.popleft()
        for vecino in grafo[nodo]:
            if not visitados[vecino]:
                visitados[vecino] = True
                cola.append(vecino)
                for i in range(len(grafo[vecino])):
                    if grafo[vecino][i] == nodo:
                        respuesta[vecino] = i + 1
                        break
    return respuesta
n = int(input())
grafo = [[] for _ in range(n)]
for i in range(n):
    datos = list(map(int, input().split()))
    for vecino in datos[1:]:
        # 1..n a índices 0..n-1
        grafo[i].append(vecino - 1)
arbol = int(input()) - 1
respuesta = bfs(grafo, arbol)
resultado = ""
for valor in respuesta:
    resultado += str(valor)
print(resultado)
```