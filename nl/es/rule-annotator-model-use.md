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

## Despliegue de un modelo basado en reglas en AlchemyLanguage
{: #wks_rule_bluemix}

Esta característica permite que las aplicaciones utilicen el modelo basado en reglas desplegado para buscar y extraer entidades de documentos en su dominio.

**Atención**: Esta es en este momento una característica [experimental](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) del servicio.

### Antes de empezar

Debe tener el plan Avanzado del servicio de {{site.data.keyword.alchemylanguageshort}} para utilizar este modelo personalizado.

### Acerca de esta tarea

Para desplegar en este servicio, debe tener una clave de acceso de {{site.data.keyword.IBM_notm}} {{site.data.keyword.alchemylanguageshort}}.

La clave debe pertenecer a una cuenta autorizada a publicar modelos personalizados o el modelo se desplegará correctamente, pero no podrá utilizarlo.

Al desplegar el modelo basado en reglas, seleccione la versión del mismo que desee desplegar. Debe especificar la clave la primera vez que despliegue un modelo en {{site.data.keyword.alchemylanguageshort}}. A continuación, puede reutilizar la clave con varias versiones del modelo que se despliega. Cada clave tiene un número máximo de modelos que se pueden desplegar al mismo tiempo.

### Procedimiento

Para desplegar un modelo basado en reglas en {{site.data.keyword.alchemylanguageshort}}:

1. Inicie sesión como un administrador o gestor de proyectos de {{site.data.keyword.knowledgestudioshort}}, y seleccione su espacio de trabajo.
1. Seleccione el separador **Gestión de modelos** > **Versiones** > **Basado en reglas**.
1. Seleccione la versión del modelo que desea desplegar.

    Si solo hay una versión que funciona del modelo, guarde el modelo actual para su despliegue pulsando **Guardar para despliegue**. Al pulsar **Guardar para despliegue** se creará una versión del modelo, lo que permite desplegar una versión mientras sigue mejorando la versión actual. Guardar la versión puede tardar unos minutos. La opción para desplegar no aparecerá hasta que se cree la versión.

1. Pulse **Desplegar**, elija desplegarla en {{site.data.keyword.alchemylanguageshort}} y, a continuación, pulse **Siguiente**.
1. Especifique la clave que ha obtenido desde {{site.data.keyword.alchemylanguageshort}} o seleccione una versión previamente desplegada del modelo que tiene una clave que desee reutilizar, y pulse **Desplegar**. Si la clave es válida, se mostrará una confirmación que contiene el ID del modelo. Esta confirmación no significa que el modelo esté listo para que lo utilicen sus aplicaciones.
1. El proceso de despliegue puede tardar unos minutos. Para comprobar el estado del despliegue, pulse **Estado** junto a la versión que ha desplegado. Si el modelo se está desplegando todavía, el estado indica "publicando". Cuando finalice el despliegue, el estado cambiará a "disponible" si el despliegue fue correcto, o "error" si se producen problemas.

    La información de estado incluye el ID de modelo, los últimos cuatro dígitos de la clave de {{site.data.keyword.alchemyapishort}} y un registro del proceso de despliegue. El ID de modelo (model_id) es cómo llaman sus aplicaciones al modelo de aprendizaje automático. Tome nota de este ID de modelo porque no hay forma programática para acceder más adelante. Utilice la clave de {{site.data.keyword.alchemyapishort}} para realizar el seguimiento del número de despliegues por clave.

### Qué hacer a continuación

Para utilizar el modelo desplegado, debe copiar y pegar el ID de modelo a la llamada de la API de su aplicación.

> **Atención:** No puede utilizar la llamada de API `GET /info/models` {{site.data.keyword.alchemylanguageshort}} para obtener el ID de modelo de modelos basados en reglas mediante programación. Puede acceder al ID de modelo de modelos de aprendizaje automático con esta llamada, pero no al ID de modelo basado en reglas.

La llamada también debe especificar el servicio de {{site.data.keyword.alchemylanguageshort}} que desea utilizar con el modelo y la clave de acceso de {{site.data.keyword.alchemyapishort}}.

Se admite el siguiente punto final:

- **&lt;*input-type*&gt;GetRankedNamedEntities**

    Utiliza el modelo personalizado que especifique en el parámetro del modelo para extraer una lista de menciones de todos los tipos de entidades conocidos que encuentre en la entrada que proporcione. Los tipos de entrada soportados incluyen texto, HTML o un URL público. Consulte [{{site.data.keyword.alchemylanguageshort}}&gt;Entities ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/smarterplanet/us/en/ibmwatson/developercloud/alchemy-language/api/v1/#entities){: new_window} para obtener más información sobre la API y la sintaxis a utilizar.

## Despliegue de un modelo basado en reglas en IBM Watson Discovery
{: #wks_rule_discovery}

Despliegue el modelo para habilitar una aplicación que utiliza el servicio de {{site.data.keyword.discoveryshort}} para utilizar el modelo basado en reglas para buscar y extraer entidades durante el enriquecimiento del documento.

**Atención**: Esta es en este momento una característica [experimental](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) del servicio.

### Antes de empezar

Debe tener acceso administrativo a una instancia de servicio de {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}, y conocer los nombres de los espacios y de las instancias de {{site.data.keyword.Bluemix_notm}} asociados con ella.

### Procedimiento

Para desplegar un modelo basado en reglas en {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}, siga estos pasos:

1. Inicie sesión como un administrador o gestor de proyectos de {{site.data.keyword.knowledgestudioshort}}, y seleccione su espacio de trabajo.
1. Seleccione el separador **Gestión de modelos** > **Versiones** > **Basado en reglas**.
1. Seleccione la versión del modelo que desea desplegar.

    Si solo hay una versión que funciona del modelo, guarde el modelo actual para su despliegue pulsando **Guardar para despliegue**. Esto versiona el modelo, lo que permite desplegar una versión, mientras sigue mejorando la versión actual. Guardar la versión puede tardar unos minutos. La opción para desplegar no aparecerá hasta que se cree la versión.

1. Pulse **Desplegar**, elija desplegarla en {{site.data.keyword.discoveryshort}} y, a continuación, pulse **Siguiente**.
1. Proporcione el espacio y la instancia de {{site.data.keyword.Bluemix_notm}}. Si es necesario, seleccione una región distinta.
1. Pulse **Desplegar**.
1. El proceso de despliegue puede tardar unos minutos. Para comprobar el estado del despliegue, pulse **Estado** en el separador **Versiones** junto a la versión que ha desplegado.

    Si el modelo se está desplegando todavía, el estado indica "publicando". Cuando finalice el despliegue, el estado cambiará a "disponible" si el despliegue fue correcto, o "error" si se producen problemas.

    Una vez disponible, tome nota del ID de modelo (model_id). Proporcionará este ID al servicio de {{site.data.keyword.discoveryshort}} para permitir al servicio que utilice su modelo personalizado.

### Qué hacer a continuación

Para utilizar el modelo desplegado, debe proporcionar el ID de modelo cuando se solicite durante el proceso de configuración de enriquecimiento del servicio de {{site.data.keyword.discoveryshort}}.

## Despliegue de un modelo basado en reglas en IBM Watson Natural Language Understanding
{: #wks_rule_nlu}

Despliegue el modelo basado en reglas para habilitar una aplicación que utiliza el servicio de {{site.data.keyword.nlushort}} para utilizar el modelo para buscar y extraer entidades relevantes para su dominio.

**Atención**: Esta es en este momento una característica [experimental](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) del servicio.

### Antes de empezar

Debe tener acceso administrativo a una instancia de servicio de {{site.data.keyword.nlushort}}, y conocer los nombres de los espacios y de las instancias de {{site.data.keyword.Bluemix_notm}} asociados con ella.

### Procedimiento

Para desplegar un modelo basado en reglas en {{site.data.keyword.nlushort}}, siga estos pasos:

1. Inicie sesión como un administrador o gestor de proyectos de {{site.data.keyword.knowledgestudioshort}}, y seleccione su espacio de trabajo.
1. Seleccione el separador **Gestión de modelos** > **Versiones** > **Basado en reglas**.
1. Seleccione la versión del modelo que desea desplegar.

    Si solo hay una versión que funciona del modelo, guarde el modelo actual para su despliegue pulsando **Guardar para despliegue**. Esto versiona el modelo, lo que permite desplegar una versión, mientras sigue mejorando la versión actual. Guardar la versión puede tardar unos minutos. La opción para desplegar no aparecerá hasta que se cree la versión.

1. Pulse **Desplegar**, elija desplegarla en {{site.data.keyword.nlushort}} y, a continuación, pulse **Siguiente**.
1. Proporcione el espacio y la instancia de {{site.data.keyword.Bluemix_notm}}. Si es necesario, seleccione una región distinta.
1. Pulse **Desplegar**.
1. El proceso de despliegue puede tardar unos minutos. Para comprobar el estado del despliegue, pulse **Estado** en el separador **Versiones** junto a la versión que ha desplegado.

    Si el modelo se está desplegando todavía, el estado indica "publicando". Cuando finalice el despliegue, el estado cambiará a "disponible" si el despliegue fue correcto, o "error" si se producen problemas.

    Una vez disponible, tome nota del ID de modelo (model_id). Proporcionará este ID al servicio de {{site.data.keyword.nlushort}} para permitir al servicio que utilice su modelo personalizado.

### Qué hacer a continuación

Para utilizar el modelo desplegado, debe especificar el ID de modelo del modelo personalizado en el parámetro `entities.model`.

Puede utilizar el modelo con la solicitud {{site.data.keyword.nlushort}} `GET /analyze` para extraer entidades.

Consulte la [documentación de {{site.data.keyword.nlushort}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/watson/developercloud/doc/natural-language-understanding/index.html){: new_window} para obtener más detalles.

## Retirada de modelos
{: #undeploy-view-model}

Si desea retirar un modelo o buscar un ID de modelo, vea la página **Modelos desplegados**. La página **Modelos desplegados** muestra todos los modelos de {{site.data.keyword.knowledgestudioshort}} desplegados en servicios de los espacios a los que tiene acceso.

Para retirar modelos o buscar los ID de modelo:

1. Inicie sesión como un administrador o gestor de proyectos de {{site.data.keyword.knowledgestudioshort}}, y seleccione su espacio de trabajo.
1. Desde el menú **Configuración** en la barra de menús de la parte superior derecha, seleccione **Gestionar modelos desplegados**.
1. En la lista de modelos desplegados, busque el modelo que desee ver o retirar.
1. Para retirar el modelo, desde la última columna de la fila, pulse **Retirar modelo**.
1. Para encontrar el ID de modelo, consulte la columna **ID de modelo**.

## Aprovechar un modelo basado en reglas en IBM Watson Explorer
{: #wks_rule_export}

Exporte el archivo PEAR que se produce cuando el modelo basado en reglas se crea para que pueda utilizarse en {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.

### Procedimiento

Para aprovechar un modelo basado en reglas en {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, siga estos pasos.

1. Inicie sesión como un administrador o gestor de proyectos de {{site.data.keyword.knowledgestudioshort}}, y seleccione su espacio de trabajo.
1. Seleccione el separador **Gestión de modelos** > **Versiones** > **Basado en reglas**.
1. Pulse **Exportar modelo actual**.

    Si tiene una suscripción a un plan gratuito, no habrá disponible ninguna opción de exportación.

    El modelo se guarda como un archivo PEAR, y se le solicitará que descargue el archivo. Un archivo PEAR (Processing Engine ARchive) es el formato de empaquetado estándar de UIMA para los componentes UIMA. El modelo se guarda en formato PEAR para que se pueda distribuir y reutilizar dentro de aplicaciones UIMA.

1. Descargue el archivo a su sistema local.
1. Desde la aplicación de {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, importe el archivo PEAR.
