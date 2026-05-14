# 04 - Configuracion en Visual Studio

Esta guia cubre la **primera configuracion** de prompt files en Visual Studio
2022 (version reciente, 17.10+) y el flujo para **añadir un prompt nuevo**.

> Requisitos: Visual Studio 2022 actualizado con la extension **GitHub Copilot
> Chat** instalada y autenticada. El soporte de prompt files en Visual Studio
> es mas reciente y mas limitado que en VS Code; revisa la documentacion
> oficial de Microsoft si una opcion no aparece en tu version:
> https://learn.microsoft.com/visualstudio/ide/copilot-chat-context

---

## 1. Primera configuracion (una sola vez)

### 1.1. Verifica que tienes Copilot Chat

`Tools` -> `Extensions and Updates` (o `Manage Extensions`) -> busca
**GitHub Copilot Chat** y comprueba que esta instalada y actualizada.

Autentica tu cuenta con `Tools` -> `Options` -> `GitHub` -> `Copilot`.

### 1.2. Ubicaciones soportadas

Visual Studio reconoce dos mecanismos relacionados:

| Mecanismo                                | Ruta                                      | Para que sirve                                          |
|------------------------------------------|-------------------------------------------|---------------------------------------------------------|
| **Custom instructions** (siempre activas)| `.github/copilot-instructions.md`         | Reglas globales que Copilot aplica a todo el repo.      |
| **Prompt files** (a demanda con `/`)     | `.github/prompts/<Nombre>.prompt.md`      | Comandos personalizados invocables desde el chat.       |

Diferencia clave frente a VS Code: Visual Studio **no tiene** una carpeta de
prompts a nivel de usuario equivalente a `AppData\Roaming\Code\User\prompts\`.
Los prompts viven en el repositorio.

### 1.3. Activar prompt files

En versiones recientes, el soporte se activa solo al detectar archivos
`.prompt.md` en `.github/prompts/`. Si no aparecen:

1. `Tools` -> `Options` -> `GitHub` -> `Copilot` -> `Copilot Chat`.
2. Busca una opcion del tipo **"Enable prompt files"** / **"Custom prompts"**
   y actviala.
3. Reinicia Visual Studio.

> Si esa opcion no existe en tu version, significa que aun no esta disponible.
> En ese caso usa solo `copilot-instructions.md` (ver mas abajo) o actualiza
> Visual Studio.

### 1.4. Custom instructions del repositorio

Crea `.github/copilot-instructions.md` en la raiz del repo con reglas que
quieras que Copilot respete **siempre** (estilo de codigo, idioma, convenciones).

Ejemplo minimo:

```md
# Copilot Instructions

- Responde en espanol.
- Sigue las convenciones de `Prompts_IA/Docs/08-Normalizacion-Prompts.md`
  cuando se trabaje con prompt files.
- No incluyas datos sensibles en los ejemplos.
```

## 2. Tabla comparativa con VS Code

| Aspecto                          | VS Code                                          | Visual Studio 2022 (17.10+)              |
|----------------------------------|--------------------------------------------------|------------------------------------------|
| Prompts de usuario               | Si (`AppData\Roaming\Code\User\prompts\`)        | No (solo workspace)                      |
| Prompts de workspace             | Si (`.github/prompts/` o configurable)           | Si (`.github/prompts/`)                  |
| Setting para activar             | `chat.promptFiles: true`                         | Opcion en `Tools > Options > Copilot`    |
| Carpetas adicionales configurables| `chat.promptFilesLocations`                     | No (de momento)                          |
| Custom instructions globales     | Si (`copilot-instructions.md`)                   | Si (`copilot-instructions.md`)           |
| Placeholders `${input:...}`      | Soportados                                       | Soporte parcial / evolutivo              |
| Campo `agent` del frontmatter    | Soportado                                        | Puede ignorarse segun version            |
| Comando para recargar            | `Developer: Reload Window`                       | Reiniciar Visual Studio                  |

> Recomendacion: mantener los prompts **portables** entre ambos IDEs.
> Si un prompt depende de algo no soportado en Visual Studio, marcarlo segun
> indica `08-Normalizacion-Prompts.md` seccion 8.

## 3. Añadir un prompt nuevo (flujo recurrente)

1. Crear la carpeta y archivos siguiendo `02-Crear-un-Prompt.md`.
2. **Copiar** o **enlazar** el `.prompt.md` a `.github/prompts/<Nombre>.prompt.md`
   en la raiz de la solucion/repo.
3. **Reiniciar Visual Studio** (no basta con recargar la solucion en algunas
   versiones).
4. Abrir Copilot Chat (`View` -> `GitHub Copilot Chat`).
5. Escribir `/` y comprobar que aparece `/Nombre`.
6. Probar el comando con un argumento real.

## 4. Buenas practicas

- Versiona `.github/prompts/` y `.github/copilot-instructions.md`.
- Combina ambos: instrucciones globales para reglas que apliquen siempre,
  prompt files para acciones puntuales.
- Prueba siempre tus prompts **tambien** en VS Code si el equipo usa los dos
  IDEs.

## 5. Troubleshooting

Ver `06-FAQ-y-Troubleshooting.md`.
