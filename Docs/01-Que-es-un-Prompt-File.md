# 01 - Que es un Prompt File

Un **Prompt File** es un archivo Markdown con extension `.prompt.md` que define
un **comando personalizado** ("slash command") para GitHub Copilot Chat.

Cuando esta cargado, al escribir `/` en el chat de Copilot aparece tu comando
junto a los integrados (`/explain`, `/fix`, etc.).

---

## Estructura minima

Un `.prompt.md` tiene dos partes:

1. **Frontmatter YAML** (entre `---`): metadatos del comando.
2. **Cuerpo Markdown**: instrucciones que recibe el modelo cuando se invoca.

Ejemplo (tomado de `Prompts/Comment/Comment.prompt.md`):

```md
---
description: "Inserta una linea de comentario en codigo usando el texto indicado tras /Comment"
name: "Comment"
argument-hint: "infoComentario"
agent: "agent"
---
Inserta una sola linea de comentario en el archivo de codigo activo, en la linea del cursor.

Reglas:
- Usa como texto del comentario lo que el usuario escriba despues de `/Comment`.
- ...
```

## Campos del frontmatter

| Campo           | Obligatorio | Que hace                                                           |
|-----------------|-------------|--------------------------------------------------------------------|
| `description`   | Si          | Texto que aparece junto al comando en el menu `/`.                 |
| `name`          | Si          | Nombre del comando. Se invoca como `/<name>`.                      |
| `argument-hint` | No          | Pista del argumento que se muestra al usuario.                     |
| `agent`         | Si          | Modo en el que corre el prompt (normalmente `"agent"`).            |

Para conocer la **norma exacta** de cada campo, ver
`08-Normalizacion-Prompts.md`.

## Argumentos del usuario

Lo que el usuario escribe tras `/<name>` esta disponible como **contexto** del
prompt. Tambien puedes pedirlo explicitamente con un placeholder:

```
${input:nombreVariable:Texto de ayuda mostrado al usuario}
```

Si el usuario invoca `/Comment` sin texto, el placeholder hace que Copilot le
pida el valor antes de ejecutar.

## Como se invoca

1. Abrir Copilot Chat (panel lateral o ventana flotante).
2. Escribir `/` y seleccionar el comando del listado, **o** escribir `/Nombre` directo.
3. (Opcional) Añadir argumento: `/Comment validar null antes de map`.

## Que NO es un Prompt File

- No es codigo ejecutable: el modelo interpreta las instrucciones, no las "corre".
- No reemplaza a una extension de VS Code (si necesitas UI propia, atajos de
  teclado avanzados o logica local, necesitas una extension).
- No es lo mismo que `copilot-instructions.md`:
  - `copilot-instructions.md` -> reglas globales que aplican **siempre**.
  - `.prompt.md` -> accion puntual invocada **a demanda** con `/`.

## Siguiente paso

Ver `02-Crear-un-Prompt.md` para crear el tuyo paso a paso.
