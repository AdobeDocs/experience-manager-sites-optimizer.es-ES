---
solution: Experience Manager
product_v2: id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
product: adobe experience manager
landing-page-name: experience-manager
landing-page-breadcrumb-title: AEM
type: Documentation
description: Documentación de AEM Sites Optimizer.
index: true
git-repo: https://github.com/AdobeDocs/experience-manager-sites-optimizer.en
feature-set: Experience Manager Assets,Experience Manager Sites,Experience Manager, Experience Manager Forms, Experience Manager Cloud Manager
cloud: Experience Cloud
recommendations: noDisplay
source-git-commit: ffd43deb5e5e763bd9a0f2cec87ae0ebd8cbe6c3
workflow-type: tm+mt
source-wordcount: 85
ht-degree: 2%

---


# Metadatos para uso interno

El sistema de creación de GitHub organiza los metadatos de forma jerárquica, utilizando los siguientes niveles crecientes de precedentes.

1. metadata.md
1. ToC
1. Artículo

Los metadatos definidos en el archivo metadata.md se aplican a todo el repositorio, pero se pueden sobrescribir en los niveles de TDC y de artículo. Cualquier anulación de los metadatos debe realizarse en el nivel más bajo posible.

Los metadatos del repositorio `experience-manager-cloud-service.en` son los mínimos requeridos.

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

ToCs

* `sub-product`
* `user-guide-title`

Artículo

* `title`
* `description`
* `contentOwner` (solo en contenido de recursos principales bajo `/help/assets`)

