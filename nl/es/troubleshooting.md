---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-13"

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

Esta documentación es para {{site.data.keyword.knowledgestudiofull}} en {{site.data.keyword.cloud}}. Para ver la documentación para la versión anterior de {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.IBM_notm}} Marketplace, [pulse este enlace ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/services/knowledge-studio/troubleshooting.html){: new_window}.
{: tip}

# Resolución de problemas, soporte y preguntas frecuentes
{: #troubleshooting}

Para aislar y resolver los problemas con los productos de {{site.data.keyword.IBM_notm}}, puede utilizar la información de resolución de problemas y soporte técnico. Esta información contiene instrucciones para utilizar los recursos de determinación de problemas que se proporcionan con los productos de {{site.data.keyword.IBM_notm}}, incluido {{site.data.keyword.knowledgestudiofull}}.
{: shortdesc}

## Técnicas para la resolución de problemas
{: #ts_overview}

La *resolución de problemas* es un procedimiento sistemático para resolver un problema. El objetivo de la resolución de problemas es determinar por
qué algo no funciona del modo esperado y cómo resolverlo. Algunas técnicas comunes pueden ayudarle con la tarea de resolución de problemas.

El primer paso del proceso de resolución de problemas consiste en describir por
completo el problema. Las descripciones de problemas le ayudan a usted y al representante del servicio de asistencia técnica de {{site.data.keyword.IBM_notm}} a saber por dónde empezar para encontrar la causa del problema. En este paso debe plantearse algunas cuestiones básicas:

- ¿Cuáles son los síntomas del problema?
- ¿Dónde se produce el problema?
- ¿Cuándo se produce el problema?
- ¿En qué condiciones se produce el problema?
- ¿Puede reproducirse el problema?

Las respuestas a estas preguntas normalmente conducen a una buena descripción del
problema, que a su vez puede llevarle a una resolución.

### ¿Cuáles son los síntomas del problema?
{: #ts_overview_symptoms}

Al empezar a describir un problema, la pregunta más evidente es "¿Cuál es el problema?". Esta pregunta puede parecer sencilla; sin embargo, puede dividirla en varias más precisas que creen una imagen más descriptiva del problema. Estas preguntas pueden incluir:

- ¿Quién o qué está informando del problema?
- ¿Cuáles son los códigos y los mensajes de error?
- ¿Cómo falla el sistema? Por ejemplo, ¿es un bucle, un cuelgue, un
bloqueo, una degradación del rendimiento o un resultado incorrecto?

### ¿Dónde se produce el problema?
{: #ts_overview_where}

Determinar dónde se origina el problema no es siempre fácil, pero es uno de los pasos más importantes para resolver un problema. Muchas capas de tecnología pueden existir entre los componentes de informe y los componentes anómalos. Las redes, discos y controladores son sólo algunos de los componentes que deben tenerse en cuenta al investigar un problema.

Las siguientes preguntas le ayudarán a centrarse en dónde se produce el problema para aislar la capa del problema:

- ¿El problema es específico de una plataforma o sistema operativo, o por el contrario es común en varias plataformas o sistemas operativos?
- ¿Están soportados el entorno y la configuración actuales?
- ¿Tienen el problema todos los usuarios?
- (Para instalaciones multisitio). ¿Tienen todos los sitios el problema?

Si una capa notifica el problema, el problema no necesariamente se ha creado en esa capa. Parte de la identificación de dónde se origina un problema
es comprender el entorno en el que existe. Dedique tiempo a describir completamente el entorno del problema, incluido el sistema operativo y la versión, todo el software y las versiones correspondientes, y la información de hardware. Confirme que está ejecutando dentro de un entorno que es una configuración admitida; muchos problemas pueden deberse a niveles incompatibles de software que no se han planeado para que se ejecuten juntos, o cuyo funcionamiento conjunto no se ha comprobado totalmente.

### ¿Cuándo se produce el problema?
{: #ts_overview_when}

Desarrolle una línea temporal detallada de sucesos que den como resultado un error, especialmente para los casos que sólo ocurran una vez. Puede desarrollar fácilmente una línea temporal realizando un retroceso: empiece en el momento en que se informó del error (tan detalladamente como sea posible, incluso hasta el milisegundo) y retroceda por los registros y la información disponibles. Normalmente sólo deberá llegar hasta el primer suceso sospechoso que encuentre en un registro de diagnóstico.

Para desarrollar una línea temporal detallada de sucesos, responda a estas preguntas:

- ¿El problema sucede una sola vez en una determinada hora del día o de la noche?
- ¿Con qué frecuencia ocurre el problema?
- ¿Qué secuencia de sucesos antecede al momento en que se informa del problema?
- ¿Sucede el problema después de un cambio de entorno como, por ejemplo, al actualizar
o instalar software o hardware?

La respuesta a este tipo de preguntas puede proporcionar un marco de referencia en el que investigar el problema.

### ¿En qué condiciones se produce el problema?
{: #ts_overview_conditions}

Saber qué sistemas y aplicaciones se están ejecutando en el momento en que se produce un problema es una parte importante de la resolución de problemas. Estas preguntas sobre el entorno pueden ayudarle a identificar la causa raíz del problema:

- ¿Se produce siempre el problema cuando se está ejecutando la misma tarea?
- ¿Debe producirse una determinada secuencia de sucesos para que ocurra el problema?
- ¿Hay otras aplicaciones que den error al mismo tiempo?

La respuesta a este tipo de preguntas le ayudará a conocer el entorno en el que se produce el problema y
establecer correlaciones de dependencias. Recuerde que aunque varios problemas hayan ocurrido al mismo tiempo estos no están necesariamente relacionados.

### ¿Puede reproducirse el problema?
{: #ts_overview_reproduce}

Desde el punto de vista de la resolución de problemas,
un problema ideal es el que se puede reproducir. Normalmente, cuando un problema se puede reproducir, dispone de un
conjunto de herramientas o procedimientos más grande para ayudarle en la investigación. Por lo tanto, los problemas que puede reproducir suelen ser más fáciles de depurar y resolver.

No obstante, los problemas que puede reproducir pueden tener una desventaja: si el problema tiene un impacto empresarial importante, no desea que se repita. Si es posible, vuelva a crear el problema en un entorno de prueba o de desarrollo, que
habitualmente ofrecen más flexibilidad y control durante la investigación.

- ¿Se puede volver a crear el problema en un sistema de prueba?
- ¿Hay varios usuarios o aplicaciones que encuentren el mismo tipo de problema?
- ¿Se puede recrear el problema mediante la ejecución de un único mandato, un conjunto
de mandatos, una aplicación concreta?

## No se puede crear una instancia en el plan Lite
{: #wks_ts_lite}

### Problema
{: #wks_ts_lite_problem}

Intenta crear una instancia de {{site.data.keyword.knowledgestudioshort}} y ve el mensaje de error, `Error 331: No se puede procesar su solicitud. Vuelva a intentarlo más tarde o póngase en contacto con el centro de atención al cliente de {{site.data.keyword.IBM_notm}}.`

### Causas
{: #wks_ts_lite_causes}

{{site.data.keyword.knowledgestudioshort}} no permite más de un plan Lite por organización.

### Resolución del problema
{: #wks_ts_lite_resolve}

Cree una cuenta no incluida en la organización.

Si necesita utilizar su cuenta actual para una instancia de {{site.data.keyword.knowledgestudioshort}} en un plan Lite y la cuenta de usuario está asociada con una cuenta de pago, puede crear un caso. Para obtener más información, consulte [Ponerse en contacto con el soporte de {{site.data.keyword.IBM_notm}}](/docs/services/watson-knowledge-studio/troubleshooting.html#ts_contactingibmsupport).

Si necesita utilizar su cuenta actual para una instancia de {{site.data.keyword.knowledgestudioshort}} en un plan Lite y la cuenta de usuario no está asociada con una cuenta de pago, publique su problema en [{{site.data.keyword.IBM_notm}} developerWorks Answers ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.ibm.com/answers/topics/watson-knowledge-studio/){: new_window}. Etiquete la pregunta, **WATSON-KNOWLEDGE-STUDIO**.

## No se puede acceder a la aplicación
{: #wks_ts_access}

Descubra cómo otorgar a los usuarios acceso a {{site.data.keyword.knowledgestudioshort}}, y aborde los problemas de acceso comunes.

Debe tener credenciales de registro de usuarios de {{site.data.keyword.IBM_notm}} para solicitar una instancia de {{site.data.keyword.IBM_notm}} {{site.data.keyword.knowledgestudioshort}}.

### Administrador
{: #wks_ts_access_administrator}

Cada instancia de {{site.data.keyword.knowledgestudioshort}} tiene un rol de administrador asociado con la misma. Se otorga el rol de administrador automáticamente a la persona que originalmente se registró para utilizar la aplicación. El administrador puede invitar a otras personas.

Para obtener información sobre cómo invitar a personas a utilizar la instancia de la aplicación, consulte [Ensamblaje del equipo](/docs/services/watson-knowledge-studio/team.html).

### Anotador humano
{: #wks_ts_access_annotator}

Si se le ha invitado a la instancia de {{site.data.keyword.knowledgestudioshort}} de alguien para servir como anotador humano, es probable que reciba una invitación por correo electrónico. En primer lugar, debe registrarse con {{site.data.keyword.IBM_notm}} si no tiene ya las credenciales de registro de {{site.data.keyword.IBM_notm}}. Una vez que se registre con {{site.data.keyword.IBM_notm}} y acepte la invitación, se le dará acceso a la instancia. Sin embargo, después de que se le dé acceso y antes de empezar a anotar documentos, el administrador o un gestor de proyectos de la instancia debe añadirle a un espacio de trabajo y asignarle una tarea de anotación. No podrá realizar ninguna acción en la instancia de {{site.data.keyword.knowledgestudioshort}} hasta que se le asigne una tarea. Para anotar documentos, utilice el editor de datos de campo. Utilice un navegador Google Chrome para el mejor rendimiento.

Para obtener ayuda al utilizar el editor de datos de campo, consulte [Anotación de documentos](/docs/services/watson-knowledge-studio/user-guide.html).

## Recopilación de datos
{: #content}

Para los planes Estándar (Lite, Estándar, Standard, Pro), de forma predeterminada, {{site.data.keyword.knowledgestudioshort}} utiliza los datos de cliente para mejorar el servicio. Estos datos se utilizan solo en conjunto. Los datos de cliente no se comparten ni se hacen públicos.

Si tiene el rol Admin, puede cambiar este comportamiento predeterminado seleccionando el valor de recopilación de datos en la página Detalles de servicio.

Para los planes Premium y las cuentas dedicadas, {{site.data.keyword.knowledgestudioshort}} no utiliza datos de cliente para mejorar el servicio.

Para obtener más información, consulte [la descripción de servicio de {{site.data.keyword.knowledgestudioshort}} más reciente ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/software/sla/sladb.nsf/searchsaas/?searchview&searchorder=4&searchmax=0&query=Knowledge+Studio){: new_window}.

## Servicios y características experimentales: ¿Qué significa *experimental*?
{: #experimental}

{{site.data.keyword.IBM_notm}} publica servicios y características experimentales para que los pruebe. Estos servicios pueden ser inestables, cambiar frecuentemente de formas no compatibles con las versiones anteriores, y pueden ser interrumpidos con avisando con poca antelación. No se recomienda utilizar estos servicios y características en entornos de producción.

Para obtener más información sobre los servicios experimentales, consulte la [documentación de {{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/get-support/servicessupport.html#s-services-exporcont){: new_window}. Para obtener los detalles completos de los servicios experimentales, consulte la versión más reciente de la [Descripción del servicio de {{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/software/sla/sladb.nsf/sla/bm?OpenDocument){: new_window}.

## Problemas de espacio de almacenamiento
{: #storage}

Dependiendo del plan de suscripción, puede alcanzar el límite de almacenamiento especificado para el plan y se le puede impedir realizar tareas que desee completar.

### Síntomas
{: #storage_symptoms}

Puede ver un mensaje sobre haber superado el espacio de almacenamiento permitido al intentar realizar una de estas tareas:

- Cargar documentos o diccionarios
- Desplegar un modelo o versión de un modelo
- Ejecutar un preanotador en documentos

### Causas
{: #storage_causes}

El límite de almacenamiento se ha alcanzado o se habría superado si la acción continuara.

### Resolución del problema
{: #storage_resolve}

Los mayores consumidores de espacio de almacenamiento son modelos de aprendizaje automático y basados en reglas. Para liberar espacio, puede realizar las siguientes acciones:

- Suprimir versiones de instantáneas de cualquier modelo al que no espere tener que revertir.
- Suprimir los modelos que no necesite.
- Si los modelos son demasiado importantes para suprimirlos, considere la posibilidad de actualizar el plan a uno que proporcione una mayor asignación de espacio de almacenamiento.

Después de eliminar modelos o versiones de modelos, espere una hora antes de volver a intentar la acción que ha dado lugar al mensaje de error. Se puede tardar un máximo de una hora para que el espacio de almacenamiento que ha liberado esté disponible para su uso.

Para gestionar su factura mensual, si tiene asignado el rol Admin y tiene una cuenta Premium o Estándar, puede establecer un límite de almacenamiento en la página Detalles de servicio en {{site.data.keyword.knowledgestudioshort}}. Para ver la página Detalles de servicio y establecer el límite de almacenamiento, desde la barra de navegación superior de {{site.data.keyword.knowledgestudioshort}}, pulse el icono **Configuración**, pulse el enlace **Ver/modificar detalles de servicio** y, a continuación, pulse el enlace **Establecer límite de almacenamiento**.
{: tip}

## Cómo ponerse en contacto con el soporte de IBM
{: #ts_contactingibmsupport}

El soporte técnico de {{site.data.keyword.IBM_notm}} proporciona ayuda con los defectos del producto, responde a las preguntas más frecuentes y permite a los usuarios a resolver los problemas con el producto.

- **Clientes del plan Lite no asociados a una cuenta de pago**

    Obtenga ayuda y respuestas a preguntas formulando preguntas a miembros de la comunidad de desarrolladores. Para obtener los enlaces, consulte la sección "Comunidad de desarrolladores" en la parte inferior de la tabla de contenido.

- **Clientes asociados a una cuenta de pago**

    Como cliente asociado a una cuenta de pago, usted también puede formular preguntas y aprender de las preguntas de otros usuarios. Las comunidades de desarrolladores están abiertas para todo el mundo y son un gran lugar para empezar. Para obtener los enlaces, consulte la sección "Comunidad de desarrolladores" en la parte inferior de la tabla de contenido.

    **Para ponerse en contacto con el soporte técnico de {{site.data.keyword.IBM_notm}}:**

    Debe tener autorización para crear casos de soporte en el Portal de servicio de {{site.data.keyword.cloud_notm}}.

    1. Defina el problema, recopile la información relacionada y determine la gravedad del problema.
    1. Recopile la información de diagnóstico, si es posible.
    1. Cree un caso en el [Portal de servicio de {{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://watson.service-now.com/wcp){: new_window}.
