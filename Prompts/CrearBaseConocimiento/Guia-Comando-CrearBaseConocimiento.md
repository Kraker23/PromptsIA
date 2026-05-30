# Guia del comando /CrearBaseConocimiento en Copilot Chat

## Objetivo
Crear una base de conocimiento del proyecto en dos fases: primero preguntas, luego documentacion completa validada con tus respuestas.

## Enfoque
Este comando se implementa como Prompt File (`.prompt.md`) y esta pensado para un flujo iterativo con pausa obligatoria tras `00-Preguntas.md`.

## Ubicacion en el repositorio
`Prompts/CrearBaseConocimiento/CrearBaseConocimiento.prompt.md`

## Como usarlo
1. Abre Copilot Chat.
2. Escribe `/CrearBaseConocimiento`.
3. Espera a que se genere `Docs-Copilot/00-Preguntas.md`.
4. Completa las respuestas en ese archivo.
5. Indica en el chat que ya esta respondido.
6. Copilot generara el resto de documentos en `Docs-Copilot/` y `.github/copilot-instructions.md`.

## Entregables esperados
- `Docs-Copilot/00-Preguntas.md`
- `Docs-Copilot/01-Resumen-Proyecto.md`
- `Docs-Copilot/02-Arquitectura-Capas.md`
- `Docs-Copilot/03-Modelos-Datos.md`
- `Docs-Copilot/04-Paginas-Navegacion.md`
- `Docs-Copilot/05-Logica-Negocio-Flujos.md`
- `.github/copilot-instructions.md`

## Cuando usar este comando
- Cuando necesitas una base de conocimiento inicial sin forzar una exploracion extrema.
- Cuando quieres validar supuestos antes de documentar en detalle.

## Si no aparece en el menu de /
- Ejecuta `Chat: Configure Prompt Files`.
- O recarga la ventana con `Developer: Reload Window`.

## Referencia de normalizacion
Este comando sigue el estandar definido en `Docs/08-Normalizacion-Prompts.md`.
