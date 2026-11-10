# Rendimiento de campañas

## Objetivo

Permitir revisar los resultados reportados de campañas de afiliación por campaña, plataforma y producto, manteniendo separados los datos conocidos y las métricas que requieren definiciones o inputs adicionales.

## Usuario

Influencer que supervisa los resultados de sus campañas promocionales.

## Historia de usuario

Como influencer, quiero consultar el alcance, las conversiones y las comisiones informadas por campaña para comparar sus resultados sin asumir atribución o retorno que no estén definidos.

## Requisitos funcionales

### Confirmados

- La tabla de campañas contempla campaña, plataforma, producto, alcance, conversiones y comisiones.
- El requisito general también menciona fechas de campaña; los ejemplos proporcionados no incluyen fechas.
- Costes, ingresos atribuibles y métricas de retorno solo se podrán presentar cuando existan datos suficientes y se definan las reglas funcionales correspondientes.
- No asumir que una conversión equivale a una unidad vendida.

### Datos ilustrativos, no reales ni normativos

| Campaña | Plataforma | Producto | Alcance | Conversiones | Comisiones |
|---|---|---|---:|---:|---:|
| Campaña 1 | Instagram | A | 10.000 | 20 | 150 € |
| Campaña 2 | TikTok | B | 8.000 | 25 | 450 € |
| Campaña 3 | YouTube | C | 6.000 | 15 | 180 € |

Estos valores no indican si la lista es exhaustiva ni proporcionan costes, ingresos atribuibles o fechas.

### Datos y reglas pendientes

- Definición funcional de conversión y datos de origen.
- Las filas de campaña de ejemplo se mantienen como muestras independientes; sus etiquetas de plataforma y producto no establecen atribución ni reconciliación con otros conjuntos.
- Si se incorporan datos funcionales, siguen pendientes las reglas para atribuir conversiones e ingresos a campañas, plataformas y productos.
- Si las campañas listadas representan todas las campañas o solo una selección.
- Fechas o periodo específico de cada campaña; el periodo general del dashboard es 2026–actualidad.
- Costes por campaña, ingresos atribuibles y definición de ROI/ROAS.
- Tratamiento de campañas con datos ausentes o incompletos.

## Criterios de aceptación

1. La vista identifica cada campaña y muestra únicamente los campos y valores informados, manteniendo conversiones separadas de unidades vendidas.
2. No presenta coste, ingreso atribuible o ROI/ROAS como calculado si faltan datos o definiciones funcionales.

## Fuera de alcance

- Integraciones reales con plataformas o marcas.
- Inventar fechas, costes, ingresos atribuibles o reglas de atribución.
- Calcular conversión, ROI o ROAS a partir de equivalencias no confirmadas.

## Cuestiones pendientes de definición

- ¿Las campañas de ejemplo son la lista completa o una muestra?
- ¿Se requiere mostrar fechas para cada campaña y qué fechas deben proporcionarse?
- Si se incorporan datos funcionales, ¿cómo se definirán y atribuirán conversiones e ingresos a una campaña cuando intervengan varios puntos de contacto? Esta regla no se aplica a las filas de ejemplo actuales.
- ¿Qué costes se incluirán y se necesita ROI o ROAS? ¿Qué fórmula y tratamiento de costes ausentes o cero se aprobarán?
- ¿Cómo se mostrarán campañas sin datos o con datos parciales?
