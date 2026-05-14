# Chuleta rapida: comando /CommentJira en Copilot

## Uso
Escribe en Copilot Chat:

`/CommentJira descripcion del cambio`

Ejemplo:

`/CommentJira fix null check antes de map`

## Formato del comentario
```
PREFIJO <TU_USUARIO> dd-MM-yyyy -> TICKET - COMENTARIO
```

Ejemplo real en C#:
```
// cRamirez 14-05-2026 -> PROJ-123 - fix null check antes de map
```

## Como se obtiene cada campo

| Campo       | Origen                                                        |
|-------------|---------------------------------------------------------------|
| PREFIJO     | Automatico segun el lenguaje del archivo (`//`, `#`, `--`...) |
| TU_USUARIO  | Configurado por ti en el archivo del prompt (ver abajo)       |
| FECHA       | Automatico: fecha actual del sistema (dd-MM-yyyy)             |
| TICKET      | Automatico: extraido del nombre de la rama git actual         |
| COMENTARIO  | Lo que escribas tras `/CommentJira`                           |

## Prefijo por lenguaje
- C#, JS, TS, Java, C, C++, Go, Rust, PHP, Kotlin, Swift -> `// texto`
- Python, Ruby, Shell, YAML, TOML -> `# texto`
- SQL, Lua, Haskell -> `-- texto`
- HTML, XML -> `<!-- texto -->`
- CSS -> `/* texto */`

## Configuracion inicial (una sola vez)
1. Copia `CommentJira.prompt.md` a tu carpeta de prompts:
   `C:/Users/<tu-usuario>/AppData/Roaming/Code/User/prompts/CommentJira.prompt.md`
2. Abre el archivo y sustituye `<TU_USUARIO>` por tu nombre real (ej: `cRamirez`).
3. Guarda y ejecuta `Developer: Reload Window`.

## Si no aparece /CommentJira
1. Ejecuta `Chat: Configure Prompt Files`.
2. Si sigue sin salir, ejecuta `Developer: Reload Window`.

## Archivo del prompt
`C:/Users/<tu-usuario>/AppData/Roaming/Code/User/prompts/CommentJira.prompt.md`
