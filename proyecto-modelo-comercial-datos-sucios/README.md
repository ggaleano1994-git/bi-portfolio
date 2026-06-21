# Modelo Comercial desde Datos Sucios — Dashboard de Rentabilidad

## Contexto

Prueba técnica para un proceso de selección como Analista de Business Intelligence. El objetivo fue construir, desde cero, un modelo analítico completo a partir de datos de producción reales con errores de calidad intencionales, y entregar un dashboard comercial profesional de dos páginas.

> **Nota de confidencialidad:** no se publican los archivos de datos originales ni el nombre de la empresa evaluadora. Este repositorio documenta la metodología, las decisiones técnicas y los resultados agregados del ejercicio.

## Fuentes de datos

Cuatro archivos CSV de producción real:

| Archivo | Contenido |
|---|---|
| `ventas_order.csv` | Encabezado de cada venta: fecha, cliente, vendedor, forma de pago |
| `ventas_order_line.csv` | Detalle de productos por venta: cantidades, precios, IVA |
| `productos_raw.csv` | Catálogo de productos sin procesar, con errores de calidad intencionales |
| `clientes.csv` | Base de clientes: segmento (Básico, Estándar, Mayorista, Premium), provincia, antigüedad |

## Proceso

### 1. Auditoría de calidad de datos (Power Query)
Antes de transformar nada, se auditaron las cuatro tablas en busca de nulos, duplicados, tipos de datos incorrectos, inconsistencias de formato y valores atípicos. Principio de trabajo: **nunca asumir que los datos están limpios**.

### 2. Modelado dimensional
Diseño de un modelo en estrella: tabla de hechos de ventas vinculada a dimensiones de clientes, productos y calendario, evitando tablas anchas desnormalizadas.

### 3. Medidas DAX
Librería de medidas para rentabilidad, ticket promedio, evolución temporal y segmentación de clientes, priorizando medidas sobre columnas calculadas y un uso correcto de contexto de fila vs. contexto de filtro.

### 4. Dashboard (2 páginas)
- **Página 1 — Rentabilidad:** ventas, ganancia, margen y ticket promedio por categoría y segmento de cliente.
- **Página 2 — Análisis temporal y segmentación:** evolución de ventas en el tiempo y comportamiento por segmento de cliente.

## Resultados (datos agregados y validados contra el modelo)

| KPI | Valor |
|---|---|
| Ventas totales | $4.623.148.580 |
| Ganancia total | $36.206.681 |
| Cantidad de transacciones | 420 |
| Ticket promedio | $11.007.497 |
| Período analizado | Enero 2022 – Diciembre 2024 |

## Stack técnico

`Power BI Desktop` · `Power Query` · `DAX` · `Modelado dimensional (esquema estrella)`

## Capturas

![Vista ejecutiva](./capturas/Vista ejecutiva.png)
![Vista operativa](./capturas/Vista operativa.png)

