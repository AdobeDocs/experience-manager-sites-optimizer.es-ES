---
title: 'AEM Sites Optimizer: Guía de incorporación de comprobaciones'
description: Obtenga información sobre las oportunidades de comprobaciones y cómo configurar el análisis de comprobaciones en AEM Sites Optimizer.
source-git-commit: 0a6ddcdfd369253500067b31617facfb7f38b656
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 6%

---


# Oportunidades de comprobación preliminar

![Oportunidades de comprobación preliminar](./assets/preflight/hero.png){align="center"}

<span class="preview">AEM Sites Optimizer Preflight analiza los datos técnicos y de rendimiento de la página y anticipa y detecta las oportunidades antes de su publicación. Utiliza IA generativa para sugerir optimizaciones.</span>

## Oportunidades

<!-- CARDS

* ../documentation/opportunities/invalid-or-missing-metadata.md
  {title=Canonical}
  {image=../assets/common/card-link.png}
* ../documentation/opportunities/broken-internal-links.md
  {title=Broken Internal Links}
  {image=../assets/common/card-link.png}
* ../documentation/opportunities/invalid-or-missing-metadata.md
  {title=Metatags}
  {image=../assets/common/card-code.png}
* ../documentation/opportunities/invalid-or-missing-metadata.md
  {title=H1 count}
  {image=../assets/common/card-code.png}
* ../documentation/opportunities/accessibility-issues.md
  {title=Accessibility}
  {image=../assets/common/card-puzzle.png}

-->
<!-- START CARDS HTML - DO NOT MODIFY BY HAND -->
<div class="columns">
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Canonical">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-image">
                <figure class="image x-is-16by9">
                    <a href="../documentation/opportunities/invalid-or-missing-metadata.md" title="Canónico" target="_blank" rel="referrer">
                        <img class="is-bordered-r-small" src="../assets/common/card-link.png" alt="Canónico"
                             style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover; overflow: hidden; display: block; margin: auto;">
                    </a>
                </figure>
            </div>
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">
                        <a href="../documentation/opportunities/invalid-or-missing-metadata.md" target="_blank" rel="referrer" title="Canónico">Canónico</a>
                    </p>
                    <p class="is-size-6">Obtenga información acerca de la oportunidad canónica y cómo utilizarla para mejorar la SEO y evitar problemas de contenido duplicado.</p>
                </div>
                <a href="../documentation/opportunities/invalid-or-missing-metadata.md" target="_blank" rel="referrer" class="spectrum-Button spectrum-Button--outline spectrum-Button--primary spectrum-Button--sizeM" style="align-self: flex-start; margin-top: 1rem;">
                    <span class="spectrum-Button-label has-no-wrap has-text-weight-bold">Más información</span>
                </a>
            </div>
        </div>
    </div>
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Broken Internal Links">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-image">
                <figure class="image x-is-16by9">
                    <a href="../documentation/opportunities/broken-internal-links.md" title="Vínculos internos rotos" target="_blank" rel="referrer">
                        <img class="is-bordered-r-small" src="../assets/common/card-link.png" alt="Vínculos internos rotos"
                             style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover; overflow: hidden; display: block; margin: auto;">
                    </a>
                </figure>
            </div>
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">
                        <a href="../documentation/opportunities/broken-internal-links.md" target="_blank" rel="referrer" title="Vínculos internos rotos">Vínculos internos rotos</a>
                    </p>
                    <p class="is-size-6">Obtenga información acerca de la oportunidad de vínculos internos rotos y cómo utilizarla para identificar y corregir vínculos rotos o problemáticos en el sitio web.</p>
                </div>
                <a href="../documentation/opportunities/broken-internal-links.md" target="_blank" rel="referrer" class="spectrum-Button spectrum-Button--outline spectrum-Button--primary spectrum-Button--sizeM" style="align-self: flex-start; margin-top: 1rem;">
                    <span class="spectrum-Button-label has-no-wrap has-text-weight-bold">Más información</span>
                </a>
            </div>
        </div>
    </div>
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Metatags">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-image">
                <figure class="image x-is-16by9">
                    <a href="../documentation/opportunities/invalid-or-missing-metadata.md" title="Metatags" target="_blank" rel="referrer">
                        <img class="is-bordered-r-small" src="../assets/common/card-code.png" alt="Metatags"
                             style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover; overflow: hidden; display: block; margin: auto;">
                    </a>
                </figure>
            </div>
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">
                        <a href="../documentation/opportunities/invalid-or-missing-metadata.md" target="_blank" rel="referrer" title="Metatags">Etiquetas de metadatos</a>
                    </p>
                    <p class="is-size-6">Conozca la oportunidad de las metaetiquetas y cómo utilizarla para optimizar los metadatos de su página y mejorar el rendimiento de la SEO.</p>
                </div>
                <a href="../documentation/opportunities/invalid-or-missing-metadata.md" target="_blank" rel="referrer" class="spectrum-Button spectrum-Button--outline spectrum-Button--primary spectrum-Button--sizeM" style="align-self: flex-start; margin-top: 1rem;">
                    <span class="spectrum-Button-label has-no-wrap has-text-weight-bold">Más información</span>
                </a>
            </div>
        </div>
    </div>
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="H1 count">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-image">
                <figure class="image x-is-16by9">
                    <a href="../documentation/opportunities/invalid-or-missing-metadata.md" title="Recuento H1" target="_blank" rel="referrer">
                        <img class="is-bordered-r-small" src="../assets/common/card-code.png" alt="Recuento H1"
                             style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover; overflow: hidden; display: block; margin: auto;">
                    </a>
                </figure>
            </div>
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">
                        <a href="../documentation/opportunities/invalid-or-missing-metadata.md" target="_blank" rel="referrer" title="Recuento H1">Recuento H1</a>
                    </p>
                    <p class="is-size-6">Obtenga información acerca de la oportunidad de recuento H1 y cómo utilizarla para garantizar una estructura de encabezados y una optimización de los motores de búsqueda adecuadas.</p>
                </div>
                <a href="../documentation/opportunities/invalid-or-missing-metadata.md" target="_blank" rel="referrer" class="spectrum-Button spectrum-Button--outline spectrum-Button--primary spectrum-Button--sizeM" style="align-self: flex-start; margin-top: 1rem;">
                    <span class="spectrum-Button-label has-no-wrap has-text-weight-bold">Más información</span>
                </a>
            </div>
        </div>
    </div>
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Accessibility">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-image">
                <figure class="image x-is-16by9">
                    <a href="../documentation/opportunities/accessibility-issues.md" title="Accesibilidad" target="_blank" rel="referrer">
                        <img class="is-bordered-r-small" src="../assets/common/card-puzzle.png" alt="Accesibilidad"
                             style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover; overflow: hidden; display: block; margin: auto;">
                    </a>
                </figure>
            </div>
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">
                        <a href="../documentation/opportunities/accessibility-issues.md" target="_blank" rel="referrer" title="Accesibilidad">Accesibilidad</a>
                    </p>
                    <p class="is-size-6">Obtenga información acerca de la oportunidad de accesibilidad y cómo utilizarla para garantizar que el sitio web sea accesible para todos los usuarios.</p>
                </div>
                <a href="../documentation/opportunities/accessibility-issues.md" target="_blank" rel="referrer" class="spectrum-Button spectrum-Button--outline spectrum-Button--primary spectrum-Button--sizeM" style="align-self: flex-start; margin-top: 1rem;">
                    <span class="spectrum-Button-label has-no-wrap has-text-weight-bold">Más información</span>
                </a>
            </div>
        </div>
    </div>

</div>
<!-- END CARDS HTML - DO NOT MODIFY BY HAND -->

## Cómo configurar

### Configuración del editor universal

1. Vaya a Extension Manager desde la dirección URL: https://experience.adobe.com/#/@org/aem/extension-manager/universal-editor
2. Seleccione la extensión de comprobaciones de AEM Sites Optimizer y solicite la activación
3. El equipo de AEM habilitará la extensión para su organización
4. Una vez hecho esto, abra una página en el editor universal como: https://author-p12345-e123456.adobeaemcloud.com/ui#/@org/aem/universal-editor/canvas/author-p12345-e123456.adobeaemcloud.com/content/site/subscription.html
5. La extensión de comprobación preliminar será visible en el carril lateral
6. Al hacer clic en Extensión de comprobación preliminar desde el carril lateral, se iniciará la auditoría de comprobaciones para la página actual

### Configuración de vista previa basada en documentos

#### Paso 1: Habilitar Sidekick con el botón de verificación previa

Agregue la siguiente configuración a `/tools/sidekick/config.json` en su repositorio de GitHub:

```json
{
  "plugins": [
    {
      "id": "preflight",
      "titleI18n": {
        "en": "Preflight"
      },
      "environments": ["preview"],
      "event": "preflight"
    }
  ]
}
```

#### Paso 2: Creación del script de integración de Sidekick

Crear `/tools/sidekick/aem-sites-optimizer-preflight.js` con el siguiente contenido:

```javascript
(function () {
  let isAEMSitesOptimizerPreflightAppLoaded = false;
  function loadAEMSitesOptimizerPreflightApp() {
    const script = document.createElement('script');
    script.src = 'https://experience.adobe.com/solutions/OneAdobe-aem-sites-optimizer-preflight-mfe/static-assets/resources/sidekick/client.js?source=plugin';
    script.onload = function () {
      isAEMSitesOptimizerPreflightAppLoaded = true;
    };
    script.onerror = function () {
      console.error('Error loading AEMSitesOptimizerPreflightApp.');
    };
    document.head.appendChild(script);
  }

  function handlePluginButtonClick() {
    if (!isAEMSitesOptimizerPreflightAppLoaded) {
      loadAEMSitesOptimizerPreflightApp();
    }
  }

  // Sidekick V1 extension support
  const sidekick = document.querySelector('helix-sidekick');
  if (sidekick) {
    sidekick.addEventListener('custom:preflight', handlePluginButtonClick);
  } else {
    document.addEventListener('sidekick-ready', () => {
      document.querySelector('helix-sidekick')
        .addEventListener('custom:preflight', handlePluginButtonClick);
    }, { once: true });
  }

  // Sidekick V2 extension support
  const sidekickV2 = document.querySelector('aem-sidekick');
  if (sidekickV2) {
    sidekickV2.addEventListener('custom:preflight', handlePluginButtonClick);
  } else {
    document.addEventListener('sidekick-ready', () => {
      document.querySelector('aem-sidekick')
        .addEventListener('custom:preflight', handlePluginButtonClick);
    }, { once: true });
  }
}());
```

#### Paso 3: Actualización del archivo de scripts

Agregue la siguiente instrucción de importación a la función `loadLazy()` en `/scripts/scripts.js` para las direcciones URL de vista previa, como se muestra a continuación:

```javascript
if (window.location.href.includes('.aem.page')) {
   import('../tools/sidekick/aem-sites-optimizer-preflight.js');
}
```

Ahora el botón Comprobaciones debería estar visible en Sidekick.

#### Paso 4: Ejecución de la auditoría

Abra la URL de vista previa (*.aem.page) de la página auditada. Haga clic en el botón Comprobaciones de Sidekick.

### Configuración de AEM Cloud Service

Puede utilizar la opción de bookmarklet para probar la comprobación preliminar en editores de páginas y entornos de espacio aislado de AEM Cloud Service.

<!-- Drag the button below to your Bookmarks Bar to get started. -->

Presione **Ctrl+Mayús+B** (Windows) o **Cmd+Mayús+B** (Mac) para mostrar la barra de marcadores. Haga clic con el botón derecho en la barra de marcadores y seleccione &quot;Nueva página&quot; o &quot;Agregar marcador&quot;. En el campo de dirección, copie el código siguiente.

<!-- **Drag this link to your Bookmarks Bar:**

<a href="javascript:(function(){const script=document.createElement('script');script.src='https://experience.adobe.com/solutions/OneAdobe-aem-sites-optimizer-preflight-mfe/static-assets/resources/sidekick/client.js?source=bookmarklet&target-source=aem-cloud-service';document.head.appendChild(script);})();">Preflight</a> -->

**Copie este código y cree un nuevo marcador:**

```
javascript:(function(){const script=document.createElement('script');script.src='https://experience.adobe.com/solutions/OneAdobe-aem-sites-optimizer-preflight-mfe/static-assets/resources/sidekick/client.js?source=bookmarklet&target-source=aem-cloud-service';document.head.appendChild(script);})();
```

Una vez añadido el bookmarklet, abra la URL de vista previa (*.aem.page) de la página auditada. Haga clic en el marcador Comprobaciones para iniciar la auditoría de comprobaciones.

## Prácticas recomendadas

Al utilizar la comprobación preliminar, tenga en cuenta lo siguiente:

* Ejecute auditorías de comprobaciones en todas las páginas de ensayo y vista previa antes de publicar.
* Aborde primero los problemas de alto impacto (vínculos rotos, etiquetas H1 faltantes, vínculos no seguros).
* Habilite la autenticación para entornos de ensayo protegidos.
* Revise e implemente sugerencias de etiquetas meta para obtener un mejor rendimiento de SEO.
