# Guia del comando /CrearBaseConocimientoExtenso en Copilot Chat

## Objetivo
Construir una base de conocimiento profunda y mantenible, con control estricto por fases y cobertura amplia de arquitectura, datos, logica y navegacion.

## Diferencia frente a /CrearBaseConocimiento
`/CrearBaseConocimientoExtenso` exige mayor detalle, seguimiento de flujos extremo a extremo y documentacion mas exhaustiva en cada salida.

## Flujo de trabajo
1. Ejecuta `/CrearBaseConocimientoExtenso`.
2. Copilot explora el proyecto en profundidad.
3. Copilot crea `Docs-Copilot/00-Preguntas.md`.
4. Responde las preguntas en ese archivo.
5. Confirma en chat que ya esta respondido.
6. Copilot genera la documentacion final y `.github/copilot-instructions.md`.

## Cobertura minima esperada
- Arquitectura por capas y dependencias.
- Punto de entrada, DI, middlewares y configuracion.
- Interfaces, implementaciones y consumidores.
- Entidades/DTOs/enums/configuraciones con campos y relaciones.
- Paginas, componentes, rutas, roles y servicios.
- Flujos de negocio con reglas, calculos, estados y transiciones.
- Deuda tecnica, TODOs y elementos en desuso.

## Ubicacion del prompt
`Prompts/CrearBaseConocimientoExtenso/CrearBaseConocimientoExtenso.prompt.md`

## Si no aparece en el menu de /
- Ejecuta `Chat: Configure Prompt Files`.
- O recarga la ventana con `Developer: Reload Window`.

## Normalizacion
Este comando sigue el estandar de `Docs/08-Normalizacion-Prompts.md`.
