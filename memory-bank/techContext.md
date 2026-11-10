# Contexto tecnológico

- HTML5 semántico.
- Tailwind CSS v4 únicamente mediante clases de utilidad; incluir en `<head>` el CDN oficial exacto: `<script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>`.
- No usar Tailwind v3, `cdn.tailwindcss.com`, CSS personalizado, bloques `<style>`, atributos `style` ni archivos CSS propios.
- Diseño Mobile First y responsive.
- No se ha seleccionado framework frontend, sistema de compilación ni biblioteca de gráficos; no añadir dependencias sin validación.
- Arquitectura prevista: frontend estático con `index.html`; `server.py` usa Flask para servir archivos locales en el puerto 3000 y no procesa campañas.
- No implementar backend de negocio, persistencia ni integraciones reales con redes sociales.
- `.vscode/settings.json` configura Prettier al guardar.
- Convenciones: HTML semántico, jerarquía de encabezados coherente, tablas para datos tabulares, accesibilidad por teclado y foco visible, y clases Tailwind responsive.

La fuente de instrucciones del repositorio es [AGENTS.md](../AGENTS.md).
