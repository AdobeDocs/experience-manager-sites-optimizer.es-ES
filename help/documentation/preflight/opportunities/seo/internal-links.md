---
title: Auditoría de vínculos internos de comprobación preliminar
description: Obtenga información acerca de la auditoría Vínculos internos en Comprobación preliminar para AEM Sites Optimizer.
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
source-git-commit: ae16300fdfd525dc5efead2f165d5a238b5ea6e1
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 0%
---
# Auditoría de vínculos internos

La auditoría **Vínculos internos** revisa los vínculos de la página que apuntan a su propio sitio. La auditoría comprueba cada vínculo interno de la página que está editando e indica los que están rotos, no son seguros o apuntan a un lugar que un visitante no puede seguir.

## Por qué es importante

Un vínculo interno roto es un callejón sin salida para el lector y un rastree desperdiciado para un motor de búsqueda, que no pasa ningún valor a la página a la que estaba destinado. Los vínculos internos también son el tipo más fácil de romper por accidente: una página se mueve o se le cambia el nombre, y cada vínculo a ella deja de funcionar silenciosamente. Como todos los vínculos están en su propio sitio, también son los que puede corregir usted mismo.

## Lo que comprueba la auditoría

La auditoría informa de una oportunidad para cada vínculo interno que tiene uno de los siguientes problemas:

* **Vínculo roto:** el vínculo devuelve un error, como `Status 404` o `Status 500`. De la misma manera, se informa de un vínculo que llega al error después de una redirección.
* **Vínculo no seguro:** el vínculo usa `http://` en lugar de `https://`. Cuando funciona la versión segura de la misma dirección URL, Comprobación preliminar la ofrece como sugerencia.
* **URL del editor:** el vínculo apunta a una URL del editor de AEM en lugar de a la página de contenido. El vínculo funciona mientras crea, lo que hace que sea fácil pasarlo por alto, pero todos los visitantes aterrizan en la interfaz de creación. Las comprobaciones sugieren la dirección URL de contenido.
* **Falta el fragmento:** el vínculo apunta a un anclaje, como `#pricing`, que la página de destino no tiene. La página sigue abriéndose, pero el lector llega en la parte superior de la misma en lugar de la sección a la que se refería, por lo que se informa de que este hecho tiene un impacto menor que el de un vínculo roto. Si la página tiene el mismo anclaje con mayúsculas de forma diferente, la comprobación preliminar sugiere el anclaje corregido. Si la página de destino en sí está rota, se mostrará como **vínculo roto**.
* **Vínculo no verificado:** se agotó el tiempo de espera de la comprobación o se produjo un error de red. La comprobación preliminar no puede comprobar si el vínculo funciona, por lo que le pide que lo compruebe usted mismo en lugar de informar de que está dañado.

Un vínculo que se resuelve correctamente no se marca, aunque tenga varias redirecciones en camino. Tampoco lo es un vínculo que redirija a un sitio diferente, ya que ya no es un vínculo interno.

## Comprobación de los vínculos

La auditoría comprueba los vínculos de la sesión de creación para que los vea como ha iniciado sesión para verlos. Una página que solo existe en la instancia de autor se resuelve correctamente en lugar de parecer rota.

Los vínculos que el verificador de vínculos de AEM ya ha marcado como no válidos se incluyen en la auditoría, aunque el editor elimine el vínculo en el que se puede hacer clic de la página. A continuación, se vuelven a comprobar en lugar de asumir una confianza, por lo que no se informa de ningún vínculo que haya comenzado a funcionar.

Se informa de una oportunidad por cada lugar donde aparece un vínculo, por lo que un vínculo incorrecto utilizado en tres puntos le ofrece tres instancias que corregir, cada una de las cuales resalta su propio punto en la página. Cuando uno de esos puntos tiene más de un problema, la comprobación preliminar los muestra juntos en una tarjeta.

## Incluir vínculos de navegación del sitio

De forma predeterminada, la auditoría Vínculos internos omite los vínculos de navegación del sitio. Estos vínculos no se comprueban ni se incluyen en el informe. Un vínculo en el cuerpo de la página sigue activado aunque la misma URL también aparezca en un menú.

Un vínculo se cuenta como navegación si el vínculo en sí o cualquier antecesor es un elemento `<nav>` o tiene un atributo `role="navigation"`.

Para incluir vínculos de navegación en la siguiente ejecución de auditoría:

1. Antes de iniciar una auditoría o después de que finalice una ejecución, abre **Configuración** (el icono del engranaje) en el encabezado de Comprobaciones. Si el icono del engranaje no está visible, abra **Más acciones** (**...**) y seleccione **Configuración**.
1. Seleccione **Mostrar vínculos de navegación del sitio**.
1. Seleccione **Analizar página** para iniciar una ejecución o **Volver a analizar** si los resultados ya se muestran.

![Menú de configuración de comprobaciones con la opción Mostrar vínculos de navegación del sitio](./assets/internal-links/settings-menu.png){align="center"}

**Mostrar vínculos de navegación del sitio** controla qué vínculos comprueba la auditoría, no solo qué resultados muestra (actualmente solo vínculos internos).

Cambiar la configuración no inicia una auditoría ni cambia los resultados que ya están en pantalla. Cuando esos resultados usan una configuración diferente, aparece un punto en **Reanalizar**, con la etiqueta **Reanalizar para aplicar la nueva configuración**. Vuelva a ejecutar las auditorías para aplicar el cambio o restaure la configuración anterior para borrar el punto.

La comprobación preliminar guarda la configuración en el explorador y la conserva después de cerrar la sesión. Las pestañas del mismo sitio comparten la configuración. Para volver a omitir los vínculos de navegación, borre **Mostrar vínculos de navegación del sitio** antes de la siguiente ejecución.

La configuración no está disponible mientras se estén ejecutando auditorías o en el Editor universal.

## Limitaciones conocidas

La auditoría se ejecuta en el Editor de páginas de AEM Sites, en Adobe Managed Services (AMS) y en la creación basada en documentos a través de Sidekick. Actualmente no está disponible en el editor universal.

## Cómo resolver

Cuando la auditoría encuentra oportunidades, cada una describe el problema y el cambio recomendado, e identifica el vínculo involucrado. Use **Resaltar en la página** para ir al vínculo del contenido y use la sección **URL actual** para copiar la URL o abrirla en una nueva pestaña y confirmar el problema. Para obtener información sobre cómo revisar y resolver oportunidades, consulte [Resultados de auditoría en comprobaciones](../../audit-results.md).
