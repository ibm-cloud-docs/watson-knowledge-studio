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

Esta documentación es para {{site.data.keyword.knowledgestudiofull}} en {{site.data.keyword.cloud}}. Para ver la documentación para la versión anterior de {{site.data.keyword.knowledgestudioshort}} en {{site.data.keyword.IBM_notm}} Marketplace, [pulse este enlace ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/services/knowledge-studio/team.html){: new_window}.
{: tip}

# Ensamblaje de un equipo
{: #team}

La creación de un modelo requiere la entrada de expertos en la materia, gestores de proyectos, y los usuarios que pueden entender e interpretar modelos estadísticos. Debe añadir un usuario en {{site.data.keyword.knowledgestudioshort}} para cada persona que necesita iniciar sesión.
{: shortdesc}

**Nota**: Solo los planes Estándar y Premium pueden añadir usuarios. Los planes gratuitos están limitados a un usuario. Como único usuario, dicha persona tiene asignado el rol con el permiso más elevado, el rol Admin.

## Antes de empezar

- Asegúrese de que está utilizando un navegador soportado. Para obtener información, consulte [Requisitos del navegador](/docs/services/watson-knowledge-studio/system-requirements.html).
- [Cree una instancia de {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/tutorials-create-project.html#instance).
- Si se ha inscrito para un plan Estándar o Premium, desde el separador **Gestionar** de {{site.data.keyword.cloud_notm}}, invite a otros usuarios a su organización que desee añadir como usuarios en {{site.data.keyword.knowledgestudioshort}}. Para obtener más información sobre cómo invitar usuarios, consulte [Invitación de usuarios y asignación de acceso ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/iam/iamuserinv.html){: new_window}.

  **Importante**:

  - Asegúrese de que los usuarios invitados tengan el rol de Cloud Foundry de **Desarrollador**. Para obtener más información, consulte [Acceso a Cloud Foundry ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/iam/cfaccess.html){: new_window}.
  - Al primer usuario que inicie {{site.data.keyword.knowledgestudioshort}} se le otorgará el rol Admin para la instancia de {{site.data.keyword.knowledgestudioshort}}. Esta tarea presupone que es la primera persona que iniciará {{site.data.keyword.knowledgestudioshort}} después de registrarse para un plan, lo que significa que tiene el rol Admin.

## Acerca de esta tarea

Normalmente, añada usuarios para llenar los roles siguientes.

**Nota:** Si se ha registrado para un plan Gratuito, no podrá añadir otros a su instancia de {{site.data.keyword.knowledgestudioshort}}. En su lugar, al iniciar {{site.data.keyword.knowledgestudioshort}}, se le añadirá a la instancia con el rol Admin. En el rol Admin, puede realizar muchas funciones que podrían realizar normalmente distintas personas que estén asignadas a roles diferentes. Puede probar cómo pueden trabajar juntos expertos de distintas áreas de un dominio para crear un modelo de aprendizaje automático o un modelo basado en reglas.

- **HumanAnnotator**

    Los anotadores humanos son normalmente expertos en la materia que revisan documentos de un dominio específico para identificar entidades y relaciones de interés en el dominio. Estos usuarios interactúan con la aplicación en una forma limitada. Utilizan el editor de datos de campo para anotar un conjunto de documentos que se les ha asignado.

- **ProjectManager**

    Los gestores de proyectos son personas que ayudan a facilitar la creación de modelos realizan tareas tales como la creación de artefactos de espacio de trabajo, y el entrenamiento, creación y despliegue de modelos. Para los espacios de trabajo que se utilizan para crear anotadores de aprendizaje automático, los gestores de proyectos también gestionan el proceso de anotación de documentos asignando tareas de revisión de documentos a los anotadores humanos, adjudicando conflictos de anotación, y aprobando documentos para añadir a los datos de campo.

## Añadir usuarios en {{site.data.keyword.knowledgestudioshort}}

Añada usuarios desde la organización de {{site.data.keyword.cloud_notm}} hasta {{site.data.keyword.knowledgestudioshort}}.

**Nota**: Solo los planes Estándar y Premium pueden añadir usuarios. Los planes gratuitos están limitados a un usuario.

Para añadir usuarios a una instancia de {{site.data.keyword.knowledgestudioshort}}:

1. Inicie sesión en el [Panel de control de {{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/dashboard/apps/){: new_window} con el {{site.data.keyword.ibmid}} e inicie {{site.data.keyword.knowledgestudioshort}}.
1. Pulse el icono **Configuración** y, a continuación, pulse **Ver/modificar detalles de servicio**.
1. En la sección **Gestor de usuarios**, escriba el {{site.data.keyword.ibmid}} para el usuario que desee añadir.
1. Seleccione el rol que desea otorgar al usuario.

   Nota: No puede degradar los roles de usuario después de asignarlos, por lo que asegúrese de comprender las tareas que puede realizar cada rol al asignar el rol Admin y el rol ProjectManager.

1. Pulse **Añadir**.

## Actualización de roles de usuario

Después de añadir usuarios a {{site.data.keyword.knowledgestudioshort}}, puede actualizar roles inferiores a roles superiores. A los usuarios se les deberá asignar los roles descritos más abajo para poder realizar las tareas respectivas.

**Nota**: Solo los planes Estándar y Premium pueden actualizar usuarios. Los planes gratuitos están limitados a un usuario que ya tiene el rol más alto, Admin.

> **Atención: La degradación de un rol superior a un rol inferior no está permitida.**

Para actualizar roles para los usuarios de {{site.data.keyword.knowledgestudioshort}}:

1. Inicie sesión en el [Panel de control de {{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/dashboard/apps/){: new_window} con el {{site.data.keyword.ibmid}} e inicie {{site.data.keyword.knowledgestudioshort}}.
1. Desde el menú de navegación de la parte superior derecha, pulse el icono **Configuración** ![el icono Configuración](images/settings.png) y luego pulse **Ver/modificar detalles de servicio**. La sección **Gestionar usuarios** de la página Detalles de servicio lista todos los ID de usuario que son usuarios para esta instancia de {{site.data.keyword.knowledgestudioshort}}.
1. Busque el nombre del usuario que desee cambiar y pulse el enlace **Editar**.

    {{site.data.keyword.knowledgestudioshort}} tiene los roles siguientes, que están listados desde el nivel superior al nivel inferior de privilegios:
    - **Admin**

      Los usuarios con este rol pueden llevar a cabo las tareas siguientes:

        - Gestionar una suscripción, como añadir características, almacenamiento y más usuarios
        - Otorgar a los usuarios acceso a una suscripción desde la página Detalles de servicio
        - Crear y gestionar todos los espacios de trabajo en su suscripción
        - Asignar personas a los roles de gestor de proyectos o de anotador humano para todos los espacios de trabajo

    - **ProjectManager**

      Los usuarios con este rol pueden realizar las tareas siguientes:

      - Gestionar espacios de trabajo a los que se añadirán
      - Asignar anotadores humanos a un espacio de trabajo

      Los usuarios con este rol no pueden realizar las tareas siguientes:

      - Crear espacios de trabajo
      - Gestionar el acceso de usuarios y los roles desde la página Detalles de servicio

    - **HumanAnnotator**

      Los usuarios con este rol pueden anotar documentos que están en los espacios de trabajo donde se les asigna el rol de anotador humano, y en un conjunto de documentos que está asociado con las tareas de anotación que se les han asignado.

      **Importante:** Debe crear un espacio de trabajo, asociar un usuario con un conjunto de documentos, y asignar una tarea de anotación a un usuario antes de que un usuario con el rol **HumanAnnotator** pueda ver ningún espacio de trabajo listado en la aplicación {{site.data.keyword.knowledgestudioshort}}. Configure el espacio de trabajo tan pronto como sea posible después de que se registren los usuarios, para que vean su espacio de trabajo cuando accedan por primera vez a la aplicación. Puede que desee notificar a los usuarios después de establecer el espacio de trabajo para hacerles saber que pueden iniciar la anotación de documentos.

1. Pulse el rol del usuario y seleccione el rol al que desea actualizar a ese usuario.
1. Opcional: Cuando termine de administrar usuarios en {{site.data.keyword.knowledgestudioshort}}, salga de la sesión cerrando el navegador web. La interfaz de usuario de {{site.data.keyword.knowledgestudioshort}} no proporciona una acción para cerrar sesión explícitamente.

## Desactivación de las cuentas de usuario

Posteriormente, si desea eliminar usuarios, siga los pasos anteriores para abrir la página Detalles de servicio de nuevo. En la lista de ID de usuario, busque el usuario que desee eliminar y pulse **Desactivar**.

> **Atención**: Si los usuarios tienen asignados documentos para anotar y usted desactiva sus cuentas, sus anotaciones se verán afectadas. Si las anotaciones realizadas por usuarios desactivados no se promocionaron a datos de campo, dichas anotaciones se suprimirán.

### Tareas relacionadas

[Creación y asignación de conjuntos de anotaciones](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projdocsets)
