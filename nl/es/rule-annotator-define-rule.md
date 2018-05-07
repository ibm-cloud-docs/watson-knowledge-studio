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

Esta documentación es para {{site.data.keyword.knowledgestudiofull}} en {{site.data.keyword.cloud}}. Para ver la documentación para la versión anterior de {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.IBM_notm}} Marketplace, [pulse este enlace ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/services/knowledge-studio/rule-annotator-define-rule.html){: new_window}.
{: tip}

# Definición de una regla
{: #wks_rule_creation}

Utilice el editor de reglas para definir reglas.
{: shortdesc}

## Acerca de esta tarea

Evite que varios usuarios editen simultáneamente reglas, clases y expresiones regulares porque podría provocar sobrescrituras o duplicaciones inesperadas.

## Procedimiento

Para definir una regla, siga estos pasos:

1. Inicie sesión como administrador o gestor de proyectos de {{site.data.keyword.knowledgestudioshort}} y abra la página **Reglas**.
1. Pulse el signo más (+) junto a Documentos para añadir un documento.

    Consulte [Añadir documentos para definir reglas](/docs/services/watson-knowledge-studio/rule-annotator-add-doc.html) para obtener detalles.

    Por ejemplo, podría añadir un documento denominado `Mi documento` que contiene esta única línea de texto:

    ```
    A 50-year-old driver was driving the 2017 Example Horizon.
    ```
    {: screen}

1. Si piensa definir una expresión regular o añadir un diccionario, cree una clase con la que asociarlos.

    1. Desde el panel **Clase**, pulse el signo más (+) junto a Clase.
    1. Añada un nombre de clase.

        Si va a asociar la clase con una expresión regular o un diccionario, piense en denominar la clase de tal forma que se pueda identificar su origen. Por ejemplo, si tiene previsto utilizar una expresión regular para definir un patrón para el número de la frase, puede crear una clase denominada AGE_REGEX. Si y piensa utilizar un diccionario para anotar el fabricante del coche en la frase, puede añadir una clase denominada MANUFACTURER_DICT.

        Tenga en cuenta estas reglas de denominación:
        - El primer carácter de un nombre de clase debe ser alfabético.
        - Utilice solo los siguientes caracteres ASCII alfanuméricos y el carácter de subrayado en valores que añada a las clases: de A a Z, de a a z, de 0 a 9.
        - Los nombres no pueden contener espacios.
        - Los nombres no pueden tener más de 64 caracteres.

1. Opcional: Para anotar clases rápidamente en el documento, puede asociar un diccionario con el editor de reglas. Los términos del documento que coincidan con las entradas del diccionario se anotarán automáticamente con la clase apropiada.

    1. Pulse el separador **Diccionarios** en el panel.

        Se visualizarán los diccionarios que haya creado.

        Si no ha añadido un diccionario, abra el separador **Diccionarios** desde la barra de navegación principal para añadir uno. Consulte [Creación de diccionarios](/docs/services/watson-knowledge-studio/dictionaries.html) para obtener más información.

    1. Pulse un diccionario y defina una asociación de clases para el mismo y, a continuación, pulse **Guardar**.

        Por ejemplo, si tiene un diccionario que contenga los nombres de la organización, puede asociarlo con la regla y asignar la clase ORGANIZATION_DICT al mismo. Los nombres de la organización que se produzcan en los documentos de ejemplo se anotarán como instancias de la clase ORGANIZATION_DICT.

    Si desea eliminar la asociación del diccionario desde el editor de reglas más tarde, puede eliminar la correlación de clases. Para ello, seleccione la opción vacía desde la parte superior de la lista desplegable.

1. Opcional: Para definir una expresión regular para ayudarle a construir una regla, pulse **Regex** en la navegación.

    1. Pulse el signo más (+) junto a Expresiones regulares para añadir una expresión regular.
    1. Asigne un nombre a la expresión regular. Por ejemplo, MyAgeRegex.

        El nombre no puede tener más de 64 caracteres.

    1. Asocie la expresión con una clase. Por ejemplo, AGE_REGEX.
    1. Pulse **Añadir entrada**.
    1. Añada la expresión.

        Por ejemplo, para capturar un número que represente una edad (hasta 99 años), puede especificar `[0-9]{1,2}`. Para capturar expresiones de tiempo, como *12:30 AM*, puede especificar esta expresión regular:

        ```
        (1[0-2]|0?[1-9]):([0-5][0-9])(\s+[AaPp][Mm])?
        ```
        {: screen}

        Puede cambiar opcionalmente el número mínimo y máximo de señales de palabras. En inglés, las señales suelen ser equivalentes a las palabras porque se delimitan mediante espacios en blanco en una frase. Sin embargo, no siempre coinciden one-to-one con palabras; otros elementos textuales se consideran señales en algunas situaciones. Por ejemplo, los guiones en el término *50-year-old* cuentan cada uno como una señal, lo que significa que el número total de señales utilizadas en este término es de 5. Y el texto *12:30 PM* contiene 4 señales. (`12 | : | 30 | PM`)

        Pulse **Añadir**.

    1. Repita los dos pasos anteriores si desea añadir más expresiones.
    1. Pulse **Guardar**.

    El editor de regex se cerrará, y el documento se visualizará. Debería ver la clase que ha definido para la expresión regular aplicada al texto con el que pretende hacerle coincidir. Si no, compruebe su expresión. Es posible que necesite ser revisada para que coincida con el texto que pretende que encuentre.

    ![El editor de reglas que muestra el separador "Regex" seleccionado, una expresión regular llamada "Age" que está asociada con la clase "AGE_REGEX", y un documento que muestra el texto "50" resaltado en amarillo. El texto resaltado coincide con la expresión regular que se ha creado.](images/rule_step3.jpg)

1. Para definir una regla, pulse **Reglas** en la navegación.
1. Abra el documento con el patrón que desea capturar como una regla. Por ejemplo, si ha creado un documento titulado `Mi documento` con el texto de ejemplo que contiene la frase `50-year-old`, abra dicho documento.
1. Desde el texto del documento, seleccione los caracteres que ilustran el patrón que desea capturar. Por ejemplo, puede seleccionar las siguientes palabras y guiones (-):

    ```
    50-year-old
    ```
    {: screen}

    Después de seleccionar caracteres, puede añadir una regla.

1. Pulse el signo más (+) en el panel **Reglas**.

    El editor de reglas representa el texto que ha seleccionado como dos capas de células. Las células de la capa superior son donde anota las clases de las señales subyacentes. La capa inferior es donde define las condiciones en que las señales participan en el patrón.

    ![El editor de reglas que muestra el aspecto del panel "Crear una regla" tras seleccionar texto del documento y pulsar el signo más en el panel "Reglas". Se mostrarán los siguientes elementos gráficos: el campo "Nombre de regla" con el término "AGE" introducido, el panel "Crear una regla" y el panel "Clase". En el panel "Crear una regla", las células con líneas de puntos se muestran en la parte superior. Se muestra una célula para cada señal del texto que se ha seleccionado. En estas células, anote las clases de las señales. En la parte inferior del panel "Crear una regla", se mostrarán las células con líneas continuas. Cada célula contiene una señal del texto seleccionado, "50-year-old". Las señales con "50", "-" (guión), "year", "-", y "old". Cada célula de línea continua tiene dos iconos junto a ella que se pueden utilizar para ajustar la condición de la palabra o la anotación.](images/rule_step4.jpg)

1. Define las condiciones por las que cada señal participa en el patrón.

    En la capa inferior de células, pulse la primera señal para revisar sus condiciones. Si desea indicar que se puede utilizar cualquier señal en la posición actual en el patrón, pulse **Abrir propiedades**, y seleccione **Permitir cualquier señal**. Pulse **Cerrar propiedades**. Si una señal es una expresión regular, como `AGE_REGEX` en el ejemplo, **Permitir cualquier señal** no estará disponible.

    > **Nota:** El número máximo de células de grupo que puede participar en un patrón es de 15 cuando cada célula tiene un valor repetido de 1 o menos. Las células de grupo incluyen señales únicas, anotaciones, o señales donde se permite cualquier señal. El número máximo de señales totales permitidas en un patrón es de 20. Tenga en cuenta el valor repetido de cada célula a medida que defina el patrón. Por ejemplo, puede definir un patrón que incluya 15 señales cuando cada célula tenga un valor repetido de 1 o menos. Sin embargo, no se pueden definir más de 4 señales en el patrón si cada una tiene un valor repetido de 1 o más porque, para cada uno, la señal se puede repetir hasta 5 veces. Cuatro señales que se repiten 5 veces le llevan al máximo permitido de 20.

    Para indicar que es necesario un tipo concreto de señal, puede definir los siguientes tipos de valores de condición:
    - **Valor repetido**: Especifica cuántas veces se debe incluir la señal actual en el patrón. Puede cambiar el valor repetido, pero solo se puede especificar un valor repetido por señal. Las opciones se describen en la tabla siguiente.

    <table cellpadding="4" cellspacing="0" summary="" border="1" class="simpletable">
      <tr class="sthead">
        <th valign="bottom" align="left" id="d27028e471" class="stentry thleft thbot">Opción de configuración</th>
        <th valign="bottom" align="left" id="d27028e473" class="stentry thleft thbot">Descripción</th>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e471" class="stentry">
          <p class="p wrapper">Necesario (Exactamente 1)</p>
        </td>
        <td valign="top" headers="d27028e473" class="stentry">
          <p class="p wrapper">Esta señal debe existir en el patrón
            una vez. Esta opción se aplica de forma predeterminada, pero se puede
            cambiar.</p></td>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e471" class="stentry">
          <p class="p wrapper">Repitiendo 1 o más veces</p>
        </td>
        <td valign="top" headers="d27028e473" class="stentry">
          <p class="p wrapper">Esta señal debe existir en el patrón
            al menos una vez, y se puede repetir más veces.</p>
        </td>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e471" class="stentry">
          <p class="p wrapper">Repitiendo 0 o más veces</p>
        </td>
        <td valign="top" headers="d27028e473" class="stentry">
          <p class="p wrapper">Esta señal puede repetirse opcionalmente en
            el patrón muchas veces, pero no tiene que repetirse.</p>
        </td>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e471" class="stentry">
          <p class="p wrapper">Produciéndose 0 o 1 veces</p>
        </td>
        <td valign="top" headers="d27028e473" class="stentry">
          <p class="p wrapper">Esta señal es opcional.</p>
        </td>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e471" class="stentry">
          <p class="p wrapper">Avanzado: _personalizado_</p>
        </td>
        <td valign="top" headers="d27028e473" class="stentry">
          <p class="p wrapper">Esta señal debe repetirse en el patrón
            el número de veces que se especifique aquí. Para definir
            un valor de repetición personalizado, pulse
            <b>Abrir propiedades</b>,
            seleccione **Avanzado** y, a continuación, seleccione el número exacto de repeticiones o rangos de repeticiones             que desee definir.</p>
          <p class="note">
            El número máximo de repeticiones permitidas para una señal es de
            5.</p>
        </td>
      </tr>
    </table>

    - **Valor de característica**: Debe definirse al menos un valor de característica. Puede añadir más características para añadir al número de condiciones que deben cumplirse para que el texto coincida con este patrón. Las opciones se describen en la tabla siguiente.

    <table cellpadding="4" cellspacing="0" summary="" border="1" class="simpletable">
      <tr class="sthead">
        <th valign="bottom" align="left" id="d27028e512" class="stentry thleft thbot">Opción de configuración</th>
        <th valign="bottom" align="left" id="d27028e514" class="stentry thleft thbot">Condición que añade</th>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e512" class="stentry">
          <p class="p wrapper">Texto</p>
        </td>
        <td valign="top" headers="d27028e514" class="stentry">
          <p class="p wrapper">Debe coincidir con el texto exacto en esta
            señal. Esta opción se aplica de forma predeterminada. Puede eliminarla,
            pero solo si añade un valor distinto como condición
            o si aplica el valor Cualquier señal.</p>
        </td>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e512" class="stentry">
          <p class="p wrapper">Longitud</p>
        </td>
        <td valign="top" headers="d27028e514" class="stentry">
          <p class="p wrapper">Debe coincidir con la longitud de caracteres de
            esta señal. La longitud se cuenta a partir de 0 frente
            al primer carácter.</p>
        </td>
      </tr>
    </table>

    El resto de las opciones varían según el tipo de la señal.

    - **La señal no anotada no coincide con una expresión regular o con un término del diccionario**: Estos valores están disponibles para señales no anotadas y no coinciden con una expresión regular o con un término del diccionario.

    <table cellpadding="4" cellspacing="0" summary="" border="1" class="simpletable">
      <tr class="sthead">
        <th valign="bottom" align="left" id="d27028e535" class="stentry thleft thbot">Opción de configuración</th>
        <th valign="bottom" align="left" id="d27028e537" class="stentry thleft thbot">Descripción</th>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e535" class="stentry">
          <p class="p wrapper">Categoría léxica</p>
        </td>
        <td valign="top" headers="d27028e537" class="stentry">
          <p class="p wrapper">Debe ser la misma categoría léxica
            que la de esta señal. Se admiten los siguientes tipos:</p>
          <ul class="ul bullets">
            <li class="li">
              <p class="p wrapper">adjetivo</p>
            </li>
            <li class="li">
              <p class="p wrapper">adposición</p>
            </li>
            <li class="li">
              <p class="p wrapper">adverbio</p>
            </li>
            <li class="li">
              <p class="p wrapper">conjunción</p>
            </li>
            <li class="li">
              <p class="p wrapper">determinante</p>
            </li>
            <li class="li">
              <p class="p wrapper">interjección</p>
            </li>
            <li class="li">
              <p class="p wrapper">nombre</p>
            </li>
            <li class="li">
              <p class="p wrapper">numeral</p>
            </li>
            <li class="li">
              <p class="p wrapper">pronombre</p>
            </li>
            <li class="li">
              <p class="p wrapper">residual</p>
            </li>
            <li class="li">
              <p class="p wrapper">verbo </p>
            </li>
          </ul>
        </td>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e535" class="stentry">
          <p class="p wrapper">Lema</p>
        </td>
        <td valign="top" headers="d27028e537" class="stentry">
          <p class="p wrapper">Debe tener el mismo lema que esta
            señal.</p>
        </td>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e535" class="stentry">
          <p class="p wrapper">Tipo de carácter</p>
        </td>
        <td valign="top" headers="d27028e537" class="stentry">
          <p class="p wrapper">Debe tener el mismo tipo de carácter
            que esta señal. Se admiten los siguientes tipos:</p>
          <ul class="ul bullets">
            <li class="li">
              <p class="p wrapper">Árabe: Contiene una secuencia
                de caracteres árabes</p>
            </li>
            <li class="li">
              <p class="p wrapper">ChineseNumeral: Contiene solo
                numerales chinos</p>
            </li>
            <li class="li">
              <p class="p wrapper">ClauseEndingPunctuation:
                Caracteres de puntuación que separan una cláusula
                o frase de la siguiente</p>
            </li>
            <li class="li">
              <p class="p wrapper">Han: Contiene caracteres han</p>
            </li>
            <li class="li">
              <p class="p wrapper">Hangul: Contiene caracteres silábicos hangul
                coreanos</p>
            </li>
            <li class="li">
              <p class="p wrapper">Hebreo: Contiene una secuencia de caracteres
                hebreos</p>
            </li>
            <li class="li">
              <p class="p wrapper">Hiragana: Contiene caracteres silábicos hiragana
                japoneses</p>
            </li>
            <li class="li">
              <p class="p wrapper">Ideográfico: Contiene un
                ideograma, o un símbolo que representa una idea o
                cosa</p>
            </li>
            <li class="li">
              <p class="p wrapper">Katakana: Contiene caracteres silábicos katakana
                japoneses</p>
            </li>
            <li class="li">
              <p class="p wrapper">Minúscula: Contiene solo caracteres alfabéticos en
                minúsculas</p>
            </li>
            <li class="li">
              <p class="p wrapper">Numérico: Contiene solo caracteres
                numéricos</p>
            </li>
            <li class="li">
              <p class="p wrapper">Puntuación: Uno o varios
                caracteres que proporcionan puntuación en el
                texto</p>
            </li>
            <li class="li">
              <p class="p wrapper">Silábico: Contiene caracteres
                silábicos</p>
            </li>
            <li class="li">
              <p class="p wrapper">Tailandés: Contiene caracteres
                tailandeses</p>
            </li>
            <li class="li">
              <p class="p wrapper">Mayúsculas de título: Empieza por un
                único carácter alfabético en mayúscula, seguido
                por uno o más caracteres alfabéticos en minúscula</p>
            </li>
            <li class="li">
              <p class="p wrapper">Mayúscula: Una señal que contiene
                solo caracteres alfabéticos en mayúscula</p>
            </li>
          </ul>
        </td>
      </tr>
    </table>

    - **Coincidencia de regla:**

    <table cellpadding="4" cellspacing="0" summary="" border="1" class="simpletable">
      <tr class="sthead">
        <th valign="bottom" align="left" id="d27028e617" class="stentry thleft thbot">Opción de configuración</th>
        <th valign="bottom" align="left" id="d27028e619" class="stentry thleft thbot">Descripción</th>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e617" class="stentry">
          <p class="p wrapper">Coincidencia de regla</p>
        </td>
        <td valign="top" headers="d27028e619" class="stentry">
          <p class="p wrapper">Debe coincidir con la clase denominada.
            Recuerde: una clase puede derivarse de una expresión regular,
            un diccionario o una regla. Si la clase especificada
            aquí se ha derivado de una expresión regular, por
            ejemplo, esta señal deberá coincidir con el patrón de búsqueda
            de la expresión.</p>
        </td>
      </tr>
    </table>

1. Para las señales que tienen anotaciones añadidas indirectamente de una anotación de diccionario o de una coincidencia de expresión regular, puede elegir si el patrón necesitaría una palabra con el mismo tipo de anotación o las palabras subyacentes reales anotadas en su lugar.

    En la capa inferior de células, puede ver qué células se incluyen en el patrón porque una línea horizontal las conecta entre sí. Cuando se haya aplicado una anotación, habrá una división. Las células con las palabras originales se muestran por debajo de una célula con la etiqueta de anotación. Puede pulsar un conjunto de células u otro para cambiar la vía de acceso de la línea, y así cambiar las células incluidas en el patrón.

    Por ejemplo, podría elegir hacer que el patrón utilice 50 en lugar de hacer que coincida con la expresión regular age.

    ![El panel "Crear una regla" que muestra una edición de la señal, "50", que utiliza la anotación, "AGE_REGEX", en la regla. De forma predeterminada, se utiliza la anotación "AGE_REGEX", pero puede editar el patrón para que la palabra subyacente, "50", se utilice en su lugar.](images/rule_step5.jpg)

1. Después de establecer el orden de patrón, podrá anotar señales en el texto.

    Desde la capa superior de células, pulse aquellas que representen las señales que desea anotar, y luego aplique una etiqueta class a las mismas. Para seleccionar varias células, pulse una, pulse la tecla **Mayús** y pulse células adicionales.

    Asigne una clase a la célula o células seleccionadas. Si la clase que desea asignar no existe, puede añadirla. Escriba el nombre de clase en el campo **Asignar clase** y pulse **Intro**.

    > **Nota:** No puede añadir más de 10 clases para la regla.

    ![La sección "Crear una regla" que muestra la ventana "Asignar clase" que se abre al pulsar una señal. La ventana muestra un campo donde puede especificar el nombre de una clase nueva, o seleccionar una clase existente de la lista.](images/rule_step6.jpg)

1. Asigne un nombre a la regla.

    El nombre de regla no puede tener más de 64 caracteres.

1. Pulse **Guardar** en el panel Reglas para guardar la regla.
