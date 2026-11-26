# 🧪 QA Portfolio - SauceDemo

Portafolio de aseguramiento de calidad (QA Manual y Automatizado) basado en pruebas funcionales sobre la plataforma de comercio electrónico **SauceDemo**.

## 🎯 Aplicación Bajo Prueba (AUT)
* **Sitio web:** [SauceDemo (Swag Labs)](https://www.saucedemo.com/)
* **Descripción:** Aplicación web de demostración que simula una tienda en línea, diseñada para validar flujos críticos de usuario y detectar comportamientos anómalos mediante distintos perfiles de prueba.

## 📋 Alcance Funcional
Las pruebas cubren los siguientes módulos y flujos principales:
* **Login:** Validación de credenciales válidas, manejo de errores con usuarios bloqueados o inválidos y restricciones de acceso.
* **Inventario:** Visualización de catálogo, ordenamiento de productos (por nombre y precio) y vista de detalle de artículos.
* **Carrito de Compras:** Agregar y eliminar productos, persistencia de ítems y validación del contador del carrito.
* **Proceso de Compra (Checkout):** Ingreso de datos de envío, validación de campos obligatorios, resumen de orden, cálculo de totales y confirmación de compra.

## 🛠️ Herramientas Utilizadas
* **Gestión y Diseño de Pruebas:** Excel / Google Sheets (Matrices de prueba y reporte de defectos)
* **Automatización Web:** Playwright / Selenium WebDriver
* **Control de Versiones:** Git & GitHub
* **Inspección y Debugging:** Chrome DevTools

## 📂 Estructura del Repositorio
* 📋 **[Plan de Pruebas](./docs/test-plan.md):** Alcance funcional, exclusiones, navegadores y resoluciones evaluadas.
* 📝 **[Casos de Prueba](./casos-de-prueba):** Matrices de prueba, escenarios positivos/negativos y criterios de aceptación.
* 🐞 **[Reporte de Bugs](./bugs):** Registro detallado de defectos encontrados, pasos para reproducir, severidad y evidencias.
* 🤖 **[Automatización](./automatizacion):** Scripts de pruebas automatizadas end-to-end (E2E) y configuración del proyecto.
