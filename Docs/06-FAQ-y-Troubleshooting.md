# 06 - FAQ y Troubleshooting

Problemas frecuentes al trabajar con prompt files y como resolverlos.

---

## "Mi comando `/Nombre` no aparece en el menu de Copilot Chat"

Comprueba en orden:

1. **El archivo se llama `<Nombre>.prompt.md`** (no `.md` a secas, no `.prompt`).
2. **El frontmatter es YAML valido** y contiene `name: "Nombre"`.
3. **El archivo esta en una ubicacion cargada**:
   - VS Code: `AppData\Roaming\Code\User\prompts\`, `.github/prompts/`, o
     una ruta declarada en `chat.promptFilesLocations`.
   - Visual Studio: `.github/prompts/` en la raiz del repo.
4. **Setting activo** (VS Code): `chat.promptFiles: true` en `settings.json`.
5. **Recarga**:
   - VS Code: `Developer: Reload Window`.
   - Visual Studio: reiniciar la aplicacion.
6. **Comando de diagnostico** (VS Code): `Chat: Configure Prompt Files` lista
   los prompts cargados.

## "El frontmatter no se reconoce / sale como texto"

Causas comunes:

- Falta uno de los `---` que delimitan el bloque.
- Hay tabuladores en lugar de espacios.
- Claves con mayuscula inicial (debe ser `description`, no `Description`).
- Valores sin comillas dobles cuando contienen `:`, `#` o comillas.
- Archivo guardado con **BOM** (UTF-8 BOM). Guardar como **UTF-8 sin BOM**.

Validacion rapida: pega el bloque YAML en https://www.yamllint.com o usa
`Format Document` en VS Code sobre el `.prompt.md`.

## "Edita el archivo equivocado / no aplica los cambios"

- Verifica que Copilot esta leyendo la ubicacion que crees: usa
  `Chat: Configure Prompt Files` (VS Code).
- Si tienes dos copias (en `Prompts/` y en `.github/prompts/`), asegurate de
  editar la que Copilot esta cargando.
- Tras editar, **siempre recarga** la ventana o reinicia.

## "El placeholder `${input:...}` no me lo pide"

- Solo se evalua si el cuerpo lo referencia explicitamente.
- Sintaxis correcta: `${input:nombreVariable:Texto ayuda}`.
- En Visual Studio el soporte puede ser parcial; prueba en VS Code para
  descartar.

## "El comando aparece pero no respeta las reglas"

- Las reglas las interpreta el modelo, no las "ejecuta". Si tu prompt es
  ambiguo, el resultado lo sera.
- Mejora la redaccion siguiendo `08-Normalizacion-Prompts.md` seccion 4:
  imperativo, secciones `Reglas:` y `No hacer:`.
- Acorta el prompt: prompts muy largos diluyen las instrucciones criticas.
- Verifica que `agent: "agent"` esta en el frontmatter si esperas que pueda
  editar archivos.

## "Tengo dos comandos con el mismo nombre"

- Renombra uno. Los nombres deben ser unicos en todo el repositorio y en
  todas las ubicaciones cargadas.
- Usa prefijos por dominio para evitarlo (`Code-Comment`, `Docs-Changelog`).

## "Funciona en VS Code pero no en Visual Studio (o al reves)"

- Comprueba la tabla comparativa en `04-VisualStudio-Configuracion.md` seccion 2.
- Algunos campos del frontmatter o placeholders no estan soportados en ambos.
- Marca el prompt como especifico de un IDE segun
  `08-Normalizacion-Prompts.md` seccion 8.

## "He cambiado un setting y no surte efecto"

- VS Code: `Developer: Reload Window`.
- Si el setting esta en `settings.json` del workspace, abre el workspace
  correcto (no el de usuario).
- Comprueba que no haya un setting con el mismo nombre **mas especifico**
  sobrescribiendolo (workspace > user > default).

## "Quiero ver el contenido real que recibe el modelo"

- VS Code: en algunas versiones, el panel de Copilot Chat permite expandir
  "Used references" o equivalente para ver el contexto enviado.
- Si no, añade temporalmente al cuerpo del prompt: `Antes de actuar, repite
  literalmente las instrucciones que has recibido.` y elimina la linea
  cuando termines de depurar.

## "Quiero desactivar un prompt temporalmente"

- Renombra el archivo cambiando la extension: `Nombre.prompt.md` ->
  `Nombre.prompt.md.disabled`.
- Recarga la ventana.

## Otros problemas

- Revisa los logs: `Help` -> `Toggle Developer Tools` -> Consola (VS Code).
- Reporta el caso en `Prompts_IA/Docs/07-Consideraciones-y-Sugerencias.md` o
  abre una incidencia interna.
