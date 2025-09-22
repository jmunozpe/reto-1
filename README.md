# reto-1

Este repositorio contiene **5 programas**, uno por cada punto del reto.

# 1.

Crear una función que realice operaciones básicas (suma, resta, multiplicación, división) entre dos números, según la elección del usuario, la forma de entrada de la función será los dos operandos y el caracter usado para la operación. entrada: (1,2,"+"), salida (3).

# codigo
```
def operar(a, b, op):
    if op not in ["+", "-", "*", "/"]:
        raise ValueError("Operación incorrecta. Usa +, -, * o /.")
    if op == "+":
        resultado = a + b  # suma
    elif op == "-":
        resultado = a - b  # resta
    elif op == "*":
        resultado = a * b  # multiplicación
    else:
        if b == 0:
            raise ValueError("No se puede dividir por cero.")
        resultado = a / b  # división

if __name__ == "__main__":
    print("=== Operaciones básicas ===")
     a = float(input("Ingresa el primer número: "))
    b = float(input("Ingresa el segundo número: "))
    op = input("Ingresa la operación (+, -, *, /): ")
    try:
        print("Resultado:", operar(a, b, op))
    except ValueError as e:
        print("Error:", e)
```
En este punto nos piden una función donde el usuario introduce sus propios datos:
num_1, num_2 y operador. Lo primero que hice fue definir la función operar(a, b, op)
con esas 3 variables. Después puse condicionales (if y else) que sirven para comparar
y saber qué operación se quiere realizar. Si el usuario escribe un carácter diferente a los pedidos
(+, -, *, /), muestro un error diciendo que el operador no es válido. En el caso de la división,
agregué una verificación para no dividir por cero. Finalmente, coloqué input() para pedir los tres
datos y un print() para mostrar el resultado al final.

# 2.
Realice una función que permita validar si una palabra es un palíndromo. Condición: No se vale hacer slicing para invertir la palabra y verificar que sea igual a la original.
```
def es_palindromo(palabra):
   
    s = palabra.lower()

    i = 0
   
    j = len(s) - 1

    while i < j:
        
        if s[i] != s[j]:
            return False
       
        i += 1
        j -= 1

    
    return True

if __name__ == "__main__":
    print("=== ¿Es palíndromo? ===")
    palabra = input("Escribe una palabra: ")
    if es_palindromo(palabra):
        print("Sí, es palíndromo.")
    else:
        print("No es palíndromo.")
```
piden revisar si una palabra es palíndromo sin usar slicing ([::-1]). Para eso pensé en dos índices
o “punteros”: uno que empieza a la izquierda y otro que empieza a la derecha. Convertí la palabra a minúscula,
y con un while voy comparando las letras de ambos lados. Si encuentro una diferente, devuelvo False. Si
llegan al centro sin encontrar diferencias, devuelvo True. 

# 3.

Escribir una función que reciba una lista de números y devuelva solo aquellos que son primos. La función debe recibir una lista de enteros y retornar solo aquellos que sean primos.

```
def es_primo(n):
   
    num = abs(n)

    if num < 2:
        return False

    for divisor in range(2, num):
        if num % divisor == 0:
            return False

    return True


def filtrar_primos(lista_numeros):
  
    resultado = []
    for numero in lista_numeros:
        if es_primo(numero):
            resultado.append(numero)
    return resultado


if __name__ == "__main__":
    print("=== Filtrar números primos (positivos y negativos) ===")
    texto = input("Escribe números enteros separados por espacio: ")
    partes = texto.split()
    numeros = []
    for p in partes:
        numeros.append(int(p))

    print("Primos encontrados:", filtrar_primos(numeros))
```
Aquí quería que también contaran los negativos. Matemáticamente los primos se definen en los números
naturales, pero para este ejercicio decidí usar el valor absoluto. Así, por ejemplo, -3 se comporta como 3.
Escribí una función es_primo(n) simple que prueba divisores desde 2 hasta n-1. Si alguno divide exacto,
entonces no es primo. Con esa función recorro la lista original y construyo otra lista nueva con los que sí
resultan primos, manteniendo el orden original. 

# 4.

Escribir una función que reciba una lista de números enteros y retorne la mayor suma entre dos elementos consecutivos.

```
def mayor_suma_consecutivos(lista_numeros):
 
    if len(lista_numeros) < 2:
        raise ValueError("Se necesitan al menos 2 números.")

    mejor = lista_numeros[0] + lista_numeros[1]

    for i in range(1, len(lista_numeros) - 1):
        suma = lista_numeros[i] + lista_numeros[i + 1]
       
        if suma > mejor:
            mejor = suma

    return mejor


if __name__ == "__main__":
    print("=== Mayor suma de consecutivos (con negativos también) ===")
    texto = input("Escribe números enteros separados por espacio: ")
    partes = texto.split()
    numeros = []
    for p in partes:
        numeros.append(int(p))

    print("Mayor suma entre dos consecutivos:", mayor_suma_consecutivos(numeros))

```
La idea fue revisar todas las parejas consecutivas: a[i] + a[i+1]. Empecé calculando la suma de los dos
primeros como “mejor” inicial y luego, con un for, fui comparando el resto de pares. Si encuentro una suma
mayor, la guardo como la nueva mejor. Este enfoque funciona tanto con positivos como con negativos;
si todos son negativos, igual devuelve la suma que resulte menos negativa (o sea, la más grande).

# 5.

Escribir una función que reciba una lista de string y retorne unicamente aquellos elementos que tengan los mismos caracteres. e.g. entrada: ["amor", "roma", "perro"], salida ["amor", "roma"]
```
def filtrar_anagramas(texto):
   
    palabras = texto.split()

    conteo = {}

    for w in palabras:
     
        clave = "".join(sorted(w.lower()))
        if clave in conteo:
            conteo[clave] = conteo[clave] + 1
        else:
            conteo[clave] = 1

    resultado = []
    for w in palabras:
        clave = "".join(sorted(w.lower()))
        if conteo[clave] >= 2:
            resultado.append(w)

    return resultado

if __name__ == "__main__":
    print("=== Filtrar anagramas ===")
   
    texto = input("Escribe varias palabras separadas por espacio: ")

    # Llamo a la función y muestro lo que devolvió
    anagramas = filtrar_anagramas(texto)
    print("Palabras con anagramas:", anagramas)

```
Parto el string con split() para tener una lista de palabras. A cada palabra le creo una clave canónica ordenando sus
letras en minúscula. Si dos o más palabras tienen la misma clave, entonces son anagramas. Primero cuento
cuántas veces aparece cada clave en un diccionario, y luego devuelvo solamente las palabras cuya clave aparece
al menos dos veces. Eso me asegura que solo salgan las que realmente tienen pareja.
