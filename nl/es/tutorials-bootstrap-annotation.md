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

Esta documentación es para {{site.data.keyword.knowledgestudiofull}} en {{site.data.keyword.cloud}}. Para ver la documentación para la versión anterior de {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.IBM_notm}} Marketplace, [pulse este enlace ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/services/knowledge-studio/tutorials-bootstrap-annotation.html){: new_window}.
{: tip}

# Preanotación de documentos
{: #wks_tutboot_intro}

Esta guía de aprendizaje le ayuda a comprender cómo preanotar documentos, lo que arranca el proceso de anotación de la anotación humana.
{: shortdesc}

## Objetivos de aprendizaje
{: #objectives}

Cuando haya completado esta guía de aprendizaje, sabrá cómo preanotar documentos con un modelo de aprendizaje automático.

Esta guía de aprendizaje debería llevar aproximadamente 5 minutos en finalizar. Si explora otros conceptos relacionados con esta guía de
aprendizaje, el tiempo puede ser mayor.

## Antes de empezar
{: #prereqs}

- Está utilizando un navegador soportado. Para obtener información, consulte [Requisitos del navegador](/docs/services/watson-knowledge-studio/system-requirements.html).
- Ha completado correctamente [Iniciación a {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/tutorials-create-project.html), que cubre la creación de un espacio de trabajo, la creación de un sistema de tipos y la adición de un diccionario.
- Ha completado correctamente [Creación de un modelo de aprendizaje automático](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html).
- Debe tener al menos un ID de usuario en el rol de Admin o Gestor de proyectos. Para obtener información sobre los roles de usuario, consulte [Roles de usuario en {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/roles.html).

## Resultados
{: #results}

Después de completar esta guía de aprendizaje, tendrá un conjunto de documentos anotados parcialmente. A continuación, puede asignar los documentos a anotadores humanos para finalizar el trabajo de anotación.

## Lección 1: Preanotación de documentos nuevos con un modelo de aprendizaje automático
{: #wks_tutboot_ml}

En esta lección, aprenderá a utilizar un modelo de aprendizaje automático para preanotar documentos en {{site.data.keyword.knowledgestudioshort}}.

### Acerca de esta tarea
{: #wks_tutboot_ml_about}

Después de entrenar un modelo de aprendizaje automático, puede utilizarlo para preanotar documentos nuevos que añada al corpus.

> **Atención:** No ejecute un preanotador en documentos anotados por humanos, pero que no se hayan añadido todavía a los datos de campo. Si lo hace, todas las anotaciones actuales se eliminarán de los documentos.

En esta guía de aprendizaje, puede añadir un segundo conjunto de documentos utilizando el archivo `documents-ml.csv`. No vuelva a añadir el archivo `documents-new.csv`, ya que podría resultar en documentos duplicados en los datos de campo. La duplicación provoca los siguientes problemas:

- Si las anotaciones en cada documento no coinciden, se baja la calidad del modelo de aprendizaje automático.
- Si las anotaciones en cada documento coinciden, sobreentrenan el modelo de aprendizaje automático en los archivos duplicados.

Para obtener más información sobre los documentos preanotados, consulte [Anotación de arranque](/docs/services/watson-knowledge-studio/preannotation.html), que cubre métodos adicionales de preanotación.

### Procedimiento
{: #wks_tutboot_ml_procedure}

1. Inicie una sesión en {{site.data.keyword.knowledgestudioshort}} como administrador.
1. Cargue más documentos en el espacio de trabajo. Puede utilizar el archivo <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/documents-ml.csv" download>`documents-ml.csv` <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo" title="Icono de enlace externo" class="style-scope doc-content"></a>.

    Para obtener más información sobre cómo añadir documentos a un espacio de trabajo, consulte [Añadir documentos para su anotación](/docs/services/watson-knowledge-studio/documents-for-annotation.html).

1. Cree un conjunto de anotaciones que utilice el archivo `documents-ml.csv` como el conjunto base y asígnelo a sí mismo, el administrador.

    Después de realizar los pasos siguientes para preanotar los nuevos documentos, puede ver el conjunto de anotaciones para ver cómo ha anotado los documentos el modelo de aprendizaje automático. Normalmente, asigna conjuntos de anotaciones a uno o varios anotadores humanos. Para obtener más información sobre la creación y la asignación de conjuntos de anotaciones, consulte [Añadir documentos para su anotación](/docs/services/watson-knowledge-studio/documents-for-annotation.html).

1. Para preanotar los nuevos documentos, pulse **Modelo de aprendizaje automático** > **Versiones**y, a continuación, pulse **Ejecutar este modelo**.
1. Seleccione el conjunto de documentos que ha añadido al corpus, `documents-ml.csv`, y pulse **Ejecutar**.
1. Una vez que la preanotación haya finalizado, cree una tarea de anotación humana que incluya el conjunto de anotaciones que ha creado.

    Para obtener más información sobre la creación de una tarea de anotación, consulte [Configuración de la anotación](/docs/services/watson-knowledge-studio/annotate-documents.html).

1. Para ver las anotaciones que ha aplicado el modelo de aprendizaje automático a los nuevos documentos, abra la tarea de anotación.

    Debido a que los nuevos documentos se han preanotado con el modelo de aprendizaje automático, la anotación humana requiere menos tiempo. Para obtener más información sobre la adición de anotaciones por anotadores humanos, consulte [Anotación de documentos](/docs/services/watson-knowledge-studio/user-guide.html).

### Resultados
{: #wks_tutboot_ml_results}

Al utilizar el modelo de aprendizaje automático para preanotar nuevos conjuntos de documentos, puede acelerar las tareas de anotación humana para estos documentos.
