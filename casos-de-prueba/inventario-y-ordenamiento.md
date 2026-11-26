# 📦 Casos de Prueba Funcionales - Inventario y Ordenamiento

Matriz de pruebas funcionales (escenarios positivos y negativos) para validar el catálogo de productos, los filtros de ordenamiento y la gestión del carrito desde el inventario en **SauceDemo**.

---

## 🛍️ Módulo: Inventario y Ordenamiento

| ID | Título del Caso | Tipo | Precondiciones | Pasos de Ejecución | Resultado Esperado | Estado |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **TC-013** | Visualización completa del inventario inicial | Positivo | Sesión iniciada con `standard_user` en `/inventory.html` | 1. Observar la grilla de productos cargada. | Se muestran los 6 productos con nombre, descripción, precio en USD, imagen y botón **Add to cart**. | ✅ Pass |
| **TC-014** | Ordenar productos alfabéticamente (Name A to Z) | Positivo | Estar en `/inventory.html` | 1. Hacer clic en el selector de ordenamiento (arriba a la derecha).<br>2. Seleccionar **Name (A to Z)**. | Los productos se ordenan de la `A` a la `Z` según su título (comenzando por *Sauce Labs Backpack*). | ✅ Pass |
| **TC-015** | Ordenar productos alfabéticamente inverso (Name Z to A) | Positivo | Estar en `/inventory.html` | 1. Abrir el selector de ordenamiento.<br>2. Seleccionar **Name (Z to A)**. | Los productos se ordenan de la `Z` a la `A` (comenzando por *Test.allTheThings() T-Shirt (Red)*). | ✅ Pass |
| **TC-016** | Ordenar productos por precio ascendente (Low to High) | Positivo | Estar en `/inventory.html` | 1. Abrir el selector de ordenamiento.<br>2. Seleccionar **Price (low to high)**. | Los artículos quedan ordenados del precio menor al mayor (`$7.99` a `$49.99`). | ✅ Pass |
| **TC-017** | Ordenar productos por precio descendente (High to Low) | Positivo | Estar en `/inventory.html` | 1. Abrir el selector de ordenamiento.<br>2. Seleccionar **Price (high to low)**. | Los artículos quedan ordenados del precio mayor al menor (`$49.99` a `$7.99`). | ✅ Pass |
| **TC-018** | Abrir detalle de producto y volver al inventario | Positivo | Estar en `/inventory.html` | 1. Hacer clic en el título o imagen de `Sauce Labs Bolt T-Shirt`.<br>2. Hacer clic en **Back to products**. | Abre `/inventory-item.html?id=...` con los datos del producto y el botón **Back to products** regresa a `/inventory.html`. | ✅ Pass |
| **TC-019** | Agregar y quitar productos desde la vista de inventario | Positivo | Estar en `/inventory.html` sin ítems en el carrito | 1. Hacer clic en **Add to cart** en dos productos.<br>2. Verificar el badge del carrito.<br>3. Hacer clic en **Remove** en uno de ellos. | El contador muestra `2` al agregar ambos y baja a `1` al quitar uno; el botón cambia a **Remove** / **Add to cart** según corresponda. | ✅ Pass |
| **TC-020** | Persistencia del ordenamiento al navegar al detalle y volver | Negativo | Estar en `/inventory.html` con filtro **Price (high to low)** aplicado | 1. Entrar al detalle de un producto.<br>2. Volver con **Back to products**. | *(Evaluar comportamiento)* Si el orden vuelve al valor por defecto (`A to Z`), documentar si se espera mantener el criterio previo o reiniciar la vista. | ⚠️ Revisar |
| **TC-021** | Imágenes e interacciones anómalas en `problem_user` | Negativo | Sesión iniciada con `problem_user` en `/inventory.html` | 1. Inspeccionar las imágenes de todos los productos.<br>2. Probar ordenamiento y botones **Add to cart** / **Remove**. | Se observan imágenes repetidas/incorrectas (`sl-404.jpg` o idénticas) y fallos al quitar ciertos productos del carrito. | ⚠️ Bug |
| **TC-022** | Acceso a detalle de producto con ID inexistente o inválido | Negativo | Sesión iniciada con `standard_user` | 1. Navegar manualmente a `/inventory-item.html?id=999` o `/inventory-item.html`. | Debe mostrar un estado controlado de "producto no encontrado" o redirigir de forma segura sin romper la interfaz. | ⚠️ Revisar |
