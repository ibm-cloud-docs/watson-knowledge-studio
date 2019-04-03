---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-16"

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

This documentation is for {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. To see the documentation for the previous version of {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [click this link ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/docs/services/knowledge-studio/tutorials-create-project.html){: new_window}.
{: tip}

# Getting started with {{site.data.keyword.knowledgestudioshort}}
{: #wks_tutintro}

This {{site.data.keyword.knowledgestudiofull}} tutorial helps you perform prerequisite tasks that must be completed before you can start any of the other tutorials.
{: shortdesc}

## Before you begin
{: #prereq}

- Confirm you're using a supported browser. For information, see [Browser requirements](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-system-requirements).
-  To complete this tutorial, you must have at least one user ID that you can use in {{site.data.keyword.knowledgestudioshort}}. This user ID must have the Admin role. If you sign up for a Lite plan, as the only user, you will have the Admin role. For information about user roles, see [Assembling a team](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-team).

## Creating a service instance
{: #instance}

1. If you haven't already, [sign up for an {{site.data.keyword.ibmid}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com){: new_window} and log in to {{site.data.keyword.cloud_notm}}.
2. Go to the [{{site.data.keyword.knowledgestudioshort}}](https://cloud.ibm.com/catalog/services/knowledge-studio) page in the {{site.data.keyword.cloud_notm}} catalog.
3. Select a pricing plan, and click **Create**.

## Launching the {{site.data.keyword.knowledgestudioshort}} application
{: #launching-the-knowledge-studio-application}

After creating a service instance, the user who created the service instance and any users with [{{site.data.keyword.cloud_notm}} roles](roles.html#notes) that allow access to the service instance will be able to launch the {{site.data.keyword.knowledgestudioshort}} application with the following steps.

1. Go to the [{{site.data.keyword.cloud_notm}} resources ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/resources){: new_window} page. Log in with your {{site.data.keyword.ibmid}}.
2. Select **Services** and click on your {{site.data.keyword.knowledgestudioshort}} service instance to open the {{site.data.keyword.knowledgestudioshort}} service dashboard.
3. Click **Launch tool** from the **Manage** tab.

After you launch {{site.data.keyword.knowledgestudioshort}}, you can copy the URL and use it to launch the application directly.

Example URL:
```
https://gateway.watsonplatform.net/knowledge-studio/tools/app/zefz11/enf01h9le5c63p50/ui/#/`
```

If you want to [add users to {{site.data.keyword.knowledgestudioshort}}](team.html#team-add) but don't want to grant them an {{site.data.keyword.cloud_notm}} role that allows access to your service instance, share the application URL to provide access to the application.
{: tip}

## Lesson 1: Assigning user roles
{: #wks_tutless1}

In this lesson, you will learn about the different roles that you can assign to users in {{site.data.keyword.knowledgestudioshort}}.

### About this task
{: #wks_tutless1_about}

The creation of a machine learning model requires input from subject matter experts, project managers, and users who can understand and interpret statistical models. Administrators assign roles to each user, such that they have appropriate authority for their tasks. For more information about user roles, see [Assembling a team](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-team).

### Procedure
{: #wks_tutless1_procedure}

1. Log in to {{site.data.keyword.knowledgestudioshort}} with your administrator ID. If you have an existing {{site.data.keyword.knowledgestudioshort}} instance, you can find it on the {{site.data.keyword.cloud_notm}} [resources page ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/resources){: new_window} under **Services**.
2. Click the Settings icon to open the Service Details page. The page lists all the user IDs that are registered as {{site.data.keyword.knowledgestudioshort}} users. Each user ID has one of the following roles (in decreasing order of included permissions):

    - Admin
    - Project Manager
    - Human Annotator

    For information about user roles, see [User roles in {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-roles).

3. Verify that there is at least one user with the Admin role. A user ID with this role can create workspaces, and act as a project manager or human annotator.
4. If you have access to additional user IDs, verify that there are at least two users with the Human Annotator role.

    > **Note:** Creating a real-life model typically involves multiple human annotators in addition to an administrator or project manager. However, for purposes of the tutorial, you can continue with a single user ID.

5. Optional: Change the role that is assigned to a user ID. From the **Action** column of the table, click the **Edit** link, an then change the assigned user role.

    > **Note:** You can upgrade a user ID to a role with greater permissions, but you cannot downgrade a user with an Admin or Project Manager role to the Human Annotator role.

## Lesson 2: Creating a workspace
{: #wks_tutless2}

In this lesson, you will learn how to create a workspace within {{site.data.keyword.knowledgestudioshort}}.

### About this task
{: #wks_tutless2_about}

A workspace defines all the resources that are required to create a machine learning model, including training documents, the type system, dictionaries, and annotations that are added by human annotators. For more information about workspace creation, see [Creating a workspace](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-create-project).

### Procedure
{: #wks_tutless2_procedure}

1. As a {{site.data.keyword.knowledgestudioshort}} administrator, from your {{site.data.keyword.cloud_notm}} [resources ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/resources){:new_window} page, click the {{site.data.keyword.knowledgestudioshort}} service instance under **Services**.
2. Click **Launch tool**.
3. Click **Create Worskpace**.
4. Specify the details for the new workspace:

    - In the **Workspace name** field, type `My workspace`.
    - In the **Workspace description** field, type `Watson Knowledge Studio tutorial workspace`.
    - In the **Language of documents** field, use the default value, **English**. The sample files you will be using for this tutorial are in English.

5. Click **Create**.

### Results
{: #wks_tutless2_results}

The workspace is created and opens automatically.

### What to do next
{: #wks_tutless2_next}

You can now start configuring the workspace resources, such as the type system.

## Lesson 3: Creating a type system
{: #wks_tutless3}

In this lesson, you will learn how to upload and modify a type system within {{site.data.keyword.knowledgestudioshort}}. You must create or upload a type system before you begin any annotation tasks.

### About this task
{: #wks_tutless3_about}

For more information about type systems, see [Type systems](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-typesystem#wks_typesystem).

### Procedure
{: #wks_tutless3_procedure}

1. Download the <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/en-klue2-types.json" download>en-klue2-types.json <img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a> file to your computer. This file contains an example KLUE type system.
1. Click **Assets**> **Entity Types**.
1. On the Entity Types page, click **Upload**.
1. Upload the `en-klue2-types.json` file from your computer. The uploaded type system is displayed in the table.
1. Browse the type system so you can see the data that was uploaded.
1. Edit an entity type:

    1. Locate the MONEY entity type.
    1. Double-click anywhere in the table row to edit the entity type.
    1. In the **Roles** column, click the **Delete a role** icon ![The "Delete a role" icon.](images/wks_delete.jpg "The "Delete a role" icon.")  next to the AWARD role.

        ![A screen capture of deleting a role from an entity type.](images/wks_tut_delete_role.jpg "A screen capture that shows the cursor hovering over the "Delete a role" icon.")

    1. Click **Save**.

### What to do next
{: #wks_tutless3_next}

After you finish making changes to the type system, you can begin adding documents to your workspace.

## Lesson 4: Adding a dictionary
{: #wks_tutless4}

In this lesson, you will learn how to add a dictionary to a workspace in {{site.data.keyword.knowledgestudioshort}}. Dictionaries are used for pre-annotating text when creating a machine learning model.

### About this task
{: #wks_tutless4_about}

For more information about dictionaries, see [Adding dictionaries to a workspace](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-dictionaries#wks_projdictionaries).

### Procedure
{: #wks_tutless4_procedure}

1. Download the <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/dictionary-items-organization.csv" download>`dictionary-items-organization.csv` <img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a> file to your computer. This file contains dictionary terms in CSV format, suitable for uploading into a {{site.data.keyword.knowledgestudioshort}} dictionary.
1. Click **Assets** > **Dictionaries**.
1. Click **Create Dictionary** to add a dictionary.

    > **Note:** Do not click **Upload dictionary**, which is used to upload a dictionary that you want to use as-is. For the tutorial, you will create a new editable dictionary and then upload terms into it.

1. In the **Name** field, type `Test dictionary` and click **Save** to create the (empty) dictionary.

    The new dictionary is created and automatically opened for editing.

1. In the dictionary pane, click **Upload**.
1. Upload the `dictionary-items-organization.csv` file from your computer. The terms in the file are uploaded into the dictionary.
1. Click **Add Entry** to create a new term. An editable row is added at the top of the table.
1. In the **Surface Forms** column, type `IBM` and `International Business Machines Corporation` on separate lines. (When you begin to type a new surface form, a space is added below for an additional surface form.) Leave the radio button next to `IBM` selected, which indicates that `IBM` is the lemma.
1. In the **Part of Speech** column, select **Noun**.
1. Click **Save**.

    ![A screen capture of the Dictionaries page. The "IBM" dictionary entry is selected and its surface forms and part of speech are highlighted.](images/wks_tutdict4.jpg "A screen capture of the Dictionaries page. The "IBM" dictionary entry is selected and its surface forms and part of speech are highlighted.")

### What to do next
{: #wks_tutless4_next}

After you create a dictionary, you can use it to speed up human annotation tasks by pre-annotating the documents.

## Tutorial summary
{: #wks_tutsum}

While learning about {{site.data.keyword.knowledgestudioshort}}, you created a workspace and added artifacts to it.

### Lessons learned
{: #tcp-ll}

By completing this tutorial, you learned about the following concepts:

- Workspaces
- Type systems
- Dictionaries
