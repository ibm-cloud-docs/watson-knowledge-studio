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

Esta documentación es para {{site.data.keyword.knowledgestudiofull}} en {{site.data.keyword.cloud}}. Para ver la documentación para la versión anterior de {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.IBM_notm}} Marketplace, [pulse este enlace ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/services/knowledge-studio/build-groundtruth.html){: new_window}.
{: tip}

# Creación de los datos de campo
{: #build-groundtruth}

El objetivo del proyecto de anotación es obtener datos de campo, la recopilación de datos evaluados que se utiliza para adaptar {{site.data.keyword.watson}} a un dominio concreto. En {{site.data.keyword.knowledgestudioshort}}, los anotadores humanos, que son normalmente expertos en la materia del dominio de destino, desempeñan un papel importante a la hora de determinar los datos de campo.
{: shortdesc}

Un flujo de trabajo típico incluye los pasos siguientes:

1. Los anotadores humanos envían documentos anotados para su revisión.
1. El gestor de proyectos (que puede ser un experto de dominio antiguo) revisa la exactitud de su trabajo y compara la coherencia con que los anotadores humanos han anotado documentos que se solapan entre los conjuntos de anotaciones.
1. Si la puntuación del acuerdo entre anotadores es demasiado bajo, el gestor de proyectos rechazará el conjunto de anotaciones y lo devolverá a los anotadores humanos para que lo mejoren. Cuando se rechaza un conjunto de anotaciones, todos los documentos del conjunto se colocarán de nuevo en modo editable.
1. Si el gestor de proyectos aprueba un conjunto de anotaciones, los documentos que no se solapen entre conjuntos de anotaciones serán promocionados a datos de campo para que las anotaciones se puedan utilizar para entrenar el modelo.
1. El gestor de proyectos revisa los documentos que se solapan y resuelve los conflictos de anotaciones. En esta etapa, conocida como adjudicación, el equipo podría revisar las directrices de anotación para ayudar a aclarar malentendidos que hicieron que los distintos anotadores humanos anotaran el texto de forma incorrecta o incoherente.

    En algunos casos, un gestor de proyectos podría desear un porcentaje mayor de solapamiento para evaluar el acuerdo entre anotadores que diferencia el porcentaje de solapamiento para la adjudicación. Por ejemplo, si el acuerdo entre anotadores es correcto, el gestor de proyectos podría decidir que estaría bien promocionar cualquier anotación a datos de campo.

1. A medida que el gestor de proyectos resuelva los conflictos de anotación, las anotaciones aprobadas se promocionarán a datos de campo.

Tenga en cuenta que la anotación humana siempre necesita decisiones. Las directrices de anotación pueden hacer mucho para asegurarse de que el texto esté anotado de forma correcta y coherente, pero incluso las mejores directrices están abiertas a interpretación por parte de los humanos. Para obtener datos de campo, querrá pasar tiempo entrenando y educando anotadores humanos para que puedan tomar las mejores decisiones al analizar el contenido de dominio.

## Acuerdo entre anotadores
{: #wks_haiaa}

Una vez que los anotadores humanos hayan anotado los documentos, debe determinar qué documentos promocionará a datos de campo. Empiece revisando las puntuaciones del acuerdo entre anotadores. Los documentos con puntuaciones bajas son candidatos a ser rechazados y devueltos al anotador humano para su mejora.

Al calcular las puntuaciones del acuerdo entre anotadores, el sistema examinará todos los documentos que se solapan en todos los conjuntos de anotaciones de la tarea, independientemente del estado de los conjuntos. Dado que no puede aceptar ni rechazar conjuntos de anotaciones hasta que estén en el estado Enviado, puede que no desee evaluar el acuerdo entre anotadores hasta que se envíen todos los conjuntos de anotaciones, o puede desear limitar la revisión a solo los anotadores humanos que han enviado sus conjuntos de anotaciones completados.

Las puntuaciones del acuerdo entre anotadores muestra cómo han anotado menciones, relaciones y cadenas de correferencia distintos anotadores humanos. Puede ver las puntuaciones comparando un par de anotadores humanos (por ejemplo, compare todas las anotaciones de mención de John con todas las anotaciones de mención de Mary). También puede ver las puntuaciones comparando documentos específicos (por ejemplo, compare las anotaciones de relación que ha hecho John en un documento con las anotaciones de relación que ha hecho Mary en el mismo documento).

Para ayudarle a identificar áreas que necesitan investigación, las puntuaciones que están por debajo del valor que ha especificado para el umbral de acuerdo entre anotadores se resaltan en rojo. En las etapas iniciales de su proyecto de anotación, puede que encuentre que las puntuaciones de relación son con frecuencia peores que las puntuaciones de mención debido a que una anotación de relación perfecta requiere que las menciones que definen las relaciones estén en acuerdo en primer lugar.

La puntuación de la columna **Todos** es una *puntuación Fleiss Kappa*. Representa la coherencia con que varios anotadores humanos han aplicado la misma anotación en todos los documentos que se solapan en la tarea. El valor, que puede llegar hasta 1 e incluso ser negativo, puede ayudarle a identificar los puntos débiles de las directrices de anotación o de anotadores humanos particulares. Las directrices siguientes (*Landis and Koch, 1977*) proporcionan un punto de partida para evaluar el rendimiento general.

<table style="width:60%" summary="Esta tabla proporciona directrices generales entre anotadores para evaluar el rendimiento general.">
  <caption>Tabla 1. Directrices entre anotadores</caption>
  <tr>
    <th style="vertical-align:bottom; text-align:center" id="d12741e148">Puntuación</th>
    <th style="vertical-align:bottom; text-align:center" id="d12741e150">Nivel de acuerdo</th>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:center" headers="d12741e148">&lt; 0</td>
    <td style="vertical-align:top; text-align:center" headers="d12741e150">Deficiente</td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:center" headers="d12741e148">0,01 - 0,20</td>
    <td style="vertical-align:top; text-align:center" headers="d12741e150">Ligero</td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:center" headers="d12741e148">0,21 - 0,40</td>
    <td style="vertical-align:top; text-align:center" headers="d12741e150">Normal</td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:center" headers="d12741e148">0,41 - 0,60</td>
    <td style="vertical-align:top; text-align:center" headers="d12741e150">Moderado</td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:center" headers="d12741e148">0,61 - 0,80</td>
    <td style="vertical-align:top; text-align:center" headers="d12741e150">Sustancial</td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:center" headers="d12741e148">0,81 - 1,0</td>
    <td style="vertical-align:top; text-align:center" headers="d12741e150">Perfecto</td>
  </tr>
</table>

La puntuación en el resto de las columnas es una *medida F1*. Representa el nivel de coherencia de anotación entre un par de anotadores humanos. El valor puede oscilar entre 0 y 1, donde el acuerdo perfecto está indicado por la puntuación 1. Lo que constituye un nivel aceptable de acuerdo depende de los datos de dominio y del sistema de tipos. Pero para proporcionar un ejemplo, aquí están los umbrales de F1 que los gestores de proyectos esperan cumplir o superar en proyectos basados en el sistema de tipos KLUE:

- Menciones con tipos de entidades: 0,85
- Relaciones: 0,8
- Cadenas de correferencia: 0,9

La interpretación de las puntuaciones depende de la complejidad del sistema de tipos, la cantidad y la complejidad del contenido anotado, la experiencia que tengan los anotadores humanos, y otros factores. Por ejemplo, si la tarea de anotación se centra en el etiquetado de partes de habla, puede esperar ver una puntuación alta debido a cómo de definidas están las partes de habla. Pero una tarea que necesite un análisis más profundo del texto, donde se necesite interpretación humana, podría mostrar puntuaciones más bajas hasta que realice los pasos para aclarar las causas de la ambigüedad.

Generalmente, un sistema de tipos que incluya muchos tipos de entidades y tipos de relaciones está abierto a más interpretación, por lo que el acuerdo entre anotadores podría ser menor durante las fases iniciales del desarrollo del modelo. Mirando las puntuaciones, puede ver qué tipos de entidades, por ejemplo, tienen puntuaciones bajas. Estas puntuaciones bajas son un indicador de que las directrices de anotación deben mejorarse. Mirando las puntuaciones entre pares de anotadores humanos, puede identificar si un anotador particular muestra de forma coherente puntuaciones inferiores que el resto. Este anotador podría tener problemas para entender las directrices o para utilizar las herramientas de anotación, y por lo tanto es un candidato para formación adicional.

## Revisión de puntuaciones de acuerdo entre anotadores
{: #wks_haaccuracy}

Al determinar qué documentos se promocionarán a datos de campo, debe revisar las puntuaciones de acuerdo entre anotadores. Los documentos con puntuaciones bajas son candidatos a ser rechazados y devueltos al anotador humano para su mejora.

### Acerca de esta tarea
{: #wks_haaccuracy_about}

Cuando examine el acuerdo entre anotadores, examine los documentos anotados por más de un anotador humano. Si un documento no se comparte entre varios conjuntos de anotaciones y los anotadores humanos, no habrá acuerdo entre anotadores para calcular. Al añadir conjuntos de anotaciones a una tarea, asegúrese de que los conjuntos que desea comparar contengan los mismos documentos que se solapan. Puede ver qué documentos se encuentran en un conjunto de anotaciones abriendo la página **Activos**> **Documentos**, pulsando el separador **Conjuntos de anotaciones** y, a continuación, pulsando los nombres de los conjuntos.

Puede experimentar situaciones en las que no se solapan los documentos. Esto puede ocurrir, por ejemplo, si crea conjuntos de anotaciones en dos fases y los añade a la misma tarea. Aunque los conjuntos de anotaciones se crearan alrededor del mismo momento, no tienen ningún documento en común. Para otro ejemplo, si crea conjuntos de anotaciones con documentos que se solapan, pero añade un conjunto de anotaciones por tarea en lugar de añadir todos los conjuntos de anotaciones a una única tarea, no se encontrarán documentos que se solapen y no se podrá calcular el acuerdo entre anotadores.

### Procedimiento
{: #wks_haaccuracy_procedure}

Para evaluar el acuerdo de anotación entre los anotadores humanos:

1. Inicie sesión como un administrador o gestor de proyectos de {{site.data.keyword.knowledgestudioshort}}, y seleccione su espacio de trabajo.
1. Seleccione la página **Modelo de aprendizaje automático** > **Tareas de anotación** y abra la tarea que desee evaluar.
1. Pulse **Calcular acuerdo entre anotadores**. La vista predeterminada muestra las puntuaciones de acuerdo para ver con cuánta coherencia han anotado menciones los pares de anotadores humanos. La fila de la parte superior muestra la coherencia global entre cada par de anotadores, y la tabla siguiente muestra con cuánta coherencia ha etiquetado un par de anotadores menciones específicas en el texto.
1. Para explorar la coherencia con que los pares de anotadores humanos han anotado relaciones y correferencias, seleccione **Relación** o **Correferencia** desde el primer menú.
1. Para explorar la coherencia con que un par de anotadores humanos han anotado entidades, relaciones o correferencias en documentos solapados específicos, seleccione **Documento** en el segundo menú y, a continuación, seleccione el par de anotadores que desea evaluar.
1. Después de revisar los resultados, puede decidir si desea aprobar o rechazar conjuntos de anotaciones que se encuentran en el estado Enviado. Una vez que un conjunto de anotaciones se haya enviado, se mostrará un recuadro de selección junto a su nombre. Lleve a cabo una de estas acciones:

    - Si las puntuaciones del acuerdo entre anotadores son aceptables para un conjunto de anotaciones, seleccione el recuadro de selección y pulse **Aceptar**. Los documentos que no se solapan con otros conjuntos de anotaciones se promocionan a datos de campo. Los documentos que se solapan deben en primer lugar ser revisados mediante adjudicación para que los conflictos se puedan resolver.
    - Si las puntuaciones del acuerdo entre anotadores no son aceptables para un conjunto de anotaciones, seleccione el recuadro de selección y pulse **Rechazar**. El conjunto de anotaciones necesita ser revisado por el anotador humano para mejorar las anotaciones.

## Adjudicación
{: #wks_haperform}

Si varios anotadores humanos trabajan en el mismo documento, probablemente deseará incoherencias entre las anotaciones antes de promocionar las anotaciones a datos de campo. Este proceso de resolución de conflictos se conoce como adjudicación.

Al aprobar los conjuntos de anotaciones enviados por anotadores humanos, los documentos que no se solapan entre los conjuntos de anotaciones se promocionan a datos de campo. Antes de promocionar documentos que se solapan, debe comprobar las anotaciones en busca de conflictos. Cuando encuentre instancias de desacuerdo, debe decidir cómo resolver el conflicto, ya sea seleccionando la anotación correcta de las aplicadas por los anotadores humanos o seleccionando una anotación distinta a aplicar.

Un documento está disponible para la adjudicación cuando al menos una de las siguientes condiciones sea verdadera:

- El gestor de proyectos aprueba dos o más conjuntos de anotaciones en una tarea al mismo tiempo, y el mismo documento existe en al menos dos de los conjuntos de anotaciones (un documento que se solapa).
- El gestor de proyectos aprueba otro conjunto de anotaciones antes de que se adjudiquen los documentos de los conjuntos de anotaciones previamente aprobados. Si adjudica un documento que se solapa entre un conjunto de anotaciones A y un conjunto de anotaciones B, promocione las anotaciones a datos de campo, y luego apruebe otro conjunto de anotaciones, C, que tenga el mismo documento, las anotaciones en el documento recién aprobado se promocionan automáticamente a datos de campo porque ya no existen conflictos. Tenga en cuenta que las anotaciones promocionadas en el conjunto de anotaciones C sustituyen los datos de campo establecidos al adjudicar los documentos que se solapan en los conjuntos de anotaciones A y B. Si aprueba el conjunto de anotaciones C antes de promocionar las anotaciones en el conjunto de anotaciones A y B, los documentos que se solapan en el conjunto C se pueden comprobar en busca de conflictos y se pueden adjudicar.

La cantidad de tiempo que pasa adjudicando podría reducirse con el tiempo si se toma unos instantes para mejorar las directrices de anotación. Al proporcionar ejemplos y aclarar áreas que causaron confusión, puede ayudar a los anotadores humanos a aprender de sus errores y a impedir conflictos futuros.

Estos son algunos ejemplos de diversas formas en que los anotadores humanos discrepan:

- **Menciones**

    - Annotator_1 coloca una mención en una parte de texto; Annotator_2 no.
    - El índice del Annotator_1 comienza o termina antes o después del Annotator_2 (hay un solapamiento parcial o un subrango de texto).
    - Annotator_1 asigna un tipo de entidad que es diferente del tipo de entidad que Annotator_2 ha asignado.

- **Relaciones**

    - Annotator_1 crea una relación entre dos menciones; Annotator_2 no.
    - Annotator_1 y Annotator_2 crean una relación entre las mismas menciones, pero con un tipo de relación diferente.
    - Annotator_1 y Annotator_2 crean una relación entre las mismas menciones, pero en el orden inverso (raro, porque la relación entre la primera y la segunda mención está restringida por el sistema de tipos).

- **Cadenas de correferencia**

    - La versión del Annotator_1 de una cadena de correferencia incluye (o excluye) menciones que la cadena de correferencia del Annotator_2 excluye (o incluye). La alineación de entidades entre Annotator_1 y Annotator_2 se convierte en una cuestión de puntuación.

## Resolución de conflictos de anotación
{: #wks_haadjudicate}

La adjudicación es un paso que permite revisar los conflictos de anotación en documentos que se solapan antes de promocionar las anotaciones a datos de campo. Puede comparar las anotaciones añadidas por un par de anotadores humanos, o comparar las anotaciones humanas con los datos de campo actuales.

### Antes de empezar
{: #wks_haadjudicate_prereq}

Pulse [este enlace ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.youtube.com/watch?v=EbexfsuXxoQ&amp;feature=youtu.be){: new_window} para ver un vídeo de 3 minutos que ilustra cómo adjudicar los documentos.

### Acerca de esta tarea
{: #wks_haadjudicate_about}

Una vez que los anotadores humanos completen sus tareas de anotación, deben enviar sus conjuntos de anotaciones completados para su revisión. Cuando se evalúan las puntuaciones del acuerdo entre anotadores, puede ver cómo han anotado distintos pares de anotadores el mismo documento. Si la puntuación del acuerdo entre anotadores es aceptable, se aprobará el conjunto de anotaciones. Si un documento no se solapa entre conjuntos de anotaciones de la tarea, las anotaciones del documento aprobado se promocionarán a datos de campo. Si un documento se solapa en conjuntos de anotaciones, debe adjudicar el documento y resolver cualquier conflicto de anotación que exista antes de promocionar las anotaciones a datos de campo.

Por ejemplo, al adjudicar un documento, puede ver que un anotador ha anotado la mención `Barack Obama` con el tipo de entidad `PeoplePerson`. Otro anotador ha anotado la misma serie de texto como dos menciones, asignando el tipo de entidad `Person` a `Barack` y el tipo de entidad `Person` a `Obama`. Para ayudar a garantizar un entrenamiento correcto del modelo de aprendizaje automático, debería resolver esta incoherencia.

{{site.data.keyword.knowledgestudioshort}} da soporte a la capacidad de adjudicar entre dos conjuntos de anotaciones a la vez, o entre un conjunto de anotaciones y los datos de campo actuales. Si un documento se solapa entre más de dos conjuntos de anotaciones, adjudique los dos conjuntos de anotaciones en los que tiene más confianza (quizá porque confía más en los anotadores humanos) para determinar los datos de campo para el documento. Y, a continuación, adjudique el resto de los conjuntos de anotaciones en función de los resultados de la adjudicación inicial.

### Procedimiento
{: #wks_haadjudicate_procedure}

Para ver los documentos que se solapan y resolver conflictos:

1. Inicie sesión como un administrador o gestor de proyectos de {{site.data.keyword.knowledgestudioshort}}, y seleccione su espacio de trabajo.
1. Seleccione la página **Modelo de aprendizaje automático** > **Tareas de anotación** y abra la tarea que desee evaluar.
1. Confirme que al menos haya dos conjuntos de anotaciones en el estado **En conflicto**.
1. Pulse **Comprobar solapamiento de documentos en busca de conflictos**. Los documentos que están en conflicto están listados.
1. Si desea ignorar los conflictos en un documento que se solapa y promocionar las anotaciones a datos de campo sin adjudicarlos, pulse **Aceptar**.
1. Para empezar a resolver conflictos en un documento que se solapa, pulse **Comprobar conflictos**.
1. Si hay tres o más candidatos para la adjudicación, incluidos los conjuntos de anotaciones que fueron anotados mediante anotación humana y los datos de campo actuales, seleccione los dos candidatos que desee adjudicar y pulse **Comprobar conflictos**. Si solo existen dos candidatos, la herramienta de adjudicación se iniciará automáticamente.

    La herramienta de adjudicación muestra cuántos conflictos de menciones, relaciones y de cadena de correferencia existen. Debe resolver los conflictos de menciones antes de pasar a resolver conflictos entre relaciones y cadenas de correferencia.

1. Pulse para resaltar una frase que contenga conflictos. Para facilitar centrarse en conflictos no resueltos, es posible que desee desmarcar el recuadro de selección **Resuelto** y asegurarse de que el recuadro de selección **No resuelto** esté seleccionado.
1. Pulse anotaciones individuales y, a continuación, pulse **Aceptar** o **Rechazar**. Para deshacer una decisión que acaba de tomar, pulse Ctrl+Z.

    También puede pulsar más de una anotación y, a continuación, pulsar para aceptar o rechazar todas las anotaciones seleccionadas. Si decide que desea deseleccionar una anotación que ha seleccionado, desmarque sus selecciones pulsando el espacio en blanco entre frases o pulsando la tecla **Esc**.

    Si las directrices de anotación estaban conectadas anteriormente al proyecto, y desea ayudar con la selección de la anotación correcta que se aplicará, pulse **Ver directrices**. Dependiendo de la configuración de los permisos de acceso en el sitio donde se alojan las directrices, es posible que pueda actualizar las directrices tras abrirlas, por ejemplo, para añadir aclaraciones y ejemplos.
    {: tip}

1. Para aplicar un tipo de entidad distinto a una mención, rechace la anotación actual, seleccione la mención, como `Barack Obama`, y luego seleccione el tipo de entidad correcto, como `Person`.
1. Continúe aceptando, rechazando y revisando otros conflictos de la frase. Después de resolver todos los conflictos de una frase, pulse el enlace **Seleccionar todas las anotaciones** y luego pulse **Aceptar**.
1. Pulse el icono de flecha para ir a la frase siguiente. Continúe hasta que todos los conflictos de menciones del documento estén resueltos.

    Para guardar el trabajo en curso, o para suspender temporalmente la sesión de adjudicación actual, pulse **Guardar** en cualquier momento. Si desea descartar todos los cambios realizados, pulse **Descartar**. Si ha guardado la sesión de adjudicación anterior, y está listo para reanudar la adjudicación, pulse **Reanudar** para empezar a adjudicar conflictos donde se detuvo anteriormente. Si ha descartado la sesión de adjudicación anterior, debe empezar una nueva sesión de adjudicación.
    {: tip}

1. Después de resolver los conflictos de mención, cambie la modalidad de adjudicación para resolver los conflictos que se producen entre las anotaciones de relaciones y las anotaciones de cadena de correferencia.

    - La resolución de conflictos en la modalidad de relación es similar a cómo resolver conflictos para menciones. Resuelva conflictos en una base de frase por frase.
    - Las cadenas de correferencia pueden existir entre varias frases. Cuando se mueva a la modalidad de correferencia, el sistema listará las cadenas de correferencia creadas por cada anotador humano en un panel a la derecha. Seleccione las cadenas que desee adjudicar y, a continuación, pulse **Rechazar cadena** o **Aceptar cadena** para rechazar o aceptar las anotaciones de una cadena, o pulse **Fusionar cadenas** para fusionar las dos cadenas. Si desea eliminar una mención de una cadena de correferencia, pulse el icono de supresión (-) en la etiqueta por encima de la mención en el área del documento.

1. Una vez que todos los conflictos del documento estén resueltos, pulse **Promocionar a datos de campo**.
