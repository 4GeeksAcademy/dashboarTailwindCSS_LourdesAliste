# Estado actual del proyecto

## Estado actual

- Frontend estático implementado únicamente en `index.html`, con HTML semántico y Tailwind CSS v4 por CDN.
- No se usan módulos JavaScript, framework, compilación, backend de negocio ni persistencia.
- Los KPI, variaciones, tasas y ranking visibles son valores demo precomputados, no cálculos de ejecución.
- No hay filtros interactivos ni estados dinámicos. Las reglas están documentadas, pero su implementación queda pendiente mientras no se autorice JavaScript o backend.
- Las entradas son demostrativas. No hay integraciones reales ni atribución cruzada de los conjuntos de plataformas, productos y campañas.

## Verificación

- `http://localhost:3000/` responde HTTP 200.
- No hay pruebas de lógica porque no existe código JavaScript.
- No hay navegador instalado en el contenedor; queda pendiente la inspección visual end-to-end.

## Pendiente

- Inspección visual en un navegador.
- Cálculos en tiempo de ejecución, filtros interactivos y estados dinámicos, sujetos a mantener la restricción sin JavaScript.
- Integraciones y datos reales, audiencia única deduplicada, atribución entre vistas y métricas ROI/ROAS de campañas continúan fuera de alcance hasta definir sus fuentes y reglas.
