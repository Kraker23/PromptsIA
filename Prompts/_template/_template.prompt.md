---
description: "<!-- Descripcion corta en una linea de lo que hace el comando -->"
name: "<!-- NombreDelComando en PascalCase, mismo nombre que el archivo sin extension -->"
argument-hint: "<!-- pistaArgumento (opcional, eliminar la linea si no hay argumento) -->"
agent: "agent"
---
<!--
PLANTILLA BASE PARA UN PROMPT FILE DE COPILOT CHAT.

Como usarla:
1. Copia esta carpeta `_template/` y renombrala con el nombre de tu prompt.
   Ejemplo: `Prompts/MiComando/`
2. Renombra `_template.prompt.md` -> `MiComando.prompt.md`.
3. Renombra los archivos acompañantes:
   - `Chuleta-Rapida-_template.md` -> `Chuleta-Rapida-MiComando.md`
   - `Guia-Comando-_template.md`   -> `Guia-Comando-MiComando.md`
4. Rellena el frontmatter de arriba (description, name, argument-hint).
5. Sustituye este bloque de comentarios y el cuerpo siguiente por tus reglas.
6. Lee `Prompts_IA/Docs/08-Normalizacion-Prompts.md` antes de hacer commit.
-->

<!-- Frase imperativa que describe la accion principal. Ejemplo:
"Inserta una sola linea de comentario en el archivo activo, en la linea del cursor." -->

Reglas:
- <!-- Regla 1: que debe hacer el modelo. -->
- <!-- Regla 2: como tratar el argumento del usuario.
     Si hay argumento, usar: ${input:pistaArgumento:Texto de ayuda mostrado al usuario}. -->
- <!-- Regla 3: contexto a respetar (lenguaje activo, archivo abierto, etc.). -->

No hacer:
- <!-- Que NO debe hacer el modelo (no añadir explicaciones, no tocar otras lineas, etc.). -->
