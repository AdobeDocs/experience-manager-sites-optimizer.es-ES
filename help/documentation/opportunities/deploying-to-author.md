---
title: Implementación en la documentación del autor
description: Descubra cómo AEM Sites Optimizer implementa las optimizaciones seleccionadas en el entorno de creación y cómo rastrearlas posteriormente.
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 1d55c607aab6c820d014b9a57bfae20b8170c672
workflow-type: tm+mt
source-wordcount: 245
ht-degree: 6%

---

# Implementación en la documentación del autor

<!--![Deploying to author](./assets/deploying-to-author/hero.png){align="center"}-->

Una vez que AEM Sites Optimizer identifica una oportunidad y sugiere optimizaciones, puede revisar e implementar las optimizaciones seleccionadas para realizar más acciones.

## Implementar en la instancia de autor

Seleccione una o más sugerencias de la lista de una oportunidad y, a continuación, haga clic en **Implementar en autor** para implementar su selección, o en **Implementar todo en autor** para implementar todas las sugerencias disponibles a la vez. AEM Sites Optimizer aplica las optimizaciones seleccionadas solo al entorno de creación y no publica los cambios en el sitio activo. El autor de AEM puede revisar y publicar los cambios desde el sistema de administración de contenido (CMS), de acuerdo con el flujo de trabajo de [optimización automática](/help/documentation/opportunities/missing-alt-text.md#auto-optimize) de cada oportunidad.

Esta acción se deshabilita cuando no tiene permiso para implementar o cuando el sitio no está completamente configurado para la implementación (por ejemplo, cuando un repositorio de código aún no se ha conectado). En cualquier caso, Sites Optimizer explica por qué junto al botón deshabilitado.

## Seguimiento de optimizaciones implementadas

<!--![Deployed tab](./assets/deploying-to-author/deployed-tab.png){align="center"}-->

Una vez que haya implementado optimizaciones seleccionadas, puede administrarlas y dar los siguientes pasos desde la pestaña **Implementado** en la página de detalles de la oportunidad, junto con las pestañas **Actual** y **Ignorado**.

La mecánica de implementación específica, incluido cómo se aplican las actualizaciones para Edge Delivery Services, AEM as a Cloud Service o Digital Asset Management, varía según el tipo de oportunidad. Consulte la sección **Optimización automática** de esa oportunidad para obtener más información.

## Consulte también

* [Oportunidad de texto alternativo que falta](/help/documentation/opportunities/missing-alt-text.md#auto-optimize)
* [Oportunidad de Core Web Vitals](/help/documentation/opportunities/core-web-vitals.md#auto-optimize)
* [Oportunidad de vínculos de retroceso rotos](/help/documentation/opportunities/broken-backlinks.md#auto-optimize)
