# 03 - Configuracion en VS Code

Esta guia cubre la **primera configuracion** de prompt files en VS Code y el
flujo para **añadir un prompt nuevo** despues.

> Requisitos: VS Code reciente (>= 1.90) con la extension **GitHub Copilot**
> y **GitHub Copilot Chat** instaladas y autenticadas.

---

## 1. Primera configuracion (una sola vez)

### 1.1. Activar el soporte de prompt files

Abre la paleta (`Ctrl+Shift+P`) y ejecuta:

```
Preferences: Open User Settings (JSON)
```

Añade (o verifica) estas claves:

```jsonc
{
  // Activa el soporte de archivos .prompt.md
  "chat.promptFiles": true,

  // (Opcional) Carpetas adicionales donde buscar prompts.
  // La carpeta de usuario y .github/prompts/ se incluyen por defecto.
  "chat.promptFilesLocations": {
    "Prompts": true
  }
}
```

- `"Prompts": true` apunta a la carpeta `Prompts/` del workspace actual.
  Asi puedes tener los `.prompt.md` versionados en el repo **sin duplicarlos**
  en `.github/prompts/`.

### 1.2. Conocer las ubicaciones por defecto

| Ubicacion                                                              | Alcance               | Versionado en Git |
|------------------------------------------------------------------------|-----------------------|-------------------|
| `C:\Users\<usuario>\AppData\Roaming\Code\User\prompts\`                | Usuario (personal)    | No                |
| `.github/prompts/` dentro del workspace                                | Workspace (equipo)    | Si                |
| Cualquier ruta declarada en `chat.promptFilesLocations`                | Workspace             | Depende           |

Ver `05-Sincronizacion-Usuario-vs-Workspace.md` para decidir cual usar.

### 1.3. Comandos utiles de la paleta

| Comando                          | Para que sirve                                     |
|----------------------------------|----------------------------------------------------|
| `Chat: New Prompt File`          | Crear un `.prompt.md` con scaffold basico.         |
| `Chat: Configure Prompt Files`   | Listar / habilitar / abrir prompts cargados.       |
| `Developer: Reload Window`       | Forzar recarga si un prompt no aparece.            |

### 1.4. Verificar que funciona

1. Abre Copilot Chat (`Ctrl+Alt+I` o icono lateral).
2. Escribe `/`.
3. Deberias ver al menos `/Comment` (el prompt de ejemplo del repo) o los
   comandos integrados.

---

## 2. Añadir un prompt nuevo (flujo recurrente)

Una vez configurado VS Code la primera vez, para cada prompt nuevo:

1. Crear la carpeta y archivos siguiendo `02-Crear-un-Prompt.md`.
2. **Colocar el `.prompt.md`** en una de las ubicaciones cargadas:
   - Copia a `AppData\Roaming\Code\User\prompts\` (uso personal), **o**
   - Deja en `Prompts/<Nombre>/` si `chat.promptFilesLocations` apunta ahi, **o**
   - Copia a `.github/prompts/` (compartido con el equipo).
3. **Recargar la ventana**: `Developer: Reload Window`.
   - En muchos casos basta con cerrar y reabrir el panel de Chat, pero
     `Reload Window` es la opcion segura.
4. Comprobar que `/Nombre` aparece en el menu de `/` del Chat.
5. Probar el comando con un argumento real.

## 3. Buenas practicas en VS Code

- **No mezcles** prompts de usuario y de workspace con el mismo `name`: el
  comportamiento ante duplicados no esta garantizado.
- Usa **Settings Sync** (`Configure Settings Sync`) si quieres llevar tus
  prompts de usuario entre maquinas. Verifica que la categoria "Prompts" este
  activada; en algunas versiones no se sincroniza por defecto.
- Si trabajas en equipo, **prefiere workspace** (`.github/prompts/` o carpeta
  versionada via `chat.promptFilesLocations`).

## 4. Troubleshooting

Ver `06-FAQ-y-Troubleshooting.md`.
