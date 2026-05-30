---
description: "Explora el proyecto y crea una base de conocimiento guiada por preguntas"
name: "CrearBaseConocimiento"
agent: "agent"
---
Explora el proyecto, genera preguntas clave y crea la documentacion cuando el usuario confirme las respuestas.

Reglas:
- Recorre toda la estructura del proyecto: solucion, proyectos, archivos principales, paginas, servicios, modelos, interfaces y configuracion.
- Lee el codigo de los archivos mas importantes para entender el funcionamiento real, no solo la estructura.
- Crea el archivo `Docs-Copilot/00-Preguntas.md` agrupando todas las dudas por tema y usando este formato exacto:
  - `## [Tema]`
  - `**P1:** <pregunta>`
  - `**R:** _[responde aqui]_`
- Incluye preguntas sobre logica de negocio, decisiones de diseno, configuraciones externas, flujo funcional, deuda tecnica y cualquier contradiccion detectada.
- Despues de crear `Docs-Copilot/00-Preguntas.md`, detente y no generes ningun otro archivo hasta que el usuario confirme que respondio todo.
- Cuando el usuario confirme que ya respondio, lee `Docs-Copilot/00-Preguntas.md` y genera en `Docs-Copilot/` los archivos:
  - `01-Resumen-Proyecto.md`
  - `02-Arquitectura-Capas.md`
  - `03-Modelos-Datos.md`
  - `04-Paginas-Navegacion.md`
  - `05-Logica-Negocio-Flujos.md`
- Crea tambien `.github/copilot-instructions.md` indicando que Copilot debe leer `Docs-Copilot/` antes de responder y respetar reglas/convenios del proyecto.
- Escribe todo en espanol.

No hacer:
- No inventes reglas de negocio que no esten en el codigo o en las respuestas del usuario.
- No saltes a la fase de documentacion completa sin confirmacion explicita del usuario.
- No omitas temas con incertidumbre: conviertelos en preguntas en `00-Preguntas.md`.