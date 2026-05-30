# Chuleta rapida: comando /CrearBaseConocimientoExtenso en Copilot

## Uso
Escribe en Copilot Chat:

`/CrearBaseConocimientoExtenso`

## Que hace
- Ejecuta una exploracion tecnica exhaustiva del proyecto.
- Genera `Docs-Copilot/00-Preguntas.md` con dudas agrupadas por tema.
- Espera tu confirmacion.
- Tras confirmar, genera 5 documentos detallados y `.github/copilot-instructions.md`.

## Entregables finales
- `Docs-Copilot/01-Resumen-Proyecto.md`
- `Docs-Copilot/02-Arquitectura-Capas.md`
- `Docs-Copilot/03-Modelos-Datos.md`
- `Docs-Copilot/04-Paginas-Navegacion.md`
- `Docs-Copilot/05-Logica-Negocio-Flujos.md`
- `.github/copilot-instructions.md`

## Si no aparece /CrearBaseConocimientoExtenso
1. Ejecuta `Chat: Configure Prompt Files`.
2. Si sigue sin salir, ejecuta `Developer: Reload Window`.

## Archivo del prompt
`Prompts/CrearBaseConocimientoExtenso/CrearBaseConocimientoExtenso.prompt.md`
