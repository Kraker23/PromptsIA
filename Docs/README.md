# Prompts_IA - Documentacion

Documentacion del repositorio sobre como crear y gestionar **prompt files**
(`.prompt.md`) para **GitHub Copilot Chat** en **VS Code** y **Visual Studio**.

> Toda contribucion debe respetar el estandar definido en
> [08-Normalizacion-Prompts.md](08-Normalizacion-Prompts.md).
> Es la **fuente de verdad** del repositorio.

---

## Indice

| #   | Documento                                                                                          | De que va                                                              |
|-----|-----------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|
| 01  | [Que es un Prompt File](01-Que-es-un-Prompt-File.md)                                                | Concepto, frontmatter, placeholders, invocacion con `/`.               |
| 02  | [Crear un Prompt paso a paso](02-Crear-un-Prompt.md)                                                | Flujo completo usando la plantilla del repo.                            |
| 03  | [Configuracion en VS Code](03-VSCode-Configuracion.md)                                              | Primera vez + añadir prompt nuevo.                                      |
| 04  | [Configuracion en Visual Studio](04-VisualStudio-Configuracion.md)                                  | VS 2022 reciente, diferencias con VS Code.                              |
| 05  | [Sincronizacion: Usuario vs Workspace](05-Sincronizacion-Usuario-vs-Workspace.md)                   | Donde colocar los prompts y por que.                                    |
| 06  | [FAQ y Troubleshooting](06-FAQ-y-Troubleshooting.md)                                                | "Mi `/comando` no aparece" y otros problemas.                           |
| 07  | [Consideraciones y Sugerencias](07-Consideraciones-y-Sugerencias.md)                                | Riesgos, buenas practicas, que podria faltar.                           |
| 08  | [**Normalizacion de Prompts**](08-Normalizacion-Prompts.md)                                         | **Estandar obligatorio** para todo `.prompt.md` del repo.               |

## Estructura del repositorio

```
Prompts_IA/
  Docs/                              <-- esta documentacion
    README.md
    01-Que-es-un-Prompt-File.md
    02-Crear-un-Prompt.md
    03-VSCode-Configuracion.md
    04-VisualStudio-Configuracion.md
    05-Sincronizacion-Usuario-vs-Workspace.md
    06-FAQ-y-Troubleshooting.md
    07-Consideraciones-y-Sugerencias.md
    08-Normalizacion-Prompts.md
  Prompts/
    _template/                       <-- plantilla base para nuevos prompts
      _template.prompt.md
      Chuleta-Rapida-_template.md
      Guia-Comando-_template.md
    Comment/                         <-- ejemplo de prompt real
      Comment.prompt.md
      Chuleta-Rapida-Comment.md
      Guia-Comando-Comment.md
  tareas.txt
```

## Convenciones rapidas

- Una carpeta por prompt en `Prompts/<NombreDelComando>/`.
- Los **tres archivos** son obligatorios: `*.prompt.md`, `Chuleta-Rapida-*.md`,
  `Guia-Comando-*.md`.
- Naming en **PascalCase**, sin espacios ni acentos.
- Idioma: **espanol**.
- Codificacion: **UTF-8 sin BOM**, fin de linea **LF**.

Detalle completo en [08-Normalizacion-Prompts.md](08-Normalizacion-Prompts.md).

## Por donde empezar

- **Quiero entender que es esto**: empieza por
  [01-Que-es-un-Prompt-File.md](01-Que-es-un-Prompt-File.md).
- **Quiero crear un prompt nuevo**:
  [02-Crear-un-Prompt.md](02-Crear-un-Prompt.md).
- **Es mi primera vez configurando el IDE**:
  [03-VSCode-Configuracion.md](03-VSCode-Configuracion.md) o
  [04-VisualStudio-Configuracion.md](04-VisualStudio-Configuracion.md).
- **Algo no funciona**:
  [06-FAQ-y-Troubleshooting.md](06-FAQ-y-Troubleshooting.md).
