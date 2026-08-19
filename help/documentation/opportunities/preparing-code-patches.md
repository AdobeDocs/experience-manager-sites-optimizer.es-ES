---
title: Preparación de la documentación de parches de código
description: Descubra cómo AEM Sites Optimizer prepara parches de código para las correcciones de Core Web Vitals y cómo rastrearlos posteriormente.
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: a86d83ee226055e6401b13fd421b40d449b96fa8
workflow-type: tm+mt
source-wordcount: 248
ht-degree: 2%

---

# Preparación de la documentación de parches de código

<!--![Preparing code patches](./assets/preparing-code-patches/hero.png){align="center"}-->

Para la [oportunidad de elementos vitales para la web](/help/documentation/opportunities/core-web-vitals.md), AEM Sites Optimizer genera correcciones en el nivel de código para los problemas de rendimiento identificados. Estas correcciones se revisan y preparan como parches de código, en lugar de implementarse directamente.

## Preparar parches de código

Seleccione uno o más problemas de la lista Core Web Vitals y, a continuación, haga clic en **Preparar parche de código** para preparar su selección, o en **Preparar todos los parches de código** para preparar todos los parches disponibles a la vez. AEM Sites Optimizer crea un problema de GitHub etiquetado para cada corrección y abre automáticamente una solicitud de extracción vinculada con el cambio de código, lista para que su equipo la revise, pruebe y combine.

Esta acción se desactiva cuando no tiene permiso para preparar parches de código o cuando el sitio no está completamente configurado para ello, por ejemplo, cuando no hay ningún repositorio de código conectado o cuando la generación de parches aún está en curso. En cada caso, Sites Optimizer explica por qué junto al botón deshabilitado.

## Seguimiento de parches de código preparados

Una vez que hayas preparado los parches de código, puedes administrarlos y dar los siguientes pasos desde la pestaña **Implementado** en la página de detalles de Core Web Vitals, junto con las pestañas **Actual** y **Ignorado**. El estado de un parche refleja si su solicitud de extracción se ha fusionado, no solo generado; un problema solo se mueve a **Implementado** una vez que la corrección se haya fusionado en la base de código.

## Consulte también

* [Oportunidad de Core Web Vitals](/help/documentation/opportunities/core-web-vitals.md#auto-optimize)
* [Implementación en la documentación del autor](/help/documentation/opportunities/deploying-to-author.md)
