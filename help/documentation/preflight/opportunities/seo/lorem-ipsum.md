---
title: Auditoría de IPSUM de Lorem de comprobación preliminar
description: Obtenga información acerca de la auditoría Lorem ipsum en Comprobación preliminar para AEM Sites Optimizer.
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
source-git-commit: 587aec4eb905a2b1ced746590ca25b8ed97b16c1
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 1%
---
# Lorem ipsum audit

La auditoría **Lorem ipsum** detecta el texto de marcador de posición que ha quedado en el contenido de la página.

## Por qué es importante

La publicación de una página con texto de marcador de posición hace que los lectores no tengan la apariencia final. Los motores de búsqueda pueden indexar el texto del marcador de posición y mostrarlo en los resultados de búsqueda, y las plataformas sociales pueden mostrarlo en las vistas previas de los vínculos. El texto de marcador de posición suele ocultarse, por ejemplo, en el texto alternativo de la imagen o en las etiquetas de accesibilidad. Cuando lo es, las personas que utilizan lectores de pantalla u otras tecnologías de asistencia pueden escucharlo, aunque no aparezca en la página.

## Lo que comprueba la auditoría

La auditoría informa de cada lugar de la página donde aparece el texto de marcador de posición. Comprueba el texto visible de la página, además de varios lugares en los que puede que no sea visible inmediatamente o en absoluto:

* texto alternativo de imagen
* etiquetas y descripciones de accesibilidad
* marcadores de posición de campo de formulario
* información sobre herramientas
* el título de la página
* metadatos, como la metadescripción y las etiquetas de uso compartido en redes sociales

El código que no se presenta a los usuarios, como scripts y estilos, no está marcado.

## Coincidencia del texto

La auditoría busca la frase &quot;lorem ipsum&quot; en cualquier combinación de letras mayúsculas y minúsculas. También encuentra la frase cuando las palabras se dividen entre líneas o elementos, o no tienen espacio entre ellos. Si la frase aparece más de una vez en el mismo elemento o atributo, ese lugar se comunica una vez.

## Limitaciones conocidas

* **Solo &quot;lorem ipsum&quot;:** no se detecta ningún otro texto de marcador de posición, como &quot;TBD&quot; u otras palabras de relleno latino sin &quot;lorem ipsum&quot;.
* **Resaltar en la página:** no está disponible para el título de página o los metadatos, ya que no aparecen en la página. Utilice el texto que se muestra en la oportunidad para encontrarlos.

## Cómo resolver

Cuando la auditoría encuentra oportunidades, cada una identifica dónde aparece el texto del marcador de posición. Cuando esté disponible, usa **Resaltar en la página** para saltar al texto del contenido. Reemplace el marcador de posición por contenido real o elimínelo. Para las etiquetas de texto alternativo y accesibilidad, escriba una descripción de la imagen o del control. Para obtener información sobre cómo revisar y resolver oportunidades, consulte [Resultados de auditoría en comprobaciones](../../audit-results.md).
