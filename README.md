# 🚀 Capa Silver: Procesamiento y Estructuración de Pedidos E-commerce

Este repositorio contiene la arquitectura y la lógica de procesamiento para transformar datos de pedidos de una tienda virtual (**WooCommerce**) desde su estado crudo en la **Capa Bronze** hacia una estructura analítica optimizada en la **Capa Silver**.



## 📌 Descripción del Proyecto
El corazón de este proyecto es la conversión de archivos **JSON** semi-estructurados en tablas **Delta** de alto rendimiento. El desafío técnico principal que resolvemos aquí es el **aplanamiento (flattening)** de la entidad de pedidos, permitiendo que cada producto vendido sea una unidad de análisis independiente sin perder la relación con la orden original.

## 🛠️ Stack Tecnológico
* **Procesamiento:** PySpark (Apache Spark).
* **Plataforma:** Azure Databricks / Databricks Free Edition
* **Formato de Tabla:** Delta Lake (soporta ACID y Time Travel).
* **Ingesta Previa:** Azure Data Factory (ADF).

---

## 💡 Consideraciones Técnicas de Ingeniería
Para lograr una capa Silver de nivel profesional, el notebook implementa:

1. **Manejo de Jerarquías Complejas:** Uso estratégico de la función `explode` para desglosar el arreglo `line_items`, transformando listas anidadas en filas relacionales.
2. **Esquema Estricto (Schema Enforcement):** Implementación de `StructType` para garantizar que la ingesta sea robusta y no falle ante cambios inesperados en la API de origen.
3. **Tipado de Datos Avanzado:** - Conversión de fechas ISO a **Timestamp** real mediante `to_timestamp`.
   - Casteo de montos financieros de `String` a `Double` para permitir agregaciones precisas.
4. **Optimización Delta:** Persistencia de datos en tablas Delta, lo que permite consultas SQL ultra rápidas y una integración nativa con herramientas de BI.

---

## 🆓 Reproducibilidad: Laboratorio 100% Gratis
He diseñado este código para que sea **completamente ejecutable en el entorno gratuito** de Databricks, facilitando el aprendizaje y la experimentación:

* **Databricks Free Edition:** Puedes importar el archivo `.ipynb` directamente en tu cuenta gratuita.
* **Carga de Datos Directa:** No requieres una suscripción de Azure paga; puedes cargar el archivo JSON de ejemplo directamente en los **Volumes** de Databricks.
* **Sin Dependencias Externas:** El código es autónomo y está listo para correr "out of the box".

---

## 📈 Impacto en el Negocio (Data-Driven Insights)
La estructuración de la Capa Silver no es solo un paso técnico; es lo que habilita:
* **Análisis de Ventas:** Comparativas mensuales de ingresos y crecimiento.
* **Optimización de Experiencia de Compra:** Identificación de productos que impulsan la conversión.
* **Customer Intelligence:** Preparación de la matriz necesaria para entrenar **Modelos de Recomendación** y segmentación de clientes.

---

## 📂 Estructura del Repositorio
* `/notebooks`: Contiene el notebook de Databricks en formato `.ipynb` o `.py`.
* `/data_sample`: Archivo JSON de ejemplo con la estructura oficial de WooCommerce.
* `LICENSE`: Licencia MIT para uso libre de la comunidad.

---
**¿Quieres llevar tu nogocio al siguiente nivel con datos?** Este proyecto es una muestra de cómo una arquitectura sólida permite escalar de simples reportes a estrategias de crecimiento basadas en evidencia. ¡Contáctame para conversar!
