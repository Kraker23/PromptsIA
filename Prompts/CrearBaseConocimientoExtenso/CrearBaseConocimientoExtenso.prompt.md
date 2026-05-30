---
description: "Analiza el proyecto a fondo y construye documentacion exhaustiva por fases"
name: "CrearBaseConocimientoExtenso"
agent: "agent"
---
Explora en profundidad el proyecto y construye una base de conocimiento extensa en fases controladas.

Reglas:
- Ejecuta una exploracion autonoma completa antes de generar documentacion final.
- Durante la exploracion, cubre al menos estos temas:
  - Estructura de la solucion, dependencias entre proyectos y responsabilidad de cada uno.
  - Punto de entrada (`Program.cs`/`Startup`), inyeccion de dependencias, middlewares y configuracion.
  - Capas de arquitectura y comunicacion entre capas.
  - Interfaces/contratos, implementaciones y consumidores.
  - Modelos de datos: entidades, DTOs, enums, configuracion, campos y relaciones.
  - Servicios y logica de negocio, incluyendo cache y mecanismos de recarga.
  - Paginas/componentes, rutas, roles y origen de datos.
  - Configuracion (`appsettings`, variables de entorno, switches relevantes).
  - Codigo comentado, en desuso o deshabilitado.
  - Flujos clave seguidos extremo a extremo.
- Crea `Docs-Copilot/00-Preguntas.md` con todas las dudas no deducibles del codigo usando este formato exacto:
  - `# Preguntas sobre el proyecto`
  - `## [Tema]`
  - `**P1:** <pregunta>`
  - `**R:** _[responde aqui]_`
- Pregunta sobre reglas no evidentes, decisiones de diseno, dependencias externas, pasos manuales, TODOs, deuda tecnica y workarounds.
- No generes ningun otro archivo hasta que el usuario confirme que respondio `00-Preguntas.md`.
- Cuando el usuario confirme, lee `Docs-Copilot/00-Preguntas.md` y genera en `Docs-Copilot/`:
  - `01-Resumen-Proyecto.md`
  - `02-Arquitectura-Capas.md`
  - `03-Modelos-Datos.md`
  - `04-Paginas-Navegacion.md`
  - `05-Logica-Negocio-Flujos.md`
- En `02-Arquitectura-Capas.md`, incluye un diagrama de capas en ASCII y el flujo de una peticion de punta a punta.
- En `03-Modelos-Datos.md`, documenta entidades, DTOs, enums, objetos de configuracion y relaciones.
- En `04-Paginas-Navegacion.md`, documenta rutas, roles, servicios inyectados, componentes reutilizables y elementos en desuso.
- En `05-Logica-Negocio-Flujos.md`, incluye flujos paso a paso, reglas con casos limite, calculos con formulas, estados/transiciones y deuda tecnica.
- Crea tambien `.github/copilot-instructions.md` con reglas del proyecto, tecnologias a priorizar/evitar, archivos en desuso y advertencias para no romper el sistema.
- Si durante fases posteriores aparece nueva informacion importante, actualiza los documentos correspondientes.
- Si detectas contradicciones o ambiguedades nuevas, agregalas como preguntas en `00-Preguntas.md`.
- Escribe todo en espanol.

No hacer:
- No avanzar a la fase de documentacion final sin confirmacion explicita del usuario.
- No omitir incertidumbres: conviertelas en preguntas trazables.
- No simplificar en exceso: prioriza cobertura y detalle.