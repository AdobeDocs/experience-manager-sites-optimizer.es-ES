---
title: Auditoría de metaetiquetas de comprobación preliminar
description: Obtenga información acerca de la auditoría Etiquetas de metadatos en Comprobación preliminar para AEM Sites Optimizer.
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
source-git-commit: 59c097682899889aa2a5d76333f80cc58e28ff1e
workflow-type: tm+mt
source-wordcount: '801'
ht-degree: 1%
---
# Auditoría de metaetiquetas

La auditoría **Etiquetas de metadatos** revisa el título de la página, la descripción de la meta y el encabezado principal (H1). Indica cualquiera de ellas que falta, que están vacías o que no tienen la longitud recomendada, e indica páginas con más de un encabezado H1.

## Por qué es importante

El título de la página y la metadescripción suelen ser lo que la gente ve para su página en los resultados de búsqueda: el título como titular en el que se puede hacer clic y la descripción como resumen debajo de ella. Un título o una descripción que falte o que no tenga el tamaño adecuado se pueden cortar o reemplazar con texto que el motor de búsqueda elija en la página. El encabezado H1 indica a los lectores y motores de búsqueda de qué se trata la página principalmente, por lo que una página debe tener un H1 claro.

## Lo que comprueba la auditoría

La auditoría informa de una oportunidad para cada uno de los problemas siguientes:

* **Título de página:** ausente, vacío, demasiado corto o más largo que la longitud ideal.
* **Descripción de Meta:** falta, está vacía, es demasiado corta o tiene una longitud superior a la ideal.
* **Encabezado H1:** ausente, vacío, con una longitud superior a la ideal o más de un H1 en la página.

Un valor con algunos caracteres sobre la longitud ideal se registra como **por encima de la longitud ideal**, y uno sobrepasa el máximo de la auditoría como **demasiado largo**. La comprobación preliminar no tiene un umbral demasiado largo para los títulos de las páginas.

| Etiqueta | Longitud ideal | Longitud superior a la ideal | Demasiado largo |
|---|---|---|---|
| Título de la página | de 40 a 60 caracteres | Más de 60 caracteres | - |
| Descripción de Meta | De 140 a 160 caracteres | De 161 a 175 caracteres | Más de 175 caracteres |
| Encabezado H1 | Hasta 70 caracteres | de 71 a 75 caracteres | Más de 75 caracteres |

Estos intervalos son directrices recomendadas, no requisitos de motores de búsqueda. Las comprobaciones las utilizan para decidir cuándo informar de una oportunidad.

## Lectura de los valores

La auditoría lee la página que está editando: el texto del elemento `<title>`, el contenido de la etiqueta `<meta name="description">` y el texto visible del primer elemento `<h1>`, incluido cualquier texto en negrita o cursiva que contenga.

**Falta** una etiqueta cuando la página no la tiene y **está vacía** cuando está ahí pero no tiene texto visible. Las longitudes cuentan todos los caracteres, incluidos los espacios y la puntuación. Solo se comprueba la longitud del primer H1. Cuando una página tiene más de un H1, cada uno se muestra como una instancia independiente, por lo que puede buscar y cambiar los encabezados adicionales.

## Sugerencias

Cada oportunidad incluye una recomendación, como la longitud ideal para la etiqueta o un H1 en una página.

El título de la página, la metadescripción y las oportunidades H1 también pueden incluir una sugerencia generada por IA y escrita desde el contenido propio de la página. Solo se muestra una sugerencia si se ajusta a la longitud ideal. Revise y edite todas las sugerencias antes de utilizarlas.

Cuando una oportunidad H1 no tiene sugerencia de IA, su sugerencia es un consejo fijo en su lugar, como acortar el encabezado o cambiar los encabezados H1 adicionales a H2. Cuando una oportunidad de título de página o metadescripción no tiene sugerencia de IA, la comprobación preliminar muestra que no hay sugerencias disponibles.

## Si un valor marcado le parece correcto

En las páginas de Edge Delivery Services, un título de página o una metadescripción que no haya establecido se rellenan automáticamente desde el primer encabezado y el primer párrafo de la página. A menudo tienen una longitud inferior a la ideal, por lo que la página se marca. Configurar su propio título y descripción en los metadatos de la página resuelve esto.

## Limitaciones conocidas

* **Otras etiquetas Head no están marcadas,** como las etiquetas Open Graph para compartir en redes sociales o la etiqueta robots.
* **La longitud se cuenta en caracteres:** los motores de búsqueda acortan los títulos y las descripciones en función del espacio que ocupan en pantalla, por lo que un valor dentro de la longitud ideal se puede acortar en los resultados de búsqueda.
* **Los idiomas sin espacios entre palabras:** en páginas en idiomas como chino, japonés o coreano, un valor que se lea bien se puede marcar y las sugerencias de IA pueden quedar fuera de la longitud ideal.

## Cómo resolver

Cada oportunidad describe el problema y el cambio recomendado, y muestra el valor actual del título de la página o la metadescripción.

* **Título de página y metadescripción:** actualícelos donde el sitio los establezca, por ejemplo, en las propiedades de página de AEM Sites o en los metadatos de página de Edge Delivery Services. Estas etiquetas están en el encabezado de la página, por lo que **Resaltar en la página** no está disponible para ellas.
* **Encabezado H1:** use **Resaltar en la página** para encontrar el encabezado en el contenido. En Edge Delivery Services, el editor de páginas de AEM Sites y Adobe Managed Services (AMS), la comprobación preliminar se desplaza al encabezado y lo describe; el editor de páginas y AMS requieren **modo de edición**. En el editor universal, Comprobaciones selecciona el encabezado o el bloque editable más cercano que lo contiene. Se muestra un encabezado en la navegación o un pie de página, pero no se puede seleccionar. Para obtener más información, consulte [Resaltar en la página](../../audit-results.md#highlight-on-page).

Para obtener información sobre cómo revisar y resolver oportunidades, consulte [Resultados de auditoría en comprobaciones](../../audit-results.md).
