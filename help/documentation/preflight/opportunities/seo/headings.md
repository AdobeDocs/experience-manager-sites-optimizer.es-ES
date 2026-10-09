---
title: Auditoría de encabezados de comprobación previa
description: Obtenga información acerca de la auditoría Encabezados en Comprobación preliminar para AEM Sites Optimizer.
source-git-commit: af80dbb47a25b10cdbe55965fb7c4ce496448871
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 0%
---
# Auditoría de encabezados

La auditoría **Encabezados** revisa los subencabezados de la página (H2 a H6). Marca los títulos que no tienen texto y los títulos que omiten un nivel, como un H2 seguido directamente por un H4.

## Por qué es importante

Los encabezados proporcionan a una página su descripción. Los lectores los analizan para encontrar lo que necesitan, los usuarios de lectores de pantalla se desplazan por una página según sus encabezados y los motores de búsqueda los utilizan para comprender cómo se organiza el contenido. Un encabezado vacío agrega una parada en ese contorno sin nada y un nivel omitido hace que la estructura sea más difícil de seguir.

## Lo que comprueba la auditoría

La auditoría informa de una oportunidad para cada uno de los problemas siguientes:

* **Encabezado vacío:** un H2, H3, H4, H5 o H6 sin texto. Un encabezado que contenga solo espacios o solo una imagen cuenta como vacío.
* **Nivel de encabezado omitido:** un encabezado que es más de un nivel más profundo que el encabezado justo antes de él, por ejemplo, un H2 seguido de un H4 o un H1 seguido de un H3. La oportunidad se recoge en un encabezado más profundo.

Ambos se notifican con impacto moderado.

La auditoría [Metatags](./metatags.md) revisa los encabezados H1, y comprueba si falta un H1, si está vacío o si es demasiado largo y si hay más de un H1 en una página.

## Cómo se leen los encabezados

La auditoría lee la página que está editando y examina cada encabezado en el orden en que aparece:

* Se cuentan todos los encabezados, incluidos los del encabezado de página, los de navegación y pie de página, y los que están ocultos en la pantalla.
* Solo se marca el paso de un encabezado al siguiente. Una página cuyo primer encabezado es un H3 no está marcado para eso.
* Los encabezados pueden volver a subir cualquier número de niveles, por ejemplo, de un H4 a un H2.

## Sugerencias

Cada oportunidad incluye una recomendación y un consejo fijo para que el cambio se realice. La auditoría de encabezados no genera sugerencias de IA.

## Si un encabezado marcado le parece correcto

Si una oportunidad no coincide con lo que espera, suele ser por una de las siguientes razones:

* **El encabezado forma parte de la plantilla de página.** Los encabezados del encabezado, la navegación o el pie de página se comprueban junto con el contenido, por lo que un encabezado de pie de página que sea varios niveles más profundo que el último encabezado del contenido se puede marcar como un nivel omitido. Si se fija en la plantilla, se resuelve en todas las páginas que utilizan la plantilla.
* **El encabezado contiene solamente una imagen o un icono.** Un encabezado sin texto se muestra como vacío incluso cuando muestra una imagen. Agregue texto al encabezado o utilice un elemento que no sea de encabezado para la imagen.

## Limitaciones conocidas

* **No se tiene en cuenta la visibilidad:** los encabezados ocultos en la pantalla siguen marcados.
* **Páginas muy grandes:** páginas con más de 500 encabezados no se comprueban.

## Cómo resolver

Cuando la auditoría encuentra oportunidades, cada una describe el problema y el cambio recomendado.

* **Encabezado vacío:** agregue texto descriptivo al encabezado o elimínelo si no es necesario.
* **Nivel de encabezado omitido:** cambie el encabezado al siguiente nivel por debajo del encabezado anterior (por ejemplo, un H4 después de un H2 se convierte en un H3) o agregue el nivel que falta en el medio.

Use **Resaltar en la página** para encontrar el encabezado en el contenido. El modo en que se resalte el encabezado depende de dónde ejecute la comprobación preliminar:

* **Edge Delivery Services:** la comprobación preliminar se desplaza al encabezado y lo describe.
* **Editor de páginas de AEM Sites y Managed Services de Adobe (AMS):** La comprobación preliminar se desplaza al encabezado y lo describe. El resaltado requiere **Editar modo**.
* **Editor universal:** La comprobación preliminar selecciona el propio encabezado o el bloque editable más cercano que lo contiene. Para un encabezado de contenido que el editor no administra, como la navegación o un pie de página, la comprobación preliminar lo muestra, pero no puede seleccionar el encabezado en sí.

Para obtener más información, consulte [Resaltar en la página](../../audit-results.md#highlight-on-page).

Para obtener información sobre cómo revisar y resolver oportunidades, consulte [Resultados de auditoría en comprobaciones](../../audit-results.md).
