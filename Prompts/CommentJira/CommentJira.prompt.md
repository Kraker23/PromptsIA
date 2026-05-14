---
description: "Inserta comentario con usuario, fecha, ticket JIRA de la rama y descripcion del cambio"
name: "CommentJira"
argument-hint: "comentario"
agent: "agent"
---
Inserta una sola linea de comentario en el archivo de codigo activo, en la linea del cursor.

NOTA DE CONFIGURACION: este prompt contiene el marcador `<TU_USUARIO>`.
Si `<TU_USUARIO>` no ha sido sustituido, detente e informa al usuario:
"Edita CommentJira.prompt.md, sustituye `<TU_USUARIO>` por tu nombre de usuario real
(ej: cRamirez), guarda el archivo y ejecuta Developer: Reload Window."

El comentario debe tener exactamente este formato:
PREFIJO <TU_USUARIO> FECHA -> TICKET - COMENTARIO

Sigue estos pasos para obtener cada valor:

PASO 1 - FECHA (formato dd-MM-yyyy):
En Windows ejecuta en terminal:
  powershell -Command "Get-Date -Format 'dd-MM-yyyy'"
En Linux o macOS ejecuta:
  date +"%d-%m-%Y"
Usa el resultado como FECHA.

PASO 2 - TICKET (codigo de incidencia JIRA):
Ejecuta en terminal: git branch --show-current
Del nombre de la rama extrae el primer patron que coincida con [A-Z]{4}+-[0-9]{4}+
  (ejemplos validos: PROJ-1234, ABCD-4567, MYAP-9999).
Si encuentras el patron, usalo como TICKET.
Si el comando falla o la rama no contiene ese patron, pide al usuario:
  ${input:ticketJira:Introduce el codigo JIRA (ej: PROJ-1234)}

PASO 3 - COMENTARIO:
Usa el texto que el usuario haya escrito tras /CommentJira en este mensaje.
Si no hay texto, pide al usuario: ${input:comentario:Describe brevemente el cambio}

PASO 4 - INSERTAR:
Determina PREFIJO segun el lenguaje del archivo activo:
  - JS/TS/Java/C/C++/C#/Go/Rust/PHP/Kotlin/Swift: construye `// <TU_USUARIO> FECHA -> TICKET - COMENTARIO`
  - Python/Ruby/Shell/YAML/TOML:                  construye `# <TU_USUARIO> FECHA -> TICKET - COMENTARIO`
  - SQL/Lua/Haskell:                              construye `-- <TU_USUARIO> FECHA -> TICKET - COMENTARIO`
  - HTML/XML:                                     construye `<!-- <TU_USUARIO> FECHA -> TICKET - COMENTARIO -->`
  - CSS:                                          construye `/* <TU_USUARIO> FECHA -> TICKET - COMENTARIO */`
Inserta la linea resultante en la posicion del cursor del archivo activo.

Reglas:
- Inserta una sola linea; no modifiques ninguna otra linea.
- No añadas explicaciones adicionales: solo realiza la edicion.

No hacer:
- No inventes ni aproximes la fecha; obtenla ejecutando el comando del terminal.
- No supongas el ticket JIRA; extraelo de la rama o pide-lo al usuario.
- No modifiques otras lineas del archivo.
