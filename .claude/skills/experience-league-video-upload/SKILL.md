---
name: experience-league-video-upload
description: Se utiliza cuando un usuario desea enviar/cargar un vídeo en Experience League (video.tv.adobe.com/KT video submission) para incrustarlo a través de >[!VIDEO] en el markdown de este repositorio (abarca rellenar el formulario de envío con automatización del explorador, los valores predeterminados de este repositorio y lo que nunca debe automatizarse).
source-git-commit: 14f10c231373992c49a8bb93c043556305b6280d
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 1%

---


# Carga de vídeo de Experience League

## Información general

Los vídeos de Experience League no están alojados en este repositorio: se sube un(a) `.mp4` local a través de un formulario de envío independiente, que devuelve una URL `video.tv.adobe.com` que luego incrustó con `>[!VIDEO](...)` (consulte [[experience-league-markdown]]). Esta aptitud rellena ese formulario mediante la automatización del explorador, hasta el (sin incluir) adjuntar el archivo y enviar.

Formulario: https://81368-exlmpcvideoupload.adobeio-static.net/#/

## Recomendación de archivo de vídeo

Antes de que el usuario registre o seleccione un clip, recomiende una relación de aspecto de **16:9** con una resolución máxima de **1920 x 1080 píxeles**; se trata del requisito establecido por el formulario, no solo de una preferencia de estilo. Menciónelo de forma proactiva (por ejemplo, cuando un usuario dice que está a punto de capturar una grabación de pantalla para esto), no solo si se le solicita.

## Regla rígida: no adjuntar nunca el archivo ni enviarlo

Al enviar, se crea un ticket real de KT Jira y se sube a la plataforma de vídeo de producción, una acción exterior y difícil de revertir. **Deténgase siempre** una vez que se rellenen todos los demás campos y devuélvalos al usuario para el archivo de vídeo y el clic final de envío, incluso si no repiten la instrucción la próxima vez. Esta es la opción predeterminada para esta aptitud, no algo que deba volver a confirmarse por solicitud; solo omita esta parada si el usuario indica explícitamente que se debe enviar en esa misma solicitud.

## Requisitos previos

Necesita el servidor MCP `chrome-devtools`, que **no** está comprometido con este repositorio (no se debe forzar un MCP de automatización de explorador en cada colaborador). Si no está cargada:

1. Crear `.mcp.json` en la raíz del repositorio:

   ```json
   {
     "mcpServers": {
       "chrome-devtools": {
         "command": "npx",
         "args": ["-y", "chrome-devtools-mcp@latest", "--accept-insecure-certs", "--no-usage-statistics"]
       }
     }
   }
   ```

2. Agregar `.mcp.json` a `.gitignore` (herramientas personales, no compartidas).
3. En `.claude/settings.local.json`, agregue `"enableAllProjectMcpServers": true` y `"enabledMcpjsonServers": ["chrome-devtools"]`.
4. Indique al usuario que reinicie el código Claude (o que ejecute `/mcp`): los servidores MCP solo se cargan al inicio; esto no se puede hacer a mitad de la sesión.

## Valores predeterminados de este repositorio

A menos que el usuario indique lo contrario, utilice:

| Campo | Predeterminado | ¿Por qué? |
|---|---|---|
| Nube | `Experience Cloud` | — |
| Producto | `AEM` | Valor predeterminado especificado por el usuario para este repositorio (el formulario también enumera `AEM as a Cloud Service`; no lo sustituya a menos que se le solicite) |
| Subproducto | `AEM Sites` | Coincidencia más cercana; el formulario no tiene entrada &quot;Sites Optimizer&quot; |
| Funciones | `User` | El contenido de las comprobaciones/Sites Optimizer está dirigido a autores/especialistas en marketing, no a administradores/desarrolladores, a menos que el vídeo esté claramente dirigido a una audiencia técnica |
| Niveles de aptitudes | `Beginner` | A menos que el flujo de trabajo mostrado tenga requisitos previos reales |
| Género de voz(s) en vídeo | `No voices` | Sólo para grabaciones de pantalla silenciosa: pregunte si el clip tiene narración |
| Tipo de vídeo | Preguntar o deducir del contenido | Las opciones activas son `Event` / `Feature` / `Technical` / `Value`: un tutorial de la interfaz de usuario suele ser `Feature` |
| Correo electrónico | lo que esté precargado | El formulario rellena automáticamente el correo electrónico de Adobe del usuario que ha iniciado sesión; no lo sobrescriba |

## Etapas

1. `mcp__chrome-devtools__new_page` a la dirección URL del formulario.
2. `mcp__chrome-devtools__take_snapshot` y espere (`mcp__chrome-devtools__wait_for` el `"Title"`) hasta que los datos del formulario terminen de cargarse: comienza con un mensaje &quot;Cargando datos de formulario...&quot; hilandero.
3. Rellenar **Título** y **Descripción**: la descripción es un cuadro de texto enriquecido editable con contenido, no un `<textarea>` sin formato. `fill`/`fill_form` en él silenciosamente sin operaciones (el valor no toma y el error &quot;requerido&quot; permanece). En su lugar: `click` lo usa para centrarse y después `mcp__chrome-devtools__type_text` con el texto.
4. Los menús desplegables (**Tipo de vídeo**, **Género de voz(s) de vídeo**, **Nube**, **Producto**, **Subproducto**, **Nombre del evento**) son botones de cuadro de lista personalizados, no `<select>` nativos. Para cada uno: `click` el botón para abrirlo, lea las opciones reales de la instantánea (están cargadas con API; no suponga que la ortografía de la opción exacta de la tabla predeterminada sigue siendo la actual) y, a continuación, `click` la `option` coincidente.
5. **Product** y **Sub-product** están deshabilitados hasta que se establezca su campo principal (Product need Cloud; Sub-product need Product); rellénelos en ese orden.
6. **Los roles** y **Niveles de habilidad** son grupos de casillas de verificación — `fill_form` con `"value": "true"` en la casilla de verificación `uid`s funciona bien aquí (a diferencia del campo de descripción).
7. Detente. Obtenga una captura de pantalla, resuma lo que se configuró y por qué (especialmente cualquier valor predeterminado que se haya sustituido, como Producto/subproducto), y dígale al usuario que adjunte el vídeo y se envíe.
8. Una vez que el usuario indique que ha enviado el formulario, pídale la URL del vídeo MPC de Adobe resultante (que se muestra en el formulario después de la carga; por ejemplo, `https://video.tv.adobe.com/v/3496629?learn=on`). Utilícelo para rellenar el código abreviado de `>[!VIDEO](...)` dondequiera que vaya este vídeo; no cree ni adivine usted mismo la dirección URL o el ID.

## Validación de una URL de vídeo devuelta

Siempre que un usuario le entregue una URL de vídeo para incrustar (paso 8 anterior o en cualquier otro momento):

- **Rechazar cualquier cosa que no esté en `video.tv.adobe.com`.** Los vídeos deben alojarse por [[experience-league-markdown]] (un vínculo a YouTube, un host de archivos o cualquier otro dominio no es un destino válido de `>[!VIDEO]`). Indique al usuario que debe pasar primero por el flujo de carga de este repositorio; no lo incruste.
- **Si es una URL `video.tv.adobe.com` válida a la que le falta `&enablevpops`, agréguela** antes de incrustarla (coincide con la convención que ya usan los demás `>[!VIDEO]` en este repositorio; consulte `help/home.md`, `help/documentation/trial.md`, etc.). Anexar `&enablevpops` si ya hay un `?`; en caso contrario, `?enablevpops`.

## Errores comunes

- Intentando `fill`/`fill_form` en el campo Descripción y avanzando cuando el banner del error siga mostrando &quot;Se requiere una descripción&quot;. — compruebe la lista de errores después de cada paso, no solo al final.
- Adivinando el texto de opción desplegable de la memoria en lugar de abrir la lista desplegable: los valores reales (por ejemplo, `No voices` para el sexo de la voz, `Feature`/`Technical`/`Value` para el tipo de vídeo, la división AEM/AEM-as-a-Cloud-Service en Producto) no se pueden adivinar y cambian independientemente de este documento.
- Haciendo clic en **Cargar vídeo** / adjuntando un archivo &quot;para guardar al usuario un paso&quot;. No... consulte Regla Hard más arriba.
