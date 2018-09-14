---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-14"

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

Esta documentación es para {{site.data.keyword.knowledgestudiofull}} en {{site.data.keyword.cloud}}. Para ver la documentación para la versión anterior de {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.IBM_notm}} Marketplace, [pulse este enlace ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/services/knowledge-studio/rule-annotator-model-use.html){: new_window}.
{: tip}

# Uso del modelo basado en reglas
{: #wks_rule_publish}

Aproveche un modelo basado en reglas que haya creado con {{site.data.keyword.knowledgestudioshort}} haciéndolo disponible para otras aplicaciones de {{site.data.keyword.watson}}.
{: shortdesc}

**Atención**: Puede desplegar un modelo basado en reglas para hacerlo disponible para su uso en estos servicios como una característica [experimental](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental).

Antes de que se pueda desplegar un modelo para que lo utilice un servicio, debe tener una suscripción al servicio. Los servicios de {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} están alojados en {{site.data.keyword.Bluemix_notm}}, que es la plataforma en la nube para {{site.data.keyword.IBM_notm}}. Consulte [¿Qué es {{site.data.keyword.Bluemix_notm}}? ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.ng.bluemix.net/docs/overview/whatisbluemix.html){: new_window} para obtener más información sobre la plataforma. Para suscribirse a uno de los servicios de {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}}, cree una cuenta desde el sitio web de [{{site.data.keyword.Bluemix_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.ng.bluemix.net/){: new_window}.

Para algunos de los servicios, debe conocer los detalles sobre la instancia de servicio a la que tiene pensado desplegar, como por ejemplo el nombre de espacio y el nombre de la instancia de servicio de {{site.data.keyword.Bluemix_notm}}. La información del nombre de espacio y de la instancia está disponible desde la página de servicios de {{site.data.keyword.Bluemix_notm}}.

También puede preanotar documentos nuevos con el modelo basado en reglas. Consulte [Preanotación de documentos con el modelo basado en reglas](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotrule) para obtener detalles.

## Despliegue de un modelo basado en reglas en IBM Watson Discovery
{: #wks_rule_discovery}

Despliegue el modelo para habilitar una aplicación que utiliza el servicio de {{site.data.keyword.discoveryshort}} para utilizar el modelo basado en reglas para buscar y extraer entidades durante el enriquecimiento del documento.

**Atención**: Esta es en este momento una característica [experimental](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) del servicio.

### Antes de empezar
{: #wks_rule_discovery_prereqs}

Debe tener acceso administrativo a una instancia de servicio de {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}, y conocer los nombres de los espacios y de las instancias de {{site.data.keyword.Bluemix_notm}} asociados con ella.

### Procedimiento
{: #wks_rule_discovery_procedure}

Para desplegar un modelo basado en reglas en {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}, siga estos pasos:

1. Inicie sesión como un administrador o gestor de proyectos de {{site.data.keyword.knowledgestudioshort}}, y seleccione su espacio de trabajo.
1. Seleccione el separador **Modelo basado en reglas** > **Versiones** > **Modelo basado en reglas**.
1. Seleccione la versión del modelo que desea desplegar.

    Si solo hay una versión que funciona del modelo, guarde el modelo actual para su despliegue pulsando **Guardar para despliegue**. Esto versiona el modelo, lo que permite desplegar una versión, mientras sigue mejorando la versión actual. Guardar la versión puede tardar unos minutos. La opción para desplegar no aparecerá hasta que se cree la versión.

    **Nota**: Cada versión se puede desplegar en una sola instancia de servicio. Si desea desplegar el mismo modelo en más de una instancia, cree una versión para cada instancia.

1. Pulse **Desplegar**, elija desplegarla en {{site.data.keyword.discoveryshort}} y, a continuación, pulse **Siguiente**.
1. Proporcione el espacio y la instancia de {{site.data.keyword.Bluemix_notm}}. Si es necesario, seleccione una región distinta.
1. Pulse **Desplegar**.
1. El proceso de despliegue puede tardar unos minutos. Para comprobar el estado del despliegue, pulse **Estado** en el separador **Versiones** junto a la versión que ha desplegado.

    Si el modelo se está desplegando todavía, el estado indica "publicando". Cuando finalice el despliegue, el estado cambiará a "disponible" si el despliegue fue correcto, o "error" si se producen problemas.

    Una vez disponible, tome nota del ID de modelo (model_id). Proporcionará este ID al servicio de {{site.data.keyword.discoveryshort}} para permitir al servicio que utilice su modelo personalizado.

### Qué hacer a continuación
{: #wks_rule_discovery_next}

Para utilizar el modelo desplegado, debe proporcionar el ID de modelo cuando se solicite durante el proceso de configuración de enriquecimiento del servicio de {{site.data.keyword.discoveryshort}}.

## Despliegue de un modelo basado en reglas en IBM Watson Natural Language Understanding
{: #wks_rule_nlu}

Despliegue el modelo basado en reglas para habilitar una aplicación que utiliza el servicio de {{site.data.keyword.nlushort}} para utilizar el modelo para buscar y extraer entidades relevantes para su dominio.

**Atención**: Esta es en este momento una característica [experimental](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) del servicio.

### Antes de empezar
{: #wks_rule_prereqs}

Debe tener acceso administrativo a una instancia de servicio de {{site.data.keyword.nlushort}}, y conocer los nombres de los espacios y de las instancias de {{site.data.keyword.Bluemix_notm}} asociados con ella.

### Procedimiento
{: #wks_rule_procedure}

Para desplegar un modelo basado en reglas en {{site.data.keyword.nlushort}}, siga estos pasos:

1. Inicie sesión como un administrador o gestor de proyectos de {{site.data.keyword.knowledgestudioshort}}, y seleccione su espacio de trabajo.
1. Seleccione el separador **Modelo basado en reglas** > **Versiones** > **Modelo basado en reglas**.
1. Seleccione la versión del modelo que desea desplegar.

    Si solo hay una versión que funciona del modelo, guarde el modelo actual para su despliegue pulsando **Guardar para despliegue**. Esto versiona el modelo, lo que permite desplegar una versión, mientras sigue mejorando la versión actual. Guardar la versión puede tardar unos minutos. La opción para desplegar no aparecerá hasta que se cree la versión.

    **Nota**: Cada versión se puede desplegar en una sola instancia de servicio. Si desea desplegar el mismo modelo en más de una instancia, cree una versión para cada instancia.

1. Pulse **Desplegar**, elija desplegarla en {{site.data.keyword.nlushort}} y, a continuación, pulse **Siguiente**.
1. Proporcione el espacio y la instancia de {{site.data.keyword.Bluemix_notm}}. Si es necesario, seleccione una región distinta.
1. Pulse **Desplegar**.
1. El proceso de despliegue puede tardar unos minutos. Para comprobar el estado del despliegue, pulse **Estado** en el separador **Versiones** junto a la versión que ha desplegado.

    Si el modelo se está desplegando todavía, el estado indica "publicando". Cuando finalice el despliegue, el estado cambiará a "disponible" si el despliegue fue correcto, o "error" si se producen problemas.

    Una vez disponible, tome nota del ID de modelo (model_id). Proporcionará este ID al servicio de {{site.data.keyword.nlushort}} para permitir al servicio que utilice su modelo personalizado.

### Qué hacer a continuación
{: #wks_rule_next}

Para utilizar el modelo desplegado, debe especificar el ID de modelo del modelo personalizado en el parámetro `entities.model`.

Puede utilizar el modelo con la solicitud {{site.data.keyword.nlushort}} `GET /analyze` para extraer entidades.

Consulte la [documentación de {{site.data.keyword.nlushort}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/services/natural-language-understanding/index.html){: new_window} para obtener más detalles.

## Retirada de modelos
{: #undeploy-view-model}

Si desea retirar un modelo o buscar un ID de modelo, vea la página **Modelos desplegados**.

### Acerca de esta tarea
{: #wks_undeploy_about}

Lo que ve en la página Modelos desplegados depende de la [región ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/resources/services_region.html){: new_window} que aloja la instancia de {{site.data.keyword.knowledgestudioshort}}. Si la región da soporte a instancias gestionadas por los métodos de gestión de acceso [IAM ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/iam/users_roles.html){: new_window} y [Cloud Foundry ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/iam/cfaccess.html){: new_window}, verá un separador para cada método. Los modelos de las instancias gestionadas por IAM se listan en el separador **Grupos de recursos**. Los modelos de las instancias gestionadas por Cloud Foundry se listan en el separador **Organizaciones**.

Si la región da soporte a instancias gestionadas por sólo uno de los métodos de gestión de acceso, sólo verá una lista de modelos, porque sólo será aplicable un método de gestión de acceso.

### Procedimiento
{: #wks_deploy_procedure}

Para retirar modelos o buscar los ID de modelo:

1. Inicie {{site.data.keyword.knowledgestudioshort}}.
1. Desde el menú **Configuración** en la barra de menús de la parte superior derecha, seleccione **Gestionar modelos desplegados**.
1. En la lista de modelos desplegados, busque el modelo que desee ver o retirar.
1. Para retirar el modelo, desde la última columna de la fila, pulse **Retirar modelo**.
1. Para encontrar el ID de modelo, consulte la columna **ID de modelo**.

De forma alternativa, puede retirar el despliegue de modelos de las páginas Versiones para modelos basados en reglas y modelos de aprendizaje automático.

## Aprovechar un modelo basado en reglas en IBM Watson Explorer
{: #wks_rule_export}

Exporte el archivo PEAR que se produce cuando el modelo basado en reglas se crea para que pueda utilizarse en {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.

### Procedimiento
{: #wks_rule_export_procedure}

Para aprovechar un modelo basado en reglas en {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, siga estos pasos.

1. Inicie sesión como un administrador o gestor de proyectos de {{site.data.keyword.knowledgestudioshort}}, y seleccione su espacio de trabajo.
1. Seleccione el separador **Modelo basado en reglas** > **Versiones** > **Modelo basado en reglas**.
1. Pulse **Exportar modelo actual**.

    Si tiene una suscripción a un plan Lite, no habrá disponible ninguna opción de exportación.

    El modelo se guarda como un archivo PEAR, y se le solicitará que descargue el archivo. Un archivo PEAR (Processing Engine ARchive) es el formato de empaquetado estándar de UIMA para los componentes UIMA. El modelo se guarda en formato PEAR para que se pueda distribuir y reutilizar dentro de aplicaciones UIMA.

1. Descargue el archivo a su sistema local.
1. Desde la aplicación de {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, importe el archivo PEAR.
