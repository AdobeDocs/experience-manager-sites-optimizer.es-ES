---
source-git-commit: ed1960cc0364dc4169a454a4860b7463890e3b74
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 0%

---
# Agente de documentos ASO: uso

Qué es esto, cómo funciona y qué hacer cuando te necesita.

## Qué hace

Cada día, este agente elige la característica de ASO indocumentada de mayor prioridad de
Registro de pendientes de [SITES-49539](https://jira.corp.adobe.com/browse/SITES-49539) (39 tickets, p. ej.
&quot;Canonical Opportunity how-to&quot;, &quot;Slack notifications&quot;), escribe un fragmento de documentación
para él en el estilo de la casa de este repositorio, y abre una PR, asignando cualquiera de los dos
los revisores configurados (`sandsinh_adobe` / `kanishka_adobe`) tienen actualmente menos elementos abiertos
revisar solicitudes de este agente. Si la función necesita una captura de pantalla o un vídeo, solicita
uno sobre Slack antes de finalizar el PR.

Cada ejecución también comprueba el estado de revisión en cada PR abierta: se fusionan las PR aprobadas
inmediatamente, y los comentarios solicitados por cambios se leen y, cuando es un elemento generalizable
lección (no un error tipográfico puntual), grabada para que los borradores futuros no repitan el mismo error.

Una ejecución = una función = como máximo una PR. Nunca toca más de un boleto por carrera,
y nunca abre más de 3 PR a la vez (espera a que las existentes se fusionen/cierren primero).

## Donde todo vive

| Qué | Ruta |
|---|---|
| Cómo decide qué hacer | `.claude/skills/aso-doc-agent/SKILL.md` |
| El paso a paso exacto | `.claude/skills/aso-doc-agent/references/pipeline.md` |
| Configuración específica del equipo (edite esta opción para cambiar los revisores, el límite, el tiempo de escalación) | `.claude/skills/aso-doc-agent/config.yml` |
| Lecciones aprendidas de los comentarios sobre las revisiones de PR (rastreadas en Git, leídas antes de cada borrador) | `.claude/skills/aso-doc-agent/references/review-learnings.md` |
| Estado de ejecución local (ignorado; seguro de eliminar, se volverá a generar) | `.claude/skills/aso-doc-agent/state/` |
| Programa de instalación diario | `.claude/scripts/aso-doc-agent-setup.sh` |
| Lista de permitidos de permisos para ejecuciones sin encabezado | `.claude/settings.local.json` (ignorado, local del equipo) |

## Ejecutándolo

- **Manualmente, en una sesión normal:** `/aso-doc-agent` (o `/aso-doc-agent --ticket SITES-XXXXX`)
- **Sin encabezado, excepcional:** `claude -p "/aso-doc-agent"` desde la raíz del repositorio
- **Diario, desatendido:** ya instalado a través de `launchctl` (ver abajo) — se ejecuta a las 07:53 hora local todos los días, no se necesita ninguna acción

### Instalación/cambio del horario diario

```bash
bash .claude/scripts/aso-doc-agent-setup.sh
```

Instala un trabajo de `launchd` (`~/Library/LaunchAgents/com.sandsinh.aso-doc-agent.plist`) que
ejecuta `claude -p "/aso-doc-agent"` desde este repositorio diariamente. Vuelva a ejecutar el script siempre que lo desee
edite la programación que contiene (predeterminado: 07:53 local). Esto solo funciona mientras la máquina esté
activado y activado en ese momento: iniciado no ejecuta trabajos perdidos de forma retroactiva, sino que se ejecuta
la siguiente hora programada normalmente.

```bash
launchctl list | grep com.sandsinh.aso-doc-agent   # confirm it's loaded
launchctl start com.sandsinh.aso-doc-agent         # trigger a run right now, don't wait for 07:53
launchctl unload ~/Library/LaunchAgents/com.sandsinh.aso-doc-agent.plist  # stop it
```

Los registros de cada ejecución programada aterrizan en `.claude/skills/aso-doc-agent/state/launchd.out.log`
y `launchd.err.log`.

## Lo que se le pedirá que haga

- **Un Slack DM del agente** (enviado como usted, a usted — sandsinh primero, kanishka en
(escalación) solicitando una captura de pantalla o un vídeo, con los pasos de captura exactos y las direcciones URL a
use. **Responder en el ticket Jira vinculado, no en Slack**: adjunte la captura de pantalla directamente,
o, para vídeo, cárguelo a través del formulario de vídeo habitual de Experience League
(`experience-league-video-upload` aptitud) y pegue el resultante `video.tv.adobe.com`
Enlace como un comentario de Jira. La siguiente ejecución lo recoge automáticamente.
- Si nadie responde en **5 días**, la solicitud se escalará de sandsinh a kanishka
automáticamente. Después de **10 días** sin respuesta de ninguno de los dos, el agente envía el documento
sin medios y añade una nota en línea. No hay una combinación automática basada en el tiempo de espera: la PR
todavía espera una revisión humana real, por mucho que tarde.
- **Un PR para revisar** — asignado al que tenga menos PR abiertas por el agente
actualmente en espera de revisión. Los borradores de PR significan que los medios siguen pendientes; cambian a
listo para revisión automáticamente una vez que se muestre el recurso. Aprobar y combinar el agente
Pasarlo en la siguiente ejecución: no es necesario realizar ningún paso de combinación independiente.
- **Si solicita cambios**, el agente leerá sus comentarios en la siguiente ejecución. Generalizable
los comentarios (no una corrección de error tipográfico o de vínculo) se escriben en `references/review-learnings.md`, por lo que la variable
La misma corrección no necesita repetirse en una futura PR.

## Ajuste del comportamiento

Editar `.claude/skills/aso-doc-agent/config.yml` (con seguimiento en Git): los cambios afectan a cada
ejecución futura, en esta máquina o en otra persona que clone el repositorio):

- `pr.max_open`: cuántos PR abiertos antes de que el agente deje de seleccionar nuevos tickets (predeterminado 3).
- `pr.stale_after_hours`: cuánto tiempo puede permanecer una RP de `CHANGES_REQUESTED` antes de que deje de contar hacia `pr.max_open` (valor predeterminado 336 = 14 días); permanece abierta, esto solo desbloquea nuevas selecciones
- `github.reviewers`: a quién se asigna y en qué saldo
- `media.contacts_in_order` / `escalate_after_hours` (predeterminado 120 = 5 días) / `give_up_after_hours` (predeterminado 240 = 10 días) — quién se ha preguntado, en qué orden y con qué paciencia; ambos se miden desde la solicitud original, de modo que al escalar no se retrasa la fecha de abandono
- `pr.check_reviews_every_run` — desactivar el paso de revisión y comprobación (no recomendado; así es como ocurren las combinaciones y las aprendizajes)

## Si se detiene en un mensaje de permisos

Las ejecuciones sin encabezado (`claude -p`, iniciadas) no tienen ningún terminal al que llamar: una llamada de herramienta no incluida en la lista
simplemente fallará en lugar de colgar. Si el registro de una ejecución muestra una denegación de permisos para un comando
Si la canalización necesita legítimamente, agréguela a la lista `permissions.allow` en
`.claude/settings.local.json` (no rastreado en Git — local del equipo; todos los desarrolladores en ejecución)
este agente necesita su propia copia con su propia lista de permitidos de ámbito).

## Si deja de progresar por completo

Marque, en orden:
1. `gh pr list --repo Adobe-Enterprise-Docs/experience-manager-sites-optimizer.en --label aso-doc-agent --state open`: si muestra 3, está esperando críticas, no atascado.
2. Jira: ¿queda un ticket `New` apto en SITES-49539 que aún no sea `aso-doc-agent-picked`? La etiqueta solo se aplica una vez que existe una rama+PR (pipeline.md Paso 6.10), por lo que una ejecución bloqueada no debe dejar un ticket etiquetado pero no publicado — si todavía encuentra uno (por ejemplo, una etiqueta añadida a mano), elimínelo manualmente para que el ticket sea elegible de nuevo.
3. `.claude/skills/aso-doc-agent/state/launchd.err.log` para el error de la ejecución más reciente.
4. Si el resumen de una ejecución muestra &quot;registro épico de pendientes totalmente cubierto&quot; o &quot;nada que hacer aquí&quot; pero sabe que debe haber trabajo apto, trátelo como sospechoso — esos mensajes están reservados para resultados genuinamente vacíos. Un error real de Jira/GitHub/Slack se registra por separado y debería aparecer como su propia línea en `launchd.err.log` en lugar de ocultarse detrás de uno de esos mensajes.
