---
description: "Genera documentacion de incidencia con trazabilidad estricta basada en git"
name: "DocumentacionIncidenciasEstricto"
argument-hint: "ramaBase"
agent: "agent"
---
Genera documentacion de incidencia en `Docs/` usando solo cambios verificables de git y validaciones estrictas.

Reglas:
- Usa como rama base el texto tras `/DocumentacionIncidenciasEstricto`.
- Si no hay rama base, solicita `${input:ramaBase:Indica la rama base (ej: develop o main)}`.
- Obtiene rama actual con `git branch --show-current`.
- Extrae `ID_TICKET` y `NombreRama` desde la rama actual con convencion `feature/TICKET-1234-Descripcion`.
- Si no se puede extraer alguno, solicita obligatoriamente:
  - `${input:idTicket:Indica el ID del ticket (ej: ISBS-5123)}`
  - `${input:nombreRama:Indica el nombre descriptivo (ej: MejorasIA)}`
- Ejecuta de forma obligatoria:
  - `git log <RAMA_BASE>..HEAD --oneline`
  - `git diff <RAMA_BASE>...HEAD`
- Bloqueo: si alguno de los comandos falla, detente y reporta el error; no generes documentos incompletos.
- Genera exactamente estos archivos en `Docs/`:
  - `<ID_TICKET>-<NombreRama>-Tecnica.md`
  - `<ID_TICKET>-<NombreRama>-Funcional.md`
  - `<ID_TICKET>-<NombreRama>-Testeo.md`
  - `<ID_TICKET>-<NombreRama> - Resumen del desarrollo.md`
- Crea primero `Resumen del desarrollo` y utilialo como portada.

Reglas para `Resumen del desarrollo`:
- Tabla de metadatos obligatoria: Incidencia, Nombre, Rama, Commit, Proyecto, Fecha, Estado.
- Seccion `¿De que trata esta incidencia?` en lenguaje llano.
- Callout de sintesis con blockquote y emoji `💡`.
- Seccion `Cambios mas importantes` separada por seguridad, bugs y mejoras, con emojis.
- Tabla completa de archivos modificados con tipo de cambio y descripcion breve.
- Tabla `Documentacion relacionada` con los otros 3 documentos y audiencia.
- Prohibido incluir pasos tecnicos o decisiones de implementacion.

Reglas para `Funcional`:
- Tabla de metadatos y audiencia obligatoria.
- Introduccion sobre objetivo y publico.
- Para cada cambio visible: `¿Que pasaba antes?`, `¿Que pasa ahora?`, `¿Por que importa?`.
- Seccion de seguridad accesible para no tecnicos.
- Seccion de correcciones de comportamiento incorrecto.
- Seccion de mejoras internas en tabla sin codigo.
- Tabla final `¿Que esperar ahora?` por area.
- Glosario final de terminos tecnicos.
- Prohibido usar bloques de codigo.

Reglas para `Tecnica`:
- Tabla de metadatos y audiencia obligatoria.
- Introduccion con referencia al documento funcional.
- Tabla de resumen por capa: Datos, Servicios, Controladores, Paginas, Configuracion.
- Por archivo modificado: problema, solucion y bloque `Antes / Despues`.
- Cambios criticos marcados con `⚠️` y advertencia de regresion.
- Tabla final con `Riesgo de regresion` (Alto/Medio/Bajo).
- Callout final con el cambio de mayor riesgo y caso de prueba asociado.

Reglas para `Testeo`:
- Tabla de metadatos con tipo de prueba `Manual — entorno local en modo Debug` y audiencia.
- Introduccion sin jerga tecnica con referencia al funcional.
- Prerrequisitos en checkboxes.
- Cada caso `TC-NN` debe incluir mini tabla con verificacion, prioridad (`🔴`, `🟡`, `🟢`) y cambio relacionado.
- Pasos numerados en lenguaje accesible.
- Seccion `¿Que debe pasar?` obligatoria por caso.
- Marcar fallos relevantes con `🚨`.
- Caso mas critico con `⚠️` en el titulo.
- Tabla final de resultados: ID, caso, prioridad, resultado, observaciones, ejecutado por, fecha.
- Leyenda obligatoria: `✅ Correcto — ❌ Fallo — ⚠️ Parcial — ⬜ Pendiente`.

Reglas generales:
- Todo en espanol.
- Usa emojis en titulos y tablas como guia visual.
- `Funcional` y `Testeo` deben ser entendibles por perfiles no tecnicos.
- `Tecnica` debe mantener detalle referenciable por archivo.
- Incluye pie obligatorio en los 4 documentos:
  - `*Generado para la incidencia \`<ID_TICKET>\` — rama \`<NOMBRE_RAMA>\`*`
- Incluye seccion `Evidencia git utilizada` en cada archivo con resumen de commits y diff aplicados.

No hacer:
- No generar contenido sin `git log` y `git diff` exitosos.
- No omitir archivos modificados de impacto medio o alto.
- No mezclar tecnicismos en secciones dirigidas a negocio o QA.
- No entregar documentos con placeholders sin marcar como pendiente.