# Guia para crear el comando /NombreDelComando en Copilot Chat

<!-- Sustituye "NombreDelComando" por el nombre real en todo el archivo. -->

## Objetivo
Crear un comando personalizado de Copilot Chat para que, al escribir:

`/NombreDelComando pistaArgumento`

Copilot ejecute la accion descrita en el prompt.

## Enfoque
Se hace con un **Prompt File** (`.prompt.md`) de Copilot Chat.
No requiere extension de VS Code ni de Visual Studio.

## Ubicacion del archivo
Elige una de las dos:

- **Usuario** (personal, todos los proyectos):
  `C:/Users/<usuario>/AppData/Roaming/Code/User/prompts/NombreDelComando.prompt.md`
- **Workspace** (compartido por Git con el equipo):
  `.github/prompts/NombreDelComando.prompt.md`

Ver `Prompts_IA/Docs/05-Sincronizacion-Usuario-vs-Workspace.md` para decidir.

## Contenido del prompt
```md
---
description: "<!-- descripcion corta -->"
name: "NombreDelComando"
argument-hint: "pistaArgumento"
agent: "agent"
---
<!-- Cuerpo del prompt con la accion y las reglas. -->
```

## Como usarlo
1. Abre Copilot Chat.
2. Escribe `/NombreDelComando`.
3. Añade el argumento (si aplica).

## Si no aparece en el menu de /
- Ejecuta `Chat: Configure Prompt Files`.
- O recarga la ventana con `Developer: Reload Window`.

## Normalizacion
Este prompt debe cumplir lo descrito en
`Prompts_IA/Docs/08-Normalizacion-Prompts.md` antes de hacer commit.
