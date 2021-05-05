---

copyright:
  years: 2018, 2020
lastupdated: "2020-11-06"

subcollection: watson-knowledge-studio

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:deprecated: .deprecated}
{:important: .important}
{:note: .note}
{:tip: .tip}
{:preview: .preview}
{:beta: .beta}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}

# User roles in {{site.data.keyword.knowledgestudioshort}}
{: #roles}

{{site.data.keyword.knowledgestudiofull}} roles are used to organize a team of people who create machine learning or rule-based models.
{: shortdesc}

## Notes about roles in {{site.data.keyword.knowledgestudioshort}}
{: #notes}

- **{{site.data.keyword.cloud}} roles** are different from **{{site.data.keyword.knowledgestudioshort}} roles**.
  - **{{site.data.keyword.cloud}} roles** control permissions for managing {{site.data.keyword.cloud_notm}} services. New service instances of {{site.data.keyword.knowledgestudioshort}} are managed with [{{site.data.keyword.cloud_notm}} Identity and Access Management (IAM)](/docs/iam) in all public regions.
  - **{{site.data.keyword.knowledgestudioshort}} roles** control access to {{site.data.keyword.knowledgestudioshort}} functionality and are managed in the {{site.data.keyword.knowledgestudioshort}} application.
- The first user to launch the {{site.data.keyword.knowledgestudioshort}} application is assigned the **Admin** role.
- Once assigned, user roles can't be downgraded from higher to lower levels of permissions. Admins can't be downgraded to project managers or human annotators, and project managers can't be downgraded to human annotators. For information about adding users, upgrading roles, and deactivating user accounts, see [Assembling a team](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-team).
- To manage a workspace, project managers need to be assigned to the workspace by an admin.
- Admins and project managers can perform the role of human annotators. They can also [directly annotate document sets](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-annotating-document-sets-directly) without creating annotation tasks.

## {{site.data.keyword.knowledgestudioshort}} role descriptions
{: #descriptions}
{{site.data.keyword.knowledgestudioshort}} roles are described in the following table. Roles are listed in order of highest to lowest level of permissions.

| Role | Description |
|------|-------------|
| Admin | Responsible for administrative tasks, which include managing users, resource consumption, and monthly charges. In large team settings, admins rarely participate in the model development process.
| Project manager | Responsible for the overall organization of the workspace that she or he is assigned to. Tasks include creating the type system, managing assets, managing annotation work, evaluating the machine learning model, and deploying models. Users in this role need industry subject-matter expertise because they create the type system, teach the human annotators how to correctly apply the type system, and evaluate the model quality. |
| Human annotator | Performs the labeling of the entity mentions and relationship mentions in the training documents that he or she is assigned to. The work is assigned to human annotators and monitored by the project manager. Human annotators may not have industry subject-matter expertise, as long as they are taught by the project manager how to correctly apply the type system. |
{:caption="Table 1. Role descriptions" caption-side="top"}

## {{site.data.keyword.knowledgestudioshort}} role permissions
{: #permissions}

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
| Annotate document sets directly | &checkmark; | &checkmark; | |
| Perform document annotation in annotation tasks | &checkmark; | &checkmark; | &checkmark; |
{:caption="Table 2. Role permissions" caption-side="top"}
