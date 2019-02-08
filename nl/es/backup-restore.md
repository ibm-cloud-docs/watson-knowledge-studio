---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-20"

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

Esta documentación es para {{site.data.keyword.knowledgestudiofull}} en {{site.data.keyword.cloud}}. Para ver la documentación para la versión anterior de {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.IBM_notm}} Marketplace, [pulse este enlace ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/docs/services/knowledge-studio/backup-restore.html){: new_window}.
{: tip}

# Copia de seguridad y restauración de datos
{: #backup-restore}

Si necesita realizar una copia de seguridad y restaurar un espacio de trabajo para {{site.data.keyword.knowledgestudioshort}}, realice estas tareas. Además, si necesita realizar una migración de datos manual de una instancia de {{site.data.keyword.knowledgestudioshort}} a otra, como por ejemplo cuando se migra de una instancia de {{site.data.keyword.IBM_notm}} Marketplace a una instancia de {{site.data.keyword.cloud_notm}}, realice estas tareas.
{: shortdesc}

_Migración manual de datos_ es el proceso de copia de seguridad de sus datos de una instancia y su restauración en otra instancia.

**Nota**: {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.cloud_notm}} utiliza el término _espacio de trabajo_, mientras que {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.IBM_notm}} Marketplace utiliza el término _proyecto_. La funcionalidad es la misma. Solo la terminología es distinta.

Para realizar una copia de seguridad y restaurar los datos, realice los pasos siguientes:

1. [Entienda de qué datos se puede realizar copia de seguridad](#data)
1. [Prepárese para la copia de seguridad](#prepare)
1. [Descargue artefactos de la instancia actual](#export)
1. [Vuelva a crear espacios de trabajo en la nueva instancia](#recreateproj)
1. [Restaure los datos del espacio de trabajo](#restoredata)
1. [Restaure los modelos](#restoremodels)
1. [Restaure cualquier tarea de anotación incompleta](#restoretasks)

## Datos de los que se puede realizar copia de seguridad
{: #data}

Se puede realizar copia de seguridad y se pueden migrar manualmente los siguientes artefactos:

- Diccionarios editables
- Sistema de tipos
- Conjuntos de documentos de datos de campo aprobados

No se puede realizar copia de seguridad ni se pueden migrar manualmente los siguientes tipos de artefactos:

- Documentos de anotación humada en curso
- Tareas de anotación
- Modelos e instantáneas
- Diccionarios de solo lectura

## Preparación para copias de seguridad
{: #prepare}

Para prepararse para la copia de seguridad y la restauración de los datos, siga estos pasos:

1. Complete cualquier trabajo que esté en curso en el espacio de trabajo.

    - > **Importante:** Finalice las tareas de anotación en curso. Solo se puede realizar copia de seguridad de los documentos que se han anotado, adjudicado, y aprobado y promocionado a datos de campo. Si no termina el trabajo de anotación, perderá cualquier esfuerzo de anotación que esté en curso, pero que no esté completamente acabado.

    - Si ha creado tareas de anotación para realizar el seguimiento del trabajo que desea realizar, pero ninguno de los trabajos de anotación ha comenzado y no tendrán lugar hasta después de restaurar el espacio de trabajo, realice una lista de las tareas de anotación pendientes. Asegúrese de anotar los conjuntos de documentos que ha importado, pero que no había añadido aún a los datos de campo. Además, tome nota de quién ha asignado para anotar cada conjunto de documentos. Necesitará volver a cargar estos conjuntos de documentos y volver a crear las tareas de anotación tras restaurar el espacio de trabajo.

1. Comprenda el uso del señalador.

    Para modelos de aprendizaje automático, los espacios de trabajo utilizan el señalador basado en aprendizaje automático de forma predeterminada. Si está utilizando un señalador basado en diccionario y tiene una necesidad específica para continuar haciéndolo, puede configurar el espacio de trabajo para utilizar el señalador basado en diccionario al restaurarlo. Para obtener más información, consulte [Señaladores](/docs/services/watson-knowledge-studio/create-project.html#wks_tokenizer).

1. Gestione los recursos de modelos.

    El modelo, sus versiones y los datos de instantánea no se pueden migrar. Los recursos (excepto los diccionarios de solo lectura) que ha utilizado para entrenar estos artefactos se pueden migrar. Por lo tanto, tras la migración, puede volver a crear el modelo. El modelo que se producirá funcionará igual que los modelos generados anteriormente a la migración porque los recursos que se utilizan para el entrenamiento serán los mismos.

    **ATENCIÓN**: Si tiene un modelo que ya está desplegado y piensa suprimir el espacio de trabajo después de realizar su copia de seguridad, retire el modelo del despliegue. Puede volver a crear y a desplegar el modelo después de restaurar el espacio de trabajo desde la copia de seguridad. Para obtener información sobre la retirada de modelos, consulte [Retirada de modelos de aprendizaje automático](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) y [Retirada de modelos basados en reglas](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model).

    **Tenga en cuenta que si no retira el modelo del despliegue, el resultado será un modelo desplegado _huérfano_. Los modelos desplegados huérfanos seguirán generando cargos en sus facturas mensuales.**

1. Gestione la información del diccionario de solo lectura.

    Los diccionarios de solo lectura no se pueden migrar. Descubra desde dónde se ha importado el diccionario de solo lectura, para que pueda volver a cargarlo en su espacio de trabajo tras la migración.

1. Haga una lista de los roles de usuario actuales.

    **NOTA**: Este paso es opcional. Normalmente se realiza cuando se migra un espacio de trabajo entre instancias y el espacio de trabajo nuevo debe ser idéntico al espacio de trabajo original. Si desea migrar solo los datos del espacio de trabajo en un espacio de trabajo nuevo, puede omitir este paso.

    Si está migrando espacios de trabajo entre instancias distintas, considere realizar una lista de usuarios y sus roles para la instancia de la que está haciendo copia de seguridad. Alguien con el rol Admin puede imprimir la lista desde la página Gestión de cuentas de usuario. Una vez vueltos a crear los espacios de trabajo en la instancia nueva, alguien con el rol Admin debe añadir los usuarios y asignar sus roles.

    Para obtener más información sobre los roles, consulte [Roles de usuario en {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/roles.html).

1. Tome nota de la información del espacio de trabajo.

    Mientras siga teniendo acceso a la instancia actual, para cada espacio de trabajo que desee migrar, tome nota de la información siguiente:
    - Nombre del espacio de trabajo
    - Descripción del espacio de trabajo
    - Propietario del espacio de trabajo
    - Idioma
    - Si tiene cualquier tarea de anotación incompleta, porque no se le puede realizar copia de seguridad o migrar, anote los anotadores humanos que se asignan a tareas incompletas en el espacio de trabajo. Anote también los detalles de la tarea de anotación, como por ejemplo el nombre de tarea, la fecha de vencimiento y qué conjuntos de documentos se asignan a qué usuarios.

## Descarga de artefactos
{: #export}

Para cada espacio de trabajo que desee migrar, descargue los artefactos siguientes. Almacénelos en una ubicación segura desde la que pueda cargarlos en la instancia nueva más tarde.

- Sistema de tipos
- Diccionarios

  **Nota**:
    - Solo se descargarán los diccionarios editables. No puede descargar diccionarios de solo lectura.
    - Para los diccionarios, las correlaciones de tipos de entidad no se migran. Una vez que restaure estos artefactos, deberá correlacionar los diccionarios con tipos de entidad, según sea necesario.

- Documentos

  Consulte [Cargar recursos desde otro espacio de trabajo](/docs/services/watson-knowledge-studio/exportimport.html) para obtener información sobre cómo descargar estos artefactos para que se puedan importar en un espacio de trabajo nuevo.

## Volver a crear espacios de trabajo
{: #recreateproj}

**NOTA**: En este paso, el único valor que debe coincidir con el valor del espacio de trabajo original (descargado) es el idioma. El resto de los valores puede diferir de los valores del espacio de trabajo original.

Vuelva a crear cada espacio de trabajo copiando la información siguiente desde la instancia anterior a la nueva:

- Nombre del espacio de trabajo
- Descripción del espacio de trabajo
- Idioma de los documentos (este valor debe coincidir con el valor del espacio de trabajo original)
- Si ha utilizado previamente un señalador basado en diccionario en el espacio de trabajo, y tiene una necesidad válida de continuar utilizándolo, debe especificar que desea utilizar el señalador basado en diccionario en lugar del señalador predeterminado en el momento de crear el espacio de trabajo. Para obtener más información sobre las opciones, consulte [Señaladores](/docs/services/watson-knowledge-studio/create-project.html#wks_tokenizer).

  Para utilizar un señalador basado en diccionario, expanda la sección Opciones avanzadas de la ventana Crear espacio de trabajo (en {{site.data.keyword.IBM_notm}} Marketplace, la ventana Crear espacio de trabajo) y cambie el valor del señalador.

## Restauración de los datos del espacio de trabajo
{: #restoredata}

Tras volver a crear los espacios de trabajo, cargue los artefactos previamente descargados:

1. Cargue el sistema de tipos desde la copia de seguridad del sistema de tipos previamente creada.
   Para obtener detalles, consulte [Cargar recursos desde otro espacio de trabajo](/docs/services/watson-knowledge-studio/exportimport.html).

  **Nota**: Debe cargar el sistema de tipos antes de poder cargar cualquier otro artefacto que esté moviendo desde el espacio de trabajo del que se ha realizado copia de seguridad.

1. Cargue los diccionarios desde la copia de seguridad del diccionario creada previamente.
   Para obtener detalles, consulte [Cargar recursos desde otro espacio de trabajo](/docs/services/watson-knowledge-studio/exportimport.html).

  Si ha utilizado cualquier diccionario de solo lectura en la versión anterior del espacio de trabajo, vuelva a cargarlos en este espacio de trabajo desde su fuente original.

1. Para los preanotadores de diccionario, asocie los diccionarios con un tipo de entidad. Los diccionarios que no tengan correlaciones para tipos de entidad no aplicarán anotaciones cuando se preanoten los documentos.

1. Cargue los documentos que ha descargado desde la versión anterior del espacio de trabajo en esta versión del espacio de trabajo.
   Para obtener detalles, consulte [Cargar recursos desde otro espacio de trabajo](/docs/services/watson-knowledge-studio/exportimport.html).

## Restauración de modelos
{: #restoremodels}

En este punto, todos los artefactos utilizados para entrenar el modelo en la versión anterior (de la que se ha realizado copia de seguridad) del espacio de trabajo ahora están disponibles en esta nueva instancia.

Para volver a desplegar un modelo de aprendizaje automático que ha desplegado en la instancia anterior, siga estos pasos:

1. [Entrene el modelo de aprendizaje automático](/docs/services/watson-knowledge-studio/train-ml.html).

  **Nota**: No ejecute preanotadores en documentos anotados que haya migrado a este espacio de trabajo porque perderán las anotaciones añadidas por anotadores humanos.

1. Después de crear el modelo, despliéguelo de nuevo. Para obtener detalles, consulte [Utilización del modelo de aprendizaje automático](/docs/services/watson-knowledge-studio/publish-ml.html).

Para volver a desplegar un modelo basado en reglas que ha desplegado en la instancia anterior, siga estos pasos:

1. [Cree el modelo basado en reglas](/docs/services/watson-knowledge-studio/rule-annotator-model-create.html).
1. [Despliegue el modelo basado en reglas](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html).

## Restauración de tareas de anotación incompletas
{: #restoretasks}

Si ha tenido alguna tarea de anotación creada, pero no completada en el espacio de trabajo anterior, siga estos pasos para volver a crear las tareas de anotación incompletas:

1. [Cargue los documentos](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projadd) que no se hayan anotado aún, pero que desee añadir a los datos de campo para seguir mejorando el modelo.
1. Desde los documentos recién importados y no anotados, [cree conjuntos de anotación](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projdocsets).
1. [Vuelva a crear las tareas de anotación](/docs/services/watson-knowledge-studio/annotate-documents.html#wks_hatask). Dé a la tarea el mismo nombre, una fecha de vencimiento apropiada, y asigne conjuntos de anotaciones a los anotadores humanos apropiados.
