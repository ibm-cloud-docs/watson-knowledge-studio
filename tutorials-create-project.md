---

copyright:
  years: 2015, 2017
lastupdated: "2017-12-19"

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

This documentation is for {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. To see the documentation for the previous version of {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [click this link ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/knowledge-studio/tutorials-create-project.html){: new_window}.
{: tip}

# Getting started with {{site.data.keyword.knowledgestudioshort}}
{: #wks_tutintro}

This {{site.data.keyword.knowledgestudiofull}} tutorial helps you perform prerequisite tasks that must be completed before you can start any of the other tutorials.
{: shortdesc}

## Before you begin
{: #prereq}

Confirm you're using a supported browser. For information, see [Browser requirements](/docs/services/watson-knowledge-studio/system-requirements.html).

## Creating a service instance
{: #instance}

1. [Sign up for an {{site.data.keyword.ibmid}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net){: new_window} and log in to {{site.data.keyword.cloud_notm}}.
1. From the [Dashboard page ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/dashboard/apps){: new_window}, sign up for a {{site.data.keyword.knowledgestudioshort}} plan.

  1. Click **Catalog**.
  1. In the search field, delete the **label:lite** filter and search for `{{site.data.keyword.knowledgestudioshort}}`.
  1. Select **{{site.data.keyword.knowledgestudioshort}}**.
  1. On the {{site.data.keyword.knowledgestudioshort}} catalog page, click **Upgrade** to upgrade your account to a Pay-As-You-Go account. You are prompted to provide credit card information.

    If you sign up for a {{site.data.keyword.knowledgestudioshort}} Free plan, your credit card will not be charged. You can use the Free plan for an unlimited time at no cost.
    {: tip}

1. After you sign up for a plan, launch {{site.data.keyword.knowledgestudioshort}}.

  To complete this tutorial, you must have at least one user ID that you can use in {{site.data.keyword.knowledgestudioshort}}. This user ID must have the Admin role. If you signed up for a free plan, as the only user, you have the Admin role. For information about user roles, see [Assembling a team](/docs/services/watson-knowledge-studio/team.html).

## Lesson 1: Assigning user roles
{: #wks_tutless1}

In this lesson, you will learn about the different roles that you can assign to users in {{site.data.keyword.knowledgestudioshort}}.

### About this task

The creation of a machine-learning annotator requires input from subject matter experts, project managers, and users who can understand and interpret statistical models. Administrators assign roles to each user, such that they have appropriate authority for their tasks. For more information about user roles, see [Assembling a team](/docs/services/watson-knowledge-studio/team.html).

### Procedure

1. Log in to {{site.data.keyword.knowledgestudioshort}} with your administrator ID.
1. Click the Settings icon to open the Service Details page. The page lists all the user IDs that are registered as {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} users. Each user ID has one of the following roles (in decreasing order of included permissions):

    - Admin
    - ProjectManager
    - HumanAnnotator

    For more information about user roles, see [Assembling a team](/docs/services/watson-knowledge-studio/team.html).

1. Verify that there is at least one user with the Admin role. A user ID with this role can create workspaces, and act as a project manager or human annotator.
1. If you have access to additional user IDs, verify that there are at least two users with the HumanAnnotator role.

    > **Note:** Creating a real-life model typically involves multiple human annotators in addition to an administrator or project manager. However, for purposes of the tutorial, you can continue with a single user ID.

1. Optional: Change the role assigned to a user ID. Click the **Modify account setting** icon in the **Action** column of the table row for a user ID, and change the assigned user role.

    > **Note:** You can upgrade a user ID to a role with greater permissions, but you cannot downgrade a user with an Admin or ProjectManager role to the HumanAnnotator role.

## Lesson 2: Creating a workspace
{: #wks_tutless2}

In this lesson, you will learn how to create a workspace within {{site.data.keyword.knowledgestudioshort}}.

### About this task

A workspace defines all of the resources that are required to create a machine-learning annotator, including training documents, the type system, dictionaries, and annotations that are added by human annotators. For more information about workspace creation, see [Creating a workspace](/docs/services/watson-knowledge-studio/create-project.html).

### Procedure

1. As a {{site.data.keyword.knowledgestudioshort}} administrator, from your {{site.data.keyword.cloud_notm}} [dashboard ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/dashboard/apps/){:new_window}, launch the {{site.data.keyword.knowledgestudioshort}} service.
1. Click **Create Worskpace**.
1. Specify the details for the new workspace:

    - In the **Workspace name** field, type `My workspace`.
    - In the **Workspace description** field, type `Watson Knowledge Studio tutorial workspace`.
    - In the **Language of documents** field, use the default value, **English**. The sample files you will be using for this tutorial are in English.

1. Click **Create**.

### Results

The workspace is created and opens automatically.

### What to do next

You can now start configuring the workspace resources, such as the type system.

## Lesson 3: Creating a type system
{: #wks_tutless3}

In this lesson, you will learn how to upload and modify a type system within {{site.data.keyword.knowledgestudioshort}}. You must create or upload a type system before you begin any annotation tasks.

### About this task

For more information about type systems, see [Type systems](/docs/services/watson-knowledge-studio/typesystem.html#wks_typesystem).

### Procedure

1. Download the <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/en-klue2-types.json" download>en-klue2-types.json<img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a> file to your computer. This file contains an example KLUE type system.
1. From the sidebar, click **Assets & Tools** > **Entity Types**.
1. On the Entity Types page, click **Upload**.
1. Select the `en-klue2-types.json` file from your computer and click **Upload**. The uploaded type system is displayed in the table.
1. Browse the type system so you can see the data that was uploaded.
1. Edit an entity type:

    1. Locate the MONEY entity type.
    1. Double-click anywhere in the table row to edit the entity type.
    1. In the **Roles** column, click the **Delete a role** icon ![_](images/wks_delete.jpg)  next to the AWARD role.

        ![A screen capture of deleting a role from an entity type.](images/wks_tut_delete_role.jpg)

    1. Click **Save**.

### What to do next

After you finish making changes to the type system, you can begin adding documents to your workspace.

## Lesson 4: Adding a dictionary
{: #wks_tutless4}

In this lesson, you will learn how to add a dictionary to a workspace in {{site.data.keyword.knowledgestudioshort}}. Dictionaries are used for pre-annotating text when creating a machine-learning annotator.

### About this task

For more information about dictionaries, see [Adding dictionaries to a workspace](/docs/services/watson-knowledge-studio/dictionaries.html#wks_projdictionaries).

### Procedure

1. Download the <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/dictionary-items-organization.csv" download>`dictionary-items-organization.csv`<img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a> file to your computer. This file contains dictionary terms in CSV format, suitable for uploading into a {{site.data.keyword.knowledgestudioshort}} dictionary.
1. From the **Assets & Tools** > **Pre-annotators** sidebar, select the **Dictionaries** tab, and click **Manage Dictionaries**.
1. Click **Create Dictionary** to add a dictionary.

    > **Note:** Do not click **Upload dictionary**, which is used to upload a dictionary that you want to use as-is. For the tutorial, you will create a new editable dictionary and then upload terms into it.

1. In the **Name** field, type `Test dictionary` and click **Save** to create the (empty) dictionary.

    The new dictionary is created and automatically opened for editing.

1. In the dictionary pane, click **Upload**.
1. In the Upload Dictionary Entries window, select the `dictionary-items-organization.csv` file from your computer and then click **Upload**. The terms in the file are uploaded into the dictionary.
1. Click **Add Entry** to create a new term. An editable row is added at the top of the table.
1. In the **Surface Forms** column, type `IBM` and `International Business Machines Corporation` on separate lines. (When you begin to type a new surface form, a space is added below for an additional surface form.) Leave the radio button next to `IBM` selected, which indicates that `IBM` is the lemma.
1. In the **Part of Speech** column, select **Noun**.
1. Click **Save**.

    ![A screen capture of the Dictionaries page. A dictionary entry is selected and its surface forms and part of speech of highlighted.](images/wks_tutdict4.jpg)

### What to do next

After you create a dictionary, you can use it to speed up human annotation tasks by pre-annotating the documents.

## Tutorial summary
{: #wks_tutsum}

While learning about {{site.data.keyword.knowledgestudioshort}}, you created a workspace and added artifacts to it.

### Lessons learned

By completing this tutorial, you learned about the following concepts:

- Workspaces
- Type systems
- Dictionaries
