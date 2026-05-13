---
title: Documentación sobre la oportunidad de Core Web Vitals
description: Obtenga información sobre la oportunidad de Core Web Vitals y cómo utilizarla para mejorar la adquisición de tráfico.
badgeSiteHealth: label="Estado del sitio" type="Caution" url="../../opportunity-types/site-health.md" tooltip="Estado del sitio"
TQID: https://experienceleague.adobe.com/3h-Xas767zUk-Sod7JEr9Lh767r5S3LKpbwJZFZU2kg
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 84a1ae98d67bc02ab272131194511efbeccab492
workflow-type: tm+mt
source-wordcount: 533
ht-degree: 100%

---

# Oportunidad de Core Web Vitals

<!--![core web vitals opportunity](./assets/core-web-vitals/hero.png){align="center"}-->

>[!VIDEO](https://video.tv.adobe.com/v/3483371/?learn=on&enablevpops)

La oportunidad de Core Web Vitals identifica las páginas del sitio web que tienen un bajo rendimiento, lo que afecta a la experiencia del usuario y al rendimiento de la búsqueda orgánica. Estos problemas pueden surgir de factores como fuentes personalizadas, dependencias de JavaScript no optimizadas y scripts de terceros. Core Web Vitals mide la rapidez con la que se carga el contenido, la estabilidad del diseño de la página y la capacidad de adaptación de la página a las interacciones del usuario.

AEM Sites Optimizer detecta las páginas afectadas por estos problemas, ofrece recomendaciones de IA específicas a nivel de código y aplica correcciones a través de los flujos de trabajo de desarrollo existentes. Tenga en cuenta que solo se pueden analizar las páginas que tienen al menos 1000 vistas de página.

## Identificación automática

<!--![Auto-identify core web vitals](./assets/core-web-vitals/auto-identify.png){align="center"}-->

AEM Sites Optimizer monitoriza continuamente el rendimiento del sitio mediante [Operational Telemetry](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/sites/operational-telemetry-for-aem-as-a-cloud-service) para detectar regresiones en las métricas de Core Web Vitals, como LCP (Largest Contentful Paint), CLS (Cumulative Layout Shift) e INP (Interaction to Next Paint). Utiliza datos de usuarios reales para identificar las regresiones de rendimiento y prioriza los problemas en función de su impacto en la experiencia del usuario.

AEM Sites Optimizer muestra la lista de todos los problemas actuales, detallados por dispositivos móviles y de escritorio. La columna **Página** indica la entrada de la página afectada y los problemas se clasifican según LCP, INP y CLS.

## Sugerencia automática

<!--![Auto-suggest core web vitals opportunity](./assets/core-web-vitals/auto-suggest.png){align="center"}-->

Para cada problema identificado, AEM Sites Optimizer genera recomendaciones prescriptivas a nivel de código para mejorar el rendimiento de Core Web Vitals. Evalúa la implementación subyacente accediendo al repositorio de código. Esto permite al sistema analizar cómo se implementan los componentes, los scripts y los estilos, así como identificar la causa raíz de los problemas de rendimiento. En función de este análisis, el sistema ofrece recomendaciones específicas y genera parches de código que especifican los cambios necesarios para mejorar el rendimiento. Cada recomendación se puede revisar antes de aplicarse.

Al hacer clic en el botón de sugerencias, aparece una nueva ventana que contiene las métricas de rendimiento LCP, INP y CLS como categorías. Puede cambiar entre estas categorías para ver una lista de problemas específicos. Cada categoría puede contener varios problemas, así que asegúrese de desplazarse hacia abajo para ver la lista completa de problemas y recomendaciones. Además, hay dos indicadores de rendimiento tanto para los dispositivos móviles como los de escritorio para cada métrica.

## Optimización automática

<!--[!BADGE Ultimate]{type=Positive tooltip="Ultimate"}-->

Una vez revisadas y aprobadas las recomendaciones, puede hacer clic en **Implementar optimización**. AEM Sites Optimizer genera parches de código basados en los problemas identificados y los pone a disposición a través de procesos de control de versiones. El proceso de optimización incluye los siguientes pasos:

* **Creación de problema**: crea un problema de GitHub etiquetado para cada corrección, incluyendo una descripción clara y una URL afectada para la visibilidad.
* **Envío de solicitud de extracción**: abre automáticamente una solicitud de extracción vinculada con la corrección de código exacta, lista para su revisión, pruebas y combinación.
* **Seguimiento del estado**: realiza el seguimiento de cada corrección hasta el final indica los intentos parciales o fallidos de seguimiento.

Antes de poner a disposición estas actualizaciones, AEM Sites Optimizer realiza una validación para garantizar que las correcciones resuelvan el problema subyacente y no introduzcan regresiones. Todas las actualizaciones siguen las prácticas de desarrollo estándar, que requieren revisión y aprobación antes de combinarse con la producción.

Esto garantiza que las optimizaciones de rendimiento sean precisas, se validen y se integren en los procesos de desarrollo y gobernanza existentes.
