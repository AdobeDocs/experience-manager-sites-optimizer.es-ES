---
title: Documentación de oportunidad de configuración CORS
description: Conozca la oportunidad de configuración de CORS y para identificar y corregir las vulnerabilidades de seguridad del sitio.
badgeSecurityPosture: label="Posición de seguridad" type="Caution" url="../../opportunity-types/security-posture.md" tooltip="Posición de seguridad"
source-git-commit: ab2d75b1d986d83e3303e29a25d2babd1598394a
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 3%

---


# Oportunidad de configuración de CORS

![Oportunidad de configuración de CORS](./assets/cors-configuration/hero.png){align="center"}

La correcta configuración del Intercambio de Recursos de Origen Cruzado (CORS) es esencial para proteger las aplicaciones web contra el acceso no autorizado a los datos. Cuando el encabezado `Access-Control-Allow-Origin` está establecido en `*`, cualquier dominio puede solicitar y recibir respuestas, lo que podría exponer la información confidencial a los atacantes. Esto presenta una oportunidad para reforzar la seguridad mediante la implementación de una lista de permitidos controlada de dominios de confianza o la desactivación de CORS donde no es necesario. Garantizar una configuración CORS segura ayuda a proteger el contenido privado y, al mismo tiempo, mantiene un acceso sin problemas para los usuarios autorizados.

## Identificar automáticamente

![Identificar automáticamente la oportunidad de configuración de CORS](./assets/cors-configuration/auto-identify.png){align="center"}

La identificación automática analiza su sitio web en busca de configuraciones incorrectas de CORS y detecta las direcciones URL que son susceptibles de acceso no autorizado. Estas direcciones URL se enumeran en la tabla superior, junto con los siguientes detalles:

* **Prefijo de página**: el prefijo de ruta de URL que es vulnerable a una configuración incorrecta de CORS.
* **Ejemplo de página**: URL de ejemplo susceptible al acceso no autorizado.

## Sugerir automáticamente

![Sugerencia automática de la oportunidad de configuración de CORS](./assets/cors-configuration/auto-suggest.png){align="center"}

La sugerencia automática proporciona **archivos de código de aplicación** y sus **líneas** que se revisarán y que pueden estar configurando políticas CORS laxas.


## Optimizar automáticamente [!BADGE Ultimate]{type=Positive tooltip="Ultimate"}



>[!BEGINTABS]

>[!TAB Implementar optimización]

{{auto-optimize-deploy-optimization-slack}}

>[!TAB Solicitar aprobación]

{{auto-optimize-request-approval}}

>[!ENDTABS]
