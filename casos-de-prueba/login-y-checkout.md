# 📝 Casos de Prueba Funcionales - Login y Checkout

Matriz de pruebas funcionales (escenarios positivos y negativos) diseñados para validar la autenticación y el flujo de compra en **SauceDemo**.

---

## 🔐 Módulo 1: Autenticación (Login)

| ID | Título del Caso | Tipo | Precondiciones | Pasos de Ejecución | Resultado Esperado | Estado |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **TC-001** | Inicio de sesión exitoso con usuario estándar | Positivo | Estar en `https://www.saucedemo.com/` | 1. Ingresar `standard_user` en Username.<br>2. Ingresar `secret_sauce` en Password.<br>3. Hacer clic en **Login**. | Redirige correctamente a `/inventory.html` y muestra el catálogo de productos. | ✅ Pass |
| **TC-002** | Intento de login con usuario bloqueado | Negativo | Estar en la pantalla de Login | 1. Ingresar `locked_out_user` en Username.<br>2. Ingresar `secret_sauce` en Password.<br>3. Hacer clic en **Login**. | Permanece en Login y muestra el banner: *"Epic sadface: Sorry, this user has been locked out."* | ✅ Pass |
| **TC-003** | Intento de login con contraseña incorrecta | Negativo | Estar en la pantalla de Login | 1. Ingresar `standard_user` en Username.<br>2. Ingresar `clave_erronea` en Password.<br>3. Hacer clic en **Login**. | Muestra el error: *"Epic sadface: Username and password do not match any user in this service"*. | ✅ Pass |
| **TC-004** | Validación de campos obligatorios vacíos | Negativo | Estar en la pantalla de Login | 1. Dejar ambos campos vacíos.<br>2. Hacer clic en **Login**. | Muestra el error: *"Epic sadface: Username is required"* y marca ambos inputs con ícono `X`. | ✅ Pass |
| **TC-005** | Acceso directo por URL sin sesión activa | Negativo | Sesión cerrada / navegador limpio | 1. Navegar directamente a `https://www.saucedemo.com/inventory.html`. | Bloquea el acceso, redirige a Login y muestra: *"Epic sadface: You can only access '/inventory.html' when you are logged in."* | ✅ Pass |
| **TC-006** | Cierre de sesión (Logout) y bloqueo de historial | Positivo | Sesión iniciada con `standard_user` | 1. Abrir menú lateral (hamburguesa).<br>2. Hacer clic en **Logout**.<br>3. Presionar el botón "Atrás" del navegador. | Cierra sesión hacia Login y, al retroceder, impide volver al inventario sin autenticarse nuevamente. | ✅ Pass |

---

## 🛒 Módulo 2: Proceso de Compra (Checkout)

| ID | Título del Caso | Tipo | Precondiciones | Pasos de Ejecución | Resultado Esperado | Estado |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **TC-007** | Compra exitosa end-to-end (1 producto) | Positivo | Sesión iniciada y al menos 1 producto en el carrito | 1. Ir al carrito y hacer clic en **Checkout**.<br>2. Completar First Name (`Juan`), Last Name (`Pérez`), Zip (`8320000`) y clic en **Continue**.<br>3. Verificar resumen y hacer clic en **Finish**. | Muestra la pantalla `Checkout: Complete!` con el mensaje *"Thank you for your order!"* y el contador del carrito desaparece. | ✅ Pass |
| **TC-008** | Cálculo exacto de subtotal, impuestos (8%) y total | Positivo | Carrito con `Sauce Labs Backpack` ($29.99) y `Sauce Labs Bike Light` ($9.99) | 1. Avanzar hasta `Checkout: Overview`.<br>2. Revisar desglose de precios. | Item total: `$39.98`, Tax: `$3.20` (8%), Total: `$43.18`. | ✅ Pass |
| **TC-009** | Validación de First Name vacío en Checkout | Negativo | Estar en `Checkout: Your Information` | 1. Dejar *First Name* vacío.<br>2. Completar *Last Name* y *Postal Code*.<br>3. Hacer clic en **Continue**. | Bloquea el avance y muestra: *"Error: First Name is required"*. | ✅ Pass |
| **TC-010** | Validación de Código Postal vacío en Checkout | Negativo | Estar en `Checkout: Your Information` | 1. Completar *First Name* y *Last Name*.<br>2. Dejar *Zip/Postal Code* vacío.<br>3. Hacer clic en **Continue**. | Bloquea el avance y muestra: *"Error: Postal Code is required"*. | ✅ Pass |
| **TC-011** | Cancelar compra desde el resumen de orden | Positivo | Estar en `Checkout: Overview` con productos | 1. Hacer clic en el botón **Cancel**. | Regresa a `/inventory.html` manteniendo los productos intactos en el carrito. | ✅ Pass |
| **TC-012** | Intento de Checkout con carrito vacío | Negativo | Sesión iniciada con 0 productos en el carrito | 1. Hacer clic en el ícono del carrito.<br>2. Hacer clic en **Checkout**. | *(Hallazgo funcional)* Permite avanzar al formulario de envío a pesar de no tener artículos seleccionados. | ⚠️ Bug |
