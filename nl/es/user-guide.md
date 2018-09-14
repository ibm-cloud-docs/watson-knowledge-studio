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

Esta documentación es para {{site.data.keyword.knowledgestudiofull}} en {{site.data.keyword.cloud}}. Para ver la documentación para la versión anterior de {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.IBM_notm}} Marketplace, [pulse este enlace ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/services/knowledge-studio/user-guide.html){: new_window}.
{: tip}

# Anotación de documentos
{: #user-guide}

La información de esta sección ayuda a los expertos en la materia a los que se ha pedido anotar los documentos del sector a utilizar el editor de datos de campo para completar la tarea.
{: shortdesc}

## Acceso al espacio de trabajo
{: #wks_access_for_annotator}

No podrá ver ningún espacio de trabajo hasta que alguien más cree un espacio de trabajo y le dé acceso al mismo.

Cuando un administrador le añada a una instancia de {{site.data.keyword.knowledgestudioshort}}, se le añadirá en el rol de anotador humano. Con tal rol, no puede crear un espacio de trabajo. Para obtener acceso a un espacio de trabajo, el administrador debe crear uno. Entonces, el administrador o un gestor de proyectos que el administrador asocie con el espacio de trabajo debe realizar los pasos siguientes:

1. Crear un conjunto de anotaciones y asociarle con él.
1. Crear una tarea que le asigne para anotar los documentos del conjunto.

Podrá ver el espacio de trabajo cuando se le asigne una tarea de anotación.

Si se le ha invitado a participar en un espacio de trabajo de {{site.data.keyword.knowledgestudioshort}}, pero no ve ningún espacio de trabajo desde la página Espacios de trabajo, póngase en contacto con la persona que le ha invitado, y pídale que realice los pasos necesarios.

## Mejores prácticas de anotación
{: #wks_anno_bp}

Estas mejores prácticas de anotación proporcionan cierta orientación y ejemplos para empezar a anotar documentos.

- Anote todos los documentos completamente.

    El aprendizaje automático aprende de ejemplos negativos (lo que no se anota) no solo a partir de lo que se ha anotado. Por lo tanto, sea prudente en lo que anote, pero realice un trabajo completo. Si ha anotado cuidadosamente solo los primeros 5 de 10 documentos de un conjunto, las anotaciones que no capture en los últimos 5 documentos enseñarán al modelo a ignorar cualquier entidad o menciones de relación que no se mencionaron en dichos documentos. Puede terminar revirtiendo cualquier ganancia que haya realizado haciendo un trabajo exhaustivo con los primeros 5 documentos.

- La anotación coherente es al menos tan importante como la anotación correcta.

    Algunas decisiones que tienen que ver con las directrices de anotación son arbitrarias, como si las líneas de corte de un coche debieran ser consideradas como parte de los nombres del modelo, como por ejemplo *Camry* o *Camry LX*. Las políticas que se escojan son mucho menos importantes que el equipo de proyecto esté de acuerdo en una u otra y que anote en conformidad con dicha política de forma coherente.

- Menciones de entidades de etiquetas solo en límites de palabra-señal, porque la búsqueda de mención-detección funciona a nivel de palabra-señal de granularidad.
- Menciones de entidades de etiquetas limitadas a una o dos palabras adyacentes siempre que sea posible.

    Hacerlo no siempre es posible o fácil. Considere estos ejemplos:
    - El documento fuente contiene una frase desde la que, para los fines de la aplicación que utilizará el sistema de tipos, se desea anotar el problema y su causa.

        ```
        The electronic module was burnt because the wrong voltage was applied.
        ```
        {: screen}

        Se podría estar tentado a anotar el problema y la causa así:

        ```
                    [PROBLEM][CAUSE]
        ```
        {: screen}

        ```
        [The electronic module was burnt][because the wrong voltage was applied].
        ```
        {: screen}

        Sin embargo, no es una práctica recomendada anotar frases tan largas como tipos de entidades. En cambio, busque las entidades de importancia e identifique cómo se asocian entre sí definiendo una mención de relación.

        ```
               [LOCATION][SYMPTOM]                [CAUSE]
        ```
        {: screen}

        ```
        The [electronic module] was [burnt] because the [wrong voltage] was applied.
        ```
        {: screen}

        ```
                      ^---isStatusOf--| |------causedBy-------^
        ```
        {: screen}

    - El documento fuente contiene un verbo dividido que desea anotar. ¿Cómo anota texto no contiguo como un único tipo de entidad? Puede anotar cada mención de entidad, e identificarlas como relacionadas entre sí mediante una mención de relación.

        ```
                  [EVENT_ANSWER][EVENT_ANSWER]
        ```
        {: screen}

        ```
        All of the phones were ringing, but he knew he should [pick] the red phone [up] first.
        ```
        {: screen}

        ```
                            ^----splitType-----^
        ```
        {: screen}

- Evite solapar menciones, que son dos etiquetas de tipo de entidad distintas aplicadas a una única frase de un documento. Por ejemplo, dada la frase *She donated her father's journals to the JFK Library.*, debería solapar menciones si anota `JFK`=`PERSON` y `JFK Library`=`LOCATION` para la frase única *JFK Library*. El uso del término es más sobre la biblioteca que la persona de esta frase, por lo que solo se aplicaría la segunda anotación.

    Descodificar tales estructuras requiere varias invocaciones paralelas de un modelo de aprendizaje automático porque la detección de menciones solo busca una etiqueta única o ninguna etiqueta en cada señal de palabra.

- Determine cómo manejará el equipo las listas y los plurales en el texto en ejecución. Por ejemplo, el sistema de tipos KLUE tiene los tipos de entidades `PERSON` y `PEOPLE` que distinguen el singular del plural. Puede elegir anotar la lista *Barack, Michelle, Malia, and Sasha Obama*, de una de las formas siguientes:

    - Anotar cada elemento de la lista como una mención de entidad singular (*Barack*, *Michelle*, *Malia*, y *Sasha Obama* son cada una una mención de `PERSON`)
    - Anotar la frase entera como una mención de entidad plural (*Barack, Michelle, Malia, and Sasha Obama* es una sola mención de `PEOPLE`).

    Ninguno de los dos métodos es necesariamente mejor que el otro. Basta con asegurarse de que su equipo elija uno de ellos y lo aplique de forma coherente a cualquier lista que se dé en los documentos.

- Se utiliza una correferencia cuando las menciones hacen referencia a la misma entidad real. Las relaciones se utilizan entre entidades distintas. Por lo tanto, no deben estar conectadas dos menciones mediante correferencia ni como una relación.

## Anotación con el editor de datos de campo
{: #wks_hagte}

Cuando un anotador humano anota un documento, este se abrirá en el *editor de datos de campo*. El editor de datos de campo es una herramienta visual que los anotadores humanos utilizan para aplicar etiquetas a texto.

El objetivo de la anotación humana es etiquetar menciones, relaciones y menciones correferenciadas para que el modelo de aprendizaje automático pueda ser entrenado para detectar estos patrones en texto invisible. Como mínimo, utilice la herramienta para anotar menciones de entidades. Si la aplicación que utilizará el modelo resultante no necesita encontrar ni extraer correferencias ni menciones de relaciones, no será necesario anotar correferencias ni menciones de relaciones.

La concordancia es una herramienta opcional que pueden utilizar los anotadores humanos para acelerar la anotación de menciones repetitivas.

Elija una modalidad que se utilizará al anotar documentos manualmente:

- Modalidad de **mención**

    En esta modalidad, el anotador humano asocia tipos de entidades, como se define en el sistema de tipos, con palabras o frases significativas en el texto. Por ejemplo, todas las menciones de nombres de persona pueden estar asociadas con un tipo de entidad denominado PERSON. La anotación de menciones es necesaria y debe producirse antes de anotar tipos de relaciones y menciones como correferencias.

    El anotador humano puede utilizar opcionalmente la herramienta de concordancia para asegurarse de que esté anotado el mismo texto con el mismo tipo de entidad en un documento y en los conjuntos de anotaciones.

- Modalidad de **relación**

    En esta modalidad, el anotador humano conecta menciones asociando un tipo de relación, tal como se define en el sistema de tipos. Por ejemplo, la mención `John Smith` podría estar conectada con la mención `{{site.data.keyword.IBM_notm}}` mediante el tipo de relación `employedBy`. La anotación de tipos de relaciones es opcional y puede producirse antes o después de anotar menciones como correferencias.

- Modalidad de **correferencia**

    En esta modalidad, el anotador humano identifica menciones que significan lo mismo, ayudando así a garantizar la coherencia en las anotaciones cuando las palabras no son idénticas. Por ejemplo, la mención de `{{site.data.keyword.IBM_notm}}` en la primera frase, la mención de `International Business Machines` y la mención de `{{site.data.keyword.IBM_notm}}` en una frase posterior hacen referencia a lo mismo y deberían ser etiquetadas mediante el mismo tipo de entidad, como `ORGANIZATION`. La anotación de menciones como correferencias es opcional y se puede producir antes o después de anotar tipos de relaciones.

### Sugerencias para utilizar el editor
{: #wks_hagte_tips}

- Guarde el trabajo a medida que se vaya.
- Si comete un error, puede pulsar Ctrl+Z para deshacer la acción anterior. Para rehacer la acción después de deshacerla, pulse Ctrl+Y. Puede deshacer las 10 acciones anteriores que haya realizado mientras edita el documento actual. Las acciones se pierden al cerrar el documento. Las acciones deben deshacerse en orden inverso, y usted debe conmutar a la modalidad en la que estaba al realizar la acción para deshacerla. No puede deshacer ni rehacer acciones de la herramienta de concordancia.

## Anotación de menciones de entidad
{: #wks_haentity}

Para anotar menciones de entidad, un anotador humano selecciona una serie de texto en un documento, y luego aplica una etiqueta que describe lo más apropiadamente posible lo que representa la serie de texto. Las etiquetas que pueden aplicarse son tipos de entidades definidos en el sistema de tipos del espacio de trabajo.

### Acerca de esta tarea
{: #wks_haentity_about}

Antes de empezar a anotar menciones de entidades en un documento, es una práctica recomendada leer todo el documento. Hacerlo puede ayudar a mantener el contexto completo en cuenta al anotar, y puede ayudar a proporcionar información sobre cómo se pueden relacionar entre sí las menciones de entidades y qué menciones necesitarían ser correferenciadas en los pases futuros en el documento.

Cuando se abre un documento para anotarlo, es posible que desee utilizar la herramienta de concordancia para anotar repitiendo las menciones de entidades en primer lugar, y luego anotar las menciones de entidades individuales. Entonces podrá anotar las menciones y las correferencias de relaciones en el orden que desee, o ninguna en absoluto. La anotación de las menciones de entidades es obligatoria. Si anota también menciones y correferencias de relaciones dependerá de la finalidad del modelo y de las necesidades del dominio. Sin embargo, hasta y a menos que se identifiquen las correferencias, se considerará que cada mención de entidad representa una entidad distinta.

#### Sugerencias
{: #wks_haentity_tips}

- Tenga en cuenta que las menciones de entidades más cortas son mejores para el entrenamiento porque es más fácil que el modelo de aprendizaje automático reconozca los patrones más cortos y añada señales de anotación correctas.
- Si elige utilizar un señalizador basado en diccionario con el espacio de trabajo, y desea manejar términos compuestos y puntuación en los datos de entrenamiento, puede añadir los términos a un diccionario y crear un anotador de diccionarios para preanotar las apariciones. Por ejemplo, para evitar las interrupciones de límites de frases para términos que incluyan puntuación, añada términos como Yahoo! y Dr. a un diccionario. Asimismo, si los datos de entrenamiento incluyen palabras con guiones o acrónimos alfanuméricos, como `Hi-C` o `MS-60-70`, añada esos términos al diccionario. Para anotar apariciones con independencia de las mayúsculas y minúsculas, añada los términos en minúscula (como `hi-c`). Para anotar variaciones, añada las variaciones como formas superficiales (`MS-60-70` y `MS 60 70`).

   **Importante**: No utilice este enfoque si está utilizando el señalizador predeterminado.

### Procedimiento
{: #wks_haentity_procedure}

Para anotar menciones de entidades en un documento:

1. Inicie sesión como un anotador humano (o como un administrador al que se asignan documentos para anotar). Se mostrarán los espacios de trabajo que contienen tareas que tiene asignadas.
1. Abra un espacio de trabajo y pulse **Modelo de aprendizaje automático** > **Tareas de anotación**. Se mostrarán las tareas de anotación que tiene asignadas.
1. Abra la tarea de anotación en la que desee trabajar. Se mostrarán los conjuntos de anotaciones que tiene asignados.
1. Pulse **Anotar** para abrir el conjunto de anotación en el que desee trabajar. Se mostrarán los documentos del conjunto de anotaciones.
1. Abra el documento que desee anotar. De forma predeterminada, el documento se en modalidad **Mención**, que es la modalidad que se utiliza para anotar menciones de entidades.
1. Empiece a anotar menciones de entidad.

    1. Pulse una palabra en el texto que se reconoce como una mención de un determinado tipo de entidad del sistema de tipos. Para las menciones de entidades que constan de más de una palabra, pulse otra palabra o arrastre los bordes del recuadro de selección para seleccionar varias palabras o palabras compuestas.
    1. Seleccione el tipo de entidad que desee aplicar desde el panel de la derecha, o escriba el atajo de teclado para el tipo de entidad.

        Si las directrices de anotación estaban conectadas anteriormente al espacio de trabajo, y desea ayudar con la selección de la anotación correcta que se aplicará, pulse **Ver directrices**. Dependiendo de la configuración de los permisos de acceso en el sitio donde se alojan las directrices, es posible que pueda actualizar las directrices tras abrirlas, por ejemplo, para añadir aclaraciones y ejemplos.
        {: tip}

    1. Evite crear menciones solapadas. Sin embargo, si se necesita una mención de superposición válida, pulse **Sustituir** para añadirla más fácilmente. Se produce un solapamiento al aplicar más de una etiqueta a una mención de entidad. Revise estas sugerencias:

        - Anote *Sub-Saharan* como una única mención, no solo *Saharan* ni solo *Sub*.
        - No cree una anotación `PERSON` solapada para la referencia *JFK* en *JFK International Airport*. Toda la mención *JFK International Airport* debería etiquetarse solo como una `FACILITY`.
        - Para el texto *CEOs*, no cree una anotación `PERSON` para *CEO* ni una anotación `PEOPLE` para *CEOs*. Anote *CEOs* solo como un tipo de entidad `PEOPLE`.

        Normalmente, la existencia de demasiadas menciones solapadas significa que las directrices de anotación son ambiguas y deben ser mejoradas para proporcionar mejores ejemplos de cómo manejar palabras compuestas en los datos de origen.

    1. Para eliminar una anotación que acaba de añadir, pulse Ctrl+Z para deshacer la acción. Para eliminar una mención de entidad más tarde, puede efectuar una pulsación con el botón izquierdo del ratón en una mención y pulsar la tecla Supr, o pulsar **Ver detalles** y, a continuación, pulsar **X** junto al tipo de entidad asignado a la mención.

1. Dependiendo del sistema de tipos, podría configurar atributos para una mención de entidad, como asignar un rol o un subtipo de entidad o una clase o tipo de mención. Si es así, seleccione una mención y pulse **Vista de atributos**.

1. Pulse **Guardar** en cualquier momento para guardar el trabajo.

### Qué hacer a continuación
{: #wks_haentity_next}

Después de terminar de anotar todas las menciones de entidades, las menciones de relaciones y las correferencias en el documento, según corresponda, cambie el estado del documento de **En curso** a **Completado**, pulse **Guardar**, y luego cierre el documento.

Después de terminar de anotar todos los documentos y de marcarlos como **Completados**, el estado del conjunto de anotaciones cambiará a **Enviado**. Así es como los gestores de proyectos saben que pueden empezar a evaluar los documentos para el acuerdo entre anotadores, rechazar o aceptar documentos y promocionarlos a datos de campo.

## Anotación de menciones repetidas
{: #wks_haconcordance}

Opcionalmente, puede utilizar la herramienta de concordancia para etiquetar varias apariciones de una mención a la vez. La herramienta le permite anotar el mismo texto con el mismo tipo de entidad en un documento y en conjuntos de anotaciones. Utilizar la herramienta ayuda a garantizar la coherencia en la anotación en varios documentos. Por ejemplo, puede etiquetar cada aparición de la mención *encryption* individualmente en modalidad de mención, o puede etiquetar todas las apariciones de la mención *encryption* utilizando la herramienta de concordancia. En cualquier caso, el modelo aprende del tipo de entidad que se aplique a la mención.

### Acerca de esta tarea
{: #wks_haconcordance_about}

Aunque la herramienta de concordancia es opcional, una práctica recomendada es utilizar la herramienta de concordancia para anotar menciones en un documento o en documentos antes de empezar a anotar menciones en documentos individuales. Cuando se aplica un tipo de entidad a una mención con la herramienta de concordancia, el sistema aplicará el tipo de entidad a todas las menciones coincidentes, sobrescribiendo los tipos de entidades existentes asignados a una mención coincidente. Para evitar conflictos, se eliminan los atributos (como roles o subtipos) de los tipos de entidades existentes cuando la herramienta de concordancia aplica un nuevo tipo de entidad.

### Procedimiento
{: #wks_haconcordance_procedure}

Para anotar menciones repetidas:

1. Inicie sesión como anotador humano (o como administrador o gestor de proyectos al que se ha asignado documentos para anotar). Se mostrarán los espacios de trabajo que contienen tareas que tiene asignadas.
1. Abra un espacio de trabajo y pulse **Modelo de aprendizaje automático** > **Tareas de anotación**. Se mostrarán las tareas de anotación que tiene asignadas.
1. Abra la tarea de anotación en la que desee trabajar. Se mostrarán los conjuntos de anotaciones que tiene asignados.
1. Pulse **Anotar** para abrir el conjunto de anotación en el que desee trabajar. Se mostrarán los documentos del conjunto de anotaciones.
1. Abra el documento que desee anotar. De forma predeterminada, el documento se en modalidad **Mención**, que es la modalidad que se utiliza para anotar menciones de entidades.
1. Si no ha añadido ninguna anotación todavía, añada al menos una anotación. Seleccione una palabra o una frase de palabras que represente una mención de un tipo de entidad desde el sistema de tipos, y asigne el tipo apropiado a la misma. Pulse **Guardar** para guardar la anotación.
1. Seleccione una sola aparición de texto repetido que desee anotar y, a continuación, pulse **Concordancia**.
1. Seleccione los documentos a los que desee aplicar el tipo de entidad seleccionado. Puede crear las anotaciones en todos los documentos que se han asignado para anotar, todos los documentos que ha comenzado a anotar, o todos los documentos que aún no se han empezado a anotar.
1. Pulse **Vista previa** para ver las anotaciones que se añadirán.

  Si desea ver las anotaciones en mayor contexto, pulse los iconos para previsualizar el contenido del documento o abrir el documento en una ventana nueva.

1. Pulse **Aplicar y revisar** para aplicar los tipos de entidades seleccionados a menciones de los documentos seleccionados. Aún tiene una oportunidad para revisar las anotaciones que se añadirán. Si una anotación es inexacta en un contexto particular, puede eliminar esa aparición pulsando el icono Editar, y luego eliminando la asignación de tipo de entidad para la mención.
1. Cuando esté satisfecho con la lista de anotaciones, pulse **Volver al editor de datos de campo**.

### Resultados
{: #wks_haconcordance_results}

Las menciones se anotan en el documento. No hay forma de eliminar el conjunto de menciones que haya añadido mediante la concordancia a la vez. Debe eliminar cada mención una por una.

## Anotación de menciones como correferencias
{: #wks_hacoref}

Para anotar menciones como correferencias en la misma entidad, un anotador humano selecciona cada aparición de una mención que hace referencia a lo mismo. La correferencia ayuda a un modelo a reconocer que las entidades a las que se hace referencia de formas distintas se asociarán con la misma entidad, como el nombre de un estado de EE.UU. y su abreviatura, el nombre de una empresa y su acrónimo, o el nombre y el pronombre de una persona que hace referencia a dicha persona.

### Antes de empezar
{: #wks_hacoref_prereqs}

Debe anotar menciones en el documento antes de poder identificar correferencias.

### Acerca de esta tarea
{: #wks_hacoref_about}

Al anotar menciones como correferencias, el sistema creará una cadena de correferencia. La cadena proporciona una forma de ver todas las menciones en contexto y verificar que todas las apariciones pertenecen a la misma entidad. Por ejemplo, "Barack", "Michelle", "he" y "she" son todas el mismo tipo de entidad, `PERSON`, pero "Barack" y "he" son una entidad, y "Michelle" y "she" son otra. En este ejemplo, creará dos cadenas de correferencia.

Al crear una cadena de correferencia, debe seleccionar menciones que haya marcado el mismo tipo de entidad. En algunos casos, sin embargo, es posible que desee incluir menciones de tipos distintos en la misma cadena de correferencia. Para ello, debe crear varias cadenas y luego fusionarlas. Por ejemplo, piense en cómo utilizan las personas las abreviaturas progresivamente para evitar repetir las cosas en el texto. En un informe de incidente de tráfico, la primera referencia a un vehículo podría ser "2004 Honda Accord Sedan". Posteriormente, el autor podría hacer referencia al vehículo como "Accord", y a continuación hacer referencia al vehículo simplemente como "vehicle". Si el sistema de tipos incluye entradas para el fabricante, el modelo y el tipo de vehículo, podría crear varias cadenas de correferencia por tipo de entidad, y luego fusionarlas para crear una cadena consolidada. La cadena fusionada ayuda a entrenar el modelo de aprendizaje automático para reconocer que todas estas menciones hacen referencia a lo mismo.

Otra forma de combinar menciones de distintos tipos de entidades es crear una cadena con menciones de un tipo de entidad. A continuación, puede pulsar una mención de otro tipo de entidad, y luego pulsar la cadena que ha creado para añadir la mención a dicha cadena.

Dependiendo de las directrices de anotaciones, es posible que desee crear cadenas de correferencia para verbos así como para nombres si los verbos mencionan la misma instancia de una acción. Por ejemplo, si dos menciones del verbo "encrypts" se refieren a la misma aparición de cifrado, puede correferenciar las menciones. Pero si una referencia a "encrypts" es una referencia general, o si las dos apariciones hacen referencia a dos actos de cifrado distintos, podría no correferenciarlos. Si dos verbos distintos hacen referencia a la misma aparición de una acción, podría desear hacer correferencia a las menciones. Por ejemplo, en la sentencia "He encrypted the document, and after that processing he sent the file ... ", las menciones "encrypted" y "processing" podrían ser correferenciadas porque hacen referencia a la misma instancia de una acción.

Lo más importante es la coherencia. Decida cómo desea anotar la correferencia y especificar las reglas, con ejemplos, claramente en las directrices de anotación.

### Procedimiento
{: #wks_hacoref_procedure}

Para anotar menciones como correferencias:

1. Inicie sesión como anotador humano (o como administrador o gestor de proyectos al que se ha asignado documentos para anotar). Se mostrarán los espacios de trabajo que contienen tareas que tiene asignadas.
1. Abra un espacio de trabajo y pulse **Modelo de aprendizaje automático** > **Tareas de anotación**. Se mostrarán las tareas de anotación que tiene asignadas.
1. Abra la tarea de anotación en la que desee trabajar. Se mostrarán los conjuntos de anotaciones que tiene asignados.
1. Pulse **Anotar** para abrir el conjunto de anotación en el que desee trabajar. Se mostrarán los documentos del conjunto de anotaciones.
1. Abra el documento que desee anotar. De forma predeterminada, el documento se en modalidad **Mención**, que es la modalidad que se utiliza para anotar menciones de entidades.
1. Pulse **Correferencias**.
1. Cree una cadena de correferencia:

    1. Muévase a través del documento y pulse cada mención que signifique lo mismo y que esté etiquetado por el mismo tipo de entidad. Por ejemplo, pulse cada aparición de `{{site.data.keyword.IBM_notm}}`, `International Business Machines` e `{{site.data.keyword.IBM_notm}} Corp.`, suponiendo que todas estas menciones tengan el tipo de entidad `ORGANIZATION`.
    1. Efectúe una doble pulsación en la última mención que desee añadir a la cadena. Se ha creado una cadena de correferencia en el panel lateral. El nombre de la cadena coincide con la primera mención que ha seleccionado.
    1. Para resaltar todas las menciones de una cadena para revisarlas en su contexto, pase el cursor por encima del nombre de la cadena en el panel lateral.

1. La **Lista de mención única** muestra términos en el documento que se han anotado, pero que no se han añadido a una cadena. Si observa una mención en la lista que pertenece a una cadena, puede añadirla a la cadena desde aquí.

    1. En la **Lista de mención única** del panel lateral, pulse la mención.
    1. En la lista desplegable por debajo de la descripción de la mención, elija el número que representa la cadena a la que desea añadir la mención.
    1. Pulse **Fusionar** para añadir la mención a la cadena, y luego pulse **Aceptar**.

    La mención se elimina de la **Lista de mención única** y el número de la cadena a la que pertenece ahora se muestra por debajo de la mención en el documento.

1. Puede deshacer el trabajo realizado mediante los métodos siguientes:

    - Para eliminar una cadena de correferencia que acaba de añadir, pulse Ctrl+Z para deshacer la acción.
    - Para eliminar una cadena de correferencias posteriormente, desde el panel lateral **Cadenas de correferencia**, pulse la **X** junto a la cadena que desee eliminar.
    - Para eliminar una única mención de la cadena, pulse el ID de correferencia para abrir una ventana que muestra una lista de las menciones de la cadena y, a continuación, pulse la **X** junto a la mención que desee eliminar.

1. Pulse **Guardar** en cualquier momento para guardar el trabajo.

### Qué hacer a continuación
{: #wks_hacoref_next}

Después de terminar de anotar todas las menciones de entidades, las menciones de relaciones y las correferencias en el documento, según corresponda, cambie el estado del documento de **En curso** a **Completado**, pulse **Guardar**, y luego cierre el documento.

Después de terminar de anotar todos los documentos y de marcarlos como **Completados**, el estado del conjunto de anotaciones cambiará a **Enviado**. Ese estado es la forma en la que los gestores de proyectos saben que pueden empezar a evaluar los documentos para el acuerdo entre anotadores, rechazarlos o aceptarlos y promocionarlos a datos de campo.

## Anotación de relaciones
{: #wks_harelation}

Para anotar menciones de relaciones, un anotador humano busca pruebas textuales de una relación entre dos menciones de entidades en una frase y, a continuación, aplica una etiqueta que describe de forma más apropiada el tipo de relación. Las etiquetas que se pueden aplicar son tipos de relaciones definidos en el sistema de tipos del espacio de trabajo.

### Antes de empezar

Debe anotar menciones de entidades en el documento antes de poder definir tipos de relaciones entre ellos.

### Acerca de esta tarea

La mención de relación solo puede definirse si el texto describe explícitamente la relación entre las dos menciones de entidades. Las pruebas textuales explícitas podrían incluir posesivos, estructuras sujeto-verbo-objeto o aposiciones. Por ejemplo, en la frase siguiente, no es válido añadir la mención de relación `ownedBy` entre `dog` y `owner`.

<pre><code>NOT VALID: The <u>dog</u> got a treat from its <u>owner</u>.</code></pre>

La mención de relación válida es entre `its` y `owner`, porque es esta parte de la frase en la que el texto define explícitamente la relación entre dog e its owner. `Owner` podría ser el propietario de una casa, o el dueño de algún otro perro, pero este texto deja claro que el mismo perro mencionado al principio de la frase es propiedad de esta persona.

<pre><code>VALID: The dog got a treat from <u>its</u> <u>owner</u>.</code></pre>

<pre><code>                                |ownedBy^</code></pre>

El requisito de que ambas menciones de entidades y el texto que define el tipo de relación entre ellas debe existir dentro de una única frase puede parecer estricto. Sin embargo, tenga en cuenta que, como en el ejemplo anterior, mientras también identifique correferencias en el documento, puede identificar menciones de relaciones en frases que contienen palabras que sirven como menciones de entidades más informales, como por ejemplo pronombres. Por ejemplo, la segunda frase de `Mary is a scientist. She works for {{site.data.keyword.IBM_notm}}.` contiene prueba textual válida de una relación `employedBy` entre Mary e {{site.data.keyword.IBM_notm}}. La correferencia, `She`, se entiende como una referencia al tipo de entidad `PERSON` `Mary`. Es la identificación de una correferencia entre `Mary` y `She` más la identificación de una mención de relación entre `She` e `{{site.data.keyword.IBM_notm}}` juntos que captura completamente esta relación. La manera correcta de anotar la mención de relación es como esta:

<pre><code>Mary[<i>#1</i>] is a scientist. <u>She</u>[<i>#1</i>] works for <u>IBM</u>.</code></pre>

<pre><code>                         |----employedBy----^</code></pre>

donde el subíndice [<i>#1</i>] indica que `Mary` y `She` son ambos miembros de la primera cadena de correferencia en el documento.

### Procedimiento

Para anotar menciones de relación entre menciones de entidad en un documento:

1. Inicie sesión como anotador humano (o como administrador o gestor de proyectos al que se ha asignado documentos para anotar). Se mostrarán los espacios de trabajo que contienen tareas que tiene asignadas.
1. Abra un espacio de trabajo y pulse **Modelo de aprendizaje automático** > **Tareas de anotación**. Se mostrarán las tareas de anotación que tiene asignadas.
1. Abra la tarea de anotación en la que desee trabajar. Se mostrarán los conjuntos de anotaciones que tiene asignados.
1. Pulse **Anotar** para abrir el conjunto de anotación en el que desee trabajar. Se mostrarán los documentos del conjunto de anotaciones.
1. Abra el documento que desee anotar. De forma predeterminada, el documento se en modalidad **Mención**, que es la modalidad que se utiliza para anotar menciones de entidades.
1. Pulse **Relaciones**.
1. Para anotar una relación:

    1. Pulse una mención de entidad en el texto y, a continuación, pulse una segunda mención de entidad en la misma frase que desee conectar a la primera mención.
    1. Seleccione el tipo de relación que desee aplicar desde el panel de la derecha, o escriba el atajo de teclado para el tipo de relación. La lista de tipos de relaciones disponibles está limitada por la primera mención de entidad que seleccione, y limitada por la segunda mención de entidad. En algunos casos, solo permanece un tipo de relación; todavía debe seleccionar explícitamente el tipo de relación a aplicar.

        Si las directrices de anotación estaban conectadas anteriormente al espacio de trabajo, y desea ayudar con la selección de la anotación correcta que se aplicará, pulse **Ver directrices**. Dependiendo de la configuración de los permisos de acceso en el sitio donde se alojan las directrices, es posible que pueda actualizar las directrices tras abrirlas, por ejemplo, para añadir aclaraciones y ejemplos.
        {: tip}

1. Para eliminar una mención de relación que acabe de añadir, pulse Ctrl+Z para deshacer la acción. Para eliminar una mención de relación más adelante, puede pulsar con el botón izquierdo del ratón el tipo de relación y a continuación pulsar la tecla **Supr** o pulsar **X** junto al tipo de relación.
1. Dependiendo del sistema de tipos, podría configurar atributos para una relación, como asignar a una relación tiempo, modalidad o clase. Si es así, seleccione una etiqueta de relación y pulse **Vista de atributos**.
1. Pulse **Guardar** en cualquier momento para guardar el trabajo.

### Qué hacer a continuación

Después de terminar de anotar todas las menciones de entidades, las menciones de relaciones y las correferencias en el documento, según corresponda, cambie el estado del documento de **En curso** a **Completado**, pulse **Guardar**, y luego cierre el documento.

Después de terminar de anotar todos los documentos y de marcarlos como **Completados**, el estado del conjunto de anotaciones cambiará a **Enviado**. Así es como los gestores de proyectos saben que pueden empezar a evaluar los documentos para el acuerdo entre anotadores, y rechazarlos o aceptarlos y promocionarlos a datos de campo.

## Información relacionada

[Creación de diccionarios](/docs/services/watson-knowledge-studio/dictionaries.html)

[Resolución de problemas del editor de datos de campo](/docs/services/watson-knowledge-studio/user-guide-help.html)

[Establecimiento de un sistema de tipos](/docs/services/watson-knowledge-studio/typesystem.html)
