# Chuleta rapida: comando /CrearBaseConocimiento en Copilot

## Uso
Escribe en Copilot Chat:

`/CrearBaseConocimiento`

## Que hace
- Explora el proyecto completo y crea `Docs-Copilot/00-Preguntas.md` con dudas por tema.
- Se detiene hasta que respondas ese archivo.
- Tras tu confirmacion, genera la base de conocimiento completa en `Docs-Copilot/` y `.github/copilot-instructions.md`.

## Flujo
1. Ejecutas `/CrearBaseConocimiento`.
2. Copilot crea `00-Preguntas.md`.
3. Respondes el archivo.
4. Avisas que esta respondido.
5. Copilot genera `01` a `05` y las instrucciones de Copilot.

## Si no aparece /CrearBaseConocimiento
1. Ejecuta `Chat: Configure Prompt Files`.
2. Si sigue sin salir, ejecuta `Developer: Reload Window`.

## Archivo del prompt
`Prompts/CrearBaseConocimiento/CrearBaseConocimiento.prompt.md`
