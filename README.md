# Transformación y Modelado de Datos en Power BI

## Autor

Matias Gomez

## Descripción

En esta práctica se trabajó con un archivo de ventas exportado desde un sistema legacy utilizando Power BI Desktop. El objetivo fue preparar los datos para su análisis mediante tareas de limpieza, transformación y normalización en Power Query, obteniendo un modelo relacional organizado y listo para construir reportes.

---

## Archivos del proyecto

- **Ventas_export_legacy.xlsx:** archivo de origen con los datos exportados del sistema legacy.
- **ventas_export_legacy.pbix:** proyecto de Power BI con las transformaciones realizadas y el modelo relacional final.

---

## Transformaciones realizadas

Las transformaciones se realizaron en el siguiente orden:

1. Importación del archivo Excel en Power BI Desktop.
2. Renombrado de las columnas utilizando nombres descriptivos.
3. Corrección de los tipos de datos.
4. Eliminación de registros duplicados.
5. Limpieza de espacios en blanco y caracteres innecesarios mediante las funciones **Trim** y **Clean**.
6. Normalización de la información separando los datos en distintas tablas.
7. Creación del modelo relacional.

---

## Tipos de datos utilizados

Se asignó un tipo de dato adecuado a cada columna para garantizar un correcto funcionamiento del modelo de datos.

| Tipo de dato | Columnas |
|--------------|----------|
| Texto | id_operacion, id_cliente, nombre_cliente, email, telefono, ciudad, provincia, segmento, cliente_activo, producto, categoria, moneda, canal_venta |
| Fecha | fecha_alta_cliente, fecha_venta |
| Número entero | id_producto, cantidad |
| Número decimal | precio_unitario, descuento |
| Moneda | total_venta |

La correcta asignación de los tipos de datos permite realizar filtros, cálculos y relaciones de manera eficiente dentro de Power BI.

---

## Tratamiento de valores nulos y duplicados

Se revisó la existencia de registros duplicados y se eliminaron aquellos que podían generar inconsistencias en el análisis.

Respecto a los valores nulos, se identificó que la columna **descuento** contenía algunos registros sin información. En esta práctica se decidió mantener dichos valores nulos, ya que representan la ausencia de un descuento registrado y no afectan la estructura del modelo de datos. En un escenario de negocio, la decisión de reemplazarlos por un valor como **0** dependería de las reglas definidas por la organización.

También se limpiaron espacios innecesarios en los campos de texto utilizando las funciones **Trim** y **Clean**, con el objetivo de mantener la consistencia de la información.

---

## Normalización de los datos

Para reducir la redundancia y mejorar la organización del modelo, la información fue dividida en tres tablas.

### D_clientes

Contiene la información de cada cliente.

- id_cliente
- nombre_cliente
- email
- telefono
- ciudad
- provincia
- segmento
- cliente_activo
- fecha_alta_cliente

### D_productos

Contiene la información de los productos.

- id_producto
- producto
- categoria
- precio_unitario

### F_Ventas

Contiene las transacciones de venta.

- id_operacion
- id_cliente
- id_producto
- fecha_venta
- cantidad
- descuento
- total_venta
- moneda
- canal_venta

---

## Modelo relacional

Se implementó un esquema estrella compuesto por dos tablas de dimensiones (**D_clientes** y **D_productos**) y una tabla de hechos (**F_Ventas**).

Relaciones creadas:

- **D_clientes[id_cliente] → F_Ventas[id_cliente]**
- **D_productos[id_producto] → F_Ventas[id_producto]**

Esta estructura reduce la redundancia de datos, facilita el mantenimiento del modelo y mejora el rendimiento de las consultas y visualizaciones.

---

## Conclusión

Luego de las transformaciones realizadas, el conjunto de datos quedó preparado para su utilización en Power BI.

La información fue limpiada, normalizada y organizada en un modelo relacional que permite construir visualizaciones y análisis de manera eficiente, manteniendo una estructura clara y escalable para futuros desarrollos.
