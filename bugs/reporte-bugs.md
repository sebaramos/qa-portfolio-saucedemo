# 🐞 Reporte de Bugs - SauceDemo

Registro de defectos funcionales y de interfaz detectados durante las pruebas manuales sobre **SauceDemo (Swag Labs)**.

---

## BUG-001: Permite iniciar el proceso de Checkout con el carrito vacío

* **Módulo:** Carrito / Checkout
* **Severidad:** Alta
* **Prioridad:** Alta
* **Estado:** Abierto
* **Entorno:** `https://www.saucedemo.com/` | Chrome Desktop (`1920x1080`) | Usuario: `standard_user`

### 📝 Descripción
El sistema permite avanzar desde la vista del carrito (`/cart.html`) hacia el formulario de información de envío (`/checkout-step-one.html`) aun cuando el carrito no contiene ningún producto agregado.

### 🔁 Pasos para Reproducir
1. Iniciar sesión en SauceDemo con `standard_user` y `secret_sauce`.
2. Verificar que el ícono del carrito no muestre artículos añadidos.
3. Hacer clic en el ícono del carrito para ir a `/cart.html`.
4. Hacer clic en el botón **Checkout**.

### ✅ Resultado Esperado
El botón **Checkout** debe estar deshabilitado o bloquear el avance mostrando un mensaje indicando que el carrito está vacío y que se debe agregar al menos un producto antes de continuar.

### ❌ Resultado Actual
La aplicación redirige a `/checkout-step-one.html` y permite ingresar datos de envío sin productos en el carrito.

---

## BUG-002: El botón "Remove" no elimina productos agregados en `problem_user`

* **Módulo:** Inventario / Carrito
* **Severidad:** Alta
* **Prioridad:** Media
* **Estado:** Abierto (Comportamiento conocido en perfil `problem_user`)
* **Entorno:** `https://www.saucedemo.com/` | Chrome Desktop (`1920x1080`) | Usuario: `problem_user`

### 📝 Descripción
Al iniciar sesión con el usuario `problem_user` y agregar ciertos productos al carrito, hacer clic en el botón **Remove** no retira el artículo ni actualiza el contador del carrito.

### 🔁 Pasos para Reproducir
1. Iniciar sesión en SauceDemo con `problem_user` y `secret_sauce`.
2. Hacer clic en **Add to cart** en `Sauce Labs Backpack` o `Sauce Labs Fleece Jacket`.
3. Verificar que el contador del carrito sube a `1`.
4. Hacer clic en el botón **Remove** del mismo producto.

### ✅ Resultado Esperado
El producto debe eliminarse del carrito, el botón debe volver a mostrar **Add to cart** y el contador del carrito debe decrementarse o desaparecer si queda en `0`.

### ❌ Resultado Actual
El producto permanece agregado y el contador del carrito no cambia al presionar **Remove**.

---

## BUG-003: El campo "Last Name" no acepta entrada en el formulario de Checkout con `problem_user`

* **Módulo:** Checkout (Información de Envío)
* **Severidad:** Bloqueante (para el flujo de compra con ese perfil)
* **Prioridad:** Media
* **Estado:** Abierto (Comportamiento conocido en perfil `problem_user`)
* **Entorno:** `https://www.saucedemo.com/` | Chrome Desktop (`1920x1080`) | Usuario: `problem_user`

### 📝 Descripción
En la pantalla `Checkout: Your Information` (`/checkout-step-one.html`), al intentar escribir en el campo **Last Name** utilizando `problem_user`, el input no conserva el texto ingresado (o lo sobrescribe/limpia), impidiendo continuar con la compra.

### 🔁 Pasos para Reproducir
1. Iniciar sesión con `problem_user` y agregar al menos un producto al carrito.
2. Ir al carrito, hacer clic en **Checkout** y llegar a `/checkout-step-one.html`.
3. Ingresar un valor en **First Name** (ej. `Sebastián`).
4. Hacer clic en **Last Name** e intentar escribir un apellido (ej. `Ramos`).
5. Ingresar un código postal en **Zip/Postal Code** (ej. `8320000`) y hacer clic en **Continue**.

### ✅ Resultado Esperado
El campo **Last Name** debe aceptar y conservar el texto ingresado, permitiendo avanzar a `/checkout-step-two.html`.

### ❌ Resultado Actual
El campo **Last Name** no permite completar el dato de forma normal y bloquea el avance hacia el resumen de la orden.
