---
source-git-commit: 14f10c231373992c49a8bb93c043556305b6280d
workflow-type: tm+mt
source-wordcount: '1030'
ht-degree: 0%

---
# Experience League Markdown: referencia de sintaxis completa

Comprimido desde https://experienceleague.adobe.com/en/docs/authoring-guide/using/markdown/markdown-syntax (última confirmación contra la página &quot;Última actualización: 17 de junio de 2026&quot;). Vuelva a recuperar la página activa si algo aquí parece estar desactualizado.

## Frontmatter y título

```markdown
---
title: Title for search optimization
description: This is the article description used for search optimization.
---
# Article title
```

La línea inmediatamente después del `---` de cierre (y una línea en blanco) debe ser el `# Title`, y debe coincidir con `title:` en la primera línea.

## Formato de texto básico

- Negrita: `**bold**`
- Cursiva: `*italic*`
- Negrita+cursiva: `***both***`
- Omitir un gráfico de formato: `\*not italic\*`
- Los párrafos no necesitan sintaxis especial, sólo una línea en blanco entre ellos.

## Encabezados

```markdown
# This is level 1 (article title)
## This is level 2 (mini-TOC entry)
### This is level 3
```

- `#` (H1) = título del artículo, debe coincidir con el contenido previo `title`.
- `##` (H2) = aparece en el mini-TOC de forma predeterminada (`mini-toc-levels: 3` en frontmatter para mostrar más niveles).
- Nunca omita un nivel (`##` → `####` no es válido).
- Se requiere una línea en blanco antes de **y** después de cada encabezado.
- Longitud máxima del encabezado: 69 caracteres (EN), 120 (localizado).
- Id. de encabezado/anclaje: `## Creating processing rules {#processing-rules}` — en minúsculas, con guiones. Obligatorio si el texto del encabezado comienza con un número (por ejemplo, año). Sin un ID explícito, el anclaje predeterminado es el texto de encabezado autofiltrado.

## Notas / advertencias

Tipos estándar: `NOTE`, `TIP`, `IMPORTANT`, `WARNING`. Tipos de solo EXL más recientes: `ADMIN`, `AVAILABILITY`, `PREREQUISITES`, `INFO`, `ERROR`, `SUCCESS`.

```markdown
>[!NOTE]
>
>This is a standard NOTE block.
>
>It can include multiple paragraphs.
```

Cada línea del bloque comienza con `>`. Incluya una línea `>` vacía justo después del marcador de tipo.

## Pestañas

```markdown
>[!BEGINTABS]

>[!TAB iOS]

Content for the iOS tab.

>[!TAB Android]

Content for the Android tab.

>[!ENDTABS]
```

- No se pueden anidar conjuntos de pestañas dentro de conjuntos de pestañas o conjuntos de pestañas dentro de listas.
- Los títulos de las fichas se representan de forma literal, sin formato de marcado dentro de `>[!TAB ...]`.
- Varios conjuntos de pestañas funcionan bien en una página.

## Vídeo

```markdown
>[!VIDEO](https://video.tv.adobe.com/v/27069/?learn=on&enablevpops)
```

- El vídeo ya debe estar hospedado en `video.tv.adobe.com` (Adobe TV/MPC); no se admiten los vínculos de archivos de vídeo sin procesar ni las etiquetas `<video>`.
- Parámetros de consulta recomendados: `?learn=on&enablevpops` (la forma canónica utilizada por cada incrustación en este repositorio). Agregar `&autoplay=true` a la reproducción automática.
- Transcripciones: agregue `{transcript=true}` al código abreviado o establezca `auto-video-transcripts: true` en `TOC.md`/`metadata.md` para toda la guía/repositorio.

## Insignias

Distintivo en línea (se procesa donde se coloca):

```markdown
[!BADGE Beta]{type=Informative url="https://www.example.com" tooltip="Go to example.com"}
```

Distintivo de metadatos (se procesa por encima de H1) — en frontmatter:

```yaml
badgePremium: label="Premium" type="Positive" url="https://www.premium-product.com" tooltip="Download Premium"
```

- `type` (sin distinción de mayúsculas): `Informative` (predeterminado/azul), `Positive` (verde), `Negative` (rojo), `Neutral` (gris oscuro), `Caution` (amarillo).
- Solo se requiere la etiqueta; `type`/`url`/`tooltip` es opcional.
- Máximo de **dos** insignias de metadatos por artículo (configurable, pero preguntar antes de confiar en una excepción).
- Los valores de las insignias de metadatos deben estar entre comillas. Se debe citar el distintivo en línea `url`/`tooltip`.
- Las direcciones URL de distintivo utilizadas desde `TOC.md` deben ser relativas a la raíz (`/help/guide/article.md`), no relativas: las entradas del índice se aplican a todas las carpetas.
- `before-title="false"` mueve un distintivo de metadatos debajo de H1.
- Agregue `newtab=true` para abrir la dirección URL del distintivo en una nueva pestaña.

## Imágenes

```markdown
![alt text](assets/logo.png "Hover text"){width="300" align="center"}
```

- `align`: solo `center` o `right` — no `left`, no `valign`.
- `width`: píxeles (`"300"`) o porcentaje del área de vista (`"50%"`).
- `zoomable="yes"` hace que la imagen haga clic para ampliarse (no la combine con una imagen que también sea un vínculo, el vínculo gana).
- Ruta de acceso relativa a la raíz para imágenes compartidas: `/help/assets/imagename.png`.
- Límites: límite máximo de 100 MB (GitHub), 5 MB antes de que empiece a preocuparse, 20 MB déclencheur un error de validación. Máximo de 100 imágenes por artículo (límite de procesamiento EDS).

## Vínculos y referencias cruzadas

- Externo: `[Adobe](https://www.adobe.com)`
- Dirección URL vacía como vínculo: `<https://www.adobe.com>`: una dirección URL vacía sin ajustar hace que **no** se vincule automáticamente.
- Referencia cruzada relativa: `[Overview](collaborative-doc-instructions/overview.md)` — resolver desde la ubicación del archivo *origen*; admite `./`, `../`, `../../`.
- Referencia cruzada relativa a la raíz: `[Overview](/help/using/docile-rules/introduction.md)` — funciona desde cualquier archivo en el repositorio independientemente de la ubicación de origen.
- Vínculo profundo a un encabezado: el destino necesita `{#heading-id}`; vincular con `[Text](file.md#heading-id)` (o solo `#heading-id` para la misma página).
- Abrir en ficha nueva: `[See What's new](whats-new.md){target="_blank"}`.

## Listas

```markdown
1. This is step 1.
1. This is the next step.
   1. Sub-step (indent 3 spaces for numbered lists)
   1. Sub-step
```

```markdown
* First item.
* Second item.
```

- Listas numeradas: escribir siempre `1.` (o siempre `1)`): GitHub procesa la secuencia real. Elija un estilo (`.` frente a `)`) y manténgase coherente con el artículo.
- Listas de viñetas: elija una de `*`, `-`, `+` y manténgase coherente: mezclarlas en el mismo artículo es un error de validación. Convención en la mayoría de los repositorios: `*`.
- Línea en blanco requerida antes y después de cualquier lista.
- El contenido entre elementos de lista (imágenes, tablas, notas) debe tener sangría al inicio del texto (3 espacios para listas numeradas, 2 para listas con viñetas) o romperá la lista. La sangría excesiva (6 espacios) lo convierte en un bloque de código.

## Bloques de código

En línea: `` `code` `` — o envuelva en triples acentos graves en línea si necesita un acento grave literal dentro.

Delimitado:

&grave;&grave;&grave;&grave;markdown

```javascript
var x = 1;
```

&grave;&grave;&grave;&grave;

- Especifique siempre un idioma para el resaltado de sintaxis + el botón Copiar.
- Línea en blanco requerida encima y debajo del bloque delimitado.
- Números de línea: `` ``&#x200B;`html {line-numbers="true"} `&#x200B;&grave;
- Iniciar numeración en otra parte: `` ``&#x200B;`html {line-numbers="true" start-line="7"} `&#x200B;&grave;
- Resaltar líneas: `` ``&#x200B;`html {line-numbers="true" start-line="7" highlight="11-13, 16"} `&#x200B;&grave;
- El contenido del bloque de código nunca se traduce (excepto las etiquetas `!UICONTROL`/`!DNL`, que se eliminan en el momento de la publicación).
- No hay formato de markdown/HTML (como `<i>`) que funcione dentro de bloques de código; utilice corchetes angulares o texto sin formato para los marcadores de posición.

## Tablas

- Las tablas de tuberías GFM estándar funcionan para casos simples.
- Se permiten tablas HTML para casos especiales (por ejemplo, una tabla sin fila de encabezado); en caso contrario, prefiera markdown.
- Se permite un HTML limitado dentro de las celdas de la tabla de marcado: `<p>`, `<br>`, `<ul>`, `<ol>`.
- Las tablas se pueden configurar en procesamiento automático o fijo; consulte el artículo &quot;Tablas&quot; vinculado desde la guía de sintaxis si necesita ese nivel de control.

## Secciones contraíbles

```markdown
+++See details

This is text inside a collapsible section.

* Bullet one
* Bullet two

+++
```

- No anide secciones contraíbles: no se procesarán correctamente (y no fallarán en la validación, por lo que el error se enviará en silencio).
- Se requieren líneas en blanco alrededor de listas internas/bloques de código dentro de la sección, igual que en cualquier otra parte.

## Resaltado de texto

```markdown
This sentence is normal. <span class="preview">This text is highlighted.</span>
```

Use `<span class="preview">` para resaltar en línea/párrafo, `<div class="preview">` para varios párrafos/componentes.

## Fragmentos e incluye

- Anclajes H2 compartidos de `help/snippets.md` de un repositorio: referencia con `{{anchor-id}}`.
- Archivos de inclusión compartidos de `help/_includes/*.md`: referencia con `{{$include /help/_includes/filename.md}}`.

## Comentarios

```markdown
<!-- standard comment code -->
```

- Nunca use `<!--> bad comment syntax <-->` (faltan guiones): se representa de forma visible en lugar de ocultar el texto.
- Los comentarios son invisibles en los documentos procesados, pero **visibles para cualquiera que vea el archivo .md sin procesar en GitHub**; sin secretos ni información confidencial.
- Evite los comentarios dentro de las listas con viñetas (puede interrumpir la renderización de la lista). En `TOC.md`, solo las líneas de comentario al final del archivo, nunca en medio de la lista.

## Solución alternativa con líneas en blanco

El procesador contrae las líneas en blanco adicionales del origen. Para forzar el espacio vertical visible, coloque `<br>&nbsp;` en su propia línea donde desee colocar el espacio.

## Caracteres de escape

- Caracteres de escape de barra invertida: `` # { } [ ] * + - . ! ``, p. ej. `\# not a heading`.
- Para los corchetes angulares (`<placeholder>`), la barra invertida no funciona; use un bloque de código en línea (`` `<placeholder>` ``) o entidades HTML (`&lt;placeholder&gt;`).
- Las entidades de HTML dentro de bloques de código **no** se convierten de nuevo en el carácter — `&gt;` permanece allí el texto literal.
- Los metadatos (YAML frontmatter) tienen sus propias reglas de escape: si un valor comienza con un carácter especial como `:` o `[`, cite todo el valor: `title: "Processing rules: A new beginning"`.

## Lista de permitidos restringida de HTML

Solo se permiten estas etiquetas HTML en Markdown; cualquier otra cosa es un error de validación:

```
table  tbody  td  tfoot  thead  th  tr  col  colgroup
p  ul  ol  li  br
b  i  strong  u  s  em  sub  sup  span
caption  a  img  div
pre  code  codeblock
```

Prefiera la sintaxis de markdown en lugar de HTML siempre que markdown pueda hacer el trabajo: HTML solo está disponible para casos extremos, como una tabla sin encabezado.

## Explícitamente no compatible (no lo utilice aunque las procese una previsualización local)

- Reglas horizontales (`***`, `<hr>`)
- Códigos abreviados de emojis (`:bowtie:`)
- Listas de tareas (`- [x] done`)
- Cita de bloque *componentes* más allá de los códigos abreviados de nota, ficha o vídeo (las citas de bloque `>` simples se representan como una cita, no como un componente con estilo)
- Sintaxis de lista de definición de Markdown (use negrita manual + formato de guión en su lugar: `**Frog** - An amphibious green creature.`)
- `valign` en imágenes

## Límites de tamaño de archivo/recuento que vale la pena conocer

| Cosa | Límite |
|---|---|
| Tamaño de archivo de imagen/descarga | Advertencia de validación a 5 MB, error a 20 MB, límite de GitHub 100 MB |
| Imágenes por artículo | 100 (límite de procesamiento EDS) |
| Distintivos de metadatos por artículo | 2 (predeterminado) |
