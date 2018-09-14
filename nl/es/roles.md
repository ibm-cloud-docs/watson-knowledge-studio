---

copyright:
  years: 2018
lastupdated: "2018-07-02"

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

# Roles de usuario en {{site.data.keyword.knowledgestudioshort}}
{: #roles}

Los roles de {{site.data.keyword.knowledgestudiofull}} se utilizan para organizar un equipo de personas que crean modelos de aprendizaje automático o basados en reglas.
{: shortdesc}

## Notas sobre los roles en {{site.data.keyword.knowledgestudioshort}}
{: #notes}

- Los roles de usuario en {{site.data.keyword.knowledgestudioshort}} se gestionan en los niveles siguientes:
  - Los roles de {{site.data.keyword.cloud}} controlan el acceso a los servicios de {{site.data.keyword.cloud_notm}}. {{site.data.keyword.knowledgestudioshort}} utiliza Cloud Foundry para el control de acceso, para lo que es necesario que los usuarios de {{site.data.keyword.knowledgestudioshort}} tengan el rol de desarrollador. Para obtener más información, consulte [Acceso a Cloud Foundry ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/iam/cfaccess.html){: new_window}.
  - Los roles de {{site.data.keyword.knowledgestudioshort}} controlan el acceso a la funcionalidad de {{site.data.keyword.knowledgestudioshort}}, tal como se describe en esta página.
- No es necesario un rol de {{site.data.keyword.knowledgestudioshort}} para crear una instancia de {{site.data.keyword.knowledgestudioshort}}. Sin embargo, cuando una persona crea una instancia de {{site.data.keyword.knowledgestudioshort}}, al primer usuario que abre {{site.data.keyword.knowledgestudioshort}} se le asigna el rol de administrador de {{site.data.keyword.knowledgestudioshort}}.
- Para gestionar un espacio de trabajo, un administrador debe asignar a los gestores de proyectos al espacio de trabajo.
- Los administradores y los gestores de proyectos pueden desempeñar el rol de anotadores humanos, pero se les debe asignar a los conjuntos de anotaciones de la misma forma que a los anotadores humanos se les debe asignar a los conjuntos de anotaciones.
- Una vez asignados, los roles de usuario no se pueden degradar de un nivel superior a un nivel inferior de permisos. A los administradores no se les puede degradar a gestores de proyectos o anotadores humanos, y a los gestores de proyectos no se les puede degradar a anotadores humanos. Para obtener información sobre cómo añadir usuarios, actualizar roles y desactivar cuentas de usuario, consulte [Ensamblaje de un equipo](/docs/services/watson-knowledge-studio/team.html).

## Descripciones de rol
{: #descriptions}
Los roles de {{site.data.keyword.knowledgestudioshort}} se describen en la tabla siguiente. Los roles se listan por orden del nivel más alto al nivel más bajo de permisos.

| Rol | Descripción |
|------|-------------|
| Admin | Responsable de tareas administrativas, que incluyen gestionar los usuarios, el consumo de recursos y los cargos mensuales. En los entornos de equipos grandes, los administradores rara vez participan en el proceso de desarrollo de modelos.
| Gestor de proyectos | Responsable de la organización global del espacio de trabajo al que está asignado. Las tareas incluyen la creación del sistema de tipos, la gestión de activos, la gestión del trabajo de anotación, la evaluación del modelo de aprendizaje automático y el despliegue de modelos. Los usuarios de este rol necesitan experiencia en el sector porque crean el sistema de tipos, enseñan a los anotadores humanos cómo aplicar correctamente el sistema de tipos y evalúan la calidad del modelo. |
| Anotador humano | Realiza el etiquetado de las menciones de entidad y las menciones de relación en los documentos de entrenamiento a los que está asignado. El trabajo se asigna a los anotadores humanos y lo supervisa el gestor de proyectos. Los anotadores humanos pueden no tener experiencia en el sector, siempre que el gestor de proyectos les enseñe a aplicar correctamente el sistema de tipos. |
{:caption="Tabla 1. Descripciones de roles" caption-side="top"}

## Permisos de rol
{: #permissions}

Para comparar los permisos de cada rol, consulte la tabla siguiente. Se lista un permiso en cada fila. Si un rol tiene ese permiso, se indica una marca de selección (&checkmark;) en la columna del rol.

| Permiso | Admin | Gestor de proyectos | Anotador humano |
|------------|-------|-----------------|-----------------|
| Gestionar el acceso de usuarios y los roles | &checkmark; |  |  |
| Gestionar espacios de trabajo | &checkmark; |  |  |
| Crear el sistema de tipos y las directrices de anotación | &checkmark; | &checkmark; |  |
| Cargar documentos de entrenamiento | &checkmark; | &checkmark; |  |
| Gestionar reglas | &checkmark; | &checkmark; |  |
| Preanotar documentos | &checkmark; | &checkmark; |  |
| Gestionar tareas de anotación | &checkmark; | &checkmark; |  |
| Resolver conflictos de anotación con anotación humana (*adjudicación*) | &checkmark; | &checkmark; |  |
| Entrenar y evaluar modelos de aprendizaje automático | &checkmark; | &checkmark; |  |
| Desplegar y retirar el despliegue de modelos en servicios de tiempo de ejecución | &checkmark; | &checkmark; |  |
| Realizar anotación de documentos | &checkmark; | &checkmark; | &checkmark; |
{:caption="Tabla 2. Permisos de rol" caption-side="top"}
