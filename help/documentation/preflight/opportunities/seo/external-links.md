---
title: Auditoría de vínculos externos de comprobación preliminar
description: Obtenga información acerca de la auditoría Vínculos externos en Comprobación preliminar para AEM Sites Optimizer.
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
source-git-commit: 12279cd1468a3442709cb73a8691922598a33dab
workflow-type: tm+mt
source-wordcount: '1112'
ht-degree: 0%
---
# Auditoría de vínculos externos

La auditoría **Vínculos externos** revisa los vínculos de la página que apuntan a otros sitios. La auditoría comprueba todos los vínculos externos de la página que está editando y marca los que están rotos, no son seguros o no se han podido comprobar automáticamente.

## Por qué es importante

Un vínculo externo roto es un callejón sin salida para el lector y una señal a los motores de búsqueda de que la página no está bien mantenida. Los vínculos externos también son los que tiene menos control: el otro sitio puede mover, cambiar el nombre o quitar una página en cualquier momento y el vínculo deja de funcionar silenciosamente. Comprobarlos antes de publicar detecta los vínculos que han quedado obsoletos desde que se agregaron por primera vez.

## Lo que comprueba la auditoría

La auditoría clasifica los problemas en tres grupos:

* **Roto:** el vínculo falla para cada visitante en este momento y no se espera que se recupere.
* **Sin comprobar:** el vínculo falla para algunos visitantes, puede fallar solo temporalmente o no se puede comprobar.
* **Práctica recomendada:** el vínculo funciona, pero no debería crearse de esa manera, como un vínculo `http://` no seguro.

La auditoría informa de una oportunidad para cada vínculo externo que tiene uno de los siguientes problemas:

* **Vínculo roto:** el vínculo no funciona para nadie que lo abra. Las comprobaciones informan de que un vínculo se ha roto cuando:
  * no se puede acceder a su sitio, por ejemplo, porque el dominio ya no existe.
  * devuelve `Status 404` o `Status 410`.
  * devuelve `Status 405`, lo que significa que el sitio rechaza las solicitudes normales de página.
  * se redirige en un bucle o más de 20 veces. Los navegadores utilizan el mismo límite y muestran el error &quot;demasiadas redirecciones&quot;.

  De la misma manera, se informa de un vínculo que llega a uno de estos errores después de una redirección.
* **Vínculo no seguro:** el vínculo usa `http://` y la comprobación preliminar no lo vio redireccionar a `https://`, incluso cuando el sitio no respondió. Un vínculo que comienza como `http://` pero que se redirige a una página `https://` segura no está marcado. Actualice el vínculo para utilizar `https://`.
* **Vínculo no verificado:** La comprobación preliminar no pudo confirmar si el vínculo funciona, por lo que le pide que abra el vínculo y lo compruebe usted mismo. La oportunidad explica qué caso se aplica:
  * **Requiere inicio de sesión:** el vínculo devuelve `Status 401`. Los visitantes sin cuenta no pueden abrirlo, por lo que debe confirmar que está previsto.
  * **Bloquea comprobaciones automatizadas:** el vínculo devuelve `Status 403` o `Status 429`, o el sitio bloquea las solicitudes automatizadas de otra manera, como lo hace LinkedIn. Confirme que el vínculo se abre en un explorador.
  * **Sitios sociales y de inicio de sesión:** LinkedIn, Instagram, Facebook, X (Twitter), TikTok y Threads devuelven errores engañosos a solicitudes anónimas, por lo que un bucle de redireccionamiento de estos sitios `Status 404`, `Status 410`, `Status 405` se registra como no verificado en lugar de como interrumpido.
  * **Error de servidor:** el vínculo devuelve un error de servidor (`Status 5xx`) que persiste cuando la comprobación preliminar vuelve a comprobarlo. Reintentos de comprobación preliminar una vez antes de notificarlo. El error puede ser temporal, por lo que confirme que el vínculo funciona antes de publicar.
  * **No disponible por motivos legales:** el vínculo devuelve `Status 451` en la región Comprobaciones de comprobación preliminar de. Confirme que funciona para su audiencia.
  * **No hay respuesta a tiempo:** el sitio no respondió a tiempo, incluso después de que la comprobación preliminar se reintentó una vez. El sitio puede estar lento o temporalmente inactivo.

Un vínculo puede ser inseguro y roto, o inseguro y no verificado, en cuyo caso se informa de ambas oportunidades. Una cadena de redireccionamiento por sí sola no se marca si llega a una página de trabajo en un plazo de 20 redirecciones.

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
* **Límites de tiempo:** cada vínculo tiene su propio límite de tiempo, por lo que un sitio lento no impide que se comprueben otros vínculos. Cada vínculo de la página obtiene un resultado. Un vínculo que no responde a tiempo, incluso después de un reintento, aparece como **Vínculo no verificado** en lugar de roto.
* **Dominios excluidos:** la configuración de su sitio puede excluir dominios específicos de la comprobación. Los vínculos a un dominio excluido o a cualquiera de sus subdominios no se comprueban y no se informa de ellos.
* **Vista del lado del servidor:** La comprobación preliminar comprueba los vínculos externos desde los servidores de Adobe en lugar de hacerlo desde el explorador. Un sitio que se comporta de forma diferente en función de la ubicación, el inicio de sesión o la detección de bots puede devolver un resultado diferente al que ve en el explorador. Estos vínculos generalmente se registran como **Vínculo no verificado** en lugar de estar roto.

## Cómo resolver

Cuando la auditoría encuentra oportunidades, cada una describe el problema y el cambio recomendado, e identifica el vínculo involucrado. Use **Resaltar en la página** para ir al vínculo del contenido y abra la dirección URL en una nueva pestaña para confirmar el problema. A continuación, aproveche la oportunidad:

* **Vínculo roto:** actualice el vínculo a la nueva ubicación de la página, o reemplácelo o elimínelo. Para realizar un bucle de redireccionamiento, póngase en contacto con el propietario del otro sitio o vincule a un origen diferente.
* **Vínculo no seguro:** cambie el vínculo para que use `https://`, después de confirmar que la versión segura funciona.
* **Vínculo no verificado:** abra el vínculo en el explorador y confirme que muestra la página esperada. Para un vínculo que requiera inicio de sesión, confirme que se espera que los lectores tengan una cuenta de. Si se produce un error en el servidor, vuelva a comprobar el vínculo antes de publicar. Si el vínculo no funciona, trátelo como roto.

Para obtener información sobre cómo revisar y resolver oportunidades, consulte [Resultados de auditoría en comprobaciones](../../audit-results.md).
