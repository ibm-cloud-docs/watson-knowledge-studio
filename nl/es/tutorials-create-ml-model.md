---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-24"

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

Esta documentación es para {{site.data.keyword.knowledgestudiofull}} en {{site.data.keyword.cloud}}. Para ver la documentación para la versión anterior de {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.IBM_notm}} Marketplace, [pulse este enlace ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/docs/services/knowledge-studio/tutorials-create-ml-model.html){: new_window}.
{: tip}

# Creación de un modelo de aprendizaje automático
{: #wks_tutml_intro}

Esta guía de aprendizaje le ayuda a comprender el proceso para crear un modelo de aprendizaje automático que puede desplegar y utilizar con otros servicios de {{site.data.keyword.watson}}.
{: shortdesc}

## Objetivos de aprendizaje
{: #objectives}

Tras completar las lecciones de esta guía de aprendizaje, sabrá cómo se realizan las tareas siguientes:

- Crear conjuntos de documentos
- Preanotar documentos
- Crear tareas para anotadores humanos
- Analizar el acuerdo entre anotadores y adjudicar conflictos en documentos anotados
- Crear modelos de aprendizaje automático

Para completar esta guía de aprendizaje se necesitan, aproximadamente, 60 minutos. Si explora otros conceptos relacionados con esta guía de aprendizaje, es posible que tarde más en completarla.

## Antes de empezar
{: #prereqs}

- Está utilizando un navegador soportado. Consulte [Requisitos del navegador](/docs/services/watson-knowledge-studio/system-requirements.html).
- Ha completado correctamente [Iniciación a {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/tutorials-create-project.html), que cubre la creación de un espacio de trabajo, la creación de un sistema de tipos y la adición de un diccionario.
- Debe tener al menos un ID de usuario en el rol de Admin o Gestor de proyectos.

    > **Nota:** Si es posible, utilice varios ID de usuario para las tareas del modelo de aprendizaje automático de esta guía de aprendizaje (un ID de usuario de Admin o Gestor de proyectos y al menos dos ID de usuario de Anotador humano). Utilizar varios ID de usuario proporciona la simulación más realista de un espacio de trabajo real de {{site.data.keyword.knowledgestudiofull}}, donde un gestor de proyectos debe coordinar y adjudicar la anotación realizada por varios anotadores humanos. Sin embargo, si tiene acceso solo a un único ID de usuario, puede seguir simulando la mayor parte del proceso.

    Para obtener información sobre los roles de usuario, consulte [Roles de usuario en {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/roles.html).

## Resultados
{: #results}

Después de completar esta guía de aprendizaje, tendrá un modelo de aprendizaje automático personalizado que puede utilizar con otros servicios de {{site.data.keyword.watson}}.

## Lección 1: Añadir documentos para su anotación
{: #tut_lessml1}

En esta lección, aprenderá a añadir documentos a un espacio de trabajo en {{site.data.keyword.knowledgestudioshort}} que pueden anotar los anotadores humanos.

### Acerca de esta tarea
{: #tut_lessml1_about}

Para obtener más información sobre cómo añadir documentos, consulte [Adición de documentos a un espacio de trabajo](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projadd).

### Procedimiento
{: #tut_lessml1_procedure}

1. Descargue el archivo <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/documents-new.csv" download>`documents-new.csv` <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo" title="Icono de enlace externo" class="style-scope doc-content"></a> en su sistema. Este archivo contiene documentos de ejemplo adecuados para cargarse.
1. Dentro del espacio de trabajo, pulse **Activos** > **Documentos**.
1. En la página Documentos, pulse **Cargar conjuntos de documentos**.
1. Cargue el archivo `documents-new.csv` desde el sistema. El archivo cargado se mostrará en la tabla.

### Qué hacer a continuación
{: #tut_lessml1_next}

Ahora puede dividir el corpus en varios conjuntos de documentos y asignar los conjuntos de documentos a anotadores humanos.

## Lección 2: Creación de conjuntos de anotaciones
{: #wks_tutless_ml2}

En esta lección, aprenderá a crear conjuntos de anotaciones en {{site.data.keyword.knowledgestudioshort}}.

### Acerca de esta tarea
{: #wks_tutless_ml2_about}

Un *conjunto de anotaciones* es un subconjunto de documentos desde un conjunto de documentos cargados que puede asignar a un anotador humano. El anotador humano anota los documentos en el conjunto de anotaciones. Para utilizar más tarde puntuaciones entre anotadores para comparar las anotaciones añadidas por cada anotador humano, debe asignar al menos dos anotadores humanos a distintos conjuntos de anotaciones. También debe especificar que algún porcentaje de documentos se solape entre los conjuntos.

> **Nota:** En un caso de ejemplo realista, podría crear tantos conjuntos de anotaciones como sea necesario, en función del número de anotadores humanos que trabajen en el espacio de trabajo. En esta guía de aprendizaje, va a crear dos conjuntos de anotaciones. Si no tiene acceso a varios ID de usuarios, puede asignar ambos conjuntos de anotaciones al mismo usuario.

Para obtener más información sobre los conjuntos de anotaciones, consulte [Creación y asignación de conjuntos de anotaciones](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projdocsets).

### Procedimiento
{: #wks_tutless_ml2_procedure}

1. Dentro del espacio de trabajo, pulse **Activos** > **Documentos**.
2. Pulse **Crear conjuntos de anotaciones**.

    Se abrirá la ventana Crear conjuntos de anotaciones. De forma predeterminada, esta ventana muestra el conjunto base, que contiene todos los documentos, y los campos donde puede especificar la información para un nuevo conjunto de anotaciones.

3. Pulse **Añadir otro conjunto y anotador humano** para añadir campos para un conjunto de anotaciones adicional. Puede pulsar para añadir tantos conjuntos de anotaciones como desee crear. Para esta guía de aprendizaje, solo necesita dos conjuntos de anotaciones.

    ![Una captura de pantalla de la página Crear conjuntos de anotaciones.](images/wks_tutdocset2.jpg "Una captura de pantalla de la página Crear conjuntos de anotaciones.")

4. En el campo **Solapar**, especifique `100`. Este valor especifica que desea que se incluya el 100 por ciento de los documentos del conjunto base en todos los conjuntos de anotaciones nuevos para que los puedan anotar todos los anotadores humanos.
5. Para cada nuevo conjunto de anotaciones, especifique la información necesaria.

    - En el campo **Anotador**, seleccione un ID de usuario de anotador humano para asignar al nuevo conjunto de anotaciones. En un caso de ejemplo realista, cada conjunto de anotaciones se asigna a un anotador humano diferente.

        > **Nota:** Si solo tiene un único ID de administrador para utilizar para la guía de aprendizaje, asigne dicho usuario a todos los conjuntos de anotaciones. En un caso de ejemplo realista, tendría varios anotadores humanos, pero para la guía de aprendizaje, el administrador puede actuar como anotador humano.

    - En el campo **Establecer nombre**, especifique un nombre descriptivo para el conjunto de anotaciones. Para esta guía de aprendizaje, puede utilizar los nombres `Set 1` y `Set 2`.

6. Pulse **Generar**.

### Resultados
{: #wks_tutless_ml2_results}

Se crean los nuevos conjuntos de anotaciones.

## Lección 3: Preanotación con un anotador basado en diccionario
{: #wks_tutless_ml3}

En esta lección, aprenderá a utilizar un anotador basado en diccionario para preanotar documentos en {{site.data.keyword.knowledgestudioshort}}.

### Acerca de esta tarea
{: #wks_tutless_ml3_about}

La preanotación de documentos es un paso opcional. Sin embargo, es un paso que merece la pena, porque facilita el trabajo de los anotadores humanos.

Para obtener más información sobre la preanotación con diccionarios, consulte [Preanotación de documentos con un diccionario](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannot).

### Procedimiento
{: #wks_tutless_ml3_procedure}

1. Dentro del espacio de trabajo, pulse **Activos** > **Diccionarios**.

  Se abrirá el diccionario `Probar diccionario`. La lección [Añadir un diccionario](/docs/services/watson-knowledge-studio/tutorials-create-project.html#wks_tutless4) de la guía de aprendizaje *Iniciación a {{site.data.keyword.knowledgestudioshort}}* muestra cómo crear este diccionario.

1. En la lista **Tipo de entidad**, seleccione el tipo de entidad `ORGANIZATION` para correlacionarlo con el diccionario `Diccionario de prueba`.

  La lección [Creación de un sistema de tipos](/docs/services/watson-knowledge-studio/tutorials-create-project.html#wks_tutless3) de la guía de aprendizaje *Iniciación a {{site.data.keyword.knowledgestudioshort}}* muestra cómo crear el sistema de tipos que contiene el tipo de entidad `ORGANIZATION`.

1. En el separador **Modelo de aprendizaje automático** > **Preanotación** > **Diccionarios**, pulse **Aplicar este preanotador**.
1. Seleccione los conjuntos de anotaciones que ha creado en la [Lección 2](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml2), sin incluir el conjunto de documentos que ha creado en la [Lección 1](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#tut_lessml1).
1. Pulse **Ejecutar**.

    ![Esta captura de pantalla muestra la página Ejecutar anotador. El botón Ejecutar está resaltado.](images/wks_tutanno3.jpg "Esta captura de pantalla muestra la página Ejecutar anotador. El botón Ejecutar está resaltado.")

### Resultados
{: #wks_tutless_ml3_results}

Los documentos de los conjuntos seleccionados se preanotan utilizando el diccionario que ha creado. Si lo desea, puede utilizar el diccionario para preanotar conjuntos de documentos o conjuntos de anotaciones que añada posteriormente.

## Lección 4: Creación de una tarea de anotación
{: #wks_tutless_ml4}

En esta lección, aprenderá a utilizar tareas de anotación para realizar un seguimiento del trabajo de los anotadores humanos en {{site.data.keyword.knowledgestudioshort}}.

### Acerca de esta tarea
{: #wks_tutless_ml4_about}

Para obtener más información sobre las tareas de anotación, consulte [Creación de una tarea de anotación](/docs/services/watson-knowledge-studio/annotate-documents.html#wks_hatask).

### Procedimiento
{: #wks_tutless_ml4_procedure}

1. Dentro del espacio de trabajo, pulse **Modelo de aprendizaje automático** > **Tareas de anotación**.
2. En la página Tareas, pulse **Añadir tarea**.
3. Especifique los detalles para la tarea:

    - En el campo **Nombre de tarea**, especifique `Prueba`.
    - En el campo **Plazo**, seleccione una fecha del futuro.

4. Pulse **Crear**.
5. Seleccione los conjuntos de anotaciones que ha creado en la [Lección 2](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml2).

 La selección de ambos conjuntos de anotaciones especifica que ambos conjuntos deben anotarlos sus anotadores humanos asignados para completar esta tarea.

7. Pulse **Crear tarea**.
8. A medida que los anotadores humanos empiezan a anotar documentos, puede abrir tareas para ver su progreso.

## Lección 5: Anotación de documentos
{: #wks_tutless_ml5}

En esta lección, aprenderá a utilizar el *editor de datos de campo* para anotar documentos en {{site.data.keyword.knowledgestudioshort}}.

### Acerca de esta tarea
{: #wks_tutless_ml5_about}

Para obtener más información sobre la anotación humana, consulte [Anotación con el editor de datos de campo](/docs/services/watson-knowledge-studio/user-guide.html#wks_hagte).

### Procedimiento
{: #wks_tutless_ml5_procedure}

1. Inicie sesión en {{site.data.keyword.knowledgestudioshort}} como usuario asignado a la tarea de anotación que ha creado en la [Lección 4](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml4).

    > **Nota:** Si solo tiene acceso a un único ID de administrador para esta guía de aprendizaje, puede utilizar dicho ID para realizar la anotación humana. Sin embargo, recuerde que en un caso de ejemplo realista, la anotación humana la realizan usuarios distintos con el rol Anotador humano.

1. Abra el espacio de trabajo `Mi espacio de trabajo` y pulse **Modelo de aprendizaje automático** > **Tareas de anotación**.
1. Abra la tarea de anotación `Prueba` que ha creado en [Lección 4](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml4).
1. Pulse **Anotar** para uno de los conjuntos de anotaciones asignados.

  En función de cómo configure las tareas de anotación, puede tener una o más tareas de anotación asignadas al ID de usuario con el que ha iniciado la sesión.

1. En la lista de documentos, busque el documento *Tecnología - gmanews.tv* y ábralo.

  Observe que el término `IBM` ya se ha anotado con el tipo de entidad `ORGANIZATION`. Esta anotación la ha añadido el preanotador de diccionarios en que se ha aplicado en la [Lección 3](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml3). Esta preanotación es correcta, por lo que no es necesario modificarla.

  ![Esta captura de pantalla muestra un documento abierto con una preanotación existente para "IBM".](images/wks_tut_preannotation.png "Esta captura de pantalla muestra un documento abierto con una preanotación existente para ")

1. Anotar una mención:

    1. Pulse el separador Entidad.
    2. En el cuerpo del documento, seleccione el texto `Thomas Watson`.
    3. En la lista de tipos de entidades, pulse `PERSON`. El tipo de entidad `PERSON` se aplica a la mención seleccionada.

        ![Esta captura de pantalla muestra el tipo de entidad "PERSON" aplicado a la mención, "Thomas Watson".](images/wks_tut_annotatemention3.png "Esta captura de pantalla muestra el tipo de entidad ")

1. Anote una relación:

    1. Pulse el separador Relación.
    1. Seleccione las menciones `Thomas Watson` e `IBM` (en ese orden). Para seleccionar una mención, pulse la etiqueta de tipo de entidad que hay encima del texto.
    1. En la lista de tipos de relaciones, pulse `founderOf`. Las dos menciones están conectadas con una relación `founderOf`.

        ![Esta captura de pantalla muestra dos menciones conectadas por el tipo de relación, "founderOf".](images/wks_tut_annotaterelation.png "Esta captura de pantalla muestra dos menciones conectadas por el tipo de relación, ")

1. Desde el menú de estado, seleccione **Completado**, y luego pulse el botón **Guardar**.
1. Pulse **Abrir lista de documentos** para volver a la lista de documentos de esta tarea y pulse **Enviar todos los documentos** para enviar los documentos para su aprobación.

    > **Nota:** En una situación realista, debería crear muchas más anotaciones y completar todos los documentos del conjunto antes de enviar.

1. Cierre este conjunto de anotaciones y, a continuación, abra el otro conjunto de anotaciones en la tarea `Prueba`.

   En función de cómo configure las tareas de anotación y a qué usuarios las haya asignado, es posible que tenga que iniciar la sesión en {{site.data.keyword.knowledgestudioshort}} como el usuario asignado al otro conjunto de anotaciones en la tarea de anotación.

1. Repita las mismas anotaciones en el documento *Tecnología - gmanews.tv*, pero esta vez utilice la relación `employedBy` en lugar de la relación `founderOf`.

  Iniciar sesión como otro usuario ayudará a ilustrar el acuerdo entre anotadores en la lección siguiente. Pero si sólo tiene un usuario, todavía puede completar la guía de aprendizaje para saber cómo funciona el acuerdo entre anotadores.

1. Después de completar las anotaciones para el segundo conjunto de anotaciones, pulse **Enviar todos los documentos**.

## Lección 6: Análisis del acuerdo entre anotadores
{: #wks_tutless_ml6}

En esta lección, aprenderá a comparar el trabajo de varios anotadores humanos en {{site.data.keyword.knowledgestudioshort}}.

### Acerca de esta tarea
{: #wks_tutless_ml6_about}

Para determinar si distintos anotadores humanos están anotando documentos solapados de forma coherente, revise las puntuaciones del *acuerdo entre anotadores* (IAA).

{{site.data.keyword.knowledgestudioshort}} calcula las puntuaciones de IAA examinando todos los documentos solapados en todos los conjuntos de documentos de la tarea, independientemente del estado de los conjuntos de documentos. Las puntuaciones de IAA muestran cómo han anotado distintos anotadores humanos menciones, relaciones y cadenas de correferencia. Es una buena idea comprobar las puntuaciones de IAA periódicamente y verificar que los anotadores humanos sean coherentes entre sí.

En esta guía de aprendizaje, los anotadores humanos han enviado todos los conjuntos de documentos para su aprobación. Si las puntuaciones del acuerdo entre anotadores son aceptables, podrá aprobar los conjuntos de documentos. Si rechaza un conjunto de documentos, se devolverá al anotador humano para su mejora.

Para obtener más información sobre el acuerdo entre anotadores, consulte [Creación de los datos de campo](/docs/services/watson-knowledge-studio/build-groundtruth.html).

### Procedimiento
{: #wks_tutless_ml6_procedure}

1. Inicie sesión en {{site.data.keyword.knowledgestudioshort}} como administrador, seleccione **Modelo de aprendizaje automático** > **Tareas de anotación** y pulse la tarea `Prueba`.

  En la columna **Estado**, puede ver que los conjuntos de documentos están enviados.

1. Pulse **Calcular acuerdo entre anotadores**.
1. Vea puntuaciones de IAA para las cadenas de menciones, relaciones y correferencia pulsando el primer menú. También puede ver el acuerdo de pares de anotadores humanos. También puede ver el acuerdo de documentos específicos. En general, el objetivo de una puntuación es de 0,8 de 1, lo que significa que 1 es un acuerdo perfecto. Puesto que solo ha anotado dos tipos de entidades en esta guía de aprendizaje, la mayoría de las puntuaciones del tipo de entidad son `N/D` (no disponible), lo que significa que no hay información disponible para dar una puntuación.

    *Figura 1. Revisión de las puntuaciones entre anotadores con los usuarios llamados `dave` y `phil`*

    ![Esta captura de pantalla muestra las puntuaciones entre anotadores para una tarea.](images/wks_tutiaa2.gif "Esta captura de pantalla muestra las puntuaciones entre anotadores para una tarea.")

1. Después de revisar las puntuaciones, puede decidir si desea aprobar o rechazar conjuntos de documentos que se encuentran en el estado `ENVIADO`. Lleve a cabo una de estas acciones:

    - Si las puntuaciones son aceptables para un conjunto de anotaciones, marque el recuadro de selección y pulse **Aceptar**. Los documentos que no se solapan con otros conjuntos de documentos se promocionarán a datos de campo. Los documentos que se solapan deben en primer lugar ser revisados mediante adjudicación para que los conflictos se puedan resolver. Para esta guía de aprendizaje, acepte los dos conjuntos de documentos.
    - Si las puntuaciones no son aceptables para un conjunto de anotaciones, marque el recuadro de selección y pulse **Rechazar**. El conjunto de documentos necesita ser revisado por el anotador humano para mejorar las anotaciones.

### Resultados
{: #wks_tutless_ml6_results}

Cuando se hayan evaluado las puntuaciones del acuerdo entre anotadores, verá cómo distintos pares de anotadores humanos han anotado el mismo documento. Si la puntuación del acuerdo entre anotadores fue aceptable, aceptará el conjunto de documentos.

## Lección 7: Adjudicación de conflictos en documentos anotados
{: #wks_tutless_ml7}

En esta lección, aprenderá a adjudicar conflictos en documentos que se solapan entre conjuntos de documentos de {{site.data.keyword.knowledgestudioshort}}.

### Acerca de esta tarea
{: #wks_tutless_ml7_about}

Cuando se aprueba un conjunto de documentos, solo se promocionarán a datos de campo los documentos que no se solapen con otros conjuntos de documentos. Si un documento forma parte del solapamiento entre varios conjuntos de documentos, debe adjudicar cualquier conflicto de anotación antes de promocionar el documento a datos de campo.

Para obtener más información sobre la adjudicación, consulte [Creación de los datos de campo](/docs/services/watson-knowledge-studio/build-groundtruth.html).

### Procedimiento
{: #wks_tutless_ml7_procedure}

1. Inicie sesión en {{site.data.keyword.knowledgestudioshort}} como administrador, seleccione **Modelo de aprendizaje automático** > **Tareas de anotación** y pulse la tarea `Prueba`.
1. Verifique que los dos conjuntos de documentos estén en un estado aprobado.
1. Pulse **Comprobar solapamiento de documentos en busca de conflictos**.

    Puede ver los documentos solapados anotados por más de un anotador humano.

1. Puesto que en guía de aprendizaje se ha indicado que cree una relación conflictiva para el documento *Tecnología - gmanews.tv *, busque ese documento en la lista y pulse **Comprobar conflictos**.
1. Seleccione dos conjuntos de anotaciones conflictivos y pulse **Comprobar conflictos**.

    Se abrirá la modalidad de adjudicación. En la modalidad de adjudicación, puede ver documentos solapados, comprobar conflictos y eliminar o sustituir anotaciones antes de promocionar los documentos a datos de campo.

1. Seleccione **Conflictos de relación**, acepte la relación `founderOf` y rechace la relación `employedBy`.
1. Pulse **Promocionar a datos de campo**.

    Como alternativa, puede promocionar un documento a datos de campo pulsando **Aceptar** en la página Documentos.

### Resultados
{: #wks_tutless_ml7_results}

Después de resolver los conflictos de anotaciones y de promocionar los documentos a datos de campo, podrá utilizarlos para entrenar el modelo de aprendizaje automático.

## Lección 8: Creación de un modelo de aprendizaje automático
{: #wks_tutless_ml8}

En esta lección, aprenderá a crear un modelo de aprendizaje automático en {{site.data.keyword.knowledgestudioshort}}.

### Acerca de esta tarea
{: #wks_tutless_ml8_about}

Cuando se crea un modelo de aprendizaje automático, seleccione los conjuntos de documentos que desea utilizar para entrenarlo. Especifique también el porcentaje de documentos que se utilizarán como datos de entrenamiento, datos de prueba y datos ciegos. Solo se podrán utilizar los documentos que se conviertan en datos de campo mediante la aprobación o la adjudicación para entrenar el modelo de aprendizaje automático.

Para obtener más información sobre el modelo de aprendizaje automático, consulte [Entrenamiento del modelo de aprendizaje automático](/docs/services/watson-knowledge-studio/train-ml.html) y [Análisis del rendimiento del modelo de aprendizaje automático](/docs/services/watson-knowledge-studio/evaluate-ml.html).

### Procedimiento
{: #wks_tutless_ml8_procedure}

1. Inicie una sesión en {{site.data.keyword.knowledgestudioshort}} como administrador.
1. Pulse **Modelo de aprendizaje automático** > **Rendimiento** > **Entrenar y evaluar**.
2. Seleccione **Todo** y a continuación, pulse **Entrenar y evaluar**.

    > **Nota:** El entrenamiento puede llevar más de diez minutos, o incluso horas, dependiendo del número de anotaciones humanas y del número de palabras en todos los documentos.

3. Una vez que el modelo de aprendizaje automático esté entrenado, puede exportarlo desde la página Versión o puede ver información detallada sobre su rendimiento pulsando los enlaces **Estadísticas detalladas** que se ubican por encima de cada gráfico en la página Rendimiento.
4. Para ver la página Conjuntos de formación / prueba / ciegos, pulse el botón **Entrenar y evaluar**.
5. Para ver los documentos en los que han trabajado los anotadores humanos, pulse **Ver datos de campo**.
6. Para ver las anotaciones que ha creado el modelo de aprendizaje automático en ese mismo conjunto de documentos, pulse **Ver resultados de descodificación**.
7. Para ver detalles sobre las puntuaciones de precisión, recuperación y F1 para el modelo de aprendizaje automático, pulse la página Rendimiento.
8. Pulse los enlaces **Estadísticas detalladas** por encima de cada uno de los gráficos. En estas páginas de Estadísticas, puede ver las puntuaciones para cadenas de menciones, relaciones y correferencias utilizando los botones de selección.

    Puede analizar el rendimiento viendo un resumen de estadísticas para los tipos de entidades, los tipos de relaciones y las cadenas de correferencia. También puede analizar estadísticas presentadas en una *matriz de confusión*. Para ver la matriz, cambie **Resumen** por **Matriz de confusión**. La matriz de confusión le ayuda a comparar las anotaciones añadidas por el modelo de aprendizaje automático con las anotaciones de los datos de campo.

    > **Nota:** En esta guía de aprendizaje, ha anotado documentos con un único diccionario para las organizaciones. Por lo tanto, las puntuaciones que verá son `0` o `N/D` para la mayoría de los tipos de entidades, excepto `ORGANIZATION`. Los números son bajos, pero es lo que se esperaba, porque no se ha realizado ninguna anotación ni corrección humana.

    *Figura 2. Opciones de la página Estadísticas para un modelo de aprendizaje automático*

    ![Esta captura de pantalla muestra la página Estadísticas.](images/wks_tutanno9.gif "Esta captura de pantalla muestra la página Estadísticas.")

9.  Pulse **Versiones**. En la página Versiones, puede realizar una instantánea del modelo y de los recursos utilizados para crearlo (excepto diccionarios y tareas de anotación). Por ejemplo, puede que desee realizar una instantánea antes de volver a entrenar el modelo. Si las estadísticas son peores la próxima vez que lo entrene, puede promocionar la versión más antigua y suprimir la versión que devolvió peores resultados.

### Resultados
{: #wks_tutless_ml8_results}

Ha creado un modelo de aprendizaje automático, lo ha entrenado y ha evaluado cómo ha funcionado al anotar datos de prueba y datos ciegos. Al explorar las métricas de rendimiento, puede identificar maneras de mejorar la exactitud del modelo de aprendizaje automático.

## Resumen de la guía de aprendizaje
{: #wks_tutml_sum}

Ha creado un modelo de aprendizaje automático.

### Lecciones aprendidas
{: #lessons_learned}

Al completar esta guía de aprendizaje, habrá aprendido los siguientes conceptos:

- Conjuntos de documentos
- Modelos de aprendizaje automático
- Tareas de anotación humana
- Acuerdo entre anotadores y adjudicación
