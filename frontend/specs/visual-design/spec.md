# Diseño visual del dashboard

## Objetivo

Establecer la organización visual funcional del dashboard de afiliación a partir de las descripciones confirmadas, sin inferir detalles que no se pudieron observar en la imagen de referencia.

## Usuario

Influencer que consulta periódicamente resultados económicos y publicitarios de sus colaboraciones de afiliación.

## Historia de usuario

Como influencer, quiero reconocer con claridad los indicadores principales y navegar entre el resumen, los factores de rendimiento y los detalles operacionales.

## Requisitos funcionales

### Confirmados

- Organizar la información en tres bloques: KPIs principales; drivers; detalles operacionales.
- El bloque superior contiene cuatro tarjetas KPI. Sus indicadores y valores están definidos en [dashboard-kpis](../dashboard-kpis/spec.md).
- El bloque intermedio se describió con dos paneles en paralelo: rendimiento por plataforma y rendimiento por producto.
- El bloque inferior contiene una sección de rendimiento de campañas y una comparación por plataforma con tarjetas independientes para Instagram, TikTok y YouTube.
- Se mencionaron navegación lateral, paneles blancos, gráficos de barras horizontales, tablas y jerarquía visual clara.
- La presentación debe adaptarse a móvil, tablet y escritorio, preservando la legibilidad y jerarquía de la información.
- Para esta implementación, los paneles de plataforma y producto se apilan en móvil/tablet y se presentan en dos columnas desde `lg`; campañas y comparativa de plataforma permanecen como secciones separadas.
- Los cambios y estados no deben comunicarse únicamente mediante el color.

### Alcance de la referencia

La imagen de referencia no pudo inspeccionarse visualmente durante el análisis. Los elementos anteriores provienen de descripciones textuales del proyecto; no se atribuyen a la imagen otros colores, tipografías, medidas, adornos o estados.

### Detalles pendientes

La apariencia visual de estados vacíos y la especificación de color, tipografía, espaciado, bordes y tamaños no están acordadas en la información disponible. No se busca fidelidad pixel a pixel con la imagen no disponible.

## Criterios de aceptación

1. La composición mantiene los tres bloques y las agrupaciones descritas, sin añadir contenido o rasgos visuales atribuidos a la referencia no observada.
2. La jerarquía y los componentes siguen siendo legibles en móvil, tablet y escritorio; variaciones o estados se distinguen sin depender únicamente del color.

## Fuera de alcance

- Reproducir literalmente una imagen que no fue inspeccionada.
- Definir una paleta, tipografía, medidas o layout definitivo sin decisión funcional o visual confirmada.
- Alterar los datos o reglas de negocio documentados en las SPEC funcionales.

## Cuestiones pendientes de definición

- ¿Puede proporcionarse una referencia visual accesible si se requiere mayor fidelidad a su apariencia?
- ¿Qué decisiones visuales se aprobarán para color, tipografía, espaciado, bordes y tamaños?
- ¿Puede proporcionarse una referencia visual accesible si se requiere fidelidad adicional?
- ¿Cómo se representan visualmente los estados sin datos o con datos parciales?
