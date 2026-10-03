---
title: Auditoría de vínculos externos de comprobación preliminar
description: Obtenga información acerca de la auditoría Vínculos externos en Comprobación preliminar para AEM Sites Optimizer.
source-git-commit: 8a465f3ef54dbd295255f326eda2e8f37a114ace
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 0%
---
# Auditoría de vínculos externos

La auditoría **Vínculos externos** revisa los vínculos de la página que apuntan a otros sitios. La auditoría comprueba todos los vínculos externos de la página que está editando y marca los que están rotos, no son seguros o no se han podido comprobar automáticamente.

## Por qué es importante

Un vínculo externo roto es un callejón sin salida para el lector y una señal a los motores de búsqueda de que la página no está bien mantenida. Los vínculos externos también son los que tiene menos control: el otro sitio puede mover, cambiar el nombre o quitar una página en cualquier momento y el vínculo deja de funcionar silenciosamente. Comprobarlos antes de publicar detecta los vínculos que han quedado obsoletos desde que se agregaron por primera vez.

## Lo que comprueba la auditoría

La auditoría informa de una oportunidad para cada vínculo externo que tiene uno de los siguientes problemas:

* **Vínculo interrumpido:** No se puede alcanzar el vínculo o devuelve un error como `Status 404`, `Status 410` o un error del servidor `5xx`. De la misma manera, se informa de un vínculo que llega al error después de una redirección. Un vínculo cuyo sitio no responde en absoluto, por ejemplo porque el dominio ya no existe, también se comunica como roto.
* **Vínculo no seguro:** el vínculo usa `http://` y el sitio no lo redirige a `https://`. Un vínculo que comienza como `http://` pero que se redirige a una página `https://` segura no está marcado. Actualice el vínculo para utilizar `https://`.
* **Vínculo no verificado:** el sitio respondió pero rechazó la comprobación automatizada, por ejemplo porque requiere el inicio de sesión (`Status 401` o `Status 403`), limita las solicitudes automatizadas (`Status 429`) o bloquea bots, como lo hacen algunas redes sociales. También se informa de este modo de un vínculo que redirige demasiadas veces para seguirlo. Es muy probable que estos vínculos funcionen en un explorador, por lo que Comprobaciones no los comunica como rotos. En su lugar, le pide que abra el vínculo y lo confirme usted mismo, y lo comunica con un bajo impacto.

Un vínculo puede ser inseguro y roto, o inseguro y no verificado, en cuyo caso se informa de ambas oportunidades. Un vínculo que se resuelve correctamente no se marca, aunque tenga redirecciones en camino.

## Comprobación de los vínculos

Un vínculo externo es cualquier vínculo cuyo host difiere de la página que está editando. El host es el nombre de dominio más cualquier puerto no estándar, como `:8443`. Los subdominios se cuentan como hosts diferentes, por lo que `blog.example.com` y `example.com` son externos a `www.example.com`. No importa si el vínculo usa `http://` o `https://`. Los vínculos al mismo host, incluidos `http://` vínculos a su propio sitio, están cubiertos por la auditoría [Vínculos internos](./internal-links.md). Se omiten vínculos como `mailto:`, `tel:` y `javascript:`.

El explorador no puede leer el estado de un vínculo en otro sitio, por lo que Comprobación preliminar comprueba los vínculos externos desde los servidores de Adobe en lugar de hacerlo desde la sesión de creación. Cada vínculo se comprueba una vez, incluso si aparece varias veces en la página o con diferentes anclajes, como `#pricing` y `#features`. La oportunidad resalta el primer lugar en el que aparece el vínculo.

Los vínculos que el verificador de vínculos de AEM ya ha marcado como no válidos se incluyen en la auditoría, aunque el editor elimine el vínculo en el que se puede hacer clic de la página. A continuación, se vuelven a comprobar en lugar de asumir una confianza, por lo que no se informa de ningún vínculo que haya comenzado a funcionar.

## Limitaciones conocidas

* **Número de vínculos:** se comprueban hasta 50 vínculos externos distintos por página. Los vínculos que superan ese límite no están marcados.
* **Límite de tiempo:** cada vínculo tiene un tiempo de espera de 10 segundos, y toda la comprobación tiene un límite de tiempo para que la comprobación preliminar siga respondiendo. Un sitio que no responde dentro del tiempo de espera se comunica como roto. En páginas con muchos sitios lentos, es posible que algunos vínculos no se comprueben en una ejecución determinada.
* **Direcciones privadas:** los vínculos que se dirigen a direcciones de red privadas o internas, como un sitio de intranet, no se comprueban y no se notifican.
* **Vista del lado del servidor:** debido a que los vínculos se comprueban desde los servidores de Adobe, un sitio que se comporta de manera diferente en función de la ubicación, el inicio de sesión o la detección de bots puede devolver un resultado diferente del que se ve en el explorador. Estos vínculos generalmente se registran como **Vínculo no verificado** en lugar de estar roto.

## Cómo resolver

Cuando la auditoría encuentra oportunidades, cada una describe el problema y el cambio recomendado, e identifica el vínculo involucrado. Use **Resaltar en la página** para ir al vínculo del contenido y abra la dirección URL en una nueva pestaña para confirmar el problema. Si se trata de un vínculo roto, actualícelo a la nueva ubicación de la página o elimínelo. Para un vínculo no verificado, confirme que se abre correctamente en el explorador. Para obtener información sobre cómo revisar y resolver oportunidades, consulte [Resultados de auditoría en comprobaciones](../../audit-results.md).
