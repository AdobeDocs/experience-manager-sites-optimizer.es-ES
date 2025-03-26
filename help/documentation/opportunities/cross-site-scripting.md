---
title: Documentación de oportunidad de ejecución de scripts en sitios múltiples
description: Obtenga información sobre la oportunidad de ejecución de scripts en sitios múltiples, así como para identificar y corregir las vulnerabilidades de seguridad del sitio.
badgeSecurityPosture: label="Posición de seguridad" type="Caution" url="../../opportunity-types/security-posture.md" tooltip="Posición de seguridad"
source-git-commit: c99bd0ab418c1eb0693f39ea16ee41f8a1263099
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 4%

---


# Oportunidad de ejecución de scripts en sitios múltiples

![Oportunidad entre sitios](./assets/cross-site-scripting/hero.png){align="center"}

La oportunidad de ejecución de scripts en sitios múltiples identifica y corrige las vulnerabilidades del código del sitio que los atacantes podrían aprovechar para insertar scripts maliciosos en páginas web que otros usuarios veían. Estos scripts pueden robar información confidencial, como las cookies de sesión, o realizar acciones en nombre del usuario, como cambiar su contraseña.

## Identificar automáticamente

![Identificar automáticamente la oportunidad entre sitios](./assets/cross-site-scripting/auto-identify.png){align="center"}

* **Código vulnerable**: cualquier código que sea vulnerable a ataques de scripts entre sitios.
* **Vínculo para reproducir**: el vínculo a la página donde se encontró la vulnerabilidad.

## Sugerir automáticamente

![Sugerencia automática de oportunidad entre sitios](./assets/cross-site-scripting/auto-suggest.png){align="center"}

* **Corrección sugerida**: Una sugerencia generada por IA sobre cómo corregir la vulnerabilidad.

## Optimización automática

[!BADGE Ultimate]{type=Positive tooltip="Ultimate"}

>[!BEGINTABS]

>[!TAB Implementar optimización]

{{auto-optimize-deploy-optimization-slack}}

>[!TAB Solicitar aprobación]

{{auto-optimize-request-approval}}

>[!ENDTABS]
