---
title: Resultados de la auditoría en Preflight
description: Obtenga información sobre cómo interpretar los resultados de la auditoría de comprobaciones, el medidor de disponibilidad y las categorías de auditoría, y vaya a las oportunidades en la vista previa.
source-git-commit: 56a56991a262d9f19a228dc9ca6ec440acdc2999
workflow-type: tm+mt
source-wordcount: '1009'
ht-degree: 3%

---


# Resultados de la auditoría en Preflight

Cuando se completan las auditorías, Comprobación preliminar muestra los resultados en el panel de preparación. El panel muestra un medidor de disponibilidad general y las oportunidades que encontró, agrupadas por categoría de auditoría. Dentro de cada categoría, las auditorías individuales identifican elementos específicos que se deben revisar o corregir.

## Barra de herramientas

La barra de herramientas situada en la parte superior del panel de preparación proporciona acciones para la ejecución actual:

* **Volver a analizar**: inicia una nueva ejecución de auditoría en la página actual. Volver a analizar siempre descarta los resultados mostrados y ejecuta cada auditoría de nuevo, por lo que debe utilizarlo siempre que desee resultados nuevos; por ejemplo, después de editar la página. Volver a analizar se encuentra en **Más acciones** (**...**) menú.
* **Exportar** - Descargue la ejecución actual como un archivo **CSV** (compatible con la hoja de cálculo) o **PDF** (un documento con formato). Según el entorno, seleccione **Exportar** en la barra de herramientas o en **Más acciones** (**...**) menú.

Al exportar, también puede elegir qué incluir:

* **Incluir tabla de metadatos**: agregue una tabla de detalles de ejecución, como el host, la ruta de contenido y los detalles de generación.
* **Incluir auditorías aprobadas**: incluya las auditorías que se aprobaron sin oportunidades, no solo las oportunidades que se encontraron.

>[!NOTE]
>
>Las exportaciones de PDF siempre se generan en inglés, independientemente del idioma de la interfaz. Las exportaciones de CSV siguen el idioma de la interfaz lo más fielmente posible.

## Medidor de preparación

En la parte superior del tablero, el indicador de disponibilidad refleja los resultados generales de la auditoría. Muestra una puntuación de preparación como porcentaje, basada en la proporción de auditorías que finalizaron sin oportunidades, junto con el número total de oportunidades encontradas en todas las auditorías. El medidor de disponibilidad le ayuda a medir el estado general de la página de un vistazo.

![El medidor de preparación y las categorías de auditoría en el tablero de comprobaciones](./assets/overview/hero.png){align="center"}

Cuando está viendo una ejecución que se recargó desde una sesión anterior, el encabezado muestra hace cuánto tiempo se realizó, por ejemplo, *ayer*. Para obtener más información, vea [Continuar una sesión anterior](./audits.md#continue-a-previous-session).

Mientras las auditorías siguen ejecutándose, el indicador de disponibilidad muestra una barra de progreso con un estado corto debajo que muestra el paso actual. Cuando se completan las auditorías, el medidor muestra el porcentaje de disponibilidad final y el recuento de oportunidades.

## Categorías de auditoría

Los grupos de comprobaciones relacionaron auditorías en categorías como **SEO** y **Accesibilidad**. Cada categoría aparece como una tarjeta que muestra el número de oportunidades encontradas o indica que todas sus auditorías pasaron sin oportunidades.

Expanda una categoría para ver sus auditorías individuales. Cada auditoría muestra si se aprobaron o encontraron oportunidades, una breve descripción y un recuento de las oportunidades encontradas. Seleccione una auditoría que haya encontrado oportunidades para abrir su página de detalles.

Para obtener la lista completa de categorías de auditoría y las auditorías de cada una, vea [Categorías de auditoría de comprobación preliminar](./overview.md#preflight-audit-categories).

## Detalles de la oportunidad

La página de detalles muestra las oportunidades que encontró la auditoría seleccionada. Cuando el mismo problema se produce en más de un lugar, cada ocurrencia se denomina instancia. Utilice el navegador (**Instancia anterior** y **Instancia siguiente**) para avanzar por ellos; muestra su posición, por ejemplo *1 de 5 instancias encontradas*. Para volver al panel de preparación, seleccione la flecha hacia atrás junto al título de la auditoría; el panel se vuelve a abrir con la categoría de la auditoría expandida.

![Página de detalles de una auditoría que muestra una oportunidad y su sugerencia](./assets/audit-results/audit-detail.png){align="center"}

Cada oportunidad incluye:

* Un distintivo de gravedad o impacto que indica la importancia de la oportunidad.
* Detalles sobre la oportunidad, como una descripción del problema, una recomendación y, para accesibilidad, la regla WCAG y el nivel de conformidad relacionados.
* Una sección **Element** que identifica el elemento afectado en la página, con un botón **Resaltar en la página**. Cuando el elemento tiene texto legible, la sección se titula **Elemento: Texto** y muestra ese texto; de lo contrario, se titula **Elemento: Selector** y muestra el selector CSS del elemento. Para las oportunidades de **Links** y **Canonical**, una sección de **URL actual** también muestra la URL involucrada, que puede abrir en una nueva pestaña si es posible.
* Una sección **Sugerencia** con una corrección recomendada. Cuando AI genera la sugerencia, se marca como una sugerencia generada por IA y puede incluir una breve justificación que explique la corrección sugerida.

## Resaltar en la página

Una vez completadas las auditorías, puede localizar y comprender rápidamente una oportunidad resaltándola directamente en la página.

La comprobación preliminar resalta el elemento afectado en el contexto y conecta el resultado del panel con la ubicación exacta del contenido. Esto facilita la revisión y la resolución de oportunidades sin buscar manualmente en la página.

1. Abra el panel Comprobaciones en el contexto de la página que desea auditar y seleccione **Analizar página** para ejecutar las auditorías.
1. Seleccione una auditoría en el panel de preparación y, a continuación, seleccione una oportunidad para revisarla.
1. Seleccione **Resaltar en la página**. La vista previa se desplaza automáticamente al área relevante y resalta el elemento correspondiente, para que pueda identificar y optimizar fácilmente la oportunidad en contexto.

Resaltar no es posible para cada oportunidad; por ejemplo, cuando una oportunidad no está vinculada a un elemento específico, el elemento está oculto o ya no está en la página. En estos casos, el botón **Resaltar en la página** aparece atenuado; pase el ratón sobre él para ver el motivo.

En el editor universal, aún no se admite el resaltado para las oportunidades de **Accesibilidad**; el botón **Resaltar en la página** aparece atenuado y puede pasar el ratón sobre él para ver el motivo.

En el editor de páginas de AEM Sites y en Adobe Managed Services (AMS), para resaltar también se requiere **modo de edición**. En **modo de vista previa**, la comprobación preliminar muestra **problemas de resaltado no disponibles**; cambie a **modo de edición** para resaltar elementos en la página.

## ID de trabajo

Cada ejecución de comprobaciones tiene un ID de trabajo único, que se muestra en la parte inferior del panel. Resulta principalmente útil cuando un administrador soluciona problemas en una ejecución específica. Pase el ratón sobre el ID y seleccione el icono de copia que aparece a su derecha; el ID se copia en el portapapeles y aparece un mensaje de confirmación. Incluya este ID cuando informe de un problema.

Cuando se utiliza la comprobación preliminar fuera del editor universal (por ejemplo, a través de Sidekick o un bookmarklet), el pie de página del panel también muestra el nombre de la organización encima del ID de trabajo. En el editor universal, su organización aparece en el encabezado de AEM.
