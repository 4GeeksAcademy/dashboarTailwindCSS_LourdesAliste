# Tareas de implementación del dashboard

## Reglas de ejecución

- Ejecutar una tarea a la vez y en el orden indicado; no iniciar la siguiente hasta completar y verificar la actual.
- No implementar JavaScript ni archivos `.js`/`.mjs`. Los resultados demo pueden presentarse estáticamente; cálculos en tiempo de ejecución, filtros y estados dinámicos quedan pendientes.
- Mantener todas las casillas sin marcar hasta que el resultado esté implementado y verificado.
- Si una tarea depende de una decisión funcional no confirmada, detener la ejecución y documentar el bloqueo. No sustituirla por una suposición.
- Los ejemplos son ilustrativos, no datos reales ni resultados calculados, salvo las operaciones confirmadas explícitamente en las SPEC.
- Las tareas originales se conservan con sus estados para trazabilidad. Si indican integración o desglose, no se ejecutan por separado: se ejecutan T32–T44 referenciadas. Los datos fijos de simulación no requieren definir métricas o fórmulas que no estén confirmadas; los cálculos funcionales sí dependen de sus definiciones.

## Fase 0: decisiones previas

Resolver estas cuestiones en las SPEC antes de implementar los comportamientos que dependen de ellas. El periodo general del dashboard, 2026–actualidad, ya está confirmado.

- [x] T01. Confirmar comparación temporal de métricas de plataforma (SPEC: [platform-performance](specs/platform-performance/spec.md)).
  - Criterio: periodos contiguos de 30 días; variación = ((actual − anterior) / anterior) × 100. Anterior cero = «Sin referencia»; entradas ausentes = «Sin datos».
- [x] T02. Confirmar fórmula de participación sobre comisiones y reglas de precisión/redondeo (SPEC: [platform-performance](specs/platform-performance/spec.md)).
  - Criterio: comisión de plataforma / total de comisiones × 100; redondeo final a un decimal. Una suma visible de 100,1 % no se ajusta artificialmente.
- [x] T03. Definir cómo se obtiene el alcance agregado y si se deduplican personas entre plataformas (SPEC: [platform-performance](specs/platform-performance/spec.md)).
  - Criterio: la definición y la fuente de datos necesaria quedan documentadas; no se infieren personas únicas a partir de la suma.
  - Decisión: para esta simulación, 55.000 es la suma aritmética de los alcances informados y no representa audiencia única. No se deduplican personas; un alcance único futuro queda fuera de alcance hasta definir fuente y método.
- [ ] T04. Definir el evento de conversión, su fórmula y los datos de entrada (SPEC: [dashboard-kpis](specs/dashboard-kpis/spec.md), [platform-performance](specs/platform-performance/spec.md), [campaigns](specs/campaigns/spec.md)).
  - Criterio: queda aprobada y documentada la definición completa, o se confirma que las tasas permanecerán solo como ejemplos no calculados; no se asume equivalencia con unidades.
  - Integrada en T33; no ejecutar por separado.
- [ ] T05. Definir la fórmula de engagement y los datos de entrada (SPEC: [dashboard-kpis](specs/dashboard-kpis/spec.md), [platform-performance](specs/platform-performance/spec.md), [product-performance](specs/product-performance/spec.md)).
  - Criterio: quedan aprobados la fórmula y los conteos de interacción requeridos, o se confirma que las tasas permanecerán solo como ejemplos no calculados.
  - Integrada en T34; no ejecutar por separado.
- [ ] T06. Definir atribución de unidades, comisiones e ingresos entre plataforma, producto y campaña (SPEC: [platform-performance](specs/platform-performance/spec.md), [product-performance](specs/product-performance/spec.md), [campaigns](specs/campaigns/spec.md)).
  - Criterio: las reglas y el tratamiento de varios puntos de contacto quedan documentados, o se mantienen explícitamente fuera del cálculo.
  - Desglosada en T35, T36 y T37; no ejecutar T06 por separado.
- [x] T07. Definir atribución de clics por plataforma (SPEC: [platform-performance](specs/platform-performance/spec.md)).
  - Criterio: cada evento tiene un identificador y un origen único de enlace; contar una vez, sumar Instagram/TikTok/YouTube y no tratar clics como compras.
- [ ] T08. Definir atribución de conversiones a plataforma y campaña (SPEC: [platform-performance](specs/platform-performance/spec.md), [campaigns](specs/campaigns/spec.md)).
  - Dependencia: T04.
  - Criterio: la regla se documenta sin equiparar conversión con unidad vendida salvo confirmación explícita.
  - Integrada en T33; no ejecutar por separado.
- [ ] T09. Definir atribución de interacciones a plataforma y producto (SPEC: [platform-performance](specs/platform-performance/spec.md), [product-performance](specs/product-performance/spec.md)).
  - Dependencia: T05.
  - Criterio: quedan documentados los conteos atribuibles necesarios para engagement, o se confirma que no se mostrará la métrica.
  - Integrada en T34; no ejecutar por separado.
- [ ] T10. Definir el tratamiento de datos ausentes, parciales, alcance cero y listados sin coincidencias (SPEC: [dashboard-kpis](specs/dashboard-kpis/spec.md), [platform-performance](specs/platform-performance/spec.md), [product-performance](specs/product-performance/spec.md), [campaigns](specs/campaigns/spec.md), [filters](specs/filters/spec.md)).
  - Criterio: cada estado y su presentación quedan documentados en las SPEC afectadas.
  - Desglosada en T41 (datos de métricas) y T42 (listados filtrados); no ejecutar T10 por separado.
- [ ] T11. Confirmar si la lista de campañas es exhaustiva o una muestra y si deben mostrarse fechas (SPEC: [campaigns](specs/campaigns/spec.md)).
  - Criterio: alcance de la lista y requisito/disponibilidad de fechas quedan documentados sin completar valores ausentes.
  - Integrada en T38; no ejecutar por separado.
- [ ] T12. Confirmar qué costes e ingresos atribuibles estarán disponibles por campaña (SPEC: [campaigns](specs/campaigns/spec.md)).
  - Criterio: campos disponibles y su fuente quedan documentados; los valores ausentes no se completan por inferencia.
  - Integrada en T39; no ejecutar por separado.
- [ ] T13. Definir si se requiere ROI o ROAS, su fórmula y los costes incluidos (SPEC: [campaigns](specs/campaigns/spec.md)).
  - Dependencia: T12.
  - Criterio: métrica, fórmula y tratamiento de costes ausentes o cero quedan aprobados y documentados; si no se define, no se implementa el cálculo.
  - Integrada en T39; no ejecutar por separado.
- [ ] T14. Definir campos, opciones, combinaciones y alcance de los filtros (SPEC: [filters](specs/filters/spec.md)).
  - Criterio: comportamiento de filtrado queda documentado para cada listado al que aplique.
  - Integrada en T40; no ejecutar por separado.
- [ ] T15. Definir criterios de “top” productos/plataformas/campañas y de “oportunidades de mejora” (SPEC: [filters](specs/filters/spec.md)).
  - Criterio: criterios de inclusión/orden quedan aprobados; no se clasifican elementos si no se definen.
  - Integrada en T40; no ejecutar por separado.
- [x] T16. Confirmar distribución visual responsive y decisiones visuales pendientes; proporcionar una referencia accesible solo si se requiere fidelidad a la imagen (SPEC: [visual-design](specs/visual-design/spec.md)).
  - Criterio: las decisiones que se implementarán quedan registradas; no se infieren rasgos de una imagen no inspeccionada.
  - Decisión: paneles plataforma/producto apilados en móvil/tablet y paralelos desde `lg`; estilos exactos y fidelidad visual no se fijan.

## Fase 1: estructura compartida

- [x] T17. Crear la estructura semántica de la página con navegación y regiones de KPI, drivers y detalles operacionales (SPEC: [visual-design](specs/visual-design/spec.md)).
  - Criterio: las tres regiones están identificadas y su agrupación coincide con la SPEC, sin fijar detalles visuales pendientes.

## Fase 2: bloque superior, KPI

- [x] T18. Presentar y verificar las cuatro tarjetas KPI con sus valores ilustrativos y unidades (SPEC: [dashboard-kpis](specs/dashboard-kpis/spec.md)).
  - Dependencia: T17.
  - Criterio actualizado: se muestran estáticamente los resultados demo 1.530 €, 150 unidades, 2,8 % y 6,7 % para 2026–actualidad; las tasas corresponden a las fórmulas aprobadas y las comisiones no se confunden con ingresos brutos.

## Fase 3: bloque intermedio, drivers

- [ ] T19. Presentar el panel de plataformas con alcance, unidades y comisiones ilustrativas, incluidas las barras horizontales comparativas (SPEC: [platform-performance](specs/platform-performance/spec.md)).
  - Dependencia: T17.
  - Criterio: cada plataforma se identifica y diferencia sus métricas; 55.000 se presenta como suma informada, no como audiencia única.
  - Integrada en T32; no ejecutar por separado.
- [ ] T20. Mostrar la participación en comisiones por plataforma según la regla aprobada (SPEC: [platform-performance](specs/platform-performance/spec.md)).
  - Dependencia: T02 y T19.
  - Criterio: valores y redondeo siguen la regla documentada y no se presentan porcentajes ilustrativos como cálculo no validado.
  - Integrada en T32 como valores demo precomputados conforme a T02; el HTML no realiza el recálculo. No ejecutar T20 por separado.
- [ ] T21. Presentar las tarjetas comparativas de plataforma con alcance, clics y variación solo cuando su significado y comparación estén definidos (SPEC: [platform-performance](specs/platform-performance/spec.md)).
  - Dependencia: T01, T07 y T19.
  - Criterio: las variaciones tienen métrica y base temporal identificables; no se muestran datos sin atribución confirmada.
  - Integrada en T32 para mostrar resultados demo precomputados de las métricas y periodos definidos en T01/T07. El cálculo y conteo de eventos siguen pendientes en T32; no ejecutar T21 por separado.
- [ ] T22. Incorporar la tasa de conversión por plataforma únicamente si la definición, atribución e inputs están aprobados (SPEC: [platform-performance](specs/platform-performance/spec.md)).
  - Dependencia: T04, T08, T10 y T19.
  - Criterio: se usa exclusivamente la fórmula y los datos aprobados, o se verifica que la tasa queda omitida/no calculada.
  - Integrada en T33; no ejecutar por separado.
- [ ] T23. Incorporar engagement por plataforma únicamente si la definición, atribución e inputs están aprobados (SPEC: [platform-performance](specs/platform-performance/spec.md)).
  - Dependencia: T05, T09, T10 y T19.
  - Criterio: se usa exclusivamente la fórmula y los datos aprobados, o se verifica que la tasa queda omitida/no calculada.
  - Integrada en T32 para mostrar el resultado demo precomputado y en T34 para el cálculo funcional pendiente; no ejecutar por separado.
- [x] T24. Presentar y verificar la tabla de productos con precios, unidades, ingresos por ventas y comisiones (SPEC: [product-performance](specs/product-performance/spec.md)).
  - Dependencia: T17.
  - Criterio: se muestran los ejemplos documentados (2.500 €/375 €, 4.800 €/720 €, 4.800 €/720 €; total 12.100 €/1.815 €) y se mantienen independientes de KPI/plataformas.
- [ ] T25. Incorporar engagement por producto únicamente si hay fórmula e inputs atribuibles aprobados (SPEC: [product-performance](specs/product-performance/spec.md)).
  - Dependencia: T05, T09, T10 y T24.
  - Criterio: se aplica la regla aprobada o se verifica que no se presenta un resultado calculado.
  - Integrada en T34; no ejecutar por separado.

## Fase 4: bloque inferior, operaciones

- [ ] T26. Presentar la tabla de campañas con los campos y ejemplos disponibles, y fechas solo si se confirman (SPEC: [campaigns](specs/campaigns/spec.md)).
  - Dependencia: T11 y T17.
  - Criterio: se muestran solo datos informados; la lista no se considera exhaustiva ni se inventan fechas; conversiones siguen separadas de unidades.
  - Integrada en T38; no ejecutar por separado.
- [ ] T27. Presentar costes, ingresos atribuibles y ROI/ROAS solo cuando la disponibilidad de datos, atribución y fórmula estén aprobadas (SPEC: [campaigns](specs/campaigns/spec.md)).
  - Dependencia: T06, T08, T10, T12, T13 y T26.
  - Criterio: cualquier retorno visible usa la definición aprobada; si faltan datos o se decide no calcularlo, se verifica que no aparece como resultado.
  - Integrada en T39; no ejecutar por separado.

## Fase 5: filtros

- [ ] T28. Aplicar ranking y filtros aprobados a Top Affiliate Products (SPEC: [filters](specs/filters/spec.md)).
  - Dependencia: T10, T14, T15, T19, T24 y T26.
  - Criterio: primero ordenar Revenue descendente y Conversion Rate descendente (desempate), hasta tres productos; después permitir filtros combinables de plataforma y categoría. No filtrar otros paneles. T42 verifica por separado el estado vacío.
  - Las facetas de filtro son metadatos demo y no implican atribución de ventas.
  - Estado: el ranking demo se presenta estáticamente; los filtros no se implementan sin JavaScript ni backend aprobado.

## Fase 6: integración visual, accesibilidad y verificación

- [x] T29. Integrar los bloques según la jerarquía aprobada y aplicar la distribución responsive definida (SPEC: [visual-design](specs/visual-design/spec.md)).
  - Dependencia: T16–T28.
  - Criterio: se conservan los tres bloques y agrupaciones especificados en móvil, tablet y escritorio, sin añadir rasgos visuales no confirmados.
  - Se mantiene independiente; dependencias de ejecución consolidadas: T16, T17, T18, T24, T28, T32, T38 y T39.
  - Decisión aplicada: paneles plataforma/producto apilados hasta tablet y en dos columnas desde `lg`; no se fijaron colores, tipografía ni otros detalles visuales pendientes.
- [ ] T30. Verificar accesibilidad de controles y datos tabulares (SPEC: todas las SPEC aplicables y convenciones generales de [AGENTS.md](../AGENTS.md)).
  - Dependencia: T18–T29.
  - Criterio: controles aplicables son utilizables con teclado y tienen foco perceptible; cambios/estados no dependen solo del color; tablas asocian datos con encabezados.
  - Desglosada en T43 (controles/estados) y T44 (tablas); no ejecutar T30 por separado.
- [ ] T31. Verificar la página servida localmente y contrastar cada bloque con los criterios de aceptación de su SPEC (todas las SPEC aplicables).
  - Dependencia: T29 y T30.
  - Criterio: la página se sirve con `server.py`; cada requisito implementado pasa su aceptación y ninguna decisión pendiente se presenta como funcionalidad concluida.
  - Se mantiene como verificación final; sus dependencias de ejecución incluyen T29, T43 y T44.
  - Estado: la página responde HTTP 200. Falta inspección visual end-to-end en navegador, no disponible en el contenedor.

## Tareas consolidadas y desglosadas para ejecución

Ejecutar estas tareas en orden de dependencia, una por una. Las tareas originales integradas o desglosadas mantienen su checkbox sin marcar únicamente como referencia y no se ejecutan por separado.

### Simulación de valores suministrados

- [ ] T32. Implementar comparación, participación y atribución de clics por plataforma (integra T01, T02, T07, T19, T20 y T21; SPEC: [platform-performance](specs/platform-performance/spec.md)).
  - Dependencia: T17.
  - Criterio secuencial: (1) calcular y mostrar variaciones con los periodos iguales y contiguos; (2) calcular participación con la regla aprobada; (3) contar una vez cada evento de clic por origen único y mostrar totales. Todos los inputs se identifican como simulados. El alcance 55.000 se etiqueta como suma, no audiencia única.
  - Estado: el HTML muestra salidas demo precomputadas; no ejecuta los cálculos ni cuenta eventos.

### Cálculos funcionales y atribución

- [ ] T33. Incorporar Conversion Rate funcional con inputs de demostración (integra T04, T08 y T22; SPEC: [dashboard-kpis](specs/dashboard-kpis/spec.md), [platform-performance](specs/platform-performance/spec.md)).
  - Dependencia: T17 y T32 para la presentación por plataforma; el cálculo requiere definición, datos y atribución aprobados.
  - Criterio: compras completadas desde enlace / clics × 100, a un decimal; 0 clics = «No calculable»; entradas ausentes = «Sin datos». Las compras no se equiparan con unidades.
  - Estado: el valor demo 2,8 % es estático; el cálculo y sus estados no se ejecutan en la página.
- [ ] T34. Incorporar Engagement Rate funcional con inputs de demostración (integra T05, T09 y T25; SPEC: [dashboard-kpis](specs/dashboard-kpis/spec.md), [platform-performance](specs/platform-performance/spec.md), [product-performance](specs/product-performance/spec.md)).
  - Dependencia: T17, T24 y T32 para las vistas aplicables; el cálculo requiere fórmula, interacciones y atribución aprobadas.
  - Criterio: (likes + comentarios + compartidos + guardados) / alcance × 100, a un decimal; views se excluyen. Alcance cero = «No calculable»; entradas ausentes = «Sin datos». No inventar engagement por producto.
  - Estado: el valor demo 6,7 % es estático; el cálculo y sus estados no se ejecutan en la página.
- [x] T35. Definir atribución real de unidades, comisiones e ingresos a plataformas (desglose de T06; SPEC: [platform-performance](specs/platform-performance/spec.md)).
  - Criterio: la regla, incluidos varios puntos de contacto, queda documentada o se confirma que esos valores se mantienen solo como muestras independientes.
- [x] T36. Definir atribución real de unidades, comisiones e ingresos a productos (desglose de T06; SPEC: [product-performance](specs/product-performance/spec.md)).
  - Criterio: la regla queda documentada o se confirma que no se requiere reconciliar las muestras de productos con otras vistas.
- [x] T37. Definir atribución real de unidades, comisiones e ingresos a campañas (desglose de T06; SPEC: [campaigns](specs/campaigns/spec.md)).
  - Criterio: la regla y los casos de varios puntos de contacto quedan documentados o se confirma que las filas de campaña son solo muestras sin reconciliación.

### Campañas y filtros

- [x] T38. Presentar la tabla de campaña con los ejemplos y resolver su alcance/fechas (integra T11 y T26; SPEC: [campaigns](specs/campaigns/spec.md)).
  - Dependencia: T17.
  - Criterio: se muestran solo campaña, plataforma, producto, alcance, conversiones y comisiones informados; no se inventan fechas ni se presenta la muestra como exhaustiva sin confirmación; conversiones y unidades permanecen separadas.
- [x] T39. Resolver disponibilidad y, solo si corresponde, presentar costes, ingresos atribuibles y ROI/ROAS (integra T12, T13 y T27; SPEC: [campaigns](specs/campaigns/spec.md)).
  - Dependencia: T37 y T38.
  - Criterio: antes de mostrar resultados quedan confirmados datos disponibles, métrica y fórmula, costes incluidos y tratamiento de datos/costes ausentes o cero; si no se definen, no se presenta retorno calculado.
- [x] T40. Definir campos, alcance de filtros y criterios de ranking (integra T14 y T15; SPEC: [filters](specs/filters/spec.md)).
  - Criterio: campos, opciones, combinaciones y reglas de clasificación quedan documentados; no se inventan oportunidades.
  - Decisión: solo Top Affiliate Products usa filtros combinables por plataforma y categoría; ranking por Revenue y Conversion Rate descendentes. Otros listados conservan orden de origen.

### Estados y accesibilidad

- [ ] T41. Definir y verificar estados para datos métricos ausentes, parciales o con alcance cero (parte de T10; SPEC: [dashboard-kpis](specs/dashboard-kpis/spec.md), [platform-performance](specs/platform-performance/spec.md), [product-performance](specs/product-performance/spec.md), [campaigns](specs/campaigns/spec.md)).
  - Criterio: los estados y su presentación siguen las decisiones aprobadas, sin convertir un dato de simulación en resultado real.
  - Ámbito aprobado: KPI superiores (Total Revenue, My Earnings, Audience Impact, Avg. Engagement); My Content Reach (Instagram, TikTok, YouTube); Top Affiliate Products (precio medio, Revenue, Conversion Rate); Recent Brand Collaborations (Followers, Revenue, My Payout, ROI); métricas por plataforma (Clicks, Shares, Views, Completion, Avg. Watch, CTR). Aplicar a campos existentes; no añadir campos ausentes para generar estados.
  - Política: dato ausente = «Sin datos»; parcial = valor con «Datos parciales»; cero informado = 0; tasa calculada sin denominador válido = «No calculable», nunca 0 %. Los datos demo completos se muestran como resultados derivados y etiquetados como simulación.
  - En el dashboard actual, Conversion Rate de producto es un resultado demo precomputado de inputs independientes. No hay casos actuales de datos parciales ni alcance cero; los estados no se ejecutan en la página estática.
  - Estado: las reglas están documentadas, pero no se ejecutan estados dinámicos en HTML estático.
- [ ] T42. Implementar y verificar el estado de listados filtrados sin coincidencias (parte de T10; SPEC: [filters](specs/filters/spec.md)).
  - Dependencia: T40 y T28.
  - Criterio: el estado coincide con el comportamiento documentado y no se inventan filas para completar el listado.
  - Cuando una combinación de filtros de Top Affiliate Products no tenga coincidencias, mostrar «No hay resultados para los filtros seleccionados», sin filas ni acciones adicionales.
  - Estado: pendiente junto con T28; no hay controles de filtro en la interfaz estática.
- [ ] T43. Verificar controles, teclado, foco perceptible y comunicación de estados (parte de T30; SPEC: [visual-design](specs/visual-design/spec.md) y [AGENTS.md](../AGENTS.md)).
  - Dependencia: controles interactivos de T28, si se autorizan, y composición integrada en T29.
  - Criterio: cada control interactivo se opera por teclado, tiene foco perceptible y los estados no dependen solo del color. Pendiente porque no hay controles interactivos en el HTML estático.
- [x] T44. Verificar asociación de encabezados y datos en tablas (parte de T30; SPEC: [platform-performance](specs/platform-performance/spec.md), [product-performance](specs/product-performance/spec.md), [campaigns](specs/campaigns/spec.md) y [AGENTS.md](../AGENTS.md)).
  - Dependencia: T24, T32 y T38.
  - Criterio: cada dato se asocia a su encabezado y las tablas no se usan para maquetación.
