---

copyright:
  years: 2015, 2018
lastupdated: "2018-10-04"

subcollection: watson-knowledge-studio

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

This documentation is for {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. To see the documentation for the previous version of {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [click this link ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/docs/services/knowledge-studio?topic=knowledge-studio-team){: new_window}.
{: tip}

# Assembling a team
{: #team}

The creation of a model requires input from subject matter experts, project managers, and users who can understand and interpret statistical models. You must add a user in {{site.data.keyword.knowledgestudioshort}} for each person who needs to log in.
{: shortdesc}

## Before you begin
{: #team-byb}

- Make sure you're using a supported browser. For information, see [Browser requirements](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-system-requirements).
- [Create an instance of {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutintro#instance). Make sure you select a **Standard** or **Premium** plan. Lite plans are limited to one user.
- Make sure that you are assigned an **Admin** role for your {{site.data.keyword.knowledgestudioshort}} instance. The first user to launch {{site.data.keyword.knowledgestudioshort}} is automatically assigned an **Admin** role.
- Understand the [{{site.data.keyword.knowledgestudioshort}} roles](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-roles#descriptions) that you can assign.

## Adding users in {{site.data.keyword.knowledgestudioshort}}
{: #team-add}

To add users to a {{site.data.keyword.knowledgestudioshort}} service instance:

1. [Launch the {{site.data.keyword.knowledgestudioshort}} application.](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutintro#launching-the-knowledge-studio-application)
1. Click the **Settings** icon ![the Settings icon](images/settings.png), then click **Manage service details**.
1. In the **Manage users** section, enter the {{site.data.keyword.ibmid}} for the user you want to add.
1. Select the role you want to give the user. For descriptions of the roles that are available, see [User roles in {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-roles).

  **Note**: You can't downgrade user roles after assigning them, so be sure that you understand the tasks each role can perform when assigning the admin role and project manager role.

1. Click **Add**.

## Upgrading user roles
{: #team-upgrade}

After you add users to {{site.data.keyword.knowledgestudioshort}}, you can upgrade lower roles to higher roles. Users must be assigned the roles described below to be able to perform the respective tasks.

**Note**: Only Standard plans and Premium plans can have more than one user. Lite plans are limited to one user who already has the highest role, admin.

> **Attention: Downgrading from a higher role to a lower role is not permitted.**

To upgrade roles for {{site.data.keyword.knowledgestudioshort}} users:

1. [Launch the {{site.data.keyword.knowledgestudioshort}} application.](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutintro#launching-the-knowledge-studio-application)
1. From the top right navigation menu, click the **Settings** icon ![the Settings icon](images/settings.png) and then click **Manage service details**.
1. In the **Manage users** section of the Service Details page, click the **Edit** link next to a user.
1. Click the role of the user and choose the role you want to upgrade that user to. For descriptions of the roles that are available, see [User roles in {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-roles).

  **Important:** You must create a workspace, associate a user with a document set, and assign an annotation task to a user before a user with the human annotator role can see any workspaces listed in the {{site.data.keyword.knowledgestudioshort}} application. Set up the workspace as soon as possible after users register so they see your workspace when they first access the application. You might want to notify users after you set up the workspace to let them know that they can start annotating documents.

1. Optional: When you finish administering users in {{site.data.keyword.knowledgestudioshort}}, exit the session by closing the web browser. The {{site.data.keyword.knowledgestudioshort}} user interface does not provide an action for explicitly logging out.

## Deactivating user accounts
{: #team-deact}

Later, if you want to remove users, follow the previous steps to open the Service Details page. From the list of user IDs, find the user you want to remove and click **Deactivate**.

> **Attention**: If users are assigned documents to annotate and you deactivate their accounts, their annotations are affected. If annotations made by deactivated users were not promoted to ground truth, those annotations are deleted.

### Related tasks
{: #team-rel}

[Creating and assigning annotation sets](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-documents-for-annotation#wks_projdocsets)
