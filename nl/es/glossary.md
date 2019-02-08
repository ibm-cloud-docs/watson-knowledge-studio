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

Esta documentación es para {{site.data.keyword.knowledgestudiofull}} en {{site.data.keyword.cloud}}. Para ver la documentación para la versión anterior de {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.IBM_notm}} Marketplace, [pulse este enlace ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/docs/services/knowledge-studio/glossary.html){: new_window}.
{: tip}

# Glosario
{: #glossary}

Este glosario incluye términos y definiciones para {{site.data.keyword.knowledgestudioshort}}.
{: shortdesc}

En este glosario se emplean las siguientes referencias cruzadas:

- *Véase* remite al lector de un término a su sinónimo preferido, o de un acrónimo o abreviatura a la definición completa.
- *Véase también* le remite a un término relacionado u opuesto.

[A](/docs/services/watson-knowledge-studio/glossary.html#gloss_A) [B](/docs/services/watson-knowledge-studio/glossary.html#gloss_B) [C](/docs/services/watson-knowledge-studio/glossary.html#gloss_C) [D](/docs/services/watson-knowledge-studio/glossary.html#gloss_D) [E](/docs/services/watson-knowledge-studio/glossary.html#gloss_E) [F](/docs/services/watson-knowledge-studio/glossary.html#gloss_F) [G](/docs/services/watson-knowledge-studio/glossary.html#gloss_G) [H](/docs/services/watson-knowledge-studio/glossary.html#gloss_H) [I](/docs/services/watson-knowledge-studio/glossary.html#gloss_I) [K](/docs/services/watson-knowledge-studio/glossary.html#gloss_K) [L](/docs/services/watson-knowledge-studio/glossary.html#gloss_L) [M](/docs/services/watson-knowledge-studio/glossary.html#gloss_M) [N](/docs/services/watson-knowledge-studio/glossary.html#gloss_N) [O](/docs/services/watson-knowledge-studio/glossary.html#gloss_O) [P](/docs/services/watson-knowledge-studio/glossary.html#gloss_P) [R](/docs/services/watson-knowledge-studio/glossary.html#gloss_R) [S](/docs/services/watson-knowledge-studio/glossary.html#gloss_S) [T](/docs/services/watson-knowledge-studio/glossary.html#gloss_T)

## A
{: #gloss_A}

- **exactitud**

    Una medida de la corrección de anotaciones producidas por un modelo de aprendizaje automático. Consulte también [precisión](/docs/services/watson-knowledge-studio/glossary.html#gloss_P) y [recuperación](/docs/services/watson-knowledge-studio/glossary.html#gloss_R).

- **análisis de exactitud**

    Analizar el modelo de aprendizaje automático puntuará para determinar si los cambios son necesarios para mejorar la exactitud.

- **adjudicación**

    Un proceso iterativo para resolver los conflictos de anotaciones al comparar las anotaciones añadidas al mismo documento por anotadores humanos distintos.

- **motor de análisis**

    Un programa que analiza los artefactos, como los documentos, e infiere información sobre ellos, y que implementa la especificación de interfaz del motor de análisis de UIMA. Los motores de análisis se crean desde bloques de construcción llamados anotadores. Un motor de análisis puede contener un único anotador, que se conoce como motor de análisis primitivo, o varios anotadores, que se conocen como un motor de análisis agregado.

- **anotación**

    Información sobre un fragmento de texto. Por ejemplo, una anotación podría indicar que un fragmento de texto representa un nombre de empresa.

- **conjunto de anotaciones**

    En la anotación humana, una recopilación de documentos extraídos desde el corpus que permiten que varios anotadores humanos compartan la carga de trabajo. En la anotación basada en máquina, una recopilación de documentos que se pueden utilizar como datos ciegos, datos de entrenamiento, o datos de prueba.

- **gestor del proceso de anotación**

    Un rol que es responsable de gestionar las actividades de ciclo de vida de anotación completa dentro de un espacio de trabajo. El gestor de proyectos que se añade a un espacio de trabajo suele realizar las actividades de un gestor de procesos de anotación.

- **anotador**

    Consulte [anotador humano](/docs/services/watson-knowledge-studio/glossary.html#gloss_H) y [anotador de aprendizaje automático](/docs/services/watson-knowledge-studio/glossary.html#gloss_M).

- **atributo**

    Característica o rasgo de una entidad que describe la entidad; por ejemplo, el número de teléfono de un empleado es uno de los atributos de empleado.

## B
{: #gloss_B}

- **datos ciegos**

    Un conjunto de documentos anotados con los datos de campo, como pares de preguntas y respuestas, anotación semántica y decisiones de pasaje. Los datos ciegos nunca los lanzan ni los ven los desarrolladores y se utilizan para probar el sistema periódicamente para evaluar el rendimiento en datos no mostrados. La prueba en datos ciegos impide que se corrompa la exactitud al sobreajustar a conjuntos o anotaciones de preguntas conocidas. Los resultados notificados solo deberían provenir de las pruebas que se ejecutan en los datos ciegos. Véase también [datos de prueba](/docs/services/watson-knowledge-studio/glossary.html#gloss_T) y [datos de entrenamiento](/docs/services/watson-knowledge-studio/glossary.html#gloss_T).

## C
{: #gloss_C}

- **concordancia**

    Proporciona una forma de asegurar que la misma mención se anote con el mismo tipo de entidad en un documento y en conjuntos de anotaciones. La concordancia ayuda a garantizar la coherencia entre varias apariciones de una mención sin necesitar que el anotador humano etiquete manualmente cada aparición.

- **matriz de confusión**

    Una tabla que proporciona un desglose numérico detallado de conjuntos de documentos anotados. La tabla se utiliza para comparar las anotaciones añadidas por un modelo de aprendizaje automático a las anotaciones en los datos de campo. La tabla informa del número de [falsos positivos](/docs/services/watson-knowledge-studio/glossary.html#gloss_F), [falsos negativos](/docs/services/watson-knowledge-studio/glossary.html#gloss_F), [verdaderos positivos](/docs/services/watson-knowledge-studio/glossary.html#gloss_T) y [verdaderos negativos](/docs/services/watson-knowledge-studio/glossary.html#gloss_T).

- **correferencia**

    Una relación entre dos palabras o frases en la que ambas hacen referencia a la misma persona o cosa y una se erige como un antecedente lingüístico de la otra. Por ejemplo, hay una correferencia entre los dos pronombres en la frase "She taught herself" ("Se enseñó a sí misma") pero no en la frase "She taught her" ("Le enseñó a ella"). Una correferencia enlaza dos entidades equivalentes en el mismo texto.

- **cadena de correferencia**

    Una lista de entidades que se han anotado como correferencias. Al anotar menciones como correferencias, el sistema creará una cadena de correferencia. La cadena proporciona una forma de ver todas las menciones en contexto y de verificar que todas las ocurrencias pertenezcan al mismo tipo de entidad.

- **corpus**

    Una recopilación de documentos de origen que se han añadido a un espacio de trabajo y que se han utilizado para entrenar un modelo de aprendizaje automático.

- **recopilar**

    Para seleccionar, recopilar, conservar y mantener contenido relevante para un tema específico. La recopilación establece, mantiene y añade valor a los datos; transforma datos en información y conocimiento de confianza.

## D
{: #gloss_D}

- **diccionario**

    Una recopilación de palabras que pueden utilizarse para preanotar documentos. Se creará una anotación nueva para cada palabra en el texto del documento que coincida con un término del diccionario. Un modelo de aprendizaje automático se puede configurar con uno o varios diccionarios independientes, que son normalmente específicos del dominio, como un diccionario para productos farmacéuticos y un diccionario para la gestión de la riqueza. Véase también [lema](/docs/services/watson-knowledge-studio/glossary.html#gloss_L) y [forma superficial](/docs/services/watson-knowledge-studio/glossary.html#gloss_S).

- **preanotador de diccionarios**

    Un componente que identifica menciones en el texto que coinciden con un conjunto específico de palabras. Al utilizar terminología específica del dominio para preanotar texto, los preanotadores de diccionarios pueden acelerar la capacidad de un anotador humano para preparar un conjunto de documentos de datos de campo.

- **conjunto de documentos**

    Una recopilación de documentos. Los documentos importados juntos se convierten en un conjunto de documentos. Los documentos anotados que se agrupan juntos para fines de entrenamiento (Prueba, entrenamiento, ciegos) se generan como conjuntos de documentos.

## E
{: #gloss_E}

- **entidad**

    1. Mención anotada por un tipo de entidad.
    1. Persona, objeto o concepto sobre el que se almacena información.
    1. Conjunto de detalles que se mantienen sobre un objeto del mundo real como una persona, una ubicación o una cuenta bancaria. Una entidad es un tipo de elemento.

- **tipo de entidad**

    El tipo de entidad que representa una mención sin tener en cuenta el contexto. Por ejemplo, la mención {{site.data.keyword.IBM_notm}} podría estar anotada por el tipo de entidad ORGANIZATION.

    En un modelo de relación basada en entidades, un tipo de entidad es lo que se modela o a lo que hace referencia una mención, como por ejemplo el nombre de una persona o de un lugar. Distintos tipos de entidades tienen distintos conjuntos de atributos como "surname" ("apellido") o "home town" ("ciudad de procedencia"), y están conectados mediante relaciones como "lives in" ("vive en"). Un tipo de entidad existe independientemente y puede identificarse de forma exclusiva.

## F
{: #gloss_F}

- **puntuación de F1**

    Una medida de la exactitud de una prueba que considera tanto la precisión como la recuperación para calcular la puntuación. La puntuación de F1 se puede interpretar como un promedio ponderado de los valores de precisión y de recuperación. Una puntuación de F1 llega a su mejor valor en 1 y a su peor valor en 0.

- **falso negativo**

    Una respuesta o una anotación que es correcta, pero que se ha predicho que es incorrecta.

- **falso positivo**

    Una respuesta o anotación que es incorrecta, pero que se ha predicho que es correcta.

- **característica**

    Un miembro de datos o atributo de un tipo.

- **puntuación de Fleiss Kappa**

    Una medida que muestra con cuánta coherencia han aplicado la misma anotación varios anotadores humanos en documentos que se solapan. La puntuación de Fleiss Kappa llega a su mejor valor en 1 y a su peor valor en 0.

## G
{: #gloss_G}

- **datos de campo**

    Conjunto de datos evaluados, que constan de anotaciones añadidas por anotadores humanos, que se utilizan para adaptar un modelo de aprendizaje automático a un dominio particular. Los datos de campo se utilizan para entrenar los modelos de aprendizaje automático, para medir el rendimiento de modelo (precisión y recopilación), y para calcular el margen dinámico para decidir dónde centrar los esfuerzos de desarrollo para mejorar el rendimiento. La exactitud de los datos de campo es esencial, ya que las inexactitudes en los datos de campo se correlacionarán con las inexactitudes en los componentes que los utilizan.

## H
{: #gloss_H}

- **análisis de margen de mejora**

    Proceso para determinar cuánta mejora en la exactitud, la precisión o la recuperación puede esperarse abordando algunas clases de problemas identificados al realizar un análisis de exactitud.

- **anotador humano**

    Un experto en la materia que revisa, modifica y aumenta los resultados de la preanotación identificando menciones, relaciones de tipos de entidades, y correferencias de menciones. Al examinar texto en contexto, un anotador humano ayuda a determinar los datos de campo y a mejorar la exactitud del modelo de aprendizaje automático.

## I
{: #gloss_I}

- **acuerdo entre anotadores**

    Una medida de con cuánta similaridad se anota un documento en dos o más conjuntos de documentos.

## K
{: #gloss_K}

- **gráfico de conocimiento**

    Un modelo que consolida las entidades con tipos, sus relaciones, sus propiedades y las taxonomías jerárquicas para representar una organización de conceptos para un dominio determinado. Una vez que el almacén de gráficos de conocimiento se cargue con entradas desde orígenes de datos estructurados y no estructurados, los usuarios y las aplicaciones podrán acceder al gráfico de conocimiento para explorar elementos clave de conocimiento para un dominio específico, para explorar interacciones y para descubrir relaciones adicionales.

## L
{: #gloss_L}

- **lema**

    Formato normalizado o canónico de una palabra. Normalmente, el lema es el formato no derivado y no declinado de un nombre o de un verbo. Por ejemplo, el lema de los términos 'organizing' ('organización') y 'organized' ('organizado') es 'organize' ('organizar'). Consulte también [diccionario](/docs/services/watson-knowledge-studio/glossary.html#gloss_D) y [forma superficial](/docs/services/watson-knowledge-studio/glossary.html#gloss_S).

## M
{: #gloss_M}

- **aprendizaje automático**

    Un método de análisis de datos que aprende de forma iterativa a partir de los datos pasados y que se adapta independientemente cuando se expone a datos nuevos. El modelo matemático en el centro de aprendizaje automático se basa en entradas de datos de campo. Mediante el entrenamiento y el refinamiento de los datos de entrada de ejemplo, el modelo puede ofrecer datos precisos y repetibles cuando analiza datos nuevos.

- **anotador de aprendizaje automático**

    Véase [modelo de aprendizaje automático](/docs/services/watson-knowledge-studio/glossary.html#gloss_M).

- **modelo de aprendizaje automático**

    Un componente que identifica entidades y relaciones de entidades según un modelo estadístico que se basa en datos de campo. El modelo se aplica a la experiencia pasada, como los datos de entrenamiento, para determinar o predecir el resultado correcto de experiencias futuras basadas en las características de los datos. Estas experiencias pasadas son captadas en forma de modelo mediante el cálculo de puntuaciones de características para cada prueba o respuesta de un candidato y su combinación con resultados conocidos. A veces conocidas como *anotador de aprendizaje automático*.

- **mención**

    Una parte de texto que considere relevante en los datos de dominio. Por ejemplo, en un sistema de tipos sobre vehículos automotores, las apariciones de términos como "airbag", "Ford Explorer" y "sistema de retención infantil" podrían ser menciones relevantes.

## N
{: #gloss_N}

- **entidad con nombre**

    Un concepto de un dominio que entra en una categoría bien definida, como los nombres de organizaciones, las ubicaciones, los autores o las enfermedades.

- **procesamiento del lenguaje natural**

    Un campo de inteligencia artificial y de lingüística que estudia los problemas inherentes en el proceso y en la manipulación de lenguaje natural, con el fin de aumentar la capacidad de los ordenadores para comprender los idiomas humanos.

## O
{: #gloss_O}

- **ontología**

    Especificación formal explícita de la representación de los objetos, conceptos y otras entidades que pueden existir en un área de interés y las relaciones entre ellos.

## P
{: #gloss_P}

- **categoría léxica (POS)**

    En un diccionario, se asigna a elementos léxicos individuales etiquetas de categoría léxica (POS). Por ejemplo, la palabra 'fly' se puede identificar como un verbo o un nombre.

- **rendimiento**

    Medida de un sistema de {{site.data.keyword.watson}} en términos de exactitud, precisión y recuperación, por ejemplo, al responder preguntas, descubrir relaciones o anotar texto.

- **preanotación**

    Proceso de anotación de un conjunto de documentos antes de la anotación humana. Los documentos se pueden preanotar utilizando un modelo basado en reglas, un modelo de aprendizaje automático, {{site.data.keyword.nlufull}}, o un diccionario. La preanotación puede ayudar a los anotadores humanos a preparar más rápidamente un conjunto de documentos de datos de campo.

- **precisión**

    Una medida que especifica la proporción de resultados que son relevantes. La precisión, que es un valor predictivo positivo, se determina mediante el número de resultados positivos correctos dividido por el número de todos los resultados positivos. La exactitud se mide mejor mediante la precisión y la recuperación. Véase también [exactitud](/docs/services/watson-knowledge-studio/glossary.html#gloss_A) y [recuperación](/docs/services/watson-knowledge-studio/glossary.html#gloss_R).

- **archivador de motor de proceso (PEAR)**

    Un archivo de archivado `.pear` que incluye un motor de análisis de UIMA (Unstructured Information Management Architecture) y todos los recursos necesarios para utilizarlo para el análisis personalizado.

## R
{: #gloss_R}

- **recuperación**

    Una medida que especifica el porcentaje de resultados relevantes devueltos, de todos los resultados relevantes disponibles. La recuperación, que es una medida de sensibilidad, está determinada por el número de resultados positivos correctos dividido por el número de resultados positivos que deberían haberse devuelto. La exactitud se mide mejor mediante la precisión y la recuperación. Véase también [exactitud](/docs/services/watson-knowledge-studio/glossary.html#gloss_A) y [precisión](/docs/services/watson-knowledge-studio/glossary.html#gloss_P).

- **relación**

    Normalmente un verbo que refleja cómo se relacionan las entidades entre sí. Por ejemplo, "lives in" ("vive en") es una relación entre una persona y una ciudad. Una relación enlaza dos entidades distintas en la misma frase.

- **tipo de relación**

    Una relación binaria y unidireccional entre dos entidades. Por ejemplo, `Mary` `employedBy` {{site.data.keyword.IBM_notm}} es una relación válida; {{site.data.keyword.IBM_notm}} `employedBy` `Mary`, no.

- **rol**

    Un atributo que proporciona un significado que distingue el contexto de una mención. Por ejemplo, en la frase "I went to {{site.data.keyword.IBM_notm}} today" ("Hoy he ido a {{site.data.keyword.IBM_notm}}"), {{site.data.keyword.IBM_notm}} es la mención, Organization es el tipo de entidad, y Facility es el rol del tipo de entidad.

- **conjunto de reglas**

    Un conjunto de reglas que definen patrones para anotar texto. Si se aplica un patrón, las acciones de la regla se realizarán en las anotaciones coincidentes. Una regla normalmente especifica la condición que debe coincidir, un cuantificador opcional, una lista de restricciones adicionales que el texto coincidente debe cumplir, y las acciones que se realizarán cuando se produzca una coincidencia, como crear una nueva anotación o modificar una anotación existente.

## S
{: #gloss_S}

- **subtipo**

    Tipo que amplía o implementa otro tipo; el supertipo.

- **forma superficial**

    Formato de una palabra o unidad de varias palabras como se encuentra en el corpus. Por ejemplo, algunas formas superficiales del lema 'organize' ('organizar') son los términos 'organizing' ('organización') y 'organized' ('organizado'). Véase también [diccionario](/docs/services/watson-knowledge-studio/glossary.html#gloss_D) y [lema](/docs/services/watson-knowledge-studio/glossary.html#gloss_L).

## T
{: #gloss_T}

- **datos de prueba**

    Un conjunto de documentos anotados que pueden utilizarse para evaluar las métricas de sistema después de la ingesta y del entrenamiento. Véase también [datos ciegos](/docs/services/watson-knowledge-studio/glossary.html#gloss_B) y [datos de entrenamiento](/docs/services/watson-knowledge-studio/glossary.html#gloss_T).

- **entrenar**

    Proceso de configurar una instancia de {{site.data.keyword.watson}} con componentes que permiten que el sistema funcione en un dominio determinado (por ejemplo: contenido del corpus, datos de entrenamiento que generan modelos de aprendizaje automático, algoritmos mediante programación u otros componentes de datos de campo) y luego de realizar mejoras y actualizaciones en estos componentes basándose en el análisis de exactitud.

- **datos de entrenamiento**

    Un conjunto de documentos anotados que pueden utilizarse para entrenar modelos de aprendizaje automático. Véase también [datos ciegos](/docs/services/watson-knowledge-studio/glossary.html#gloss_B) y [datos de prueba](/docs/services/watson-knowledge-studio/glossary.html#gloss_T).

- **verdadero negativo**

    Una respuesta o anotación que en realidad es incorrecta y se prevé que sea incorrecta.

- **verdadero positivo**

    Una respuesta o anotación que en realidad es correcta y que se prevé que sea correcta.

- **sistema de tipos**

    El sistema de tipos define los tipos de objetos que se pueden descubrir en un documento. El sistema de tipos define todos los tipos de entidades y relaciones posibles entre tipos de entidades. Puede definir cualquier número de tipos distintos en un sistema de tipos. Los sistemas de tipos son generalmente específicos del dominio y de la aplicación.
