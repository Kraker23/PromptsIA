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
