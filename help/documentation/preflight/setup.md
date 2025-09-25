---
title: Configuración de comprobación preliminar
description: Obtenga información sobre cómo configurar la extensión de comprobaciones para AEM Sites Optimizer.
source-git-commit: 6e177ef6b9d121ac7484ae118037c7e542f981d8
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 1%

---


# Configuración de comprobación preliminar

La identificación de la oportunidad de comprobación preliminar de AEM Sites Optimizer requiere la configuración de la extensión de comprobación preliminar en el editor universal, la vista previa basada en documentos o AEM Cloud Service para ejecutar auditorías de comprobaciones en las páginas antes de publicarlas.

## Habilitar acceso de usuario

Para usar la extensión de comprobaciones, asegúrese de que el usuario esté asignado al menos a uno de los siguientes perfiles de producto de AEM Sites Optimizer en [Adobe Admin Console](https://adminconsole.adobe.com):

* AEM Sites Optimizer: Sugerencia automática de usuario
* AEM Sites Optimizer: Optimización automática del usuario

## Habilitar la extensión de comprobaciones

>[!BEGINTABS]

>[!TAB Editor universal]

Para configurar la comprobación preliminar en el editor universal, siga estos pasos:

1. Abra **Extension Manager** en:
   [https://experience.adobe.com/#/@org/aem/extension-manager/universal-editor](https://experience.adobe.com/#/@org/aem/extension-manager/universal-editor)
1. Busque la **extensión de comprobaciones de AEM Sites Optimizer** y envíe una solicitud para habilitarla.
1. El **equipo de AEM de Adobe** revisará y habilitará la extensión para su organización.
1. Una vez habilitada la extensión, abra una página en **Editor universal**, por ejemplo:
   `https://author-p12345-e123456.adobeaemcloud.com/ui#/@org/aem/universal-editor/canvas/author-p12345-e123456.adobeaemcloud.com/content/en/example/home.html`
1. La **extensión de comprobación preliminar** aparecerá en el **carril lateral**.
1. Seleccione la **extensión de comprobaciones** del carril lateral para iniciar una **auditoría de comprobaciones** de la página actual.

>[!TAB Creación basada en documentos]

Para configurar la comprobación preliminar para la creación basada en documentos, siga estos pasos:

1. Agregue la siguiente configuración a `/tools/sidekick/config.json` en el repositorio de GitHub de su proyecto de Edge Delivery Services:

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

1. Cree un nuevo archivo `/tools/sidekick/aem-sites-optimizer-preflight.js` y agregue el siguiente contenido:

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

1. Actualice la función `loadLazy()` en `/scripts/scripts.js` para importar el script de comprobación preliminar para las direcciones URL de vista previa:

   ```javascript
   if (window.location.href.includes('.aem.page')) {
      import('../tools/sidekick/aem-sites-optimizer-preflight.js');
   }
   ```

1. Abra la dirección URL de vista previa (`*.aem.page`) de la página que desea auditar.
1. En **Sidekick**, haga clic en el botón **Comprobación preliminar** para iniciar la auditoría de la página actual.

>[!TAB Editor de páginas AEM Sites]

Para utilizar la comprobación preliminar en el editor de páginas de AEM Sites, puede crear un bookmarklet en el explorador web. Siga estos pasos:

1. Mostrar la **Barra de marcadores** en el explorador web:

   * Presione **Ctrl+Mayús+B** (Windows) o **Cmd+Mayús+B** (Mac).

!. Cree un nuevo marcador en el explorador:

* Haga clic con el botón derecho en la barra de marcadores y seleccione **Nueva página** o **Agregar marcador**.
* En el campo **Dirección (URL)**, pegue el siguiente código:

```javascript
javascript:(function(){const script=document.createElement('script');script.src='https://experience.adobe.com/solutions/OneAdobe-aem-sites-optimizer-preflight-mfe/static-assets/resources/sidekick/client.js?source=bookmarklet&target-source=aem-cloud-service';document.head.appendChild(script);})();
```

1. Asigne un nombre al marcador **Comprobación preliminar** (o cualquier nombre que prefiera).
1. Abra la URL de vista previa (`*.aem.page`) de la página que desea auditar en el **Editor de páginas de AEM Sites**.
1. Haga clic en el marcador **Comprobación preliminar** de la barra de marcadores para iniciar la auditoría de la página actual.

>[!ENDTABS]

## Prácticas recomendadas

Cuando ejecute auditorías de comprobaciones, tenga en cuenta las siguientes directrices:

* Ejecute siempre auditorías en **páginas de ensayo o vista previa** antes de publicar en producción.
* Priorice la resolución de **problemas de alto impacto**, como vínculos rotos, etiquetas H1 que faltan o vínculos no seguros.
* Asegúrese de que la autenticación **esté habilitada** para los entornos de ensayo protegidos antes de ejecutar auditorías.
* Revise y aplique **recomendaciones de etiquetas meta** para mejorar el rendimiento de SEO.
