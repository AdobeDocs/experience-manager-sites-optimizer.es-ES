---
title: Documentación de oportunidad de permisos de sitio web
description: Obtenga información acerca de la oportunidad de permisos del sitio web y cómo utilizarla para aumentar la seguridad de en el sitio web.
badgeSecurityPosture: label="Posición de seguridad" type="Caution" url="../../opportunity-types/security-posture.md" tooltip="Posición de seguridad"
source-git-commit: 5d1ae616ddde74f69b73ba5b44297c14b2dea36b
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 2%

---


# Oportunidad de permisos de sitio web

![Oportunidad de permisos de sitio web](./assets/website-permissions/hero.png){align="center"}

La oportunidad de permisos del sitio web optimiza los permisos del sitio web, lo que resulta crucial para mantener un entorno de AEM seguro y manejable. Esta oportunidad le permite restringir los controles de acceso eliminando los permisos demasiado amplios, como `jcr:all` en rutas genéricas como `/` o `/content`, y alineando el acceso de usuario con el principio de privilegios mínimos. Al optimizar los permisos y eliminar las redundancias, puede reducir los riesgos de seguridad, mejorar la capacidad de mantenimiento y evitar futuras configuraciones incorrectas. Realice acciones revisando y actualizando permisos en la consola Permisos de seguridad de AEM o en su repositorio de código, asegurándose de que los usuarios del servicio solo tengan el acceso que realmente necesitan.

## Identificar automáticamente

![Identificar automáticamente los permisos del sitio web](./assets/website-permissions/auto-identify.png){align="center"}

La característica de **oportunidad de Permisos de sitios web** identifica y enumera automáticamente

* **Usuario** - La cuenta de usuario con el permiso sospechoso.
* **Ruta**: la ruta de acceso de AEM afectada por el permiso.
* **Permiso** - El permiso que es sospechoso.
* **Problema**: indica el tipo de problema que afecta el permiso.

## Sugerir automáticamente

![Sugerir automáticamente vulnerabilidades de sitios web](./assets/website-permissions/auto-suggest.png){align="center"}

La sugerencia automática proporciona recomendaciones generadas por IA en el campo **Permisos sugeridos**, lo que le permite reemplazar cualquier permiso marcado con alternativas seguras.

## Optimizar automáticamente [!BADGE Ultimate]{type=Positive tooltip="Ultimate"}

![Optimizar automáticamente los permisos del sitio web](./assets/website-permissions/auto-optimize.png){align="center"}

Sites Optimizer Ultimate añade la capacidad de implementar la optimización automática para las vulnerabilidades encontradas.

>[!BEGINTABS]

>[!TAB Implementar optimización]

{{auto-optimize-deploy-optimization-slack}}

>[!TAB Solicitar aprobación]

{{auto-optimize-request-approval}}

>[!ENDTABS]
