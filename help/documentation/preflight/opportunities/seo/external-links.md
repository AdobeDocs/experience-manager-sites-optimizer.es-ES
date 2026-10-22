---
title: Auditoría de vínculos externos de comprobación preliminar
description: Obtenga información acerca de la auditoría Vínculos externos en Comprobación preliminar para AEM Sites Optimizer.
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
source-git-commit: 59c097682899889aa2a5d76333f80cc58e28ff1e
workflow-type: tm+mt
source-wordcount: '753'
ht-degree: 0%
---
# Auditoría de vínculos externos

La auditoría **Vínculos externos** revisa los vínculos de la página que apuntan a otros sitios. La auditoría comprueba todos los vínculos externos de la página que está editando y marca los que están rotos, no son seguros o no se han podido comprobar automáticamente.

## Por qué es importante

Un vínculo externo roto es un callejón sin salida para el lector y una señal a los motores de búsqueda de que la página no está bien mantenida. Los vínculos externos también son los que tiene menos control: el otro sitio puede mover, cambiar el nombre o quitar una página en cualquier momento y el vínculo deja de funcionar silenciosamente. Comprobarlos antes de publicar detecta los vínculos que han quedado obsoletos desde que se agregaron por primera vez.

## Lo que comprueba la auditoría

La auditoría informa de una oportunidad para cada vínculo externo que tiene uno de los siguientes problemas:

* **Vínculo roto:** el vínculo devuelve `Status 404` o `Status 410`, o bien no se puede llegar a su sitio, por ejemplo porque el dominio ya no existe. De la misma manera, se informa de un vínculo que llega al error después de una redirección.
* **Vínculo no seguro:** el vínculo usa `http://` y el sitio no lo redirige a `https://`. Un vínculo que comienza como `http://` pero que se redirige a una página `https://` segura no está marcado. Actualice el vínculo para utilizar `https://`.
* **Vínculo no verificado:** La comprobación preliminar no pudo confirmar que el vínculo funciona, por ejemplo porque el sitio requiere inicio de sesión, bloquea las comprobaciones automatizadas, devuelve un error del servidor, no responde a tiempo o redirige demasiadas veces. Algunas redes sociales, como LinkedIn e Instagram, informan de páginas que faltan en comprobaciones automatizadas, por lo que los errores de páginas que faltan en esos sitios también se registran como no verificados. Es muy probable que estos vínculos funcionen en un explorador, por lo que Comprobaciones no los comunica como rotos. En su lugar, le pide que abra el vínculo y lo confirme.

Un vínculo puede ser inseguro y roto, o inseguro y no verificado, en cuyo caso se informa de ambas oportunidades. Un vínculo que se resuelve correctamente no se marca, aunque tenga redirecciones en camino.

## Qué vínculos se comprueban

Se comprueban todos los vínculos externos de la página. Un vínculo externo es cualquier vínculo cuyo host difiere de la página que está editando. El host es el nombre de dominio más cualquier puerto no estándar, como `:8443`. Los subdominios se cuentan como hosts diferentes, por lo que `blog.example.com` y `example.com` son externos a `www.example.com`. Los vínculos al mismo host, incluidos `http://` vínculos a su propio sitio, están cubiertos por la auditoría [Vínculos internos](./internal-links.md). Los vínculos en la exploración del sitio siempre se incluyen, ya que la opción **Mostrar vínculos de exploración del sitio** sólo se aplica a la auditoría de vínculos internos. Se omiten vínculos como `mailto:`, `tel:` y `javascript:`.

Se informa de cada vínculo una vez, incluso si aparece varias veces en la página o con diferentes anclajes, como `#pricing` y `#features`. La oportunidad resalta el primer lugar en el que aparece el vínculo.

Los vínculos que el verificador de vínculos de AEM ya ha marcado como no válidos se incluyen en la auditoría, aunque el editor elimine el vínculo en el que se puede hacer clic de la página. Se vuelven a comprobar en lugar de tener confianza, por lo que no se informa de ningún vínculo que haya comenzado a funcionar.

## Filtrado de los resultados

En la página de detalles, use el filtro que se encuentra junto al encabezado **Instancias** para mostrar solo algunas de las oportunidades:

| Filter | Oportunidades mostradas |
|---|---|
| **Todos** (predeterminado) | Cada oportunidad |
| **Roto** | Vínculos rotos |
| **Necesita verificación** | Vínculos no verificados y vínculos no seguros |

Si un vínculo tiene más de una oportunidad, como un vínculo no seguro que también está roto, cada oportunidad aparece bajo su propio filtro. Para obtener más información, consulte [Instancias de filtro](../../audit-results.md#filter-instances).

## Limitaciones conocidas

* **Direcciones privadas:** los vínculos a direcciones de red privadas o internas, como un sitio de intranet, no se comprueban y no se notifican.
* **Vista del lado del servidor:** La comprobación preliminar comprueba los vínculos externos desde los servidores de Adobe en lugar de hacerlo desde el explorador. Un sitio que se comporta de forma diferente en función de la ubicación, el inicio de sesión o la detección de bots puede devolver un resultado diferente al que ve en el explorador. Estos vínculos generalmente se registran como **Vínculo no verificado** en lugar de estar roto.

## Cómo resolver

Cuando la auditoría encuentra oportunidades, cada una describe el problema y el cambio recomendado, e identifica el vínculo involucrado. Use **Resaltar en la página** para ir al vínculo del contenido y abra la dirección URL en una nueva pestaña para confirmar el problema. Si se trata de un vínculo roto, actualícelo a la nueva ubicación de la página o elimínelo. Para un vínculo no verificado, confirme que se abre correctamente en el explorador. Para obtener información sobre cómo revisar y resolver oportunidades, consulte [Resultados de auditoría en comprobaciones](../../audit-results.md).
