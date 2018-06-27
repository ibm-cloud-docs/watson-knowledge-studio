---

copyright:
  years: 2018
lastupdated: "2018-06-27"

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

# User roles in {{site.data.keyword.knowledgestudioshort}}
{: #roles}

{{site.data.keyword.knowledgestudiofull}} roles are used to organize a team of people who create machine learning or rule-based models.
{: shortdesc}

## Notes about roles in {{site.data.keyword.knowledgestudioshort}}
{: #notes}

- User roles in {{site.data.keyword.knowledgestudioshort}} are managed at the following levels:
  - {{site.data.keyword.cloud}} roles control access to {{site.data.keyword.cloud_notm}} services. {{site.data.keyword.knowledgestudioshort}} uses Cloud Foundry for access control, which requires that {{site.data.keyword.knowledgestudioshort}} users have the developer role. For more information, see [Cloud Foundry access ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/iam/cfaccess.html){: new_window}.
  - {{site.data.keyword.knowledgestudioshort}} roles control access to {{site.data.keyword.knowledgestudioshort}} functionality, as described on this page.
- A {{site.data.keyword.knowledgestudioshort}} role isn't required to create an instance of {{site.data.keyword.knowledgestudioshort}}. However, when a person creates an instance of {{site.data.keyword.knowledgestudioshort}}, the first user to launch {{site.data.keyword.knowledgestudioshort}} is assigned the {{site.data.keyword.knowledgestudioshort}} admin role.
- To manage a workspace, project managers need to be assigned to the workspace by an admin.
- Admins and project managers can perform the role of human annotators, but they must be assigned to annotation sets in the same way that human annotators must be assigned to annotation sets.
- Once assigned, user roles can't be downgraded from higher to lower levels of permissions. Admins can't be downgraded to project managers or human annotators, and project managers can't be downgraded to human annotators. For information about adding users, upgrading roles, and deactivating user accounts, see [Assembling a team](/docs/services/watson-knowledge-studio/team.html).

## Role descriptions
{: #descriptions}
{{site.data.keyword.knowledgestudioshort}} roles are described in the following table. Roles are listed in order of highest to lowest level of permissions.

| Role | Description |
|------|-------------|
| Admin | Responsible for administrative tasks, which include managing users, resource consumption, and monthly charges. In large team settings, admins rarely participate in the model development process.
| Project manager | Responsible for the overall organization of the workspace that she or he is assigned to. Tasks include creating the type system, managing assets, managing annotation work, evaluating the machine learning model, and deploying models. Users in this role need industry subject-matter expertise because they create the type system, teach the human annotators how to correctly apply the type system, and evaluate the model quality. |
| Human annotator | Performs the labeling of the entity mentions and relationship mentions in the training documents that he or she is assigned to. The work is assigned to human annotators and monitored by the project manager. Human annotators may not have industry subject-matter expertise, as long as they are taught by the project manager how to correctly apply the type system. |
{:caption="Table 1. Role descriptions" caption-side="top"}

## Role permissions
{: #descriptions}

To compare the permissions of each role, see the following table. One permission is listed on each row. If a role has that permission, the role column is marked with a check mark (&checkmark;).

| Permission | Admin | Project manager | Human annotator |
|------------|-------|-----------------|-----------------|
| Manage user access and roles | &checkmark; |  |  |
| Manage workspaces | &checkmark; |  |  |
| Create the type system and annotation guidelines | &checkmark; | &checkmark; |  |
| Upload training documents | &checkmark; | &checkmark; |  |
| Manage rules | &checkmark; | &checkmark; |  |
| Pre-annotate documents | &checkmark; | &checkmark; |  |
| Manage annotation tasks | &checkmark; | &checkmark; |  |
| Resolve annotation conflicts with human annotation (*adjudication*) | &checkmark; | &checkmark; |  |
| Train and evaluate machine learning models | &checkmark; | &checkmark; |  |
| Deploy and undeploy models to runtime services | &checkmark; | &checkmark; |  |
| Perform document annotation | &checkmark; | &checkmark; | &checkmark; |
{:caption="Table 2. Role permissions" caption-side="top"}
