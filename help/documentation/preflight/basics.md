---
title: Conceptos básicos de comprobación preliminar
description: Obtenga información acerca de los conceptos básicos de las comprobaciones y cómo utilizar su interfaz.
source-git-commit: 85b592d5486ed5197d7bd8214c31732465c41f78
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---


# Conceptos básicos de comprobación preliminar

![Preflight](./assets/overview/hero.png){align="center"}

Las comprobaciones le ayudan a identificar oportunidades para mejorar las páginas web antes de publicarlas. La extensión de comprobaciones identifica las oportunidades realizando auditorías en el contenido y muestra los resultados en un panel para que pueda solucionarlas antes de publicar.

## Donde aparece la comprobación preliminar

Las comprobaciones están disponibles en diferentes entornos de creación:

* **Editor universal** - La extensión de comprobación preliminar aparece en el **carril lateral**. Selecciónelo para iniciar una auditoría de la página actual.
* **Creación basada en documentos**: a través de Sidekick o bookmarklet, ejecute la herramienta de comprobación preliminar en el contenido de la página de vista previa para ver la lista de oportunidades.
* **Editor de páginas de AEM Sites**: use el bookmarklet Preflight en el explorador para iniciar una auditoría.

Para obtener instrucciones de configuración, consulte [Configuración de comprobación preliminar](./setup.md).

## Inicio de una auditoría

Para ejecutar la comprobación preliminar:

1. Abra la página que desee auditar en el entorno de creación (editor universal, vista previa basada en documentos o editor de páginas de AEM Sites).
2. Abra el panel Comprobaciones: seleccione la extensión de comprobaciones en el carril lateral o haga clic en el botón Comprobaciones de Sidekick.
3. La comprobación preliminar analiza la página y muestra las oportunidades que se han encontrado para mejorarla.

## Resultados de auditoría

Cuando finaliza la auditoría, la comprobación preliminar muestra las oportunidades que ha encontrado. Cada oportunidad está organizada por tipo e incluye detalles sobre cómo resolver el problema.

En la parte superior del cuadro de diálogo Comprobaciones de AEM hay una barra de progreso del usuario que refleja los resultados generales de la auditoría. Muestra el porcentaje de oportunidades que pasaron sin problemas y la cantidad total de problemas encontrados en todas las oportunidades. La barra de progreso del usuario ayuda a los autores a medir el estado general de la página de un vistazo. La barra está codificada por colores: rojo para menos de un tercio de las oportunidades completadas, naranja para un tercio a dos tercios completados y verde para más de dos tercios completados. Mientras las auditorías siguen ejecutándose, la barra de progreso se muestra en azul.

## Acerca de las oportunidades de comprobación preliminar

Las comprobaciones evalúan varios aspectos del contenido, incluida la accesibilidad, los metadatos, los vínculos y la legibilidad. Consulte [Oportunidades de comprobación preliminar](./overview.md) para obtener una lista completa de los tipos de oportunidades disponibles y cómo solucionarlos.