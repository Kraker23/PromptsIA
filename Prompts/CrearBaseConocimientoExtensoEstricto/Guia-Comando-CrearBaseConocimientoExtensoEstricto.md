# Guia del comando /CrearBaseConocimientoExtensoEstricto en Copilot Chat

## Objetivo
Documentar el proyecto con profundidad maxima, trazabilidad y control de incertidumbre.

## Enfoque estricto
- Cobertura amplia y validada por lectura de codigo.
- Preguntas obligatorias para cerrar lagunas.
- Documentacion final solo tras confirmacion explicita.

## Flujo de trabajo
1. Ejecuta `/CrearBaseConocimientoExtensoEstricto`.
2. Copilot realiza exploracion profunda.
3. Copilot crea `Docs-Copilot/00-Preguntas.md`.
4. Respondes las preguntas.
5. Confirmas en chat.
6. Copilot genera `01` a `05` y `.github/copilot-instructions.md`.

## Contenido esperado en salida
- `01-Resumen-Proyecto.md`: alcance, stack, roles, flujo general.
- `02-Arquitectura-Capas.md`: diagrama ASCII, dependencias, DI, patrones.
- `03-Modelos-Datos.md`: entidades, DTOs, enums, configuraciones y relaciones.
- `04-Paginas-Navegacion.md`: rutas, roles, servicios, componentes, desuso.
- `05-Logica-Negocio-Flujos.md`: flujos, reglas, calculos, estados, deuda tecnica.

## Ubicacion del prompt
`Prompts/CrearBaseConocimientoExtensoEstricto/CrearBaseConocimientoExtensoEstricto.prompt.md`

## Si no aparece en el menu de /
- Ejecuta `Chat: Configure Prompt Files`.
- O recarga la ventana con `Developer: Reload Window`.

## Referencia
Cumple `Docs/08-Normalizacion-Prompts.md`.
