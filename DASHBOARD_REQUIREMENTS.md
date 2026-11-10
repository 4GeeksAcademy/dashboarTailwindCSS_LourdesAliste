# Requisitos del dashboard de rendimiento de afiliación

## Propósito y alcance

Dashboard frontend para que una influencer analice comisiones, ventas, conversión, engagement y rendimiento de campañas en Instagram, TikTok y YouTube. Se usarán datos ficticios coherentes para la representación visual. No se implementarán backend, persistencia ni integraciones reales con redes sociales.

Este documento recoge los requisitos funcionales y los datos aportados; no define el layout definitivo. Se indicó conservar tarjetas KPI, gráficos de barras, tablas, paneles blancos, navegación lateral y jerarquía visual clara. La imagen de referencia no pudo inspeccionarse visualmente en esta sesión, por lo que no se infieren de ella otros componentes o estilos.

La implementación actual es HTML estático: los valores y comparaciones demo se muestran precomputados. Las fórmulas documentadas definen los resultados esperados, pero no se ejecutan en tiempo de ejecución. La restricción de proyecto prohíbe JavaScript; los cálculos dinámicos, filtros y estados dinámicos siguen pendientes.

## Requisitos funcionales

### Bloque superior: cuatro KPIs

| Indicador | Valor de ejemplo | Significado |
|---|---:|---|
| Comisiones generadas | 1.530 € | Ganancia de la influencer por comisiones |
| Unidades vendidas | 150 | Unidades, no ingresos monetarios |
| Tasa de conversión | 2,8 % | Compras completadas desde enlace afiliado / clics únicos × 100 |
| Engagement rate | 6,7 % | (likes + comentarios + compartidos + guardados) / alcance × 100 |

Los cuatro valores son resultados demo precomputados a partir de las entradas ficticias descritas en la SPEC de plataformas. Los 1.530 € y 150 unidades son sumas de las muestras de plataforma. Las tasas corresponden a sus fórmulas confirmadas y no representan datos reales; el HTML no las calcula en tiempo de ejecución.

### Bloque intermedio: drivers

**Rendimiento por plataforma.** Comparar alcance, unidades vendidas y comisiones con barras horizontales. La participación sigue la fórmula comisión de plataforma / total de comisiones × 100, redondeada solo al final a un decimal. Las tasas de conversión y engagement siguen las fórmulas confirmadas en la SPEC de plataformas. La vista estática presenta resultados demo precomputados; no ejecuta estas operaciones.

| Plataforma | Alcance | Unidades vendidas | Comisiones | Participación calculada en comisiones |
|---|---:|---:|---:|---:|
| Instagram | 25.000 | 45 | 405 € | 26,5 % |
| TikTok | 18.000 | 60 | 720 € | 47,1 % |
| YouTube | 12.000 | 45 | 405 € | 26,5 % |
| **Total** | **55.000** | **150** | **1.530 €** | **100,1 % visible** |

**Rendimiento por producto.** Distinguir unidades vendidas e ingresos por ventas en columnas separadas. Mostrar precio, ingresos y comisión. El engagement rate solo podrá mostrarse si se definen su fórmula, datos de entrada y atribución al producto.

| Producto | Precio unitario | Unidades | Ingresos por ventas | Comisión |
|---|---:|---:|---:|---:|
| A | 50 € | 50 | 2.500 € | 375 € |
| B | 120 € | 40 | 4.800 € | 720 € |
| C | 80 € | 60 | 4.800 € | 720 € |
| **Total** | — | **150** | **12.100 €** | **1.815 €** |

Esta tabla es un ejemplo independiente de los valores de las tarjetas KPI y de la tabla de plataformas; no debe forzarse a coincidir con los 1.530 € de comisión superiores.

### Bloque inferior: detalles operacionales

**Rendimiento de campañas.** Mostrar campaña, plataforma, producto, alcance, conversiones y comisiones. Costes, ingresos atribuibles y ROI/ROAS solo cuando los datos y la fórmula estén definidos.

| Campaña | Plataforma | Producto | Alcance | Conversiones | Comisiones |
|---|---|---|---:|---:|---:|
| Campaña 1 | Instagram | A | 10.000 | 20 | 150 € |
| Campaña 2 | TikTok | B | 8.000 | 25 | 450 € |
| Campaña 3 | YouTube | C | 6.000 | 15 | 180 € |

Como cálculo aritmético hipotético usando conversiones / alcance, las tasas de estas filas serían 0,20 %, 0,31 % y 0,25 %, respectivamente. Esto no define una tasa de conversión para campañas: las muestras de campaña son independientes y no se debe asumir que conversión equivale a unidad vendida.

**Comparativa por plataforma.** Comparar Instagram, TikTok y YouTube con variaciones frente al periodo contiguo anterior de igual duración: ((actual − anterior) / anterior) × 100. Si el anterior es cero, mostrar «Sin referencia»; si faltan entradas, «Sin datos». Los clics tienen origen único y no equivalen a compras. Las compras e interacciones de la simulación permiten calcular las tasas acordadas; la variación se distingue con signo y texto, no solo con color.

| Indicador | Instagram | TikTok | YouTube |
|---|---:|---:|---:|
| Variación de alcance | +19,0 % | +20,0 % | +9,1 % |
| Conversion Rate | 2,5 % | 3,4 % | 2,0 % |
| Engagement Rate | 6,5 % | 8,2 % | 4,8 % |

Las entradas actuales y anteriores, los clics y los conteos de interacciones son datos demostrativos ficticios detallados en la SPEC de plataformas. Las comparaciones y tasas visibles en el HTML son resultados precomputados, no cálculos de ejecución.

## Decisiones de negocio confirmadas

- Productos y precios: A = 50 €, B = 120 €, C = 80 €.
- Comisión de la influencer: 15 % del ingreso por ventas de cada producto. Las comisiones unitarias son A = 7,50 €, B = 18 € y C = 12 €.
- Ingresos por ventas y comisiones son magnitudes distintas. No presentar el ingreso bruto como ganancia de la influencer.
- Fórmulas confirmadas:
  - Ingresos por ventas = unidades vendidas × precio unitario.
  - Comisión = ingresos por ventas × 15 %.
- El periodo funcional del dashboard es 2026–actualidad.
- Conversion Rate = compras completadas desde enlace afiliado / clics únicos × 100. Engagement Rate = (likes + comentarios + compartidos + guardados) / alcance × 100; las visualizaciones se excluyen. Ambas tasas se redondean a un decimal.
- El ROI solo puede calcularse si están disponibles ingresos atribuibles y costes; el tratamiento exacto de ROI/ROAS sigue pendiente.
- Los datos actuales de plataforma suman 150 unidades, 55.000 de alcance, 1.530 € en comisiones, 3.900 clics y 109 compras completadas desde enlaces. El alcance se presenta como suma, no como audiencia única. Las participaciones visibles pueden sumar 100,1 % al redondear cada plataforma a un decimal.
- Los ejemplos de producto son explícitamente independientes de los KPI, las plataformas y las campañas; no se reconcilian con esos conjuntos.
- Los valores ilustrativos de unidades y comisiones por plataforma se mantienen independientes de los conjuntos de producto y campaña; no se concilian ni se presentan como atribución multi-touch. No se derivan ingresos atribuibles a partir de ellos.
- Las filas ilustrativas de campaña se mantienen como muestras independientes; sus etiquetas de plataforma y producto no establecen atribución ni reconciliación con otros conjuntos.
- Las demás relaciones y atribuciones entre conjuntos de datos no deben asumirse si no se confirman.
- No hay datos reales ni conexión a cuentas de redes sociales.

## Comprobaciones y cautelas sobre los ejemplos

- Conversion Rate total = 109 compras / 3.900 clics = 2,8 %. Engagement Rate total = 3.677 interacciones / 55.000 de alcance = 6,7 %.
- Las comisiones de las campañas coinciden con el 15 % del precio del producto multiplicado por sus conversiones, si cada conversión representa una venta unitaria. Esa equivalencia aún no está confirmada.
- Los valores actuales y anteriores, clics e interacciones son entradas ficticias suministradas para probar fórmulas. El periodo funcional general sigue siendo 2026–actualidad; los dos periodos de la simulación tienen 30 días y son contiguos.
- No calcular costes, ingresos atribuibles, ROI o ROAS a partir de datos ausentes.

## Cuestiones pendientes de validación

1. **Datos reales:** no hay integraciones ni entradas de redes reales; las fórmulas se aplican solo a la simulación.
2. **Audiencia única:** fuente y método para deduplicar alcance entre plataformas siguen fuera de alcance.
3. **Atribución a campañas y productos:** las muestras de plataforma, producto y campaña se mantienen independientes; la simulación de compras por enlaces no concilia sus ingresos ni unidades.
4. **Alcance de campañas y costes:** si las campañas listadas son el conjunto completo o una muestra; costes e ingresos atribuibles por campaña.
5. **Definición y cálculo de ROI/ROAS:** confirmar si se desea ROAS (ingresos atribuibles / costes × 100) o ROI convencional ((ingresos atribuibles - costes) / costes × 100), qué costes se incluyen y cómo tratar costes cero o ausentes.
