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

Esta documentación es para {{site.data.keyword.knowledgestudiofull}} en {{site.data.keyword.cloud}}. Para ver la documentación para la versión anterior de {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.IBM_notm}} Marketplace, [pulse este enlace ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/services/knowledge-studio/improve-ml.html){: new_window}.
{: tip}

# Cómo mejorar el modelo de aprendizaje automático
{: #improve-ml}

Después de determinar áreas en las que el modelo está teniendo problemas, adopte medidas para mejorar su rendimiento.
{: shortdesc}

## Creación de versiones de modelos
{: #wks_maversions}

Después de crear un modelo de aprendizaje automático, puede realizar una instantánea para mantener una versión de copia de seguridad de los recursos actuales en caso de que desee restaurar los recursos en una iteración futura.

### Acerca de esta tarea

La puntuación de F1 proporciona una indicación de la calidad del modelo. Si los resultados de rendimiento de modelo son buenos, puede que desee almacenar una versión del componente antes de cambiar ninguno de los recursos. Si los cambios que realice dan lugar a una peor calidad, puede revertir a una versión que haya almacenado. Al revertir a una versión anterior, todas las tareas de anotación se archivarán porque ya no son válidas.

Puede tener un máximo de 10 versiones de un espacio de trabajo. Si llega a ese límite, suprima versiones anteriores o versiones que ya no necesite antes de crear una nueva versión.

Al crear una nueva versión, se capturarán los siguientes recursos:

- Sistema de tipos
- Corpus
- Datos de campo
- Modelo de aprendizaje automático
- Resultados de evaluación del modelo de aprendizaje automático

Los siguientes recursos están excluidos:

- Las tareas de anotación, porque son temporales por diseño, y solo se utilizan para determinar los datos de campo
- Los diccionarios, porque los diccionarios pueden ser grandes, y diversos tipos de diccionarios se gestionan de formas distintas

### Procedimiento

Para crear y restaurar versiones del modelo de aprendizaje automático:

1. Inicie sesión como un administrador o gestor de proyectos de {{site.data.keyword.knowledgestudioshort}}, y seleccione su espacio de trabajo.
1. Seleccione **Gestión de modelos** > **Rendimiento**. Se mostrarán las estadísticas de rendimiento sobre la versión actual, etiquetada como versión 1.0.
1. Para realizar una instantánea de la versión actual, en el separador **Gestión de modelos** > **Versiones** > **Aprendizaje automático**, pulse **Realizar instantánea**. Los recursos de la versión 1.0 están bloqueados, y una nueva versión, etiquetada como 1.1, se convierte en la versión actual. Para cada nueva versión que cree, el número de versión menor se aumenta, por ejemplo, 1.0 se convierte en 1.1 y luego se convierte en 1.2.
1. Revise los recursos de espacio de trabajo según sea necesario, reentrene y reevalúe el modelo.
1. Si está satisfecho con los resultados de rendimiento y desea almacenar la nueva versión antes de realizar cambios en el futuro, cree otra versión. Siga revisando los recursos y reentrenando el modelo como sea necesario, creando una nueva versión para cada iteración que desee conservar.
1. Si los resultados de rendimiento son peores, y desea volver a una versión anterior antes de probar más:

    1. Abra el separador **Activos y herramientas** > **Preanotadores** > **Diccionarios** y descargue cualquier diccionario que desee volver a utilizar en el modelo restaurado.
    1. Vuelva al separador **Gestión de modelos** > **Versiones** > **Aprendizaje automático** y pulse **Promocionar** para la versión que desea restaurar. La versión que promocione se convertirá en la versión actual, y el número de versión cambia a 2.0. Al promocionar una versión, el número de versión principal se incrementa y el número de versión menor se convierte en 0, por ejemplo, 1.1 se convierte en 2.0.
    1. Abra el separador **Diccionarios** y cargue los diccionarios que ha descargado.
    1. Si la prueba de la nueva versión requiere cambios en los datos de campo, abra el separador **Activos y herramientas** > **Documentos** > **Tareas** y cree una nueva tarea de anotación.

## Modificación de un sistema de tipos sin perder anotaciones humanas
{: #wks_projtypesysmod}

Es posible que tenga que realizar modificaciones al entrenar un modelo, en función de las estadísticas de rendimiento. Pero, en general, desea que el sistema de tipos esté lo más cerca posible del final antes de empezar las tareas de anotación a gran escala. Si cambia el sistema de tipos después de que los anotadores humanos comenzaran su trabajo, deben revisar los documentos que han anotado. Deben evaluar la aplicabilidad de los cambios del sistema de tipos.

### Acerca de esta tarea

Este proceso propaga el sistema de tipos actual, los atajos de teclado del editor de datos de campo, y la configuración de colores en todos los conjuntos de documentos de una tarea.

### Procedimiento

Para modificar el sistema de tipos sin perder el trabajo realizado por los anotadores humanos:

1. Cambie el sistema de tipos. Por ejemplo, puede añadir o eliminar tipos de entidades o tipos de relaciones.
1. Decida si desea propagar los cambios a tareas de anotación humana existente.
1. En el separador **Activos y herramientas** > **Documentos** > **Tareas**, abra cada tarea que desee actualizar y pulse **Aplicar actualizaciones del sistema de tipos**.

    Si ha eliminado tipos de entidades o tipos de relaciones del sistema de tipos, todas las apariciones de dichos tipos se resaltan en gris en los documentos. Estos tipos no válidos los ignora el modelo de aprendizaje automático. No le impiden enviar y aprobar conjuntos de documentos.

1. Proporcione detalles a los anotadores humanos sobre lo que ha cambiado en el sistema de tipos.
1. Solicite a los anotadores humanos que actualicen sus documentos para que reflejen los cambios en el sistema de tipos. Por ejemplo, si ha añadido nuevos tipos de entidades o tipos de relaciones, deben revisar sus documentos y anotarlos adecuadamente.

    > **Nota:** Si la tarea contiene documentos completados, los anotadores humanos no podrán alterar los documentos para evaluar los cambios del sistema de tipos hasta que vuelvan a estar en un estado editable. Para convertirse en editables, solicite a los anotadores humanos que envíen los conjuntos de documentos para que pueda rechazarlos.

**Conceptos relacionados**:

[Sistemas de tipos](/docs/services/watson-knowledge-studio/typesystem.html#wks_typesystem)

## Gestión de conjuntos de documentos
{: #wks_mamanagedata}

Utilice los conjuntos de datos correctos para probar y entrenar el modelo en el momento correcto.

Los documentos que añada al sistema deben asignarse a los siguientes conjuntos de datos de nivel de sistema cuando se crea un modelo de aprendizaje automático:

- **Conjunto de entrenamiento**

    Un conjunto de documentos que se han anotado a través de preanotación o a través de anotadores humanos que se utiliza para entrenar el modelo. El objetivo del conjunto de entrenamiento es enseñar al modelo de aprendizaje automático anotaciones correctas, que incluye la enseñanza del modelo a través de texto que no se ha anotado.

- **Conjunto de pruebas**

    Un conjunto de documentos anotados que se utiliza para probar el modelo entrenado. Después de ejecutar una prueba en el conjunto de pruebas, realice un análisis de errores con objetivo de diagnóstico detallado de los resultados. Cerrar el análisis le ayuda a encontrar debilidades en el modelo actual que puede abordarse.

- **Conjunto ciego**

    Un conjunto de documentos anotados que se reserva y se utiliza para probar el sistema periódicamente después de que se hayan producido varias iteraciones de prueba y de mejora. Para evitar que se corrompa la exactitud (por ejemplo, haciendo cambios basados únicamente en anotaciones en documentos conocidos), los datos ciegos deberían ser datos que los usuarios no hayan visto previamente implicados en la creación del modelo. Los resultados notificados solo deberían provenir de las pruebas que se ejecutan en datos ciegos. Después de ejecutar una prueba en el conjunto ciego, mire solo las puntuaciones de nivel más alto, como por ejemplo la mención general y las puntuaciones de F1 de relación. No quiera saber demasiados detalles sobre el rendimiento o esto podría influir en las mejoras que desea realizar en el modelo.

El objetivo de {{site.data.keyword.knowledgestudioshort}} es permitir que grandes equipos trabajen juntos para crear modelos. Como tal, presupone que los modelos los produce un equipo que incluye un grupo de anotadores humanos y una persona independiente o un grupo de personas que crea y prueba el modelo, y que realiza mejoras en el mismo. Debido a esta suposición, la aplicación se configura para enviar una agrupación de documentos igualmente proporcionada desde un conjunto de documentos único en los conjuntos de prueba, de entrenamiento y ciegos. Sin embargo, si el equipo no está segregado (si las personas que hacen anotación humana también están revisando los resultados de la prueba del modelo en detalle, por ejemplo), podría necesitar cambiar la asignación de documentos en estos conjuntos para separar más explícitamente los documentos que se están utilizando en cada uno.

### ¿Por qué necesito un conjunto ciego?

Puesto que utiliza datos de prueba para evaluar la exactitud en detalle, conocerá los documentos y sus características después de un tiempo. Por ejemplo, empiece a saber qué tipos de entidades, tipos de relaciones y tipos de texto de los documentos entiende mejor el modelo de aprendizaje automático, y cuáles no. Esta información es importante porque ayuda a centrarse en realizar las mejoras correctas: a refinar el sistema de tipos, a suplementar los datos de entrenamiento para llenar lagunas, o a añadir diccionarios, por ejemplo. A medida que los documentos de prueba se utilizan iterativamente para mejorar el modelo, pueden empezar a influir en el entrenamiento del modelo indirectamente. Por eso el conjunto "ciego" de documentos sea tan importante.

### ¿Cómo controlo qué documentos están asignados a un conjunto?

Cuando se crea un modelo de aprendizaje automático, debe especificar la proporción de documentos del conjunto para asignar a los conjuntos de entrenamiento, de prueba o ciegos. {{site.data.keyword.knowledgestudioshort}} aplica automáticamente una proporción de 70/23/7 a los conjuntos de documentos que utiliza para crear un modelo de aprendizaje automático. Puede cambiar estos valores.

- Para añadir un conjunto que fue anotado por humanos en el conjunto de entrenamiento, especifique una proporción de desglose de 100/0/0.
- Después de entrenar con un conjunto, podrá utilizarlo para las pruebas. Para utilizar un conjunto de documentos solo para las pruebas, especifique una proporción de desglose de 0/100/0.
- Añada solo un conjunto de documentos que no se haya utilizado nunca para entrenar o probar en el conjunto ciego. Para ello, especifique una proporción de desglose de 0/0/100 para el conjunto de documentos.

Planifique dejar de utilizar un conjunto ciego tras unas iteraciones. Cuando más se utiliza un conjunto ciego, menos "ciego" será. Lo mismo ocurre con los datos de prueba. En lugar de descartar los conjuntos, puede migrarlos para que sirvan un nuevo propósito. Siga este flujo de migración:

```
blind --> test --> train
```
{: screen}

A medida que se migren los conjuntos, podrá añadir conjuntos de documentos nuevos y no vistos como datos ciegos y datos de prueba. Pero asegúrese de conservar un método para evaluar la exactitud entre versiones de modelos. Una forma de establecer una línea base es ejecutar una versión anterior del modelo en el nuevo conjunto de documentos. Los resultados de esta ejecución le da una base de comparación con ejecuciones de modelos más nuevos en esos mismos conjuntos.
