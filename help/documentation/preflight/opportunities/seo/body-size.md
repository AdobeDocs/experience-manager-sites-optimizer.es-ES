---
title: Auditoría de tamaño de cuerpo de comprobación preliminar
description: Obtenga información acerca de la auditoría de tamaño del cuerpo en Comprobación preliminar para AEM Sites Optimizer.
source-git-commit: c85cfb84b315b64ab5fcddfaa192ce78dd8d1a67
workflow-type: tm+mt
source-wordcount: '692'
ht-degree: 0%
---
# Auditoría del tamaño del cuerpo

La auditoría **Tamaño del cuerpo** revisa la cantidad de contenido del cuerpo en su página. Las páginas con muy poco contenido pueden ser menos útiles para los lectores y pueden clasificarse mal en los resultados de búsqueda. La auditoría marca las páginas que parecen tener demasiado poco texto.

## Por qué es importante

Los motores de búsqueda y los asistentes de IA dependen del texto de una página para comprender de qué se trata. Una página con poco texto o sin él se trata a menudo como de bajo valor, lo que puede dañar su clasificación y si aparece en las respuestas de IA.

## Lo que comprueba la auditoría

La auditoría mide la cantidad de texto creado en la página e informa de dos situaciones:

* **Sin contenido de texto:** la página se leyó correctamente pero no tiene texto en absoluto, por ejemplo, una página que es sólo una imagen.
* **Contenido delgado:** la página tiene algo de texto, pero es inferior al mínimo recomendado.

Una página con suficiente texto pasa y no se marca.

## Cómo se mide el contenido

La auditoría mide el texto del área de contenido principal de la página, no toda la página. Los elementos compartidos, como la navegación, los encabezados, los pies de página y las rutas de exploración, se repiten en todas las páginas y la auditoría los excluye, donde puede reconocerlos para que este Chrome compartido no enmascara contenido realmente delgado. La forma en que puede separar completamente el contenido de ese cromo depende del marcado de la página, como se describe a continuación.

Para buscar el contenido, la auditoría utiliza el primero de estos métodos que se aplica:

1. **`<main>`elementos (o `role="main"`).** Se trata como el área de contenido definitiva y solo se mide el texto que contiene (si una página tiene más de un elemento de este tipo, se combina el texto). Es la opción más confiable.
1. **Cuerpo de la página, con Chrome eliminado.** Si no hay `<main>` ni `role="main"`, la auditoría mide `<body>` después de quitar el valor de página chrome: navigation reconocido y el encabezado y pie de página de nivel de página, ya estén marcados con etiquetas HTML estándar, funciones de punto de referencia ARIA o los componentes estándar de encabezado, pie de página, ruta de exploración y navegación de AEM. Se mantiene un encabezado o pie de página que pertenece a una sección de contenido, como el título o el firma del artículo.
1. **Cuerpo de toda la página.** Si no hay ningún punto de referencia de contenido ni ningún cromo reconocido, se mide todo el `<body>`.

Unas cuantas notas sobre lo que cuenta. Las imágenes no aportan texto (no se mide el texto de `alt`), por lo que se puede marcar una página que sea principalmente de imágenes. El texto dentro de las etiquetas `<script>` y `<style>` nunca se cuenta, por lo que los scripts de análisis o de capa de datos no inflan la medición. Sin embargo, el texto normal del vínculo se cuenta como cualquier otro texto del contenido.

## Si una página marcada le parece correcta

Si una página está marcada como fina pero está seguro de que tiene contenido suficiente, es posible que la auditoría no haya separado claramente el contenido del Chrome que la rodea, como la navegación, los encabezados y los pies de página.

Si desea que la auditoría mida su página con más precisión, las siguientes opciones de marcado le ayudan a ello:

* La opción más confiable es envolver el contenido creado en un elemento `<main>` (o agregar `role="main"`). Esto elimina cualquier ambigüedad, por lo que solo se mide el contenido.
* Si no puede agregar `<main>`, las marcas de encabezado y pie de página estándar (`<header>`, `<footer>`) o las variaciones de fragmentos de experiencia de encabezado y pie de página estándar de AEM ayudan a la auditoría a reconocer y excluir su página con Chrome.
* Al marcar los encabezados y pies de página de nivel de sección dentro de `<article>`, `<section>` o `<aside>`, se evita que se borre el contenido que se encuentra en esos encabezados y pies de página.

## Limitaciones conocidas

La auditoría depende del marcado de la página para distinguir el contenido de Chrome. En una página que no tiene **ningún `<main>`, ningún marcador de referencia estándar ni componentes de encabezado/pie de página con nombres diferentes a los de las convenciones de plataforma**, es posible que se incluya texto cromado en la medición o que se excluya ocasionalmente texto creado. Agregar un elemento `<main>` al contenido resuelve todos estos casos. La auditoría no intenta adivinar el área de contenido a partir de la densidad del texto o el diseño visual; se basa en señales de marcado para que los resultados sean predecibles y repetibles.

## Cómo resolver

Cuando la auditoría encuentra oportunidades, cada una describe el problema y el cambio recomendado. Para obtener información sobre cómo revisar y resolver oportunidades, consulte [Resultados de auditoría en comprobaciones](../../audit-results.md).
