# Guia para crear el comando /CommentJira en Copilot Chat

## Objetivo
Crear un comando personalizado de Copilot Chat para que, al escribir:

`/CommentJira descripcion del cambio`

Copilot inserte una sola linea de comentario en el codigo con el siguiente formato:

```
PREFIJO <TU_USUARIO> dd-MM-yyyy -> TICKET - COMENTARIO
```

Donde el prefijo se adapta al lenguaje del archivo activo.

## Formato del comentario

```
PREFIJO <TU_USUARIO> dd-MM-yyyy -> TICKET - COMENTARIO
```

Ejemplos por lenguaje:

| Lenguaje        | Resultado                                                              |
|-----------------|------------------------------------------------------------------------|
| C# / JS / Java  | `// cRamirez 14-05-2026 -> PROJ-123 - fix null check`                  |
| Python / Shell  | `# cRamirez 14-05-2026 -> PROJ-123 - fix null check`                   |
| SQL             | `-- cRamirez 14-05-2026 -> PROJ-123 - fix null check`                  |
| HTML / XML      | `<!-- cRamirez 14-05-2026 -> PROJ-123 - fix null check -->`            |
| CSS             | `/* cRamirez 14-05-2026 -> PROJ-123 - fix null check */`               |

## Como funciona cada campo

| Campo      | Descripcion                                                                         |
|------------|-------------------------------------------------------------------------------------|
| PREFIJO    | Determinado automaticamente segun el lenguaje del archivo abierto.                  |
| TU_USUARIO | Nombre configurado una sola vez en el archivo del prompt (ver seccion siguiente).   |
| FECHA      | Fecha actual del sistema en formato dd-MM-yyyy, obtenida via terminal.              |
| TICKET     | Codigo JIRA extraido del nombre de la rama git activa (patron `[A-Z]+-[0-9]+`).    |
|            | Si la rama no contiene el patron o no hay repo git, Copilot lo pide al usuario.     |
| COMENTARIO | Texto que el usuario escribe tras `/CommentJira`. Si no escribe nada, Copilot lo pide. |

## Configuracion inicial (una sola vez)

El archivo del repo (`Prompts/CommentJira/CommentJira.prompt.md`) contiene el marcador
`<TU_USUARIO>` como placeholder. Cada usuario debe sustituirlo en **su copia personal**:

1. Copia el archivo a tu carpeta de prompts de usuario:
   ```
   C:\Users\<tu-usuario>\AppData\Roaming\Code\User\prompts\CommentJira.prompt.md
   ```
2. Abre esa copia y sustituye **todas las ocurrencias** de `<TU_USUARIO>` por tu
   nombre de usuario real (ej: `cRamirez`).
3. Guarda el archivo.
4. En VS Code ejecuta `Developer: Reload Window`.
5. Escribe `/` en Copilot Chat y comprueba que aparece `/CommentJira`.

El archivo del repo NO se modifica; conserva `<TU_USUARIO>` como marcador.

## Como usarlo

1. Abre el archivo de codigo donde quieres insertar el comentario.
2. Coloca el cursor en la linea donde debe aparecer.
3. Abre Copilot Chat.
4. Escribe `/CommentJira` seguido de la descripcion del cambio.
   Ejemplo: `/CommentJira fix null check antes de map`
5. Copilot:
   - Obtiene la fecha actual del sistema.
   - Obtiene el ticket JIRA de la rama git activa (o te lo pide si no lo encuentra).
   - Inserta la linea con el formato completo en la posicion del cursor.

## Ejemplo de resultado

Rama git activa: `feature/PROJ-123-null-check`
Archivo abierto: `OrderService.cs`
Comando ejecutado: `/CommentJira fix null check antes de map`

Resultado insertado:
```
// cRamirez 14-05-2026 -> PROJ-123 - fix null check antes de map
```

## Notas

- **Requiere repo git activo** para obtener el ticket automaticamente. Si no hay
  repo o la rama no contiene el patron JIRA (`[A-Z]+-[0-9]+`), Copilot solicita
  el ticket al usuario antes de insertar.
- El campo FECHA usa la fecha del sistema en el momento de ejecucion.
- El PREFIJO se adapta al lenguaje; no es necesario cambiarlo manualmente.
- Si el mismo desarrollador trabaja en varios equipos o maquinas, debe copiar y
  configurar el prompt en cada una.

## Si no aparece en el menu de /
- Ejecuta `Chat: Configure Prompt Files`.
- O recarga la ventana con `Developer: Reload Window`.
- Verifica que el archivo esta en una ubicacion cargada por Copilot
  (ver `Prompts_IA/Docs/03-VSCode-Configuracion.md`).

## Normalizacion
Este prompt cumple el estandar descrito en
`Prompts_IA/Docs/08-Normalizacion-Prompts.md`.
