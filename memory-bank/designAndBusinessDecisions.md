# Decisiones de diseño y negocio

## Decisiones confirmadas

- Productos: A = 50 €, B = 120 €, C = 80 €.
- Comisión de la influencer: 15 % del ingreso por ventas; comisión unitaria: A = 7,50 €, B = 18 €, C = 12 €.
- Ingresos por ventas y comisiones son importes distintos.
- Fórmulas confirmadas: ingresos por ventas = unidades × precio; comisión = ingresos por ventas × 15 %.
- En el bloque KPI, 1.530 € es un valor ilustrativo confirmado por la suma de las comisiones de Instagram (405 €), TikTok (720 €) y YouTube (405 €). Las cifras de la tabla de productos, que suma 1.815 €, son un ejemplo independiente.
- Las unidades y comisiones ilustrativas por plataforma se mantienen como muestras independientes de los datos de productos y campañas; no se reconcilian ni se les aplica atribución multi-touch.
- El alcance agregado de plataforma se representa como suma aritmética informada (55.000), no como audiencia única. La participación es comisión de plataforma / total × 100, redondeada al final a un decimal; el total visible puede sumar 100,1 %.
- Comparaciones: ((actual − anterior) / anterior) × 100 sobre periodos contiguos de igual duración; anterior cero = «Sin referencia», datos ausentes = «Sin datos».
- Clics: evento único atribuido al origen de su enlace; se suman por plataforma y no se confunden con compras o ventas.
- Conversion Rate: compras completadas desde enlace / clics × 100. Engagement Rate: (likes + comentarios + compartidos + guardados) / alcance × 100; views se excluyen. Tasas redondeadas al final a un decimal, denominador cero = «No calculable», entradas ausentes = «Sin datos».
- Las entradas para esas métricas son ficticias; no hay integraciones ni datos reales.
- Los ejemplos de producto se mantienen independientes de KPI, plataformas y campañas; no se les aplica atribución multi-touch ni se reconcilian con esas vistas.
- Las filas de campaña son muestras independientes; sus etiquetas de plataforma y producto no implican atribución ni reconciliación con otras vistas.
- Top Affiliate Products se ordena por Revenue y luego Conversion Rate descendentes, hasta tres filas. Inputs demo por producto: A 300 clics/15 compras, B 1.000/30, C 900/45. Los empates restantes conservan el orden de origen.
- Solo Top Affiliate Products tiene filtros combinables por plataforma y categoría. Las facetas son datos demo, no atribución de ventas. Sin coincidencias: «No hay resultados para los filtros seleccionados» sin filas ni acciones.
- Estados métricos aprobados: datos ausentes = «Sin datos»; parciales = valor con «Datos parciales»; cero expreso = 0; tasas calculadas sin denominador válido = «No calculable», nunca 0 %. En la implementación actual, resultados demo precomputados aparecen estáticamente; no se ejecutan estados dinámicos.
- Listados filtrados vacíos: para Top Affiliate Products, mostrar «No hay resultados para los filtros seleccionados», sin filas ficticias ni acciones adicionales. T42 queda pendiente y el HTML actual no expone filtros.
- Los paneles de plataforma y producto se apilan en móvil/tablet y usan dos columnas desde `lg`; campañas y comparativa permanecen en secciones separadas. Los detalles visuales finos siguen pendientes.
- Los valores de demostración son ficticios y no representan datos reales.
- La referencia de diseño se describió textualmente como tarjetas KPI, gráficos de barras horizontales, tablas, paneles blancos, navegación lateral y jerarquía visual clara. La imagen no se inspeccionó visualmente; no inferir otros rasgos ni fijar el layout definitivo.

## Pendiente

Siguen fuera de alcance los datos reales, la deduplicación de audiencia y la atribución entre muestras de plataforma, producto y campaña. Las fórmulas y entradas demo vigentes están en las SPEC de KPI, plataformas, producto y filtros; las fórmulas no se ejecutan en el HTML estático.
