# Rendimiento por plataforma

## Objetivo

Permitir comparar el rendimiento de afiliación de las plataformas incluidas en los ejemplos del proyecto, distinguiendo alcance, unidades vendidas y comisiones.

## Usuario

Influencer que revisa el rendimiento de sus actividades de afiliación por plataforma.

## Historia de usuario

Como influencer, quiero comparar los resultados de mis plataformas para identificar dónde se concentran el alcance, las unidades vendidas y las comisiones.

## Requisitos funcionales

### Confirmados

- Comparar Instagram, TikTok y YouTube.
- Mostrar por plataforma el alcance, las unidades vendidas y las comisiones.
- Comparar comisiones mediante barras horizontales e identificar plataforma e importe.
- Calcular participación sobre comisiones como comisión de plataforma / total de comisiones × 100, usando importes originales y redondeando solo el resultado a un decimal. Si el total es cero, mostrar «Sin datos».
- Comparar cada métrica de plataforma con el periodo inmediatamente anterior de igual duración: ((valor actual − valor anterior) / valor anterior) × 100. Si el valor anterior es cero, mostrar «Sin referencia»; si falta un valor de cualquiera de los periodos, mostrar «Sin datos».
- La comparativa inferior presenta las métricas por plataforma y sus valores actuales, anteriores y variación. El signo y el texto distinguen aumentos y descensos, sin depender únicamente del color.
- En esta simulación, el alcance agregado es la suma aritmética de los valores informados (55.000); debe etiquetarse como suma, no como audiencia única.
- Cada evento de clic se atribuye al origen único del enlace afiliado, se cuenta una sola vez y el total es la suma de eventos atribuidos a Instagram, TikTok y YouTube. Los clics no son conversiones ni ventas.
- Una conversión es una compra completada procedente de un enlace afiliado. Conversion Rate = conversiones / clics × 100, redondeado a un decimal; con cero clics, mostrar «No calculable»; con entradas ausentes, «Sin datos».
- Engagement Rate = (likes + comentarios + compartidos + guardados) / alcance × 100, redondeado a un decimal. Las visualizaciones no son interacciones; con alcance cero, mostrar «No calculable»; con componentes ausentes, «Sin datos».
- El periodo del dashboard es 2026–actualidad.

### Datos ilustrativos, no reales ni normativos

| Plataforma | Alcance | Unidades vendidas | Comisiones |
|---|---:|---:|---:|
| Instagram | 25.000 | 45 | 405 € |
| TikTok | 18.000 | 60 | 720 € |
| YouTube | 12.000 | 45 | 405 € |
| **Suma informada** | **55.000** | **150** | **1.530 €** |

Los valores históricos de variación (+18 %, +32 %, −2 %) se reemplazan por comparaciones derivadas de la muestra temporal descrita abajo. Los clics y tasas de engagement anteriores se conservan únicamente como referencia de origen y no se usan como resultados: clics, conversiones e interacciones se derivan de las entradas ficticias documentadas.

Las participaciones calculadas con los importes originales son 26,5 %, 47,1 % y 26,5 %. Su suma visible es 100,1 % por redondeo a un decimal; no se fuerza a 100 %.

### Entradas y resultados de demostración

Los datos actuales y anteriores siguientes son entradas ficticias para probar las fórmulas; no son eventos reales. Cada periodo dura 30 días y es contiguo: actual, 2026-10-12 a 2026-11-10; anterior, 2026-09-12 a 2026-10-11.

- Instagram: alcance 25.000 / 21.000; unidades 45 / 39; comisiones 405 € / 351 €; clics únicos 1.200 / 1.000; compras completadas desde enlace 30 / 24; interacciones actuales (1.200 likes, 200 comentarios, 125 compartidos, 100 guardados); anteriores (1.000, 170, 100, 95).
- TikTok: alcance 18.000 / 15.000; unidades 60 / 53; comisiones 720 € / 636 €; clics únicos 1.800 / 1.500; compras completadas desde enlace 61 / 48; interacciones actuales (1.100 likes, 190 comentarios, 96 compartidos, 90 guardados); anteriores (900, 150, 80, 70).
- YouTube: alcance 12.000 / 11.000; unidades 45 / 40; comisiones 405 € / 360 €; clics únicos 900 / 1.000; compras completadas desde enlace 18 / 20; interacciones actuales (400 likes, 80 comentarios, 56 compartidos, 40 guardados); anteriores (360, 80, 48, 40).
- Resultados derivados actuales: clics 3.900; conversiones 109; Conversion Rate total 2,8 %; Engagement Rate total 6,7 %. Las tasas por plataforma se derivan de sus propios conteos y alcance. No se redondean los datos de entrada antes de calcular.
- La variación se calcula con los valores originales; su presentación visual usa un decimal. Este formato no altera los valores usados en las fórmulas.

### Datos y reglas pendientes

- Los antiguos valores +18 %, +32 % y −2 % no tenían una métrica asociada; se sustituyen por variaciones derivadas de las entradas ilustrativas por métrica.
- No se proporciona una medida de audiencia única ni se deduplican personas en la suma de alcance. Si se requiere alcance único en el futuro, quedan pendientes su fuente y método.
- Decisión confirmada: las unidades y comisiones de los ejemplos por plataforma se mantienen como muestras ilustrativas independientes de los conjuntos de productos y campañas. No se reconcilian ni se presentan como atribución multi-touch calculada; tampoco se derivan ingresos atribuibles de estas cifras.
- No se conectan cuentas o fuentes reales. Las entradas de demostración permiten verificar comportamiento, pero no representan rendimiento real.
- La atribución de ventas entre campañas, productos y plataformas no se deduce de los conteos de clics o conversiones de esta simulación.

## Criterios de aceptación

1. La comparación identifica Instagram, TikTok y YouTube, separa alcance, unidades y comisiones, y diferencia entradas ilustrativas de resultados derivados.
2. Las participaciones se calculan sobre importes originales, se redondean a un decimal y pueden sumar 100,1 %.
3. Las variaciones usan periodos contiguos de igual duración y la fórmula aprobada; cero anterior y datos ausentes producen sus estados definidos.
4. El total de 55.000 se etiqueta como suma informada, no como audiencia única.
5. Los clics se cuentan una vez y por origen único; el total es la suma de las tres plataformas y no se confunde con conversiones o ventas.
6. Conversion Rate y Engagement Rate aplican sus fórmulas, precisión y estados; visualizaciones no se suman como interacciones.

## Fuera de alcance

- Datos reales sincronizados desde redes sociales.
- Deducir alcance único, reglas de atribución, conversión o engagement a partir de los ejemplos.
- Definir por cuenta propia las comparativas temporales o el redondeo.

## Cuestiones pendientes de definición

- Si se requiere audiencia única en una integración futura, ¿qué fuente y método permitirían deduplicar personas entre plataformas?
- Las entradas para datos reales, si se conectaran en el futuro, no forman parte de esta simulación.

## Estado de implementación

El HTML muestra estáticamente los valores demo de plataforma y comparativas precomputadas. No calcula variaciones, participaciones o tasas en tiempo de ejecución, ni cuenta eventos de clic; T32 permanece pendiente. Las decisiones funcionales de comparación, participación y origen de clic se conservan según T01, T02 y T07.
