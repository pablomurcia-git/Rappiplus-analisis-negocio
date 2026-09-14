# 📦 RappiPlus: de datos a decisiones de negocio

Análisis end-to-end del desempeño del servicio **RappiPlus** (rentabilidad, comportamiento de usuarios y un experimento A/B) para apoyar decisiones de negocio basadas en datos. Proyecto desarrollado durante el bootcamp de Data Analytics de TripleTen.

## 🎯 Objetivo

Responder, con datos, si el negocio es rentable, dónde se pierden los usuarios en el proceso de compra, si regresan después de su primera compra, y si un cambio de UI en el checkout mejora la conversión.

## 🗂️ Datos

- `rappiplus_orders_raw.csv` — pedidos, precios, descuentos y revenue
- `rappiplus_catalog.csv` — costos de productos, categorías y proveedores
- `rappiplus_marketing_spend.csv` — inversión en marketing por canal y país
- Tablas `events`, `users`, `user_activity` (PostgreSQL) — comportamiento del usuario en la plataforma
- `experiment_checkout_ui.csv` — resultados de un experimento A/B en el checkout

## 🛠️ Herramientas

Python (pandas, matplotlib), SQL (PostgreSQL vía SQLAlchemy), pruebas estadísticas (SciPy / statsmodels) y un dashboard en Power BI / Tableau para comunicar resultados.

## 🔍 Metodología

1. **Calidad de datos** — limpieza y validación de los tres datasets (nulos, duplicados, formatos).
2. **Rentabilidad** — cálculo de revenue, costos, profit y margen, general y por categoría de producto.
3. **Funnel de conversión** (SQL) — seguimiento acumulado de usuarios desde `first_visit` hasta `purchase`.
4. **Retención por cohortes** (SQL) — ¿los usuarios regresan después de su primera compra?
5. **Experimento A/B** — prueba de proporciones sobre la tasa de conversión de un cambio en el checkout.
6. **Dashboard** — visualización ejecutiva de todos los hallazgos anteriores.

## 📊 Hallazgos clave

- El negocio genera **$6.08M de profit** (margen de **11.73%** sobre el ingreso).
- **Electrónica** concentra el mayor volumen y profit absoluto, pero con el margen más bajo (10.79%); **Hogar** (62.54%) y **Moda** (59.23%) son mucho más rentables por unidad vendida.
- De 7,796 usuarios que visitan el sitio, solo el **49.47%** completa una compra. Las mayores fugas del funnel ocurren en `begin_checkout → add_payment_info` (-21.95%) y `add_payment_info → purchase` (-22.35%).
- El experimento A/B sobre el checkout **no mostró una mejora estadísticamente significativa** en conversión (p = 0.416), por lo que no se recomienda escalarlo tal como está.

## 💡 Recomendación de negocio

Priorizar la reducción de fricción en las etapas finales del checkout (pago y confirmación) antes de invertir en más tráfico, y usar ese tráfico ya convertido para impulsar categorías de mayor margen (Hogar y Moda) sin sacrificar el volumen que aporta Electrónica.

## 📁 Contenido

- [`analisis_rappiplus.ipynb`](./analisis_rappiplus.ipynb) — notebook completo con limpieza, análisis, SQL y pruebas estadísticas.
- Dashboard: enlace incluido al final del notebook.

---
