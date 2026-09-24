---
title: Configuración de Sites Optimizer
description: Obtenga información sobre cómo configurar los valores de Sites Optimizer e integrarlo con otras herramientas.
TQID: https://experienceleague.adobe.com/eznjSHZgAmCh-ek-XE-lLtuoGJxC0yY4UVrmPjc0KYo
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
source-git-commit: 37d90154e6868ee392bf1b779b2bf3697112b7ce
workflow-type: tm+mt
source-wordcount: '1960'
ht-degree: 39%
---
# Configuración de Sites Optimizer

![Configuración de Sites Optimizer](./assets/settings/hero.png){align="center"}

La configuración de Sites Optimizer es el repositorio central para configurar la experiencia de Sites Optimizer.

## Consola de Google Search

![Configuración de Site Optimizer para Google Search Console](./assets/settings/google-search-console.png){align="center"}

El conector de configuración de Google Search Console en AEM Sites Optimizer permite realizar el análisis de métricas clave de optimización de los motores de búsqueda, como clasificaciones de búsqueda, tasas de clics y Core Web Vitals. Al mantener Google Search Console conectada, puede aprovechar el análisis JSON para descubrir oportunidades de optimización y mejorar el rendimiento del sitio.

Para configurar este conector, debe tener credenciales con acceso administrativo a Google Search Console para el dominio.

## Conectar con AEM Sites

En esta guía se explica cómo conectar el sitio de Edge Delivery Services (EDS) existente a AEM Sites Optimizer. Antes de empezar, asegúrese de que el sitio de EDS ya esté configurado y en funcionamiento; esta conexión se ha diseñado específicamente para que AEM Sites Optimizer acceda al contenido.

La conexión requiere dos pasos:

1. Proporcione la URL del repositorio de código y la URL del origen de contenido.
2. Conceda el acceso a AEM Sites Optimizer a su origen de contenido.

### Paso 1: Vincular el repositorio de código y el origen de contenido

En AEM Sites Optimizer, vaya a **Configuración → Conectar con AEM Sites** e introduzca lo siguiente:

- **URL del repositorio de código**: la URL de GitHub de su sitio EDS, por ejemplo:
  `https://github.com/owner/repo`

- **URL del origen de contenido**: la URL de la carpeta de SharePoint o de la carpeta de Google Drive que sirve de reserva de su sitio EDS, por ejemplo:
  `https://drive.google.com/drive/folders/...` o `https://myorg.sharepoint.com/...`

Cuando haya introducido la URL del origen de contenido, AEM Sites Optimizer detectará el tipo de origen de contenido y mostrará las instrucciones de acceso pertinentes a continuación.

### Paso 2: Conceder acceso al origen de contenido

Siga la sección que coincide con el origen del contenido.

#### SharePoint: dominio de Adobe

![Cuadro de diálogo Conectar con AEM Sites en el que se muestra que no hay ninguna acción necesaria para el dominio de Adobe SharePoint](./assets/settings/connect-content-and-drive.png){align="center"}

Si la URL del origen de contenido utiliza el dominio de SharePoint de Adobe, no se requiere ninguna otra acción. El acceso ya se ha configurado. Haga clic en **Guardar** para completar la conexión.

#### SharePoint: dominio personalizado

Si la URL del origen de contenido utiliza el dominio SharePoint de su organización, debe registrar una aplicación de Azure y proporcionar sus credenciales a AEM Sites Optimizer.

##### Lo que necesitará

- Permiso para registrar aplicaciones en Azure Portal o un contacto que pueda registrar aplicaciones en su nombre.
- Derechos de administrador del inquilino para conceder el consentimiento de la API o de un administrador que pueda aprobar el consentimiento de la API en su nombre.

##### Paso 2a: Registrar una aplicación en Azure

1. Vaya a **Azure Portal → Microsoft Entra ID → Registros de aplicación → Nuevo registro**.
2. Asígnele un nombre, por ejemplo: `AEM Sites Optimizer`.
3. Deje todos los demás valores predeterminados y haga clic en **Registrarse**.
4. En la página **Información general**, anote lo siguiente:
   - **ID de aplicación (cliente)**
   - **ID de directorio (inquilino)**

##### Paso 2b: Añadir permisos de API

1. Vaya a **Permisos de API → Añadir un permiso → Microsoft Graph → Permisos de aplicación**.
2. Añada lo siguiente:
   - `Sites.Selected`: acceso con ámbito a colecciones de sitios de SharePoint específicas.
   - `Files.SelectedOperations.Selected`: acceso a archivos sin un usuario que ha iniciado sesión.
3. Haga clic en **Conceder consentimiento de administrador** para ambos.

![Permisos de la API de Azure que muestran Sites.Selected y Files.SelectedOperations.Selected concedidos](./assets/settings/app-permissions.png){align="center"}

>[!NOTE]
>
>La concesión del consentimiento de administrador requiere derechos de administrador del inquilino. Si no los tiene, pídale al administrador de TI o de Azure que complete este paso antes de continuar.

##### Paso 2c: Crear un secreto de cliente

![Certificados de Azure y página de secretos para el registro de la aplicación](./assets/settings/create-credentials.png){align="center"}

1. Vaya a **Certificados y secretos → Nuevo secreto de cliente**.
2. Establezca una descripción y una caducidad y, a continuación, haga clic en **Añadir**.
3. Copie el valor secreto inmediatamente; solo se muestra una vez.

##### Paso 2d: Conceder acceso a la aplicación a su sitio de SharePoint

Puede conceder acceso a la aplicación mediante Microsoft Graph Explorer, PowerShell o llamadas directas a la API de Graph.

Vaya a [Microsoft Graph Explorer](https://developer.microsoft.com/graph/graph-explorer), inicie sesión con su cuenta de Microsoft y ejecute las siguientes solicitudes:

1. Busque el ID del sitio:

```
GET https://graph.microsoft.com/v1.0/sites/{tenant}.sharepoint.com:/sites/{site-name}
```

1. Copie el `id` de la respuesta y, a continuación, conceda acceso a nivel de sitio:

```
POST https://graph.microsoft.com/v1.0/sites/{siteId}/permissions
```

Cuerpo:

```json
{
  "roles": ["write"],
  "grantedToIdentities": [{
    "application": {
      "id": "{your-client-id}",
      "displayName": "{Your app name}"
    }
  }]
}
```

##### Paso 2e: introducir las credenciales en AEM Sites Optimizer

![Cuadro de diálogo Conectar con AEM Sites que muestra los campos de credenciales de SharePoint](./assets/settings/add-sharepoint-credentials.png){align="center"}

Cuando vuelva al cuadro de diálogo **Conectar con AEM Sites**, escriba lo siguiente en **Conexión del repositorio de contenido mediante SharePoint**:

- **ID de inquilino (Azure AD)** — en Registro de la aplicación → Información general.
- **ID de cliente (registro de la aplicación)** — en Registro de la aplicación → Información general.
- **Secreto de cliente** — creado en el Paso 2c.

Haga clic en **Validar conexión** para confirmar el acceso y, a continuación, haga clic en **Guardar**.

#### Google Drive

![Cuadro de diálogo Conectar con AEM Sites que muestra la cuenta de servicio de Google Drive para compartir el acceso](./assets/settings/validate-eds-google.png){align="center"}

1. En Google Drive, haga clic con el botón derecho del ratón en la carpeta que contiene su sitio EDS y seleccione **Compartir**.
2. En el campo **Añadir personas y grupos**, escriba el correo electrónico de la cuenta de servicio que se muestra en el cuadro de diálogo **Conectar con AEM Sites**:
   `aem-sites-optimizer@adbe-gcp0843.iam.gserviceaccount.com`
3. Establezca el nivel de permiso en **Editor**.
4. Desmarque **Notificar a las personas** y haga clic en **Compartir**.

Una vez completado el uso compartido, haga clic en **Validar conexión** en el cuadro de diálogo y, a continuación, haga clic en **Guardar**.

## Administrar permisos de usuario

Controle quién puede acceder a un sitio en Sites Optimizer y qué puede hacer con él. El acceso se genera a partir de un pequeño conjunto de *capacidades* independientes (ver, editar, implementar, configurar y administrar usuarios) que usted concede a cada persona.

El acceso es **aditivo**: los permisos de una persona son la suma de todo lo que se le ha concedido. No hay &quot;denegar&quot;, así que las concesiones nunca entran en conflicto ni se cancelan mutuamente. Para que alguien tenga menos acceso, quite una concesión en lugar de intentar anularla.

### Cómo se concede el acceso

Hay dos maneras en que una persona puede obtener acceso y trabajan juntas:

- **Acceso en toda la organización** — asignado por el administrador de organización de Adobe en [Adobe Admin Console](https://adminconsole.adobe.com/). Se aplica a todos los sitios de su organización. Utilícelo para personas que necesitan el mismo acceso en todas partes.
- **Acceso de nivel de sitio** — asignado dentro de Sites Optimizer, en la página **Configuración → Permisos**. Se aplica a un solo sitio y puede ser tan amplio o estrecho como necesite. No se requiere acceso a Admin Console.

>[!NOTE]
>
>Las dos capas se suman. Alguien con acceso de visualización en toda la organización y a quien también se le conceda Editar en un sitio, puede ver todos los sitios y editar ese sitio. Para mantener a una persona limitada a un solo sitio, asegúrese de que no tenga también una función para toda la organización.

#### Funciones en toda la organización (Admin Console)

El acceso para toda la organización proviene de una de las dos funciones de producto de **AEM Sites Optimizer**, asignadas en [Adobe Admin Console](https://adminconsole.adobe.com/):

- **Administrador de ASO**: acceso completo a todos los sitios, incluidos **Administrar usuarios**. Un administrador puede abrir la página **Permisos** para cualquier sitio y asignar acceso a otros.
- **Usuario ASO**: acceso de solo vista a cada sitio. Sin cambios ni administración de usuarios.

Para asignar una función, debes ser **administrador del sistema** para la organización o **administrador de productos** para AEM Sites Optimizer.

1. Inicie sesión en [Adobe Admin Console](https://adminconsole.adobe.com/).
1. Vaya a **Productos** y seleccione **AEM Sites Optimizer**.
1. Abra la ficha **Usuarios** y agregue el usuario por correo electrónico (o seleccione un usuario existente).
1. Haga clic en el icono **+** (agregar) para agregar un perfil de producto y, a continuación, elija el perfil de producto.

   ![Selección del perfil de producto para un usuario en Adobe Admin Console](./assets/settings/permissions-admin-console-product-profile.png){align="center"}

1. Haga clic en **Siguiente**.
1. Elija la función **Administrador de ASO** para obtener acceso completo o **Usuario de ASO** para obtener acceso de solo vista y, a continuación, haga clic en **Aplicar**.

   ![Selección del rol de Administrador de ASO en Adobe Admin Console](./assets/settings/permissions-admin-console-aso-manager-role.png){align="center"}

   ![Selección del rol de usuario ASO en Adobe Admin Console](./assets/settings/permissions-admin-console-aso-user-role.png){align="center"}

Para obtener más información sobre cómo agregar usuarios, consulte [Usuarios incorporados](setup/onboard-users.md).

>[!IMPORTANT]
>
>Solamente un administrador de organización puede otorgar **Administrar usuarios** en toda la organización. Un miembro que tenga **Administrar usuarios** en un sitio puede asignar acceso a ese sitio, pero no puede crear un **Administrador de ASO** para toda la organización.

### Niveles de capacidad

Cada capacidad controla un tipo de acción. Son independientes; por ejemplo, se puede conceder la opción Implementar sin Editar.

| Capacidad | Lo que permite | Lo que no permite |
|---|---|---|
| Ver | Vea los datos del sitio (oportunidades, sugerencias, correcciones, informes y configuración) sin cambiar nada. | Cualquier cambio. |
| Editar | Cree y cambie oportunidades y sugerencias (qué debería cambiar). | Publicar cambios, cambiar la configuración o administrar usuarios. |
| Implementación | Publique las correcciones en directo en el sitio y deshágalas. | Administración de usuarios. |
| Configuración | Cambie la configuración y las conexiones del sitio. | Publicar correcciones o administrar usuarios. |
| Administrar usuarios | Conceder o revocar el acceso de otros miembros al sitio. | Administración de un sitio al que la persona no tiene acceso. |

>[!NOTE]
>
>**Vista siempre está incluida.** Cada concesión incluye Ver automáticamente: no puede administrar, configurar, editar ni implementar algo que no puede ver. Debido a esto, la vista no se puede eliminar por sí sola. Para quitar el acceso de alguien por completo, quita el miembro (consulta [Editar o quitar un miembro](#edit-or-remove-a-member) a continuación) en lugar de desmarcar todas las capacidades.

### Acceso del ámbito a los tipos de oportunidad

En un solo sitio, puede conceder Ver, Editar e Implementar para **tipos de oportunidades específicas** (por ejemplo, Core Web Vitals o vínculos internos rotos) en lugar de todo el sitio. Esto permite que una persona edite Core Web Vitals mientras solo ve todo lo demás.

- **Ver**, **Editar** y **Implementar** se pueden vincular a uno o más tipos de oportunidad o a **Todos**.
- **Configurar** y **Administrar usuarios** siempre se aplican a todo el sitio; no se pueden limitar a un tipo de oportunidad.

Cada concesión con ámbito aparece como su propia fila para el miembro, con una columna **Se aplica a** que muestra el tipo de oportunidad, **Todos** o **En todo el sitio**.

>[!CAUTION]
>
>El ámbito solo limita lo que proporciona *esa concesión de*; nunca elimina el acceso que proporciona otra concesión. Si una persona también tiene acceso en toda la organización o una concesión de tipo **All**, se seguirá aplicando ese acceso más amplio. Por lo tanto, para limitar a alguien a tipos de oportunidades específicos, asegúrese de que no tenga una función más amplia o una concesión de **Todos**.

### Agregar un miembro

1. Vaya a **Configuración → Permisos** y seleccione el sitio.
1. Haga clic en **Agregar miembros**.
1. Busque por nombre o correo electrónico y seleccione una o más personas.
1. Elija **los tipos de oportunidad** a los que se aplica el acceso (o **Todos**) y, a continuación, seleccione las capacidades que desea conceder.
1. Haga clic en **Agregar**.

<!-- MEDIA PENDING: Site Manager / Site User walkthrough videos are being re-recorded with demo data to remove PII, then re-uploaded to video.tv.adobe.com and embedded here with >[!VIDEO]. The earlier uploads v/3503767 and v/3503768 (KT-22672 / KT-22673) contain PII and must not be used. -->

### Editar o quitar un miembro

En la tabla **Members**:

- Haga clic en **Editar capacidades** en la fila de un miembro para cambiar lo que puede hacer. Al editar una concesión existente, su tipo de oportunidad permanece fijo: sólo cambia las capacidades y debe permanecer seleccionada al menos una.
- Haga clic en **Quitar** para revocar por completo el acceso de ese miembro al sitio.

>[!NOTE]
>
>Cambiar las capacidades y quitar un miembro son acciones diferentes. Para quitar todo acceso, use **Quitar**; no puede hacerlo desmarcando las capacidades, porque una concesión debe conservar al menos una capacidad (y Ver siempre permanece).

### Quién puede administrar permisos

La página **Permisos** de un sitio está disponible para:

- Miembros con la capacidad **Administrar usuarios** en ese sitio y
- Administradores de organización (un administrador de ASO).

Los miembros sin **Administrar usuarios** ven un mensaje que indica que no tienen permiso para administrar el acceso a ese sitio.

### Activar la administración de usuarios y acceso

La administración de usuarios y accesos está controlada por una configuración para su organización. Puede asignar el acceso antes de activarlo, pero solo se **aplicará** una vez activado el ajuste.

Si aún no está habilitada, la página **Permisos** muestra un banner en el que se le pide que se ponga en contacto con el equipo de la cuenta. Póngase en contacto con el equipo de su cuenta de Sites Optimizer para activarla.

>[!NOTE]
>
>Hasta que se active la administración de usuarios y acceso, los permisos que asigne se guardarán, pero no se aplicarán.

### Preguntas frecuentes

**¿Necesitan los miembros de nivel de sitio un rol de Admin Console?**

No. El acceso de nivel de sitio se concede completamente dentro de Sites Optimizer, en la página **Permisos**. En Admin Console solo se asignan funciones para toda la organización.

**¿Qué sucede si alguien tiene acceso a nivel de sitio y a nivel de toda la organización?**

Ambos se aplican. Su acceso efectivo es la combinación de ambos. Las concesiones nunca entran en conflicto, ya que ninguna concesión puede denegar el acceso.

**¿Por qué un miembro con la función Administrar usuarios no puede crear un administrador para toda la organización?**

La creación de una función para toda la organización es una acción de Admin Console. Un miembro con **Administrar usuarios** puede asignar acceso a su propio sitio, pero solamente un administrador de la organización puede otorgar roles en toda la organización.

**¿Cómo revoco el acceso de una persona a un sitio?**

Eliminar su concesión en la página **Permisos**. Esto es diferente a las capacidades de edición, que siempre deben dejar al menos una capacidad.

**¿Puedo limitar a una persona a tipos de oportunidades específicos?**

Sí — conceder vista, edición o implementación con ámbito a tipos de oportunidad específicos en lugar de **Todos**. Como el acceso es aditivo, esto solo tiene efecto si la persona no tiene también acceso en toda la organización o una concesión de tipo **All**.
