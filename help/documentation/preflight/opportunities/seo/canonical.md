---
title: Auditoría canónica de comprobación preliminar
description: Obtenga información acerca de la auditoría canónica en Comprobación preliminar para AEM Sites Optimizer.
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
source-git-commit: 5c97431c2029e117339877219c2d6e4e30902a70
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%
---
# Auditoría canónica

La auditoría **Canonical** revisa el vínculo canónico en su página. El vínculo canónico es una etiqueta `<link rel="canonical">` en `<head>` de la página que indica la dirección URL preferida para el contenido de la página. La auditoría indica los vínculos canónicos que faltan, que se han configurado incorrectamente o que apuntan a algún lugar distinto de la propia página.

## Por qué es importante

Con frecuencia se puede acceder al mismo contenido en más de una dirección URL, por ejemplo, con y sin barra diagonal, con parámetros de seguimiento o con mayúsculas diferentes. Los motores de búsqueda tratan cada URL como una página independiente a menos que se indique lo contrario. El vínculo canónico les indica la dirección URL que prefiere, lo que les ayuda a agrupar los duplicados, combinar señales de clasificación como los vínculos entrantes en una dirección URL y mostrar esa dirección URL en los resultados de búsqueda.

Un vínculo canónico que está mal puede ser peor que ninguno. Los motores de búsqueda pueden omitir un vínculo canónico en el que no pueden confiar, como uno sin dirección URL, uno fuera de `<head>` o una de varias etiquetas en desacuerdo. Un vínculo canónico que señala a una página diferente pide a los motores de búsqueda que muestren esa página en lugar de la suya, lo que puede excluir la página de los resultados de búsqueda.

## Lo que comprueba la auditoría

La auditoría comprueba la existencia de problemas en tres ámbitos:

* **Tanto si la página tiene un vínculo canónico:** falta el vínculo canónico, como si la página tiene más de uno. Se informa de varios vínculos canónicos que apuntan a direcciones URL diferentes por separado, ya que los motores de búsqueda pueden ignorarlas todas.
* **Si la etiqueta está configurada correctamente:** la etiqueta está fuera de `<head>`, no tiene un atributo `href` o está vacía, o lleva un atributo como `hreflang`, `media` o `type` que puede hacer que los motores de búsqueda la ignoren.
* **Indica si la dirección URL es correcta:** la dirección URL canónica es relativa en lugar de absoluta, contiene letras mayúsculas en la ruta de acceso o en la cadena de consulta, utiliza un protocolo diferente (`http://` o `https://`) de la página o apunta a una página diferente de la que está editando.

## Comparación de la URL canónica

Las comprobaciones se ejecutan en páginas de vista previa, cuyo host suele ser diferente del sitio de producción. Para evitar marcar todas las páginas de vista previa, la auditoría no compara el host de la URL canónica con el host de la página. Cuando comprueba si el vínculo canónico apunta a la página en sí, compara únicamente la ruta de acceso de la dirección URL, de modo que `https://www.example.com/products/shoes` coincide con la página de vista previa `/products/shoes`. Una barra diagonal y un caso de letra en la ruta no se cuentan como diferencias para esta comprobación.

## Limitaciones conocidas

* **Dominio diferente:** una dirección URL canónica que señala a un sitio diferente no está marcada por la comprobación preliminar, porque los hosts de vista previa siempre difieren del sitio de producción. Confirme que el dominio de la URL canónica es el que espera.
* **Encabezado HTTP `Link`:** La comprobación preliminar solo comprueba la etiqueta canónica, no el encabezado HTTP `Link`. Una página que establece su dirección URL canónica solo en el encabezado se comunica como que falta el vínculo canónico.

## Cómo resolver

Cuando la auditoría encuentra oportunidades, cada una describe el problema y el cambio recomendado. En la mayoría de los casos, la página debe tener exactamente un vínculo canónico, en el `<head>`, con una dirección URL absoluta con una ruta de acceso en minúsculas que apunte a la propia página. Si la página señala intencionadamente a otra página como su versión canónica, por ejemplo, una copia duplicada o compatible con la impresora, puede dejarla tal cual. La auditoría seguirá informando. Para obtener información sobre cómo revisar y resolver oportunidades, consulte [Resultados de auditoría en comprobaciones](../../audit-results.md).
