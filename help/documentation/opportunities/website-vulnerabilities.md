---
title: Documentación sobre la oportunidad de vulnerabilidades del sitio web
description: Obtenga información sobre la oportunidad de vulnerabilidades del sitio web y cómo utilizarla para aumentar la seguridad de en el sitio web.
badgeSecurityPosture: label="Posición de seguridad" type="Caution" url="../../opportunity-types/security-posture.md" tooltip="Posición de seguridad"
TQID: https://experienceleague.adobe.com/vCLnRixzZCCqUVVHR0uBUYExdaPOZI60wsfhdRkF1Nc
product_v2: id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 252f5292d6dc62711b4ebeb8ce5a2707857fd674
workflow-type: ht
source-wordcount: 384
ht-degree: 100%

---

# Oportunidad de vulnerabilidades del sitio web

![Oportunidad de vulnerabilidades del sitio web](./assets/website-vulnerabilities/hero.png){align="center"}

La oportunidad de vulnerabilidades del sitio web identifica vulnerabilidades en materia de seguridad en las bibliotecas de terceros utilizadas por el código de la aplicación. Los atacantes maliciosos explotan estas vulnerabilidades, aumentando el riesgo y disminuyendo la posición de seguridad de su sitio web.

La oportunidad de vulnerabilidades del sitio web muestra un resumen en la parte superior de la página, que incluye lo siguiente:

* **Problemas encontrados**: número de vulnerabilidades encontradas, clasificadas por el riesgo de seguridad que representan (bajo, medio, alto).
* **Riesgo de seguridad añadido**: el riesgo de seguridad general para su sitio web basado en las vulnerabilidades encontradas por la oportunidad.

## Identificación automática

![Identificación automática de las vulnerabilidades del sitio web](./assets/website-vulnerabilities/auto-identify.png){align="center"}

La característica **Oportunidad de vulnerabilidades del sitio web** identifica y enumera automáticamente las vulnerabilidades que se encuentran en las bibliotecas de terceros utilizadas por el código de la aplicación. Proporciona los siguientes detalles:

* **Biblioteca**: la biblioteca de terceros que contiene la vulnerabilidad. Una sola biblioteca puede tener varias vulnerabilidades.
* **Versión actual**: la versión de la biblioteca que se está usando actualmente.
* **Versión recomendada**: la versión sugerida que resuelve la vulnerabilidad.
* **Puntuación**: la clasificación de gravedad de la vulnerabilidad, también resumida en la parte superior de la página.
* **Vulnerabilidad**: el identificador de vulnerabilidad, una breve descripción y un vínculo a la base de datos nacional de vulnerabilidades (NVD) para obtener más detalles. Para acceder al vínculo de NVD, haga clic en el identificador o en el vínculo situado junto a la descripción.

## Sugerencia automática

![Sugerencia automática de vulnerabilidades del sitio web](./assets/website-vulnerabilities/auto-suggest.png){align="center"}

La sugerencia automática proporciona sugerencias generadas por IA para la **versión recomendada** de la biblioteca vulnerable a la que debería actualizarse. Cada entrada tiene una **puntuación** que indica su gravedad general, lo que ayuda a priorizar las vulnerabilidades más críticas.

>[!BEGINTABS]

>[!TAB Detalles de la vulnerabilidad]

Cada vulnerabilidad contiene un vínculo a la información detallada de la [Base de datos nacional de vulnerabilidades (NVD)](https://nvd.nist.gov/). Al hacer clic en el identificador de vulnerabilidades o en el elemento de vínculo a la derecha de la descripción, se le redirigirá a la página de NVD correspondiente a esa vulnerabilidad.

>[!TAB Ignorar entradas]

Puede elegir ignorar las entradas de la lista de vulnerabilidades. Si se selecciona el ![icono Eliminar](https://spectrum.adobe.com/static/icons/ui_18/CrossSize500.svg), se eliminará la entrada de la lista. Las entradas ignoradas se pueden volver a activar desde la pestaña **Ignorado** en la parte superior de la página de la oportunidad.<!---right now it does not seem to be implemented, but the page description mentions this functionality-->

>[!ENDTABS]


## Optimización automática

[!BADGE Ultimate]{type=Positive tooltip="Ultimate"}

![Optimización automática de las vulnerabilidades del sitio web](./assets/website-vulnerabilities/auto-optimize.png){align="center"}

Sites Optimizer Ultimate añade la posibilidad de implementar la optimización automática para las vulnerabilidades encontradas.

>[!BEGINTABS]

>[!TAB Implementar optimización]

{{auto-optimize-deploy-optimization-slack}}

>[!TAB Solicitar aprobación]

{{auto-optimize-request-approval}}

>[!ENDTABS]