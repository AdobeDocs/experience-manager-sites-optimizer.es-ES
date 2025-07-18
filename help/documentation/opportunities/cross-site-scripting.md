---
title: Documentación sobre la oportunidad de ejecución de scripts en sitios múltiples
description: Obtenga información sobre la oportunidad de ejecución de scripts en sitios múltiples e identifique y corrija las vulnerabilidades de seguridad del sitio.
badgeSecurityPosture: label="Posición de seguridad" type="Caution" url="../../opportunity-types/security-posture.md" tooltip="Posición de seguridad"
source-git-commit: cb64a34b758de8f5dcea298014ddd0ba79a24c17
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 78%

---


# Oportunidad de ejecución de scripts en sitios múltiples

![Oportunidad de sitios múltiples](./assets/cross-site-scripting/hero.png){align="center"}

La oportunidad de ejecución de scripts en sitios múltiples identifica las vulnerabilidades en el código del sitio. A continuación, soluciona problemas que los atacantes podrían aprovechar para insertar secuencias de comandos malintencionadas en las páginas web que ven otros usuarios. Estos scripts pueden robar información confidencial, como las cookies de sesión, o realizar acciones en nombre del usuario, como cambiar su contraseña.

## Identificación automática

![Identificación automática de la oportunidad en sitios múltiples](./assets/cross-site-scripting/auto-identify.png){align="center"}

* **Código vulnerable**: cualquier código que sea vulnerable a ataques de ejecución de scripts en sitios múltiples.
* **Vínculo para reproducir**: el vínculo a la página donde se encontró la vulnerabilidad.

## Sugerencia automática

![Sugerencia automática de oportunidad en sitios múltiples](./assets/cross-site-scripting/auto-suggest.png){align="center"}

* **Corrección sugerida**: una sugerencia generada por la IA sobre cómo corregir la vulnerabilidad.

## Optimización automática

[!BADGE Ultimate]{type=Positive tooltip="Ultimate"}

>[!BEGINTABS]

>[!TAB Implementar optimización]

{{auto-optimize-deploy-optimization-slack}}

>[!TAB Solicitar aprobación]

{{auto-optimize-request-approval}}

>[!ENDTABS]
