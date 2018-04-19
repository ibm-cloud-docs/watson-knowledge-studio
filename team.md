---

copyright:
  years: 2015, 2018
lastupdated: "2018-04-18"

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

This documentation is for {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. To see the documentation for the previous version of {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [click this link ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/knowledge-studio/team.html){: new_window}.
{: tip}

# Assembling a team
{: #team}

The creation of a model requires input from subject matter experts, project managers, and users who can understand and interpret statistical models. You must add a user in {{site.data.keyword.knowledgestudioshort}} for each person who needs to log in.
{: shortdesc}

**Note**: Only Standard plans and Premium plans can add users. Lite plans are limited to one user. As the only user, that person is assigned the role with the highest permission, the Admin role.

## Before you begin

- Make sure you're using a supported browser. For information, see [Browser requirements](/docs/services/watson-knowledge-studio/system-requirements.html).
- [Create an instance of {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/tutorials-create-project.html#instance).
- If you signed up for a Standard or Premium plan, from the {{site.data.keyword.cloud_notm}} **Manage** tab, invite other users to your organization that you want to add as users in {{site.data.keyword.knowledgestudioshort}}. For more information about inviting users, see [Inviting users and assigning access ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/iam/iamuserinv.html){: new_window}.

  **Important**:

  - Ensure that invited users have the Cloud Foundry role of **Developer**. For more information, see [Cloud Foundry access ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/iam/cfaccess.html){: new_window}.
  - The first user to launch {{site.data.keyword.knowledgestudioshort}} is granted the Admin role for the {{site.data.keyword.knowledgestudioshort}} instance. This task assumes you are the first person to launch {{site.data.keyword.knowledgestudioshort}} after you sign up for a plan, which means that you have the Admin role.

## About this task

Typically, you add users to fill the following roles.

**Note:** If you signed up for a Lite plan, you can't add others to your instance of {{site.data.keyword.knowledgestudioshort}}. Instead, when you launch {{site.data.keyword.knowledgestudioshort}}, you are added to the instance with the Admin role. In the Admin role, you can perform many functions that would typically be performed by different people who are assigned to different roles. You can test how experts from different areas of a domain can work together to build a machine learning model or rules-based model.

- **HumanAnnotator**

    Human annotators are typically subject matter experts who reviews documents from a specific domain to identify entities and relationships of interest to the domain. These users interact with the application in a limited way. They use the ground truth editor to annotate a set of documents that have been assigned to them.

- **ProjectManager**

    Project managers are people who help to facilitate the creation of models by performing such tasks as creating workspace artifacts, and training, creating, and deploying models. For workspaces that are used to build machine learning models, project managers also manage the document annotation process by assigning document review tasks to human annotators, adjudicating annotation conflicts, and approving documents to add to the ground truth.

## Adding users in {{site.data.keyword.knowledgestudioshort}}

Add users from your {{site.data.keyword.cloud_notm}} organization to {{site.data.keyword.knowledgestudioshort}}.

**Note**: Only Standard plans and Premium plans can add users. Lite plans are limited to one user.

To add users to a {{site.data.keyword.knowledgestudioshort}} instance:

1. Log in to the [{{site.data.keyword.cloud_notm}} Dashboard ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/dashboard/apps/){: new_window} with your {{site.data.keyword.ibmid}} and launch {{site.data.keyword.knowledgestudioshort}}.
1. Click the **Settings** icon, and then click **View/modify service details**.
1. In the **Manager users** section, enter the {{site.data.keyword.ibmid}} for the user you want to add.
1. Select the role you want to give the user.

   Note: You can't downgrade user roles after assigning them, so be sure that you understand the tasks each role can perform when assigning the Admin role and ProjectManager role.

1. Click **Add**.

## Upgrading user roles

After you add users to {{site.data.keyword.knowledgestudioshort}}, you can upgrade lower roles to higher roles. Users must be assigned the roles described below to be able to perform the respective tasks.

**Note**: Only Standard plans and Premium plans can upgrade users. Lite plans are limited to one user who already has the highest role, Admin.

> **Attention: Downgrading from a higher role to a lower role is not permitted.**

To upgrade roles for {{site.data.keyword.knowledgestudioshort}} users:

1. Log in to the [{{site.data.keyword.cloud_notm}} Dashboard ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/dashboard/apps/){: new_window} with your {{site.data.keyword.ibmid}} and launch {{site.data.keyword.knowledgestudioshort}}.
1. From the top right navigation menu, click the **Settings** icon ![the Settings icon](images/settings.png) and then click **View/modify service details**. The **Manage users** section of the Service Details page lists all the user IDs that are users for this instance of {{site.data.keyword.knowledgestudioshort}}.
1. Find the user's name you want to change and click the **Edit** link.

    {{site.data.keyword.knowledgestudioshort}} has the following roles, which are listed from the highest level to the lowest level of privileges:
    - **Admin**

      Users in this role can perform the following tasks:

        - Manage a subscription, such as add features, storage, and more users
        - Give users access to a subscription from the Service Details page
        - Create and manage all workspaces in their subscription
        - Assign people to the project manager or human annotator roles for all workspaces

    - **ProjectManager**

      Users with this role can perform the following tasks:

      - Manage workspaces to which they are added
      - Assign human annotators to a workspace

      Users with this role cannot perform the following tasks:

      - Create workspaces
      - Manage user access and roles from the Service Details page

    - **HumanAnnotator**

      Users with this role can annotate documents that are in workspaces where they are assigned the human annotator role, and in a document set that is associated with annotation tasks that are assigned to them.

      **Important:** You must create a workspace, associate a user with a document set, and assign an annotation task to a user before a user with the **HumanAnnotator** role can see any workspaces listed in the {{site.data.keyword.knowledgestudioshort}} application. Set up the workspace as soon as possible after users register so they see your workspace when they first access the application. You might want to notify users after you set up the workspace to let them know that they can start annotating documents.

1. Click the role of the user and choose the role you want to upgrade that user to.
1. Optional: When you finish administering users in {{site.data.keyword.knowledgestudioshort}}, exit the session by closing the web browser. The {{site.data.keyword.knowledgestudioshort}} user interface does not provide an action for explicitly logging out.

## Deactivating user accounts

Later, if you want to remove users, follow the previous steps to open the Service Details page again. From the list of user IDs, find the user you want to remove and click **Deactivate**.

> **Attention**: If users are assigned documents to annotate and you deactivate their accounts, their annotations are affected. If annotations made by deactivated users were not promoted to ground truth, those annotations are deleted.

### Related tasks

[Creating and assigning annotation sets](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projdocsets)
