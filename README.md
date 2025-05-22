# ae1-bim1-aa2025

# Problemática
Un almacén de venta de trajes desea optimizar su sistema de facturación y análisis de ventas. Para ello, se requiere desarrollar un programa que cumpla con los siguientes requerimientos:

## Entrada de datos:

* El usuario ingresará el nombre y apellido del cliente.
* Luego, ingresará la cantidad de trajes a comprar.
* Cada traje tiene un mismo precio unitario, que también debe ser ingresado por el usuario.

## Cálculo de descuentos:

* Si se compra 1 traje, se aplica un 10% de descuento.
* Si se compran 2 trajes, se aplica un 20% de descuento.
* Si se compran 3 trajes, se aplica un 40% de descuento.
* Si se compran más de 3 trajes, se aplica un 60% de descuento.

## Cálculo de totales:

* Se debe calcular el subtotal antes del descuento.
* Se debe calcular el monto del descuento aplicado.
* Se debe calcular el total a pagar después del descuento.

## Registro de múltiples clientes:

* El sistema debe permitir registrar la compra de varios clientes, usando un ciclo while hasta que el usuario decida terminar el ingreso de datos.

## Almacenamiento de datos en estructuras de datos adecuadas:

* Utilizar un arreglo unidimensional para registrar los totales de cada cliente.
* Utilizar un arreglo unidimensional para almacenar los nombres
* Utilizar un arreglo unidimensional para almacenar los apellidos
* Utilizar un arreglo unidimensional para almacenar los cantidad de trajes
* Utilizar un arreglo unidimensional para almacenar el precio unitario de la venta

Las posiciones se corresponden, la posición 0 de cada arreglo, darian una registro completo

## Mostrar la información de cada compra registrada.

## Calcular y mostrar el promedio de ventas realizadas.
## Determinar la venta más alta y la más baja.
# Listas para almacenar los datos de los clientes
nombres = []
apellidos = []
cantidades = []
precios_unitarios = []
totales = []

def calcular_descuento(cantidad, precio_unitario):
    subtotal = cantidad * precio_unitario

    if cantidad == 1:
        descuento = 0.10
    elif cantidad == 2:
        descuento = 0.20
    elif cantidad == 3:
        descuento = 0.40
    elif cantidad > 3:
        descuento = 0.60
    else:
        descuento = 0.0

    monto_descuento = subtotal * descuento
    total_pagar = subtotal - monto_descuento

    return subtotal, monto_descuento, total_pagar

# Ingreso de múltiples clientes
while True:
    print("\n--- Nueva venta ---")
    nombre = input("Ingrese el nombre del cliente: ")
    apellido = input("Ingrese el apellido del cliente: ")
    cantidad = int(input("Ingrese la cantidad de trajes a comprar: "))
    precio_unitario = float(input("Ingrese el precio unitario del traje: "))

    subtotal, monto_descuento, total_pagar = calcular_descuento(cantidad, precio_unitario)

    # Guardar datos
    nombres.append(nombre)
    apellidos.append(apellido)
    cantidades.append(cantidad)
    precios_unitarios.append(precio_unitario)
    totales.append(total_pagar)

    print(f"\nResumen de la compra para {nombre} {apellido}:")
    print(f"Subtotal: ${subtotal:.2f}")
    print(f"Descuento aplicado: ${monto_descuento:.2f}")
    print(f"Total a pagar: ${total_pagar:.2f}")

    continuar = input("\n¿Desea ingresar otra venta? (s/n): ").lower()
    if continuar != 's':
        break

# Mostrar la información de todas las compras
print("\n--- Registro de todas las ventas ---")
for i in range(len(nombres)):
    print(f"\nCliente: {nombres[i]} {apellidos[i]}")
    print(f"Cantidad de trajes: {cantidades[i]}")
    print(f"Precio unitario: ${precios_unitarios[i]:.2f}")
    print(f"Total pagado: ${totales[i]:.2f}")

# Calcular promedio de ventas
promedio_ventas = sum(totales) / len(totales) if totales else 0
print(f"\nPromedio de ventas: ${promedio_ventas:.2f}")

# Venta más alta y más baja
venta_maxima = max(totales) if totales else 0
venta_minima = min(totales) if totales else 0
print(f"Venta más alta: ${venta_maxima:.2f}")
print(f"Venta más baja: ${venta_minima:.2f}")

