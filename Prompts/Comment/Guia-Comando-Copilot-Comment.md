# Guia para crear el comando /Comment en Copilot Chat

## Objetivo
Crear un comando personalizado de Copilot Chat para que, al escribir:

`/Comment infoComentario`

Copilot inserte una sola linea de comentario en el codigo, usando el texto `infoComentario` y respetando el formato de comentario del lenguaje actual.

## Enfoque correcto (sin extension de VS Code)
No hace falta crear una extension para esto.
Se hace con un **Prompt File** (`.prompt.md`) de Copilot.

## Dato importante
Un prompt file aparece como comando al escribir `/` en Copilot Chat.

- Nombre del comando: se define con `name` en el frontmatter
- Texto sugerido de argumento: se define con `argument-hint`
- Texto que escribes tras el comando (`/Comment ...`) se usa como contexto de entrada

## Ubicacion usada
Se creo el prompt a nivel de usuario en:

`C:/Users/Cristian/AppData/Roaming/Code/User/prompts/Comment.prompt.md`

Esto hace que este disponible en tus chats de Copilot (perfil de usuario).

## Contenido del prompt creado
```md
---
description: "Inserta una linea de comentario en codigo usando el texto indicado tras /Comment"
name: "Comment"
argument-hint: "infoComentario"
agent: "agent"
---
Inserta una sola linea de comentario en el archivo de codigo activo, en la linea del cursor.

Reglas:
- Usa como texto del comentario lo que el usuario escriba despues de `/Comment` en este mensaje.
- Si no hay texto despues del comando, usa `${input:infoComentario:Escribe el texto del comentario}`.
- Respeta el estilo del lenguaje del archivo actual para comentar una sola linea:
  - JS/TS/Java/C/C++/C#/Go/Rust/PHP/Kotlin/Swift: `// texto`
  - Python/Ruby/Shell/YAML/TOML: `# texto`
  - SQL/Lua/Haskell: `-- texto`
  - HTML/XML: `<!-- texto -->`
  - CSS: `/* texto */`
- No cambies otras lineas.
- No agregues explicaciones adicionales: solo realiza la edicion.
```

## Como usarlo
1. Abre Copilot Chat.
2. Escribe `/Comment`.
3. Añade el texto del comentario.

Ejemplo:

`/Comment validar null antes de map`

Resultado esperado:
Copilot inserta una sola linea de comentario en la linea actual del cursor.

## Si no aparece en el menu de /
- Ejecuta `Chat: Configure Prompt Files`
- O recarga VS Code con `Developer: Reload Window`

## Diferencia clave
- Prompt/Slash command: ideal para tareas rapidas y reutilizables como esta.
- Extension de VS Code: solo necesaria si quieres UI propia, comandos complejos, logica local avanzada, etc.

## Nota sobre la prueba que hicimos
Probamos ejecutar la accion con argumento `test` en tu archivo activo, pero la edicion se canceló en esa llamada.
No hubo cambios aplicados en esa prueba.
