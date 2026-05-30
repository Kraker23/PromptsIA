# Guia del comando /DocumentacionIncidencias en Copilot Chat

## Objetivo
Generar documentacion consistente de una incidencia a partir de cambios reales en git, separada por audiencias: negocio, desarrollo y QA.

## Enfoque
El comando ejecuta `git log` y `git diff` contra una rama base para construir 4 documentos conectados entre si.

## Requisitos previos
- Estar en la rama de trabajo de la incidencia.
- Tener git disponible en el entorno.
- Conocer la rama base (normalmente `develop` o `main`).
- Seguir una convencion de nombre de rama con ticket y descripcion.

## Uso recomendado
1. Abre Copilot Chat.
2. Ejecuta `/DocumentacionIncidencias develop`.
3. Revisa los 4 archivos generados en `Docs/`.
4. Ajusta detalles de redaccion si necesitas una adaptacion especifica para Confluence.

## Estructura de salida
- `Resumen del desarrollo`: portada para no tecnicos y mapa de cambios.
- `Funcional`: impacto visible para producto/negocio.
- `Tecnica`: detalle por archivo, riesgo y trazabilidad.
- `Testeo`: casos de prueba manuales y registro de resultados.

## Metodologia obligatoria
- Basar la documentacion en diferencias reales de la rama.
- Mantener lenguaje accesible en funcional/testeo.
- Mantener precision en tecnica.
- Incluir pie de trazabilidad en todos los documentos.

## Ubicacion del prompt
`Prompts/DocumentacionIncidencias/DocumentacionIncidencias.prompt.md`

## Si no aparece en el menu de /
- Ejecuta `Chat: Configure Prompt Files`.
- O recarga la ventana con `Developer: Reload Window`.

## Normalizacion
Este comando cumple el estandar de `Docs/08-Normalizacion-Prompts.md`.
