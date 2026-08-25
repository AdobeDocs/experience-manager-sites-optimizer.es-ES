---
source-git-commit: ed1960cc0364dc4169a454a4860b7463890e3b74
workflow-type: tm+mt
source-wordcount: '2275'
ht-degree: 0%

---
# Agente de documentos ASO — Canalización

Con referencia desde `SKILL.md`. Esta es la fuente fiable para el orden de ejecución; SKILL.md es
el resumen. Lea `config.yml` antes de comenzar — cada valor de `{braces}` a continuación es un
clave de configuración.

**Tratamiento de errores (se aplica a cada uno de los pasos siguientes).** Llamada de API/herramienta que genera errores (autenticación)
error, tiempo de espera, consulta mal formada, esquema inesperado) nunca es lo mismo que un
resultado vacío legítimo, y nunca se debe permitir que caiga en silencio en un
rama &quot;vacía&quot; o &quot;nada que hacer&quot; (por ejemplo, &quot;nada que hacer aquí&quot; en el paso 1.2, paso 3.3
&quot;registro épico de pendientes totalmente cubierto o todo en vuelo&quot;). Cuando se produzca un error en una llamada, detener y registrar el
error real en el resumen de la ejecución en lugar de continuar como si se devolviera limpiamente.

## Paso 0: Comprobación preliminar

1. `pwd` y la marca `guidelines.md` + `.claude/skills/aso-doc-agent/config.yml` existen. Si no, deténgase — directorio incorrecto.
2. `gh auth status` — confirmar que la cuenta `sandsinh_adobe` tiene un token válido en este host. **No ejecutar nunca`gh auth switch`**: cambia la cuenta activa de `gh` en todo el equipo como un efecto secundario, que puede bloquear silenciosamente cualquier otro terminal o proceso de este equipo en la cuenta incorrecta para una ejecución diaria desatendida. En su lugar, se debe establecer el ámbito de esta ejecución solamente: `export GH_TOKEN=$(gh auth token --user sandsinh_adobe)` una vez al principio, de modo que cada llamada a `gh` a continuación utilice ese token a través de la variable env `GH_TOKEN` independientemente de la cuenta que esté activa globalmente.
3. `mkdir -p {state_dir}` si falta.
4. Leer `{state_dir}/run-state.json` si existe (tratar como `{"runs_completed": 0, "tracked_prs": []}`). `tracked_prs` es la lista propia de este agente de `{number, headRefName, key}` para las relaciones públicas que abrió; se usa solamente para detectar una relación de relaciones públicas que se cerró sin combinar (paso 1.5), ya que `gh pr list --state open` por sí solo no puede verla una vez que ha desaparecido. El tiempo de solicitud de medios se encuentra en un archivo independiente, `{state_dir}/media-requests.json` (Paso 5): GitHub y Jira siguen siendo la fuente fiable para todo lo demás (estado de PR, estado de ticket).
5. `--ticket KEY` presentes -> omiten el autopicking del paso 3, use KEY directamente (sigue ejecutando los pasos 4-7). De lo contrario, seleccione automáticamente en el paso 3.

## Paso 1: Conciliación de ejecuciones anteriores

Ejecute esto cada vez, incluso en una ejecución cerrada o vacía.

1. `gh pr list --repo {github.repo} --label {github.pr_label} --state open --json number,url,isDraft,headRefName,title,reviewDecision`
2. **Revisar comprobación — cada PR abierta, cada ejecución** (`pr.check_reviews_every_run`):
   - `gh pr view <number> --repo {github.repo} --json reviewDecision,reviews,comments`
   - `reviewDecision == "APPROVED"` -> combinar ahora: `gh pr merge <number> --repo {github.repo} --merge`. Compruebe que la combinación realmente aterrizó (`gh pr view <number> --json state,mergedAt` — `state == "MERGED"`) antes de tratarla como realizada; un rechazo de rama protegida o una comprobación necesaria aún pendiente pueden dejar la PR abierta incluso después de llamar a `gh pr merge`, y eso debe registrarse como un error, no notificarse a Jira como combinada (esta es una combinación normal aprobada por humanos, no basada en el tiempo de espera). En la combinación confirmada: comente el ticket Jira vinculado que combinó y elimine el PR de `tracked_prs`.
   - `reviewDecision == "CHANGES_REQUESTED"` -> **no** corrige automáticamente el PR en esta versión. Lea los comentarios de revisión (`gh api repos/{github.repo}/pulls/<number>/comments` para comentarios en línea, además del cuerpo de revisión de nivel superior del campo `reviews`) y ejecute **Aprender de los comentarios** a continuación. Registre el PR en espera de la acción del autor en el resumen de ejecución. Si esta PR ha sido `CHANGES_REQUESTED` durante más de `pr.stale_after_hours` sin ninguna actualización, márquela como obsoleta para la puerta de límite del paso 2: permanece abierta para un ser humano, pero ya no ocupa una ranura de límite.
   - Cualquier otra cosa (sin críticas aún, `REVIEW_REQUIRED` sin revisión enviada) -> nada que hacer aquí.
3. **Aprender de los comentarios.** Para cada comentario de revisión o cuerpo de revisión que se lea como una nota *generalizable* sobre el tono, la estructura o el contenido, no una corrección única específica de esa PR (compare &quot;mencionar siempre la ficha Ignorado para oportunidades con soporte para omitir&quot; frente a &quot;error tipográfico en la línea 12&quot;), anexe una entrada con fecha y vínculo a `references/review-learnings.md`. Omitir comentarios puramente mecánicos (errores tipográficos, enlaces rotos, pelusa): arregle los que están en el propio PR, no necesitan una lección duradera. El formato de entrada exacto está documentado en ese archivo.
4. Para cada **borrador** PR de esa lista, extraiga la clave Jira del nombre de la rama (`{github.branch_prefix}<KEY>-...`).
   - `mcp__Corp-Jira__list_attachments` + `mcp__Corp-Jira__get_jira_comments` en esa clave.
   - Busque: un nuevo archivo adjunto de imagen que coincida con la captura solicitada, O un comentario que contenga una URL de `video.tv.adobe.com`.
   - Si se encuentra: `git fetch`/`checkout` en la rama, agregue la imagen a `help/**/assets/` (si es un archivo adjunto de imagen, descargue a través de `download_attachment`) o rellene el marcador de posición `>[!VIDEO](...)` (si es un comentario de dirección URL de vídeo), valide con `experience-league-markdown`, confirme, inserte, `gh pr ready <number>`, comente en la PR &quot;Medios agregados — listos para revisión&quot;, actualice la entrada `{state_dir}/media-requests.json` a `resolved`.
   - Si no se encuentra: compruebe el tiempo transcurrido desde la solicitud en `{state_dir}/media-requests.json`. Aplique la lógica de escalar/renunciar al paso 5 aquí también (un borrador de PR que se haya dejado abierto en todas las ejecuciones aún necesita que se persigan los medios), incluida la llamada `gh pr ready` de la ruta de abandono, de modo que un borrador abandonado aún se pueda revisar en lugar de quedarse atascado.
5. **Detectar PR cerradas sin combinar.** Comparar la lista de relaciones públicas abiertas de esta ejecución (paso 1) con `tracked_prs` de `run-state.json`. Cualquier PR rastreada que faltara en la lista abierta y que no se confirmara fusionada en el paso 2, se cerró sin fusionarla; antes de soltarla, recupere su estado final (`gh pr view <number> --repo {github.repo} --json reviews,comments`) y ejecute **Aprenda de los comentarios** sobre ella una última vez, para que no se pierda el razonamiento de rechazo de un ser humano. A continuación, suéltelo desde el seguimiento. No se necesita ninguna acción adicional en el ticket en sí: dado que la etiqueta de notificación solo se aplica en el momento de la publicación (Paso 6.10), un ticket cerrado no fusionado ya no tiene etiqueta, y las comprobaciones del Paso 3.2 (sin PR abierta/fusionada) lo hacen elegible de forma natural para ser elegido nuevamente en una ejecución futura.
6. Establezca `tracked_prs` en `run-state.json` en la lista de open-PR actual (`number`, `headRefName` y la clave Jira analizada desde el nombre de la rama), para que el paso 5 de la siguiente ejecución se diferencie con.

## Paso 2: Puerta de límite PR

1. Contar PR abiertas a partir de la salida `gh pr list` del paso 1, excluyendo cualquier PR marcada en el paso 1.2 como obsoleta-`CHANGES_REQUESTED` (abierta más de `pr.stale_after_hours` sin actualización): permanecen abiertas para un ser humano, pero ya no ocupan una ranura de límite.
2. Si count >= `{pr.max_open}` (3): log `"cap reached ({count}/{pr.max_open} open) — skipping new ticket this run"`, vaya al paso 7.
3. De lo contrario, continúe con el paso 3.

## Paso 3: Elija un billete

Omitir por completo si se pasó `--ticket KEY` (usar CLAVE).

```
JQL: "Epic Link" = {jira.epic} AND status = "{jira.open_status}"
     ORDER BY priority DESC, created ASC
```

1. Ejecute la búsqueda (`mcp__Corp-Jira__search_jira_issues`, `minimizeOutput: true`, campos limitados a `key,summary,priority,status,labels`).
2. Resultados de la caminata en orden. Omita cualquier ticket que:
   - ya tiene la etiqueta `{jira.picked_label}`, O
   - ya tiene una rama existente `{github.branch_prefix}<KEY>-*` en el remoto (`git ls-remote --heads origin '{github.branch_prefix}<KEY>-*'`), O
   - ya tiene una PR abierta o combinada (compare con la lista del paso 1 / `gh pr list --state all --search <KEY>`).
3. El primer boleto que pasa los tres cheques es el pick. Si ninguno supera **porque la búsqueda genuinamente devolvió cero tickets elegibles**, registre `"epic backlog fully covered or all in flight"` y vaya al paso 7. Si la búsqueda en sí falla (error de autenticación, tiempo de espera, JQL mal formado), no es este caso: registre el error real en su lugar (consulte Tratamiento de errores más arriba).
4. Aún **no** etiqueta el ticket: la etiqueta de notificación se aplica en el paso 6.10, solo una vez que exista una rama y una PR. Los pasos 4-5 (investigación/borrador/medios) pueden fallar o bloquearse sin dejar ningún rastro en el ticket; las únicas señales en curso antes del paso 6 son las comprobaciones de existencia de ramas/existencia de PR anteriores, lo que es suficiente dado que esto se ejecuta desde una sola máquina sin concurrencia real para protegerse.

## Etapa 4 — Investigación + Borrador

La investigación es lo primero y es **multifuente**; nunca se extrae de una sola entrada (el Jira
ticket solo, o solo leer documentos de hermanos). Todas las fuentes siguientes confirman o
corrige las otras; las contradicciones se resuelven confiando en el código fuente > Documentos de Wiki/PR >
Discusión de Slack > la propia inferencia del redactor del documento, en ese orden, y recibe marcas en línea
como `<!-- CONFIRM -->` cuando no se pueden resolver.

&#x200B;0. **Lecciones acumuladas de revisión.** Lea `references/review-learnings.md` primero. Aplique todo lo que sea relevante para el tema de esta entrada antes de redactar el borrador: así es como los comentarios de las revisiones de PR anteriores mejoran los borradores futuros en lugar de repetir la misma corrección.

### Investigue (haga todo lo que corresponda; no pase directamente a la redacción)

1. **Código Source (la verdad básica de cómo funciona realmente).** Busque en el repositorio de la interfaz de usuario principal (`research.code_repos` en config.yml) el adaptador/controlador (`*OpportunityAdapter.tsx`, `*SuggestionAdapter.tsx`) de la característica, su enlace de datos (`use*Data.ts`) y sus cadenas de título/descripción `.l10n.ts`/`.I10n.ts`. Esta es la autoridad para los nombres de campo, la forma de los datos, la categoría y la copia exacta del producto; prefiérela sobre cualquier otra cosa cuando las fuentes no estén de acuerdo.
2. **Wiki (intención de diseño, especificaciones, decisiones).** `mcp__Adobe-Wiki__search_wiki_content` con el nombre de la función/oportunidad y la clave épica/ticket. Leer las páginas coincidentes (`get_wiki_content`) para: por qué existe la función, la terminología que utiliza el equipo del producto, cualquier caso documentado de flujo de experiencia de usuario o Edge y cualquier captura de pantalla incrustada que establezca el aspecto de la interfaz de usuario real (informa la especificación de captura de medios en el paso 5, no reemplaza una captura de pantalla nueva real a menos que la página sea actual).
3. **Slack (cómo habla realmente el equipo, preguntas abiertas, cambios recientes).** `mcp__Slack__slack_search_messages` con el nombre de característica/oportunidad y la clave de vale, sin restricciones de canal a menos que `research.slack_channels` lo reduzca en config.yml. Busque: mensajes de anuncio (a menudo tienen el marco limpio de cara al cliente), hilos de discusión de diseño y cualquier cosa que indique la función modificada recientemente de una manera que los documentos del mismo nivel o los comentarios de código aún no se reflejen.
4. **Historial de PR de GitHub (motivos de implementación, capturas de pantalla, discusión de revisión).** `gh search prs --repo <repo> "<feature name>"` o `gh pr list --repo <repo> --search "<ticket key OR feature name>" --state all` en `research.code_repos`. Lea descripciones de PR combinadas para obtener información racional, documentos de diseño vinculados y capturas de pantalla que aclaren el comportamiento que el código por sí solo no explica (por ejemplo, por qué se bloquea un tipo de corrección, cómo se ve un caso límite en la interfaz de usuario).
5. **Análogos de tono.** Basándose en el resumen del ticket, encuentre 2-3 páginas existentes más cercanas:
   - &quot;... tickets de procedimientos de oportunidad -> leer 2 archivos del mismo nivel en `help/documentation/opportunities/` (la ubicación de procedimientos real por oportunidad — `help/opportunity-types/*.md` son las páginas de aterrizaje de categoría con cuadrículas de tarjetas que se vinculan a estas, no el propio contenido de procedimientos).
   - Configuración/flujo de trabajo/vales de conexión -> leer 1-2 archivos del mismo nivel en `help/documentation/` (compruebe `setup/`, `opportunities/`, `settings.md`, `basics.md` para ver cuál es la coincidencia más cercana).
     Estructura del encabezado espejo, uso del cuadro de notas, longitud de la oración, nivel de detalle técnico.
6. **Reglas de formato.** Vuelva a leer la referencia rápida de la aptitud de `experience-league-markdown` antes de escribir. Cada encabezado, nota, imagen o vínculo debe coincidir exactamente con su sintaxis.

### Borrador

&#x200B;7. **Decisión de archivo de destino.** Prefiera ampliar la sección relevante de una página existente en lugar de crear un nuevo archivo, a menos que el ticket coincida con la granularidad de las páginas independientes existentes (por ejemplo, cada oportunidad obtiene su propio archivo en `help/documentation/opportunities/`; una nueva sigue la estructura exacta de un elemento secundario existente). Al ampliar una página existente, toque solo la sección de este ticket: no edite secciones no relacionadas aunque parezcan obsoletas. Si es una nueva página independiente, agregue también su tarjeta a la página de aterrizaje `help/opportunity-types/*.md` correspondiente (lista de comentarios de origen + bloque de HTML generado, que coincide con el patrón exacto de las tarjetas existentes) y regístrela en `help/main-toc/TOC.md`.
&#x200B;8. **Borrador v1.** Escriba el contenido ahora (en memoria/en el principio, aún no en el archivo de repositorio; esto sucede en el paso 6 después de la decisión sobre los medios, por lo que un documento pendiente de los medios y un documento resuelto en los medios pasan por la misma ruta de escritura). Sintetice todos los pasos del 1 al 6: no se limite a reiterar la descripción del ticket de Jira.
&#x200B;9. **Iterar.** Vuelva a leer el borrador de la versión 1 en contra de todos los hallazgos de investigación de los pasos 1-4: ¿el borrador pasó por alto algo que apareció en Slack o en Wiki? ¿Contradice lo que realmente hace el código fuente? ¿Coincide con el tono del hermano lo más que podría? Revise antes de continuar: se trata de un segundo pase, no de una formalidad. Cualquier cosa que siga genuinamente sin confirmar después de este pase (no encontrada en ninguna de las cuatro fuentes) obtiene un comentario de `<!-- CONFIRM -->` en línea en lugar de una suposición.
&#x200B;10. **Decisión de medios.** Decida `mediaNeeded: true|false`.
    - `true` si la característica es un flujo de trabajo de interfaz de usuario de varios pasos en el que una descripción textual por sí sola sería materialmente más difícil de seguir (coincide con el de `guidelines.md` &quot;usado con prudencia... cuando una descripción textual no es suficiente&quot;).
    - Si `true` produce: `mediaType` (`screenshot` o `video`), `captureSteps` (pasos exactos para reproducir el estado que se va a capturar), `urls` (direcciones URL de aplicaciones orientadas al cliente o direcciones URL de páginas internas necesarias para alcanzar ese estado), extraiga direcciones URL reales de la descripción/los comentarios del ticket de Jira, la wiki o las convenciones de `open-aso-devmode-url` si se hace referencia en ellas; nunca cree una dirección URL.
    - Si `false`, omita el paso 5 para este ticket.

## Paso 5: Puerta de medios

Solo se ejecuta cuando el paso 4 estableció `mediaNeeded: true`. Todas las marcas de tiempo en
`{state_dir}/media-requests.json` son UTC ISO-8601 (`date -u +%Y-%m-%dT%H:%M:%SZ`) —
escriba y compare siempre en este formato para que la matemática de tiempo transcurrido que aparece a continuación sea inequívoca
a través de las carreras.

1. Busque en `{state_dir}/media-requests.json` una entrada existente para esta clave de vale. Si no hay ninguna, se trata de una solicitud nueva.
2. **Nueva solicitud:**
   - `mcp__Slack__slack_lookup_user` el `media.contacts_in_order[0].email` (sandsinh) para obtener el ID de usuario de Slack.
   - `mcp__Slack__slack_send_dm` con un mensaje que contiene: la clave + vínculo del ticket Jira, exactamente qué capturar (`captureSteps`), las direcciones URL que se usarán y adónde debe ir la respuesta (&quot;responder en el ticket Jira — adjuntar la captura de pantalla directamente o, para vídeo, cargar a través del formulario de vídeo habitual de Experience League y pegar el vínculo `video.tv.adobe.com` resultante como comentario&quot;).
   - Escriba `{state_dir}/media-requests.json[KEY] = {requestedTo: "sandsinh", requestedAt: <UTC ISO-8601 now>, escalated: false}`.
3. **Solicitud existente:** ambos umbrales a continuación se miden desde el original `requestedAt` — la escalación no restablece el reloj:
   - `now - requestedAt` &lt; `media.escalate_after_hours` -> no haga nada esta ejecución, continúe con la publicación con los medios aún pendientes (borrador de PR).
   - `now - requestedAt` >= `media.escalate_after_hours` y aún no se ha escalado -> DM `media.contacts_in_order[1]` (kanishka), las notas de mensajes sandsinh ya se preguntó hace N horas sin respuesta. Actualizar entrada: `escalated: true, escalatedAt: <UTC ISO-8601 now>`.
   - `now - requestedAt` >= `media.give_up_after_hours` (independientemente del estado de escalación) -> establezca `mediaNeeded: false` con fines de publicación, inserte una nota en línea en el borrador: `>[!TIP]\n>\n>A screenshot for this step is being added in a follow-up update.` Si ya existe una PR para este ticket y sigue siendo un borrador (alcanzado aquí a través del paso 1.4, no una nueva publicación del paso 6), `git fetch`/cierre la rama, aplique la nota, confirme, inserte y llame a `gh pr ready <number>` — un borrador dado debe seguir siendo revisable, no permanecer atascado indefinidamente. Marcar entrada `gaveUp: true`.

## Paso 6: Publicación

Omita si el ticket se omitió por completo en el paso 3 (no hay nada para publicar).

1. `git fetch origin` y `git checkout -B {github.branch_prefix}<KEY>-<short-slug> origin/main` — `-B` (no `-b`), por lo que se restablece una rama local sobrante de una ejecución anterior bloqueada en lugar de bloquear la desprotección; la bifurcación directa desde `origin/main` también descarta cualquier estado local sucio de un bloqueo anterior en lugar de generar errores en él.
2. Escriba el borrador del paso 4 en el archivo de destino decidido en el paso 4.3. Vuelva a comprobarlo con la lista de comprobación &quot;Antes de confirmar los cambios de Markdown&quot; de `experience-league-markdown` línea por línea.
3. Si se ha configurado un filtro de markdown (`markdownlint_custom.json` en la raíz del repositorio) y `markdownlint-cli`/`npx markdownlint` está disponible, ejecútelo con los archivos modificados y corrija las infracciones antes de confirmarlo.
4. Transferir: `docs(aso): <ticket summary, lowercase, no trailing period>\n\nSITES-XXXXX`.
5. `git push -u origin <branch>`.
6. Selección de revisor: `gh pr list --repo {github.repo} --label {github.pr_label} --state open --json reviewRequests`: cuente cuántos enumeran actualmente cada uno de los dos revisores configurados; asigne el que tenga menos (tiempo -> `sandsinh_adobe`).
7. Cuerpo de PR:

   ```
   ## Summary
   [1-2 sentence description of the feature now documented]
   
   ## Source
   Closes documentation gap tracked in [SITES-XXXXX](https://jira.corp.adobe.com/browse/SITES-XXXXX)
   
   ## Media
   [either "No media needed for this update." OR "Screenshot/video requested from {contact} on {date} — PR opened as draft until resolved." OR "Media follow-up pending — shipped without it; see inline note."]
   
   > 🤖 Drafted by aso-doc-agent
   ```

8. `gh pr create --repo {github.repo} --title "<ticket summary>" --body "<above>" --label {github.pr_label} --reviewer <chosen-github-handle> --draft` si el medio sigue pendiente; de lo contrario, omita `--draft`.
9. `gh pr edit <number> --add-label {github.pr_label}` si el indicador de la etiqueta no se tomó (cinturón y tirantes, coincide con el patrón utilizado en otras partes de las herramientas de esta organización).
10. Jira: `add_jira_comment` vincula la dirección URL PR y ahora, por primera vez en esta ejecución, agrega `{jira.picked_label}` (`update_jira_issue`, combina con etiquetas existentes). Esta es la afirmación, aplicada deliberadamente solo una vez que una sucursal y PR existen: un bloqueo en cualquier lugar en los pasos 3-5 deja el ticket completamente sin etiqueta y con seguridad reciclable, en lugar de atascado permanentemente. No cambiar el estado del ticket: déjelo en manos del propio equipo de docs; `{jira.picked_label}` es la única señal de estado que escribe este agente.

## Paso 7: Ejecución del resumen

1. Actualización `{state_dir}/run-state.json`: `runs_completed += 1`, marca de tiempo, ticket seleccionado (o &quot;ninguno&quot; + motivo), PR abierto/actualizado (o &quot;ninguno&quot; + motivo), estado de límite.
2. Imprima un breve resumen legible en lenguaje natural (ticket, acción realizada, vínculo de PR, estado de los medios).
