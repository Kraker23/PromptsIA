# Chuleta rapida: comando /Comment en Copilot

## Uso
Escribe en Copilot Chat:

`/Comment tu texto`

Ejemplo:

`/Comment validar null antes de map`

## Que hace
- Inserta **una sola linea** de comentario en la linea del cursor.
- Usa el texto que pongas tras `/Comment`.
- Si no pones texto, te lo pide.

## Formato por lenguaje
- C#, JS, TS, Java, C, C++, Go, Rust, PHP, Kotlin, Swift -> `// texto`
- Python, Ruby, Shell, YAML, TOML -> `# texto`
- SQL, Lua, Haskell -> `-- texto`
- HTML, XML -> `<!-- texto -->`
- CSS -> `/* texto */`

## Si no aparece /Comment
1. Ejecuta `Chat: Configure Prompt Files`
2. Si sigue sin salir, ejecuta `Developer: Reload Window`

## Archivo del prompt
`C:/Users/Cristian/AppData/Roaming/Code/User/prompts/Comment.prompt.md`
