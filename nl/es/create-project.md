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

    Solo se visualizarán los nombres de las personas que haya asignado al rol del gestor de proyectos desde la página Gestión de cuentas de usuario para la instancia. Consulte [Ensamblaje del equipo](/docs/services/watson-knowledge-studio/team.html) para obtener más información sobre la adición de usuarios.

    > **Nota:** Si tiene una suscripción a un plan gratuito, omita este paso. No puede añadir otros usuarios, por lo que no puede asignar a nadie al rol de gestor de proyectos. No se necesita un gestor de proyectos independiente. Como administrador, puede realizar todas las tareas que un gestor de proyectos realizaría normalmente.

1. Pulse **Crear**.

## Qué hacer a continuación

Una vez creado el espacio de trabajo, puede empezar a configurar los recursos de espacio de trabajo.

Para cambiar la descripción o el nombre del espacio de trabajo, o para añadir o eliminar los gestores de proyectos más adelante, un administrador puede editar el espacio de trabajo. Desde la página de inicio de {{site.data.keyword.knowledgestudioshort}}, pulse el icono **Mostrar menú** en el mosaico del espacio de trabajo y seleccione la opción de menú **Editar**.

**Conceptos relacionados**:

[Carga de recursos desde otro espacio de trabajo](/docs/services/watson-knowledge-studio/exportimport.html)

**Referencia relacionada**:

[Soporte de varios idiomas](/docs/services/watson-knowledge-studio/language-support.html)

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

<table cellpadding="4" cellspacing="0" summary="" border="1" class="simpletable"><tr class="sthead"><th valign="bottom" align="left" id="d25459e252" class="stentry thleft thbot">Tarea</th>
<th valign="bottom" align="left" id="d25459e254" class="stentry thleft thbot">Uso típico</th>
<th valign="bottom" align="left" id="d25459e256" class="stentry thleft thbot">Formatos de entrada soportados</th>
<th valign="bottom" align="left" id="d25459e258" class="stentry thleft thbot">Formatos de salida soportados</th>
<th valign="bottom" align="left" id="d25459e260" class="stentry thleft thbot">Límites y requisitos</th>
</tr>
<tr class="strow"><td valign="top" headers="d25459e252" class="stentry"><p class="p wrapper">Gestión de sistema de tipos</p></td>
<td valign="top" headers="d25459e254" class="stentry"><p class="p wrapper">Cree un sistema de tipos o cargue y modifique un sistema de tipos existente.</p><p class="p">Defina tipos de entidades
y tipos de relaciones para su dominio.</p>
<p class="p">No puede ver una visualización del sistema de tipos.</p>
</td>
<td valign="top" headers="d25459e256" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">Archivo JSON que ha descargado desde un
espacio de trabajo de Watson Knowledge
Studio</p></li>
<li class="li"><p class="p wrapper">Archivo ZIP que ha descargado desde la HAT (Human Annotation Tool, herramienta de anotación humana)</p></li>
</ul>
</td>
<td valign="top" headers="d25459e258" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">JSON</p></li>
</ul>
</td>
<td valign="top" headers="d25459e260" class="stentry"><p class="p wrapper">Para evitar la sobrecarga visual para la anotación humana, defina no más de 50 tipos de entidades y 50
tipos de relaciones.</p><p class="p">Limitación de tamaño de archivo para cargar un sistema de tipos: 20 MB</p>
</td>
</tr>
<tr class="strow"><td valign="top" headers="d25459e252" class="stentry"><p class="p wrapper">Gestión del diccionario</p></td>
<td valign="top" headers="d25459e254" class="stentry"><p class="p wrapper">Cargue un archivo de diccionario CSV en modalidad de solo lectura o un ZIP de diccionarios que ha descargado
desde otro espacio de trabajo.</p><p class="p">Cree un diccionario nuevo y, a continuación, cargue un archivo CSV de entradas de términos o añada
entradas de términos al mismo.</p>
</td>
<td valign="top" headers="d25459e256" class="stentry"><p class="p wrapper">Archivo de diccionario:</p><ul class="ul bullets"><li class="li"><p class="p wrapper">Archivo CSV en formato UTF-8</p></li>
<li class="li"><p class="p wrapper">ZIP de diccionarios descargados desde otro espacio de trabajo</p></li>
</ul><p class="p wrapper">
Archivo de entradas de términos:</p><ul class="ul bullets"><li class="li"><p class="p wrapper">Archivo CSV en formato UTF-8</p></li>
</ul>
</td>
<td valign="top" headers="d25459e258" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">Archivo CSV en formato UTF-8</p></li>
<li class="li"><p class="p wrapper">ZIP de diccionarios para utilizar en otro espacio de trabajo</p></li>
</ul>
</td>
<td valign="top" headers="d25459e260" class="stentry"><p class="p wrapper">Limitaciones de tamaño de archivo:</p><ul class="ul bullets"><li class="li"><p class="p wrapper">1 MB por archivo CSV de entradas de términos</p></li>
<li class="li"><p class="p wrapper">16 MB por archivo de diccionario CSV de solo lectura</p></li>
<li class="li"><p class="p wrapper">15.000 entradas por diccionario, excepto un diccionario de solo lectura</p></li>
<li class="li"><p class="p wrapper">64 diccionarios por espacio de trabajo</p></li>
</ul>
</td>
</tr>
</table>

 {: #wks_formats__datasimpletable_xxj_qr5_2y}

### Modelo de aprendizaje automático

<table cellpadding="4" cellspacing="0" summary="" border="1" class="simpletable"><tr class="sthead"><th valign="bottom" align="left" id="d25459e331" class="stentry thleft thbot">Tarea</th>
<th valign="bottom" align="left" id="d25459e333" class="stentry thleft thbot">Uso típico</th>
<th valign="bottom" align="left" id="d25459e335" class="stentry thleft thbot">Formatos de entrada soportados</th>
<th valign="bottom" align="left" id="d25459e337" class="stentry thleft thbot">Formatos de salida soportados</th>
<th valign="bottom" align="left" id="d25459e339" class="stentry thleft thbot">Límites y requisitos</th>
</tr>
<tr class="strow"><td valign="top" headers="d25459e331" class="stentry"><p class="p wrapper">Gestión de documentos </p></td>
<td valign="top" headers="d25459e333" class="stentry"><p class="p wrapper">Cargue un pequeño subconjunto representativo de documentos </p><p class="p">Cargue documentos que contengan
anotaciones previamente añadidas por un anotador humano, un modelo de aprendizaje automático o un
motor de análisis de UIMA</p>
<p class="p">No puede
ingerir todo el corpus de
IBM Watson Explorer
para calcular los documentos de alto valor para
la anotación. </p>
</td>
<td valign="top" headers="d25459e335" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">Archivo CSV en formato UTF-8</p></li>
<li class="li"><p class="p wrapper">Archivo DOCXML en formato UTF-8</p></li>
<li class="li"><p class="p wrapper">Texto en formato UTF-8</p></li>
<li class="li"><p class="p wrapper">Archivo ZIP que contiene documentos descargados desde otro corpus</p></li>
<li class="li"><p class="p wrapper">Archivo ZIP que contiene documentos en
formato UIMA CAS XMI</p></li>
</ul>
</td>
<td valign="top" headers="d25459e337" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">Archivo de archivado ZIP de documentos</p></li>
</ul>
</td>
<td valign="top" headers="d25459e339" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">40.000 caracteres por documento</p></li>
<li class="li"><p class="p wrapper">10.000 documentos por espacio de trabajo</p></li>
<li class="li"><p class="p wrapper">1.000 conjuntos de documentos (incluidos los conjuntos de anotaciones) por espacio de trabajo</p></li>
</ul>
</td>
</tr>
<tr class="strow"><td valign="top" headers="d25459e331" class="stentry"><p class="p wrapper">Preanotación</p></td>
<td valign="top" headers="d25459e333" class="stentry"><p class="p wrapper">Utilice un diccionario o un
preanotador de {{site.data.keyword.nlushort}}
para proporcionar
un punto de partida para la anotación humana.</p><p class="p">No puede volver a anotar un corpus desde
IBM Watson Discovery Advisor ni
desde IBM Watson Explorer.</p>
</td>
<td valign="top" headers="d25459e335" class="stentry"><p class="p wrapper">Documentos en bruto. </p><p class="p wrapper"><b>Nota:</b> No preanote documentos que un anotador humano ya haya anotado,
o perderá el trabajo realizado por el anotador humano.</p>
</td>
<td valign="top" headers="d25459e337" class="stentry"><p class="p wrapper">Documentos parcialmente anotados</p></td>
<td valign="top" headers="d25459e339" class="stentry"><p class="p wrapper">Ninguno</p></td>
</tr>
<tr class="strow"><td valign="top" headers="d25459e331" class="stentry"><p class="p wrapper">Anotación de documentos</p></td>
<td valign="top" headers="d25459e333" class="stentry"><p class="p wrapper">Gestionar anotación humana</p><p class="p">Anote entidades, relaciones y cadenas de correferencia para crear
datos de campo</p>
</td>
<td valign="top" headers="d25459e335" class="stentry"><p class="p wrapper">Tarea de anotación</p></td>
<td valign="top" headers="d25459e337" class="stentry"><p class="p wrapper">Datos de campo</p></td>
<td valign="top" headers="d25459e339" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">256 tareas de anotación activa por espacio de trabajo</p></li>
</ul>
</td>
</tr>
<tr class="strow"><td valign="top" headers="d25459e331" class="stentry"><p class="p wrapper">Entrenamiento y refinamiento</p></td>
<td valign="top" headers="d25459e333" class="stentry"><p class="p wrapper">Entrene un modelo de aprendizaje automático supervisado para extraer información específica del dominio de texto
no estructurado.</p><p class="p">Evalúe y mejore un modelo de aprendizaje automático supervisado.</p>
<p class="p">No puede crear
un modelo de aprendizaje automático semisupervisado ni no supervisado.</p>
<p class="p">No puede realizar
ingeniería de características extensiva.</p>
</td>
<td valign="top" headers="d25459e335" class="stentry"><p class="p wrapper">No aplicable</p></td>
<td valign="top" headers="d25459e337" class="stentry"><p class="p wrapper">Modelo de aprendizaje automático</p></td>
<td valign="top" headers="d25459e339" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">1 modelo de aprendizaje automático por espacio de trabajo</p></li>
<li class="li"><p class="p wrapper">10 versiones de modelo por espacio de trabajo</p></li>
<li class="li"><p class="p wrapper">El número máximo de espacios de trabajo está determinado por su plan de suscripción.</p></li>
<li class="li"><p class="p wrapper">El número máximo de acciones de entrenamiento que puede realizar por mes está determinado por su plan de suscripción. </p></li>
</ul>
</td>
</tr>
<tr class="strow"><td valign="top" headers="d25459e331" class="stentry"><p class="p wrapper">Publicación</p></td>
<td valign="top" headers="d25459e333" class="stentry"><p class="p wrapper">Publique un modelo de aprendizaje automático que se utilizará para realizar extracción de texto en otras

aplicaciones de Watson. </p></td>
<td valign="top" headers="d25459e335" class="stentry"><p class="p wrapper">No aplicable</p></td>
<td valign="top" headers="d25459e337" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">ID de modelo (para su uso en servicios de AlchemyLanguage
o
Watson Discovery) </p></li>
<li class="li"><p class="p wrapper">Archivo ZIP (para su uso en
IBM Watson Explorer)</p></li>
</ul>
</td>
<td valign="top" headers="d25459e339" class="stentry">
  <p class="p">Para desplegar en AlchemyLanguage,
    debe tener un ID de clave de plan Avanzado
    de AlchemyLanguage válido.</p>
  <p class="p">Para desplegar al servicio de Watson Discovery,
    debe conocer los nombres de instancias y de espacio de {{site.data.keyword.cloud_notm}}
    de servicio.</p>
</td>
</tr>
</table>

### Modelo basado en reglas

<table cellpadding="4" cellspacing="0" summary="" border="1" class="simpletable"><tr class="sthead"><th valign="bottom" align="left" id="d25459e509" class="stentry thleft thbot">Tarea</th>
<th valign="bottom" align="left" id="d25459e511" class="stentry thleft thbot">Uso típico</th>
<th valign="bottom" align="left" id="d25459e513" class="stentry thleft thbot">Formatos de entrada soportados</th>
<th valign="bottom" align="left" id="d25459e515" class="stentry thleft thbot">Formatos de salida soportados</th>
<th valign="bottom" align="left" id="d25459e517" class="stentry thleft thbot">Límites y requisitos</th>
</tr>
<tr class="strow"><td valign="top" headers="d25459e509" class="stentry"><p class="p wrapper">Editor de reglas</p></td>
<td valign="top" headers="d25459e511" class="stentry"><p class="p">Cree o cargue documentos al Editor de reglas desde el que se definen clases, expresiones regulares
y reglas.</p>
</td>
<td valign="top" headers="d25459e513" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">Texto sin formato (añadido en el editor)</p></li>
<li class="li"><p class="p wrapper">Archivo CSV en formato UTF-8</p></li>
<li class="li"><p class="p wrapper">Copiado desde Todos los conjuntos de documentos</p></li>
</ul>
</td>
<td valign="top" headers="d25459e515" class="stentry"><p class="p wrapper">Ninguno</p></td>
<td valign="top" headers="d25459e517" class="stentry"><ul class="ul bullets">
<li class="li"><p class="p wrapper">1 modelo basado en reglas por espacio de trabajo</p></li>
<li class="li"><p class="p wrapper">5.000 caracteres por documento</p></li>
<li class="li"><p class="p wrapper">100 documentos por espacio de trabajo</p></li>
<li class="li"><p class="p wrapper">El tamaño máximo del título del documento es de 256 caracteres</p></li>
<li class="li"><p class="p wrapper">200 reglas por espacio de trabajo</p></li>
<li class="li"><p class="p wrapper">400 clases por espacio de trabajo</p></li>
<li class="li"><p class="p wrapper">100 grupos de expresiones regulares por espacio de trabajo</p></li>
<li class="li"><p class="p wrapper">100 entradas de expresiones regulares por grupo de expresiones regulares</p></li>
<li class="li"><p class="p wrapper">1.000 caracteres por entrada de expresión regular</p></li>
<li class="li"><p class="p wrapper">5 versiones de modelo basado en reglas por espacio de trabajo</p></li>
</ul>
</td>
</tr>
<tr class="strow"><td valign="top" headers="d25459e509" class="stentry"><p class="p wrapper">Publicación</p></td>
<td valign="top" headers="d25459e511" class="stentry"><p class="p wrapper">Publique un modelo basado en reglas que se utilizará para realizar el reconocimiento de patrones en otras
aplicaciones de Watson.</p></td>
<td valign="top" headers="d25459e513" class="stentry"><p class="p wrapper">No aplicable</p></td>
<td valign="top" headers="d25459e515" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">ID de modelo (para su uso en servicios de AlchemyLanguage
o
Watson Discovery) </p></li>
</ul>
</td>
<td valign="top" headers="d25459e517" class="stentry">
  <p class="p">Para desplegar en AlchemyLanguage,
    debe tener un ID de clave de plan Avanzado
    de AlchemyLanguage válido.</p>
  <p class="p">Para desplegar al servicio de Watson Discovery,
    debe conocer los nombres de instancias y de espacio de {{site.data.keyword.cloud_notm}}
    de servicio.</p>
</td>
</tr>
</table>
