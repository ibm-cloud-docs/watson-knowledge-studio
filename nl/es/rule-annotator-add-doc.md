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

Esta documentación es para {{site.data.keyword.knowledgestudiofull}} en {{site.data.keyword.cloud}}. Para ver la documentación para la versión anterior de {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.IBM_notm}} Marketplace, [pulse este enlace ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/docs/services/knowledge-studio/rule-annotator-add-doc.html){: new_window}.
{: tip}

# Añadir documentos para definir reglas
{: #wks_rule_anno_add}

Añada documentos con patrones lingüísticos que ilustran los tipos de reglas que desea definir.
{: shortdesc}

Los documentos que añada para la definición de reglas se guardan por separado de documentos que añada para su anotación. Su único propósito es utilizarse para la minería de ejemplos de patrones. No se utilizan para entrenar ni nunca se descargan.

## Formas en que se pueden añadir documentos al editor de reglas

- **Crear un documento de texto en formato UTF-8**

    Puede añadir texto que ilustra un patrón directamente en el editor de reglas. El nombre que especifique para el documento no puede tener más de 256 caracteres.

- **Cargar un archivo CSV**

    Cargue un archivo en formato CSV que contenga el texto del documento.

- **Copiar un documento que fue importado para su anotación**

    Si un documento que forma parte de un conjunto importado para fines de anotación contiene ejemplos de patrones que desea capturar como reglas, puede copiar el documento al editor de reglas. Los cambios que realice en el documento no afectan a la versión original del documento que se está utilizando para su anotación. Consulte [Adición de documentos a un espacio de trabajo](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projadd) para obtener información sobre la carga de documentos.

Para documentos que copie o cargue, seleccione aquellos que contengan patrones distintos que ayuden a identificar tipos de entidades en documentos.
