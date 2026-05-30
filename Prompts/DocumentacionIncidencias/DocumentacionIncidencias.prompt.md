---
description: "Genera documentacion tecnica, funcional y de pruebas para una rama de incidencia"
name: "DocumentacionIncidencias"
argument-hint: "ramaBase"
agent: "agent"
---
Analiza la rama actual frente a la rama base y genera un paquete de documentacion de incidencia en `Docs/`.

Reglas:
- Usa como rama base lo que el usuario escriba tras `/DocumentacionIncidencias`.
- Si no se indica rama base tras el comando, pide `${input:ramaBase:Indica la rama base (ej: develop o main)}`.
- Obtiene la rama actual ejecutando `git branch --show-current`.
- Extrae `ID_TICKET` y `NombreRama` desde la rama actual con la convencion `feature/TICKET-1234-Descripcion`.
- Si no puedes deducir `ID_TICKET` o `NombreRama`, pide:
  - `${input:idTicket:Indica el ID del ticket (ej: ISBS-5123)}`
  - `${input:nombreRama:Indica el nombre descriptivo (ej: MejorasIA)}`
- Ejecuta obligatoriamente:
  - `git log <RAMA_BASE>..HEAD --oneline`
  - `git diff <RAMA_BASE>...HEAD`
- Basa toda la documentacion en los cambios reales detectados en esos comandos.
- Genera exactamente estos archivos en `Docs/`:
  - `<ID_TICKET>-<NombreRama>-Tecnica.md`
  - `<ID_TICKET>-<NombreRama>-Funcional.md`
  - `<ID_TICKET>-<NombreRama>-Testeo.md`
  - `<ID_TICKET>-<NombreRama> - Resumen del desarrollo.md`
- Crea primero el archivo de resumen y usalo como portada del conjunto.

Reglas para `Resumen del desarrollo`:
- Incluye tabla de metadatos: Incidencia, Nombre, Rama, Commit, Proyecto, Fecha, Estado.
- Incluye seccion `¿De que trata esta incidencia?` en lenguaje llano para publico no tecnico.
- Incluye un callout de sintesis con blockquote y emoji `💡`.
- Incluye seccion `Cambios mas importantes` separada por tematica (seguridad, bugs, mejoras), con emojis y sin jerga tecnica.
- Incluye tabla de archivos modificados con: archivo, tipo de cambio (con emoji), descripcion breve.
- Incluye tabla `Documentacion relacionada` con los otros 3 documentos, audiencia y contenido.
- No incluyas pasos ni decisiones tecnicas en este archivo.

Reglas para `Funcional`:
- Incluye tabla de metadatos y audiencia: `Producto · Negocio · Gestores · Cualquier persona del equipo`.
- Incluye parrafo introductorio explicando proposito y audiencia.
- Para cada cambio visible usa bloques: `¿Que pasaba antes?` / `¿Que pasa ahora?` / `¿Por que importa?`.
- Incluye seccion de seguridad en lenguaje accesible.
- Incluye seccion de correcciones de comportamiento incorrecto.
- Incluye seccion de mejoras internas en tabla resumida sin codigo.
- Incluye tabla final `¿Que esperar ahora?` por area de aplicacion.
- Incluye glosario final de terminos tecnicos usados.
- No incluyas bloques de codigo.

Reglas para `Tecnica`:
- Incluye tabla de metadatos y audiencia: `Desarrolladores · Revisores de codigo · Tech Leads`.
- Incluye introduccion con referencia al documento funcional para publico no tecnico.
- Incluye tabla de resumen por capa: Datos, Servicios, Controladores, Paginas, Configuracion.
- Para cada archivo modificado documenta: problema detectado, solucion aplicada y bloque `Antes / Despues`.
- Marca los cambios criticos con `⚠️` y advertencia de riesgo de regresion.
- Incluye tabla final de archivos afectados con columna `Riesgo de regresion` (Alto/Medio/Bajo).
- Incluye callout final con el cambio de mayor riesgo y referencia al caso de prueba asociado.

Reglas para `Testeo`:
- Incluye tabla de metadatos, tipo de pruebas `Manual — entorno local en modo Debug` y audiencia.
- Incluye introduccion en lenguaje no tecnico con referencia al documento funcional.
- Incluye prerequisitos como lista de checkboxes.
- Para cada caso `TC-NN`, incluye:
  - Mini tabla con que se verifica, prioridad (`🔴`, `🟡`, `🟢`) y cambio relacionado.
  - Pasos numerados en lenguaje accesible (sin codigo interno).
  - Seccion `¿Que debe pasar?`.
  - Senal de fallo con `🚨` cuando aplique.
- El caso del cambio mas critico debe incluir `⚠️` en el titulo.
- Incluye tabla final de resultados con: ID, caso, prioridad, resultado, observaciones, ejecutado por, fecha.
- Incluye leyenda: `✅ Correcto — ❌ Fallo — ⚠️ Parcial — ⬜ Pendiente`.

Reglas generales:
- Usa emojis como guias visuales en titulos y tablas.
- Usa tablas de metadatos en cabecera (no blockquotes sueltos).
- Asegura que `Funcional` y `Testeo` sean comprensibles para personas sin perfil tecnico.
- Mantiene precision tecnica y trazabilidad en `Tecnica`.
- Escribe todo en espanol.
- Incluye este pie en los 4 archivos:
  - `*Generado para la incidencia \`<ID_TICKET>\` — rama \`<NOMBRE_RAMA>\`*`

No hacer:
- No generar contenido sin ejecutar `git log` y `git diff` contra la rama base.
- No omitir archivos modificados relevantes de la rama.
- No mezclar lenguaje tecnico avanzado en secciones orientadas a negocio o QA.