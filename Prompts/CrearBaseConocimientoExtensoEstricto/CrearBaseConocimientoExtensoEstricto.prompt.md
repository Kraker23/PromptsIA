---
description: "Construye una base de conocimiento exhaustiva con fases y controles de calidad estrictos"
name: "CrearBaseConocimientoExtensoEstricto"
agent: "agent"
---
Realiza una exploracion profunda del proyecto y genera documentacion exhaustiva bajo reglas estrictas de validacion.

Reglas:
- Fase 1 obligatoria de exploracion completa, cubriendo:
  - Estructura de solucion, responsabilidades por proyecto y dependencias.
  - Punto de entrada, DI, middlewares y flujo de configuracion.
  - Capas y contratos entre capas.
  - Interfaces, implementaciones y consumidores.
  - Entidades, DTOs, enums, objetos de configuracion, campos y relaciones.
  - Servicios, logica de negocio, cache, recarga y estados.
  - Paginas, componentes, rutas, roles y origen de datos.
  - Configuracion por `appsettings`, variables de entorno y switches.
  - Codigo comentado, deshabilitado o en desuso.
  - Flujos extremo a extremo.
- Crea `Docs-Copilot/00-Preguntas.md` con formato exacto y agrupado por tema.
- Incluye todas las dudas no deducibles del codigo, sin filtrar por conveniencia.
- Bloqueo obligatorio: no generes documentos finales hasta recibir confirmacion explicita del usuario.
- Tras confirmacion, genera exactamente:
  - `Docs-Copilot/01-Resumen-Proyecto.md`
  - `Docs-Copilot/02-Arquitectura-Capas.md`
  - `Docs-Copilot/03-Modelos-Datos.md`
  - `Docs-Copilot/04-Paginas-Navegacion.md`
  - `Docs-Copilot/05-Logica-Negocio-Flujos.md`
- `02-Arquitectura-Capas.md` debe incluir diagrama ASCII y flujo de peticion completo.
- `03-Modelos-Datos.md` debe incluir tablas de campos y relaciones explicitas o implicitas.
- `04-Paginas-Navegacion.md` debe identificar claramente elementos en desuso.
- `05-Logica-Negocio-Flujos.md` debe incluir reglas con casos limite, calculos con formulas y transiciones de estado.
- Crea `.github/copilot-instructions.md` con reglas operativas, tecnologias a priorizar, tecnologias a evitar y advertencias criticas.
- Si surge nueva informacion relevante, actualiza el documento correspondiente y registra el ajuste.
- Si detectas contradicciones, agrega nuevas preguntas a `00-Preguntas.md`.
- En todos los docs finales incluye `Suposiciones y limites` cuando exista informacion parcial.
- Escribe todo en espanol.

No hacer:
- No resumir en exceso ni omitir capas por falta de tiempo.
- No convertir dudas en afirmaciones.
- No cerrar la documentacion final con huecos sin marcar.
- No ignorar codigo deshabilitado si impacta decisiones tecnicas.