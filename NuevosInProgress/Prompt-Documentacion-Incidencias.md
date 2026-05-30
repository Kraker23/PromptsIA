# 📝 Prompt reutilizable — Documentación de incidencias

> Guarda este archivo. Copia el bloque de prompt y adáptalo para cada nueva incidencia.

---

## Requisitos previos para usar este prompt

Antes de lanzar el prompt, asegúrate de tener:

| Requisito | Detalle |
|---|---|
| **Agent Mode activo** | Copilot debe estar en modo agente (no modo chat) para poder ejecutar comandos de terminal |
| **Git disponible** | Git debe estar instalado. Si no está en el PATH del sistema, Copilot lo buscará automáticamente |
| **Rama de trabajo activa** | Debes estar en la rama de la incidencia que quieres documentar |
| **Rama base conocida** | Normalmente `develop` o `main` |
| **ID del ticket en el nombre de la rama** | Por convención: `feature/TICKET-1234-NombreDescriptivo` |

---

## Prompt

Copia el siguiente bloque, sustituye los valores entre `[corchetes]` y pégalo en Copilot en modo agente:

---

```
Estoy trabajando en la rama de git `[NOMBRE_RAMA]` (por ejemplo `feature/TICKET-1234-Descripcion`).

Quiero que analices los cambios de esta rama respecto a `[RAMA_BASE]` (normalmente `develop`) 
y generes 4 documentos de documentación en la carpeta `Docs/` de la raíz del proyecto.

Los archivos deben llamarse exactamente así:
- `[ID_TICKET]-[NombreRama]-Tecnica.md`
- `[ID_TICKET]-[NombreRama]-Funcional.md`
- `[ID_TICKET]-[NombreRama]-Testeo.md`
- `[ID_TICKET]-[NombreRama] - Resumen del desarrollo.md`

INSTRUCCIONES POR DOCUMENTO:

**1. Resumen del desarrollo** — El primero en crearse, actúa como portada del conjunto.
   - Cabecera con tabla de metadatos: Incidencia, Nombre, Rama, Commit, Proyecto, Fecha, Estado
   - Sección "¿De qué trata esta incidencia?" explicada en lenguaje llano (apta para no técnicos)
   - Callout resumido con lo más importante (usando blockquote con emoji 💡)
   - Sección "Cambios más importantes" con subsecciones por temática (seguridad, bugs, mejoras), 
	 cada una con emoji y explicación sin jerga técnica
   - Tabla de todos los archivos modificados con: archivo, tipo de cambio (con emoji), descripción breve
   - Tabla "Documentación relacionada" con los otros 3 docs, a quién van dirigidos y qué contienen
   - Sin sección de pasos ni de decisiones técnicas

**2. Funcional** — Para producto, negocio y cualquier persona del equipo.
   - Cabecera con tabla de metadatos e indicar audiencia: "Producto · Negocio · Gestores · Cualquier persona del equipo"
   - Párrafo introductorio explicando qué es el documento y para quién
   - Secciones con formato "¿Qué pasaba antes? / ¿Qué pasa ahora? / ¿Por qué importa?" para cada cambio visible
   - Sección de seguridad separada, con lenguaje accesible
   - Sección de correcciones de comportamiento incorrecto
   - Sección de mejoras internas (tabla resumida, sin código)
   - Tabla resumen final "¿Qué esperar ahora?" por área de la aplicación
   - Glosario al final con los términos técnicos que aparezcan (bug, rol, hardcodeado, timer, etc.)
   - Sin bloques de código

**3. Técnica** — Para desarrolladores y revisores de código.
   - Cabecera con tabla de metadatos e indicar audiencia: "Desarrolladores · Revisores de código · Tech Leads"
   - Párrafo introductorio con referencia al doc Funcional para quien no necesite detalles técnicos
   - Resumen por capa en tabla (Datos, Servicios, Controladores, Páginas, Configuración)
   - Por cada archivo modificado: problema detectado, solución aplicada, bloque de código "Antes / Después"
   - Los cambios más críticos deben marcarse con ⚠️ y una advertencia de riesgo de regresión
   - Tabla final de archivos afectados con columna de "Riesgo de regresión" (Alto/Medio/Bajo)
   - Callout final destacando el cambio de mayor riesgo y referencia al caso de prueba correspondiente

**4. Testeo** — Para QA, testers y responsables de validación.
   - Cabecera con tabla de metadatos, indicar tipo de pruebas ("Manual — entorno local en modo Debug") y audiencia
   - Párrafo introductorio explicando el documento sin jerga técnica, con referencia al doc Funcional
   - Sección de prerequisitos en lista de checkboxes
   - Por cada caso de prueba (TC-NN):
	 - Mini tabla con: qué se verifica, prioridad (🔴🟡🟢), relacionado con qué cambio
	 - Pasos numerados en lenguaje accesible (sin mencionar código interno)
	 - Sección "¿Qué debe pasar?" en lugar de "Resultado esperado"
	 - Señal de fallo claramente marcada con 🚨 donde sea relevante
   - El caso de prueba del cambio más crítico debe llevar ⚠️ en el título
   - Tabla de registro de resultados al final con columnas: ID, caso, prioridad, resultado, observaciones, ejecutado por, fecha
   - Leyenda de resultados: ✅ Correcto — ❌ Fallo — ⚠️ Parcial — ⬜ Pendiente

REQUISITOS GENERALES PARA TODOS LOS DOCUMENTOS:
- Ejecuta `git log [RAMA_BASE]..HEAD --oneline` y `git diff [RAMA_BASE]...HEAD` para basar 
  la documentación en los cambios reales del repositorio
- Usa emojis como guías visuales en títulos y tablas (Confluence los renderiza correctamente)
- Usa tablas de metadatos en la cabecera de cada documento (no blockquotes de una sola línea)
- Los documentos Funcional y Testeo deben ser comprensibles para personas sin conocimientos de programación
- El documento Técnico debe ser preciso y referenciable por desarrolladores
- Todo en español
- Pie de página en todos los documentos: 
  `*Generado para la incidencia \`[ID_TICKET]\` — rama \`[NOMBRE_RAMA]\`*`
```

---

## Valores a sustituir

| Placeholder | Ejemplo | Dónde encontrarlo |
|---|---|---|
| `[NOMBRE_RAMA]` | `feature/ISBS-5123-MejorasIA` | `git branch` o nombre de la rama activa |
| `[RAMA_BASE]` | `develop` | Rama de la que salió esta rama de trabajo |
| `[ID_TICKET]` | `ISBS-5123` | Extraído del nombre de la rama |
| `[NombreRama]` | `MejorasIA` | La parte descriptiva del nombre de la rama |

---

## Archivos generados (resultado esperado)

```
Docs/
├── [ID_TICKET]-[NombreRama] - Resumen del desarrollo.md   ← Portada / visión general
├── [ID_TICKET]-[NombreRama]-Funcional.md                  ← Para producto y negocio
├── [ID_TICKET]-[NombreRama]-Tecnica.md                    ← Para desarrolladores
└── [ID_TICKET]-[NombreRama]-Testeo.md                     ← Para QA y validación
```

---

## Notas de uso

- Los documentos están pensados para **copiarse manualmente a Confluence**. El formato Markdown es compatible con el editor de Confluence.
- Las tablas, emojis y blockquotes (`>`) se renderizan correctamente en Confluence.
- Los bloques de código (``` ``` ```) también se renderizan en Confluence como bloques de código.
- Si el proyecto tiene más de una rama base (p. ej. `main` y `develop`), usa siempre la más cercana al punto de partida de la rama de trabajo.

---

*Archivo mantenido en `Docs/Prompt-Documentacion-Incidencias.md`*
