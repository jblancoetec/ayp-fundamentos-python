# Guía de Estudio: Fundamentos de Python

Este apunte te ayudará a resolver el práctico de Fundamentos de Python siguiendo la metodología TDD (Test-Driven Development).

## Metodología TDD

1. **Lee el test** en `tests/`. Cada test tiene un docstring que describe el comportamiento esperado.
2. **Ejecuta los tests** y verifica que fallen.
3. **Implementa** la función en `ejercicios/` hasta que los tests pasen.
4. **No modifiques los tests**. Si un test falla, tu código es el que debe corregirse.

## Ejecución de Tests

```bash
# Todos los tests
pytest

# Un módulo específico
pytest tests/test_variables.py
pytest tests/test_condicionales.py
pytest tests/test_funciones.py
```

---

## Módulo 1: Variables y Tipos de Datos Primitivos

### Tipos básicos en Python

| Tipo | Ejemplo | Descripción |
|------|---------|-------------|
| `int` | `42`, `-7`, `0` | Números enteros |
| `float` | `3.14`, `-0.5`, `2.0` | Números decimales |
| `str` | `"Hola"`, `'Mundo'` | Texto (cadenas de caracteres) |
| `bool` | `True`, `False` | Valores booleanos |

### Verificar tipos con `isinstance()`

Para verificar el tipo de una variable, se usa `isinstance(valor, Tipo)`:

```python
isinstance(42, int)      # True
isinstance(3.14, float)  # True
isinstance("hola", str)  # True
isinstance(True, bool)   # True
```

### Conversiones entre tipos

```python
int("10")      # "10" -> 10
int(3.7)       # 3.7 -> 3 (trunca, no redondea)
float("2.5")   # "2.5" -> 2.5
float(7)       # 7 -> 7.0
str(100)       # 100 -> "100"
str(True)      # True -> "True"
```

### Operadores aritméticos

```python
a + b    # Suma
a - b    # Resta
a * b    # Multiplicación
a / b    # División (devuelve float)
a // b   # División entera (trunca decimales)
a % b    # Resto de la división entera
a >= b   # Mayor o igual (devuelve bool)
a == b   # Igual (devuelve bool)
```

### Ejercicios del módulo

#### 1. `crear_variables_primitivas()`
Crea variables de tipos `int`, `float`, `str` y `bool` a nivel del módulo.

```python
mi_int = 10
mi_float = 3.14
mi_str = "hola"
mi_bool = True
```

#### 2. `es_entero(valor)` → `bool`
Retorna `True` solo si el valor es de tipo `int`.

```python
def es_entero(valor):
    return isinstance(valor, int)
```

#### 3. `es_float(valor)` → `bool`
Retorna `True` solo si el valor es de tipo `float`.

```python
def es_float(valor):
    return isinstance(valor, float)
```

#### 4. `a_entero(valor)` → `int`
Convierte el valor a entero. Puede recibir string o float.

```python
def a_entero(valor):
    return int(valor)
```

#### 5. `a_float(valor)` → `float`
Convierte el valor a float. Puede recibir string o int.

```python
def a_float(valor):
    return float(valor)
```

#### 6. `a_string(valor)` → `str`
Convierte cualquier valor a string.

```python
def a_string(valor):
    return str(valor)
```

#### 7. `es_entero_par(n)` → `bool`
Un número es par si el resto de dividirlo por 2 es 0.

```python
def es_entero_par(n):
    return n % 2 == 0
```

#### 8. `sumar_dos_numeros(a, b)` → `float`
Retorna la suma de dos números.

```python
def sumar_dos_numeros(a, b):
    return a + b
```

#### 9. `division_entera(a, b)` → `int`
Usa el operador `//` para división entera.

```python
def division_entera(a, b):
    return a // b
```

#### 10. `resto_division(a, b)` → `int`
Usa el operador `%` para obtener el resto.

```python
def resto_division(a, b):
    return a % b
```

#### 11. `comparar_mayores_o_iguales(a, b)` → `bool`
Usa el operador `>=`.

```python
def comparar_mayores_o_iguales(a, b):
    return a >= b
```

#### 12. `concatenar_nombre_y_apellido(nombre, apellido)` → `str`
Une dos strings con un espacio en el medio.

```python
def concatenar_nombre_y_apellido(nombre, apellido):
    return nombre + " " + apellido
```

#### 13. `plantilla_presentacion(nombre, edad, ciudad)` → `str`
Crea una frase usando f-strings o concatenación.

```python
def plantilla_presentacion(nombre, edad, ciudad):
    return f"Hola, soy {nombre}, tengo {edad} años y vivo en {ciudad}."
```

#### 14. `calcular_imc(peso_kg, altura_m)` → `float`
El IMC se calcula como: `peso / (altura ^ 2)`

```python
def calcular_imc(peso_kg, altura_m):
    return peso_kg / (altura_m ** 2)
```

#### 15. `clasificar_imc(imc)` → `str`
Clasifica según los rangos del IMC usando `if/elif/else`.

```python
def clasificar_imc(imc):
    if imc < 18.5:
        return "Bajo peso"
    elif imc < 25:
        return "Normal"
    elif imc < 30:
        return "Sobrepeso"
    else:
        return "Obesidad"
```

---

## Módulo 2: Estructuras de Control - Condicionales

### Sintaxis de `if/elif/else`

```python
if condición1:
    # código si condición1 es True
elif condición2:
    # código si condición2 es True
else:
    # código si ninguna condición es True
```

### Operadores de comparación

```python
a == b    # Igual
a != b    # Distinto
a > b     # Mayor
a < b     # Menor
a >= b    # Mayor o igual
a <= b    # Menor o igual
```

### Operadores lógicos

```python
and  # Y lógico (ambas condiciones deben ser True)
or   # O lógico (al menos una debe ser True)
not  # Negación
```

### Ejercicios del módulo

#### 1. `es_par_o_impar(n)` → `str`
Retorna `"par"` si es divisible por 2, `"impar"` en caso contrario.

```python
def es_par_o_impar(n):
    if n % 2 == 0:
        return "par"
    else:
        return "impar"
```

#### 2. `clasificar_nota(nota)` → `str`
Clasifica según los rangos:
- `nota >= 7`: "Promocionado"
- `4 <= nota < 7`: "Aprobado"
- `nota < 4`: "Recupatorio"

```python
def clasificar_nota(nota):
    if nota >= 7:
        return "Promocionado"
    elif nota >= 4:
        return "Aprobado"
    else:
        return "Recupatorio"
```

#### 3. `maximo_de_tres(a, b, c)` → valor
Retorna el mayor de tres valores.

```python
def maximo_de_tres(a, b, c):
    if a >= b and a >= c:
        return a
    elif b >= a and b >= c:
        return b
    else:
        return c
```

#### 4. `minimo_de_tres(a, b, c)` → valor
Retorna el menor de tres valores.

```python
def minimo_de_tres(a, b, c):
    if a <= b and a <= c:
        return a
    elif b <= a and b <= c:
        return b
    else:
        return c
```

#### 5. `es_bisiesto(year)` → `bool`
Un año es bisiesto si:
- Es divisible por 4 **Y** no es divisible por 100
- **O** es divisible por 400

```python
def es_bisiesto(year):
    if year % 400 == 0:
        return True
    elif year % 100 == 0:
        return False
    elif year % 4 == 0:
        return True
    else:
        return False
```

#### 6. `calcular_precio_final(precio_base, categoria)` → `float`
Aplica descuentos según categoría:
- "general": sin descuento
- "estudiante": 20% off → `precio * 0.8`
- "jubilado": 30% off → `precio * 0.7`

```python
def calcular_precio_final(precio_base, categoria):
    if categoria == "estudiante":
        return precio_base * 0.8
    elif categoria == "jubilado":
        return precio_base * 0.7
    else:
        return precio_base
```

#### 7. `calculadora_simple(a, operacion, b)` → `float` o `str`
Realiza operaciones básicas. Maneja división por cero.

```python
def calculadora_simple(a, operacion, b):
    if operacion == "+":
        return a + b
    elif operacion == "-":
        return a - b
    elif operacion == "*":
        return a * b
    elif operacion == "/":
        if b == 0:
            return "Error: división por cero"
        return a / b
```

#### 8. `fizzbuzz(n)` → `str`
- Múltiplo de 3 y 5: "FizzBuzz"
- Múltiplo de 3: "Fizz"
- Múltiplo de 5: "Buzz"
- Otros: el número como string

```python
def fizzbuzz(n):
    if n % 3 == 0 and n % 5 == 0:
        return "FizzBuzz"
    elif n % 3 == 0:
        return "Fizz"
    elif n % 5 == 0:
        return "Buzz"
    else:
        return str(n)
```

#### 9. `describir_numero(n)` → `str`
Describe si es positivo/negativo y par/impar.

```python
def describir_numero(n):
    if n == 0:
        return "Cero"
    elif n > 0:
        if n % 2 == 0:
            return "Positivo y par"
        else:
            return "Positivo e impar"
    else:
        if n % 2 == 0:
            return "Negativo y par"
        else:
            return "Negativo e impar"
```

#### 10. `acceso_usuario(edad, tiene_identificacion)` → `bool`
Acceso granted si `edad >= 18` **Y** `tiene_identificacion == True`.

```python
def acceso_usuario(edad, tiene_identificacion):
    return edad >= 18 and tiene_identificacion == True
```

#### 11. `dia_de_la_semana(numero)` → `str`
Convierte 1-7 a nombre del día. Invalid other values.

```python
def dia_de_la_semana(numero):
    if numero == 1:
        return "Lunes"
    elif numero == 2:
        return "Martes"
    elif numero == 3:
        return "Miércoles"
    elif numero == 4:
        return "Jueves"
    elif numero == 5:
        return "Viernes"
    elif numero == 6:
        return "Sábado"
    elif numero == 7:
        return "Domingo"
    else:
        return "Día inválido"
```

---

## Módulo 3: Funciones

### Estructura de una función

```python
def nombre_funcion(argumento1, argumento2):
    """Docstring: descripción de qué hace"""
    # código
    return resultado  # valor que devuelve
```

### Argumentos y valores por defecto

```python
def saludar(nombre="mundo"):
    return f"Hola, {nombre}!"

saludar()          # "Hola, mundo!"
saludar("Ana")     # "Hola, Ana!"
```

### `*args` - Argumentos variables

Permite pasar cualquier cantidad de argumentos:

```python
def sumar_todos(*args):
    total = 0
    for num in args:
        total += num
    return total

sumar_todos(1, 2, 3)    # 6
sumar_todos(10, 5)      # 15
sumar_todos()           # 0
```

### `**kwargs` - Argumentos por nombre variables

Permite pasar argumentos con nombre arbitrarios:

```python
def construir_usuario(nombre, **kwargs):
    resultado = {"nombre": nombre}
    for clave, valor in kwargs.items():
        resultado[clave] = valor
    return resultado

construir_usuario("Ana", edad=30, ciudad="Córdoba")
# {"nombre": "Ana", "edad": 30, "ciudad": "Córdoba"}
```

### `print()` vs `return`

- `print()`: muestra texto en pantalla, no devuelve nada
- `return`: devuelve un valor para usar en el código

```python
def saludar():              # No retorna, solo imprime
    print("¡Hola!")

def sumar(a, b):            # Retorna el resultado
    return a + b
```

### Ejercicios del módulo

#### 1. `saludar()` → None (imprime)
Imprime `"¡Hola!"`.

```python
def saludar():
    print("¡Hola!")
```

#### 2. `saludar_persona(nombre)` → None (imprime)
Imprime `"¡Hola, {nombre}!"`.

```python
def saludar_persona(nombre):
    print(f"¡Hola, {nombre}!")
```

#### 3. `sumar(a, b)` → `float`

```python
def sumar(a, b):
    return a + b
```

#### 4. `restar(a, b)` → `float`

```python
def restar(a, b):
    return a - b
```

#### 5. `multiplicar(a, b)` → `float`

```python
def multiplicar(a, b):
    return a * b
```

#### 6. `dividir(a, b)` → `float` o `None`
Retorna `None` si `b == 0`.

```python
def dividir(a, b):
    if b == 0:
        return None
    return a / b
```

#### 7. `es_positivo(n)` → `bool`

```python
def es_positivo(n):
    return n > 0
```

#### 8. `es_multiplo_de_tres(n)` → `bool`
Usa `n % 3 == 0`. Recordá que 0 es múltiplo de cualquier número.

```python
def es_multiplo_de_tres(n):
    return n % 3 == 0
```

#### 9. `obtener_mensaje_estado(es_correcto, mensaje_base)` → `str`
- `es_correcto=True` → `"[OK] {mensaje_base}"`
- `es_correcto=False` → `"[ERROR] {mensaje_base}"`

```python
def obtener_mensaje_estado(es_correcto, mensaje_base):
    if es_correcto:
        return f"[OK] {mensaje_base}"
    else:
        return f"[ERROR] {mensaje_base}"
```

#### 10. `sumar_hasta_limite(inicio, limite)` → `int`
Suma todos los enteros desde `inicio` hasta `limite` inclusive.

```python
def sumar_hasta_limite(inicio, limite):
    total = 0
    for i in range(inicio, limite + 1):
        total += i
    return total
```

#### 11. `aplicar_descuento(precio, descuento=10)` → `float`
Aplica un descuento porcentual. `descuento=10` significa 10% off.

```python
def aplicar_descuento(precio, descuento=10):
    return precio * (1 - descuento / 100)
```

#### 12. `repetir_texto(texto, veces=2)` → `str`
Repite el texto `veces` veces, separado por espacios.

```python
def repetir_texto(texto, veces=2):
    return " ".join([texto] * veces)
```

#### 13. `sumar_todos(*args)` → `float`
Suma todos los argumentos. Si no hay argumentos, retorna 0.

```python
def sumar_todos(*args):
    total = 0
    for num in args:
        total += num
    return total
```

#### 14. `promediar(*args)` → `float` o `None`
Calcula el promedio. Si no hay argumentos, retorna `None`.

```python
def promediar(*args):
    if len(args) == 0:
        return None
    return sum(args) / len(args)
```

#### 15. `construir_usuario(nombre, **kwargs)` → `dict`
Construye un diccionario con el nombre y todos los kwargs.

```python
def construir_usuario(nombre, **kwargs):
    resultado = {"nombre": nombre}
    for clave, valor in kwargs.items():
        resultado[clave] = valor
    return resultado
```

#### 16. `validar_edad_y_rol(edad, rol)` → `tuple`
Retorna una tupla `(bool, str)`:
- `(True, "Válido")` si `edad >= 18` y `rol` es "admin", "usuario" o "invitado"
- `(False, "Edad mínima: 18")` si `edad < 18`
- `(False, "Rol inválido")` si `rol` no es válido

```python
def validar_edad_y_rol(edad, rol):
    roles_validos = ["admin", "usuario", "invitado"]
    if edad < 18:
        return (False, "Edad mínima: 18")
    elif rol not in roles_validos:
        return (False, "Rol inválido")
    else:
        return (True, "Válido")
```

---

## Tips para resolver el práctico

1. **Ejecutá los tests primero** para ver qué falla
2. **Leé el docstring de cada test** - describe exactamente qué se espera
3. **Implementá una función a la vez** y ejecutá los tests
4. **Usá las conversiones y operadores** aprendidos en cada módulo
5. **Para `*args`**: recorré los argumentos con un bucle `for`
6. **Para `**kwargs`**: usá `.items()` para iterar sobre clave-valor
7. **Para `print()` vs `return`**: recordá que `print()` no retorna nada

## Cheatsheet rápida

```python
# Verificar tipo
isinstance(x, int)

# Convertir tipos
int(x), float(x), str(x)

# Operadores
a + b, a - b, a * b, a / b
a // b, a % b
a >= b, a == b

# Condicionales
if/elif/else

# Funciones
def nombre(arg):
    return valor

# Args variables
def f(*args): ...
def f(**kwargs): ...

# F-string
f"Hola, {nombre}!"
```