---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-29"

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

Esta documentación es para {{site.data.keyword.knowledgestudiofull}} en {{site.data.keyword.cloud}}. Para ver la documentación para la versión anterior de {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.IBM_notm}} Marketplace, [pulse este enlace ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/docs/services/knowledge-studio/train-ml.html){: new_window}.
{: tip}

# Entrenamiento del modelo de aprendizaje automático
{: #train-ml}

En {{site.data.keyword.knowledgestudiofull}}, la creación del modelo de aprendizaje automático implica el entrenamiento del modelo de aprendizaje automático y la evaluación de cómo ha funcionado el modelo al anotar los datos de prueba y los datos ciegos.
{: shortdesc}

## Creación de un modelo de aprendizaje automático
{: #wks_madocsets}

Al crear un modelo de aprendizaje automático, seleccione los conjuntos de documentos que desee utilizar para entrenar el modelo y especifique el porcentaje de documentos que se utilizarán como datos de entrenamiento, datos de prueba y datos ciegos.

### Acerca de esta tarea
{: #wks_madocsets_about}

Al explorar las métricas de rendimiento, puede identificar maneras de mejorar la exactitud del modelo.

> **Restricción:** Solo se pueden entrenar tres modelos de aprendizaje automático a la vez por instancia de {{site.data.keyword.knowledgestudioshort}}. Si la instancia contiene varios espacios de trabajo y el número de modelos de aprendizaje automático que se están entrenando en otros espacios de trabajo ya lleva 3, su solicitud para entrenar el modelo de aprendizaje automático en el espacio de trabajo se pondrá en cola hasta que haya finalizado el resto de los procesos de entrenamiento.

### Procedimiento
{: #wks_madocsets_procedure}

Para crear un modelo de aprendizaje automático:

1. Inicie sesión como administrador de {{site.data.keyword.knowledgestudioshort}} y seleccione el espacio de trabajo.
1. Seleccione **Modelo de aprendizaje automático** > **Rendimiento**.
1. Verifique que todos los conjuntos de documentos hayan sido aprobados y que todos los conflictos de anotación hayan sido resueltos mediante adjudicación. Solo se pueden utilizar para entrenar el modelo los documentos que se han convertido en datos de campo mediante adjudicación o aprobación.
1. Pulse **Entrenar y evaluar**.
1. Opcional: Para especificar cómo desea asignar documentos desde sus conjuntos de documentos que utilizarán los conjuntos de entrenamiento a nivel de sistema, conjuntos de pruebas o ciegos, pulse **Editar valores**.

    Consulte [Gestión de conjuntos de documentos](/docs/services/watson-knowledge-studio/improve-ml.html#wks_mamanagedata) para ayudar a determinar qué proporciones se aplicarán.

1. Opcional: Asocie los diccionarios que desee que utilice el modelo de aprendizaje automático durante el entrenamiento con el tipo de entidad de las entradas del diccionario.

    Si ha creado un preanotador de diccionarios, ya ha realizado este paso. Pulse **Reutilizar la correlación definida para el preanotador de diccionarios** para reutilizarla o definir una nueva correlación.

    El modelo utiliza la información de tipos de términos del diccionario como una característica entre muchas características de análisis lingüístico que considera durante el entrenamiento.

1. Pulse **Entrenar** para entrenar el modelo, o pulse **Entrenar y evaluar** para entrenar el modelo, evaluar anotaciones añadidas por el modelo de aprendizaje automático, y analizar las estadísticas de rendimiento.

    > **Importante:** Entrenar un modelo de aprendizaje automático puede llevar varios minutos o varias horas, dependiendo del número de anotaciones humanas que existan y del número total de palabras en todos los documentos.

1. Seleccione los conjuntos de documentos que desee utilizar para entrenar el modelo.

    > **Nota:** Los conjuntos de documentos deben contener al menos 10 documentos anotados.

1. Tras crear el modelo, seleccione una de las acciones siguientes:

    <table summary="Cada fila de esta tabla describe una opción para una elección.">
      <caption>Tabla 1. Opciones de documento</caption>
      <tr>
        <th style="vertical-align:bottom; text-align"left" id="d33883e137-option">Option</th>
        <th style="vertical-align:bottom; text-align"left" id="d33883e137-desc">Descripción</th>
      </tr>
      <tr>
        <td style="vertical-align:top; text-align"left" headers="d33883e137-option" id="d33883e139">
          <p><strong>Log</strong></p>
        </td>
        <td style="vertical-align:top; text-align"left" headers="d33883e137-desc d33883e139">
          <p>Visualice el archivo de registro para ver si se ha producido algún problema.</p>
        </td>
      </tr>
      <tr>
        <td style="vertical-align:top; text-align"left" headers="d33883e137-option" id="d33883e144">
          <p><strong>Details</strong></p>
        </td>
        <td style="vertical-align:top; text-align"left" headers="d33883e137-desc d33883e144">
          <p>Visualice las estadísticas de rendimiento de las anotaciones, cambie los conjuntos de documentos que desee utilizar para entrenar y probar el modelo, y cree versiones de instantáneas de los artefactos del modelo.</p>
        </td>
      </tr>
      <tr>
        <td style="vertical-align:top; text-align"left" headers="d33883e137-option" id="d33883e149">
          <p><strong>Export</strong></p>
        </td>
        <td style="vertical-align:top; text-align"left" headers="d33883e137-desc d33883e149">
          <p>Si tiene un plan estándar o un plan premium, puede exportar un archivo <code>ZIP</code> al sistema local que contenga los componentes necesarios para que el modelo se ejecute en un entorno de ejecución de aprendizaje automático, como {{site.data.keyword.watson}} Explorer.</p>
        </td>
      </tr>
    </table>

## Evaluación de anotaciones añadidas por el modelo
{: #wks_matest}

Puede comparar la vista de datos de campo para anotaciones añadidas por anotadores humanos a las anotaciones añadidas por el modelo.

### Procedimiento
{: #wks_matest_procedure}

Para evaluar las anotaciones añadidas por el modelo:

1. Seleccione **Modelo de aprendizaje automático** > **Rendimiento** > **Entrenar y evaluar**. Se mostrará la página Conjuntos de entrenamiento/prueba/ciegos.
1. Pulse **Ver datos de campo** para el conjunto de entrenamiento o el conjunto de pruebas para ver las anotaciones añadidas mediante preanotación y mediante anotadores humanos. Se abrirá el editor de datos de campo. Pulse para abrir documentos individuales y vea cómo se han anotado las menciones, las relaciones y las menciones correferenciadas.
1. En la página **Rendimiento**, pulse **Ver resultados de descodificación** para ver las anotaciones que el modelo de aprendizaje automático ha añadido a los documentos del conjunto de pruebas. Este botón solo está disponible después de evaluar el modelo. Al ver los resultados, puede ver cómo ha etiquetado el modelo de aprendizaje automático las menciones, las relaciones y las menciones correferenciadas en los datos de prueba.
1. Si desea cambiar cómo se dividen los documentos entre conjuntos de datos de entrenamiento, prueba y ciegos, pulse **Rendimiento** > **Entrenar y evaluar** > **Editar valores**. Por ejemplo, si los resultados iniciales parecen aceptables, es posible que desee aumentar el número de documentos en el conjunto de pruebas para probar más los resultados del modelo de aprendizaje automático. Puede cambiar la proporción para cómo se dividen automáticamente los documentos para fines distintos, o puede seleccionar conjuntos de documentos específicos para utilizar como datos de entrenamiento, datos de prueba y datos ciegos.
1. Si ha realizado cambios, pulse **Entrenar y evaluar** para volver a entrenar el modelo y reevaluar las anotaciones.

## Supresión de un modelo de aprendizaje automático
{: #wks_madelete}

No puede suprimir un modelo de aprendizaje automático.

Puede suprimir el espacio de trabajo utilizado para desarrollar el modelo, pero no puede suprimir el propio modelo. La supresión de un modelo no es el mejor enfoque. En su lugar, actualice o sustituya los artefactos utilizados para entrenar el modelo. Incluso aunque el modelo no esté produciendo los resultados esperados, puede seguir refinándolo. Cada vez que cree una versión nueva, el modelo se creará de nuevo. Puede editar artefactos como los diccionarios y el sistema de tipos, y elegir utilizar conjuntos de anotaciones distintos al entrenar la versión siguiente.
