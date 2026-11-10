# Filtros de listados

## Objetivo

Permitir filtrar Top Affiliate Products por plataforma y categoría, conforme a los campos demo definidos en la SPEC de producto.

## Usuario

Influencer que necesita acotar los listados para revisar elementos relevantes del rendimiento de afiliación.

## Historia de usuario

Como influencer, quiero combinar filtros de plataforma y categoría en Top Affiliate Products para centrar mi consulta en los productos relevantes.

## Requisitos funcionales

### Confirmados

- Solo Top Affiliate Products ofrece filtros. Los filtros por plataforma y categoría se pueden combinar; cada uno admite «Todas» como estado sin restricción.
- Plataforma y categoría son metadatos demo definidos para filtrar, no atribución de ventas.
- **Top Affiliate Products:** ordenar por Revenue descendente y, en caso de empate, por Conversion Rate descendente; mostrar hasta tres productos. La tasa se calcula desde los inputs demo por producto.
- Para otros rankings se aplican los criterios que aparezcan en las SPEC. Si no existen, mantener el orden original de los ejemplos y no presentarlos como clasificaciones “Top”. No crear oportunidades de mejora sin criterios y datos.
- Los datos de demostración son ilustrativos y no representan datos reales.
- Revenue disponible: B = 4.800 €, C = 4.800 €, A = 2.500 €. Los inputs demo producen C = 5,0 %, B = 3,0 % y A = 5,0 % de Conversion Rate; el orden final es C, B, A.

### Comportamiento pendiente

Si una combinación no produce coincidencias, mostrar exactamente «No hay resultados para los filtros seleccionados», sin filas ficticias ni acciones adicionales. No se filtran plataformas, campañas ni otros paneles. Los criterios de otros rankings y oportunidades de mejora siguen pendientes; sus ejemplos conservan el orden original y no se inventan oportunidades.

## Criterios de aceptación

1. Solo Top Affiliate Products responde a filtros de plataforma y categoría.
2. Los filtros pueden combinarse; el listado se ordena por Revenue y luego Conversion Rate, ambos descendentes, y muestra hasta tres filas.
3. Las facetas de filtro y entradas de tasa son ficticias, se etiquetan como demostración y no implican atribución.
4. Una combinación sin coincidencias muestra el mensaje aprobado sin filas ni acciones adicionales.
5. Los otros listados conservan su orden de origen; no se inventan rankings ni oportunidades.

## Fuera de alcance

- Añadir filtros a otras vistas o atribuir ventas usando facetas demo.
- Inventar tasas de conversión por producto o criterios para rankings y oportunidades no definidos.
- Persistencia de filtros o sincronización con servicios externos.

## Estado de implementación

Los filtros combinables están definidos como requisito, pero no se exponen controles en el HTML estático. La restricción del proyecto prohíbe JavaScript y no hay backend; T28 y T42 permanecen pendientes hasta que se apruebe una arquitectura que permita interacción.

## Cuestiones pendientes de definición

- ¿Cómo se representarán futuras entradas reales ausentes en las facetas demo?
- ¿Qué criterios definirán rankings para plataformas y campañas?
- ¿Qué datos o condiciones califican una oportunidad de mejora?
