---

copyright:
  years: 2015, 2018
lastupdated: "2018-04-04"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

Esta documentación es para {{site.data.keyword.knowledgestudiofull}} en {{site.data.keyword.cloud}}. Para ver la documentación para la versión anterior de {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.IBM_notm}} Marketplace, [pulse este enlace ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/services/knowledge-studio/release-notes.html){: new_window}.
{: tip}

# Notas del release
{: #release-notes}

Están disponibles las siguientes novedades y modificaciones en {{site.data.keyword.knowledgestudiofull}}.
{: shortdesc}

## Marzo de 2018
{: #march2018}

### Novedades y modificaciones
{: #new-march2018}

- Hay disponible una página **Modelos desplegados** donde puede ver todos los modelos de {{site.data.keyword.knowledgestudioshort}} desplegados en los servicios en los espacios a los que tiene acceso. Para ver la página **Modelos desplegados**, desde el menú **Configuración** de la barra de menús de la parte superior derecha, pulse **Gestionar modelos desplegados**. Para obtener información sobre la retirada y la visualización de modelos en la página **Modelos desplegados**, consulte [Retirada de modelos de aprendizaje automático](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) y [Retirada de modelos basados en reglas](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model).
- Hay disponible una traducción en francés de la interfaz de {{site.data.keyword.knowledgestudioshort}}.
- {{site.data.keyword.alchemylanguagefull}} ya no está disponible como preanotador. En lugar de {{site.data.keyword.alchemylanguageshort}}, puede utilizar {{site.data.keyword.nlushort}} para preanotar los documentos. Para obtener más información, consulte [Anotación de arranque](/docs/services/watson-knowledge-studio/preannotation.html).

## Diciembre de 2017
{: #december2017}

### Novedades y modificaciones
{: #new-december2017}

- {{site.data.keyword.knowledgestudioshort}} se inició en {{site.data.keyword.cloud_notm}}. Para obtener información sobre el proceso de migración y su planificación, consulte [Migración a {{site.data.keyword.cloud_notm}}](/docs/services/watson-knowledge-studio/client-migration.html).
- Navegación rediseñada. Para obtener detalles sobre los cambios de navegación, consulte [Tabla 2](#september2017) en las notas de release de septiembre de 2017.
- Se ha añadido {{site.data.keyword.nlufull}} como preanotador.
- Se han añadido valores de gestión de usuarios y de almacenamiento a la página Detalles de servicio. Para obtener información sobre cómo añadir usuarios, consulte [Ensamblaje de un equipo](/docs/services/watson-knowledge-studio/team.html). Para obtener información sobre el establecimiento de límites de almacenamiento, consulte [Resolución de problemas > Problemas de espacio de almacenamiento](/docs/services/watson-knowledge-studio/troubleshooting.html#storage).
- Se ha añadido una página Rendimiento para la evaluación y la orientación de la calidad del modelo sobre cómo mejorar la calidad.

## Noviembre de 2017
{: #november2017}

### Modificaciones
{: #new-november2017}

- Se ha solucionado un problema donde faltaban algunas anotaciones de relación en el corpus descargado.
- Se ha solucionado un problema donde un modelo no se podía retirar del despliegue si su estado era **Ninguno**.
- Se ha solucionado un problema donde el modelo no se ha podido evaluar para coreano.

## Octubre de 2017
{: #october2017}

### Modificaciones
{: #new-october2017}

- Se ha solucionado el problema con el botón **Exportar** que no se podía habilitar hasta que renovara la ventana del navegador en el release [experimental](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) de {{site.data.keyword.Bluemix_notm}}.
- Se han solucionado las etiquetas y las ayudas contextuales del botón para que coincidan con los cambios para los términos _cargar_ y _descargar_ en el release [experimental](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) de {{site.data.keyword.Bluemix_notm}}. Se utilizan estos términos en lugar de _importar_ y _exportar_ al referirse a sistemas de tipos, documentos y diccionarios.
- Se ha solucionado el retraso en la actualización de las descripciones en la página Gestión de cuentas de usuario de {{site.data.keyword.knowledgestudioshort}} en el release [experimental](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) de {{site.data.keyword.Bluemix_notm}}.
- En la sección de preanotación de la interfaz, realizó un par de cambios de GUI para aclarar la funcionalidad del modelo de aprendizaje automático, el modelo basado en reglas, el diccionario y {{site.data.keyword.alchemylanguagefull}}. Se ha modificado la etiqueta del botón de **Ejecutar** a **Preanotar**, se ha modificado el título de la ventana de **Ejecutar anotador** a **Ejecutar preanotación**, y se ha modificado el mensaje de error para aclarar que no puede añadir anotaciones automatizadas una vez que los humanos hayan anotado los documentos.
- Para los proyectos o los espacios de trabajo que utilizan señalizadores basados en diccionario, se ha solucionado un problema que mostraba frases vacías si ha importado los documentos sin datos de campo.

## Septiembre de 2017
{: #september2017}

### Novedades y modificaciones
{: #new-sept17}

- Se ha lanzado una nueva experiencia de usuario frontal para {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.Bluemix}} como un servicio [experimental](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental). Las modificaciones incluyen una navegación reorganizada y una nueva página de análisis de rendimiento del modelo. Para obtener un resumen de las modificaciones de navegación, consulte la tabla en los problemas conocidos.
- Se ha añadido soporte de idiomas en chino (simplificado) y neerlandés.

### Problemas conocidos
{: #issues-sept17}

- Para un modelo basado en reglas, después de correlacionar clases y tipos de entidades, el botón **Exportar** no estará habilitado hasta que renueve la ventana de navegador.
- Para el release [experimental](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) de {{site.data.keyword.Bluemix_notm}}, alguna de la terminología de documentación no coincide con la nueva interfaz. La documentación coincide con la interfaz de {{site.data.keyword.IBM_notm}} Marketplace. Los términos siguientes han cambiado en el release [experimental](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental):

| Término en {{site.data.keyword.IBM_notm}} Marketplace | Término en {{site.data.keyword.Bluemix_notm}} | Notas |
|----------|----------|----------|
| _proyecto_ | _espacio de trabajo_ | Este término se ha cambiado porque {{site.data.keyword.Bluemix_notm}} también utiliza el término _proyecto_ |
| _importar_ y _exportar_ | _cargar_ y _descargar_ | Los términos _importar_ y _exportar_ ahora se llaman _cargar_ y _descargar_ cuando se utilizan en términos de documentos y tipos de entidades. El término _exportar_ todavía se utiliza cuando se refiere a exportar un modelo a aplicaciones como {{site.data.keyword.watson}} Explorer. |
{: caption="Tabla 1. Cambios de terminología para la versión de {{site.data.keyword.Bluemix_notm}}" caption-side="top"}

- Para el release [experimental](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) de {{site.data.keyword.Bluemix_notm}}, algunos de los pasos de la tarea de documentación no coinciden con la nueva interfaz. La documentación coincide con la interfaz de {{site.data.keyword.IBM_notm}} Marketplace. La tabla siguiente resume los cambios de navegación para el release [experimental](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental):

| Característica | Ubicación de {{site.data.keyword.IBM_notm}} Marketplace | Ubicación de {{site.data.keyword.Bluemix_notm}}
|----------|----------|----------|
|Separador Componente de anotador | Navegación principal | Ya no existe |
|Tabla Matriz de confusión (desde el separador Estadísticas) | Componente de anotador > Detalles | Gestión de modelos > Rendimiento > Enlace Estadísticas detalladas |
|Separador Diccionarios | Navegación principal | Activos y herramientas > Preanotadores |
|Página Correlación de diccionarios | Componente de anotador | Activos y herramientas > Preanotadores |
|Separador Tipos de entidades | Sistema de tipos | Activos y herramientas > Tipos de entidades |
|Editor de datos de campo | Anotación humana | Separador Anotación de documentos |
|Separador Configuración del editor de datos de campo | Anotación humana | Configuración > Configuración de la anotación de documentos |
|Modelos, ejecución y exportación | Componente de anotador | Gestión de modelos > Versiones |
|Separador Reglas | Navegación principal | Anotación de documentos > Reglas |
|Separador Estadísticas | Componente de anotador > Detalles | Gestión de modelos > Rendimiento |
|Tabla Resumen (desde el separador Estadísticas) | Componente de anotador > Detalles | Gestión de modelos > Rendimiento > Enlace Estadísticas detalladas |
|Separador Correlación de tipos (para el modelo basado en reglas) | Componente de anotador > Detalles | Gestión de modelos > Versiones > Correlación de tipos de modelos basados en reglas |
{: caption="Tabla 2. Cambios de navegación para la versión de {{site.data.keyword.Bluemix_notm}}" caption-side="top"}

## Julio de 2017
{: #july2017}

- Se ha solucionado un defecto que, en algunos casos, hizo que la cabecera desapareciera
- Se han aplicado actualizaciones de seguridad para los componentes de infraestructura

## Junio de 2017
{: #june2017}

- Se ha mejorado la estabilidad para manejar datos grandes en determinadas condiciones
- Se ha solucionado un defecto para un error de adjudicación

## Mayo de 2017
{: #may2017}

- Se ha añadido la capacidad para renombrar varios objetos, como proyectos, conjuntos de documentos, etc.
- Se ha añadido la capacidad para desplegar modelos de NLU en regiones de {{site.data.keyword.Bluemix}} específicas
- Se ha mejorado el rendimiento para mostrar una tabla grande para IAA
- Se han solucionado defectos menores
- Se han aplicado arreglos de seguridad

## Abril de 2017
{: #april2017}

- Se ha mejorado la estabilidad para {{site.data.keyword.knowledgestudioshort}} Premium
- Se ha añadido análisis de uso para métricas empresariales

## Releases anteriores a abril de 2017

Consulte [Nota técnica número 1986001 de {{site.data.keyword.IBM_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://www.ibm.com/support/docview.wss?uid=swg21986001){: new_window}.
