# Rendimiento por producto

## Objetivo

Permitir revisar el rendimiento económico de cada producto promocionado, distinguiendo precio, unidades vendidas, ingresos brutos por ventas y comisiones de la influencer.

## Usuario

Influencer que compara los productos de afiliación que promociona.

## Historia de usuario

Como influencer, quiero comparar los productos por unidades, ingresos por ventas y comisiones para conocer los resultados económicos de cada uno sin confundir ventas brutas con mis comisiones.

## Requisitos funcionales

### Confirmados

- Presentar los productos A, B y C con precio unitario, unidades vendidas, ingresos por ventas y comisión.
- Mantener separados los ingresos por ventas y las comisiones.
- Top Affiliate Products calcula Conversion Rate como compras completadas desde enlace afiliado / clics únicos × 100, a un decimal; estos inputs por producto son una muestra ficticia independiente.
- Para filtros de Top Affiliate Products, cada producto tiene una categoría y una plataforma demostrativas. Esos metadatos son facetas de filtro únicamente y no atribuyen ventas, unidades o comisiones.
- Los ejemplos de producto son independientes de los KPI, las plataformas y las campañas; no se reconcilian con esos conjuntos.

### Datos ilustrativos, no reales ni normativos

| Producto | Precio unitario | Unidades | Ingresos por ventas | Comisión |
|---|---:|---:|---:|---:|
| A | 50 € | 50 | 2.500 € | 375 € |
| B | 120 € | 40 | 4.800 € | 720 € |
| C | 80 € | 60 | 4.800 € | 720 € |
| **Total** | — | **150** | **12.100 €** | **1.815 €** |

Los valores de unidades y totales son ejemplos. No se deben conciliar con los 1.530 € del KPI o del desglose por plataforma.

| Producto | Plataforma (filtro demo) | Categoría (filtro demo) | Clics afiliados | Compras completadas desde enlace | Conversion Rate |
|---|---|---|---:|---:|---:|
| A | Instagram | Belleza | 300 | 15 | 5,0 % |
| B | TikTok | Tecnología | 1.000 | 30 | 3,0 % |
| C | YouTube | Hogar | 900 | 45 | 5,0 % |

Esta tabla de inputs también es ficticia. Los clics son conteos únicos por enlace de producto; las compras no se equiparan con las unidades de la tabla de ventas. No sumar estos clics y compras a los datos por plataforma: son muestras separadas sin atribución cruzada.

### Reglas confirmadas

- Producto A cuesta 50 €, B 120 € y C 80 €.
- La comisión de la influencer es 15 % del ingreso por ventas.
- Ingresos por ventas = unidades vendidas × precio unitario.
- Comisión = ingresos por ventas × 15 %.

### Datos y reglas pendientes

- Fórmula e inputs de engagement atribuible a producto.
- No se define atribución multi-touch funcional para unidades, ingresos o comisiones; las tasas de compra demo y metadatos de filtro no concilian estas muestras con otras vistas.
- Tratamiento de productos sin datos o con datos parciales.

## Criterios de aceptación

1. La información de cada producto diferencia claramente precio, unidades, ingresos por ventas y comisión, y los importes de ejemplo respetan las reglas confirmadas.
2. El total del ejemplo de productos se mantiene independiente de los KPI, los datos de plataforma y las campañas; los filtros demo no se presentan como atribución de ventas.

## Fuera de alcance

- Modificar precios o el porcentaje de comisión confirmados.
- Presentar ingresos brutos como ganancias de la influencer.
- Inferir engagement o atribución a producto a partir de los datos de ejemplo.

## Estado de implementación

La tabla de productos y el ranking demo se presentan estáticamente, con los valores precomputados documentados. No hay filtros interactivos ni cálculo de Conversion Rate en tiempo de ejecución; T28 permanece pendiente según [tasks.md](../../tasks.md).

## Cuestiones pendientes de definición

- ¿Qué datos de alcance e interacciones se atribuyen a cada producto y con qué regla?
- ¿Qué fórmula funcional se aprobará para el engagement rate de producto?
- ¿Cómo se representan productos sin datos de alcance, interacciones o ventas en futuras entradas reales?
