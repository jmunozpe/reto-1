# reto-1

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
