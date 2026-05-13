---
title: Documentación sobre la oportunidad de vínculos de retroceso rotos
description: Obtenga información sobre la oportunidad de vínculos de retroceso rotos y cómo utilizarla para mejorar la adquisición de tráfico.
badgeTrafficAcquisition: label="Adquisición de tráfico" type="Caution" url="../../opportunity-types/traffic-acquisition.md" tooltip="Adquisición de tráfico"
TQID: https://experienceleague.adobe.com/HTgcPKBO-r-NRgdUdqS6ZOklYRaLM8pQbr3KbaYD4nQ
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 84a1ae98d67bc02ab272131194511efbeccab492
workflow-type: tm+mt
source-wordcount: 655
ht-degree: 30%

---

# Oportunidad de vínculos de retroceso rotos

<!--![Broken backlinks opportunity](./assets/broken-backlinks/hero.png){align="center"}-->

>[!VIDEO](https://video.tv.adobe.com/v/3483250/?learn=on&enablevpops)

La oportunidad de vínculos secundarios rotos identifica vínculos externos que apuntan a páginas inexistentes (404) del sitio. Estos vínculos resultan en pérdida de tráficos de referencia y menor valor de SEO, ya que los motores de búsqueda dependen de los backlinks para evaluar la relevancia y la autoridad. Estos problemas se producen cuando se cambian las direcciones URL, se elimina el contenido o las páginas ya no están disponibles sin las redirecciones adecuadas. AEM Sites Optimizer identifica todos los vínculos secundarios rotos, proporciona recomendaciones de IA específicas y permite una implementación con un solo clic para corregirlas, todo en una sola vista centralizada.

## Identificación automática

<!--![Auto-identify broken backlinks](./assets/broken-backlinks/auto-identify.png){align="center"}-->

AEM Sites Optimizer analiza continuamente las fuentes de datos externas para detectar los vínculos secundarios que apuntan a páginas 404 inexistentes del sitio. Se agregan datos de múltiples fuentes, entre ellas Google Search Console, [Telemetría operativa](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/sites/operational-telemetry-for-aem-as-a-cloud-service) y plataformas de optimización de los motores de búsqueda de terceros. La oportunidad de identificación automática identifica los dominios externos que se vinculan a direcciones URL rotas y las prioriza en función del impacto, incluidas la autoridad de dominio y las pérdidas de tráfico y equidad de vínculos esperadas.

Esta oportunidad enumera todos los problemas identificados, incluidos los siguientes detalles:

* **Dominio de referencia y página**: La página o dominio externo que contiene el vínculo roto.
* **Prioridad**: alta, media o baja que indica el impacto que tiene el vínculo roto en el proceso de SEO.
* **Dirección URL de destino dañada**: Dirección URL inexistente del sitio a la que se está vinculando.

## Sugerencia automática

<!--![Auto-suggest broken backlinks](./assets/broken-backlinks/auto-suggest.png){align="center"}-->

Para cada vínculo posterior roto identificado, AEM Sites Optimizer recomienda el destino más adecuado para restaurar el tráfico y el valor SEO. Determina la intención del vínculo de retorno analizando:

* Estructura y tokens de URL
* Anclar texto
* Título y contexto de la página de referencia

Esta intención se compara con el contenido existente del sitio para identificar la página de destino más relevante. Cada URL rota se asigna a una página de reemplazo exacta o a la correspondiente más cercana. Si no se puede determinar un destino adecuado, el problema se muestra para su revisión manual.

>[!BEGINTABS]

>[!TAB Motivo de la IA]

<!--![AI rationale on autosuggestion of broken backlinks](./assets/broken-backlinks/auto-suggest-ai-rationale.png){align="center"}-->

Seleccione el icono **información** para ver los motivos de IA para la URL sugerida. El motivo explica por qué la IA cree que la URL sugerida es la mejor opción para el vínculo roto. Esto puede ayudarle a comprender el proceso de toma de decisiones de la IA y a tomar una decisión fundamentada sobre si aceptar o rechazar la sugerencia.

>[!TAB Editar URL de destino]

<!--![Edit suggested URL of broken backlinks](./assets/broken-backlinks/edit-target-url.png){align="center"}-->

Si no está de acuerdo con la sugerencia generada por IA, puede editar la URL sugerida seleccionando el **icono de edición**. Esto le permite introducir manualmente la dirección URL que crea que es la mejor opción para el vínculo roto. Sites Optimizer también enumerará otras direcciones URL del sitio que crea que pueden ser adecuadas para el vínculo roto.

>[!TAB Ignorar entradas]

<!--![Ignore broken backlinks](./assets/broken-backlinks/ignore.png){align="center"}-->

Puede elegir ignorar las entradas con las direcciones URL rotas indicadas. Al seleccionar el ![icono de eliminar o el icono de ignorar](https://spectrum.adobe.com/static/icons/ui_18/CrossSize500.svg), se eliminará el vínculo de retroceso roto de la lista de oportunidades. Los vínculos de retroceso rotos ignorados se pueden volver a activar desde la pestaña **Ignorado** en la parte superior de la página de la oportunidad.

>[!ENDTABS]

## Optimización automática

<!--[!BADGE Ultimate]{type=Positive tooltip="Ultimate"}-->

Una vez que las sugerencias se hayan revisado y aprobado, puede hacer clic en **Implementar optimización**. A continuación, AEM Sites Optimizer aplica las correcciones en el entorno de creación, en función de cómo se administran las redirecciones en la implementación. El autor de AEM puede publicar los cambios desde el sistema de administración de contenido (CMS).

Según la configuración, las correcciones se aplican como cambios de contenido o código dentro de los flujos de trabajo de implementación existentes. El proceso de optimización incluye los siguientes pasos:

* **Validación**: garantiza que los cambios funcionen según lo esperado y no introduzcan regresiones antes de la implementación.
* **Implementación**: aplica cambios a través de procesos existentes, como actualizaciones de contenido en AEM o implementación de código a través de canalizaciones de CI/CD.
* **Comprobación de permisos** - Comprueba que el usuario tiene los permisos adecuados para implementar los cambios. Si no es así, se proporcionan salidas alternativas como listas de redireccionamiento descargables o parches de código.

Este proceso garantiza que las redirecciones se implementen con precisión, se validen antes de la versión y se alineen con las configuraciones y los procesos de gobernanza existentes.
