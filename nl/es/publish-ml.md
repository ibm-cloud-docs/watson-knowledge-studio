---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-13"

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

Esta documentación es para {{site.data.keyword.knowledgestudiofull}} en {{site.data.keyword.cloud}}. Para ver la documentación para la versión anterior de {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.IBM_notm}} Marketplace, [pulse este enlace ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/services/knowledge-studio/publish-ml.html){: new_window}.
{: tip}

# Uso del modelo de aprendizaje automático
{: #publish-ml}

Aproveche un modelo de aprendizaje automático que haya entrenado con {{site.data.keyword.knowledgestudioshort}} haciendo que esté disponible en otras aplicaciones de {{site.data.keyword.watson}}.
{: shortdesc}

Puede desplegar o exportar un modelo de aprendizaje automático. Un diccionario o un preanotador de {{site.data.keyword.nlushort}} solo se puede utilizar para preanotar documentos dentro de {{site.data.keyword.knowledgestudioshort}}.

Antes de que se pueda desplegar un modelo para que lo utilice un servicio, debe tener una suscripción al servicio. Los servicios de {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} están alojados en {{site.data.keyword.Bluemix_short}}, que es la plataforma en la nube para {{site.data.keyword.IBM_notm}}. Consulte [¿Qué es {{site.data.keyword.Bluemix_notm}}? ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.ng.bluemix.net/docs/overview/whatisbluemix.html){: new_window} para obtener más información sobre la plataforma. Para suscribirse a uno de los servicios de {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}}, cree una cuenta desde el sitio web de [{{site.data.keyword.Bluemix_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.ng.bluemix.net/){: new_window}.

Para algunos de los servicios, debe conocer los detalles sobre la instancia de servicio a la que tiene pensado desplegar, como por ejemplo el nombre de espacio y el nombre de la instancia de servicio de {{site.data.keyword.Bluemix_notm}}. La información del nombre de espacio y de la instancia está disponible desde la página de servicios de {{site.data.keyword.Bluemix_notm}}.

También puede preanotar nuevos documentos con el modelo de aprendizaje automático. Consulte [Preanotación de documentos con el modelo de aprendizaje automático](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotsire) para obtener detalles.

## Despliegue de un modelo de aprendizaje automático en IBM Watson Discovery
{: #wks_madiscovery}

Cuando esté satisfecho con el rendimiento del modelo, podrá desplegar una versión del mismo en {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}. Esta característica permite que sus aplicaciones utilicen el modelo de aprendizaje automático desplegado para enriquecer la información que se obtiene de los datos para incluir el reconocimiento de conceptos y relaciones relevantes para su dominio.

### Antes de empezar
{: #wks_madiscovery_prereqs}

Debe tener acceso administrativo a una instancia de servicio de {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}, y conocer los nombres de los espacios y de las instancias de {{site.data.keyword.Bluemix_notm}} asociados con ella.

### Acerca de esta tarea
{: #wks_madiscovery_about}

Al desplegar el modelo de aprendizaje automático, seleccione la versión del mismo que desea desplegar.

### Procedimiento
{: #wks_madiscovery_procedure}

Para desplegar un modelo de aprendizaje automático en {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}, siga estos pasos:

1. Inicie sesión como un administrador o gestor de proyectos de {{site.data.keyword.knowledgestudioshort}}, y seleccione su espacio de trabajo.
1. Seleccione **Modelo de aprendizaje automático** > **Versiones**.
1. Seleccione la versión del modelo que desea desplegar.

    Si solo hay una versión que funciona del modelo, cree una instantánea del modelo actual. Esto versiona el modelo, lo que permite desplegar una versión, mientras sigue mejorando la versión actual. La opción para desplegar no aparecerá hasta que cree al menos una versión.

    **Nota**: Cada versión se puede desplegar en una sola instancia de servicio. Si desea desplegar el mismo modelo en más de una instancia, cree una versión para cada instancia.

1. Pulse **Desplegar**, elija desplegarla en {{site.data.keyword.discoveryshort}} y, a continuación, pulse **Siguiente**.
1. Seleccione el espacio y la instancia de {{site.data.keyword.Bluemix_notm}}. Si es necesario, seleccione una región distinta.
1. Pulse **Desplegar**.
1. El proceso de despliegue puede tardar unos minutos. Para comprobar el estado del despliegue, pulse **Estado** en el separador **Versiones** junto a la versión que ha desplegado.

    Si el modelo se está desplegando todavía, el estado indica "publicando". Cuando finalice el despliegue, el estado cambiará a "disponible" si el despliegue fue correcto, o "error" si se producen problemas.

    Una vez disponible, tome nota del ID de modelo (model_id). Proporcionará este ID al servicio de {{site.data.keyword.discoveryshort}} para permitir al servicio que utilice su modelo personalizado.

### Qué hacer a continuación
{: #wks_madiscovery_next}

Para utilizar el modelo desplegado, debe proporcionar el ID de modelo cuando se solicite durante el proceso de configuración de enriquecimiento del servicio de {{site.data.keyword.discoveryshort}}. Para obtener más detalles, consulte la [documentación de servicio de {{site.data.keyword.discoveryshort}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/services/discovery/integrate-wks.html){: new_window}.

## Despliegue de un modelo de aprendizaje automático en IBM Watson Natural Language Understanding
{: #wks_manlu}

Cuando esté satisfecho con el rendimiento del modelo, podrá desplegar una versión del mismo en {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.nlushort}}. Esta característica permite a las aplicaciones utilizar el modelo de aprendizaje automático desplegado para analizar características semánticas de entrada de texto, incluidas entidades y relaciones.

### Antes de empezar
{: #wks_manlu_prereqs}

Debe tener un servicio de {{site.data.keyword.nlushort}} en el que desplegar. Y debe conocer los nombres de los espacios y de las instancias de {{site.data.keyword.Bluemix_notm}} asociados con el servicio. Si no recuerda los nombres de los espacios o de las instancias, búsquelos iniciando sesión en {{site.data.keyword.Bluemix_notm}}. Si no tiene una cuenta de {{site.data.keyword.Bluemix_notm}}, regístrese.

### Acerca de esta tarea
{: #wks_manlu_about}

Al desplegar el modelo de aprendizaje automático, seleccione la versión del mismo que desea desplegar.

### Procedimiento
{: #wks_manlu_procedure}

Para desplegar un modelo de aprendizaje automático en el servicio de {{site.data.keyword.nlushort}}, siga estos pasos:

1. Inicie sesión como un administrador o gestor de proyectos de {{site.data.keyword.knowledgestudioshort}}, y seleccione su espacio de trabajo.
1. Seleccione **Modelo de aprendizaje automático** > **Versiones**.
1. Seleccione la versión del modelo que desea desplegar.

    Si solo hay una versión que funciona del modelo, cree una instantánea del modelo actual. Esto versiona el modelo, lo que permite desplegar una versión, mientras sigue mejorando la versión actual. La opción para desplegar no aparecerá hasta que cree al menos una versión.

    **Nota**: Cada versión se puede desplegar en una sola instancia de servicio. Si desea desplegar el mismo modelo en más de una instancia, cree una versión para cada instancia.

1. Pulse **Desplegar**, elija desplegarla en {{site.data.keyword.nlushort}} y, a continuación, pulse **Siguiente**.
1. Seleccione el espacio y la instancia de {{site.data.keyword.Bluemix_notm}}. Si es necesario, seleccione una región distinta.
1. Pulse **Desplegar**.
1. El proceso de despliegue puede tardar unos minutos. Para comprobar el estado del despliegue, pulse **Estado** en el separador **Versiones** junto a la versión que ha desplegado. Si el modelo se está desplegando todavía, el estado indica "publicando". Cuando finalice el despliegue, el estado cambiará a "disponible" si el despliegue fue correcto, o "error" si se producen problemas.

    Una vez disponible, tome nota del ID de modelo (model_id). Proporcionará este ID al servicio de {{site.data.keyword.nlushort}} para permitir al servicio que utilice su modelo personalizado.

### Qué hacer a continuación
{: #wks_manlu_next}

Para utilizar el modelo desplegado, debe especificar el ID de modelo del modelo personalizado en el parámetro `entities.model`.

Puede utilizar el modelo con la solicitud {{site.data.keyword.nlushort}} `GET /analyze` para extraer las características siguientes:

- **entities**

    El siguiente mandato busca las entidades que están presentes en la frase que se pasa utilizando el parámetro de texto:

    ```bash
    curl -G -u "3330af09-4b22-4f2d-a54c-1cb099df1fa8":"338rTJSvPVqeG"
    -d "version=2016-05-17"
    -d "text=Vehicle%201%2C%20a%201995%20Honda%20Civic%20was%20traveling%20north
    %20on%20a%20two%20lane%20undivided%20roadway%2C%20negotiating%20a%20curve%20to
    %20the%20left%20on%20an%20upgrade."
    -d "features=entities"
    -d "entities.model=10:7abc4c2f-5846-3334-b8f7-af5a6fad3398"
    "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze" -k
    ```
    {: pre}

    El servicio devuelve un objeto JSON de instancias que busca de tipos de entidades definidos en el modelo personalizado:

    ```javascript
    {
      "language": "en",
      "entities": [
        {
          "type": "MANUFACTURER",
          "text": "Honda",
          "count": 1
        },
        {
          "type": "MODEL",
          "text": "Civic",
          "count": 1
        },
        {
          "type": "VEHICLE",
          "text": "Vehicle 1",
          "count": 1
        },
        {
          "type": "STRUCTURE",
          "text": "two lane undivided roadway",
          "count": 1
        },
        {
          "type": "STRUCTURE",
          "text": "curve",
          "count": 1
        },
        {
          "type": "MODEL_YEAR",
          "text": "1995",
          "count": 1
        },
        {
          "type": "CONDITION",
          "text": "negotiating",
          "count": 1
        }
      ],
      "language": "en"
    }
    ```
    {: codeblock}

- **relations**

    El siguiente mandato busca las relaciones que están presentes en la frase que se pasa utilizando el parámetro de texto:

    ```bash
    curl -G -u "3330af09-4b22-4f2d-a54c-1cb099df1fa8":"338rTJSvPVqeG"
    -d "version=2016-05-17"
    -d "text=Vehicle%201%2C%20a%201995%20Honda%20Civic%20was%20traveling%20north
    %20on%20a%20two%20lane%20undivided%20roadway%2C%20negotiating%20a%20curve%20to
    %20the%20left%20on%20an%20upgrade."
    -d "features=relations"
    -d "entities.model=10:7abc4c2f-5846-3334-b8f7-af5a6fad3398"
    "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze" -k
    ```
    {: pre}

    El servicio devuelve un objeto JSON de instancias que busca de tipos de relaciones definidos en el modelo personalizado:

    ```javascript
    {
      "relations": [
        {
          "type": "timeOf",
          "sentence": "Vehicle 1, a 1995 Honda Civic was traveling north
           on a two lane undivided roadway, negotiating a curve to
           the left on an upgrade.",
          "score": 0.954254,
          "arguments": [
            {
              "text": "1995",
              "entities": [
                {
                  "type": "Date",
                  "text": "1995"
                }
              ]
            },
            {
              "text": "Honda Civic",
              "entities": [
                {
                  "type": "SportingEvent",
                  "text": "Honda Civic"
                }
              ]
            }
          ]
        },
        {
          "type": "locatedAt",
          "sentence": "Vehicle 1, a 1995 Honda Civic was traveling north
           on a two lane undivided roadway, negotiating a curve to
           the left on an upgrade.",
          "score": 0.40592,
          "arguments": [
            {
              "text": "negotiating",
              "entities": [
                {
                  "type": "EventMeeting",
                  "text": "negotiating"
                }
              ]
            },
            {
              "text": "roadway",
              "entities": [
                {
                  "type": "Facility",
                  "text": "roadway"
                }
              ]
            }
          ]
        }
      ],
      "language": "en"
    }
    ```
    {: codeblock}

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

## Aprovechar un modelo de aprendizaje automático en IBM Watson Explorer
{: #wks_maexport}

Exporte el modelo de aprendizaje automático entrenado para que pueda utilizarse en {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.

### Antes de empezar
{: #wks_maexport_prereqs}

Si elige identificar los tipos de relaciones y anotarlos, debe definir al menos dos tipos de relaciones, y anotar instancias de las relaciones de los datos de campo antes de exportar el modelo. Definir y anotar solo un tipo de relación puede provocar problemas subsiguientes en {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, release 11.0.1.0.

### Acerca de esta tarea
{: #wks_maexport_about}

Ahora que el modelo de aprendizaje automático está entrenado para reconocer entidades y relaciones para un dominio específico, puede aprovecharlo en {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.

Pulse [este enlace ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.youtube.com/watch?v=1VoS-xczBow&amp;feature=youtu.be){: new_window} para ver un vídeo de menos de 2 minutos que ilustra cómo exportar un modelo y cómo utilizarlo en {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.

### Procedimiento
{: #wks_maexport_procedure}

Para aprovechar un modelo de aprendizaje automático en {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, siga estos pasos.

1. Inicie sesión como un administrador o gestor de proyectos de {{site.data.keyword.knowledgestudioshort}}, y seleccione su espacio de trabajo.
1. Seleccione **Modelo de aprendizaje automático** > **Versiones**.
1. Pulse **Exportar modelo actual**.

    Si tiene una suscripción a un plan Lite, no habrá disponible ninguna opción de exportación.

    El modelo se guarda como un archivo ZIP, y se le solicitará que descargue el archivo.

1. Descargue el archivo a su sistema local.
1. Desde la aplicación de {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, importe el modelo.

    A continuación, puede correlacionar el modelo a un modelo de aprendizaje automático en {{site.data.keyword.watson}} Explorer Content Analytics. Después de realizar el paso de correlación, cuando rastree documentos, el modelo buscará instancias de las entidades y de las relaciones que entenderá el modelo. Para aprender a importar y a configurar el modelo en {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, consulte el documento técnico que describe la integración: [http://www.ibm.com/support/docview.wss?uid=swg27048147 ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://www.ibm.com/support/docview.wss?uid=swg27048147){: new_window}.

#### Tareas relacionadas
{: #wks_maexport_related}

[Exportación de documentos analizados desde {{site.data.keyword.watson}} Explorer Content Analytics](/docs/services/watson-knowledge-studio/preannotation.html#wks_uimawexca)
