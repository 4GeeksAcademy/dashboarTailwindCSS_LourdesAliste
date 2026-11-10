# Requisitos funcionales

## Fuente disponible

Las SPEC funcionales están en `frontend/specs/` para KPI, plataformas, productos, campañas, filtros y diseño. `DASHBOARD_REQUIREMENTS.md` conserva el alcance general.

## Funcionalidad documentada

El HTML presenta estáticamente los resultados demo 1.530 €, 150 unidades, 2,8 % y 6,7 %. Las fórmulas y estados de datos ausentes, cero y comparación están definidos en las SPEC, pero no se ejecutan en tiempo de ejecución.

Las reglas y datos de entrada del bloque, incluidos los pendientes, se mantienen en la SPEC para evitar duplicar su detalle aquí.

## Alcance general previsto

La interfaz está implementada únicamente en `index.html` con HTML semántico y Tailwind CSS v4. No se usa JavaScript, backend, persistencia ni integraciones reales; las muestras de plataforma, producto y campaña se mantienen independientes.
