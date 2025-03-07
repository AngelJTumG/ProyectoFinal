# API Supermercado - Documentación y Uso

## 1. Introducción
Este proyecto proporciona una API REST para la gestión de usuarios, clientes, categorías, productos, carritos de compra e historial de facturas en un sistema de supermercado.

---

## 2. Uso de la Colección de Postman

### 2.1 Importar la Colección en Postman
Para facilitar la prueba de los endpoints, se proporciona una colección de Postman.

#### Pasos para importar la colección:
1. Abre **Postman**.
2. Ve a la pestaña **Import** en la parte superior izquierda.
3. Selecciona la opción **File**.
4. Busca el archivo `supermercado.postman_collection.json` y cárgalo.
5. Una vez importado, la colección aparecerá en la lista de Postman.

---

## 3. Importar Datos a MongoDB

Para poblar la base de datos con datos iniciales, sigue estos pasos:

### 3.1 Instalación de MongoDB (Si no está instalado)
Si aún no tienes MongoDB instalado, puedes hacerlo desde:
- [MongoDB Community Server](https://www.mongodb.com/try/download/community)

### 3.2 Importar Datos
1. Ubica el archivo JSON con los datos iniciales, por ejemplo: `data.json`.
2. Usa el siguiente comando en la terminal para importar los datos:

```sh
mongoimport --db supermercado --collection clientes --file data.json --jsonArray
```

**Nota:** Ajusta el nombre de la colección según los datos que deseas importar (ej. `productos`, `categorias`).

---

## 4. Endpoints Disponibles

A continuación, se presentan los endpoints organizados por sus respectivas rutas:

### 4.1 Autenticación (`auth.routes.js`)
- **POST** `/supermercado/v1/auth/register` → Registrar un nuevo usuario.
- **POST** `/supermercado/v1/auth/login` → Iniciar sesión de un usuario.

### 4.2 Clientes (`cliente.routes.js`)
- **GET** `/supermercado/v1/cliente/findCliente/:uid` → Obtener un cliente por ID.
- **GET** `/supermercado/v1/cliente/` → Obtener todos los clientes.
- **DELETE** `/supermercado/v1/cliente/deleteCliente/:uid` → Eliminar un cliente por ID.
- **PATCH** `/supermercado/v1/cliente/updatePassword/:uid` → Actualizar la contraseña de un cliente.
- **PUT** `/supermercado/v1/cliente/updateCliente/:uid` → Actualizar un cliente.
- **PATCH** `/supermercado/v1/cliente/updateRol/:uid` → Actualizar el rol de un cliente.

### 4.3 Categorías (`categoria.routes.js`)
- **POST** `/supermercado/v1/categoria/addCategory` → Agregar una nueva categoría.
- **GET** `/supermercado/v1/categoria/` → Obtener todas las categorías.
- **PATCH** `/supermercado/v1/categoria/updateCategory/:id` → Actualizar una categoría.
- **DELETE** `/supermercado/v1/categoria/deleteCategory/:id` → Eliminar una categoría por ID.

### 4.4 Productos (`product.routes.js`)
- **POST** `/supermercado/v1/product/addProduct` → Agregar un nuevo producto.
- **GET** `/supermercado/v1/product/findProduct/:nameProduct` → Obtener un producto por nombre.
- **GET** `/supermercado/v1/product/` → Obtener todos los productos.
- **GET** `/supermercado/v1/product/category/:categoryId` → Obtener productos por categoría.
- **GET** `/supermercado/v1/product/soldOut/` → Obtener productos agotados.
- **PUT** `/supermercado/v1/product/updateProduct/:uid` → Actualizar un producto.
- **DELETE** `/supermercado/v1/product/deleteProduct/:uid` → Eliminar un producto por ID.
- **GET** `/supermercado/v1/product/topSellingProducts` → Obtener los productos más vendidos.

### 4.5 Carrito de Compras (`carrito.routes.js`)
- **POST** `/supermercado/v1/carrito/agregarCarrito` → Agregar productos al carrito.
- **GET** `/supermercado/v1/carrito/` → Obtener productos del carrito.
- **POST** `/supermercado/v1/carrito/completarCompra/:carritoId` → Completar la compra.

### 4.6 Facturas (`invoices.routes.js`)
- **GET** `/supermercado/v1/invoices/historialFactura` → Obtener el historial de facturas.

---

## 5. Consideraciones Finales

- Asegúrate de que MongoDB esté en ejecución antes de hacer peticiones a la API.
- Usa Postman para probar cada endpoint.
- En caso de errores, revisa los registros en la consola del servidor.

---

### **Autor**: Equipo de Desarrollo - Supermercado API

