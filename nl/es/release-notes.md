---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-09"

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

## Agosto de 2018
{: #august2018}

### Novedades y modificaciones
{: #new-august2018}

- Se ha introducido una nueva opción para la migración automatizada de las instancias de plan estándar desde la plataforma {{site.data.keyword.IBM_notm}} Marketplace en desuso a la [plataforma {{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/blogs/bluemix/2017/12/watson-knowledge-studio-ibm-cloud/){: new_window}. Si tiene una instancia estándar en la plataforma en desuso, tendrá la opción de migrar. Para obtener más información, consulte [Migración a {{site.data.keyword.cloud_notm}}](/docs/services/watson-knowledge-studio/client-migration.html).

## Julio de 2018
{: #july2018}

### Novedades y modificaciones
{: #new-july2018}

- La página **Modelos desplegados** se ha actualizado para incluir modelos de las instancias de {{site.data.keyword.knowledgestudioshort}} gestionadas por [*grupos de recursos* de IAM ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/iam/users_roles.html){: new_window}, además de modelos gestionados por [*organizaciones* de Cloud Foundry ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/iam/cfaccess.html){: new_window}.

   Lo que ve en la página Modelos desplegados depende de la [región ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/resources/services_region.html){: new_window} que aloja la instancia de {{site.data.keyword.knowledgestudioshort}}. Si la región da soporte a instancias gestionadas por los dos métodos de gestión de acceso, verá un separador para cada método. Los modelos de las instancias gestionadas por IAM se listan en el separador **Grupos de recursos**. Los modelos de las instancias gestionadas por Cloud Foundry se listan en el separador **Organizaciones**.

  Si la región da soporte a instancias gestionadas por sólo uno de los métodos de gestión de acceso, sólo verá una lista de modelos, porque sólo será aplicable un método de gestión de acceso.

   Para ver la página **Modelos desplegados**, desde el menú **Configuración** de la barra de menús de la parte superior derecha, pulse **Gestionar modelos desplegados**. Para obtener información sobre la retirada de modelos en la página **Modelos desplegados**, consulte [Retirada de modelos de aprendizaje automático](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) y [Retirada de modelos basados en reglas](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model).

- La navegación se ha cambiado para que se ajuste mejor al flujo de trabajo de {{site.data.keyword.knowledgestudioshort}}. Además, se han reorganizado las funciones siguientes:

    - En la versión anterior, la gestión de los diccionarios estaba incluida como parte de la página Preanotadores. Ahora, la gestión de los diccionarios se encuentra en la página Diccionarios de la sección Activos de la navegación.
    - En la versión anterior, las funciones de anotación humana estaban distribuidas en los separadores Menciones, Relaciones y Correferencias en la sección Anotación de documentos de la navegación. Ahora, esta funcionalidad se ha incorporado a la página Tareas de anotación en la sección Modelo de aprendizaje automático de la navegación.
    - Para gestionar las tareas de anotación humana, en la versión anterior estaba disponible el separador Tareas en la página Activos y herramientas > Documentos. Ahora, las tareas se añaden y se gestionan en la página Tareas de anotación en la sección Modelo de aprendizaje automático de la navegación.
    - En la versión anterior, las páginas Reglas, Expresiones regulares y Diccionarios eran páginas independientes en la sección Anotación de documentos de la navegación. Ahora, esta funcionalidad se ha incorporado a la página Reglas en la sección Modelo basado en reglas de la navegación.

    Para obtener más detalles sobre los cambios de navegación, consulte la Figura 1 y la Tabla 3.

![Capturas de pantalla de la navegación anterior (lado izquierdo) y de la navegación nueva (lado derecho).](images/nav3-0718.svg "Capturas de pantalla de la navegación anterior y de la navegación nueva. Los detalles de los cambios están enumerados en la Tabla 3 y en el texto anterior.") Figura 1. Capturas de pantalla de la navegación anterior (lado izquierdo) y de la navegación nueva (lado derecho).

| Característica | Ubicación anterior | Ubicación actual |
|---------|--------------------------|----------------------|
| Tareas de anotación | Activos y herramientas > Documentos > Tareas | Modelo de aprendizaje automático > Tareas de anotación |
| Separador Correferencias | Anotación de documentos | Modelo de aprendizaje automático > Tareas de anotación > tarea > conjunto de anotación > documento |
| Página Diccionarios (gestión) | Activos y herramientas > Preanotadores > Gestionar diccionarios | Activos |
| Separador Diccionarios (correspondencia con clases para el modelo basado en reglas) | Anotación de documentos | Modelo basado en reglas > Reglas |
| Página Documentos | Activos y herramientas | Activos |
| Página Tipos de entidades | Activos y herramientas | Activos |
| Separador menciones | Anotación de documentos | Modelo de aprendizaje automático > Tareas de anotación > tarea > conjunto de anotación > documento |
| Página Rendimiento | Gestión de modelos | Modelo de aprendizaje automático |
| Página Preanotadores | Activos y herramientas | Modelo de aprendizaje automático > Preanotación |
| Separador Expresión regular | Anotación de documentos | Modelo basado en reglas > Reglas |
| Página Tipos de relaciones | Activos y herramientas | Activos |
| Separador Relaciones | Anotación de documentos | Modelo de aprendizaje automático > Tareas de anotación > tarea > conjunto de anotación > documento |
| Separador Reglas | Anotación de documentos | Modelo basado en reglas |
| Separador Tareas | Activos y herramientas > Documentos | Modelo de aprendizaje automático > Tareas de anotación |
| Página Versiones (modelo de aprendizaje automático) | Gestión de modelos | Modelo de aprendizaje automático |
| Página Versiones (modelo basado en reglas) | Gestión de modelos | Modelo basado en reglas |
{: caption="Tabla 3. Cambios de navegación (julio de 2018)" caption-side="top"}

## Mayo de 2018
{: #may2018}

### Novedades y modificaciones
{: #new-may2018}

- Se ha solucionado un problema de configuración que provocaba que las instancias de servicio en la región de Sídney no apareciesen en la región EE.UU. sur.
- En la ventana Desplegar modelo, si la región en la que va a desplegar admite los *grupos de recursos* de {{site.data.keyword.iamlong}} y los *espacios* de Cloud Foundry, para ver la lista, necesitará elegir el método de gestión de accesos que utiliza la instancia de servicio. Para obtener más información acerca de Cloud Foundry y {{site.data.keyword.iamshort}}, consulte [Gestión de acceso y grupos de recursos ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/blogs/bluemix/2017/12/resource-groups-access-management/){: new_window}.
- Se ha añadido el valor de recopilación de datos en la página Detalles de servicio. Para obtener más información sobre la recopilación de datos, consulte [Resolución de problemas, soporte y preguntas frecuentes](/docs/services/watson-knowledge-studio/troubleshooting.html#content)
- Se ha añadido soporte de idioma chino (tradicional).
- Los usuarios que tienen el rol Admin ahora pueden ver el número de espacios de trabajo que se utilizan. Esta información está disponible en la página Detalles de servicio.
- {{site.data.keyword.alchemylanguagefull}} ya no está disponible para desplegar modelos. Para obtener información, consulte [Retirada de servicio de {{site.data.keyword.alchemyapishort}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/blogs/bluemix/2017/03/bye-bye-alchemyapi/){: new_window}.
- Ahora, si suprime un espacio de trabajo, se le solicitará que confirme la acción. Esperamos que esta confirmación impida las eliminaciones accidentales.
- La documentación incluye algunos detalles nuevos sobre la privacidad de los datos. Consulte más información en [Seguridad de la información](/docs/services/watson-knowledge-studio/information-security.html).

## Abril de 2018
{: #april2018}

### Novedades y modificaciones
{: #new-april2018}

- El plan gratuito de {{site.data.keyword.knowledgestudioshort}} ha sido sustituido por el plan Lite. Para obtener más información, consulte [Obtenga la versión Lite de Watson {{site.data.keyword.knowledgestudioshort}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/blogs/bluemix/2018/04/go-lite-watson-knowledge-studio/){: new_window}.

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
