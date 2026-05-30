# Chuleta rapida: comando /DocumentacionIncidencias en Copilot

## Uso
Escribe en Copilot Chat:

`/DocumentacionIncidencias develop`

Tambien puedes usar `main` u otra rama base.

## Que hace
- Compara la rama actual contra la rama base con `git log` y `git diff`.
- Extrae ticket y nombre descriptivo desde la rama actual.
- Genera 4 documentos en `Docs/`:
  - Resumen del desarrollo
  - Funcional
  - Tecnica
  - Testeo

## Archivos generados
- `<ID_TICKET>-<NombreRama> - Resumen del desarrollo.md`
- `<ID_TICKET>-<NombreRama>-Funcional.md`
- `<ID_TICKET>-<NombreRama>-Tecnica.md`
- `<ID_TICKET>-<NombreRama>-Testeo.md`

## Si no aparece /DocumentacionIncidencias
1. Ejecuta `Chat: Configure Prompt Files`.
2. Si sigue sin salir, ejecuta `Developer: Reload Window`.

## Archivo del prompt
`Prompts/DocumentacionIncidencias/DocumentacionIncidencias.prompt.md`
