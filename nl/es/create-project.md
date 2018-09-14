---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-18"

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

Esta documentación es para {{site.data.keyword.knowledgestudiofull}} en {{site.data.keyword.cloud}}. Para ver la documentación para la versión anterior de {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.IBM_notm}} Marketplace, [pulse este enlace ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/services/knowledge-studio/create-project.html){: new_window}.
{: tip}

# Creación de un espacio de trabajo
{: #create-project}

El primer paso en la creación de un modelo personalizado es crear un espacio de trabajo.
{: shortdesc}

## Acerca de esta tarea

Para cada modelo que desee crear y utilizar, cree un espacio de trabajo único que contenga los artefactos y recursos necesarios para crear el modelo. A continuación, entrene el modelo para producir un modelo personalizado que se pueda desplegar en un servicio externo para su uso.

Antes de crear un espacio de trabajo, responda a estas preguntas:

- **¿Qué tipo de modelo desea crear?**

    - Modelo de aprendizaje automático: Utiliza un enfoque estadístico para encontrar entidades y relaciones en los documentos. Este tipo de modelo puede adaptarse como la cantidad de crecimientos de datos.
    - Modelo basado en reglas: Utiliza un enfoque declarativo para encontrar entidades en documentos. Este tipo de modelo es más previsible, y es más fácil de comprender y mantener. Sin embargo, no aprende de datos nuevos. Solo puede encontrar patrones que se ha enseñado a buscar.

    > **Nota:** También puede crear un espacio de trabajo que contenga tanto un modelo basado en reglas como un modelo de aprendizaje automático.

- **¿Qué servicios utilizará el modelo?**

    Consulte [Integración de servicios de {{site.data.keyword.watson}}](/docs/services/watson-knowledge-studio/index.html#wks_watsoninteg) para obtener información sobre el resto de los servicios de {{site.data.keyword.watson}} con el que se pueden utilizar los modelos personalizados.

## Procedimiento

Para crear un espacio de trabajo, efectúe los pasos siguientes:

1. Inicie sesión como administrador de {{site.data.keyword.knowledgestudioshort}} y pulse **Crear espacio de trabajo**.

    > **Nota:** Las personas con el rol de gestor de proyectos pueden realizar casi todas las tareas, excepto crear un espacio de trabajo. Un administrador debe crear el espacio de trabajo inicialmente y asignar gestores de proyectos al mismo.

1. Dé un nombre al espacio de trabajo. Elija un nombre abreviado que refleje el contenido de dominio o el propósito del modelo. Si es necesario, puede cambiar el nombre del espacio de trabajo más adelante.
1. Identifique el idioma de los documentos de su espacio de trabajo. Los documentos que añada al espacio de trabajo, y los diccionarios que cree o cargue, deben estar en el idioma que especifique.
1. Opcional: Si desea cambiar el señalizador que utiliza la aplicación desde el señalizador basado en aprendizaje automático predeterminado, puede expandir la sección **Opciones avanzadas** y elegir **Señalizadores basados en diccionario**.

    El señalizador predeterminado es más avanzado que el señalizador basado en diccionario; utiliza el aprendizaje automático para identificar las señales de los documentos de origen basadas en el aprendizaje estadístico que ha hecho en el idioma de los documentos de origen. Identifica señales con más precisión porque entiende los patrones de lenguaje más naturales y matizados. El señalizador basado en diccionario identifica señales en función de las reglas del idioma. Consulte [Señalizadores](/docs/services/watson-knowledge-studio/create-project.html#wks_tokenizer) para obtener más detalles.

1. Opcional: Si desea añadir gestores de proyectos al espacio de trabajo, expanda la sección **Opciones avanzadas** y seleccione los nombres de las personas que desee añadir como gestores de proyectos de la lista. El administrador puede añadir o eliminar gestores de proyectos más adelante editando el espacio de trabajo.

    Solo se visualizarán los nombres de las personas que haya asignado al rol del gestor de proyectos desde la página Gestión de cuentas de usuario para la instancia. Consulte [Ensamblaje de un equipo](/docs/services/watson-knowledge-studio/team.html) para obtener más información sobre la adición de usuarios.

    > **Nota:** Si tiene una suscripción a un plan Lite, omita este paso. No puede añadir otros usuarios, por lo que no puede asignar a nadie al rol de gestor de proyectos. No se necesita un gestor de proyectos independiente. Como administrador, puede realizar todas las tareas que un gestor de proyectos realizaría normalmente.

1. Pulse **Crear**.

## Qué hacer a continuación

Una vez creado el espacio de trabajo, puede empezar a configurar los recursos de espacio de trabajo.

Para cambiar la descripción o el nombre del espacio de trabajo, o para añadir o eliminar los gestores de proyectos más adelante, un administrador puede editar el espacio de trabajo. Desde la página de inicio de {{site.data.keyword.knowledgestudioshort}}, pulse el icono **Mostrar menú** en el mosaico del espacio de trabajo y seleccione la opción de menú **Editar**.

**Conceptos relacionados**:

[Carga de recursos desde otro espacio de trabajo](/docs/services/watson-knowledge-studio/exportimport.html)

**Referencia relacionada**:

[Soporte de idioma](/docs/services/watson-knowledge-studio/language-support.html)

## Señalizadores
{: #wks_tokenizer}

Un señalizador agrupa caracteres en señales, y señales en frases. Una señal es equivalente en parte a una palabra.

Las acciones que un señalizador debe realizar para identificar las señales de un documento difieren en función del idioma del documento. En inglés, las señales suelen ser equivalentes a las palabras porque se delimitan mediante espacios en blanco en una frase. Sin embargo, no siempre coinciden one-to-one con palabras; otros elementos textuales se consideran señales en algunas situaciones. Por ejemplo, la puntuación al final de una frase se considera una señal, y las contracciones a menudo se expanden en dos señales. En idiomas que no utilizan espacios en blanco, como el chino, se utilizan algoritmos estadísticos más complicados para identificar las señales.

El proceso de señalización es importante porque determina los grupos de caracteres que los usuarios pueden resaltar para anotación en el editor de datos de campo. Las anotaciones de menciones de entidades y de relaciones se alinean generalmente con los límites de señales, y se deben etiquetar dentro de una frase; no pueden abarcar los límites de las frases.

### Tipos soportados

{{site.data.keyword.knowledgestudioshort}} da soporte a los siguientes señalizadores:

- **Señalizador basado en aprendizaje automático (valor predeterminado)**

    Este es un señalizador más avanzado que identifica las señales de los documentos de origen basadas en el aprendizaje estadístico que ha hecho en el idioma de los documentos de origen. Este señalizador encuentra señales que capturan los patrones más naturales y matizados del lenguaje. No puede personalizar este señalizador.

- **Señalizador basado en diccionario**

    Este señalizador se basa en diccionarios lingüísticos. Encuentra señales que siguen las reglas del idioma del documento de origen. Solo los usuarios avanzados pueden personalizar este señalizador.

Debe seleccionar el señalizador que desea utilizar al crear el espacio de trabajo. No puede cambiar a un señalizador distinto más tarde. Para obtener mejores resultados, utilice el señalizador predeterminado. Solo los usuarios avanzados que deseen modificar el comportamiento del señalizador mediante un mecanismo de diccionario determinista pueden elegir el señalizador basado en diccionario. Podrán entonces personalizarlo añadiendo entradas nuevas al diccionario. Sin embargo, la personalización debe realizarse cuidadosamente porque cuando se añaden palabras nuevas al diccionario, los cambios pueden afectar al modelo de aprendizaje automático de formas no deseadas.

## Resumen de entradas, salidas y limitaciones
{: #wks_formats}

Diferentes fases de desarrollo de modelos requieren diferentes entradas y producen resultados diferentes.

Para cada etapa del proceso de desarrollo de modelos, esta tabla resume las actividades típicas que realiza, los formatos de archivos de entrada soportados, los resultados que se pueden producir, y cualquier límite de tamaño u otros requisitos.

### Todos los tipos de modelos

<table summary="Esta tabla proporciona un resumen de la entrada, la salida y las limitaciones de todos los tipos de modelo.">
  <caption>Tabla 1. Todos los tipos de modelo</caption>
  <tr>
    <th style="vertical-align:bottom; text-align:left" id="d25459e252">
      Tarea
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e254">
      Uso típico
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e256">
      Formatos de entrada soportados
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e258">
      Formatos de salida soportados
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e260">
      Límites y requisitos
    </th>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e252">
      <p>Gestión de sistema de tipos</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e254">
      <p>Cree un sistema de tipos o cargue y modifique un sistema de tipos existente.</p>
      <p>Defina tipos de entidades
y tipos de relaciones para su dominio.</p>
      <p>No puede ver una visualización del sistema de tipos.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e256">
      <ul>
        <li>
          <p>Archivo JSON que ha descargado desde un espacio de trabajo de {{site.data.keyword.knowledgestudioshort}}</p>
        </li>
        <li>
          <p>Archivo ZIP que ha descargado desde la HAT (Human Annotation Tool, herramienta de anotación humana)</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e258">
      <ul>
        <li>
          <p>JSON</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e260">
      <p>Para evitar la sobrecarga visual para la anotación humana, defina no más de 50 tipos de entidades y 50
tipos de relaciones.</p>
      <p>Limitación de tamaño de archivo para cargar un sistema de tipos: 20 MB</p>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e252">
      <p>Gestión del diccionario</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e254">
      <p>Cargue un archivo de diccionario CSV en modalidad de solo lectura o un ZIP de diccionarios que ha descargado
desde otro espacio de trabajo.</p>
      <p>Cree un diccionario nuevo y, a continuación, cargue un archivo CSV de entradas de términos o añada
entradas de términos al mismo.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e256">
      <p>Archivo de diccionario:</p>
      <ul>
        <li>
          <p>Archivo CSV en formato UTF-8</p>
        </li>
        <li>
          <p>ZIP de diccionarios descargados desde otro espacio de trabajo</p>
        </li>
      </ul>
      <p>Archivo de entradas de términos:</p>
      <ul>
        <li>
          <p>Archivo CSV en formato UTF-8</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e258">
      <ul>
        <li>
          <p>Archivo CSV en formato UTF-8</p>
        </li>
        <li>
          <p>ZIP de diccionarios para utilizar en otro espacio de trabajo</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e260">
      <p>Limitaciones de tamaño de archivo:</p>
      <ul>
        <li>
          <p>1 MB por archivo CSV de entradas de términos</p>
        </li>
        <li>
          <p>16 MB por archivo de diccionario CSV de solo lectura</p>
        </li>
        <li>
          <p>15.000 entradas por diccionario, excepto un diccionario de solo lectura</p>
        </li>
        <li>
          <p>64 diccionarios por espacio de trabajo</p>
        </li>
      </ul>
    </td>
  </tr>
</table>

 {: #wks_formats__datasimpletable_xxj_qr5_2y}

### Modelo de aprendizaje automático

<table summary="Esta tabla proporciona un resumen de la entrada, la salida y las limitaciones del modelo de aprendizaje automático.">
  <caption>Tabla 2. Modelo de aprendizaje automático</caption>
  <tr>
    <th style="vertical-align:botton; text-align:left" id="d25459e331">Tarea</th>
    <th style="vertical-align:botton; text-align:left" id="d25459e333">Uso típico</th>
    <th style="vertical-align:botton; text-align:left" id="d25459e335">Formatos de entrada soportados</th>
    <th style="vertical-align:botton; text-align:left" id="d25459e337">Formatos de salida soportados</th>
    <th style="vertical-align:botton; text-align:left" id="d25459e339">Límites y requisitos</th>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>Gestión de documentos </p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
      <p>Cargue un pequeño subconjunto representativo de documentos</p>
      <p>Cargue documentos que contengan
anotaciones previamente añadidas por un anotador humano, un modelo de aprendizaje automático o un
motor de análisis de UIMA</p>
      <p>No puede ingerir todo el corpus de {{site.data.keyword.ibmwatson_notm}} Explorer para calcular los documentos de alto valor para la anotación.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <ul>
        <li>
          <p>Archivo CSV en formato UTF-8</p>
        </li>
        <li>
          <p>Texto en formato UTF-8</p>
        </li>
        <li>
          <p>Archivo ZIP que contiene documentos descargados desde otro corpus</p>
        </li>
        <li>
          <p>Archivo ZIP que contiene documentos en
formato UIMA CAS XMI</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <ul>
        <li>
          <p>Archivo de archivado ZIP de documentos</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <ul>
        <li>
          <p>40.000 caracteres por documento</p>
        </li>
        <li>
          <p>10.000 documentos por espacio de trabajo</p>
        </li>
        <li>
          <p>1.000 conjuntos de documentos (incluidos los conjuntos de anotaciones) por espacio de trabajo</p>
        </li>
      </ul>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>Preanotación</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
       <p>Utilice un diccionario o un
preanotador de {{site.data.keyword.nlufull}}
para proporcionar
un punto de partida para la anotación humana.</p>
       <p>No puede volver a anotar un corpus desde {{site.data.keyword.ibmwatson_notm}} Explorer.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <p>Documentos en bruto.</p>
      <p><b>Nota:</b> No preanote documentos que un anotador humano ya haya anotado,
o perderá el trabajo realizado por el anotador humano.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <p>Documentos parcialmente anotados</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <p>Ninguno</p>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>Anotación de documentos</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
      <p>Gestionar anotación humana</p><p>Anote entidades, relaciones y cadenas de correferencia para crear
datos de campo</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <p>Tarea de anotación</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <p>Datos de campo</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <ul>
        <li>
          <p>256 tareas de anotación activa por espacio de trabajo</p>
        </li>
      </ul>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>Entrenamiento y refinamiento</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
      <p>Entrene un modelo de aprendizaje automático supervisado para extraer información específica del dominio de texto
no estructurado.</p><p>Evalúe y mejore un modelo de aprendizaje automático supervisado.</p>
      <p>No puede crear
un modelo de aprendizaje automático semisupervisado ni no supervisado.</p>
      <p>No puede realizar
ingeniería de características extensiva.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <p>No aplicable</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <p>Modelo de aprendizaje automático</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <ul>
        <li>
          <p>1 modelo de aprendizaje automático por espacio de trabajo</p>
        </li>
        <li>
          <p>10 versiones de modelo por espacio de trabajo</p>
        </li>
        <li>
          <p>El número máximo de espacios de trabajo está determinado por su plan de suscripción.</p>
        </li>
        <li>
          <p>El número máximo de acciones de entrenamiento que puede realizar por mes está determinado por su plan de suscripción.</p>
        </li>
      </ul>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>Publicación</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
      <p>Publique un modelo de aprendizaje automático que se utilizará para realizar extracción de texto en otras aplicaciones de {{site.data.keyword.watson}}.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <p>No aplicable</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <ul>
        <li>
          <p>ID de modelo (para utilizarlo en {{site.data.keyword.nlufull}} o {{site.data.keyword.discoveryfull}})</p>
        </li>
        <li>
          <p>Archivo ZIP (para su uso en {{site.data.keyword.ibmwatson_notm}} Explorer)</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <p>Para desplegar en los servicios de {{site.data.keyword.watson}}, debe conocer los nombres de instancias y de espacio de servicio de {{site.data.keyword.cloud_notm}}.</p>
    </td>
  </tr>
</table>

### Modelo basado en reglas

<table summary="Esta tabla proporciona un resumen de la entrada, la salida y las limitaciones del modelo basado en reglas.">
  <caption>Tabla 3. Modelo basado en reglas</caption>
  <tr>
    <th style="vertical-align:bottom; text-align:left" id="d25459e509">
      Tarea
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e511">
      Uso típico
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e513">
      Formatos de entrada soportados
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e515">
      Formatos de salida soportados
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e517">
      Límites y requisitos
    </th>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e509">
      <p>Editor de reglas</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e511">
      <p>Cree o cargue documentos en el editor de reglas desde el que se definen clases, expresiones regulares y reglas.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e513">
      <ul>
        <li>
          <p>Texto sin formato (añadido en el editor)</p>
        </li>
        <li>
          <p>Archivo CSV en formato UTF-8</p>
        </li>
        <li>
          <p>Copiado desde Todos los conjuntos de documentos</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e515">
      <p>Ninguno</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e517">
      <ul>
        <li>
          <p>1 modelo basado en reglas por espacio de trabajo</p>
        </li>
        <li>
          <p>5.000 caracteres por documento</p>
        </li>
        <li>
          <p>100 documentos por espacio de trabajo</p>
        </li>
        <li>
          <p>El tamaño máximo del título del documento es de 256 caracteres</p>
        </li>
        <li>
          <p>200 reglas por espacio de trabajo</p>
        </li>
        <li>
          <p>400 clases por espacio de trabajo</p>
        </li>
        <li>
          <p>100 grupos de expresiones regulares por espacio de trabajo</p>
        </li>
        <li>
          <p>100 entradas de expresiones regulares por grupo de expresiones regulares</p>
        </li>
        <li>
          <p>1.000 caracteres por entrada de expresión regular</p>
        </li>
        <li>
          <p>5 versiones de modelo basado en reglas por espacio de trabajo</p>
        </li>
      </ul>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e509">
      <p>Publicación</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e511">
      <p>Publique un modelo basado en reglas que se utilizará para realizar el reconocimiento de patrones en otras aplicaciones de {{site.data.keyword.watson}}.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e513">
      <p>No aplicable</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e515">
      <ul>
        <li>
          <p>ID de modelo (para utilizarlo en {{site.data.keyword.nlufull}} o {{site.data.keyword.discoveryfull}})</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e517">
      <p>Para desplegar en los servicios de {{site.data.keyword.watson}}, debe conocer los nombres de instancias y de espacio de servicio de {{site.data.keyword.cloud_notm}}.</p>
    </td>
  </tr>
</table>
