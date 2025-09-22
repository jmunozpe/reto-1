# reto-1

Este repositorio contiene **5 programas**, uno por cada punto del reto.

1.Crear una función que realice operaciones básicas (suma, resta, multiplicación, división) entre dos números, según la elección del usuario, la forma de entrada de la función será los dos operandos y el caracter usado para la operación. entrada: (1,2,"+"), salida (3).

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

2.Realice una función que permita validar si una palabra es un palíndromo. Condición: No se vale hacer slicing para invertir la palabra y verificar que sea igual a la original.
