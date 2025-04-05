---
title: Documentación sobre la oportunidad de problemas del mapa del sitio
description: Obtenga información sobre la oportunidad de problemas del mapa del sitio y cómo utilizarla para mejorar la adquisición de tráfico.
badgeTrafficAcquisition: label="Adquisición de tráfico" type="Caution" url="../../opportunity-types/traffic-acquisition.md" tooltip="Adquisición de tráfico"
source-git-commit: c99bd0ab418c1eb0693f39ea16ee41f8a1263099
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 99%

---


# Oportunidad de problemas del mapa del sitio

![Oportunidad de problemas del mapa del sitio](./assets/sitemap-issues/hero.png){align="center"}

Un mapa del sitio completo y preciso ayuda a los motores de búsqueda a rastrear e indexar eficientemente las páginas del sitio web, lo que garantiza una mejor visibilidad en los resultados de búsqueda. La oportunidad del mapa del sitio identifica posibles problemas con el mapa del sitio. Solucionar estos problemas puede mejorar en gran medida la indexación del motor de búsqueda y la capacidad de detección del contenido del sitio.

En la parte superior de la página se muestra un resumen que incluye una sinopsis del problema y su impacto en el sitio y en la empresa.

* **Tráfico proyectado perdido**: la pérdida de tráfico estimada debido a problemas con el mapa del sitio.
* **Valor de tráfico proyectado**: el valor estimado del tráfico perdido.

## Identificación automática

Los problemas con el mapa del sitio se pueden filtrar según los siguientes criterios:

* **Mapa del sitio con problemas**: URL del mapa del sitio analizada que contiene posibles problemas.
* **Tipo de problema**: el tipo de problema identificado en el mapa del sitio:
   * **Errores del cliente**: entradas que no devuelven una respuesta de `200 Success`.
   * **Redireccionamientos**: redireccionamientos erróneos o mal configurados.

>[!BEGINTABS]

>[!TAB Errores del cliente]

![Identificación automática de los errores del cliente del mapa del sitio](./assets/sitemap-issues/auto-identify-client-errors.png){align="center"}

Si las direcciones URL del mapa del sitio devuelven estos errores, los motores de búsqueda pueden suponer que el mapa del sitio está obsoleto o que las páginas se eliminaron por error. El cliente indica que la solicitud del cliente (explorador o rastreador) no era válida. Los errores habituales son:

* **404 No encontrado**: la página solicitada no existe.
* **403 Prohibido**: el servidor deniega el acceso a la página solicitada.
* **410 Se ha ido**: la página se eliminó intencionadamente y no se devolverá.
* **401 No autorizado**: se requiere autenticación, pero no se proporciona.

Estos errores pueden dañar la optimización de los motores de búsqueda, especialmente si las páginas importantes devuelven **404 o 410**, ya que los motores de búsqueda pueden desindexarlas.

Cada problema se muestra en una tabla, con la columna **Página** que identifica la entrada de mapa del sitio afectada:

* **Página**: URL de la entrada del mapa del sitio con un problema.

>[!TAB Redireccionamientos]

![Identificación automática de los errores de cliente del mapa del sitio](./assets/sitemap-issues/auto-identify-redirects.png){align="center"}

Los mapas del sitio solo deben incluir direcciones URL de destino finales, no direcciones URL de redireccionamiento. Los redireccionamientos están pensados para guiar a los usuarios y rastreadores hasta la ubicación correcta, pero pueden causar problemas si se configuran incorrectamente:

* **302 Encontrado (redireccionamiento temporal)**: puede causar problemas de optimización de los motores de búsqueda si se usa por error en lugar de **301**.
* **307 Redireccionamiento temporal**: similar a 302, pero conserva el método HTTP.
* **Bucles de redireccionamiento**: cuando una página se vuelve a redirigir a sí misma o crea un bucle infinito.
* **Redireccionamientos interrumpidos**: cuando un redireccionamiento conduce a una página inexistente o 4xx.

Cada problema se muestra en una tabla, con la columna **Página** que identifica la entrada de mapa del sitio afectada:

* **Página**: URL de la entrada del mapa del sitio con un problema.

>[!ENDTABS]

## Sugerencia automática

Cada problema del mapa del sitio [ que cumple los criterios de filtro ](#auto-identify) se indica en una tabla con las columnas siguientes:

* **Página**: URL de la entrada del mapa del sitio con un problema.
* **Sugerencia**: la corrección recomendada para el problema.

Las sugerencias suelen incluir una ruta del sitio actualizada para corregir la entrada del mapa del sitio. En algunos casos, también pueden proporcionar instrucciones más detalladas, como especificar el destino de redireccionamiento correcto.

## Optimización automática

[!BADGE Ultimate]{type=Positive tooltip="Ultimate"}

![Problemas de optimización automática de mapas del sitio](./assets/sitemap-issues/auto-optimize.png){align="center"}

Sites Optimizer Ultimate añade la posibilidad de implementar optimizaciones automáticas de mapas del sitio.

>[!BEGINTABS]

>[!TAB Implementar optimización]

{{auto-optimize-deploy-optimization-slack}}

>[!TAB Solicitar aprobación]

{{auto-optimize-request-approval}}

>[!ENDTABS]
