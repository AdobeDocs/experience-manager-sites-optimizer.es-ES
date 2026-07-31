---
name: experience-league-markdown
description: 'Se utiliza al escribir o editar archivos Markdown en un repositorio de Adobe Experience League/Adobe-Enterprise-Docs (help/**/*.md): rige el contenido preliminar, los encabezados, las notas (NOTE/TIP/IMPORTANT/WARNING/etc.), las pestañas (BEGINTABS/TAB/ENDTABS), las incrustaciones de vídeo, los distintivos, las imágenes, los vínculos/referencias cruzadas, las tablas, las listas, los bloques de código y la lista de permitidos de etiquetas restringidas de HTML que aplica la canalización de validación de Experience League.'
source-git-commit: 14f10c231373992c49a8bb93c043556305b6280d
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 1%

---


# Experience League Markdown

## Información general

Los documentos de Experience League utilizan Markdown al estilo de GitHub, además de un conjunto de extensiones personalizadas (códigos abreviados, insignias, pestañas e incrustaciones de vídeo basadas en blockquote). La canalización de creación **valida** estos archivos con sintaxis no admitida (etiquetas `<video>` sin procesar, `<hr>`, listas de tareas, caracteres de viñetas mixtos, niveles de encabezado omitidos, imágenes sobredimensionadas) causa un error de compilación/validación, no solo una unidad de estilo.

Source de la verdad: https://experienceleague.adobe.com/en/docs/authoring-guide/using/markdown/markdown-syntax (recupere esta página si el archivo reference.md local parece obsoleto; la fecha de la &quot;última actualización&quot; se encuentra en la parte superior).

Referencia de sintaxis completa con cada código abreviado y regla: [reference.md](reference.md). Léalo antes de escribir cualquier cosa que no sea trivial (pestañas, vídeo, insignias, tablas con HTML).

## Referencia rápida

| Elemento | Sintaxis | Notas |
|---|---|---|
| Frontmatter | `---\ntitle: ...\ndescription: ...\n---` | Línea en blanco, entonces `# Title` debe ser el siguiente |
| Niveles de encabezado | `#`, `##`, `###` | `#` = título (coincide con el contenido previo `title`), `##` = entradas de mini-TOC. Nunca saltes un nivel. Línea en blanco antes/después. Máx. 69 caracteres (EN) |
| Identificador de encabezado | `## Heading text {#custom-id}` | Requerido si el encabezado empieza por o contiene un número, p. ej. `## 2026 release notes {#2026-release-notes}` |
| Nota/sugerencia/etc. | `>[!NOTE]` entonces `>` entonces `>Text` (cada uno en su propia línea) | Tipos: NOTA, SUGERENCIA, IMPORTANTE, ADVERTENCIA, PRECAUCIÓN, ADMINISTRADOR, DISPONIBILIDAD, REQUISITOS PREVIOS, INFORMACIÓN, ERROR, ÉXITO |
| Pestañas | `>[!BEGINTABS]` / `>[!TAB Title]` / `>[!ENDTABS]` | No se pueden anidar conjuntos de pestañas; no se puede anidar dentro de listas |
| Vídeo | `>[!VIDEO](https://video.tv.adobe.com/v/ID/?learn=on&enablevpops)` | Debe alojarse en video.tv.adobe.com — sin vínculos sin procesar `<video>`/archivo |
| Imagen | `![alt text](assets/img.png "hover text"){width="300" align="center"}` | `align` es `center` o `right` solamente (no `left`, no `valign`) |
| Vínculo (relativo) | `[Text](../folder/file.md)` | Cuenta para la ubicación del archivo de origen |
| Vínculo (raíz) | `[Text](/help/guide/file.md)` | Funciona desde cualquier lugar del repositorio; necesario para las URL de insignias de TOC.md |
| Vínculo profundo | `[Text](file.md#heading-id)` | El encabezado de destino necesita un `{#heading-id}` explícito |
| Vínculo externo (URL vacía) | `<https://example.com>` | Las direcciones URL vacías NO se vinculan automáticamente: ajuste `< >` o use `[text](url)` |
| Lista con viñetas | `* item` (elija uno de `*`/`-`/`+`, mantenga la coherencia) | Línea en blanco antes/después de la lista; mezcla de marcadores = error de validación |
| Lista numerada | `1. item` (repetir `1.` cada línea) | GitHub procesa los números reales |
| Código (en línea) | `` `code` `` | Para nombres de archivo, comandos, valores y direcciones URL de ejemplo no validadas |
| Código (delimitado) | ` ```language ` ... ` ``` ` | Especificar siempre un idioma; línea en blanco antes o después; `{line-numbers="true" start-line="n" highlight="n-m"}` opcional |
| Insignia (en línea) | `[!BADGE Beta]{type=Informative url="..." tooltip="..."}` | `type`: informativo/positivo/negativo/neutro/precaución |
| Contraíble | `+++Summary` ... `+++` | No hay contraíbles anidados; líneas en blanco alrededor de listas/códigos internos |
| Hack de línea en blanco | `<br>&nbsp;` en su propia línea | El procesador contrae/ignora las líneas en blanco adicionales sin formato |
| Comentar | `<!-- text -->` | Nunca `<!--> text <-->`: visible para cualquiera que vea el archivo sin procesar en GitHub, por lo que no hay secretos |

## Errores comunes

- **Error de validación de → de `<video>`, `<iframe>` sin procesar u otro HTML** no incluido en la lista de permitidos. La lista de permitidos de HTML es: `table tbody td tfoot thead th tr col colgroup p ul ol li br b caption i strong u s span sub sup a img div em pre code codeblock`. Se rechaza cualquier otra cosa (incluido `<video>`/`<source>`): use el código abreviado `>[!VIDEO]` en su lugar, lo que requiere que el vídeo ya esté alojado en video.tv.adobe.com.
- **`<hr>`/ `***` reglas horizontales, códigos abreviados de emoji (`:bowtie:`), listas de tareas (`- [x]`)**: no se admiten; no las utilice aunque las procese una vista previa local.
- **Combinación de caracteres de viñeta** (`*` y `-` en la misma lista): error de validación. Elija uno por artículo.
- **No se permite omitir los niveles de encabezado** (`##` directamente a `####`).
- **Un encabezado numeral inicial sin un identificador explícito** (p. ej. `## 2026 release notes`) — debe agregar `{#some-id}` o el slug automático puede chocar o romperse.
- **Las direcciones URL vacías en prose** (`Visit https://example.com for more`) no se representarán como un vínculo. Ajustar en `< >` o usar `[text](url)`.
- **Líneas en blanco adicionales para el espaciado visual** — contraídas por el procesador. Use `<br>&nbsp;` en lugar de `<br>` o líneas nuevas repetidas.
- **Imágenes de más de ~5 MB** — advertencia de validación a 5 MB, error a 20 MB. Más de 100 imágenes en un artículo rompen el procesamiento (límite EDS).
- **Más de dos insignias en los metadatos de frontmatter**; no se permite de forma predeterminada.
- **Problemas de escape**: la tecla de escape de barra invertida solo funciona para `` # { } [ ] * + - . ! ``. Para `<` `>` en elementos como `<filename>` marcadores de posición, use un bloque de código en línea o entidades de HTML (`&lt;filename&gt;`), no una barra invertida.

## Antes de confirmar los cambios de Markdown

1. Presente la materia frontal, `# Title` sigue inmediatamente (después de la línea en blanco).
2. Cada encabezado tiene una línea en blanco antes y después; no se omiten niveles.
3. Cualquier vídeo es `>[!VIDEO](https://video.tv.adobe.com/...)`, no una etiqueta `<video>` sin procesar.
4. Cualquier código abreviado personalizado (`>[!NOTE]`, `>[!BEGINTABS]`, `>[!BADGE ...]`) coincide con la sintaxis exacta en [reference.md](reference.md), incluida la línea `>` en blanco dentro de bloques multilínea.
5. Las listas utilizan un estilo de viñeta/número coherente, con líneas en blanco alrededor de toda la lista.
6. Vínculos: los vínculos relativos se resuelven desde la carpeta del archivo *source*; los vínculos entre repositorios o TOC/distintivo utilizan el formulario relativo a la raíz (`/help/...`).
7. No hay ninguna etiqueta de HTML fuera de la lista de permitidos en la sección Errores comunes anterior.
