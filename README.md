# spring-boot
# API Sistema de Créditos

API REST para la gestión de un sistema de créditos financieros. La aplicación permite administrar **clientes, productos, créditos, pagos y contratos**, proporcionando operaciones CRUD mediante endpoints HTTP.

La API está documentada mediante **OpenAPI 3.0** y puede visualizarse utilizando Swagger UI.

---

## 📋 Contenido

* [Descripción](#-descripción)
* [Tecnologías](#-tecnologías)
* [Configuración](#-configuración)
* [Ejecución](#-ejecución)
* [Swagger UI](#-swagger-ui)
* [Estructura de la API](#-estructura-de-la-api)

  * [Clientes](#clientes)
  * [Productos](#productos)
  * [Créditos](#créditos)
  * [Pagos](#pagos)
  * [Contratos](#contratos)
* [Modelos de datos](#-modelos-de-datos)
* [Códigos HTTP](#-códigos-http)

---

## 📌 Descripción

El proyecto consiste en una API REST desarrollada para administrar las operaciones principales de un sistema de créditos financieros.

La API permite:

* Registrar y administrar clientes.
* Registrar y administrar productos financieros.
* Crear y consultar créditos.
* Registrar y consultar pagos.
* Crear y consultar contratos asociados a créditos.
* Relacionar clientes con créditos.
* Relacionar créditos con productos.
* Relacionar pagos con clientes y créditos.

La API utiliza JSON como formato principal para el intercambio de información.

---

## 🛠️ Tecnologías

Las tecnologías utilizadas en el proyecto incluyen:

* **Java**
* **Spring Boot**
* **Spring Web / REST**
* **OpenAPI 3.0**
* **Swagger UI**
* **Maven**
* **Base de datos** configurada en el proyecto

---

## ⚙️ Configuración

Por defecto, la API se encuentra disponible en:

```text
http://localhost:8081/snpp
```

La estructura base de los endpoints es:

```text
http://localhost:8081/snpp/api/{recurso}
```

Por ejemplo:

```text
http://localhost:8081/snpp/api/clientes
```

> **Nota:** La URL `localhost` funciona únicamente cuando el servidor se encuentra ejecutándose en el equipo local.

---

## ▶️ Ejecución

Para ejecutar el proyecto:

1. Clonar el repositorio.

```bash
git clone URL_DEL_REPOSITORIO
```

2. Ingresar a la carpeta del proyecto.

```bash
cd nombre-del-proyecto
```

3. Ejecutar la aplicación Spring Boot.

Si se utiliza Maven:

```bash
mvn spring-boot:run
```

También es posible ejecutar la clase principal de Spring Boot directamente desde el IDE.

Una vez iniciada la aplicación, la API estará disponible en:

```text
http://localhost:8081/snpp
```

---

# 📚 Swagger UI

La API utiliza Swagger UI para visualizar y probar los endpoints.

Una vez iniciada la aplicación, acceder a:

```text
http://localhost:8081/snpp/swagger-ui/index.html
```

También se puede acceder directamente a la especificación OpenAPI:

```text
http://localhost:8081/snpp/v3/api-docs
```

Swagger permite:

* Visualizar los endpoints disponibles.
* Consultar parámetros.
* Consultar modelos de datos.
* Ejecutar peticiones HTTP.
* Probar los endpoints directamente desde el navegador.

---

# 🔌 Estructura de la API

La API está organizada en cinco recursos principales:

| Recurso   | Descripción                      |
| --------- | -------------------------------- |
| Clientes  | Gestión de clientes del sistema  |
| Productos | Gestión de productos financieros |
| Créditos  | Gestión de créditos financieros  |
| Pagos     | Gestión de pagos de créditos     |
| Contratos | Gestión de contratos de crédito  |

---

# 👤 Clientes

Los endpoints relacionados con clientes utilizan:

```text
/api/clientes
```

## Listar todos los clientes

**GET**

```http
GET /api/clientes
```

Obtiene la lista completa de clientes registrados.

### Respuesta

```json
[
  {
    "id": 1,
    "nombre": "Juan Pérez",
    "documento": "1234567"
  }
]
```

---

## Registrar un cliente

**POST**

```http
POST /api/clientes
```

### Body

```json
{
  "nombre": "Juan Pérez",
  "documento": "1234567"
}
```

### Respuesta

```json
{
  "id": 1,
  "nombre": "Juan Pérez",
  "documento": "1234567"
}
```

---

## Buscar un cliente

**GET**

```http
GET /api/clientes/{id}
```

### Parámetro

| Parámetro | Tipo | Descripción    |
| --------- | ---- | -------------- |
| `id`      | Long | ID del cliente |

### Ejemplo

```http
GET /api/clientes/1
```

---

## Actualizar un cliente

**PUT**

```http
PUT /api/clientes/{id}
```

### Body

```json
{
  "nombre": "Juan Carlos Pérez",
  "documento": "1234567"
}
```

### Ejemplo

```http
PUT /api/clientes/1
```

---

## Eliminar un cliente

**DELETE**

```http
DELETE /api/clientes/{id}
```

### Ejemplo

```http
DELETE /api/clientes/1
```

---

# 💰 Productos

Los endpoints relacionados con productos utilizan:

```text
/api/productos
```

## Listar productos

**GET**

```http
GET /api/productos
```

Obtiene todos los productos registrados.

### Respuesta

```json
[
  {
    "id": 1,
    "nombre": "Préstamo Personal",
    "precio": 5000000
  }
]
```

---

## Registrar un producto

**POST**

```http
POST /api/productos
```

### Body

```json
{
  "nombre": "Préstamo Personal",
  "precio": 5000000
}
```

---

## Buscar un producto

**GET**

```http
GET /api/productos/{id}
```

### Ejemplo

```http
GET /api/productos/1
```

---

## Eliminar un producto

**DELETE**

```http
DELETE /api/productos/{id}
```

### Ejemplo

```http
DELETE /api/productos/1
```

---

# 💳 Créditos

Los endpoints relacionados con créditos utilizan:

```text
/api/creditos
```

## Listar créditos

**GET**

```http
GET /api/creditos
```

Obtiene todos los créditos registrados.

### Respuesta

```json
[
  {
    "id": 1,
    "monto": 5000000,
    "fecha": "2026-08-12",
    "nombreCliente": "Juan Pérez",
    "productos": [
      "Préstamo Personal"
    ]
  }
]
```

---

## Registrar un crédito

**POST**

```http
POST /api/creditos
```

### Body

```json
{
  "monto": 5000000,
  "fecha": "2026-08-12",
  "idCliente": 1,
  "idsProductos": [
    1,
    2
  ]
}
```

### Campos

| Campo          | Tipo        | Descripción                    |
| -------------- | ----------- | ------------------------------ |
| `monto`        | Double      | Monto del crédito              |
| `fecha`        | Date        | Fecha del crédito              |
| `idCliente`    | Long        | ID del cliente                 |
| `idsProductos` | Array<Long> | IDs de los productos asociados |

---

## Buscar un crédito

**GET**

```http
GET /api/creditos/{id}
```

### Ejemplo

```http
GET /api/creditos/1
```

---

## Eliminar un crédito

**DELETE**

```http
DELETE /api/creditos/{id}
```

### Ejemplo

```http
DELETE /api/creditos/1
```

---

# 💵 Pagos

Los endpoints relacionados con pagos utilizan:

```text
/api/pagos
```

## Listar pagos

**GET**

```http
GET /api/pagos
```

### Respuesta

```json
[
  {
    "id": 1,
    "monto": 500000,
    "fecha": "2026-08-12",
    "nombreCliente": "Juan Pérez",
    "idCredito": 1
  }
]
```

---

## Registrar un pago

**POST**

```http
POST /api/pagos
```

### Body

```json
{
  "monto": 500000,
  "fecha": "2026-08-12",
  "idCliente": 1,
  "idCredito": 1
}
```

### Campos

| Campo       | Tipo   | Descripción    |
| ----------- | ------ | -------------- |
| `monto`     | Double | Monto del pago |
| `fecha`     | Date   | Fecha del pago |
| `idCliente` | Long   | ID del cliente |
| `idCredito` | Long   | ID del crédito |

---

## Buscar un pago

**GET**

```http
GET /api/pagos/{id}
```

### Ejemplo

```http
GET /api/pagos/1
```

---

## Eliminar un pago

**DELETE**

```http
DELETE /api/pagos/{id}
```

### Ejemplo

```http
DELETE /api/pagos/1
```

---

# 📄 Contratos

Los endpoints relacionados con contratos utilizan:

```text
/api/contratos
```

## Listar contratos

**GET**

```http
GET /api/contratos
```

### Respuesta

```json
[
  {
    "id": 1,
    "condiciones": "Pago mensual durante 12 meses",
    "fechaFirma": "2026-08-12",
    "idCredito": 1
  }
]
```

---

## Registrar un contrato

**POST**

```http
POST /api/contratos
```

### Body

```json
{
  "condiciones": "Pago mensual durante 12 meses",
  "fechaFirma": "2026-08-12",
  "idCredito": 1
}
```

### Campos

| Campo         | Tipo   | Descripción              |
| ------------- | ------ | ------------------------ |
| `condiciones` | String | Condiciones del contrato |
| `fechaFirma`  | Date   | Fecha de firma           |
| `idCredito`   | Long   | ID del crédito asociado  |

---

## Buscar un contrato

**GET**

```http
GET /api/contratos/{id}
```

### Ejemplo

```http
GET /api/contratos/1
```

---

## Eliminar un contrato

**DELETE**

```http
DELETE /api/contratos/{id}
```

### Ejemplo

```http
DELETE /api/contratos/1
```

---

# 🧩 Modelos de datos

## ClienteRequest

Se utiliza para registrar o actualizar clientes.

```json
{
  "nombre": "Juan Pérez",
  "documento": "1234567"
}
```

### Propiedades

| Campo       | Tipo   |
| ----------- | ------ |
| `nombre`    | String |
| `documento` | String |

---

## ClienteResponse

```json
{
  "id": 1,
  "nombre": "Juan Pérez",
  "documento": "1234567"
}
```

---

## ProductoRequest

```json
{
  "nombre": "Préstamo Personal",
  "precio": 5000000
}
```

### Propiedades

| Campo    | Tipo   |
| -------- | ------ |
| `nombre` | String |
| `precio` | Double |

---

## ProductoResponse

```json
{
  "id": 1,
  "nombre": "Préstamo Personal",
  "precio": 5000000
}
```

---

## PagoRequest

```json
{
  "monto": 500000,
  "fecha": "2026-08-12",
  "idCliente": 1,
  "idCredito": 1
}
```

---

## PagoResponse

```json
{
  "id": 1,
  "monto": 500000,
  "fecha": "2026-08-12",
  "nombreCliente": "Juan Pérez",
  "idCredito": 1
}
```

---

## CreditoRequest

```json
{
  "monto": 5000000,
  "fecha": "2026-08-12",
  "idCliente": 1,
  "idsProductos": [
    1,
    2
  ]
}
```

---

## CreditoResponse

```json
{
  "id": 1,
  "monto": 5000000,
  "fecha": "2026-08-12",
  "nombreCliente": "Juan Pérez",
  "productos": [
    "Préstamo Personal",
    "Seguro de Vida"
  ]
}
```

---

## ContratoRequest

```json
{
  "condiciones": "Pago mensual durante 12 meses",
  "fechaFirma": "2026-08-12",
  "idCredito": 1
}
```

---

## ContratoResponse

```json
{
  "id": 1,
  "condiciones": "Pago mensual durante 12 meses",
  "fechaFirma": "2026-08-12",
  "idCredito": 1
}
```

---

# 📊 Resumen de endpoints

| Método | Endpoint              | Descripción        |
| ------ | --------------------- | ------------------ |
| GET    | `/api/clientes`       | Listar clientes    |
| POST   | `/api/clientes`       | Registrar cliente  |
| GET    | `/api/clientes/{id}`  | Buscar cliente     |
| PUT    | `/api/clientes/{id}`  | Actualizar cliente |
| DELETE | `/api/clientes/{id}`  | Eliminar cliente   |
| GET    | `/api/productos`      | Listar productos   |
| POST   | `/api/productos`      | Registrar producto |
| GET    | `/api/productos/{id}` | Buscar producto    |
| DELETE | `/api/productos/{id}` | Eliminar producto  |
| GET    | `/api/creditos`       | Listar créditos    |
| POST   | `/api/creditos`       | Registrar crédito  |
| GET    | `/api/creditos/{id}`  | Buscar crédito     |
| DELETE | `/api/creditos/{id}`  | Eliminar crédito   |
| GET    | `/api/pagos`          | Listar pagos       |
| POST   | `/api/pagos`          | Registrar pago     |
| GET    | `/api/pagos/{id}`     | Buscar pago        |
| DELETE | `/api/pagos/{id}`     | Eliminar pago      |
| GET    | `/api/contratos`      | Listar contratos   |
| POST   | `/api/contratos`      | Registrar contrato |
| GET    | `/api/contratos/{id}` | Buscar contrato    |
| DELETE | `/api/contratos/{id}` | Eliminar contrato  |

---

# 🔢 Códigos HTTP

La especificación OpenAPI actual define principalmente respuestas exitosas `200 OK` para las operaciones disponibles.

| Código   | Significado                           |
| -------- | ------------------------------------- |
| `200 OK` | La operación se realizó correctamente |

> Los códigos adicionales como `400 Bad Request`, `404 Not Found` o `500 Internal Server Error` no están definidos explícitamente en la especificación OpenAPI proporcionada.

---

# 🔗 Arquitectura de relaciones

La API maneja las siguientes relaciones principales:

```text
Cliente
   │
   ├── Créditos
   │      │
   │      ├── Productos
   │      │
   │      └── Contrato
   │
   └── Pagos
          │
          └── Crédito
```

Un **cliente** puede estar asociado a créditos y pagos.

Un **crédito** puede estar asociado a uno o varios productos y puede tener un contrato.

Los **pagos** están relacionados con un cliente y un crédito.

---

# 📖 Documentación OpenAPI

La especificación de la API está generada mediante OpenAPI 3.0.1.

Para consultar la documentación interactiva:

```text
http://localhost:8081/snpp/swagger-ui/index.html
```

Para consultar el documento JSON:

```text
http://localhost:8081/snpp/v3/api-docs
```

---

# 👨‍💻 Autor

Proyecto desarrollado como parte de un sistema de gestión de créditos financieros.

---
