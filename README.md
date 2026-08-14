# API de Gestión Financiera y Créditos

Esta es una API RESTful desarrollada para la gestión de clientes, créditos, pagos, productos financieros y contratos. La documentación interactiva de la API está integrada mediante Swagger UI (OpenAPI 3.0).

---

## 🚀 Tabla de Contenidos
- [Características](#-características)
- [Estructura del Proyecto](#-estructura-del-proyecto)
- [Endpoints de la API](#-endpoints-de-la-api)
  - [Pagos](#1-pagos)
  - [Créditos](#2-créditos)
  - [Clientes](#3-clientes)
  - [Contratos](#4-contratos)
  - [Productos](#5-productos)
- [Modelos / Esquemas (Schemas)](#-modelos--esquemas-schemas)
- [Documentación Interactiva (Swagger)](#-documentación-interactiva-swagger)
- [Instalación y Ejecución](#-instalación-y-ejecución)

---

## 🛠 Características

- **Gestión de Clientes:** Altas, consultas, modificaciones y bajas de clientes.
- **Gestión de Productos Financieros:** Registro y mantenimiento de la oferta de productos.
- **Gestión de Créditos:** Asignación y administración de créditos financieros.
- **Gestión de Contratos:** Control de acuerdos y contratos vinculados a los créditos.
- **Gestión de Pagos:** Registro y seguimiento del historial de pagos de créditos.

---

## 🌐 Endpoints de la API

La API cuenta con un prefijo base `/api` para todas sus rutas.

### 1. Pagos (`/api/pagos`)
*Gestión de pagos de créditos.*

| Método | Endpoint | Descripción |
| :--- | :--- | :--- |
| `GET` | `/api/pagos` | Listar todos los pagos |
| `POST` | `/api/pagos` | Registrar un nuevo pago |
| `GET` | `/api/pagos/{id}` | Buscar un pago por ID |
| `DELETE` | `/api/pagos/{id}` | Eliminar un pago |

---

### 2. Créditos (`/api/creditos`)
*Gestión de créditos financieros.*

| Método | Endpoint | Descripción |
| :--- | :--- | :--- |
| `GET` | `/api/creditos` | Listar todos los créditos |
| `POST` | `/api/creditos` | Registrar un nuevo crédito |
| `GET` | `/api/creditos/{id}` | Buscar un crédito por ID |
| `DELETE` | `/api/creditos/{id}` | Eliminar un crédito |

---

### 3. Clientes (`/api/clientes`)
*Gestión de clientes del sistema de crédito.*

| Método | Endpoint | Descripción |
| :--- | :--- | :--- |
| `GET` | `/api/clientes` | Listar todos los clientes |
| `POST` | `/api/clientes` | Registrar un nuevo cliente |
| `GET` | `/api/clientes/{id}` | Buscar un cliente por ID |
| `PUT` | `/api/clientes/{id}` | Actualizar datos de un cliente |
| `DELETE` | `/api/clientes/{id}` | Eliminar un cliente |

---

### 4. Contratos (`/api/contratos`)
*Gestión de contratos de crédito.*

| Método | Endpoint | Descripción |
| :--- | :--- | :--- |
| `GET` | `/api/contratos` | Listar todos los contratos |
| `POST` | `/api/contratos` | Registrar un nuevo contrato |
| `GET` | `/api/contratos/{id}` | Buscar un contrato por ID |
| `DELETE` | `/api/contratos/{id}` | Eliminar un contrato |

---

### 5. Productos (`/api/productos`)
*Gestión de productos financieros.*

| Método | Endpoint | Descripción |
| :--- | :--- | :--- |
| `GET` | `/api/productos` | Listar todos los productos |
| `POST` | `/api/productos` | Registrar un nuevo producto |
| `GET` | `/api/productos/{id}` | Buscar un producto por ID |
| `DELETE` | `/api/productos/{id}` | Eliminar un producto |

---

## 📦 Modelos / Esquemas (Schemas)

El sistema maneja los siguientes objetos de transferencia de datos (DTOs):

- **Cliente:** `ClienteRequest`, `ClienteResponse`
- **Producto:** `ProductoRequest`, `ProductoResponse`
- **Crédito:** `CreditoRequest`, `CreditoResponse`
- **Pago:** `PagoRequest`, `PagoResponse`
- **Contrato:** `ContratoRequest`, `ContratoResponse`

---

## 📄 Documentación Interactiva (Swagger)

Una vez iniciada la aplicación en entorno local, puedes acceder a la interfaz de Swagger UI para probar los endpoints e inspeccionar los modelos de datos en:

- **Swagger UI:** `http://localhost:8081/snpp/swagger-ui/index.html`
- **OpenAPI Docs (JSON):** `http://localhost:8081/snpp/v3/api-docs`

---

## 💻 Instalación y Ejecución

1. **Clonar el repositorio:**
   ```bash
   git clone [https://github.com/tu-usuario/tu-repositorio.git](https://github.com/tu-usuario/tu-repositorio.git)
   cd tu-repositorio