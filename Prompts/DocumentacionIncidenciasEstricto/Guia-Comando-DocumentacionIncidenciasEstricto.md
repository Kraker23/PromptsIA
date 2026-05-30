# Guia del comando /DocumentacionIncidenciasEstricto en Copilot Chat

## Objetivo
Generar documentacion de incidencia de nivel formal, auditable y basada exclusivamente en cambios reales de git.

## Enfoque estricto
- Validacion previa de entradas (rama base, rama actual, ticket, nombre).
- Ejecucion obligatoria de `git log` y `git diff`.
- Bloqueo ante errores para evitar entregables inconsistentes.

## Flujo
1. Ejecuta `/DocumentacionIncidenciasEstricto <ramaBase>`.
2. Copilot valida datos y ejecuta comandos git.
3. Si todo es correcto, genera los 4 documentos en `Docs/`.
4. Si algo falla, informa y detiene generacion.

## Estructura de salida
- `Resumen del desarrollo`: portada no tecnica y mapa de cambios.
- `Funcional`: impacto por negocio/producto.
- `Tecnica`: detalle por archivo, riesgo y trazabilidad.
- `Testeo`: casos manuales y registro de resultados.

## Reglas de calidad
- No hay secciones vacias sin justificar.
- Todo cambio critico debe tener riesgo y prueba asociada.
- Cada documento debe incluir evidencia git resumida.

## Ubicacion del prompt
`Prompts/DocumentacionIncidenciasEstricto/DocumentacionIncidenciasEstricto.prompt.md`

## Si no aparece en el menu de /
- Ejecuta `Chat: Configure Prompt Files`.
- O recarga la ventana con `Developer: Reload Window`.

## Referencia
Cumple `Docs/08-Normalizacion-Prompts.md`.
