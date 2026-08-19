---
title: Ejecutar auditorías en Preflight
description: Obtenga información sobre cómo iniciar una auditoría de Preflight en la página.
source-git-commit: 7224badecd83652a0971f669e23ff325b26892f3
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 14%

---


# Auditorías en Preflight

Preflight realiza una auditoría de la página para identificar las oportunidades de mejorar el contenido antes de publicarlo. A diferencia de un análisis automático, usted elige cuándo ejecutar las auditorías, de modo que puede analizar una página cuando esté listo.

![La pantalla de aterrizaje de comprobación preliminar con el botón Analizar página](./assets/audits/hero.png){align="center"}

Para ejecutar auditorías de Preflight para una página:

1. Abra la página que desee auditar en su [entorno de creación](./access-preflight.md) (editor universal, creación basada en documentos o editor de páginas de AEM Sites).
1. Abra el [panel Preflight](./access-preflight.md). Se abre la comprobación preliminar en la pantalla de aterrizaje **Ejecutar auditoría de preparación para el rendimiento**.
1. Seleccione **Analizar página**. Preflight ejecuta todas sus auditorías en la página actual y abre el panel de preparación, donde muestra una puntuación de preparación y las oportunidades que encuentra, agrupadas por categoría.

Para comprender los resultados de la vista previa e identificar las oportunidades de optimización, vea [Resultados de auditoría en la comprobación preliminar](./audit-results.md).

## Utilice el botón Comprobaciones integrado

Si su entorno de creación ejecuta [AEM 2026.7.0 (versión 27083)](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/maintenance/2026/2026-7-0#release-27083) o posterior, la comprobación preliminar está integrada en la barra de herramientas del Editor de páginas de AEM Sites. Seleccione el icono **Comprobaciones** (el botón de reproducción) para abrir el panel de la página actual y, a continuación, seleccione **Analizar página** para ejecutar las auditorías.

>[!VIDEO](https://video.tv.adobe.com/v/3496629?learn=on&enablevpops)

## Continuar una sesión anterior

La comprobación preliminar recuerda la ejecución más reciente, por lo que no tiene que volver a ejecutar las auditorías si sale y vuelve.

* Si vuelve a abrir el panel Comprobación preliminar en la **misma ficha del explorador**, incluso después de una actualización, la Comprobación preliminar carga automáticamente los resultados de la última ejecución.
* Si devuelves **en una ficha nueva o después de cerrar el explorador**, la pantalla de aterrizaje mostrará el botón **Continuar última sesión** junto a **Analizar página**. Seleccione **Continuar última sesión** para volver a cargar los resultados más recientes o seleccione **Analizar página** para iniciar una nueva ejecución.

La comprobación preliminar realiza un seguimiento de la ejecución más reciente por separado para cada página, por lo que **Continuar la última sesión** siempre vuelve a cargar la última ejecución de la página en la que se encuentra.

Cuando vuelve a cargar una ejecución anterior, el encabezado muestra hace cuánto tiempo se realizó esa ejecución (por ejemplo, *2 minutos atrás* o *ayer*) para que pueda saber de un vistazo qué tan actuales son los resultados. La etiqueta se actualiza a medida que pasa el tiempo y permanece visible a medida que se mueve entre el panel de preparación y las páginas de detalles de auditoría.

Una vez que finalicen las auditorías y se muestren los resultados, seleccione **Volver a analizar** de las **acciones más** (**...**) en la barra de herramientas para descartar los resultados y volver a ejecutar cada auditoría. Ver [resultados de auditoría en comprobación preliminar](./audit-results.md#toolbar).

