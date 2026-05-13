---
title: Documentación sobre la oportunidad de configuración de CORS
description: Obtenga información sobre la oportunidad de configuración de CORS y aprenda a identificar y corregir las vulnerabilidades de seguridad del sitio.
badgeSecurityPosture: label="Posición de seguridad" type="Caution" url="../../opportunity-types/security-posture.md" tooltip="Posición de seguridad"
TQID: https://experienceleague.adobe.com/z-8fvRSLN71AnJ4Y6n9TnHGHoOEAAjt8AbVJY9RG-C0
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 252f5292d6dc62711b4ebeb8ce5a2707857fd674
workflow-type: ht
source-wordcount: 199
ht-degree: 100%

---

# Oportunidad de configuración de CORS

![Oportunidad de configuración de CORS](./assets/cors-configuration/hero.png){align="center"}

Configurar correctamente CORS (Cross-Origin Resource Sharing) es esencial para proteger las aplicaciones web frente al acceso no autorizado a los datos. Cuando el encabezado `Access-Control-Allow-Origin` está establecido en `*`, cualquier dominio puede solicitar y recibir respuestas, lo que podría exponer la información confidencial a los atacantes. Esta funcionalidad presenta una oportunidad para reforzar la seguridad implementando una lista de permitidos controlada de dominios de confianza o la desactivación de CORS donde no es necesario. Garantizar una configuración de CORS segura ayuda a proteger el contenido privado y, al mismo tiempo, mantiene un acceso sin problemas para los usuarios autorizados.

## Identificación automática

![Identificación automática de la oportunidad de configuración de CORS](./assets/cors-configuration/auto-identify.png){align="center"}

La identificación automática analiza su sitio web en busca de configuraciones incorrectas de CORS y detecta las direcciones URL que son susceptibles de acceso no autorizado. Estas direcciones URL se enumeran en la tabla de arriba, junto con los siguientes detalles:

* **Prefijo de página**: el prefijo de ruta de URL que es vulnerable ante una configuración incorrecta de CORS.
* **Ejemplo de página**: Un ejemplo de URL susceptible de acceso no autorizado.

## Sugerencia automática

![Sugerencia automática de la oportunidad de configuración de CORS](./assets/cors-configuration/auto-suggest.png){align="center"}

La sugerencia automática proporciona **Archivos de código de aplicación** y sus **Líneas** que se revisarán y que pueden estar configurando políticas CORS laxas.


## Optimización automática

[!BADGE Ultimate]{type=Positive tooltip="Ultimate"}

>[!BEGINTABS]

>[!TAB Implementar optimización]

{{auto-optimize-deploy-optimization-slack}}

>[!TAB Solicitar aprobación]

{{auto-optimize-request-approval}}

>[!ENDTABS]
