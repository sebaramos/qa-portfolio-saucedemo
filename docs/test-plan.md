# 📋 Plan de Pruebas (Mini Test Plan) - SauceDemo

## 1. Objetivo
Validar el correcto funcionamiento de los flujos críticos de negocio, las reglas de validación de formularios y el manejo de estados de sesión en la aplicación web **SauceDemo (Swag Labs)**, asegurando una experiencia libre de defectos bloqueantes antes de su despliegue.

---

## 2. Alcance de las Pruebas (In-Scope)

### 🔹 Flujos Críticos (End-to-End)
* **Autenticación:** Inicio de sesión con los distintos perfiles de usuario (`standard_user`, `locked_out_user`, `problem_user`, `performance_glitch_user`, `error_user`, `visual_user`) y cierre de sesión (*Logout*).
* **Catálogo e Inventario:** Visualización de productos, navegación hacia el detalle de cada artículo, y filtros de ordenamiento (A-Z, Z-A, precio menor a mayor y mayor a menor).
* **Gestión del Carrito:** Añadir y quitar productos tanto desde el catálogo como desde la vista de detalle, y verificación de persistencia durante la navegación.
* **Proceso de Compra (Checkout):** Flujo completo desde el carrito hasta la pantalla de confirmación de orden (`Checkout: Complete!`), incluyendo cálculo de subtotal, impuestos (8%) y total.

### 🔹 Validaciones de Formularios
* **Login:** Campos vacíos (usuario y/o contraseña), credenciales incorrectas y mensajes de error descriptivos.
* **Información de Envío (Checkout Step One):** Validación de obligatoriedad en los campos *First Name*, *Last Name* y *Zip/Postal Code*, manejo de caracteres especiales y espacios en blanco.

### 🔹 Estados de Sesión y Seguridad Básica
* Restricción de acceso directo por URL a rutas internas (`/inventory.html`, `/cart.html`, `/checkout-step-one.html`) sin una sesión activa.
* Limpieza de estado de sesión al ejecutar *Logout* y comportamiento al usar el botón "Atrás" del navegador tras cerrar sesión.

---

## 3. Fuera de Alcance (Out-of-Scope)
En esta iteración **no** se ejecutarán los siguientes tipos de prueba:
* **Pruebas de Rendimiento y Carga:** Pruebas de estrés, concurrencia masiva o tiempos de respuesta bajo carga (excepto la observación funcional básica con `performance_glitch_user`).
* **Pasarelas de Pago Reales:** Integraciones bancarias, validación de tarjetas de crédito reales o procesamiento financiero externo (la app simula la compra).
* **Pruebas de Seguridad Avanzada:** Pruebas de penetración (Pentesting), inyección SQL o auditoría de vulnerabilidades OWASP.
* **Compatibilidad con Navegadores Obsoletos:** No se dará soporte a Internet Explorer ni versiones antiguas de navegadores móviles.

---

## 4. Entorno de Pruebas (Navegadores y Resoluciones)

| Categoría | Detalle |
| :--- | :--- |
| **URL del Entorno** | `https://www.saucedemo.com/` (Producción / Demo) |
| **Sistema Operativo** | macOS / Windows 11 |
| **Navegadores Desktop** | Google Chrome (v130+), Mozilla Firefox (v131+), Microsoft Edge (v130+) |
| **Resoluciones Desktop** | `1920x1080` (Full HD), `1366x768` (Laptop estándar) |
| **Resoluciones Mobile (Emulación DevTools)** | `390x844` (iPhone 14/15), `360x800` (Android estándar) |

---

## 5. Criterios de Entrada y Salida
* **Criterio de Entrada:** Entorno web accesible y disponibilidad de los usuarios de prueba proporcionados en la pantalla de login.
* **Criterio de Salida:** 100% de los casos de prueba críticos ejecutados, defectos encontrados documentados en la carpeta `/bugs` con su respectiva evidencia y ausencia de errores bloqueantes sin reportar.
