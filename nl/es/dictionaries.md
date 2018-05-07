---

copyright:
  years: 2015, 2018
lastupdated: "2018-04-04"

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

Esta documentación es para {{site.data.keyword.knowledgestudiofull}} en {{site.data.keyword.cloud}}. Para ver la documentación para la versión anterior de {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.IBM_notm}} Marketplace, [pulse este enlace ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/services/knowledge-studio/dictionaries.html){: new_window}.
{: tip}

# Creación de diccionarios
{: #dictionaries}

Los diccionarios ayudan a los anotadores automáticos de {{site.data.keyword.knowledgestudioshort}} a comprender el idioma del dominio.
{: shortdesc}

## Diccionarios
{: #wks_dictionaries}

En el aprendizaje automático, un diccionario agrupa palabras y frases que tienen algo en común. Una entrada del diccionario no significa que todas las palabras de la entrada signifiquen lo mismo, sino que un modelo tratará a las palabras de forma equivalente.

Un diccionario es una lista de palabras y frases que son equivalentes para fines de extracción de información, lo que significa que son intercambiables para los fines de identificación de menciones de entidades y de relaciones.

Tenga en cuenta este ejemplo: una entrada de diccionario contiene los siete días de la semana. Para anotar un documento, un anotador humano asigna el tipo de entidad DAY_OF_WEEK a menciones de Lunes y Viernes en el texto. Dado que el diccionario equipara los siete días de la semana, ayudará a garantizar que un modelo de aprendizaje automático anote correctamente apariciones de Martes, Miércoles y el resto de los días de la semana en documentos no vistos en tiempo de ejecución. Además, equiparar estas palabras también beneficia la extracción de información en el texto circundante. Lo que aprende el modelo de aprendizaje automático de ejemplos de entrenamiento sobre los textos cerca de Lunes y Viernes se aplica a los textos que el modelo de aprendizaje automático ve cerca de otros días de la semana porque el diccionario indica que estos términos son equivalentes para fines de extracción de información.

> **Nota:** No es necesario crear un diccionario que contenga información de los días de la semana; se crean varios diccionarios de finalidad general como este en la aplicación. Otros incluyen países, nombres de lugares, palabras de números, animales, plantas, enfermedades, palabras de medida (como onza y metro), y palabras de título de saludo (como Mr. (Señor) y Mrs. (Señora)). No puede inhabilitar ni editar diccionarios incorporados.

Evite añadir entradas que tengan varios significados. Por ejemplo, en un dominio sobre automovilismo, tiene sentido incluir el término *banco*, que hace referencia a una característica vial, solo si las instituciones financieras no se tratan también frecuentemente en el texto. Si se dan ambos sentidos de la palabra con frecuencia en los documentos de origen, será mejor dejarla fuera de ambos tipos de diccionarios: el diccionario que está asociado con características viales, y el que está asociado con las instituciones financieras.

Puede crear diccionarios en {{site.data.keyword.knowledgestudioshort}} añadiendo manualmente entradas individuales. {{site.data.keyword.knowledgestudioshort}} también da soporte a la capacidad de cargar varios tipos de archivos de diccionario.

### ¿Cómo se utilizan los diccionarios?

Los diccionarios se utilizan en un par de formas, todas opcionales. Los utiliza el modelo de aprendizaje automático para proporcionar palabras o frases que son equivalentes para fines de extracción de información y durante la preanotación para arrancar el esfuerzo de anotación.

- **Uso del aprendizaje automático**

    El tipo de entidad que asocie con un diccionario no se utiliza para definir reglas para el modelo de aprendizaje automático. El aprendizaje automático evalúa las menciones en los documentos de forma independiente. No presupone que una mención tenga un tipo de entidad específico solo porque la mención coincida con una entrada de un diccionario asociado con tal tipo de entidad. Pone la información en la cuenta, pero la trata como una parte de información entre otras partes de información que se recopile mediante el análisis lingüístico. De hecho, si ninguno de los términos de un diccionario se da en los documentos de datos de campo, el diccionario no lo utilizará en absoluto el modelo de aprendizaje automático.

- **Uso de la preanotación**

    Los diccionarios son importantes para los siguientes procesos de preanotación.
    - Preanotador del diccionario: Asocie un diccionario con un tipo de entidad desde el sistema de tipos al ejecutar el preanotador del diccionario.
    - Modelo basado en reglas: Puede asociar un diccionario opcionalmente con una clase de regla. Las clases se correlacionarán con tipos de entidades desde el sistema de tipos al ejecutar el modelo basado en reglas para preanotar documentos. Como resultado, los términos del diccionario se correlacionan, aunque no directamente, con los tipos de entidades también para el modelo basado en reglas.

    En ambos casos, los diccionarios proporcionan términos que el sistema puede encontrar y anotar como menciones. Asigna a cada mención el tipo de entidad asociado con el diccionario que contiene el término. Cuando un anotador humano empieza a trabajar en documentos nuevos que se preanotaron, muchas menciones ya estarán anotadas en función de las entradas del diccionario. El anotador humano así tendrá más tiempo para centrarse en asignar tipos de entidades a menciones que requieren un análisis más profundo.

### Consideraciones sobre el idioma

- Para el portugués de Brasil, el inglés, el francés, el alemán, el italiano y el español, {{site.data.keyword.knowledgestudioshort}} no proporciona actualmente una opción para especificar coincidencias del diccionario que no distingan entre mayúsculas y minúsculas, pero sí entradas del diccionario que coinciden con texto en mayúsculas. Por ejemplo, "vehicle" ("vehículo") del diccionario coincide con "vehicle", "Vehicle" o "VEHICLE" del texto, mientras que "Sat" del diccionario coincide con "Sat" o "SAT" del texto, pero no con "sat".
- Para el japonés y el coreano, la coincidencia del diccionario durante la preanotación distingue entre mayúsculas y minúsculas.
- Para el árabe, {{site.data.keyword.knowledgestudioshort}} presupone que el texto en árabe se almacena sin formato y trata el formato numérico como una propiedad de nivel de almacenamiento. Para obtener detalles sobre cómo maneja {{site.data.keyword.knowledgestudioshort}} el formato de caracteres y el formato numérico en árabe, consulte [Configuración de soporte para árabe](/docs/services/watson-knowledge-studio/language-support.html#wks_langsupp_ar).

### Diccionario de archivo CSV
{: #wks_dictionaries__cvsdict}

También conocido como el formato de diccionario estándar, un diccionario en formato de valores separados por coma (`CSV`) es un archivo que puede editar después de cargarlo. El tamaño máximo de un archivo `CSV` que se puede cargar es de 1 MB. Si tiene un archivo de diccionario mayor, divida el archivo grande en varios archivos y cárguelos uno por uno en un diccionario único del espacio de trabajo de {{site.data.keyword.knowledgestudioshort}}.

Para resumir los requisitos, debe utilizar un editor de texto para crear el archivo `CSV`, no software como Microsoft Excel, y el archivo debe utilizar la codificación UTF-8 que no incluye la marca de orden de bytes (BOM) al principio de la secuencia de texto. La primera fila del archivo debe especificar las siguientes cabeceras de columna:

```
lemma,poscode,surface
```
{: screen}

Las líneas restantes del archivo especifican las entradas de diccionario, donde:

- **`lema`**

    Especifica el formato de palabras más representativo para la entrada.

- **`poscode (árabe, portugués de Brasil, inglés, francés, alemán, italiano y español)`**

    Especifica un código que identifica la categoría léxica. Esta información de categoría léxica la utiliza el anotador del diccionario para ayudar con la señalización de la frase.
    - 0 - Desconocido

        > **Nota:** Este código soporta el caso de ejemplo donde desea cargar un diccionario grande generado automáticamente que no incluya la información de la categoría léxica en cada entrada. Puede asignar Desconocido a todas las entradas de forma predeterminada. Evite utilizar este código, si es posible.

    - 1 - Pronombre
    - 2 - Verbo
    - 3 - Nombre
    - 4 - Adjetivo
    - 5 - Adverbio
    - 6 - Adposición
    - 7 - Interjección
    - 8 - Conjunción
    - 9 - Determinador
    - 10 - Cuantificador

    En inglés, nombre(3), verbo(2) y adjetivo(4) son las partes de discurso más comunes utilizadas para las entradas de diccionario.

    > **Nota:** La categoría léxica no determina automáticamente el tipo de una mención. No presuponga que todos los nombres equivalen a las menciones de tipo de entidad ni que todos los verbos equivalen a menciones de tipo de relación. Por ejemplo, *American* es un adjetivo pero podría anotarse mejor como tipo de entidad GPE (entidad geopolítica) o PERSON. *Met* es un verbo, pero podría anotarse mejor como un EVENT_MEETING.

    En otros idiomas, como el alemán, que utiliza palabras compuestas, la exactitud de la información de categoría léxica es incluso más importante para ayudar a determinar los límites de palabras.

- **`poscode (japonés)`**

    Especifica un código que identifica la categoría léxica. El valor de categoría léxica es importante para la señalización del texto y para la preanotación en idiomas como el japonés, que no utilizan espacio en blanco para denotar límites de palabras.
    - 19 - Nombre
    - 23 - Prefijo común
    - 24 - Sufijo común
    - 140 - Nombre propio (Nombre)
    - 141 - Nombre propio (Apellidos)
    - 146 - Nombre propio (Nombre de persona)
    - 142 - Nombre propio (Organización)
    - 144 - Nombre propio (Nombre de lugar)
    - 143 - Nombre propio (Región)
    - 145 - Nombre propio (Otros)

- **`poscode (coreano)`**

    Especifica un código que identifica la categoría léxica. El valor de categoría léxica es importante para la señalización de texto y la preanotación en idiomas como el coreano, que no utilizan el espacio en blanco para denotar límites de palabras.
    - 10010 - Nombre
    - 10300 - Nombre propio (Nombre)
    - 10310 - Nombre propio (Apellidos)
    - 110360 - Nombre propio (Nombre de persona)
    - 10320 - Nombre propio (Organización)
    - 10340 - Nombre propio (Nombre de lugar)
    - 10330 - Nombre propio (Región)
    - 10350 - Nombre propio (Otros)

- **`superficie`**

    Especifica los términos equivalentes, también llamados formas superficiales. Repita el lema como una forma superficial y utilice una coma para separar varias formas superficiales. Si una forma superficial incluye una coma, ponga la forma superficial entre comillas.

Por ejemplo:

```
lemma,poscode,surface
IBM,3,IBM Corp.,IBM,"International Business Machines, Inc."
Department of Energy,3,DOE,Department of Energy
premium,4,premium,premium-grade
```
{: screen}

**Conceptos relacionados**:

[Carga de recursos desde otro espacio de trabajo](/docs/services/watson-knowledge-studio/exportimport.html)

**Tareas relacionadas**:

[Preanotación de documentos con el Preanotador de diccionarios](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannot)

## Adición de diccionarios a un espacio de trabajo
{: #wks_projdictionaries}

La adición de diccionarios es un paso opcional al crear un modelo. Los diccionarios son útiles porque permiten iniciar rápidamente el proceso de anotación.

### Acerca de esta tarea

Si proporciona un diccionario, puede ejecutar el preanotador de diccionarios en los documentos. El preanotador busca términos representados en el diccionario y los anota automáticamente. Este paso inicial en los documentos simplifica el trabajo del anotador humano porque podrá revisar las anotaciones añadidas por el preanotador y corregirlas o añadirlas a los mismos. No tiene que empezar todo desde cero.

Se aplican las siguientes restricciones a los diccionarios:

- Máximo de 15.000 entradas por diccionario

    > **Nota:** Este límite no se aplica a los diccionarios cargados como un archivo CSV de diccionario. Los diccionarios de solo lectura pueden contener más entradas.

- Máximo de 64 diccionarios por espacio de trabajo

### Procedimiento

Para añadir un diccionario al espacio de trabajo:

1. Inicie sesión como un administrador o gestor de proyectos de {{site.data.keyword.knowledgestudioshort}} y abra el separador **Activos y herramientas** > **Preanotadores** > **Diccionarios**.
1. Efectúe una de las tareas siguientes:

    - Pulse el botón **Cargar diccionario**, seleccione un diccionario y, a continuación, pulse **Cargar**. Después de cargar un diccionario, pulse **Gestionar diccionarios** para ver el diccionario y asociarlo con un tipo de entidad.

        - Puede cargar un archivo ZIP que contenga un diccionario descargado de otro espacio de trabajo de {{site.data.keyword.knowledgestudioshort}}. Debe cargar el sistema de tipos descargado desde el otro espacio de trabajo en formato JSON para poder cargar el archivo de diccionario correspondiente. Puede editar y añadir entradas a un diccionario que reutilice de otro espacio de trabajo de {{site.data.keyword.knowledgestudioshort}}. Consulte [Carga de recursos desde otro espacio de trabajo](/docs/services/watson-knowledge-studio/exportimport.html) para obtener más detalles.

        La carga de un archivo CSV también está soportada, pero cargar directamente como un diccionario crea un diccionario de solo vista previa que no puede editar ni utilizar para preanotar documentos. Para cargar un archivo CSV que pueda editar y utilizar para la preanotación, pulse **Gestionar diccionarios** y, a continuación, **Crear diccionario** para crear un diccionario en primer lugar y, a continuación, cargar el contenido de CSV como entradas a dicho diccionario creado recientemente.

    - Pulse el botón **Gestionar diccionarios** para crear un diccionario nuevo al que puede añadir entradas de diccionario.

        Pulse el botón **Crear diccionario** y especifique un nombre descriptivo para el diccionario. Seleccione el tipo de entidad que describa mejor el propósito del diccionario y, a continuación, pulse **Guardar**.

1. Para añadir entradas al diccionario, realice una de las siguientes tareas:

    - Pulse **Añadir entrada** para añadir una entrada de diccionario. Especifique el lema (el formato de palabra más representativo para el término).
    - Pulse **Cargar** para cargar un archivo `CSV` que contenga entradas de diccionario, y, a continuación, examine para seleccionar el archivo. El archivo CSV debe ser inferior a 1 MB.

1. Después de cargar o de añadir entradas, podrá editar las entradas.

    Abra una entrada para especificar términos equivalentes, llamados formas superficiales. Cada forma superficial debe tener 256 o menos caracteres. Puede cambiar cuál de las formas superficiales se utilizará como lema.

    Por ejemplo, el lema *{{site.data.keyword.IBM_notm}}* puede tener formas superficiales como *{{site.data.keyword.IBM_notm}} Corp.* e *International Business Machines, Inc.*.

1. Seleccione la categoría léxica apropiada para cada lema y forma superficial del diccionario.

    La información de categoría léxica la utiliza el señalizador, y durante la preanotación.

1. Pulse **Guardar** para almacenar los cambios.

### Qué hacer a continuación

Ejecute el preanotador, que utiliza los diccionarios creados para realizar un pase preliminar de los documentos de origen, y que añade anotaciones a los mismos.

**Tareas relacionadas**:

[Preanotación de documentos con el Preanotador de diccionarios](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannot)

**Referencia relacionada**:

[Soporte de varios idiomas](/docs/services/watson-knowledge-studio/language-support.html)
