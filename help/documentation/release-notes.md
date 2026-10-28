---
title: Notas de la versión
description: Obtenga información sobre las últimas funciones, mejoras y correcciones de errores en Adobe Experience Manager Sites Optimizer.
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
source-git-commit: 733056458d3e34a9ef2e285adfc810a98159002b
workflow-type: tm+mt
source-wordcount: '3666'
ht-degree: 2%
---

# Notas de la versión

Esta página documenta las últimas actualizaciones, nuevas funciones y mejoras de Adobe Experience Manager Sites Optimizer.

Las características marcadas **(acceso anticipado)** están disponibles bajo petición; póngase en contacto con el equipo de su cuenta o con el ingeniero de éxito del cliente para habilitarlas en su organización.

## Del 26 al 28 de octubre de 2026 {#october-26-28-2026}

### Nuevas funciones

- **Cobertura de auditoría en la configuración** — La configuración ahora incluye una sección **Cobertura de auditoría** que enumera las auditorías que se ejecutan para su sitio, agrupadas por categoría como SEO, Accesibilidad, Seguridad y Conversión y participación.
- **Valor estimado (acceso anticipado)**: Core Web Vitals, texto alternativo, accesibilidad, contraste de color, accesibilidad del formulario y oportunidades de seguridad ahora muestran un valor estimado, como la mano de obra ahorrada o el riesgo evitado, para ayudarle a priorizar las correcciones. La mano de obra guardada para correcciones de accesibilidad y seguridad se muestra como un valor único, y las oportunidades de mapa del sitio y de Hreflang muestran cuántos problemas se han marcado.

### Mejoras

- **Entradas de Jira para texto alternativo (acceso anticipado)**: cree entradas de Jira para uno o más problemas de texto alternativo, con la dirección URL de la página, la dirección URL de la imagen y el texto alternativo sugerido incluidos en cada entrada.

## 19-25 de octubre de 2026 {#october-19-25-2026}

### Nuevas funciones

- **Informe de accesibilidad unificado (acceso anticipado)**: El informe de accesibilidad ahora reúne todos los resultados en un informe, con información general sobre los problemas y un desglose por tipo de problema, grupo de páginas y página. Abra un panel lateral para obtener instrucciones de correcciones de nivel de elemento y exporte el informe como archivo CSV.
- **Configuración de vínculos de exploración del sitio de comprobación preliminar**: elija si la auditoría de vínculos internos comprueba los vínculos dentro de los menús de exploración del sitio. La configuración está desactivada de manera predeterminada, por lo que las auditorías finalizan más rápido y **Volver a analizar** muestra cuándo aún no se ha aplicado una configuración modificada.
- **Filtros de instancia de comprobación preliminar**: en las páginas de detalles Vínculos internos y Vínculos externos, filtre las instancias por **Rotos** o **Necesita verificación**.

### Mejoras

- **Redirecciones de Dispatcher de vínculos rotos (acceso anticipado)**: en los sitios de AEM as a Cloud Service donde Sites Optimizer implementa redirecciones a través de Dispatcher, las correcciones de vínculos rotos ahora se etiquetan como implementadas en Dispatcher en lugar de en AEM Author y puede revertir una redirección implementada.
- **Estado de auditoría del monitor de estado del sitio**: las puntuaciones de estado ahora reflejan las auditorías habilitadas para el sitio. Las auditorías deshabilitadas están ocultas, las auditorías que deben configurarse se muestran con una explicación y ninguna cuenta para las puntuaciones de categoría.
- **Sin CTA sobre las propuestas de plegado** — Ahora las sugerencias de plegado sobre no CTA muestran una propuesta estructurada de call-to-action con capturas de pantalla de **Control** y **Propuesta** en paralelo, y las oportunidades aparecen solamente cuando ambas capturas de pantalla están disponibles.
- **Permisos de grupo (acceso anticipado)**: conceda acceso al sitio a grupos de usuarios de su organización, no solo a personas individuales, y vea un distintivo de **Usuario inactivo** para los miembros que ya no se encuentren en el directorio de su organización.
- **Omisiones de datos estructurados restaurables** — Los problemas de datos estructurados omitidos ahora aparecen en una ficha **Omitido**, donde puede restaurarlos.
- **Sugerencias de datos estructurados de preguntas más frecuentes**: las sugerencias de preguntas más frecuentes ahora muestran exactamente los pares de pregunta y respuesta que se implementarán. Los pares individuales ya no se pueden eliminar de la tabla.
- **Progreso de auditoría de comprobación preliminar**: el medidor de preparación ahora muestra el porcentaje de auditorías que se superaron y cada categoría muestra cuándo se siguen ejecutando las auditorías, con un recuento &quot;superado hasta el momento&quot; hasta que los resultados sean finales.
- **Comprobación preliminar de la cobertura de los vínculos internos**: la auditoría de vínculos internos ahora comprueba todos los vínculos válidos del mismo host en la página, incluidos los vínculos de componentes repetidos, como las listas de tarjetas. Los vínculos de navegación del sitio se incluyen solamente cuando se selecciona **Mostrar vínculos de navegación del sitio**. Primero se enumeran los vínculos fuera de la navegación del sitio y Comprobación preliminar informa claramente cuando una página tiene demasiados vínculos para protegerse a tiempo.
- **Acciones de encabezado de comprobación preliminar** — **Volver a analizar** y **Cerrar** siempre permanecen visibles en el encabezado de comprobación preliminar, y **Exportar** y **Configuración** se mueven al menú **Más acciones** cuando el espacio es limitado.
- **Reintentos de vínculos internos de comprobación preliminar**: la auditoría de vínculos internos ahora reintenta los vínculos que fallan temporalmente, por lo que es menos probable que una interrupción breve se comunique como un vínculo roto.
- **Indicadores de progreso de comprobación preliminar**: los indicadores de procesamiento ahora aparecen solamente en las auditorías que aún se están ejecutando, no en sus categorías.
- **Detalles de oportunidad de comprobación preliminar**: las oportunidades ya no muestran distintivos de gravedad y las exportaciones de CSV y PDF ya no incluyen gravedad.

### Correcciones de errores

- La búsqueda de oportunidades ahora devuelve resultados coherentes independientemente de las mayúsculas y minúsculas de las letras, los acentos, los guiones o los espacios adicionales, incluso al pegar un nombre de oportunidad.
- El Monitor de estado del sitio ya no enumera los documentos de PDF como páginas.
- **Más información** los vínculos del cuadro de diálogo Conectar con AEM Sites, las etiquetas de gravedad compuesta y las tarjetas de métrica de inicio de prueba ahora se muestran correctamente en todos los idiomas compatibles.
- Las direcciones URL largas en los detalles de la oportunidad de comprobación preliminar ahora se ajustan en lugar de ampliar la tarjeta.

## Del 12 al 18 de octubre de 2026 {#october-12-18-2026}

### Mejoras

- **Tickets masivos de Jira para accesibilidad (acceso anticipado)**: seleccione varios problemas de accesibilidad, contraste de color y accesibilidad de formularios y cree un ticket de Jira con un título agrupado y un único archivo adjunto combinado de corrección de código.
- **Métricas del monitor de mantenimiento del sitio**: el monitor de mantenimiento del sitio ya no utiliza la métrica de tasa de pulsaciones (CTR) retirada en su lógica de mantenimiento o panel.
- **Comprobación preliminar de coincidencia de sitios**: cuando una página coincide con más de un sitio incorporado, Comprobación preliminar explica el problema y le permite continuar con uno de los sitios coincidentes.
- **Sugerencias de texto alternativo de comprobación preliminar**: las oportunidades de texto alternativo muestran el texto alternativo sugerido como una sugerencia lista para usar, seguida del motivo de la sugerencia cuando hay una disponible.
- **Detalles de Lorem Ipsum de comprobación preliminar**: cuando se encuentra texto de marcador de posición en un atributo, como el texto alternativo de una imagen, la oportunidad muestra qué atributo coincide.

### Correcciones de errores

- Las oportunidades con sugerencias obsoletas ahora muestran un estado coherente en la lista de oportunidades y en las páginas de detalles.

## Del 5 al 11 de octubre de 2026 {#october-5-11-2026}

### Nuevas funciones

- **Preguntas más frecuentes sobre la vista implementada de datos estructurados (acceso anticipado)**: una vista **implementada** enumera las preguntas más frecuentes sobre las correcciones de datos estructurados implementadas, y muestra la página donde se aplicó cada corrección con un vínculo para abrirla en AEM.

### Mejoras

- **Alertas del sitio y Core Web Vitals (acceso anticipado)** — Muévase entre alertas del sitio y sugerencias de Core Web Vitals con un solo clic. Los incidentes de alerta enlazan a correcciones disponibles y las filas de Core Web Vitals muestran un distintivo **Alerta** cuando la página tiene una alerta de sitio.
- **Comprobaciones en el editor universal**: las auditorías en el editor universal ahora usan el contenido procesado de la página, lo que las hace más rápidas y fiables.
- **Detalles del vínculo de comprobación preliminar**: los vínculos rotos marcados por el verificador de vínculos de AEM ahora muestran el texto visible del vínculo en lugar de un selector CSS.

### Correcciones de errores

- La conexión de una cuenta de Google Ads desde Experience Cloud ahora se realiza de forma fiable, el selector de cuentas ya no se vuelve a abrir después de guardar la selección y la tarjeta de conexión se actualiza después de la desconexión.
- **Implementar** en una fila de datos estructurados de preguntas más frecuentes individual ahora abre el cuadro de diálogo Administrador de varios sitios para que pueda elegir si desea actualizar la página de origen o solo la página local.

## Del 28 de septiembre al 4 de octubre de 2026 {#september-28-october-4-2026}

### Nuevas funciones

- **Oportunidades para agentes de IA personal (acceso anticipado)**: filtre las oportunidades que ayudan a los agentes de IA personal a leer su sitio e interactuar con él, con insignias y directrices que explican los beneficios.

### Mejoras

- **Implementación de vínculo interno interrumpida (acceso anticipado)**: proporcione una URL de reemplazo para un vínculo que no se puede corregir automáticamente e implemente la actualización validada.
- **Estado de publicación de texto alternativo**: vea cuándo se confirma un cambio de texto alternativo activo en la página publicada mientras se conservan los estados de error y redetección claros.
- **Parches de código Core Web Vitals**: revise los parches de archivo por archivo con números de línea y adiciones y eliminaciones resaltadas.
- **Implementación de código Core Web Vitals (acceso anticipado)**: envíe parches de código aptos como solicitud de extracción en el repositorio de código configurado.

### Correcciones de errores

- Las oportunidades de accesibilidad de Forms ahora admiten la creación de problemas de Jira.
- Los vínculos de seguimiento de la implementación ahora abren el repositorio de código configurado.
- Los informes detallados de accesibilidad ahora se abren y muestran su contenido en lugar de redirigirlos a la página principal o aparecer en blanco.
- Los recuentos y grupos de fechas implementados de texto alternativo ahora coinciden con las correcciones mostradas, sin grupos de implementación fallidos vacíos.
- La restauración de las sugerencias de mapas del sitio omitidos y Core Web Vitals ahora actualiza su estado de forma fiable.

## Del 21 al 27 de septiembre de 2026

### Mejoras

- **Preguntas más frecuentes sobre la implementación de datos estructurados (acceso anticipado)**: para las páginas administradas con el Administrador de varios sitios de AEM, elija si desea aplicar actualizaciones de datos estructurados a la página de origen o solo a la página local.
- **Implementación de formulario**: implemente de forma fiable la corrección asociada con la variación de formulario seleccionada.
- **Experiencias localizadas**: Las etiquetas de permisos y el contenido de tabla truncado son más claros en los idiomas compatibles.

### Correcciones de errores

- Las descargas de parches de Core Web Vitals están disponibles siempre que existe un parche.
- Las exportaciones de CSV ahora conservan los caracteres localizados en Excel.
- Las métricas de rendimiento ya no permanecen atascadas al cargarse cuando los datos de origen están incompletos.

## Del 14 al 20 de septiembre de 2026

### Mejoras

- **Permisos granulares**: los administradores pueden otorgar a los miembros acceso a los tipos de oportunidades seleccionados mientras administran los permisos de todo el sitio por separado.

### Correcciones de errores

- La implementación de metadatos ahora restaura la advertencia que se muestra al corregir una página local interrumpe la herencia.

## Del 7 al 13 de septiembre de 2026

### Nuevas funciones

- **Exclusiones de ubicación de Google Ads**: revise los riesgos de ubicación de las cuentas de Google Ads conectadas y descargue listas de exclusión específicas del sitio para campañas automatizadas y Máximo rendimiento.

### Mejoras

- **Guía de errores de implementación**: los mensajes de error ahora explican si una actualización de contenido necesita acceso a la conexión, un nuevo análisis o soporte técnico.

### Correcciones de errores

- Los valores y diseños del informe de accesibilidad ahora se muestran más claramente en los distintos idiomas admitidos.
- El canal de tráfico de pago y los totales de plataforma ahora incluyen tráfico no clasificado anteriormente.
- Los recuentos implementados de vínculos secundarios rotos ahora coinciden con las filas mostradas, incluidos los estados de implementación revertidos y rellenados.
- Los sitios de Edge Delivery Services aptos ya no están bloqueados incorrectamente de la implementación de vínculos rotos.

## Del 31 de agosto al 6 de septiembre de 2026

### Mejoras

- **Conexiones de contenido de AEM**: ahora, la configuración reconoce las configuraciones de Edge Delivery Services creadas por AEM, conserva los detalles de su origen y bloquea las direcciones URL de origen no admitidas antes de guardar.
- **Incorporación de prueba**: la entrada de dominio ahora explica los requisitos del sitio de producción admitidos antes de que se agregue un sitio de prueba.

### Correcciones de errores

- Los selectores y las etiquetas de mes de tráfico de pago ahora se muestran correctamente en los distintos idiomas admitidos.
- Las exportaciones de CSV ahora utilizan la dirección URL de la página correcta de cada problema de accesibilidad.
- Los sitios de Edge Delivery Services aptos ya no están bloqueados incorrectamente de la implementación de texto alternativo.

## 20-27 de agosto de 2026

### Nuevas funciones

- **Vista de alertas**: revise una cronología de 90 días de incidentes de mantenimiento del sitio detectados automáticamente, correlacione cambios con implementaciones y actualizaciones de contenido e inspeccione las páginas afectadas y las métricas de rendimiento en un solo lugar.
- **Informes y ganancias**: utilice la sección Informes para revisar el historial de optimización, las tendencias de rendimiento y las ganancias del antes y después que le ayudarán a comunicar el impacto de su trabajo de optimización.
- **Novedades y Centro de ayuda**: descubra las funciones lanzadas recientemente, abra la documentación del producto y acceda a las notas de la versión directamente desde el Centro de ayuda en la aplicación.
- **Conexión de Google Ads (acceso anticipado)**: conecte una cuenta de Google Ads para incorporar datos de rendimiento de tráfico de pago a las oportunidades y recomendaciones de Sites Optimizer.

### Mejoras

- **Controles de lista de oportunidades**: filtre y ordene oportunidades por dirección URL, estado de estrella, prioridad o actualización, guarde vistas en la dirección URL para compartirlas y exporte los datos de sugerencias al archivo CSV.
- **Controles del flujo de trabajo de sugerencias**: edite las sugerencias generadas por IA antes de la implementación, ignore las sugerencias individuales, omita las oportunidades completas y restaure las oportunidades omitidas cuando vuelvan a ser relevantes.
- **Historial de implementación**: revise el historial de implementación por fecha, distinga las implementaciones automáticas de los cambios marcados como implementados manualmente y siga los vínculos de solicitud de extracción para las correcciones basadas en código.
- **Integraciones de marcas y Slack**: seleccione una marca Adobe GenStudio para generar contenido sin marca y comparta actualizaciones de optimización relevantes con un canal de Slack configurado.

## 6-19 de agosto de 2026

### Nuevas funciones

- **Comprobación preliminar en el editor de páginas de AEM Sites**: si su entorno de creación ejecuta AEM 2026.7.0 o posterior, puede abrir Comprobación preliminar directamente desde la barra de herramientas del editor de páginas para analizar la página actual sin abandonar el flujo de trabajo de creación.
- **Opciones de exportación de comprobaciones**: exporte los resultados de las comprobaciones como CSV o PDF, con opciones para incluir la ejecución de metadatos y las auditorías que se superaron, lo que facilita el uso compartido de conclusiones y el seguimiento de la preparación.

### Mejoras

- **Detalles de la sesión de comprobaciones**: cuando continúa una sesión de auditoría anterior, la comprobación preliminar muestra cuándo se realizó la ejecución y facilita la identificación de los elementos afectados mostrando texto legible o un selector CSS.

## Del 1 al 19 de julio de 2026

### Nuevas funciones

- **Administración de permisos (acceso anticipado)**: los usuarios con la capacidad Administrar usuarios ahora pueden controlar el acceso al sitio desde una nueva ficha Permisos. Busque personas por nombre o correo electrónico y conceda o revoque capacidades específicas. Las acciones que un usuario no puede realizar aparecen deshabilitadas con información sobre herramientas que explica cómo solicitar acceso.
- **Insignias de estado de implementación**: las correcciones marcadas como implementadas manualmente ahora muestran el distintivo &quot;Marcado como implementado&quot; en la vista Implementado, lo que facilita la identificación de las actualizaciones manuales, excepto las implementaciones automáticas.

### Mejoras

- **Corrección automática para GitHub (Cloud Manager)**: La corrección automática de revisión de código para oportunidades como Core Web Vitals, Seguridad y Accesibilidad de formularios ahora puede generar solicitudes de extracción en repositorios de Git propios alojados en GitHub de Cloud Manager, que coinciden con la compatibilidad existente con GitLab, Bitbucket y Azure DevOps. Una nueva opción de configuración permite controlar la confirmación de configuración única del sitio.
- **Corrección automática mediante rama (Cloud Manager Standard)**: La corrección automática mediante rama ya está disponible para los repositorios estándar de Cloud Manager cuando está habilitada para su sitio.
- **Vista implementada: realizada por** — La vista implementada ahora muestra quién marcó cada corrección como implementada y cuándo se actualizó por última vez su estado, a través de las nuevas columnas &quot;Realizado por&quot; y &quot;Última actualización de estado&quot;.
- **Comentarios sobre la desconexión de Google Ads**: al desconectar una cuenta de Google Ads en Configuración ahora se muestra el estado &quot;Desconectando...&quot;, con un mensaje de error que se puede omitir si la desconexión falla y se puede reintentar.

### Correcciones de errores

- La oportunidad Corregir etiquetas ARIA ahora muestra la dirección URL de página correcta en el cuadro de diálogo Detalles cuando una corrección abarca varias páginas.
- El mensaje de información del cuadro de diálogo Omitir ahora se muestra correctamente, con el texto correctamente alineado, en coreano, chino simplificado y chino tradicional.
- Los cuadros de diálogo de páginas relacionadas para Texto alternativo y Metadatos no válidos o que faltan ahora se cargan de forma fiable, y la vista implementada de Metadatos no válidos o que faltan y las correcciones de metaetiquetas ahora funcionan correctamente con el formato de sugerencia más reciente.

## 11-22 de mayo de 2026

### Nuevas funciones

- **Informe de alertas del sitio (acceso anticipado)**: un nuevo informe de alertas del sitio de 90 días proporciona una vista trimestral del estado del sitio, usando bloques diarios con códigos de colores para resaltar períodos de alertas elevadas, de modo que pueda identificar e investigar rápidamente las tendencias a lo largo del tiempo.
- **Incorporación de telemetría operativa**: Los sitios que aún no tienen datos de telemetría operativa conectados ahora reciben un banner persistente en la página de inicio y un cuadro de diálogo de incorporación guiada para completar la configuración, lo que garantiza una visibilidad completa del rendimiento del usuario real.
- **Texto alternativo: reconocimiento del administrador de varios sitios**: al generar correcciones de texto alternativo para sitios que usan AEM Multi-Site Manager o Language Copy, Sites Optimizer ahora comprueba si las correcciones se pueden aplicar de forma segura a cada variante de idioma antes de sugerirlas.

### Mejoras

- **Precisión de texto alternativo**: las sugerencias de texto alternativo ahora se basan en la señal de auditoría más reciente y los problemas detectados de nuevo aparecen en las pestañas Problemas actuales e Implementados para obtener una imagen completa.

### Correcciones de errores

- El estado del botón Implementar ahora refleja correctamente si se puede implementar una corrección.
- El tema oscuro ahora se aplica correctamente al actualizar la página.
- Los informes muestran las fechas en la configuración regional del usuario.
- Las preferencias regionales para el idioma y el formato de número/fecha ahora se pueden configurar de forma independiente.
- El texto alternativo de imagen interrumpida ahora es accesible para los lectores de pantalla.

## Del 21 de abril al 10 de mayo de 2026

### Nuevas funciones

- **No hay ningún estado de integración en el sitio**: los clientes que aún no hayan agregado un sitio verán un mensaje claro y procesable en la página principal para comenzar rápidamente.
- **Documentación en el Centro de ayuda**: ahora se puede acceder directamente a la documentación de AEM Sites Optimizer en Experience League desde el Centro de ayuda en la aplicación, sin salir del producto.

### Correcciones de errores

- Los sitios sin sugerencias activas ahora muestran correctamente un cuadro de diálogo Acción necesaria.
- Las sugerencias omitidas ahora aparecen en la pestaña Ignorado como se espera.
- Los desplegables del selector Tráfico de pago ya no truncan el texto traducido.
- El tamaño del selector de página de mapa del sitio ahora es correcto.

## Del 13 de marzo al 20 de abril de 2026

### Nuevas funciones

- **Incorporación de pruebas**: los nuevos usuarios de prueba ahora experimentan un flujo de configuración guiada: ingresa tu dominio, espera a análisis y luego explora tus primeras oportunidades, no se requiere configuración para comenzar.
- **Página de oportunidades de prueba**: los usuarios de prueba pueden buscar, ordenar y filtrar oportunidades, con tres sugerencias desbloqueadas y las restantes mostradas en una vista previa bloqueada con un mensaje de actualización.
- **Progreso de optimización mensual**: una barra de progreso en la página de inicio hace un seguimiento de cuántas acciones de optimización ha realizado este mes, lo que le ayuda a mantenerse al día con respecto a los objetivos de mantenimiento del sitio.
- **Auditar direcciones URL de destino (acceso anticipado)**: en Configuración, puede especificar hasta 100 direcciones URL personalizadas para garantizar que esas páginas se incluyan siempre en las auditorías.
- **Configuración del tipo de envío**: la configuración ahora le permite especificar el tipo de envío del sitio (Edge Delivery Services, AEM Cloud Service o AEM Managed Services) y conectar con su proveedor de contenido.
- **Rediseño de Core Web Vitals**: la oportunidad de Core Web Vitals se ha rediseñado con vinculación Jira, descarga de CSV y compatibilidad con selecciones múltiples para acciones por lotes.
- **Tabla unificada de vínculos rotos**: los vínculos rotos de todas las fuentes ahora se muestran en una sola tabla unificada, con la capacidad de exportar directamente las reglas de redireccionamiento de CDN.
- **No hay CTA sobre el pliegue: implementar para el autor**: las correcciones para la oportunidad No hay CTA sobre el pliegue ahora se pueden implementar directamente en el autor de AEM.
- **Implementación de correcciones automáticas de Forms**: las correcciones de oportunidades de Forms ahora se pueden implementar directamente en AEM Author.
- **Compatibilidad con AEM Multi-Site Manager**: las oportunidades que afectan a varias copias de idioma de un sitio ahora indican en qué sitio raíz se aplicó la corrección, usando la columna &quot;Fijo en&quot;.
- **Omitir correcciones con errores**: ahora puede omitir las correcciones individuales que hayan fallado en la implementación y mantener el flujo de trabajo desbloqueado.
- **Abrir en el editor de AEM**: las sugerencias de oportunidad ahora incluyen un vínculo directo para abrir la página afectada en el editor visual de AEM para realizar ediciones rápidas en línea.

## Del 28 de febrero al 13 de marzo de 2026

### Nuevas funciones

- **Oportunidad de discrepancia de intenciones de anuncios**: Un nuevo tipo de oportunidad identifica las páginas de aterrizaje de tráfico de pago que no se convierten, que muestran tasa de salida hacia otro sitio, costo por clic y métricas de tráfico para ayudarle a priorizar las mejoras de la página de aterrizaje.
- **Sin CTA encima del pliegue**: esta oportunidad es ahora un tipo de primera clase con su propia página de detalles y filtrado, lo que facilita el seguimiento y la priorización de las mejoras de conversión.
- **Sugerencias de URL de mapa del sitio**: La oportunidad de mapa del sitio ahora sugiere URL de reemplazo para las páginas que devuelven errores 404, lo que facilita la corrección de las entradas de mapa del sitio rotas.
- **Vínculos rotos rediseñados**: la página de detalles Vínculos rotos se ha rediseñado para mejorar la claridad y facilidad de uso.

### Mejoras

- **Páginas de búsqueda orgánica principales V2**: Los datos del tráfico orgánico ahora provienen de un conjunto de datos de 30 días de Ahrefs, lo que proporciona perspectivas de rendimiento de búsqueda más completas y procesables.
- **Vulnerabilidades de seguridad: árbol de dependencias**: los detalles de la vulnerabilidad de seguridad ahora incluyen una visualización del árbol de dependencias para que pueda comprender el impacto total de una vulnerabilidad en todo el proyecto.

## 14-27 de febrero de 2026

### Nuevas funciones

- **Páginas de búsqueda orgánica principales**: el Monitor de estado del sitio ahora incluye una pestaña dedicada que muestra las páginas de tráfico orgánico principales del sitio, lo que le da visibilidad sobre qué contenido genera la mayor cantidad de tráfico de búsqueda.
- **Corrección automática de texto alternativo V2** — Antes de implementar una corrección de texto alternativo, puede ejecutar una evaluación de &quot;Corrección de comprobación&quot; previa al vuelo para verificar que la corrección se pueda aplicar correctamente al contenido.
- **Vista implementada para texto alternativo**: ahora las correcciones de texto alternativo aparecen en una ficha Implementado, lo que le ofrece un historial completo de mejoras de accesibilidad junto con los problemas pendientes actuales.
- **Puerta de implementación de organización externa**: al implementar correcciones en un sitio administrado externamente, ahora se requiere un paso de confirmación explícito para evitar cambios accidentales.

### Mejoras

- **Exenciones de URL de etiquetas de Meta**: ahora se pueden excluir URL específicas de la validación de etiquetas de Meta mediante la configuración, lo que reduce los falsos positivos para títulos intencionalmente cortos o no estándar.
- **Filtrado de URL avanzado**: las listas de oportunidades ahora admiten la coincidencia de prefijos de subruta al filtrar por dirección URL, lo que facilita el enfoque en secciones específicas del sitio.
- **Gráficos de tendencias mejorados**: Los gráficos de tendencias de tráfico ahora administran correctamente los datos año tras año, lo que elimina las caídas engañosas en los límites de los años.

## 6-13 de febrero de 2026

### Nuevas funciones

- **Modo de mantenimiento**: Sites Optimizer ahora gestiona correctamente las ventanas de mantenimiento planificadas, mostrando un mensaje de estado claro en lugar de datos incompletos o engañosos durante el tiempo de inactividad.
- **Vista implementada para vínculos de fondo rotos**: los vínculos de fondo fijos ahora se rastrean en una ficha Implementada, agrupados por fecha, para que pueda ver el historial de corrección de un vistazo.
- **Sin CTA sobre la oportunidad de plegado**: un nuevo tipo de oportunidad muestra páginas en las que no se ve un call-to-action claro sobre el pliegue, lo que le ayuda a identificar y mejorar páginas con bajo potencial de conversión.
- **Integración de Jira para accesibilidad y contraste de color (acceso anticipado)**: las oportunidades de accesibilidad de Forms y Contraste de color ahora se pueden vincular directamente a los tickets de Jira para optimizar el seguimiento de problemas dentro del flujo de trabajo existente.

### Mejoras

- **Vistas implementadas para etiquetas y seguridad de Meta**: las oportunidades de etiquetas y seguridad de Meta ahora incluyen fichas implementadas agrupadas por fecha, coherentes con otros tipos de oportunidades.
- **Seguimiento de implementación de texto alternativo** — &quot;Marcar como implementado&quot; ya está disponible para correcciones de texto alternativo y el texto alternativo editado manualmente se conserva durante las ejecuciones de reanálisis.

## Del 26 de enero al 6 de febrero de 2026

### Nuevas funciones

- **Vista implementada para Canonical y Hreflang**: los cambios en las oportunidades Canonical y Hreflang ahora se agrupan por fecha de implementación en una ficha Implementado, lo que le proporciona un historial claro de lo que se ha corregido y cuándo.
- **Exportación de CSV**: ahora puede exportar a CSV los datos de oportunidad para las oportunidades de High Organic Low CTR y Forms para el análisis y la creación de informes sin conexión.
- **Oportunidades favoritas**: inicia cualquier oportunidad desde el encabezado para agregarla a tus favoritos, lo que hace que sea más rápido volver a las oportunidades en las que estás trabajando activamente.
- **Vista implementada para cadenas de redireccionamiento**: ahora las correcciones de cadenas de redireccionamiento se pueden marcar como Implementadas directamente desde la página de detalles.

### Mejoras

- **Estimaciones de costos de banners de cookies mejoradas** — Los cálculos de costos para la oportunidad de Banner de cookies se han refinado para lograr una mayor precisión.

## 16-23 de enero de 2026

### Nuevas funciones

- **Monitor de estado del sitio (disponibilidad general)**: el Monitor de estado del sitio ya está disponible para todos los clientes y proporciona una vista continua del estado de rendimiento del sitio. Los nuevos sitios se configuran automáticamente al incorporarse.
- **Compatibilidad con sitios de subrutas**: los sitios con ámbitos de subrutas de URL específicas ahora son totalmente compatibles con el Monitor de estado del sitio.

### Mejoras

- **Avisos de suficiencia de datos procesables**: las oportunidades de tráfico de pago con menos de 1000 vistas de página ahora muestran un aviso de suficiencia de datos, lo que le ayuda a enfocar los esfuerzos de optimización donde los datos de tráfico tienen significado estadístico.
- **Validación flexible de títulos de Meta**: se ha reducido el requisito mínimo de caracteres para los metatítulos, lo que le proporciona más flexibilidad para crear títulos de páginas concisos.
- **Diálogo localizado de novedades**: el cuadro de diálogo de anuncios de funciones en la aplicación ahora se muestra en su idioma preferido.
- **Insignia publicada**: las variaciones en la oportunidad de CTR baja y orgánica alta que se han implementado ahora muestran una insignia &quot;Publicada&quot;, lo que facilita distinguir los cambios activos de los pendientes.
- **Vínculos de solicitud de extracción en Accesibilidad**: la ficha Implementada de la oportunidad de accesibilidad ahora muestra la dirección URL de solicitud de extracción asociada para cada corrección, lo que facilita el seguimiento de los cambios en el historial de control de código fuente.
