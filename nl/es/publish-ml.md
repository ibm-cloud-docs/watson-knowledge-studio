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

Esta documentación es para {{site.data.keyword.knowledgestudiofull}} en {{site.data.keyword.cloud}}. Para ver la documentación para la versión anterior de {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.IBM_notm}} Marketplace, [pulse este enlace ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/services/knowledge-studio/publish-ml.html){: new_window}.
{: tip}

# Uso del modelo de aprendizaje automático
{: #publish-ml}

Aproveche un modelo de aprendizaje automático que haya entrenado con {{site.data.keyword.knowledgestudioshort}} haciendo que esté disponible en otras aplicaciones de {{site.data.keyword.watson}}.
{: shortdesc}

Puede desplegar o exportar un modelo de aprendizaje automático. Un diccionario o un preanotador de {{site.data.keyword.nlushort}} solo se puede utilizar para preanotar documentos dentro de {{site.data.keyword.knowledgestudioshort}}.

Antes de que se pueda desplegar un modelo para que lo utilice un servicio, debe tener una suscripción al servicio. Los servicios de {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} están alojados en {{site.data.keyword.Bluemix_short}}, que es la plataforma en la nube para {{site.data.keyword.IBM_notm}}. Consulte [¿Qué es {{site.data.keyword.Bluemix_notm}}? ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.ng.bluemix.net/docs/overview/whatisbluemix.html){: new_window} para obtener más información sobre la plataforma. Para suscribirse a uno de los servicios de {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}}, cree una cuenta desde el sitio web de [{{site.data.keyword.Bluemix_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.ng.bluemix.net/){: new_window}.

Para algunos de los servicios, debe conocer los detalles sobre la instancia de servicio a la que tiene pensado desplegar, como por ejemplo el nombre de espacio y el nombre de la instancia de servicio de {{site.data.keyword.Bluemix_notm}}. La información del nombre de espacio y de la instancia está disponible desde la página de servicios de {{site.data.keyword.Bluemix_notm}}.

También puede preanotar nuevos documentos con el modelo de aprendizaje automático. Consulte [Preanotación de documentos con un modelo de aprendizaje automático](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotsire) para obtener detalles.

## Despliegue de un modelo de aprendizaje automático en AlchemyLanguage
{: #wks_mabluemix}

Cuando esté satisfecho con el rendimiento del modelo, puede desplegar una versión del mismo en {{site.data.keyword.IBM_notm}} {{site.data.keyword.alchemylanguageshort}}. Esta característica, que requiere que se proporcione una clave de acceso de {{site.data.keyword.alchemyapishort}}, permite que las aplicaciones utilicen el modelo de aprendizaje automático desplegado para anotar documentos en su dominio.

### Antes de empezar

Debe tener el plan Avanzado del servicio de {{site.data.keyword.alchemylanguageshort}} para poder desplegar y utilizar el modelo.
>Nota: El servicio de {{site.data.keyword.alchemylanguageshort}} ha estado en desuso. No puede desplegar este modelo en el servicio a menos que tenga un plan existente.

### Acerca de esta tarea

Al desplegar el modelo de aprendizaje automático, seleccione la versión del mismo que desea desplegar. Para desplegar en este servicio, debe tener una clave de acceso de {{site.data.keyword.IBM_notm}} {{site.data.keyword.alchemylanguageshort}}.

La clave debe pertenecer a una cuenta autorizada a publicar modelos personalizados o el modelo se desplegará correctamente, pero no podrá utilizarlo.

Debe especificar la clave la primera vez que despliegue un modelo en {{site.data.keyword.alchemylanguageshort}}. A continuación, puede reutilizar la clave con varias versiones del modelo que se despliega. Cada clave tiene un número máximo de modelos que se pueden desplegar al mismo tiempo.

### Procedimiento

Para desplegar un modelo de aprendizaje automático en {{site.data.keyword.alchemylanguageshort}}:

1. Inicie sesión como un administrador o gestor de proyectos de {{site.data.keyword.knowledgestudioshort}}, y seleccione su espacio de trabajo.
1. Seleccione el separador **Gestión de modelos** > **Versiones** > **Aprendizaje automático**.
1. Seleccione la versión del modelo que desea desplegar.

    Si solo hay una versión que funciona del modelo, cree una instantánea del modelo actual. Esto versiona el modelo, lo que permite desplegar una versión, mientras sigue mejorando la versión actual. La opción para desplegar no aparecerá hasta que cree al menos una versión.

1. Pulse **Desplegar**, y seleccione desplegarla en el servicio de {{site.data.keyword.alchemylanguageshort}}, y luego pulse **Siguiente**.
1. Especifique la clave que ha obtenido desde {{site.data.keyword.alchemylanguageshort}} o seleccione una versión previamente desplegada del modelo que tiene una clave que desee reutilizar, y pulse **Desplegar**. Si la clave es válida, se mostrará una confirmación que contiene el ID del modelo. Esta confirmación no significa que el modelo esté listo para que lo utilicen sus aplicaciones.
1. El proceso de despliegue puede tardar unos minutos. Para comprobar el estado del despliegue, pulse **Estado** junto a la versión que ha desplegado. Si el modelo se está desplegando todavía, el estado indica "publicando". Cuando finalice el despliegue, el estado cambiará a "disponible" si el despliegue fue correcto, o "error" si se producen problemas.

    La información de estado incluye el ID de modelo, los últimos cuatro dígitos de la clave de {{site.data.keyword.alchemyapishort}} y un registro del proceso de despliegue. El ID de modelo (model_id) es cómo llaman sus aplicaciones al modelo de aprendizaje automático. Utilice la clave de {{site.data.keyword.alchemyapishort}} para realizar el seguimiento del número de despliegues por clave.

### Qué hacer a continuación

Para utilizar el modelo desplegado, debe copiar y pegar el ID de modelo a la llamada de la API de su aplicación. La llamada también debe especificar el servicio del plan Avanzado de {{site.data.keyword.alchemylanguageshort}} que desee utilizar con el modelo y su clave de acceso de {{site.data.keyword.alchemyapishort}} asociada. Están soportados los siguientes puntos finales:

- **&lt;*input-type*&gt;GetRankedNamedEntities**

    Utiliza el modelo personalizado que especifique en el parámetro del modelo para extraer una lista de menciones de todos los tipos de entidades conocidos que encuentre en la entrada que proporcione. Los tipos de entrada soportados incluyen texto, HTML o un URL público. Consulte [{{site.data.keyword.alchemylanguageshort}}&gt;Entities ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/smarterplanet/us/en/ibmwatson/developercloud/alchemy-language/api/v1/#entities){: new_window} para obtener más información sobre la API y la sintaxis a utilizar.

- **&lt;*input-type*&gt;GetTypedRelations**

    Utiliza el modelo personalizado que especifique en el parámetro del modelo para extraer una lista de instancias de relaciones conocidas que encuentre en la entrada que proporcione. Consulte [{{site.data.keyword.alchemylanguageshort}}&gt;TypedRelations ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/smarterplanet/us/en/ibmwatson/developercloud/alchemy-language/api/v1/#typed-relations){: new_window} para obtener más información sobre la API y la sintaxis a utilizar.

#### Ejemplos

- La siguiente llamada de API busca los tipos de entidades conocidos en la serie de texto que se pasa en el cuerpo POST. La solicitud especifica el ID del modelo que se ha creado y una clave de API de Alchemy que tiene derechos para ejecutar modelos personalizados.

    ```bash
    curl -d 'text=Mary had a little lamb.'
    "https://gateway-a.watsonplatform.net/calls/text/TextGetRankedNamedEntities?
    showSourceText=1&
    model=44476a63-c55t-451f-ad3r-8b23c0f4628c&
    apikey=s3wee88r25wwe2p6442w99g8t77phll5323kkf3a&
    outputMode=json"
    ```
    {: pre}

    La respuesta devuelve `Mary` y `lamb` si esas son las menciones reconocidas por el modelo de aprendizaje automático.

- La siguiente llamada de API busca las relaciones conocidas en la serie de texto que se pasa en el cuerpo POST. La solicitud especifica el ID del modelo que se ha creado y una clave de API de Alchemy que tiene derechos para ejecutar modelos personalizados.

    ```bash
    curl -d 'text=Mary had a little lamb.'
    "https://gateway-a.watsonplatform.net/calls/text/TextGetTypedRelations?
    showSourceText=1&
    model=44476a63-c55t-451f-ad3r-8b23c0f4628c&
    apikey=s3wee88r25wwe2p6442w99g8t77phll5323kkf3a&
    outputMode=json"
    ```
    {: pre}

    La respuesta devuelve `ownedBy` si dicha relación está reconocida por el modelo de aprendizaje automático.

> **Nota:** Los retornos de carro están incluidos para dar un mejor formato a los ejemplos para la pantalla. No incluya los retornos de carro en la sintaxis de API.

Para obtener más información, consulte la [documentación de {{site.data.keyword.alchemylanguageshort}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/watson/developercloud/doc/alchemylanguage/customizing.shtml){: new_window}.

#### Información relacionada

[Problemas del modelo de {{site.data.keyword.alchemylanguageshort}}](/docs/services/watson-knowledge-studio/troubleshooting.html#wks_ts_deployed_model_deleted)

## Despliegue de un modelo de aprendizaje automático en IBM Watson Discovery
{: #wks_madiscovery}

Cuando esté satisfecho con el rendimiento del modelo, podrá desplegar una versión del mismo en {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}. Esta característica permite que sus aplicaciones utilicen el modelo de aprendizaje automático desplegado para enriquecer la información que se obtiene de los datos para incluir el reconocimiento de conceptos y relaciones relevantes para su dominio.

### Antes de empezar

Debe tener acceso administrativo a una instancia de servicio de {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}, y conocer los nombres de los espacios y de las instancias de {{site.data.keyword.Bluemix_notm}} asociados con ella.

### Acerca de esta tarea

Al desplegar el modelo de aprendizaje automático, seleccione la versión del mismo que desea desplegar.

### Procedimiento

Para desplegar un modelo de aprendizaje automático en {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}, siga estos pasos:

1. Inicie sesión como un administrador o gestor de proyectos de {{site.data.keyword.knowledgestudioshort}}, y seleccione su espacio de trabajo.
1. Seleccione el separador **Gestión de modelos** > **Versiones** > **Aprendizaje automático**.
1. Seleccione la versión del modelo que desea desplegar.

    Si solo hay una versión que funciona del modelo, cree una instantánea del modelo actual. Esto versiona el modelo, lo que permite desplegar una versión, mientras sigue mejorando la versión actual. La opción para desplegar no aparecerá hasta que cree al menos una versión.

1. Pulse **Desplegar**, elija desplegarla en {{site.data.keyword.discoveryshort}} y, a continuación, pulse **Siguiente**.
1. Seleccione el espacio y la instancia de {{site.data.keyword.Bluemix_notm}}. Si es necesario, seleccione una región distinta.
1. Pulse **Desplegar**.
1. El proceso de despliegue puede tardar unos minutos. Para comprobar el estado del despliegue, pulse **Estado** en el separador **Versiones** junto a la versión que ha desplegado.

    Si el modelo se está desplegando todavía, el estado indica "publicando". Cuando finalice el despliegue, el estado cambiará a "disponible" si el despliegue fue correcto, o "error" si se producen problemas.

    Una vez disponible, tome nota del ID de modelo (model_id). Proporcionará este ID al servicio de {{site.data.keyword.discoveryshort}} para permitir al servicio que utilice su modelo personalizado.

### Qué hacer a continuación

Para utilizar el modelo desplegado, debe proporcionar el ID de modelo cuando se solicite durante el proceso de configuración de enriquecimiento del servicio de {{site.data.keyword.discoveryshort}}. Para obtener más detalles, consulte la [documentación de servicio de {{site.data.keyword.discoveryshort}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://www.ibm.com/watson/developercloud/doc/discovery/integrate-wks.shtml){: new_window}.

## Despliegue de un modelo de aprendizaje automático en IBM Watson Natural Language Understanding
{: #wks_manlu}

Cuando esté satisfecho con el rendimiento del modelo, podrá desplegar una versión del mismo en {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.nlushort}}. Esta característica permite a las aplicaciones utilizar el modelo de aprendizaje automático desplegado para analizar características semánticas de entrada de texto, incluidas entidades y relaciones.

### Antes de empezar

Debe tener un servicio de {{site.data.keyword.nlushort}} en el que desplegar. Y debe conocer los nombres de los espacios y de las instancias de {{site.data.keyword.Bluemix_notm}} asociados con el servicio. Si no recuerda los nombres de los espacios o de las instancias, búsquelos iniciando sesión en {{site.data.keyword.Bluemix_notm}}. Si no tiene una cuenta de {{site.data.keyword.Bluemix_notm}}, regístrese.

### Acerca de esta tarea

Al desplegar el modelo de aprendizaje automático, seleccione la versión del mismo que desea desplegar.

### Procedimiento

Para desplegar un modelo de aprendizaje automático en el servicio de {{site.data.keyword.nlushort}}, siga estos pasos:

1. Inicie sesión como un administrador o gestor de proyectos de {{site.data.keyword.knowledgestudioshort}}, y seleccione su espacio de trabajo.
1. Seleccione el separador **Gestión de modelos** > **Versiones** > **Aprendizaje automático**.
1. Seleccione la versión del modelo que desea desplegar.

    Si solo hay una versión que funciona del modelo, cree una instantánea del modelo actual. Esto versiona el modelo, lo que permite desplegar una versión, mientras sigue mejorando la versión actual. La opción para desplegar no aparecerá hasta que cree al menos una versión.

1. Pulse **Desplegar**, elija desplegarla en {{site.data.keyword.nlushort}} y, a continuación, pulse **Siguiente**.
1. Seleccione el espacio y la instancia de {{site.data.keyword.Bluemix_notm}}. Si es necesario, seleccione una región distinta.
1. Pulse **Desplegar**.
1. El proceso de despliegue puede tardar unos minutos. Para comprobar el estado del despliegue, pulse **Estado** en el separador **Versiones** junto a la versión que ha desplegado. Si el modelo se está desplegando todavía, el estado indica "publicando". Cuando finalice el despliegue, el estado cambiará a "disponible" si el despliegue fue correcto, o "error" si se producen problemas.

    Una vez disponible, tome nota del ID de modelo (model_id). Proporcionará este ID al servicio de {{site.data.keyword.nlushort}} para permitir al servicio que utilice su modelo personalizado.

### Qué hacer a continuación

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

## Aprovechar un modelo de aprendizaje automático en IBM Watson Explorer
{: #wks_maexport}

Exporte el modelo de aprendizaje automático entrenado para que pueda utilizarse en {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.

### Antes de empezar

Si elige identificar los tipos de relaciones y anotarlos, debe definir al menos dos tipos de relaciones, y anotar instancias de las relaciones de los datos de campo antes de exportar el modelo. Definir y anotar solo un tipo de relación puede provocar problemas subsiguientes en {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, release 11.0.1.0.

### Acerca de esta tarea

Ahora que el modelo de aprendizaje automático está entrenado para reconocer entidades y relaciones para un dominio específico, puede aprovecharlo en {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.

Pulse [este enlace ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.youtube.com/watch?v=1VoS-xczBow&amp;feature=youtu.be){: new_window} para ver un vídeo de menos de 2 minutos que ilustra cómo exportar un modelo y cómo utilizarlo en {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.

### Procedimiento

Para aprovechar un modelo de aprendizaje automático en {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, siga estos pasos.

1. Inicie sesión como un administrador o gestor de proyectos de {{site.data.keyword.knowledgestudioshort}}, y seleccione su espacio de trabajo.
1. Seleccione el separador **Gestión de modelos** > **Versiones** > **Aprendizaje automático**.
1. Pulse **Exportar modelo actual**.

    Si tiene una suscripción a un plan gratuito, no habrá disponible ninguna opción de exportación.

    El modelo se guarda como un archivo ZIP, y se le solicitará que descargue el archivo.

1. Descargue el archivo a su sistema local.
1. Desde la aplicación de {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, importe el modelo.

    A continuación, puede correlacionar el modelo a un modelo de aprendizaje automático en {{site.data.keyword.watson}} Explorer Content Analytics. Después de realizar el paso de correlación, cuando rastree documentos, el modelo buscará instancias de las entidades y de las relaciones que entenderá el modelo. Para aprender a importar y a configurar el modelo en {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, consulte el documento técnico que describe la integración: [http://www.ibm.com/support/docview.wss?uid=swg27048147 ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://www.ibm.com/support/docview.wss?uid=swg27048147){: new_window}.

#### Tareas relacionadas

[Exportación de documentos analizados desde {{site.data.keyword.watson}} Explorer Content Analytics](/docs/services/watson-knowledge-studio/preannotation.html#wks_uimawexca)
