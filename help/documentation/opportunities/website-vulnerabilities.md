---
title: Documentación de oportunidad de vulnerabilidades de sitio web
description: Obtenga información sobre la oportunidad de vulnerabilidades del sitio web y cómo utilizarla para aumentar la seguridad de en el sitio web.
badgeSecurityPosture: label="Posición de seguridad" type="Caution" url="../../opportunity-types/security-posture.md" tooltip="Posición de seguridad"
source-git-commit: c99bd0ab418c1eb0693f39ea16ee41f8a1263099
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 1%

---


# Oportunidad de vulnerabilidades del sitio web

![Oportunidad de vulnerabilidades del sitio web](./assets/website-vulnerabilities/hero.png){align="center"}

La oportunidad de vulnerabilidades del sitio web identifica vulnerabilidades de seguridad en las bibliotecas de terceros que utiliza el código de la aplicación. Estas vulnerabilidades podrían ser explotadas por un atacante malicioso, lo que aumenta el riesgo y disminuye la postura de seguridad de su sitio web.

La oportunidad de vulnerabilidades del sitio web muestra un resumen en la parte superior de la página, que incluye lo siguiente:

* **Problemas encontrados**: número de vulnerabilidades encontradas, clasificadas por el riesgo de seguridad que representan (bajo, medio, alto).
* **Riesgo de seguridad agregado**: el riesgo de seguridad general para su sitio web basado en las vulnerabilidades encontradas por la oportunidad.

## Identificar automáticamente

![Identificar automáticamente las vulnerabilidades del sitio web](./assets/website-vulnerabilities/auto-identify.png){align="center"}

La característica **Oportunidad de vulnerabilidades del sitio web** identifica y enumera automáticamente las vulnerabilidades que se encuentran en las bibliotecas de terceros que usa el código de la aplicación. Proporciona los siguientes detalles:

* **Biblioteca**: la biblioteca de terceros que contiene la vulnerabilidad. Una sola biblioteca puede tener varias vulnerabilidades.
* **Versión actual** - La versión de la biblioteca que se está usando actualmente.
* **Versión recomendada**: la versión sugerida que resuelve la vulnerabilidad.
* **Puntuación**: la clasificación de gravedad de la vulnerabilidad, también resumida en la parte superior de la página.
* **Vulnerabilidad**: el identificador de vulnerabilidad, una breve descripción y un vínculo a la base de datos de vulnerabilidad nacional (NVD) para obtener más detalles. Para acceder al vínculo NVD, haga clic en el identificador o en el vínculo situado junto a la descripción.

## Sugerir automáticamente

![Sugerir automáticamente vulnerabilidades de sitios web](./assets/website-vulnerabilities/auto-suggest.png){align="center"}

La sugerencia automática proporciona sugerencias generadas por IA para la **versión recomendada** de la biblioteca vulnerable a la que debería actualizar. Cada entrada tiene una **puntuación** que indica su gravedad general, lo que ayuda a priorizar las vulnerabilidades más críticas.

>[!BEGINTABS]

>[!TAB Detalles de vulnerabilidad]

Cada vulnerabilidad contiene un vínculo a la información detallada de la [Base de datos de vulnerabilidad nacional (NVD)](https://nvd.nist.gov/). Al hacer clic en el identificador de vulnerabilidad o en el elemento de vínculo a la derecha de la descripción, se le redirigirá a la página de NVD correspondiente a esa vulnerabilidad.

>[!TAB Omitir entradas]

Puede elegir ignorar las entradas de la lista de vulnerabilidades. Si se selecciona el **icono de omitir**, se eliminará la entrada de la lista. Las entradas ignoradas se pueden volver a activar desde la ficha **Ignorado** en la parte superior de la página de la oportunidad.<!---right now it does not seem to be implemented, but the page description mentions this functionality-->

>[!ENDTABS]


## Optimización automática

[!BADGE Ultimate]{type=Positive tooltip="Ultimate"}

![Optimizar automáticamente las vulnerabilidades del sitio web](./assets/website-vulnerabilities/auto-optimize.png){align="center"}

Sites Optimizer Ultimate añade la capacidad de implementar la optimización automática para las vulnerabilidades encontradas.

>[!BEGINTABS]

>[!TAB Implementar optimización]

{{auto-optimize-deploy-optimization-slack}}

>[!TAB Solicitar aprobación]

{{auto-optimize-request-approval}}

>[!ENDTABS]