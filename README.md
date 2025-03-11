def agregar_producto(productos, id_producto, nombre, precio, stock):
    productos.append({"id": id_producto, "nombre": nombre, "precio": precio, "stock": stock})


def cambiar_estado_pedido(pedidos, id_pedido, nuevo_estado):
    for pedido in pedidos:
        if pedido["id_pedido"] == id_pedido:
            pedido["estado"] = nuevo_estado
            return
    print("Pedido no encontrado.")


def pedidos_por_cliente(pedidos, email):
    return [pedido for pedido in pedidos if pedido["cliente"] == email]


productos = [
    {"id": 1, "nombre": "Camiseta", "precio": 19.99, "stock": 50},
    {"id": 2, "nombre": "Zapatos", "precio": 49.99, "stock": 30}
]

pedidos = [
    {"id_pedido": 101, "cliente": "juan@email.com", "estado": "Pendiente"},
    {"id_pedido": 102, "cliente": "ana@email.com", "estado": "En proceso"}
]

clientes = [
    {"nombre": "Juan Pérez", "email": "juan@email.com"},
    {"nombre": "Ana Gómez", "email": "ana@email.com"}
]


agregar_producto(productos, 3, "Pantalón", 39.99, 75)


cambiar_estado_pedido(pedidos, 101, "Entregado")


pedidos_juan = pedidos_por_cliente(pedidos, "juan@email.com")

print("Productos en la tienda:")
for producto in productos:
    print(f"* {producto['nombre']} (ID: {producto['id']}, Precio: ${producto['precio']}, Stock: {producto['stock']})")


print("\nPedidos en la tienda:")
for pedido in pedidos:
    print(f"ID Pedido: {pedido['id_pedido']}, Cliente: {pedido['cliente']}, Estado: {pedido['estado']}")


print("\nPedidos de Juan:")
for pedido in pedidos_juan:
    print(f"ID Pedido: {pedido['id_pedido']}, Estado: {pedido['estado']}")
