---
description: Convierta las notas de la versión de ASO sprint internas al formato Experience League orientado al cliente y añádalas a la página de notas de la versión.
source-git-commit: 5f400c37283d1a3d8285b4d2ac5246761a7275e6
workflow-type: tm+mt
source-wordcount: '1029'
ht-degree: 0%

---


# Conversor de notas de versión

Convierte las notas de la versión de sprint interna (del canal `#aem-sites-optimizer-announcements` de Slack o de la salida del cursor `.cursor/commands/release-notes`) en una entrada orientada al cliente y la anexa a `help/documentation/release-notes.md`.

## Uso

Invoque esta aptitud y pegue el contenido de las notas de la versión interna cuando se le solicite. La aptitud:

1. Aplique las directrices siguientes para reglas de filtrado y tonificación.
2. Analice las notas de la versión interna (secciones clasificadas por emojis: ✨ funciones, 🚀 mejoras, 🤖 AI-First, 🔧 correcciones, 🏢 BackOffice).
3. Filtrar todas las categorías excluidas según las directrices (herramientas de IA, BackOffice, filtro de localización, pruebas E2E, elementos solo internos de Sites).
4. Vuelva a escribir los elementos restantes en tono orientado al cliente utilizando los ejemplos de tono que aparecen a continuación como referencia.
5. Agrupar elementos relacionados por área de capacidad (no por equipo o repositorio).
6. Aplique el formato como una nueva entrada de versión según la plantilla de estructura de página que aparece a continuación.
7. Anteponer la nueva entrada a `help/documentation/release-notes.md` (encima de la entrada más reciente anterior, debajo del párrafo de introducción de la página).
8. Imprimir una tabla de resumen que muestre: los elementos guardados, los elementos reescritos y los elementos borrados (con el motivo de cada elemento borrado).

## Directrices

### Principios básicos

1. **Primero el beneficio para el cliente.** Cada entrada debe responder &quot;¿qué puedo hacer ahora que no podía antes, o hacerlo mejor?&quot; — no &quot;¿qué enviamos?&quot; Posible cliente con el valor, no con la implementación.

2. **Tono de liderazgo.** Escriba para un encargado de la toma de decisiones: resultados y capacidades, no mecánica técnica. Un vicepresidente de experiencia digital debería comprender inmediatamente por qué una actualización es importante.

3. **No hay jerga interna.** Reemplazar todos los métodos abreviados internos del equipo:
   - &quot;PLG&quot; → &quot;usuarios de prueba&quot; o &quot;clientes nuevos&quot;
   - La → &quot;BackOffice&quot; se omite por completo (cambio solo de infraestructura)
   - &quot;MSM&quot; → &quot;Administrador de varios sitios de AEM&quot;
   - &quot;SHM&quot; → &quot;Monitor de estado del sitio&quot;
   - &quot;OrcaFix&quot;, &quot;Comandos del cursor&quot;, &quot;AGENTS.md&quot; → omitir por completo
   - &quot;EDS&quot; → &quot;Edge Delivery Services&quot;

4. **Entradas cortas.** Una frase de *qué*, una frase de *por qué importa*. Si ambos encajan en una frase, hágalo.

5. **Ámbito preciso.** Incluya solo los cambios que verá un cliente en la interfaz de usuario del producto o la experiencia en sus flujos de trabajo. Se excluyen los cambios en la infraestructura, las herramientas y la experiencia del desarrollador.

6. **Marcar funciones de acceso anticipado.** Si una característica se envía detrás de una marca de características que está desactivada de forma predeterminada (inclusión por organización o sitio, por ejemplo, a través de LaunchDarkly `FeatureGate`/`isEnabledByDefault={false}`), anexe `(Early Access)` al nombre en negrita de la característica, reflejando la convención de `(General Availability)` existente que se usa para las características graduadas. En caso de duda, compruebe si la función está activada de forma predeterminada para todos los clientes; de lo contrario, es Acceso anticipado. Verificar con el indicador de funcionalidad predeterminado en el código: no adivinar.

### Plantilla de estructura de página

Cada entrada de versión sigue esta estructura:

```markdown
## [Month Start]–[Day End], [Year]

### New Features

- **[Feature Name]** — [One-sentence benefit statement. One sentence of business context if needed.] (append `(Early Access)` or `(General Availability)` to the feature name when the feature's availability status is notable)

### Enhancements

- **[Enhancement Name]** — [One-sentence improvement statement.]

### Bug Fixes

- [Short description of what was fixed and why it matters to users.]
```

**Reglas:**
- Formato de intervalo de fechas: `May 11–22, 2026` (en guión, mes abreviado, año de cuatro dígitos).
- Orden cronológico inverso: versión más reciente en la parte superior de la página.
- Incluir solo las secciones que tienen contenido. Omita &quot;Mejoras&quot; o &quot;Correcciones de errores&quot; si está vacío.
- Las entradas de correcciones de errores no utilizan nombres de funciones en negrita; son viñetas sin formato.
- Incluya solo correcciones de errores si hay 3 o más correcciones visibles para el usuario que vale la pena mencionar.

### Qué incluir y qué excluir

**Incluir:**

| Categoría | Ejemplos |
|---|---|
| Nuevos tipos de oportunidades | Discordancia de intención de anuncio, sin CTA por encima del pliegue |
| Nuevas vistas o flujos de trabajo | Pestaña Implementado, exportación de CSV, vinculación Jira |
| Mejoras de prueba/incorporación | Flujo de configuración guiado, estado integrado en el sitio |
| Mejoras de configuración | URL de destino de auditoría, configuración de tipo de envío |
| Correcciones de UX significativas | Recuentos incorrectos, navegación dañada, problemas de visualización que afectan a las decisiones |
| Nuevos datos e integraciones | Datos Ahrefs en la búsqueda orgánica, árbol de dependencias en Seguridad |
| Implementar funciones de autor | Nuevos tipos de oportunidades que admiten la implementación directa |

**Excluir:**

| Categoría | ¿Por qué? |
|---|---|
| Herramientas de IA (OrcaFix, comandos del cursor, AGENTS.md, reglas de Claude Code) | Herramientas internas para desarrolladores, no visibles para los clientes |
| Enlaces de filtrado/preconfirmación de localización | Proceso de ingeniería, no función del producto |
| BackOffice / cambios en la infraestructura | No es visible en la interfaz de usuario a menos que cambien el comportamiento del usuario final |
| Actualizaciones de la versión de React Spectrum | Dependencia interna, no visible para el usuario |
| Mejoras en las pruebas E2E | Calidad de ingeniería, no una función del producto |
| Automatización de canalización de versiones | Proceso interno |
| Funciones solo internas de Sites | No disponible para los clientes |

### Ejemplos de tonos

| Fraseado interno | Fraseado orientado al cliente |
|---|---|
| &quot;Introdujo el estado RECHAZADO para el flujo de trabajo de validación manual&quot; | &quot;Ahora puede marcar las sugerencias como rechazadas para indicar que no se aplican a su sitio, manteniendo la lista de oportunidades centrada en los elementos procesables&quot;. |
| &quot;Vista implementada para oportunidades de Canonical y Hreflang (agrupadas por fecha)&quot; | &quot;Los cambios en las oportunidades de Canonical y Hreflang ahora se agrupan por fecha de implementación en una pestaña Implementado, lo que le ofrece un historial claro de lo que se corrigió y cuándo&quot;. |
| &quot;Alt Text Autofix V2 — &#39;Comprobar la fijabilidad&#39; evaluación previa al vuelo&quot; | &quot;Antes de implementar una corrección de texto alternativo, puede ejecutar una comprobación previa al vuelo para verificar que la corrección se pueda aplicar correctamente al contenido.&quot; |
| &quot;Optimización del almacenamiento del 96 % para métricas de SHM&quot; | omitir: sólo infraestructura |
| &quot;AGENTS.md con funciones de agente formales y protecciones de seguridad&quot; | omitir: herramientas de IA internas |
| &quot;Optimizaciones de rendimiento de pruebas E2E (~6min → ~5min)&quot; | omitir: proceso de ingeniería |

### Reglas de agrupación

- **Agrupar por área de capacidad**, no por equipo o repositorio. Por ejemplo, todas las mejoras de texto alternativo (funciones, mejoras y correcciones) pertenecen a la misma área, no las distribuya entre secciones.
- **Consolide las correcciones** estrechamente relacionadas en una sola viñeta en lugar de enumerarlas por separado (por ejemplo, &quot;Varias mejoras en la visualización y el diseño en las oportunidades de tráfico de pago, accesibilidad y seguridad&quot;).
- **Umbral para la sección de correcciones de errores**: incluya esta sección solo cuando haya 3 o más correcciones visibles para el usuario que merezcan la pena llamar. Deben omitirse las correcciones triviales o puramente cosméticas por debajo de este umbral.

## Etapas

1. Aplicar las directrices de este archivo: internalice todos los principios, incluya o excluya reglas, ejemplos de tonos y reglas de agrupación.
2. Pregunte al usuario el intervalo de fechas cubierto (por ejemplo, &quot;11-22 de mayo de 2026&quot;) si no se ha proporcionado previamente.
3. Pida al usuario que pegue el contenido de las notas de la versión interna (o acepte una ruta de archivo).
4. Procese el contenido:
   - **Analizar** cada sección (✨/🚀/🤖/🔧/🏢) y sus puntos de viñeta.
   - **Filtro** por la tabla de exclusión anterior. Marcar cada elemento colocado con un motivo.
   - **Reescribir** mantuvo los elementos en el tono del cliente: primero para los beneficios, sin jerga, entradas cortas.
   - **Agrupar** por área de capacidad donde hay varios elementos relacionados.
   - **Comprobación de umbral**: solo incluya una sección &quot;Correcciones de errores&quot; si hay más de 3 correcciones visibles para el usuario.
5. Dé formato a la nueva entrada con la plantilla de estructura de página de arriba.
6. Leer el contenido actual de `help/documentation/release-notes.md`.
7. Inserte la nueva entrada inmediatamente después del párrafo de introducción a la página (antes del último encabezado de fecha `##` anterior).
8. Escriba el archivo actualizado.
9. Imprimir la tabla de resumen.

## Formato de entrada

La aptitud acepta las notas de la versión interna en el formato de equipo estándar:

```
*ASO UI Release Notes — [Date Range]*
Collaborators: [teams]

✨ *Features*
• [Feature description]

🚀 *Enhancements*
• [Enhancement description]

🤖 *AI-First Development*
• [AI tooling items — will be dropped]

🔧 *Fixes & UX Improvements*
• [Fix description]

🏢 *BackOffice*
• [BackOffice items — will be dropped]
```

## Salida

La aptitud genera:

1. La entrada con formato de cliente (para revisarla antes de escribirla).
2. Un mensaje de confirmación antes de modificar `release-notes.md`.
3. Después de escribir: una tabla resumen de elementos guardados, reescritos o eliminados.
