---
title: Resultados de auditoría en comprobación preliminar
description: Obtenga información sobre cómo interpretar los resultados de la auditoría de comprobaciones y la barra de progreso del usuario, navegar a los problemas de la vista previa y aplicar sugerencias generadas por IA.
source-git-commit: 10534d1fabdd88b11f45895d39bc1afd0d664ff1
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---


# Resultados de auditoría en comprobación preliminar

Cuando finaliza la auditoría, la comprobación preliminar muestra los resultados de la auditoría como oportunidades. Cada oportunidad está organizada por tipo e incluye recomendaciones para ayudarle a mejorar y optimizar la página. Dentro de una oportunidad, los problemas individuales identifican elementos específicos que se deben revisar o corregir.

En la parte superior del cuadro de diálogo Comprobaciones de AEM hay una barra de progreso del usuario que refleja los resultados generales de la auditoría. Muestra el porcentaje de oportunidades que pasaron sin problemas y la cantidad total de problemas encontrados en todas las oportunidades. La barra de progreso del usuario ayuda a los autores a medir el estado general de la página de un vistazo.

![Barra de progreso del usuario y oportunidades de auditoría en el cuadro de diálogo Comprobaciones de AEM](./assets/overview/hero.png){align="center"}

La barra tiene un código de colores:

* Rojo para **menos de 1/3** de oportunidades completadas
* Naranja para **1/3 a 2/3 completado**
* Verde para **más de 2/3 completado**
* Azul mientras las auditorías **siguen ejecutándose**

Consulte la [lista completa de tipos de oportunidades disponibles y cómo solucionarlos](./overview.md#preflight-opportunities).

## Navegar a problemas y aplicar sugerencias

Una vez finalizada la auditoría, puede pasar rápidamente a los problemas identificados y aplicar sugerencias generadas por IA directamente en la vista previa.

![Resalte de vista previa de comprobación preliminar y panel de sugerencias de IA](./assets/audit-results/highlight-issue.png){align="center"}

### Navegar a un problema

1. Seleccione un problema de la lista de problemas en el panel Comprobaciones.
1. La vista previa se desplaza automáticamente a y resalta la ubicación correspondiente en la página, por lo que puede revisar el problema en contexto sin buscarlo manualmente.

### Aplicar sugerencias generadas por IA

Para los problemas que incluyen recomendaciones generadas por IA, puede aplicar optimizaciones sugeridas directamente desde el panel de sugerencias.

#### Aplicación de una optimización

1. Revise la sugerencia generada por IA.
1. Seleccione **Aplicar optimización**.

El contenido recomendado se aplica directamente al contenido.

#### Editar antes de aplicar

Si es necesario realizar ajustes:

1. Modifique la sugerencia generada por IA en el panel de sugerencias.
1. Seleccione **Aplicar optimización**.

La versión editada se aplicará a la vista previa.
