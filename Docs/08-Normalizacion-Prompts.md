# 08 - Normalizacion de Prompts

Este documento es la **fuente de verdad** que todo `.prompt.md` del repositorio
debe cumplir. Si una regla aqui choca con otra guia, **gana esta**.

> Toda nueva propuesta de prompt que no cumpla este estandar debe rechazarse
> en revision.

---

## 1. Estructura de carpeta

Cada prompt vive en **su propia carpeta** bajo `Prompts/`:

```
Prompts/
  NombreDelComando/
    NombreDelComando.prompt.md
    Chuleta-Rapida-NombreDelComando.md
    Guia-Comando-NombreDelComando.md
```

- Una carpeta = un comando.
- Los tres archivos son **obligatorios**.
- La carpeta `Prompts/_template/` es la plantilla de referencia.

## 2. Naming

| Elemento                | Regla                                                  | Ejemplo                       |
|-------------------------|--------------------------------------------------------|-------------------------------|
| Carpeta                 | PascalCase, sin espacios, sin acentos                  | `Comment`, `RegistroCambios`  |
| Archivo prompt          | `<NombreCarpeta>.prompt.md`                            | `Comment.prompt.md`           |
| Archivo chuleta         | `Chuleta-Rapida-<NombreCarpeta>.md`                    | `Chuleta-Rapida-Comment.md`   |
| Archivo guia            | `Guia-Comando-<NombreCarpeta>.md`                      | `Guia-Comando-Comment.md`     |
| Campo `name:`           | Igual al nombre de carpeta (sin extension)             | `name: "Comment"`             |
| Invocacion en Chat      | `/<name>`                                              | `/Comment`                    |

Reglas adicionales:

- **Sin espacios, sin acentos, sin caracteres especiales** en ningun nombre.
- **PascalCase** (no kebab-case ni snake_case) para el nombre del comando.
- El nombre debe ser **unico** en todo el repositorio.

## 3. Frontmatter obligatorio

Todo `.prompt.md` debe abrir con un bloque YAML con estos campos:

```yaml
---
description: "Texto corto en una linea de lo que hace el comando"
name: "NombreDelComando"
argument-hint: "pistaArgumento"   # opcional, omitir si el comando no recibe argumento
agent: "agent"
---
```

Reglas:

- `description`: 1 linea, < 100 caracteres, **sin punto final**.
- `name`: coincide exactamente con el nombre de carpeta y de archivo.
- `argument-hint`: solo si el comando acepta argumento. **Omitir la linea** si no.
- `agent`: por defecto `"agent"`. Cambiar solo si se sabe lo que se hace.
- Todos los valores **entre comillas dobles**.
- Sin tabuladores, solo espacios.

## 4. Cuerpo del prompt

El cuerpo (despues del frontmatter) debe seguir esta plantilla:

```md
<Frase imperativa de una linea con la accion principal.>

Reglas:
- <Regla 1>
- <Regla 2>
- ...

No hacer:
- <Antiregla 1>
- ...
```

Reglas de estilo:

- **Imperativo** ("Inserta...", "Genera...", "Valida..."), no condicional.
- Listas con `-` (no `*` ni numeradas, salvo que el orden importe).
- Si el prompt usa el argumento, declararlo asi:
  `${input:pistaArgumento:Texto de ayuda mostrado al usuario}`
- **Sin acentos** en identificadores tecnicos (rutas, nombres de variables).
  En el texto explicativo, los acentos son opcionales pero deben ser consistentes.
- **Sin ejemplos de codigo largos** dentro del prompt (los ejemplos van en la guia).

## 5. Idioma

- **Espanol** para el cuerpo, descripcion y argument-hint.
- **Ingles** solo permitido para terminos tecnicos consolidados (`commit`, `null`, `array`).
- La chuleta y la guia tambien en espanol.

## 6. Codificacion y formato de archivo

- UTF-8 **sin BOM**.
- Fin de linea **LF** (no CRLF), aunque el repo este en Windows.
- Sin espacios al final de linea.
- Una linea en blanco al final del archivo.

## 7. Archivos acompañantes

Cada prompt debe ir acompañado de:

- `Chuleta-Rapida-<Nombre>.md`: resumen ultra-breve de uso (1 pantalla).
  Secciones minimas: `Uso`, `Que hace`, `Si no aparece`, `Archivo del prompt`.
- `Guia-Comando-<Nombre>.md`: explicacion completa (objetivo, enfoque, ubicacion,
  contenido, como usar, troubleshooting, referencia a este documento).

Las plantillas vacias estan en `Prompts/_template/`.

## 8. Compatibilidad VS Code / Visual Studio

- Mantener prompts **portables** entre ambos IDEs siempre que sea posible.
- Si un prompt usa una caracteristica especifica de un IDE (ej. un agente o
  placeholder no soportado en el otro), indicarlo **al inicio del cuerpo** con:
  `<!-- Compatibilidad: solo VS Code -->` o `<!-- Compatibilidad: solo Visual Studio -->`.

## 9. Seguridad

- **Prohibido** incluir en un `.prompt.md` versionado:
  - Tokens, claves API, contraseñas.
  - Rutas absolutas con nombre de usuario real (usar `<usuario>`).
  - Nombres de servidores, IPs internas, datos de clientes.
- Si necesitas un dato sensible en tiempo de ejecucion, pasalo como argumento
  con `${input:...}`, nunca lo embebas.

## 10. Checklist pre-commit

Antes de hacer commit de un prompt nuevo o modificado, verifica:

- [ ] La carpeta sigue la estructura `Prompts/<Nombre>/` con los **3 archivos**.
- [ ] El nombre cumple PascalCase, sin acentos ni espacios, y es unico.
- [ ] El frontmatter tiene `description`, `name`, `agent` (y `argument-hint` si aplica).
- [ ] `name` coincide con el nombre de archivo y de carpeta.
- [ ] Cuerpo en imperativo, con secciones `Reglas:` y `No hacer:`.
- [ ] Idioma espanol, codificacion UTF-8 sin BOM, fin de linea LF.
- [ ] Sin datos sensibles ni rutas con nombre de usuario real.
- [ ] Probado en local: tras `Developer: Reload Window`, el comando `/Nombre`
      aparece en el menu de Copilot Chat y funciona como se espera.
- [ ] La chuleta y la guia estan actualizadas y referencian la ruta correcta.

## 11. Ejemplo correcto vs incorrecto

### Correcto

```md
---
description: "Inserta una linea de comentario en codigo usando el texto indicado tras /Comment"
name: "Comment"
argument-hint: "infoComentario"
agent: "agent"
---
Inserta una sola linea de comentario en el archivo activo, en la linea del cursor.

Reglas:
- Usa como texto del comentario lo que el usuario escriba tras `/Comment`.
- Si no hay texto, usa `${input:infoComentario:Escribe el texto del comentario}`.
- Respeta el estilo de comentario del lenguaje del archivo activo.

No hacer:
- No modifiques otras lineas.
- No añadas explicaciones adicionales.
```

### Incorrecto (y por que)

```md
---
Description: comentario rapido.        # mayusculas en clave, sin comillas, con punto
nombre: comment_rapido                 # clave en espanol, snake_case, no PascalCase
agent: agent                           # sin comillas
---
Pues mira, esto hace que se inserte un comentario y tal, y si no le pasas
nada pues no hace nada, o a veces si, depende.   # tono conversacional, ambiguo
```

Problemas detectados:

1. Claves del frontmatter con mayuscula inicial / en espanol.
2. Valores sin comillas dobles.
3. Naming en `snake_case`.
4. Cuerpo no imperativo y ambiguo.
5. Sin secciones `Reglas:` / `No hacer:`.
6. Falta de archivos acompañantes (chuleta + guia).
