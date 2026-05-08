# Análisis de Ventas eCommerce — Febrero 2026

> EDA estructurado sobre **621 órdenes únicas** en 2 mercados (US, MX) y 6 categorías de producto. Incluye notebook técnico en Python y presentación ejecutiva en PowerPoint.

---

## Contexto

Análisis exploratorio de un dataset de órdenes de ecommerce de febrero 2026, enfocado en cuatro frentes: **calidad de datos, salud comercial, comportamiento por mercado y oportunidades de optimización operativa**. El entregable final es una presentación ejecutiva pensada para áreas comerciales y operativas.

## Objetivos

- Diagnosticar la calidad del dataset y documentar todas las decisiones de limpieza
- Calcular KPIs base de revenue, cancelaciones y tipo de fulfillment
- Comparar comportamiento entre mercados (US vs MX)
- Generar insights accionables para áreas comerciales y operativas

## Decisiones de calidad de datos

| # | Decisión | Justificación |
|---|---|---|
| 01 | Conversión MXN → USD ($20 MXN/USD) | Homologar ingresos para comparativos entre mercados; análisis por mercado mantiene moneda original |
| 02 | Exclusión de líneas con `quantity = 0` | 51 líneas con status "Shipped" interpretadas como cancelaciones/ajustes de inventario |
| 03 | Documentación de outliers en canal External | 2 órdenes con cantidades de 112 y 51 unidades identificadas como B2B/mayoreo, conservadas con flag |
| 04 | Revenue calculado como `unit_price × quantity` | Campos `tax` y `shipping_cost` con >70% de nulos; se omiten para mantener consistencia |

## Insights clave

| KPI | Valor | Comentario |
|---|---|---|
| Órdenes únicas | **621** | Sobre 722 líneas totales |
| Ingreso estimado (USD) | **~$16.6K** | Excluye líneas con qty=0 y sin precio |
| Cancelación MX | **10.9%** | vs 4.4% en US — gap de **6.5 pp** |
| Fulfillment Platform vs Seller | **75% / 25%** | Concentración alta en Platform |
| Envío Expedited vs Standard | **59% / 39%** | Preferencia clara por envío rápido |
| Líneas con `qty=0` | **7.1%** | Probables cancelaciones/ajustes |

**Hallazgo principal:** El mercado MX muestra una tasa de cancelación 2.5x mayor que US. Esto sugiere problemas de fulfillment, comunicación pre-venta o gestión de inventario específicos del mercado mexicano que merecen profundización.

## Entregables

| Archivo | Tipo |
|---|---|
| `Analisis_Ventas_Feb2026_CesarRabago.pptx` | Presentación ejecutiva (12 slides) |
| `Analisis_Ventas_Feb2026.ipynb` | Notebook con análisis técnico completo |
| `ecommerce_orders_feb2026.csv` | Dataset (si políticas de datos lo permiten) |

## Stack

Python · pandas · matplotlib · seaborn · PowerPoint

## Estructura del notebook

1. Carga y diagnóstico inicial
2. Calidad de datos (nulos, outliers, valores únicos)
3. Limpieza y normalización (conversión moneda, filtros)
4. Análisis por mercado (US vs MX)
5. Análisis por categoría y canal
6. Tendencia semanal (ISO week feb 2026)
7. Síntesis y recomendaciones

---

*César Rábago Pérez · Analista BI Jr · 2026*
