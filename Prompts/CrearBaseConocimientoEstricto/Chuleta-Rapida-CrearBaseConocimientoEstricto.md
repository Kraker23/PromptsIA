# Chuleta rapida: comando /CrearBaseConocimientoEstricto en Copilot

## Uso
Escribe en Copilot Chat:

`/CrearBaseConocimientoEstricto`

## Que hace
- Explora el proyecto completo con criterio estricto de evidencia.
- Genera `Docs-Copilot/00-Preguntas.md` y se detiene.
- Solo tras tu confirmacion, genera la documentacion final y `.github/copilot-instructions.md`.

## Regla de bloqueo
- Sin confirmacion explicita del usuario, no se permite generar `01` a `05`.

## Si no aparece /CrearBaseConocimientoEstricto
1. Ejecuta `Chat: Configure Prompt Files`.
2. Si sigue sin salir, ejecuta `Developer: Reload Window`.

## Archivo del prompt
`Prompts/CrearBaseConocimientoEstricto/CrearBaseConocimientoEstricto.prompt.md`
