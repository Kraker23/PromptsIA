# 05 - Sincronizacion: Usuario vs Workspace

Hay dos lugares donde puede vivir un `.prompt.md`. Elegir bien evita
duplicaciones y conflictos.

---

## 1. Resumen rapido

| Ubicacion                                                 | Alcance      | Versionado | Compartido con el equipo |
|-----------------------------------------------------------|--------------|------------|--------------------------|
| `AppData\Roaming\Code\User\prompts\` (VS Code)            | Usuario      | No         | No                       |
| `.github/prompts/` (workspace)                            | Workspace    | Si (Git)   | Si                       |
| Carpeta del repo via `chat.promptFilesLocations`          | Workspace    | Si (Git)   | Si                       |

Visual Studio solo soporta las opciones de **workspace**.

## 2. Cuando usar cada una

### Usar **Usuario** (`AppData\...\User\prompts\`) si:

- El prompt es para tu uso personal en cualquier proyecto.
- Contiene flujos de trabajo tuyos (ej. `MisNotas`, `RevisarCommit`).
- No quieres que aparezca en proyectos donde otros no lo necesitan.

### Usar **Workspace** (`.github/prompts/` o configurado) si:

- El prompt es especifico del proyecto.
- Quieres que el equipo lo use con las mismas reglas (esto es lo habitual en
  este repositorio).
- Necesita estar en Visual Studio (solo soporta workspace).

### Regla practica para este repositorio

Los prompts del proyecto (`Comment`, futuros prompts del equipo) viven en
`Prompts/<Nombre>/` y se exponen al IDE configurando
`chat.promptFilesLocations` en `Prompts/`. **No** se duplican en
`AppData\...\User\prompts\`.

## 3. Estrategias de exposicion en VS Code

### Estrategia A. Carpeta `Prompts/` del repo como fuente unica (recomendada)

`.vscode/settings.json` del workspace:

```jsonc
{
  "chat.promptFiles": true,
  "chat.promptFilesLocations": {
    "Prompts": true
  }
}
```

VS Code escaneara recursivamente `Prompts/**/*.prompt.md`.

Pros:
- Sin duplicacion.
- Versionado completo (prompt + chuleta + guia juntos).
- El equipo lo recibe automaticamente al clonar.

Contras:
- Solo aplica al workspace abierto.

### Estrategia B. Copia a `.github/prompts/`

Pros:
- Convencion estandar de GitHub Copilot, compatible con Visual Studio.

Contras:
- Hay que mantener `Prompts/<Nombre>/Nombre.prompt.md` y
  `.github/prompts/Nombre.prompt.md` sincronizados (o tratar uno como copia).

### Estrategia C. Carpeta de usuario

Pros:
- Disponible en cualquier proyecto.

Contras:
- No versionada, dificil de mantener en equipo.
- No funciona en Visual Studio.

## 4. Estrategia en Visual Studio

Visual Studio solo lee `.github/prompts/`. Opciones:

1. **Mover** los `.prompt.md` finales a `.github/prompts/` (lo mas simple).
2. **Duplicar** desde `Prompts/<Nombre>/Nombre.prompt.md` a
   `.github/prompts/Nombre.prompt.md` con un script o tarea de build.
3. **Symlink** (NTFS junction) desde `.github/prompts/Nombre.prompt.md` ->
   `Prompts/<Nombre>/Nombre.prompt.md`. Funciona, pero no es portable en Git.

Recomendacion: opcion 1 o 2.

## 5. Migrar entre ubicaciones

### De usuario a workspace

1. Localiza el archivo en `AppData\Roaming\Code\User\prompts\`.
2. Crea la carpeta `Prompts/<Nombre>/` siguiendo la normalizacion
   (`08-Normalizacion-Prompts.md`).
3. **Mueve** el `.prompt.md` a `Prompts/<Nombre>/`.
4. Crea la chuleta y la guia (obligatorias en este repo).
5. Ajusta `chat.promptFilesLocations` si no estaba ya.
6. `Developer: Reload Window`.
7. Verifica que el comando sigue apareciendo y funcionando.

### De workspace a usuario

Inverso: copia (no muevas) el `.prompt.md` al directorio de usuario. Conserva
los archivos del repo para el equipo.

## 6. Conflictos de nombre

Si existen dos `.prompt.md` con el mismo `name` en distintas ubicaciones:

- VS Code: el comportamiento ante duplicados no esta garantizado, puede ganar
  el primero detectado o mostrar ambos. **Evitalo**.
- Visual Studio: idem.

Buena practica: prefijos por dominio (`Code-Comment`, `Docs-Changelog`) para
reducir colisiones.

## 7. Settings Sync (VS Code)

Si quieres llevar los prompts de **usuario** entre maquinas:

1. `Settings Sync: Turn On`.
2. Activa la categoria de prompts si tu version lo permite.
3. Confirma despues que los `.prompt.md` aparecen en la otra maquina.

Para los prompts de **workspace** no hace falta sync: viajan con el repo.
