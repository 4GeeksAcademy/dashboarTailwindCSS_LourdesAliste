# Instrucciones del agente

## Alcance del proyecto

Este repositorio parte de una plantilla HTML básica. Antes de implementar o cambiar el dashboard, consulta [DASHBOARD_REQUIREMENTS.md](DASHBOARD_REQUIREMENTS.md), que es la fuente de requisitos funcionales y decisiones de negocio. No inventes respuestas para los puntos marcados como pendientes ni cambies los datos de ejemplo sin actualizar su documentación.

## Tecnologías y herramientas

- HTML5 semántico para la interfaz.
- Tailwind CSS v4 exclusivamente mediante clases de utilidad. Incluir en el `<head>` el CDN oficial exacto:
  `<script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>`
- No usar `cdn.tailwindcss.com`, Tailwind CSS v3, CSS personalizado, bloques `<style>`, atributos `style` ni archivos CSS propios.
- Interfaz Mobile First y responsive.
- No implementar JavaScript de negocio ni archivos `.js`/`.mjs`. La interfaz debe permanecer estática; filtros, cálculos en tiempo de ejecución y estados dinámicos quedan pendientes mientras no se apruebe otra arquitectura. Se permite únicamente el script CDN de Tailwind CSS v4 indicado arriba.
- No hay framework frontend, sistema de compilación ni biblioteca de gráficos seleccionados. No añadas dependencias sin validación.
- No implementar backend de negocio ni integraciones reales con redes sociales. El `server.py` existente sirve archivos locales con Flask en el puerto 3000; se usa para previsualización, no para procesar campañas.
- `.vscode/settings.json` configura Prettier como formateador al guardar. No hay otras convenciones de formato específicas configuradas.

## Arquitectura prevista

- La interfaz es un frontend estático, con `index.html` como entrada servida por `server.py`.
- Los valores de demostración son datos ficticios de frontend, no datos sincronizados con plataformas ni persistidos en un backend.
- Mantén la documentación funcional separada de estas instrucciones generales. No fijes una arquitectura de componentes, un layout definitivo o una estrategia de interactividad que no esté acordada.

## Convenciones de código y accesibilidad

- Usa estructura HTML semántica y jerarquía de encabezados coherente; reserva `header`, `nav`, `main`, `section` y `footer` para las regiones que correspondan.
- Para datos tabulares, usa tablas HTML con encabezados asociados a sus columnas y filas. No uses tablas para maquetación.
- Mantén nombres descriptivos en identificadores y archivos, y reutiliza patrones de marcado y clases de utilidad cuando ayuden a mantener consistencia. Evita abstracciones o dependencias innecesarias.
- Construye primero para pantallas pequeñas y añade variantes responsive de Tailwind para tamaños mayores. Evita desbordamientos y conserva una jerarquía visual legible.
- Mantén consistencia de espaciado, tipografía, colores y componentes. Los colores no deben ser el único medio para comunicar estados o variaciones.
- Los controles deben tener nombre accesible, foco visible y uso por teclado. Usa elementos nativos y etiquetas asociadas cuando sea posible; añade atributos ARIA solo cuando el HTML semántico no sea suficiente.
- Expresa importes en euros y distingue siempre ingresos brutos por ventas de comisiones de la influencer.
- Limita cada cambio al requisito solicitado; no reescribas documentación o configuración existente sin necesidad.
