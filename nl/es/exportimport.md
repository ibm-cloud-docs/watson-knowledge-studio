---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-18"

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

Esta documentación es para {{site.data.keyword.knowledgestudiofull}} en {{site.data.keyword.cloud}}. Para ver la documentación para la versión anterior de {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.IBM_notm}} Marketplace, [pulse este enlace ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/services/knowledge-studio/exportimport.html){: new_window}.
{: tip}

# Carga de recursos desde otro espacio de trabajo
{: #exportimport}

Para acelerar la creación de un modelo, puede cargar recursos como documentos (con o sin anotaciones de datos de campo), un sistema de tipos y diccionarios que haya descargado desde otro espacio de trabajo.
{: shortdesc}

La capacidad de descargar y cargar por separado distintos recursos le da flexibilidad al designar y crear un modelo. Por ejemplo, podría crear un espacio de trabajo para designar el sistema de tipos y realizar anotación humana, y a continuación crear un espacio de trabajo independiente, quizá en una instancia independiente de {{site.data.keyword.knowledgestudioshort}} con distintos usuarios, para entrenar el modelo de aprendizaje automático. Ser capaz de cargar los recursos, incluidos los datos de campo creados por anotadores humanos, hace posible este caso de ejemplo.

No puede descargar ni cargar un modelo de aprendizaje automático. En su lugar, puede descargar todos los artefactos utilizados para crear el modelo desde un espacio de trabajo y cargarlos en un nuevo espacio de trabajo. Desde el nuevo espacio de trabajo, puede ejecutar el entrenamiento de nuevo para volver a crear el modelo. El nuevo modelo debería producir resultados similares al modelo original porque los dos estaban entrenados con el mismo conjunto de artefactos.

Los archivos descargados son independientes del sistema operativo. Las instancias de {{site.data.keyword.knowledgestudioshort}} donde ha descargado y cargado archivos no tienen que ejecutar la misma versión de Linux.

## Sistemas de tipos
{: #wks_exportimport_expimp_type}

Para descargar un sistema de tipos, abra la página **Activos**> **Tipos de entidades** y pulse **Descargar tipos**. El sistema crea un archivo denominado `types-ID.json` y le solicita que descargue el archivo a su sistema local. Para utilizar este sistema de tipos en un nuevo espacio de trabajo, abra la página **Tipos de entidades** y cargue el archivo `JSON` que ha descargado.

## Diccionarios
{: #wks_exportimport_expimp_dict}

Para descargar todos los diccionarios, seleccione la página **Activos** > **Diccionarios**, pulse el icono **Menú** situado junto al botón **Crear diccionario** y seleccione **Descargar diccionarios**. Para cada diccionario que descargue, el sistema creará un archivo denominado `dictionary name_timestamp.csv`, combina los archivos en un archivo `ZIP` denominado `workspace name_dictionary_timestamp.zip`, y le solicitará que descargue el archivo a su sistema local.

Puede descargar un diccionario individual abriendo el diccionario y pulsando **Descargar**. Los diccionarios de solo vista previa que ha cargado como un archivo CSV de diccionario no se pueden descargar.

Antes de cargar un diccionario descargado a un nuevo espacio de trabajo, debe descargar el sistema de tipos desde el espacio de trabajo antiguo y cargarlo en el espacio de trabajo nuevo. El sistema de tipos y los diccionarios deben originarse desde el mismo espacio de trabajo de {{site.data.keyword.knowledgestudioshort}}, y el sistema de tipos debe existir en el espacio de trabajo nuevo antes de cargar los diccionarios.

Para cargar diccionarios, abra el separador **Diccionarios** y o bien añada un archivo `CSV` que haya descargado o bien cargue el archivo `ZIP`.

## Documentos
{: #wks_exportimport_expimp_doc}

Para descargar documentos que haya añadido al corpus, abra el separador **Activos**> **Documentos** > **Conjuntos de documentos** y pulse **Descargar conjuntos de documentos**. El sistema crea un archivo denominado `corpus-ID.zip` y le solicita que descargue el archivo a su sistema local. El archivo `ZIP` contiene todos los documentos del corpus. Las anotaciones añadidas a los conjuntos de anotaciones están incluidas en el archivo ZIP, pero solo después de que los conjuntos de anotaciones se hayan aprobado y promocionado a datos de campo.

> **Restricción:** Los documentos que fueron preanotados serán ocultados en un formato no legible cuando se descarguen. Incluso las anotaciones en tales documentos que añadió la anotación humana son ilegibles.

Antes de cargar documentos que incluyen datos de campo en un nuevo espacio de trabajo, debe descargar el sistema de tipos desde el espacio de trabajo antiguo y cargarlo en el nuevo espacio de trabajo. El sistema de tipos y los documentos deben originarse desde el mismo espacio de trabajo de {{site.data.keyword.knowledgestudioshort}}, y el sistema de tipos debe existir en el espacio de trabajo nuevo antes de cargar las anotaciones de datos de campo.

Para cargar documentos, abra el separador **Conjuntos de documentos** en el nuevo espacio de trabajo, pulse **Cargar conjuntos de documentos** y seleccione el archivo `ZIP` del corpus que ha descargado. Especifique si desea que los documentos cargados incluyan o excluyan las anotaciones de datos de campo antes de pulsar **Cargar**. Solo se cargarán las anotaciones promocionadas a datos de campo antes de que se descargaran los documentos.

**Conceptos relacionados**:

[Tipos de artefactos](/docs/services/watson-knowledge-studio/artifacts.html)

[Añadir documentos para su anotación](/docs/services/watson-knowledge-studio/documents-for-annotation.html)

[Añadir documentos para definir reglas](/docs/services/watson-knowledge-studio/rule-annotator-add-doc.html)
