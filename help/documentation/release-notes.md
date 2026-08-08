---
title: Notas de la versión
description: Obtenga información sobre las últimas funciones, mejoras y correcciones de errores en Adobe Experience Manager Sites Optimizer.
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 9af59e18de7ce016778f25d4add450b50e0b1fde
workflow-type: tm+mt
source-wordcount: 1805
ht-degree: 1%

---


# Notas de la versión

Esta página documenta las últimas actualizaciones, nuevas funciones y mejoras de Adobe Experience Manager Sites Optimizer.

Las características marcadas **(acceso anticipado)** están disponibles bajo petición; póngase en contacto con el equipo de su cuenta o con el ingeniero de éxito del cliente para habilitarlas en su organización.

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
