---
solution: Experience Manager
product: adobe experience manager
type: Documentation
description: Documentación de AEM Sites Optimizer.
index: y
git-repo: https://github.com/AdobeDocs/experience-manager-sites-optimizer.es-ES
feature-set: Experience Manager Assets,Experience Manager Sites,Experience Manager, Experience Manager Forms, Experience Manager Cloud Manager
cloud: Experience Cloud
recommendations: noDisplay
source-git-commit: eda941a0096e32f61b45d69d89a3ee5b1a0c7e4b
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 53%

---


# Metadatos para uso interno

Los metadatos del sistema de creación de GitHub son jerárquicos y se definen con los siguientes niveles crecientes de precedentes.

1. metadata.md
1. TDC
1. Artículo

Los metadatos definidos en el archivo metadata.md se aplican a todo el repositorio, pero se pueden sobrescribir en los niveles de TDC y de artículo. Cualquier anulación de los metadatos debe realizarse en el nivel más bajo posible.

Los metadatos del repositorio experience-manager-cloud-service.en son los mínimos requeridos.

metadata.md

* `product`
* `git-repo`
* `index`
* `solution-title`
* `solution-hub-url`
* `getting-started-title`
* `getting-started-url`
* `tutorials-title`
* `tutorials-url`

TDC

* `sub-product`
* `user-guide-title`

Artículo

* `title`
* `description`
* `contentOwner` (solo en contenido de recursos principales bajo `/help/assets`)

