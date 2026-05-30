---
description: "Explora el proyecto con control estricto y documenta solo con evidencias verificadas"
name: "CrearBaseConocimientoEstricto"
agent: "agent"
---
Ejecuta una exploracion completa del proyecto y construye la base de conocimiento con control estricto por fases.

Reglas:
- Fase 1 obligatoria: explora solucion, proyectos, capas, servicios, modelos, interfaces, paginas y configuracion.
- Lee codigo real de archivos clave antes de concluir cualquier hallazgo.
- Registra solo hechos verificables en codigo o configuracion; toda inferencia debe etiquetarse como `Suposicion`.
- Crea `Docs-Copilot/00-Preguntas.md` con formato exacto:
  - `# Preguntas sobre el proyecto`
  - `## [Tema]`
  - `**P1:** <pregunta>`
  - `**R:** _[responde aqui]_`
- Incluye preguntas sobre reglas de negocio no evidentes, decisiones de diseno, integraciones externas, pasos manuales, TODOs y deuda tecnica.
- Bloqueo obligatorio: no generes ningun archivo adicional hasta confirmacion explicita del usuario indicando que respondio `00-Preguntas.md`.
- Tras confirmacion, lee `Docs-Copilot/00-Preguntas.md` y genera exactamente:
  - `Docs-Copilot/01-Resumen-Proyecto.md`
  - `Docs-Copilot/02-Arquitectura-Capas.md`
  - `Docs-Copilot/03-Modelos-Datos.md`
  - `Docs-Copilot/04-Paginas-Navegacion.md`
  - `Docs-Copilot/05-Logica-Negocio-Flujos.md`
- Crea `.github/copilot-instructions.md` con convenciones, reglas criticas y advertencias de seguridad del proyecto.
- En cada documento final agrega seccion `Trazabilidad de fuentes` con lista de archivos analizados.
- Escribe todo en espanol.

No hacer:
- No avanzar a fase de documentacion final sin confirmacion explicita.
- No ocultar incertidumbres: conviertelas en preguntas.
- No inventar datos de negocio, integraciones o configuraciones.
- No omitir evidencia de origen cuando describas arquitectura o logica.