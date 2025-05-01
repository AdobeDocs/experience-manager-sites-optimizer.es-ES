---
title: Documentación sobre la oportunidad de vínculos internos rotos
description: Obtenga información sobre la oportunidad de vínculos rotos y cómo utilizarla para mejorar la participación en el sitio web.
badgeEngagement: label="Participación" type="Caution" url="../../opportunity-types/engagement.md" tooltip="Participación"
source-git-commit: c2bd3f7dc998b103ecdd02c239b1ea0312db20f1
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 99%

---


# Oportunidad de vínculos internos rotos

![Oportunidad de vínculos internos rotos](./assets/broken-internal-links/hero.png){align="center"}

Los vínculos internos rotos afectan a la posibilidad del motor de búsqueda para indexar el sitio y afectan negativamente a la experiencia del usuario y a la optimización del motor de búsqueda. Para ayudar a solucionar este problema, la oportunidad de vínculos internos rotos señala las direcciones URL rotas y proporciona sugerencias para actualizaciones de vínculos válidos. Solucionar estos problemas mejorará la participación del usuario y garantizará una navegación y accesibilidad fluidas.

La oportunidad de vínculos internos rotos muestra un resumen en la parte superior de la página, que incluye una sinopsis del problema y su impacto en el sitio y en la empresa.

* **Tráfico proyectado perdido**: la pérdida de tráfico estimada debido a vínculos internos rotos.
* **Valor de tráfico proyectado**: el valor estimado del tráfico perdido.

## Identificación automática

<!---![Auto-identify broken internal links](./assets/missing-or-invalid-metadata/auto-identify.png){align="center"}-->

La oportunidad de vínculos internos rotos identifica y enumera automáticamente todos los vínculos internos rotos de las páginas, e incluye lo siguiente:

* **Página de referencia**: la página que contiene el vínculo roto.
* **URL de destino rota**: el vínculo interno roto.
* **Sugerencia**: una sugerencia generada por la IA sobre cómo actualizar el vínculo interrumpido. Consulte la sección de sugerencia automática para obtener más información.

## Sugerencia automática

<!--![Auto-suggest broken internal links](./assets/broken-internal-links/auto-suggest.png){align="center"}-->

La oportunidad de vínculos internos rotos proporciona sugerencias generadas por la IA sobre cómo actualizar los vínculos rotos. Estas sugerencias se basan en la dirección URL interrumpida de destino y proporcionan un reemplazo adecuado. Al seleccionar el **icono de información**, se proporciona un motivo generado por la IA para la actualización sugerida.


>[!BEGINTABS]

>[!TAB Motivo de la IA]

<!--[AI rationale of broken internal links](./assets/broken-internal-links/auto-suggest-ai-rationale.png) -->

Seleccione el icono **información** para ver los motivos de la IA para la URL sugerida. El motivo explica por qué la IA cree que la URL sugerida es la mejor opción para el vínculo roto. Esto puede ayudarle a comprender el proceso de toma de decisiones de la IA y a tomar una decisión fundamentada sobre si aceptar o rechazar la sugerencia.

>[!TAB Editar URL de destino]

<!--![Edit suggested URL of broken internal links](./assets/broken-internal-links/edit-target-url.png){align="center"}-->

Si no está de acuerdo con la sugerencia generada por la IA, puede editar el valor de vínculo sugerido seleccionando el **icono de edición**. Esto le permite introducir manualmente el vínculo deseado. La ventana de edición contiene la **Ruta de destino rota** del vínculo, la **Ruta de destino deseada** donde puede editar manualmente el vínculo y un campo con la sugerencia generada por la IA. Una vez que haya terminado de editar, haga clic en **Guardar** para actualizar la entrada de vínculo roto. Aparecerá un punto amarillo en el campo de entrada para indicar que el vínculo se ha editado.

>[!TAB Ignorar entradas]

<!--![Ignore broken links](./assets/broken-internal-links/ignore.png){align="center"}-->

Puede elegir ignorar las entradas con las direcciones URL rotas indicadas. Al seleccionar el **icono de ignorar**, se eliminará la entrada de la lista de oportunidades. Las entradas ignoradas se pueden volver a activar desde la pestaña **Ignorado** en la parte superior de la página de la oportunidad.

>[!ENDTABS]


## Optimización automática

[!BADGE Ultimate]{type=Positive tooltip="Ultimate"}

<!---![Auto-optimize suggested invalid or missing metadata](./assets/broken-internal-links/auto-optimize.png){align="center"}-->

Sites Optimizer Ultimate añade la posibilidad de implementar la optimización automática para los vínculos rotos encontrados por la oportunidad. <!--- TBD-need more in-depth and opportunity specific information here. What does the auto-optimization do?-->


>[!BEGINTABS]

>[!TAB Implementar optimización]

{{auto-optimize-deploy-optimization-slack}}

>[!TAB Solicitar aprobación]

{{auto-optimize-request-approval}}

>[!ENDTABS]

