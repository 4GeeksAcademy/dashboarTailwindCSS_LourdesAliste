## 1. Objetivo y alcance

Resumir el rendimiento de afiliación mediante cuatro indicadores principales: comisiones generadas, unidades vendidas, tasa de conversión y engagement rate. El bloque debe distinguir las comisiones de la influencer de los ingresos brutos por ventas.

El periodo funcional es 2026–actualidad. Los valores disponibles son datos ficticios de ejemplo, no datos reales ni sincronizados con plataformas. El alcance se limita a estos cuatro KPI; no define filtros, comparativas temporales ni interacciones con las tarjetas.

## 2. Requisitos funcionales

Mostrar los siguientes indicadores y los valores de ejemplo proporcionados:

| Indicador | Valor de ejemplo | Significado |
|---|---:|---|
| Comisiones generadas | 1.530 € | Comisión de la influencer |
| Ventas generadas | 150 | Unidades vendidas, no importe monetario |
| Tasa de conversión | 2,8 % | Compras completadas desde enlace afiliado / clics únicos × 100 |
| Engagement rate | 6,7 % | (likes + comentarios + compartidos + guardados) / alcance × 100 |

Los cuatro valores son resultados demo precomputados a partir de las entradas ficticias definidas en la SPEC de plataformas. El HTML los muestra estáticamente; no ejecuta las fórmulas en tiempo de ejecución. Las comisiones (1.530 €) y unidades (150) son sumas de esa muestra; las tasas siguen las fórmulas aprobadas y no representan datos reales.

## 3. Datos de entrada necesarios

- **Comisiones generadas:** ingresos por ventas atribuibles y porcentaje de comisión, o un total de comisiones ya calculado. Para recalcularlas desde unidades se necesita la distribución de unidades por producto, dado que los precios varían.
- **Ventas generadas:** cantidad de unidades vendidas. El ejemplo informado es 150.
- **Tasa de conversión:** compras completadas desde enlace afiliado / clics únicos × 100. Las compras son eventos separados de unidades vendidas.
- **Engagement rate:** (likes + comentarios + compartidos + guardados) / alcance × 100. Views se excluyen del numerador.

El periodo del bloque es 2026–actualidad. Se proporcionan alcances por plataforma, pero no está definido si ni cómo deben agregarse para estos KPI.

## 4. Reglas de negocio y fórmulas

- El porcentaje de comisión de los ejemplos es 15 %.
- Los precios unitarios son: producto A, 50 €; producto B, 120 €; producto C, 80 €.
- Ingresos por ventas = unidades vendidas × precio unitario.
- Comisión = ingresos por ventas × 15 %.
- Las comisiones no son equivalentes a los ingresos brutos por ventas.
- Redondear las tasas al final a un decimal. Sin clics o alcance (denominador cero), mostrar «No calculable»; con entradas ausentes, «Sin datos».
- El alcance agregado de plataformas es la suma informada (55.000), no audiencia única; no se deduplican personas.
- No asignar un valor calculado si faltan los datos necesarios.

## 5. Comportamiento esperado

- Presentar los cuatro KPI con sus valores derivados: 1.530 €, 150 unidades, 2,8 % y 6,7 %.
- Mostrar las comisiones en euros, las tasas como porcentajes y las ventas como unidades.
- Identificar los valores como simulación, no como datos reales. No asumir que las unidades vendidas equivalen a compras completadas desde enlace.
- Mantener separados los datos del KPI de comisiones y los de la tabla de productos: se indicó que son ejemplos independientes. La tabla de productos suma 1.815 € de comisión y no debe sustituir los 1.530 € del KPI.

## 6. Estados y casos especiales

- Política aprobada para estados visibles: dato ausente = «Sin datos»; dato parcial = valor acompañado de «Datos parciales»; cero expresamente informado = 0.
- Una tasa con denominador cero se representa como «No calculable», nunca como 0 %; entradas ausentes producen «Sin datos».
- En la simulación actual se muestran resultados precomputados con entradas completas. Los estados de cero y datos ausentes están especificados, pero no se ejecutan ni se verifican en el HTML estático.
- Conversion Rate total = 109 compras / 3.900 clics = 2,8 %; Engagement Rate total = 3.677 interacciones / 55.000 de alcance = 6,7 %.
- La suma de comisiones por plataforma es 405 € + 720 € + 405 € = 1.530 €. La tabla de productos suma 1.815 € y es un ejemplo independiente confirmado; no debe forzarse la igualdad entre ambos conjuntos.

## 7. Criterios de aceptación

- Se identifican los cuatro KPI: comisiones generadas, unidades vendidas, tasa de conversión y engagement rate.
- Los valores derivados de la simulación son 1.530 €, 150 unidades, 2,8 % y 6,7 %, respectivamente.
- Se indica que el periodo es 2026–actualidad.
- Las ventas se expresan como unidades y no se confunden con ingresos monetarios.
- Las comisiones se distinguen de los ingresos brutos por ventas.
- Los 1.530 € se identifican como valor ilustrativo confirmado por la suma de las comisiones por plataforma.
- Las tasas se derivan con las fórmulas aprobadas y las entradas ficticias de la SPEC de plataformas.
- No se asignan resultados calculados cuando faltan datos de entrada.
- Los datos de producto, expresamente independientes, no se usan para reemplazar el KPI de comisiones.

## Estado de implementación

El HTML presenta los cuatro resultados demo de forma estática. No hay cálculos en tiempo de ejecución ni renderizado dinámico de estados; T33, T34 y T41 permanecen pendientes según [tasks.md](../../tasks.md).

## 8. Cuestiones pendientes

- **Conversión:** definir qué evento cuenta como conversión, si equivale a una venta o unidad, y la fórmula funcional del KPI. No se confirma su equivalencia con unidades vendidas.
- **Datos reales:** no hay integraciones con plataformas; los resultados actuales son demostrativos.
- **Audiencia única:** fuente y método para deduplicar personas entre plataformas siguen fuera de alcance.
- **Atribución:** no se atribuyen los datos simulados a campañas/productos ni se reconcilian las muestras independientes.
- **Precisión:** definir el redondeo de porcentajes y valores monetarios.
