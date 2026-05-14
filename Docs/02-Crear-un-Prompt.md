# 02 - Crear un Prompt paso a paso

Esta guia explica como crear un prompt nuevo cumpliendo la normalizacion del
repositorio (`08-Normalizacion-Prompts.md`).

> Requisito: haber leido `01-Que-es-un-Prompt-File.md`.

---

## Paso 1. Decide el nombre del comando

Reglas (resumen, ver `08-Normalizacion-Prompts.md` para el detalle):

- PascalCase, sin espacios, sin acentos.
- Unico en todo el repositorio.
- Debe describir la accion en una palabra o dos (`Comment`, `RegistroCambios`).

Ejemplo en esta guia: **`RegistroCambios`**.

## Paso 2. Copia la plantilla

1. Copia la carpeta `Prompts/_template/` y renombrala con tu comando:

   `Prompts/_template/` -> `Prompts/RegistroCambios/`

2. Renombra los tres archivos:

   | Antes                                | Despues                                          |
   |--------------------------------------|--------------------------------------------------|
   | `_template.prompt.md`                | `RegistroCambios.prompt.md`                      |
   | `Chuleta-Rapida-_template.md`        | `Chuleta-Rapida-RegistroCambios.md`              |
   | `Guia-Comando-_template.md`          | `Guia-Comando-RegistroCambios.md`                |

## Paso 3. Rellena el frontmatter

Abre `RegistroCambios.prompt.md` y completa:

```yaml
---
description: "Genera una linea de registro con los cambios indicados tras /RegistroCambios"
name: "RegistroCambios"
argument-hint: "descripcionCambio"
agent: "agent"
---
```

- `name` debe coincidir con el nombre de la carpeta y del archivo.
- Si tu comando no recibe argumento, **elimina** la linea `argument-hint`.

## Paso 4. Escribe el cuerpo

Sigue la plantilla del estandar:

```md
<Frase imperativa de una linea con la accion principal.>

Reglas:
- <Regla 1>
- <Regla 2>

No hacer:
- <Antiregla 1>
```

Buenas practicas:

- Imperativo, no condicional.
- Si usas el argumento, declaralo con `${input:descripcionCambio:Describe el cambio}`.
- No incluyas ejemplos de codigo largos (van en la guia).

## Paso 5. Coloca el archivo en la ubicacion correcta

Tienes dos opciones (ver `05-Sincronizacion-Usuario-vs-Workspace.md`):

- **Usuario** (personal): copia el `.prompt.md` a
  `C:\Users\<usuario>\AppData\Roaming\Code\User\prompts\`.
- **Workspace** (compartido por Git): copia el `.prompt.md` a
  `.github/prompts/` del repositorio.

> La carpeta `Prompts/<Nombre>/` del repo es la **fuente** (versionada, con
> chuleta y guia). El `.prompt.md` que Copilot detecta es la **copia** en la
> ubicacion correspondiente. Configurando `chat.promptFilesLocations` puedes
> apuntar directamente a `Prompts/` sin duplicar (ver `03-VSCode-Configuracion.md`).

## Paso 6. Configura el IDE (solo la primera vez)

- VS Code -> ver `03-VSCode-Configuracion.md`.
- Visual Studio -> ver `04-VisualStudio-Configuracion.md`.

## Paso 7. Recarga y prueba

1. `Developer: Reload Window` (VS Code) o reiniciar Visual Studio.
2. Abre Copilot Chat.
3. Escribe `/` y verifica que aparece `/RegistroCambios`.
4. Ejecutalo con un argumento de prueba: `/RegistroCambios cambio de ejemplo`.
5. Verifica que el resultado cumple las reglas.

## Paso 8. Rellena la chuleta y la guia

- `Chuleta-Rapida-RegistroCambios.md`: uso rapido (1 pantalla).
- `Guia-Comando-RegistroCambios.md`: explicacion completa.

Ambos son obligatorios segun la normalizacion.

## Paso 9. Checklist final

Antes de commit, valida la lista de
`08-Normalizacion-Prompts.md` -> **10. Checklist pre-commit**.

## Problemas frecuentes

Ver `06-FAQ-y-Troubleshooting.md`.
