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

Esta documentación es para {{site.data.keyword.knowledgestudiofull}} en {{site.data.keyword.cloud}}. Para ver la documentación para la versión anterior de {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.IBM_notm}} Marketplace, [pulse este enlace ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/services/knowledge-studio/typesystem.html){: new_window}.
{: tip}

# Establecimiento de un sistema de tipos
{: #typesystem}

El sistema de tipos controla cómo se puede anotar el contenido.
{: shortdesc}

## Sistemas de tipos
{: #wks_typesystem}

Un sistema de tipos define cosas que son interesantes en el contenido de dominio que desea etiquetar con una anotación. El sistema de tipos controla cómo se puede anotar el contenido definiendo los tipos de entidades que pueden ser etiquetados y cómo se pueden etiquetar las relaciones entre distintas entidades. El gestor de procesos de modelos normalmente trabaja con expertos en la materia
para el dominio para definir el sistema de tipos.

En {{site.data.keyword.knowledgestudioshort}}, puede crear un sistema de tipos desde cero o cargar un sistema de tipos existente. Para iniciar rápidamente un espacio de trabajo, podría desear cargar un sistema de tipos creado para un dominio similar. Entonces podrá editar el sistema de tipos para añadir o eliminar tipos de entidades o volver a definir los tipos de relaciones.

Se proporciona un sistema de tipos de ejemplo basado en el sistema de tipos *KLUE* para utilizarlo con las guías de aprendizaje de {{site.data.keyword.knowledgestudioshort}}. KLUE es la abreviatura de Knowledge from Language Understanding and Extraction y se deriva de {{site.data.keyword.IBM_notm}} Research basado en el análisis de recopilaciones de artículos de noticias. Puede descargar un sistema de tipos de KLUE de ejemplo desde <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/en-klue2-types.json" download>aquí<img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo" title="Icono de enlace externo" class="style-scope doc-content"></a>.

Muchos sectores, por ejemplo los dominios como la metalurgia, la geología, la investigación de mercados, las ciencias de la vida, los registros sanitarios electrónicos y la oncología publican diccionarios u ontologías de terminología específica del dominio. Considere la posibilidad de hacer referencia a este tipo de recurso para hacerse una idea de los tipos de entidades que desea definir en su propio sistema de tipos.

### Menciones
{: #wks_typesystem__wks_typesystemS2}

Una mención es cualquier parte de texto que considere relevante en los datos de dominio. Por ejemplo, en un sistema de tipos sobre vehículos automóviles, las apariciones de términos como `airbag`, `Ford Explorer`, y `sistema de retención infantil` podrían ser menciones relevantes.

### Tipos de entidades
{: #wks_typesystem__wks_typesystemS3}

Un tipo de entidad es cómo puede categorizar algo real. Una mención de entidad es un ejemplo de algo de ese tipo. Por ejemplo, la mención `President Obama` se puede anotar como un tipo de entidad `PERSON`. La mención `{{site.data.keyword.IBM_notm}}` se puede anotar como un tipo de entidad `ORGANIZATION`. Las entidades suelen ser nombres, pero también pueden ser verbos, siempre que el verbo sea importante para capturarse para fines de la aplicación que utilizará el sistema de tipos. Por ejemplo, `EVENT_CRASH` podría ser un tipo de entidad válido para un sistema de tipos sobre vehículos automóviles, por lo que la palabra `hit` en la frase `The car hit the barrier.` se puede anotar.

El objetivo del espacio de trabajo de la anotación es anotar cada mención en un documento con el tipo de cosa que es. Después de que una mención esté clasificada por tipo de entidad, el intervalo etiquetado de texto se conocerá como una entidad.

Un sistema de tipos que cree con {{site.data.keyword.knowledgestudioshort}} puede incluir los siguientes atributos de tipo de entidad. Los atributos ayudan a calificar menciones en el texto, pero no están marcados como tipos de entidades por un modelo de aprendizaje automático. Por ejemplo, si el tipo de entidad `ORGANIZATION` tiene un subtipo de entidad denominado `COMMERCIAL`, `COMMERCIAL` no se marcará como un tipo de entidad por sí mismo.

- **Rol**

    Califica la mención por el contexto en el que se produce la mención. Por ejemplo, la mención `France` en la afirmación `the students went to France` está marcada con el tipo de entidad `GPE` porque `France` es una entidad geopolítica. No obstante, dado que `France` en este contexto es también un destino para los estudiantes que han viajado, el tipo de entidad se cualifica añadiendo un atributo, en este caso el rol `LOCATION`. Otro ejemplo sería que la mención `Lawyers` se podría marcar con el tipo de entidad `PEOPLE` y también mediante el rol `OCCUPATION`.

- **Subtipo de entidad**

    Clasifica más el tipo de entidad. Por ejemplo, el tipo de entidad `ORGANIZATION` podría incluir los subtipos `COMMERCIAL`, `GOVERNMENT`, `MILITARY` y `EDUCATION`.

- **Tipo de mención**

    Califica la mención mediante determinadas categorías léxicas:
    - **NAM**: la mención es un nombre propio, como por ejemplo el nombre de una persona o el nombre de una organización.
    - **NOM**: la mención es nominal (un nombre común), como *company* o *president*.
    - **PRO**: la mención es un pronombre, como *he*, *we* o *it*.
    - **NONE**: ninguno de los otros tres tipos de menciones es aplicable.

- **Clase de mención**

    Califica la mención indicando si la mención es específica, genérica, o negada:
    - **SPC**: la mención es específica, y a menudo incluye la palabra *the* en inglés, como *the book* o *the hurricane occurred in September*. En estos ejemplos, las menciones *book* y *hurricane* se anotarían con el atributo **SPC**.
    - **GEN**: la mención es genérica, como *a book* o *hurricanes usually occur in the fall*. En estos ejemplos, las menciones *book* y *hurricanes* se anotarían con el atributo **GEN**.
    - **NEG**: la mención se niega, como las referencias a *no book*. Cuando entrene un modelo, el algoritmo puede aprender de los ejemplos negativos y positivos, por lo que es importante marcar menciones de ambos tipos.

### Tipos de relaciones
{: #wks_typesystem__wks_typesystemS4}

Un tipo de relación define una relación binaria y ordenada entre dos entidades. Para que exista una mención de relación, el texto debe definir explícitamente las menciones de relación y de enlace de las dos entidades juntas, y debe hacerlo dentro de una única frase. Por ejemplo, la frase `Mary works for {{site.data.keyword.IBM_notm}}` es una evidencia textual del tipo de relación `employedBy`.

Para algunos tipos de relaciones, el orden de las menciones de entidades importa. Por ejemplo, el tipo de relación `employedBy` permite que el tipo de entidad `PERSON` o `PEOPLE` sea la primera mención de la relación, y `ORGANIZATION` o **GPE** la segunda mención, pero no al contrario. `Mary` `employedBy` `{{site.data.keyword.IBM_notm}}` es una relación válida. `{{site.data.keyword.IBM_notm}}` `employedBy` `Mary` no lo es. Para algunos tipos de relaciones, como `spouseOf`, `colleague` o `sibling`, el orden no importa. Al definir un tipo de relación donde el orden no es importante, una práctica recomendada es añadir información a las directrices de anotación para regularizar cómo se utiliza el tipo de relación. Una convención para anotar tales relaciones simétricas es decir que la mención de entidad que se da en primer lugar en el texto debería ser la primera en la relación.

**Conceptos relacionados**:

[Carga de recursos desde otro espacio de trabajo](/docs/services/watson-knowledge-studio/exportimport.html)

## Adición de un sistema de tipos al espacio de trabajo
{: #wks_projtypesys}

Debe crear o cargar un sistema de tipos antes de empezar cualquier tarea de anotación.

### Acerca de esta tarea

Se aplican las siguientes reglas de denominación a las entradas de sistema de tipos:

- Los nombres no pueden contener espacios.
- Utilice solo los siguientes caracteres ASCII alfanuméricos y el carácter de subrayado en valores que añada al sistema de tipos: de `A` a `Z`, de `a` a `z`, de `0` a `9`.
- El primer carácter de una entidad o de un nombre de tipo de relación debe ser alfabético.
- Los nombres de tipos de entidades no pueden tener más de 64 caracteres.
- Los nombres de tipos de relaciones no pueden tener más de 128 caracteres.

Por convención, los nombres de tipos de entidades están especificados en caracteres en mayúscula (`ORGANIZATION`) y los nombres de tipos de relaciones están especificados en bicapitalización (`employedBy`). Pero esta convención es opcional.

### Procedimiento

1. Inicie sesión como un administrador o gestor de proyectos de {{site.data.keyword.knowledgestudioshort}} y abra la página **Activos**> **Tipos de entidades**.
1. Elija uno de los métodos siguientes para crear un sistema de tipos:

    - Cargue un sistema de tipos existente:

        1. En el separador **Tipos de entidades**, pulse **Cargar**.

            Si ha descargado previamente un sistema de tipos desde un espacio de trabajo de {{site.data.keyword.knowledgestudioshort}}, el sistema de tipos se descargará en formato `JSON`. Puede cargar este sistema de tipos para iniciar rápidamente la creación de un espacio de trabajo. Para obtener detalles, consulte [Cargar recursos desde otro espacio de trabajo](/docs/services/watson-knowledge-studio/exportimport.html).

            > **Nota:** Independientemente del origen del sistema de tipos, las entradas del mismo deben cumplir las reglas de denominación listadas anteriormente.

        1. Añada, edite y suprima tipos de entidades y tipos de relaciones de la misma forma en que lo hace al crear un sistema de tipos desde cero.

    - Cree un sistema de tipos desde cero:

        1. En el separador **Tipos de entidades**, pulse **Añadir tipo de entidad**.
        1. Especifique un nombre de tipo de entidad descriptivo, teniendo en cuenta que el tipo de entidad es una etiqueta para anotar partes de texto importantes (menciones) en el contenido del dominio. Mantenga el nombre abreviado y representativo, para que los anotadores humanos lo puedan recordar fácilmente.

            También puede definir opcionalmente roles y subtipos para el tipo de entidad:
            - Un rol ayuda a cualificar el tipo de entidad en el contexto en el que se produce la mención. Por ejemplo, la mención `Software Engineer` podría etiquetarse con el tipo de entidad `PEOPLE` y, en este contexto, mediante el rol `OCCUPATION`. Consulte [Cuándo definir roles](/docs/services/watson-knowledge-studio/typesystem.html#wks_typesystem_roles) para obtener más información.
            - Un subtipo ayuda a clasificar más el tipo de entidad. Por ejemplo, el tipo de entidad `GOVERNMENT` puede tener los subtipos `MILITARY` y `CIVILIAN`.

            > **Nota:** Al definir un rol o un subtipo para una entidad, estará dando más opciones a la persona que asociará la información de tipos a menciones en el momento de la anotación. El anotador humano puede aplicar una anotación que especifique solo el tipo de entidad, o el tipo de entidad más el rol o subtipo que esté definiendo ahora.

            Intente definir suficientes tipos de entidades para capturar los conceptos clave que desee anotar, pero no tantos tipos de entidades que sea engorroso para que los anotadores humanos apliquen las etiquetas con precisión.

        1. Pulse **Clases de menciones** y **Tipos de menciones** para ver las clases de menciones y los tipos de menciones predeterminados. No se pueden editar estos valores.

            El objetivo de un atributo es ayudar a etiquetar cada mención mediante el tipo de cosa que es. Un tipo de mención indica si la mención es un nombre, nominal, o pronombre, y una clase de mención indica si la mención es específica, genérica o negada.

        1. Abra la página **Activos**> **Tipos de relaciones** y especifique cómo se pueden relacionar dos menciones entre sí.

            El orden entre la primera y la segunda entidad en un tipo de relación es normalmente relevante. Por ejemplo, una entidad `PERSON` puede ser un empleado de una entidad `ORGANIZATION` o una entidad geopolítica (**GPE**), como por ejemplo `Mary` `employedBy` `{{site.data.keyword.IBM_notm}}`, pero las organizaciones y las entidades geopolíticas no pueden ser empleadas de una persona. Cuando un anotador humano pulsa una entidad en el editor de datos de campo, la lista de tipos de relaciones disponibles se controla mediante lo definido en el sistema de tipos.

            No defina los atributos de relación. No los utiliza el modelo de aprendizaje automático. El modelo solo utiliza el tipo de relación y el orden, e ignora los atributos de relación.

        1. Utilice los iconos **Editar** y **Suprimir** para modificar los tipos de entidades y sus tipos de relaciones asociados, o para suprimir un tipo de entidad o un tipo de relación desde el sistema de tipos.

            Si suprime una entidad que se utiliza en una definición de tipo de relación, esta última también se suprimirá.

**Tareas relacionadas**:

[Modificación de un sistema de tipos sin perder anotaciones humanas](/docs/services/watson-knowledge-studio/improve-ml.html#wks_projtypesysmod)

## Directrices de creación del sistema de tipos
{: #wks_typesys_guidelines}

La finalidad de cualquier sistema de tipos en {{site.data.keyword.knowledgestudioshort}} es definir cómo se pueden anotar partes de texto. Si elige crear un sistema de tipos desde cero, siga estas directrices.

Céntrese en crear un inventario de tipos de entidades y tipos de relaciones que cubran la información que necesita la aplicación en la que se utilizará el sistema de tipos. No cubra cosas que no sean necesarias. No divida tipos ni realice distinciones no necesarias por la aplicación. Por ejemplo, si el documento fuente contiene la frase `Murder on the Orient Express made headlines`, la forma en que defina los tipos de entidades para capturar la información clave en la frase difiere en función del tipo de aplicación que utilizará el modelo que cree con el sistema de tipos.

- Para una aplicación literaria, puede crear tipos que capturen esta información:

    ```
               [NOVEL][CRITICAL_RECEPTION]
    ```
    {: screen}

    ```
    [Murder on the Orient Express][made headlines]
    ```
    {: screen}

- Para una aplicación de seguridad pública, puede crear estos tipos:

    ```
    [EVENT_CRIME][LOCATION]
    ```
    {: screen}

    ```
      [Murder] on the [Orient Express] made headlines
    ```
    {: screen}

La estructura es a menudo impulsada por las características de los documentos desde los que se extrae información, pero siempre debe ser moderada por la información que la aplicación realmente utilizará de esos documentos. Por ejemplo, puede crear una aplicación que tiene seguimiento de registros médicos. Para crear el sistema de tipos, empiece a buscar en registros de pacientes para ver qué tipos de información se deben capturar. Los registros de pacientes podrían contener un campo que describe lo que el paciente comió para almorzar. Sin embargo, si la aplicación no va a utilizar esa información, no la añada al sistema de tipos. Y al tomar la decisión de hacer esta omisión, reconozca que esto significa que las secciones de los documentos de registro del paciente se dejarán sin anotar. Esto es correcto y es lo que se espera.

Las menciones anotan una parte de texto; no sustituyen el texto. Un sistema de tipos no es una ontología para un dominio. Se espera tener tipos de entidades generales como `MEDICATION_NAME` en lugar de tener un tipo de entidad para cada tipo de medicina. El texto del documento seguirá conteniendo el nombre de medicina específico. Simplemente se reforzará con una anotación que identifica su tipo, lo que hace más fácil encontrar y extraer la información mediante programación.

Al empezar, defina de 10 a 40 tipos de entidades y de relaciones. Quédese en el extremo inferior del rango si los anotadores humanos que trabajarán en el espacio de trabajo no están muy especializados en el campo. No defina más de 50.

Piense en pasar una gran cantidad de tiempo definiendo el sistema de tipos antes de que el equipo empiece cualquier tarea de anotación humana. Cuando el equipo empiece a anotar documentos, empiece con un conjunto pequeño, quizá de no más de 50. Anote solo menciones de forma inicial, examine los resultados y refine las directrices de anotación y el sistema de tipos según sea necesario. Cuando esté satisfecho con los resultados de la anotación de mención, siga anotando relaciones y correferencias.

Aunque el trabajo fundamental está en marcha para definir un conjunto de tipos de entidades y de directrices de mención-anotación, evite poner mucho esfuerzo en las menciones de relaciones de anotación. Los cambios de menciones desharán el trabajo de anotaciones de relación. Tómese un tiempo para definir un conjunto de tipos de relaciones y sus pares de tipos de entidades permitidos para que se tengan en cuenta las necesidades de tipos de relaciones antes de que el inventario de los tipos de entidades finalice.

Espere que el sistema de tipos evolucione con la experiencia de personas que intentan anotar en él. Si revisa el sistema de tipos después de crear tareas de anotación humana, debe decidir si se aplicarán los cambios a cada tarea. Si aplica los cambios, los anotadores humanos tendrán que revisar los documentos que anotaron previamente.

Cuando pruebe el modelo, puede revisar estadísticas que muestran con cuánta frecuencia se producen los tipos de entidades y los tipos de relaciones en los documentos de ejemplo. Asegúrese de revisar estas estadísticas. Para asegurarse de que la aplicación recibe contexto suficiente para anotar con precisión grandes colecciones de documentos, los datos de prueba deben incluir un gran muestreo de los tipos de entidades y de los tipos de relaciones más importantes.

> **Importante:** Después de entrenar el primer modelo, es probable que necesite realizar modificaciones basadas en las estadísticas de rendimiento. Sin embargo, para crear un modelo estadístico fiable para la anotación automática, deseará que el sistema de tipos esté lo más cerca posible al final como sea posible antes de empezar tareas de anotación a gran escala.

## Cuándo definir roles
{: #wks_typesystem_roles}

El uso de roles le permite definir tipos de entidades más precisos.

Cada entidad que añada tiene un rol. A menos que lo cambie, el nombre de rol es el mismo que el nombre de entidad. Puede optar por definir un rol diferente para una entidad para capturar un uso más matizado de la mención. La palabra o frase a la que se aplica el rol es literalmente un ejemplo de un tipo de entidad, pero en la frase tiene el rol de otro tipo de entidad. Por ejemplo, en la frase `the White House vetoed the bill`, se puede capturar más precisamente el significado de `the White House` si se anota el tipo de entidad de `FACILITY` y un rol de `ORGANIZATION` o `PERSON`. White House es un edificio (`FACILITY`), pero representa al gobierno (`ORGANIZATION`) o al Presidente de los Estados Unidos (`PERSON`) en esta construcción. El tipo de entidad más la etiqueta de rol crean una clasificación más precisa de la mención del texto.

Los roles también pueden proporcionarle una forma de capturar la información de relación sin basarse en el uso de las menciones solapadas. Por ejemplo, puede que desee anotar el texto `31-year-old male` de forma que capture la idea de que esta es una referencia a una persona con el atributo edad de 31 años y el atributo género de hombre. Al examinar el texto, se determina que `31-year-old` es una edad, `male` es un género, y juntos significan una persona. Está tratando con 3 tipos de entidades, básicamente: `AGE`, `GENDER` y `PERSON`. Un enfoque para representar esto podría ser anotar `31-year-old` como `AGE`, `male` como `GENDER` y, dado que falta la mención aparte de una `PERSON`, pero `male` viene a representar a una persona, la palabra `male` puede tener un rol de `PERSON`. A continuación, puede capturar las relaciones entre el rol `PERSON` y todos los atributos de una persona que desee capturar. Por ejemplo, puede definir una relación `hasAttribute` entre el rol `PERSON` y la mención `AGE`. Dado que ha aplicado tanto un tipo de entidad `GENDER` como una etiqueta de tipo de rol `PERSON` a la misma palabra `male`, no puede definir una relación `hasAttribute` entre los dos. Sin embargo, el hecho de que dos etiquetas se apliquen a la misma mención las asocia entre sí. Esta asociación es considerada por el modelo de aprendizaje automático sin tener que definir un tipo de relación hasAttribute para llamar la relación explícitamente.

Un ejemplo similar es cuando se utiliza la frase `2008 Ford F-150` como abreviatura para `2008 Ford F-150 truck`. Aquí, `2008` se anota como un tipo de entidad `MODEL_YEAR`, `Ford` se anota como un tipo de entidad `MANUFACTURER` y a `F-150` se le da un tipo de entidad `MODEL`. Pero cuando falta la palabra `truck`, `F-150` también representa un vehículo. Decir `the F-150` es como decir `the truck`. Puede capturar tal uso añadiendo un rol `VEHICLE` a la mención además de su tipo de entidad `MODEL`. A continuación, puede definir las relaciones `hasAttribute` entre el rol `VEHICLE` y las menciones de entidades `MANUFACTURER` y `MODEL_YEAR`.

### ¿En qué se diferencian los roles de los subtipos?

Los subtipos de entidades son para estratificar un inventario de tipos de entidades en una jerarquía. Por ejemplo, si piensa distinguir 40 cosas, pero se agrupan de forma lógica en 10 conjuntos de 4 (`VITALSIGN_BLOODPRESSURE`, `VITALSIGN_HEARTRATE`, `MEDICATION_DOSAGE`, `MEDICATION_FREQUENCY`), podría estructurarlas en tipos y subtipos, lo que produce más menús compactos, pero añade un nivel de profundidad y de matización en el proceso de etiquetado. Para los fines de extracción de información, hay una combinación de tipos y subtipos intercambiable con muchísimos tipos sin subtipos. Por el contrario, la palabra o frase a la que se aplica un rol es un ejemplo de un tipo de entidad, pero que desempeña el rol de otro tipo de entidad, y uno que no es un subtipo del otro.

### ¿Cómo se tratan los roles?

El modelo de aprendizaje automático de {{site.data.keyword.knowledgestudioshort}} define etiquetas de clasificador para cada mención de una entidad que se encuentra en los documentos fuente concatenando el tipo de entidad y los valores del rol. Cuando se proporcionen valores de rol, cree etiquetas más precisas. Cada grupo de instancias de un tipo de etiqueta que se encuentra en los datos de entrenamiento forma un conjunto de menciones más uniforme. El reto es que, al seleccionar ser más preciso, también debe acceder al suministro de más datos de entrenamiento para asegurarse de que el modelo funciona bien. Pero, cuantos más datos de entrenamiento proporcione, mejor será el modelo. Por lo tanto, si no le importa hacer anotaciones adicionales, utilizar roles le da mejores resultados.

Como ejemplo, vamos a suponer que las sentencias siguientes se producen en un documento fuente, y que deseamos capturar `Acme` (donde `Acme` es un fabricante de camiones muy conocido), `sedan` y `truck` como entidades similares porque todas hacen referencia a un vehículo físico:

- a) `The Acme crashed into the concrete barrier.`
- b) `The sedan crashed into the concrete barrier.`
- c) `The Acme A-160 truck crashed into the concrete barrier.`

Puede manejar el diseño del sistema de tipos de dos formas:

1. Defina dos tipos de entidades: `MANUFACTURER` y `VEHICLE`. Para la entidad `MANUFACTURER`, defina un rol `VEHICLE` que se puede utilizar además del rol predeterminado `MANUFACTURER`.

    Al utilizar este sistema de tipos, las frases se anotarán de la forma siguiente:
    - a) `Acme` se anota como una entidad `MANUFACTURER`, pero con un rol de `VEHICLE`, ya que hace referencia a un vehículo real. Por lo tanto, su etiqueta interna es `MANUFACTURER-VEHICLE`.
    - b) `sedan` se anota como tipo de entidad `VEHICLE`. Se le asigna automáticamente el rol `VEHICLE`, ya que no hay ningún otro rol definido.
    - c) `Acme` se anota como tipo de entidad `MANUFACTURER` y `truck` se anota como tipo de entidad `VEHICLE`. No hay roles asignados, por lo que se utilizan los roles predeterminados.

1. Defina dos tipos de entidades solo sin roles: `MANUFACTURER` y `VEHICLE`.

    Al utilizar este sistema de tipos, las frases se anotarán de la forma siguiente:
    - a) `Acme` se anota como tipo de entidad `VEHICLE`.
    - b) `sedan` se anota como tipo de entidad `VEHICLE`.
    - c) `Acme` se anota como tipo de entidad `MANUFACTURER` y `truck` se anota como tipo de entidad `VEHICLE`.

¿Cómo funcionan los dos sistemas de tipos distintos? Presupongamos que los anotadores humanos han anotado un conjunto de documentos. Después de pasar la anotación, se identifican los siguientes sucesos de entrenamiento, que son entidades manualmente etiquetadas, en el corpus de entrenamiento:

- **Sistema de tipos 1**

    ```
    MANUFACTURER-MANUFACTURER 800 events
    MANUFACTURER-VEHICLE 200 events
    VEHICLE-VEHICLE 400 events
    ```
    {: screen}

- **Sistema de tipos 2**

    ```
    MANUFACTURER 800 events
    VEHICLE 200 + 400 = 600 events
    ```
    {: screen}

Cuando el modelo procesa nuevos documentos, es probable que `Acme` se etiquete como `MANUFACTURER` la mayoría del tiempo porque la ortografía de una palabra es una característica fuerte y la palabra `Acme` se definirá con probabilidad en el diccionario `MANUFACTURER`. Haría falta mucho contexto para etiquetarla de forma distinta. Si se utiliza el sistema de tipos 1, solo hay 200 sucesos de entrenamiento `MANUFACTURER-VEHICLE`, lo que es una desventaja en comparación con los 600 sucesos de `VEHICLE` en el sistema de tipos 2. Sin embargo, los clústeres de sucesos de entrenamiento del sistema de tipos 1 son todos bastante uniformes, lo que lleva a un mejor rendimiento. Para el sistema de tipos 2, el conjunto de 600 sucesos de entrenamiento para `VEHICLE` se compone en realidad de dos clústeres bastante disyuntivos: uno contiene los nombres del fabricante que hacen referencia a los vehículos reales, como `Acme` y `Ford`, y el resto contiene tipos de vehículos, como `sedan`, `SUV` y `truck`. De forma intuitiva, cada uno de estos dos clústeres son uniformes, pero mezclarlos diluye el clúster de entrenamiento y presenta un problema más difícil de resolver. Si sigue haciendo anotaciones y añadiendo más sucesos de entrenamiento, el rendimiento del sistema de tipos 1 sigue mejorando, mientras que el problema de resolver dos clústeres disyuntivos que obtenga con el sistema de tipos 2 no mejora con más entrenamiento.
