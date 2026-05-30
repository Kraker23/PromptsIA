# Chuleta rapida: comando /DocumentacionIncidenciasEstricto en Copilot

## Uso
Escribe en Copilot Chat:

`/DocumentacionIncidenciasEstricto develop`

## Que hace
- Valida rama actual, ticket y rama base.
- Ejecuta `git log` y `git diff` como requisito obligatorio.
- Si hay error en git, se detiene.
- Genera 4 documentos en `Docs/` con trazabilidad estricta.

## Archivos generados
- `<ID_TICKET>-<NombreRama> - Resumen del desarrollo.md`
- `<ID_TICKET>-<NombreRama>-Funcional.md`
- `<ID_TICKET>-<NombreRama>-Tecnica.md`
- `<ID_TICKET>-<NombreRama>-Testeo.md`

## Regla de bloqueo
- Sin evidencia git valida, no se permite generar la documentacion.

## Si no aparece /DocumentacionIncidenciasEstricto
1. Ejecuta `Chat: Configure Prompt Files`.
2. Si sigue sin salir, ejecuta `Developer: Reload Window`.

## Archivo del prompt
`Prompts/DocumentacionIncidenciasEstricto/DocumentacionIncidenciasEstricto.prompt.md`
