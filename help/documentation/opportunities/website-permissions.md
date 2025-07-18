---
title: Documentación sobre la oportunidad de permisos del sitio web
description: Obtenga información sobre la oportunidad de permisos del sitio web y cómo utilizarla para aumentar la seguridad en el sitio web.
badgeSecurityPosture: label="Posición de seguridad" type="Caution" url="../../opportunity-types/security-posture.md" tooltip="Posición de seguridad"
source-git-commit: cb64a34b758de8f5dcea298014ddd0ba79a24c17
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 79%

---


# Oportunidad de permisos del sitio web

![Oportunidad de permisos del sitio web](./assets/website-permissions/hero.png){align="center"}

La oportunidad de permisos del sitio web optimiza los permisos del sitio web, lo que resulta crucial para mantener un entorno de AEM seguro y manejable. Esta oportunidad le permite restringir los controles de acceso, eliminando los permisos demasiado amplios, como, por ejemplo, `jcr:all` en rutas genéricas como `/` o `/content`, y alineando el acceso de usuario con el principio de privilegios mínimos. Al optimizar los permisos y eliminar las redundancias, puede reducir los riesgos de seguridad, mejorar la capacidad de mantenimiento y evitar futuras configuraciones incorrectas. Revise y actualice los permisos en la consola Permisos de seguridad de AEM o en su repositorio de código. Al hacerlo, se garantiza que los usuarios del servicio solo tengan el acceso que realmente necesitan.

## Identificación automática

![Identificación automática de los permisos del sitio web](./assets/website-permissions/auto-identify.png){align="center"}

La característica de **oportunidad Permisos del sitio web** identifica y enumera automáticamente lo siguiente

* **Usuario**: la cuenta de usuario con el permiso sospechoso.
* **Ruta**: usa las pestañas de la parte superior para organizar y filtrar oportunidades por estado.
* **Permiso** - El permiso sospechoso.
* **Problema**: indica el tipo de problema que afecta al permiso.

## Sugerencia automática

![Sugerencia automática de vulnerabilidades del sitio web](./assets/website-permissions/auto-suggest.png){align="center"}

La sugerencia automática ofrece recomendaciones generadas por la IA en el campo **Permisos sugeridos**, lo que le permite reemplazar cualquier permiso marcado por alternativas seguras.

## Optimización automática

[!BADGE Ultimate]{type=Positive tooltip="Ultimate"}

![Optimización automática de los permisos del sitio web](./assets/website-permissions/auto-optimize.png){align="center"}

Sites Optimizer Ultimate añade la posibilidad de implementar la optimización automática para las vulnerabilidades encontradas.

>[!BEGINTABS]

>[!TAB Implementar optimización]

{{auto-optimize-deploy-optimization-slack}}

>[!TAB Solicitar aprobación]

{{auto-optimize-request-approval}}

>[!ENDTABS]
