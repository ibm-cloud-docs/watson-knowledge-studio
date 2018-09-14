---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-19"

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

Esta documentación es para {{site.data.keyword.knowledgestudiofull}} en {{site.data.keyword.cloud}}. Para ver la documentación para la versión anterior de {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.IBM_notm}} Marketplace, [pulse este enlace ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/services/knowledge-studio/rule-annotator-model-create.html){: new_window}.
{: tip}

# Creación del modelo basado en reglas
{: #wks_rule_train}

Después de definir reglas, puede crear un modelo basado en reglas.
{: shortdesc}

## Procedimiento
{: #wks_rule_train_procedure}

Para crear un modelo basado en reglas, siga estos pasos:

1. Inicie sesión como un administrador o gestor de proyectos de {{site.data.keyword.knowledgestudioshort}}, y seleccione su espacio de trabajo.
1. Seleccione el separador **Modelo basado en reglas** > **Versiones** > **Modelo basado en reglas**.
2. Pulse **Correlacionar tipos de entidad y clases**.
3. Correlacione los tipos de entidades desde su sistema de tipos con una o varias clases que haya utilizado para definir reglas.

  Después de que los tipos de entidades estén correlacionados, puede [desplegar el modelo basado en reglas](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html) o utilizarlo para [preanotar documentos](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotrule) en el proceso de creación de un modelo de aprendizaje automático.

## Supresión de un modelo basado en reglas
{: #wks_rule_delete_model}

No puede suprimir un modelo basado en reglas.

Puede suprimir el espacio de trabajo que se ha utilizado para desarrollar el modelo basado en reglas, pero no puede suprimir el propio modelo. La supresión de un modelo no es el mejor enfoque. En su lugar, vuelva a crear las reglas definidas para el mismo. Editar las reglas directamente cambia el comportamiento del modelo basado en reglas.
