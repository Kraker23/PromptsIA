# Guia del comando /CrearBaseConocimientoEstricto en Copilot Chat

## Objetivo
Crear una base de conocimiento confiable, auditable y trazable, minimizando suposiciones.

## Principios estrictos
- Evidencia primero: no hay conclusiones sin lectura de codigo.
- Fases bloqueadas: preguntas primero, documentacion despues.
- Trazabilidad explicita: toda seccion relevante debe poder rastrearse a archivos fuente.

## Flujo
1. Ejecuta `/CrearBaseConocimientoEstricto`.
2. Copilot analiza proyecto y crea `Docs-Copilot/00-Preguntas.md`.
3. Respondes el archivo.
4. Confirmas en chat que esta completo.
5. Copilot genera `01` a `05` y `.github/copilot-instructions.md`.

## Entregables
- `Docs-Copilot/00-Preguntas.md`
- `Docs-Copilot/01-Resumen-Proyecto.md`
- `Docs-Copilot/02-Arquitectura-Capas.md`
- `Docs-Copilot/03-Modelos-Datos.md`
- `Docs-Copilot/04-Paginas-Navegacion.md`
- `Docs-Copilot/05-Logica-Negocio-Flujos.md`
- `.github/copilot-instructions.md`

## Ubicacion del prompt
`Prompts/CrearBaseConocimientoEstricto/CrearBaseConocimientoEstricto.prompt.md`

## Si no aparece en el menu de /
- Ejecuta `Chat: Configure Prompt Files`.
- O recarga la ventana con `Developer: Reload Window`.

## Referencia
Alineado con `Docs/08-Normalizacion-Prompts.md`.
