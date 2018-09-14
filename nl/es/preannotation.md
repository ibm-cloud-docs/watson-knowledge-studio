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

Esta documentación es para {{site.data.keyword.knowledgestudiofull}} en {{site.data.keyword.cloud}}. Para ver la documentación para la versión anterior de {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.IBM_notm}} Marketplace, [pulse este enlace ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/services/knowledge-studio/preannotation.html){: new_window}.
{: tip}

# Anotación de arranque
{: #preannotation}

Simplifique el trabajo del anotador humano preanotando los documentos en un espacio de trabajo. Un preanotador es un modelo basado en reglas de diccionario de {{site.data.keyword.knowledgestudioshort}}, o un modelo de aprendizaje automático que puede ejecutar para buscar y anotar menciones automáticamente.
{: shortdesc}

La preanotación hace que el trabajo de los anotadores humanos sea más fácil porque cubre las anotaciones sencillas, y hace que el trabajo de anotar los documentos esté en curso.

El método que se utiliza para preanotar documentos no restringe de ninguna forma las maneras en que se puede utilizar el modelo de resultado. Por ejemplo, solo porque utiliza el servicio de {{site.data.keyword.nlushort}} para preanotar documentos no significa que deba desplegar el modelo de aprendizaje automático final que haya creado en el servicio de {{site.data.keyword.nlushort}}. La preanotación solo está pensada para arrancar el proceso de anotación humano.

## Notas importantes
{: #preannotation_notes}

- No ejecute nunca un preanotador en documentos que los anotadores humanos hayan anotado porque las anotaciones añadidas por los anotadores humanos se eliminarán.
- Solo puede ejecutar un preanotador en documentos. Si ejecuta un preanotador, y luego ejecuta un segundo preanotador, el segundo preanotador eliminará las anotaciones añadidas por el primer preanotador. Elija el método de preanotación que se ajuste mejor a su caso de uso, y utilice solo ese preanotador.

## Métodos de preanotación
{: #preannotation_methods}

Están disponibles los siguientes preanotadores:

- **{{site.data.keyword.nlushort}}**

    Un preanotador que puede utilizar para buscar menciones de entidades en los documentos automáticamente. Si los documentos de origen tienen materias de conocimiento general, este preanotador es una buena opción para usted. Si está trabajando con documentos muy especializados que se centran en un campo específico, como por ejemplo la investigación de la ley de patentes, por ejemplo, el preanotador de diccionarios o el modelo basado en reglas podría ser una mejor opción.

- **Diccionario**

    Utiliza un diccionario de términos que proporcione y asocie con un tipo de entidad para buscar menciones de tal tipo de entidad en los documentos. Esta opción es mejor para los campos con terminología exclusiva o especializada porque este preanotador no analiza el contexto en el que se utiliza el término de la forma en que lo hace un preanotador de aprendizaje automático; en su lugar, se basa en el término que sea lo suficientemente distinto como para tener un significado descifrable independientemente del contexto en el que se utilice. Por ejemplo, es más fácil reconocer *amianto* como un tipo de entidad mineral que determinar el tipo de entidad de *squash*, que puede referirse a un vegetal, un deporte, o un verbo que significa aplastar algo.

- **Aprendizaje automático**

    Utiliza un modelo de aprendizaje automático para anotar documentos automáticamente. Esta opción solo está disponible para usted si ha creado un modelo de aprendizaje automático con {{site.data.keyword.knowledgestudioshort}} ya. Si añade un nuevo conjunto de documentos, puede ejecutar el anotador de aprendizaje automático que ha creado previamente para preanotar los documentos nuevos. Si el nuevo conjunto de documentos son similares a los documentos utilizados para entrenar el anotador de aprendizaje automático originalmente, esta es probablemente su mejor opción para la preanotación.

- **Regla**

    Utiliza un modelo basado en reglas para anotar documentos automáticamente. Esta opción solo está disponible si ha creado un modelo basado en reglas con {{site.data.keyword.knowledgestudioshort}} ya. Si los documentos contienen patrones comunes de señales desde las que pueda derivar significado, este modelo puede ser una buena opción. Puede incorporar algunas de las funciones del preanotador de diccionarios si lo habilita, identificando los tipos de clases para los términos del diccionario que también busca en los documentos.

Como alternativa, puede cargar documentos ya anotados, y utilizarlos para empezar el entrenamiento del modelo de aprendizaje automático. No puede ejecutar un preanotador en documentos anotados que cargue o las anotaciones existentes se eliminarán de los documentos y se sustituirán por anotaciones producidas solo por el preanotador.

> **Nota:** *Puede* ejecutar un preanotador en documentos añadidos a los datos de campo como parte del espacio de trabajo actual. Las anotaciones añadidas a los documentos, revisadas, aceptadas y promocionadas a datos de campo dentro del espacio de trabajo actual no se eliminarán.

## Preanotación de documentos con {{site.data.keyword.nlushort}}
{: #wks_preannotnlu}

Puede utilizar el servicio de {{site.data.keyword.nlushort}} para preanotar documentos añadidos al corpus.

### Antes de empezar
{: #wks_preannotnlu_prereqs}

Determine si es probable que el preanotador de {{site.data.keyword.nlushort}} añada un valor para el caso de uso. Revise la lista de [tipos y subtipos de entidades de servicio de {{site.data.keyword.nlushort}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/services/natural-language-understanding/entity-types.html){: new_window} soportados para determinar si hay un solapamiento natural entre ellos y los tipos del sistema de tipos. Si es así, continúe con este procedimiento. Si no lo es, elija un preanotador distinto para utilizar.

### Acerca de esta tarea
{: #wks_preannotnlu_about}

{{site.data.keyword.nlushort}} es un servicio que ofrece análisis de texto mediante procesamiento del lenguaje natural. Cuando utilice el preanotador de {{site.data.keyword.nlushort}}, se llama al servicio de {{site.data.keyword.nlushort}} para buscar y anotar entidades en los documentos.

Debe especificar los tipos de entidades que desea que busque el servicio correlacionando los tipos de entidades de {{site.data.keyword.nlushort}} con los tipos de entidades de {{site.data.keyword.knowledgestudioshort}} correspondientes que haya añadido al sistema de tipos de {{site.data.keyword.knowledgestudioshort}}. Solo se buscarán y anotarán las menciones de los tipos de entidades que se correlacionen.

### Procedimiento
{: #wks_preannotnlu_procedure}

Para utilizar el servicio de {{site.data.keyword.nlushort}} para preanotar documentos, siga estos pasos:

1. Inicie sesión como administrador de {{site.data.keyword.knowledgestudioshort}} y seleccione el espacio de trabajo.
1. Seleccione el separador **Activos** > **Preanotación** > **Comprensión de lenguaje natural**.
1. Pulse **Editar** para correlacionar cada tipo de entidad definido en la página **Tipos de entidades** con los tipos de entidades de {{site.data.keyword.nlushort}} correspondientes.

    - La lista desplegable de los tipos de entidades de {{site.data.keyword.nlushort}} se prerrellena con tipos de entidades reconocidos por el servicio de {{site.data.keyword.nlushort}}.
    - Debe correlacionar al menos un tipo de entidad.
    - No puede correlacionar un tipo de entidad de {{site.data.keyword.nlushort}} con un rol de entidad de {{site.data.keyword.knowledgestudioshort}}, solo con tipos de entidades de {{site.data.keyword.knowledgestudioshort}}.
    - Puede correlacionar más de un tipo de entidad de {{site.data.keyword.nlushort}} con un tipo de entidad de {{site.data.keyword.knowledgestudioshort}} único, o al revés. Por ejemplo, se permiten las siguientes correlaciones:

    <table summary="Correlación de ejemplo de tipos de entidades">
    <caption>Tabla 1. Correlación de ejemplo de tipos de entidades</caption>
      <tr>
        <th style="vertical-align:bottom; text-align"left" id="d20428e292">Watson Knowledge Studio Entity Type</th>
        <th style="vertical-align:bottom; text-align"left" id="d20428e298">Tipo de entidad de {{site.data.keyword.nlushort}}</th>
      </tr>
      <tr>
        <td headers="d20428e292">
          ENGINEER<br/>
          SCIENTIST
        </td>
        <td headers="d20428e298">
          Persona
        </td>
      </tr>
      <tr>
        <td headers="d20428e292">
          LOCATION
        </td>
        <td headers="d20428e298">
          CityTown<br/>
          País
        </td>
      </tr>
    </table>
    {: #wks_preannotnlu__datasimpletable_cm1_y3g_fx}

1. Después de correlacionar todos los tipos de entidades que desea aplicar, pulse **Aplicar este preanotador**.

    El botón **Aplicar este preanotador** no estará disponible hasta que correlacione al menos un tipo de entidad.

1. Marque el recuadro de selección para cada conjunto de documentos que desee preanotar.

    Si está ejecutando este preanotador por primera vez, valide en primer lugar que el preanotador pueda buscar menciones de las entidades correlacionadas como se esperaba. Cree un conjunto de documentos que contenga un documento o documentos representativos de cada origen de datos distinto.
    {: tip}

1. Pulse **Ejecutar**.

    Si está realizando una comprobación de validación del preanotador, abra los documentos anotados y revise las anotaciones que se han añadido. Asegúrese de que se haya creado un número suficiente de anotaciones precisas. Si las anotaciones son precisas, podrá ejecutar el anotador de nuevo en más conjuntos de documentos más grandes. Si las anotaciones no son precisas, considere la posibilidad de correlacionar tipos de entidades de {{site.data.keyword.nlushort}} distintos para sus tipos. Si los tipos no se solapan naturalmente, entonces el preanotador de {{site.data.keyword.nlushort}} no es el mejor preanotador para su uso.

    La preanotación se aplica a documentos individuales sin importar los distintos conjuntos de documentos a los que puede pertenecer un documento. Un documento que se solape entre un conjunto de documentos seleccionado y un conjunto de documentos no seleccionado se preanotará en ambos conjuntos de documentos.

1. Después de ejecutar el preanotador una vez, puede pulsar **Aplicar este preanotador** cada vez que desee utilizarlo para preanotar conjuntos de documentos adicionales que añada al corpus.

    > **Restricción:** Si edita la definición de correlación de tipos del preanotador de {{site.data.keyword.nlushort}}, debe volver a crear tareas de anotación que incluyan los conjuntos de documentos preanotados. La preanotación basada en los cambios que realice en la definición de correlación del preanotador no se puede aplicar a conjuntos de documentos ya asignados a una tarea de anotación.

### Resultados
{: #wks_preannotnlu__export-warning}

Los datos de campo producidos por documentos preanotados por el servicio de {{site.data.keyword.nlushort}} no se pueden utilizar directamente fuera de {{site.data.keyword.knowledgestudioshort}}. Puede descargar los datos de campo (en formato no legible) para moverlos de un espacio de trabajo de {{site.data.keyword.knowledgestudioshort}} a otro. Y puede seguir desarrollando los datos de campo y utilizarlos para crear un modelo de aprendizaje automático o un modelo basado en reglas que puede desplegarse para utilizarlo en servicios fuera de {{site.data.keyword.knowledgestudioshort}}.

> **Restricción:** Los documentos preanotados con {{site.data.keyword.nlushort}} están ocultos en un formato no legible al descargarse. Pero todas las anotaciones de estos documentos están ocultas, incluidas las anotaciones añadidas a los documentos mediante anotadores humanos.

**Información relacionada**:

[{{site.data.keyword.nlushort}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/watson/services/natural-language-understanding/){: new_window}

## Preanotación de documentos con un diccionario
{: #wks_preannot}

Para ayudar a los anotadores humanos a empezar con sus tareas de anotación, puede crear un diccionario y utilizarlo para preanotar documentos que añada al corpus.

### Acerca de esta tarea
{: #wks_preannot_about}

Cuando un anotador humano empiece a trabajar en documentos que fueron preanotados, es probable que un número de menciones ya estén marcadas por tipos de entidades basados en las entradas del diccionario. El anotador humano puede cambiar o eliminar los tipos de entidades preanotados y asignar tipos de entidades a menciones no anotadas. La preanotación que realice un diccionario no anota relaciones ni correferencias. Las relaciones y las correferencias deben anotarlas los anotadores humanos.

**Nota**: Esta tarea muestra cómo crear un diccionario que es editable. Si desea cargar y preanotar los documentos con un diccionario de solo lectura, pulse el icono **Menú** situado junto al botón **Crear diccionario**. Seleccione **Cargar diccionario**.

### Procedimiento
{: #wks_preannot_procedure}

Para crear un diccionario editable y preanotar documentos:

1. Inicie sesión como administrador de {{site.data.keyword.knowledgestudioshort}} y seleccione el espacio de trabajo.
1. Seleccione la página **Activos** > **Diccionarios**.
1. Pulse **Crear diccionario**, especifique un nombre y, a continuación, pulse **Guardar**.
1. Desde la lista **Tipo de entidad**, seleccione un tipo de entidad para asociar con el diccionario.
3. Añada entradas para el diccionario o cargue un archivo que contenga términos del diccionario.
4. Pulse **Modelo de aprendizaje automático** > **Preanotación**.
5. En el separador **Diccionarios**, pulse **Aplicar este preanotador**.
6. Marque el recuadro de selección para cada conjunto de documentos que desee preanotar y pulse **Ejecutar**.

    La preanotación se aplica a documentos individuales sin importar los distintos conjuntos de documentos o conjuntos de anotaciones a los que puede pertenecer un documento. Un documento que se solape entre un conjunto de documentos seleccionado y un conjunto de documentos no seleccionado se preanotará en ambos conjuntos de documentos.

7. Después de crear el diccionario, pulse **Ejecutar** en cualquier momento que desee utilizar el diccionario para preanotar conjuntos de documentos adicionales que añada al corpus.

    > **Restricción:** Si edita el diccionario para añadir o eliminar entradas, debe volver a crear las tareas de anotación que incluyan los conjuntos de documentos preanotados. La preanotación basada en los cambios que realice en el anotador del diccionario no se puede aplicar a conjuntos de anotaciones ya asignadas a una tarea de anotación.

**Información relacionada**:

[Creación de diccionarios](/docs/services/watson-knowledge-studio/dictionaries.html)

[Iniciación > Añadir un diccionario](/docs/services/watson-knowledge-studio/tutorials-create-project.html#wks_tutless4)

## Preanotación de documentos con el modelo de aprendizaje automático
{: #wks_preannotsire}

Puede utilizar un modelo de aprendizaje automático existente para preanotar documentos que añada al corpus.

### Acerca de esta tarea
{: #wks_preannotsire_about}

Una vez que se anoten de 10 a 30 documentos, se puede entrenar un modelo de aprendizaje automático en los datos. Tal modelo mínimamente entrenado no debería utilizarse en una producción, pero puede utilizarse para preanotar documentos para ayudar a acelerar la anotación humana de documentos posteriores. Por ejemplo, si añade documentos al corpus después de entrenar un modelo de aprendizaje automático, puede utilizar el modelo para preanotar los nuevos conjuntos de documentos. No ejecute nunca un preanotador en los mismos documentos que haya anotado una persona. Los preanotadores eliminan la anotación humana.

### Procedimiento
{: #wks_preannotsire_procedure}

Para utilizar un modelo de aprendizaje automático existente para preanotar documentos:

1. Inicie sesión como administrador de {{site.data.keyword.knowledgestudioshort}} y seleccione el espacio de trabajo.
2. Seleccione **Modelo de aprendizaje automático** > **Versiones**.
3. Para preanotar documentos nuevos, pulse **Ejecutar este modelo**.
4. Marque el recuadro de selección para cada conjunto de documentos que desee preanotar y pulse **Ejecutar**.

    La preanotación se aplica a documentos individuales sin importar los distintos conjuntos de documentos o conjuntos de anotaciones a los que puede pertenecer un documento. Un documento que se solape entre un conjunto de documentos seleccionado y un conjunto de documentos no seleccionado se preanotará en ambos conjuntos de documentos.

5. Puede pulsar **Ejecutar este modelo** en cualquier momento que desee utilizar el modelo de aprendizaje automático para preanotar conjuntos de documentos adicionales que añada al corpus.

## Preanotación de documentos con el modelo basado en reglas
{: #wks_preannotrule}

Puede utilizar un modelo basado en reglas existente para preanotar documentos que añada al corpus.

### Procedimiento
{: #wks_preannotrule_procedure}

Para utilizar el modelo basado en reglas para preanotar documentos, siga estos pasos:

1. Inicie sesión como administrador de {{site.data.keyword.knowledgestudioshort}} y seleccione el espacio de trabajo.
1. Seleccione el separador **Modelo basado en reglas** > **Versiones** > **Modelo basado en reglas**.
1. Si aún no se ha completado, pulse **Correlacionar tipos y clases de entidades** para correlacionar tipos de entidades definidos en el sistema de tipos de {{site.data.keyword.knowledgestudioshort}} con una o varias clases de modelos basados en reglas.
2. Pulse **Editar** para cada tipo de entidad que desee correlacionar.

    - La lista desplegable de la columna **Nombre de clase** se prerrellena con clases asociadas con el modelo basado en reglas.
    - Debe correlacionar al menos un tipo de entidad con una clase.

3. En el separador **Modelo basado en reglas**, pulse **Ejecutar este modelo**.

    El botón **Ejecutar este modelo** no estará disponible hasta que correlacione al menos un tipo de entidad con una clase.

4. Seleccione los conjuntos de documentos o conjuntos de anotaciones que desee preanotar. Asegúrese de que los conjuntos que seleccione no contengan documentos que tengan anotaciones humanas. Los preanotadores eliminan la anotación humana.
5. Pulse **Ejecutar**.

    La preanotación se aplica a documentos individuales sin importar los distintos conjuntos de documentos a los que puede pertenecer un documento. Un documento que se solape entre un conjunto de documentos seleccionado y un documento no seleccionado aparecerá preanotado en ambos conjuntos de documentos.

6. Puede pulsar **Ejecutar este modelo** en cualquier momento en que desee utilizar el modelo basado en reglas para preanotar conjuntos de documentos adicionales que añada al corpus.

    > **Restricción:** Si edita la correlación de tipo de entidad a clase del modelo basado en reglas, debe volver a crear tareas de anotación que incluyan los conjuntos de documentos preanotados. La preanotación basada en los cambios que realice en la definición de correlación del preanotador no se puede aplicar a conjuntos de documentos ya asignados a una tarea de anotación.

## Carga de documentos preanotados
{: #wks_uima}

Puede iniciar rápidamente el entrenamiento del modelo cargando documentos que fueron preanotados mediante un motor de análisis UIMA (Unstructured Information Management Architecture).

Los documentos preanotados deben estar en el formato de serialización XMI de UIMA CAS XMI (UIMA Common Analysis Structure). El archivo ZIP que cargue debe incluir el archivo descriptor de UIMA TypeSystem y un archivo que correlacione los tipos de UIMA a tipos de entidades en el sistema de tipos de {{site.data.keyword.knowledgestudioshort}}.

UIMA CAS XMI es un formato estándar de Apache UIMA. Se proporcionan directrices sobre cómo crear archivos en el formato correcto de recopilaciones analizadas en {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer. Si utiliza otra implementación de Apache UIMA, adapte estas directrices para sus propósitos. Independientemente de cómo se creen los archivos XMI, los requisitos para crear el archivo de correlación del sistema de tipos y el archivo ZIP son las mismas para todos.

Si asigna los documentos importados a los anotadores humanos, los documentos aparecerán preanotados en el editor de datos de campo y es posible que ya esté anotado un número de menciones. El anotador humano así tendrá más tiempo para centrarse en aplicar las directrices de anotación a menciones no marcadas. Como alternativa, puede omitir el paso de anotación humana y utilizar los documentos previamente anotados para iniciar inmediatamente el entrenamiento y evaluar un modelo de aprendizaje de máquina.

### Exportación de documentos analizados desde Watson Explorer Content Analytics
{: #wks_uimawexca}

Puede exportar documentos que fueron rastreados y analizados en {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer Content Analytics, y cargar los documentos analizados como archivos XMI en un espacio de trabajo de {{site.data.keyword.knowledgestudioshort}}.

#### Procedimiento
{: #wks_uima_procedure}

Para obtener documentos analizados desde una recopilación de {{site.data.keyword.watson}} Explorer Content Analytics:

1. Abra la consola de administración de Content Analytics en un navegador web.
1. En la vista Recopilaciones, expanda la recopilación desde la que desee exportar documentos. En el panel Análisis e índice, asegúrese de que se esté ejecutando el proceso de análisis y de índice, y luego pulse el icono de flecha para **Exportar contenido y metadatos de documentos analizados**.
1. En el área **Opciones de exportación de documentos analizados**, seleccione **Exportar documentos como archivos XML**, marque el recuadro de selección **Habilitar la exportación de formato CAS como XMI**, especifique la vía de acceso de resultados para dónde se grabarán los datos exportados, y pulse **Aceptar**.
1. Detenga y reinicie los servicios de análisis e índice para la recopilación, y luego realice uno de los pasos siguientes:

    - Si la recopilación ya contiene documentos indexados que desea utilizar para entrenar el modelo de aprendizaje automático en la memoria caché de documentos, reinicie una compilación de índice completa.
    - Si la recopilación no contiene documentos indexados que desee utilizar para entrenar el modelo de aprendizaje automático, cargue documentos, configure al menos un rastreador para que rastree los documentos, e inicie el rastreador.

1. En el área **Exportar**, compruebe el estado de la solicitud de exportación. El progreso indica cuántos documentos se han exportado.
1. Vaya a la carpeta de salida que haya especificado al configurar las opciones de exportación. Cuando los documentos se exporten como archivos XML, el nombre de la carpeta de salida se basará en la indicación de fecha y hora en que se produzca la exportación. La carpeta de salida contiene archivos XMI (`*.xmi`) y el archivo de descriptor de UIMA TypeSystem (`exported_typesystem.xml`).

#### Qué hacer a continuación
{: #wks_uimawexca__preUIMAimport}

Debe definir una correlación entre los tipos de UIMA y los tipos de entidades de {{site.data.keyword.knowledgestudioshort}}. También debe crear un archivo ZIP que contenga todos los archivos necesarios para cargar los datos analizados en un espacio de trabajo de {{site.data.keyword.knowledgestudioshort}}.

**Información relacionada**:

[Exportación de documentos rastreados o analizados ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ad.doc/iiysatexportca.htm){: new_window}

[Vías de acceso de resultados para documentos exportados ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ad.doc/iiysaexportoutput.htm){: new_window}

### Exportación de una recopilación analizada desde Content Analytics Studio
{: #wks_uimawexstudio}

Puede exportar una recopilación de documentos analizados desde {{site.data.keyword.watson}} Explorer Content Analytics Studio, y cargar los documentos analizados como archivos XMI en un proyecto de {{site.data.keyword.knowledgestudioshort}}.

#### Procedimiento
{: #wks_uimawexstudio_procedure}

Para obtener documentos analizados desde una recopilación de Content Analytics Studio:

1. Inicie Content Analytics Studio y abra el proyecto de Studio.
1. Pulse con el botón derecho del ratón una carpeta que contenga documentos que desee utilizar para entrenar un modelo de aprendizaje automático y seleccione **Analizar recopilación**.
1. Seleccione un archivo de configuración de interconexión de UIMA.
1. Vaya a la vista Análisis de recopilación y pulse el icono **Guardar** en la vista Análisis de recopilación. Especifique la carpeta donde se escribirán los resultados guardados y especifique el nombre de archivo.
1. Abra la carpeta que ha especificado. La extensión de archivo del archivo guardado es `.annotations`.
1. Copie el archivo `.annotations` a su sistema de archivos local y cambie el nombre de la extensión de archivo de `.annotations` a `.zip`.
1. Extraiga todos los archivos del archivo ZIP. Entre los contenidos extraídos se incluyen archivos XMI (`*.xmi`), el archivo de descriptor de UIMA TypeSystem (`TypeSystem.xml`), y otros archivos.

#### Qué hacer a continuación
{: #wks_uimawexstudio_next}

Debe definir una correlación entre los tipos de UIMA y los tipos de entidades de {{site.data.keyword.knowledgestudioshort}}. También debe crear un archivo ZIP que contenga todos los archivos necesarios para cargar los datos analizados en un espacio de trabajo de {{site.data.keyword.knowledgestudioshort}}.

### Correlación de tipos de UIMA con tipos de entidades
{: #wks_uimawexmap}

Antes de cargar archivos XMI en un espacio de trabajo de {{site.data.keyword.knowledgestudioshort}}, debe definir correlaciones entre los tipos de UIMA y los tipos de entidades de {{site.data.keyword.knowledgestudioshort}}.

#### Antes de empezar
{: #wks_uimawexmap_prereqs}

El sistema de tipos del espacio de trabajo de {{site.data.keyword.knowledgestudioshort}} debe incluir los tipos de entidades con los que desee correlacionar los tipos de UIMA.

#### Procedimiento
{: #wks_uimawexmap_procedure}

Para correlacionar los tipos de UIMA con tipos de entidades de {{site.data.keyword.knowledgestudioshort}}:

1. Cree un archivo denominado `cas2di.tsv` en la carpeta que contenga el archivo de descriptor de UIMA TypeSystem, como por ejemplo `exported_typesystem.xml` o `TypeSystem.xml`.
1. Abra el archivo `cas2di.tsv` con un editor de texto. Cada línea del archivo especifica una única correlación. El formato de la correlación depende de qué anotaciones del anotador desee correlacionar:

    - Puede crear correlaciones utilizando el formato básico:

        `UIMA_Type_Name[TAB]WKS_Entity_Type`

        El ejemplo siguiente define las correlaciones entre tipos de UIMA producidos por el anotador de Named Entity Recognition en {{site.data.keyword.watson}} Explorer Content Analytics y los tipos de entidades definidos en un sistema de tipos de {{site.data.keyword.knowledgestudioshort}}:

        ```
        com.ibm.langware.Organization  ORGANIZATION
        com.ibm.langware.Person  PERSON
        com.ibm.langware.Location  LOCATION
        ```
        {: screen}

        Otro ejemplo define una correlación entre los tipos de UIMA producidos por un anotador personalizado creado en {{site.data.keyword.watson}} Explorer Content Analytics Studio y en los tipos de entidades de {{site.data.keyword.knowledgestudioshort}}:

        ```
        com.ibm.Person  PERSON
        com.ibm.Date  DATE
        ```
        {: screen}

    - Puede crear correlaciones basadas en facetas que se utilizan en el anotador de Buscador de coincidencias de patrones o en el anotador Búsqueda en el diccionario en {{site.data.keyword.watson}} Explorer Content Analytics. En los archivos de reglas de análisis de texto (`*.pat`), la faceta está representada como el atributo de categoría. Para definir una correlación, utilice la sintaxis siguiente:

        ```
        com.ibm.takmi.nlp.annotation_type.ContiguousContext:category={FACET_PATH}[TAB]{WKS_ENTITY_TYPE}
        ```
        {: screen}

        El ejemplo siguiente, que se aplica a los anotadores de Buscador de coincidencias de patrones y de Búsqueda en el diccionario, define una correlación entre la categoría $.mykeyword.product y el tipo de entidad de {{site.data.keyword.knowledgestudioshort}} PRODUCT:

        ```
        com.ibm.takmi.nlp.annotation_type.ContiguousContext:category=$.mykeyword.product PRODUCT
        ```
        {: screen}

#### Qué hacer a continuación
{: #wks_uimawexmap_next}

Debe crear un archivo ZIP que contenga todos los archivos necesarios para cargar los datos analizados en un espacio de trabajo de {{site.data.keyword.knowledgestudioshort}}.

**Información relacionada**:

[Anotador de Buscador de coincidencias de patrones ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ta.doc/iiystapattmatch.htm){: new_window}

[Anotador de Búsqueda en el diccionario ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ta.doc/iiystadictlookup.htm){: new_window}

[Anotador de Reconocimiento de entidad con nombre ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ta.doc/iiystasystemt.htm){: new_window}

### Carga de archivos UIMA CAS XMI en un espacio de trabajo
{: #wks_uimaweximport}

Para utilizar los documentos preanotados que haya descargado para entrenar un modelo, debe crear un archivo ZIP que contenga todos los archivos necesarios para cargar los archivos XMI, y luego cargar el archivo ZIP en un espacio de trabajo de {{site.data.keyword.knowledgestudioshort}}.

#### Antes de empezar
{: #wks_uimaweximport_prereqs}

Antes de cargar el archivo ZIP, asegúrese de que el sistema de tipos de su espacio de trabajo de {{site.data.keyword.knowledgestudioshort}} incluya los tipos de entidades con los que se correlacionan los tipos de UIMA.

> **Aviso:** Los motores de análisis de UIMA permiten anotaciones para distribuir frases. En {{site.data.keyword.knowledgestudioshort}}, deben existir anotaciones dentro de los límites de una sola frase. Si los archivos XMI que cargue incluyen anotaciones que distribuyan frases, dichas anotaciones no aparecerán en el editor de datos de campo.

#### Procedimiento
{: #wks_uimaweximport_procedure}

Para cargar documentos preanotados en un espacio de trabajo de {{site.data.keyword.knowledgestudioshort}}:

1. Cree un archivo ZIP que contenga todos los archivos que necesita {{site.data.keyword.knowledgestudioshort}}.

    1. Seleccione la carpeta que contiene los archivos XMI, el archivo de descriptor del sistema de tipos UIMA y el archivo `cas2di.tsv`, o seleccione todos los archivos de la carpeta.
    1. Cree un archivo ZIP que incluya todos los archivos. Asegúrese de que los archivos de descriptor del sistema de tipos de `cas2di.tsv` y UIMA estén almacenados en el directorio raíz del archivo ZIP. Estos archivos no se pueden almacenar en una subcarpeta dentro del archivo ZIP o {{site.data.keyword.knowledgestudioshort}} no podrá leerlos, y no se importará nada.

        En Windows, puede pulsar con el botón derecho del ratón y seleccionar **Enviar a** > **Carpeta comprimida (en zip)**.

1. Cargue el archivo ZIP en un espacio de trabajo de {{site.data.keyword.knowledgestudioshort}}.

    1. Inicie sesión como administrador o gestor de proyectos de {{site.data.keyword.knowledgestudioshort}}, abra el espacio de trabajo al que desee añadir los documentos y abra la página **Activos**> **Documentos**.
    1. Pulse **Cargar conjuntos de documentos**.
    1. Arrastre el archivo ZIP que haya creado o pulse para ubicar y seleccionar el archivo.
    1. Marque el recuadro de selección para indicar que el archivo ZIP contiene archivos UIMA CAS XMI.
    1. Pulse **Cargar**.
