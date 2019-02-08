---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-16"

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

Esta documentación es para {{site.data.keyword.knowledgestudiofull}} en {{site.data.keyword.cloud}}. Para ver la documentación para la versión anterior de {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.IBM_notm}} Marketplace, [pulse este enlace ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/docs/services/knowledge-studio/tutorials-create-project.html){: new_window}.
{: tip}

# Iniciación a {{site.data.keyword.knowledgestudioshort}}
{: #wks_tutintro}

Esta guía de aprendizaje de {{site.data.keyword.knowledgestudiofull}} le ayuda a realizar tareas de requisitos previos que deben completarse antes de poder iniciar cualquiera de las otras guías de aprendizaje.
{: shortdesc}

## Antes de empezar
{: #prereq}

- Confirme que está utilizando un navegador soportado. Para obtener información, consulte [Requisitos del navegador](/docs/services/watson-knowledge-studio/system-requirements.html).
-  Para completar esta guía de aprendizaje, debe tener al menos un ID de usuario que pueda utilizar en {{site.data.keyword.knowledgestudioshort}}. Este ID de usuario debe tener el rol Admin. Si se registra para un plan Lite, como el único usuario, tendrá el rol Admin. Para obtener información sobre los roles de usuario, consulte [Ensamblaje de un equipo](/docs/services/watson-knowledge-studio/team.html).

## Creación de una instancia de servicio
{: #instance}

1. Si aún no lo ha hecho, [regístrese para un {{site.data.keyword.ibmid}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}){: new_window} e inicie sesión en {{site.data.keyword.cloud_notm}}.
1. Desde la página de servicios de {{site.data.keyword.cloud_notm}} {{site.data.keyword.watson}} [ ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/developer/watson/services){: new_window}, pulse el recuadro de {{site.data.keyword.knowledgestudioshort}} y regístrese para un plan.
1. Después de registrarse para un plan, desde la lista de servicios existentes, inicie {{site.data.keyword.knowledgestudioshort}}.

## Lección 1: Asignación de roles de usuario
{: #wks_tutless1}

En esta lección, aprenderá sobre los distintos roles que puede asignar a los usuarios en {{site.data.keyword.knowledgestudioshort}}.

### Acerca de esta tarea
{: #wks_tutless1_about}

La creación de un modelo de aprendizaje automático requiere entrada de expertos en la materia, de gestores de proyectos y de usuarios que pueden entender e interpretar los modelos estadísticos. Los administradores asignan roles a cada usuario, por lo que tienen autoridad apropiada para sus tareas. Para obtener más información sobre los roles de usuario, consulte [Ensamblaje de un equipo](/docs/services/watson-knowledge-studio/team.html).

### Procedimiento
{: #wks_tutless1_procedure}

1. Inicie sesión en {{site.data.keyword.knowledgestudioshort}} con su ID de administrador. Si tiene una instancia de {{site.data.keyword.knowledgestudioshort}} existente, lo encontrará en la página de servicios de {{site.data.keyword.cloud_notm}} {{site.data.keyword.watson}} [ ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/developer/watson/services){: new_window}.
1. Pulse el icono Configuración para abrir la página Detalles de servicio. La página lista todos los ID de usuario registrados como usuarios de {{site.data.keyword.knowledgestudioshort}}. Cada ID de usuario tiene uno de los siguientes roles (en orden descendente de permisos incluidos):

    - Admin
    - Gestor de proyectos
    - Anotador humano

    Para obtener información sobre los roles de usuario, consulte [Roles de usuario en {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/roles.html).

1. Verifique que haya al menos un usuario con el rol Admin. Un ID de usuario con este rol puede crear espacios de trabajo, y actuar como un gestor de proyectos o un anotador humano.
1. Si tiene acceso a ID de usuario adicionales, verifique que haya al menos dos usuarios con el rol Anotador humano.

    > **Nota:** La creación de un modelo real normalmente incluye varios anotadores humanos además de un administrador o gestor de proyectos. Sin embargo, para fines de la guía de aprendizaje, puede continuar con un único ID de usuario.

1. Opcional: Cambie el rol asignado a un ID de usuario. En la columna **Acción** de la tabla, pulse el enlace **Editar** y, a continuación, cambie el rol de usuario asignado.

    > **Nota:** Puede actualizar un ID de usuario a un rol con permisos mayores, pero no puede degradar un usuario con un rol Admin o Gestor de proyectos al rol Anotador humano.

## Lección 2: Creación de un espacio de trabajo
{: #wks_tutless2}

En esta lección, aprenderá a crear un espacio de trabajo dentro de {{site.data.keyword.knowledgestudioshort}}.

### Acerca de esta tarea
{: #wks_tutless2_about}

Un espacio de trabajo define todos los recursos que son necesarios para crear un modelo de aprendizaje automático, incluidos documentos de entrenamiento, el sistema de tipos, diccionarios y anotaciones que añaden anotadores humanos. Para obtener más información sobre la creación del espacio de trabajo, consulte [Creación de un espacio de trabajo](/docs/services/watson-knowledge-studio/create-project.html).

### Procedimiento
{: #wks_tutless2_procedure}

1. Como administrador de {{site.data.keyword.knowledgestudioshort}}, desde su {{site.data.keyword.cloud_notm}} [panel de control ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}){:new_window}, inicie el servicio de {{site.data.keyword.knowledgestudioshort}}.
1. Pulse **Crear espacio de trabajo**.
1. Especifique los detalles del nuevo espacio de trabajo:

    - En el campo **Nombre de espacio de trabajo**, escriba `Mi espacio de trabajo`.
    - En el campo **Descripción del espacio de trabajo**, escriba `Espacio de trabajo de la guía de aprendizaje de Watson Knowledge Studio`.
    - En el campo **Idioma de los documentos**, utilice el valor predeterminado, **Inglés**. Los archivos de ejemplo que utilizará para esta guía de aprendizaje están en inglés.

1. Pulse **Crear**.

### Resultados
{: #wks_tutless2_results}

El espacio de trabajo se crea y se abre automáticamente.

### Qué hacer a continuación
{: #wks_tutless2_next}

Ahora puede empezar a configurar los recursos del espacio de trabajo, como por ejemplo el sistema de tipos.

## Lección 3: Creación de un sistema de tipos
{: #wks_tutless3}

En esta lección, aprenderá a cargar y modificar un sistema de tipos dentro de {{site.data.keyword.knowledgestudioshort}}. Debe crear o cargar un sistema de tipos antes de empezar cualquier tarea de anotación.

### Acerca de esta tarea
{: #wks_tutless3_about}

Para obtener más información sobre los sistemas de tipos, consulte [Sistemas de tipos](/docs/services/watson-knowledge-studio/typesystem.html#wks_typesystem).

### Procedimiento
{: #wks_tutless3_procedure}

1. Descargue el archivo <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/en-klue2-types.json" download>en-klue2-types.json<img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo" title="Icono de enlace externo" class="style-scope doc-content"></a> en el sistema. Este archivo contiene un sistema de tipos de KLUE de ejemplo.
1. Pulse **Activos**> **Tipos de entidades**.
1. En la página Tipos de entidades, pulse **Cargar**.
1. Cargue el archivo `en-klue2-types.json` desde el sistema. El sistema de tipos descargado se mostrará en la tabla.
1. Examine el sistema de tipos para que pueda ver los datos cargados.
1. Edite un tipo de entidad:

    1. Localice el tipo de entidad MONEY.
    1. Efectúe una doble pulsación en cualquier lugar de la fila de la tabla para editar el tipo de entidad.
    1. En la columna **Roles**, pulse el icono **Suprimir un rol** ![El icono "Suprimir un rol".](images/wks_delete.jpg "El icono ") junto al rol AWARD.

        ![Una captura de pantalla de la supresión de un rol desde un tipo de entidad.](images/wks_tut_delete_role.jpg "Una captura de pantalla que muestra el cursor sobre ")

    1. Pulse **Guardar**.

### Qué hacer a continuación
{: #wks_tutless3_next}

Cuando termine de hacer cambios en el sistema de tipos, puede empezar a añadir documentos a su espacio de trabajo.

## Lección 4: Añadir un diccionario
{: #wks_tutless4}

En esta lección, aprenderá a añadir un diccionario a un espacio de trabajo en {{site.data.keyword.knowledgestudioshort}}. Los diccionarios se utilizan para preanotar texto al crear un modelo de aprendizaje automático.

### Acerca de esta tarea
{: #wks_tutless4_about}

Para obtener más información sobre los diccionarios, consulte [Adición de diccionarios a un espacio de trabajo](/docs/services/watson-knowledge-studio/dictionaries.html#wks_projdictionaries).

### Procedimiento
{: #wks_tutless4_procedure}

1. Descargue el archivo <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/dictionary-items-organization.csv" download>`dictionary-items-organization.csv` <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo" title="Icono de enlace externo" class="style-scope doc-content"></a> en el sistema. Este archivo contiene términos de diccionario en formato CSV, adecuado para cargar en un diccionario de {{site.data.keyword.knowledgestudioshort}}.
1. Pulse **Activos** > **Diccionarios**.
1. Pulse **Crear diccionario** para añadir un diccionario.

    > **Nota:** No pulse **Cargar diccionario**, que se utiliza para cargar un diccionario que desea utilizar tal cual. Para la guía de aprendizaje, creará un nuevo diccionario editable y, a continuación, cargará términos en él.

1. En el campo **Nombre**, escriba `Diccionario de prueba` y pulse **Guardar** para crear el diccionario (vacío).

    El nuevo diccionario se creará y se abrirá automáticamente para su edición.

1. En el panel del diccionario, pulse **Cargar**.
1. Cargue el archivo `dictionary-items-organization.csv` desde el sistema. Los términos del archivo se cargan en el diccionario.
1. Pulse **Añadir entrada** para crear un término nuevo. Se añadirá una fila editable en la parte superior de la tabla.
1. En la columna **Formas superficiales**, escriba `IBM` e `International Business Machines Corporation` en líneas distintas. (Al empezar a escribir una nueva forma superficial, se añadirá un espacio debajo de una forma superficial adicional). Deje el botón de selección junto a `IBM` seleccionado, lo que indica que `IBM` es el lema.
1. En la columna **Categoría léxica**, seleccione **Nombre**.
1. Pulse **Guardar**.

    ![Una captura de pantalla de la página Diccionarios. La entrada de diccionario "IBM" se selecciona, y su forma superficial y categoría léxica se resaltan.](images/wks_tutdict4.jpg "Una captura de pantalla de la página Diccionarios. La entrada de diccionario ")

### Qué hacer a continuación
{: #wks_tutless4_next}

Después de crear un diccionario, puede utilizarlo para acelerar las tareas de anotación humana preanotando los documentos.

## Resumen de la guía de aprendizaje
{: #wks_tutsum}

A la vez que aprendía sobre {{site.data.keyword.knowledgestudioshort}}, ha creado un espacio de trabajo y ha añadido artefactos al mismo.

### Lecciones aprendidas
{: #lessons_learned}

Al completar esta guía de aprendizaje, habrá aprendido los siguientes conceptos:

- Espacios de trabajo
- Sistemas de tipos
- Diccionarios
