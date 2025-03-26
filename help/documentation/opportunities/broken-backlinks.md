---
title: Documentación de oportunidad de vínculos rotos
description: Obtenga información acerca de la oportunidad de vínculos rotos y cómo utilizarla para mejorar la adquisición de tráfico.
badgeTrafficAcquisition: label="Adquisición de tráfico" type="Caution" url="../../opportunity-types/traffic-acquisition.md" tooltip="Adquisición de tráfico"
source-git-commit: c99bd0ab418c1eb0693f39ea16ee41f8a1263099
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 1%

---


# Oportunidad de backlinks rotos

![Oportunidad de vínculos rotos](./assets/broken-backlinks/hero.png){align="center"}

La oportunidad de vínculos secundarios rotos identifica los vínculos de otros sitios web al sitio que generan un error 404. Dado que los motores de búsqueda utilizan vínculos secundarios para determinar la relevancia de la búsqueda, los vínculos rotos pueden afectar negativamente a la SEO y la capacidad de detección del sitio. Estos problemas pueden deberse a factores como los cambios de URL o la eliminación de la página vinculada.

La oportunidad de vínculos secundarios rotos muestra un resumen en la parte superior de la página, que incluye una sinopsis del problema y su impacto en el sitio y en la empresa.

* **Tráfico proyectado perdido** - La pérdida de tráfico estimada debido a enlaces rotos.
* **Valor de tráfico proyectado** - Valor estimado del tráfico perdido.

## Identificar automáticamente

![Identificar automáticamente los backlinks rotos](./assets/broken-backlinks/auto-identify.png){align="center"}

La oportunidad de vínculos secundarios rotos enumera todos los vínculos secundarios rotos del sitio, incluidos los siguientes:

* **Página de referencia**: el dominio del sitio web que contiene el vínculo roto.
* **Prioridad**: alta, media o baja, lo que indica el impacto que tiene el vínculo roto en SEO según TODO.
* **Dirección URL de destino rota**: La dirección URL no existente del sitio a la que se está vinculando.

## Sugerir automáticamente

![Sugerencia automática de backlinks rotos](./assets/broken-backlinks/auto-suggest.png){align="center"}

La oportunidad de vínculos rotos también proporciona sugerencias generadas por IA sobre a qué página del sitio web debe redirigirse la URL rota. Las sugerencias se basan en el texto que incluye la dirección URL rota y el contenido de la página sugerida.


>[!BEGINTABS]

>[!TAB Fundamento de IA]

![Razones de IA sobre la autosugerencia de backlinks rotos](./assets/broken-backlinks/auto-suggest-ai-rationale.png){align="center"}

Seleccione el icono **information** para ver los motivos de IA para la URL sugerida. La justificación explica por qué la IA cree que la URL sugerida es la mejor opción para el vínculo roto. Esto puede ayudarle a comprender el proceso de toma de decisiones de la IA y a tomar una decisión informada sobre si aceptar o rechazar la sugerencia.

>[!TAB Editar URL de destino]

![Editar URL sugerida de backlinks rotos](./assets/broken-backlinks/edit-target-url.png){align="center"}

Si no está de acuerdo con la sugerencia generada por IA, puede editar la URL sugerida seleccionando el **icono de edición**. Esto le permite introducir manualmente la dirección URL que crea que es la mejor opción para el vínculo roto. Sites Optimizer también enumerará otras direcciones URL del sitio que crea que pueden ser adecuadas para el vínculo roto.

>[!TAB Omitir entradas]

![Ignorar vínculos rotos](./assets/broken-backlinks/ignore.png){align="center"}

Puede optar por ignorar las entradas con la URL de destino rota. Al seleccionar el **icono de omitir**, se eliminará el vínculo de retorno roto de la lista de oportunidades. Los backlinks rotos ignorados se pueden volver a activar desde la pestaña **Ignorado** en la parte superior de la página de la oportunidad.

>[!ENDTABS]

## Optimización automática

[!BADGE Ultimate]{type=Positive tooltip="Ultimate"}

![Optimizar automáticamente los backlinks rotos](./assets/broken-backlinks/auto-optimize.png){align="center"}

Sites Optimizer Ultimate añade la capacidad de implementar la optimización automática para los vínculos secundarios rotos. Al seleccionar el botón **Optimizar automáticamente**, se actualizarán automáticamente las reglas de redireccionamiento del sitio de AEM para asignar la **URL de destino rota** a la **URL sugerida**. Esto garantiza que los visitantes del sitio web y los bots de búsqueda que siguen los vínculos rotos en las **páginas de referencia** se redirijan a la página correcta del sitio, lo que mejora la optimización de los motores de búsqueda y la experiencia del usuario.

>[!BEGINTABS]

>[!TAB Implementar optimización]

![Implementar la optimización de los backlinks rotos](./assets/broken-backlinks/deploy-optimization.png){align="center"}

Si se selecciona **Implementar optimización**, se actualizarán las reglas de redireccionamiento del sitio de AEM para asignar la **URL de destino rota** a la **URL sugerida**. Esto garantiza que los visitantes del sitio web y los bots de búsqueda que siguen los vínculos rotos en las **páginas de referencia** se redirijan a la página correcta del sitio, lo que mejora la optimización de los motores de búsqueda y la experiencia del usuario.

>[!TAB Solicitar aprobación]

![Solicitar aprobación para los backlinks rotos](./assets/broken-backlinks/request-approval.png){align="center"}

{{auto-optimize-request-approval}}

>[!ENDTABS]
