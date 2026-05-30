
Vamos a trabajar juntos en este proyecto durante mucho tiempo y necesito que lo conozcas 
en profundidad antes de tocar nada.

## FASE 1 — Exploración autónoma

Antes de generar nada, explora el proyecto por tu cuenta:

- Estructura de la solución: proyectos, dependencias entre ellos y su responsabilidad
- Punto de entrada: Program.cs / Startup, inyección de dependencias, middlewares, configuración
- Capas de la arquitectura: qué proyecto hace qué, cómo se comunican entre sí
- Interfaces y contratos: qué interfaces existen, quién las implementa y quién las consume
- Modelos de datos: entidades, DTOs, enums, objetos de configuración, sus campos y relaciones
- Servicios y lógica de negocio: qué hace cada servicio, qué cachea, cómo se recarga
- Páginas y componentes: rutas, roles, qué datos cargan y cómo interactúan con los servicios
- Configuración: appsettings.json, variables de entorno, switches importantes
- Archivos comentados o en desuso: identifícalos y anótalos como tal
- Flujos clave: sigue el código de extremo a extremo para los flujos principales

## FASE 2 — Archivo de preguntas

Genera el archivo "Docs-Copilot/00-Preguntas.md" con TODAS las preguntas que necesites,
agrupadas por tema y con este formato exacto:

---
# Preguntas sobre el proyecto

## [Tema — ej: Lógica de negocio]
**P1:** ¿Pregunta?
**R:** _[responde aquí]_

**P2:** ¿Pregunta?
**R:** _[responde aquí]_

## [Tema — ej: Arquitectura]
**P3:** ¿Pregunta?
**R:** _[responde aquí]_
---

Pregunta sobre todo lo que no puedas deducir del código:
- Lógica de negocio y reglas no evidentes
- Decisiones de diseño que parezcan intencionadas pero no sean obvias
- Funcionalidades comentadas, deshabilitadas o en desuso y por qué
- Flujos que dependan de intervención manual
- Datos o configuraciones que vengan de fuera del código
- Cualquier cosa que parezca un TODO, deuda técnica o workaround conocido

**No generes nada más hasta que el usuario confirme que ha respondido todas las preguntas.**

## FASE 3 — Documentación

Cuando el usuario te avise, lee "Docs-Copilot/00-Preguntas.md" con las respuestas 
y genera en "Docs-Copilot/" los siguientes archivos:

**01-Resumen-Proyecto.md**
- Qué es el proyecto y para qué sirve
- Tecnologías, frameworks y librerías principales con su versión
- Estructura de proyectos con la responsabilidad de cada uno
- Roles de usuario y qué puede hacer cada uno
- Flujo general de la aplicación de principio a fin

**02-Arquitectura-Capas.md**
- Diagrama de capas en ASCII
- Cómo fluye una petición desde la UI hasta los datos
- Interfaces clave y quién las implementa
- Inyección de dependencias: qué se registra y con qué ciclo de vida
- Patrones de diseño utilizados
- Decisiones de arquitectura importantes y su razonamiento

**03-Modelos-Datos.md**
- Todas las entidades con tabla, campos, tipos y descripción de cada campo
- DTOs y objetos intermedios: para qué sirven y dónde se usan
- Enums con sus valores y significado
- Objetos de configuración con su sección en appsettings y valores posibles
- Relaciones entre entidades aunque no sean FK explícitas en el código

**04-Paginas-Navegacion.md**
- Todas las páginas con ruta, rol requerido y descripción de lo que hace
- Qué servicios inyecta cada página y para qué
- Componentes reutilizables: qué son, qué parámetros aceptan y dónde se usan
- Páginas o componentes en desuso, marcados claramente
- Flujo de navegación entre páginas

**05-Logica-Negocio-Flujos.md**
- Cada flujo clave documentado paso a paso con las llamadas exactas entre capas
- Reglas de negocio con ejemplos concretos y casos límite
- Cálculos importantes explicados con fórmulas y ejemplos numéricos
- Estados posibles de las entidades principales y sus transiciones
- Funcionalidades deshabilitadas con la razón y el estado actual
- TODOs, deuda técnica y workarounds conocidos

## FASE 4 — Instrucciones para Copilot

Crea ".github/copilot-instructions.md" que incluya:
- Instrucción de leer toda la documentación de Docs-Copilot/ antes de responder
- Las reglas y convenciones más importantes del proyecto como recordatorio rápido
- Qué tecnologías priorizar y cuáles evitar
- Qué archivos están en desuso y no deben tocarse
- Cualquier advertencia importante para no romper el proyecto
- Siempre en español

## REGLAS DEL PROCESO

- No pases a la Fase 3 hasta que el usuario confirme que ha respondido en "00-Preguntas.md"
- Si en cualquier momento del trabajo posterior descubres algo nuevo importante, 
  actualiza la documentación correspondiente
- Si algo del código es confuso o contradictorio, añádelo como pregunta en "00-Preguntas.md"
- Sé exhaustivo: prefiero más detalle que menos
- Escribe todo en español.