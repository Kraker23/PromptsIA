# 07 - Consideraciones, riesgos y sugerencias

Esta seccion recoge **lo que podria faltar**, decisiones a tomar a futuro y
buenas practicas que no son obligatorias pero conviene tener en mente.

---

## 1. Consideraciones generales

### 1.1. Los prompt files no ejecutan codigo

Un `.prompt.md` solo da **instrucciones** al modelo. No corre scripts, no
accede a la red, no garantiza idempotencia. Si necesitas eso, usa una
extension de VS Code o un script externo.

### 1.2. Dependen del modelo activo

El comportamiento puede variar segun el modelo seleccionado en Copilot Chat
(GPT-4o, Claude, etc.). Prueba tu prompt con **varios modelos** si lo va a
usar mas de una persona.

### 1.3. Evolutivos

GitHub Copilot esta evolucionando rapidamente. Campos del frontmatter,
ubicaciones soportadas y caracteristicas pueden cambiar entre versiones del
IDE. Recomendaciones:

- Revisar los prompts cada vez que se actualiza Copilot Chat de forma
  significativa.
- Consultar la documentacion oficial cuando algo deje de funcionar:
  - VS Code: https://code.visualstudio.com/docs/copilot
  - Visual Studio: https://learn.microsoft.com/visualstudio/ide/copilot-chat-context

### 1.4. Compatibilidad VS Code <-> Visual Studio

No todo el frontmatter ni todos los placeholders se interpretan igual.
Mantener los prompts **portables** y marcar los especificos segun
`08-Normalizacion-Prompts.md` seccion 8.

## 2. Riesgos

### 2.1. Seguridad

- **Nunca** incluyas tokens, claves, contraseñas, rutas con nombres de
  usuario reales, IPs internas o datos de clientes en un `.prompt.md`
  versionado.
- Para datos sensibles en tiempo de ejecucion, usar `${input:...}`.
- Revisa los prompts antes de hacer publico el repo.

### 2.2. Calidad inconsistente

- Un prompt mal escrito produce resultados ambiguos. Sigue siempre la
  normalizacion (`08-Normalizacion-Prompts.md`).
- Pruebalo en varios lenguajes/contextos antes de marcarlo como estable.

### 2.3. Conflictos de nombres

- Dos prompts con el mismo `name` en distintas ubicaciones causan
  comportamiento impredecible. Usar prefijos por dominio reduce el riesgo.

### 2.4. Drift entre ubicaciones

- Si mantienes copias en `Prompts/<Nombre>/` y en `.github/prompts/`, pueden
  divergir. Mejor: usar `chat.promptFilesLocations` y mantener una sola
  copia, o automatizar la sincronizacion.

## 3. Sugerencias y buenas practicas

### 3.1. Naming y dominio

- Prefijos por dominio: `Code-*` (operan sobre codigo), `Docs-*` (generan
  documentacion), `Git-*` (commits, registros), `Test-*` (tests).
- Ayuda a navegar el menu `/` cuando hay muchos comandos.

### 3.2. Versionado por prompt

- Mantener un mini changelog dentro de la guia (`Guia-Comando-<Nombre>.md`)
  con seccion `## Cambios:` y fechas / version.

### 3.3. Plantilla unica

- Crear cualquier prompt nuevo **siempre** copiando `Prompts/_template/`.
  No hacerlo desde cero.

### 3.4. Tests manuales

- Por cada prompt, definir una lista de **casos de prueba** en la guia:
  - Lenguajes a cubrir.
  - Casos limite (sin argumento, argumento vacio, archivo sin foco).
- Ejecutarlos antes de hacer merge.

### 3.5. Integracion con `copilot-instructions.md`

- Reglas que apliquen **siempre** -> `copilot-instructions.md` global.
- Acciones puntuales -> `.prompt.md`.
- Ejemplo: la regla "responder en espanol" mejor en `copilot-instructions.md`
  que repetirla en cada prompt.

### 3.6. Idioma de los prompts

- Mantener un solo idioma por prompt. En este repo: **espanol** (coherente
  con lo existente).
- Evaluar a futuro: en algunos modelos los prompts en ingles producen
  ligeramente mejores resultados. No es razon suficiente para cambiar todo.

### 3.7. Settings Sync

- Verificar tras cada actualizacion mayor de VS Code que los prompts de
  usuario se sincronizan como esperas. El comportamiento ha cambiado entre
  versiones.

### 3.8. Backups

- Hacer copia ocasional de `AppData\Roaming\Code\User\prompts\` si tienes
  prompts personales no versionados. Una reinstalacion limpia los borra.

## 4. Que podria faltar a futuro

Ideas que no estan implementadas pero podrian añadirse:

- [ ] Script para **sincronizar** `Prompts/<Nombre>/*.prompt.md` ->
      `.github/prompts/` automaticamente (npm/pwsh/bat).
- [ ] **Test runner** que valide el frontmatter de todos los `.prompt.md`
      contra la norma (`yamllint` + reglas custom).
- [ ] **Pre-commit hook** que rechace prompts que no cumplan la norma.
- [ ] Plantilla **bilingue** (ES + EN) si en el futuro hay equipos
      internacionales.
- [ ] Documentar **otros IDEs** (JetBrains, Cursor) si el equipo los adopta.
- [ ] Guia para **Copilot CLI** y **Copilot Workspace** si se empiezan a usar.
- [ ] Galeria de **ejemplos avanzados**: prompts que invocan otros prompts,
      prompts con multiples argumentos, etc.

## 5. Decisiones pendientes

- ¿Adoptamos prefijos por dominio (`Code-`, `Docs-`) **ya** o cuando haya N
  prompts?
- ¿Movemos los `.prompt.md` a `.github/prompts/` (compatibilidad maxima con
  Visual Studio) o mantenemos `Prompts/` con `chat.promptFilesLocations`
  (sin duplicar archivos)?
- ¿Quien revisa los PRs que añaden o modifican prompts?

Documentar la decision en este archivo cuando se tome.
