---

copyright:
  years: 2015, 2018
lastupdated: "2018-03-20"

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

# Anotación de arranque
{: #wks_tutboot_intro}

Esta guía de aprendizaje le ayuda a comprender cómo preanotar documentos, lo que simplifica el trabajo de anotación de los anotadores humanos.
{: shortdesc}

## Objetivos de aprendizaje

Cuando haya completado esta guía de aprendizaje, sabrá cómo preanotar documentos con un modelo de aprendizaje automático.

Esta guía de aprendizaje debería llevar aproximadamente 5 minutos en finalizar. Si explora otros conceptos relacionados con esta guía de
aprendizaje, el tiempo puede ser mayor.

## Antes de empezar

- Está utilizando un navegador soportado. Para obtener información, consulte [Requisitos del navegador](/docs/services/watson-knowledge-studio/system-requirements.html).
- Ha completado correctamente [Guía de aprendizaje: Creación de un espacio de trabajo](/docs/services/watson-knowledge-studio/tutorials-create-project.html) y [Guía de aprendizaje: Creación de un modelo de aprendizaje automático](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html).
- Debe tener al menos un ID de usuario en el rol de Admin o ProjectManager. Para obtener información sobre los roles de usuario, consulte [Ensamblaje de un equipo](/docs/services/watson-knowledge-studio/team.html).

## Resultados

Después de completar esta guía de aprendizaje, tendrá un conjunto de documentos anotados parcialmente. A continuación, puede asignar los documentos a anotadores humanos para finalizar el trabajo de anotación.

## Lección 1: Preanotación de documentos nuevos con un modelo de aprendizaje automático
{: #wks_tutboot_ml}

En esta lección, aprenderá a utilizar un modelo de aprendizaje automático para preanotar documentos en {{site.data.keyword.knowledgestudioshort}}.

### Acerca de esta tarea

Después de entrenar un modelo de aprendizaje automático, puede utilizarlo para preanotar documentos nuevos que añada al corpus.

> **Atención:** No ejecute un preanotador en documentos anotados por humanos, pero que no se hayan añadido todavía a los datos de campo. Si lo hace, todas las anotaciones actuales se eliminarán de los documentos.

En esta guía de aprendizaje, puede añadir un segundo conjunto de documentos utilizando el archivo `documents-ml.csv`. No vuelva a añadir el archivo `documents-new.csv`, ya que podría resultar en documentos duplicados en los datos de campo. La duplicación provoca los siguientes problemas:

- Si las anotaciones en cada documento no coinciden, se baja la calidad del modelo de aprendizaje automático.
- Si las anotaciones en cada documento coinciden, sobreentrenan el modelo de aprendizaje automático en los archivos duplicados.

### Procedimiento

1. Inicie una sesión en {{site.data.keyword.knowledgestudioshort}} como administrador.
1. Cargue más documentos en el espacio de trabajo. Puede utilizar el archivo <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/documents-ml.csv" download>`documents-ml.csv`<img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo" title="Icono de enlace externo" class="style-scope doc-content"></a>.

    Para obtener detalles sobre cómo cargar documentos, consulte [Creación de un modelo de aprendizaje automático > Adición de documentos para anotación](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#tut_lessml1).

1. Cree un conjunto de anotaciones con el archivo `documents-ml.csv`.

    Para esta guía de aprendizaje, asigne el conjunto de anotaciones a sí mismo, el administrador. Después de ejecutar el modelo de aprendizaje automático para preanotar los documentos nuevos, puede ver el conjunto de anotaciones para ver cómo los ha preanotado el modelo de aprendizaje automático. Normalmente, asigna el conjunto de anotaciones a uno o varios anotadores humanos. Para obtener más información sobre cómo crear conjuntos de anotaciones, consulte [Creación de un modelo de aprendizaje automático > Creación de conjuntos de anotaciones](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml2).

1. Desde la barra lateral **Gestión de modelos** > **Versiones**, seleccione el separador **Aprendizaje automático** y pulse **Ejecutar este modelo**.
1. Seleccione el conjunto de documentos que ha añadido al corpus, `documents-ml.csv`, y pulse **Ejecutar**.
1. Una vez que la preanotación haya finalizado, puede crear una tarea de anotación humana y anotar los documentos nuevos y preanotados.

    Para obtener detalles sobre cómo crear una tarea y anotar documentos, consulte [Creación de un modelo de aprendizaje automático > Creación de una tarea de anotación](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml4) y [Creación de un modelo de aprendizaje automático > Anotación de documentos](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml5).

    En esta situación, la anotación humana necesita menos tiempo porque ha utilizado el modelo de aprendizaje automático para preanotar los documentos.

### Resultados

Al utilizar el modelo de aprendizaje automático para preanotar nuevos conjuntos de documentos, puede acelerar las tareas de anotación humana para estos documentos.
