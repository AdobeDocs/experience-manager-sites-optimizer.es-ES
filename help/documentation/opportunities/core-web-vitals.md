---
title: Documentación de oportunidad de elementos vitales web principales
description: Obtenga información acerca de la oportunidad de elementos vitales de la web y cómo utilizarla para mejorar la adquisición de tráfico.
badgeSiteHealth: label="Estado del sitio" type="Caution" url="../../opportunity-types/site-health.md" tooltip="Estado del sitio"
source-git-commit: 81343812472477448fd0ee8be89bd6ae784a9e61
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 1%

---


# Oportunidad de elementos vitales web principales

![oportunidad de elementos vitales de la web principal](./assets/core-web-vitals/hero.png){align="center"}

La oportunidad de elementos fundamentales para la web identifica problemas que pueden degradar la experiencia del usuario y el rendimiento de búsqueda orgánica de sus páginas web. Estos problemas surgen de una amplia gama de factores como: fuentes personalizadas, dependencias de javascript no optimizadas, scripts de terceros, etc. La oportunidad de elementos vitales de la web apunta a estos elementos defectuosos y sugiere correcciones que pueden aumentar el rendimiento de su página web. Tenga en cuenta que solo se pueden analizar las páginas que tienen al menos 1000 vistas de página.

Para empezar, la oportunidad de elementos vitales de la web principal muestra un resumen en la parte superior de la página, incluida una sinopsis del problema y su impacto en el sitio y en la empresa.

* **Se ha perdido tráfico proyectado** - La pérdida de tráfico estimada debido a los elementos vitales de la web que están por debajo de los umbrales de rendimiento.
* **Valor de tráfico proyectado** - Valor estimado del tráfico perdido.

## Identificar automáticamente

![Identificar automáticamente los elementos vitales de la web principal](./assets/core-web-vitals/auto-identify.png){align="center"}

En la parte inferior de la página, tiene una lista de todos los problemas actuales agrupados como:

* **Problemas móviles**: una lista de problemas que afectan a la versión móvil de la página.
* **Problemas de escritorio**: una lista de problemas que afectan a la versión de escritorio de la página.

Cada problema se muestra en una tabla, con la columna **Página** que identifica la entrada de página afectada.

Además, estos problemas también se agrupan por las métricas de rendimiento estándar del informe de constantes web principales: pintura de contenido más grande **LCP**, interacción con la siguiente pintura **INP** y cambio de diseño acumulativo **CLS**.

## Sugerir automáticamente

![Sugerir automáticamente la oportunidad de elementos vitales de la web](./assets/core-web-vitals/auto-suggest.png){align="center"}

La oportunidad de constantes web principales proporciona sugerencias de correcciones generadas por IA. Al hacer clic en el botón de sugerencias, aparece una nueva ventana que contiene las métricas de rendimiento **LCP**, **INP** y **CLS** como categorías. Puede cambiar entre estas categorías para ver una lista de problemas específicos.

Cada categoría puede contener varios problemas, por lo que asegúrese de desplazarse hacia abajo para ver la lista completa de problemas y recomendaciones.  Además, hay dos indicadores de rendimiento para móviles y equipos de escritorio para cada métrica.

## Optimizar automáticamente [!BADGE Ultimate]{type=Positive tooltip="Ultimate"}


![Oportunidad de optimizar automáticamente los elementos vitales de la web principal](./assets/core-web-vitals/auto-optimize.png){align="center"}

Sites Optimizer Ultimate agrega la capacidad de implementar la optimización automática para los problemas encontrados por la oportunidad de elementos vitales de la web principal. <!--- TBD-need more in-depth and opportunity specific information here. What does the auto-optimization do?-->

>[!BEGINTABS]

>[!TAB Implementar optimización]

{{auto-optimize-deploy-optimization-slack}}

>[!TAB Solicitar aprobación]

{{auto-optimize-request-approval}}

>[!ENDTABS]

