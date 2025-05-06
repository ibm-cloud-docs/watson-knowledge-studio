---

copyright:
  years: 2015, 2020
lastupdated: "2020-06-25"

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

This documentation is for {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. To see the documentation for the previous version of {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [click this link](/docs/knowledge-studio?topic=knowledge-studio-backup-restore).
{: tip}

# Backing up and restoring data
{: #backup-restore}

If you need to backup and restore a workspace for {{site.data.keyword.knowledgestudioshort}}, perform these tasks. Also, if you need to perform a manual data migration from one {{site.data.keyword.knowledgestudioshort}} instance to another, such as when migrating from an instance on {{site.data.keyword.IBM_notm}} Marketplace to an instance on {{site.data.keyword.cloud_notm}}, perform these tasks.
{: shortdesc}

_Manual data migration_ is the process of backing up your data from one instance and restoring it on another instance.

{{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud_notm}} uses the term _workspace_, while {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace uses the term _project_. The functionality is the same. Only the terminology is different.
{: tip}

To back up and restore your data complete the following steps:

1.  [Understand which data can be backed up](#data)
1.  [Prepare for backup](#prepare)
1.  [Download artifacts from the current instance](#export)
1.  [Re-create workspaces on the new instance](#recreateproj)
1.  [Restore the workspace data](#restoredata)
1.  [Restore the models](#restoremodels)
1.  [Restore any incomplete annotation tasks](#restoretasks)

## Data that can be backed up
{: #data}

The following artifacts can be backed up and migrated manually:

- Editable dictionaries
- Type system
- Approved ground truth document sets

The following types of artifacts cannot be backed up and migrated manually:

- In-progress human annotation documents
- Annotation tasks
- Models and snapshots
- Read-only dictionaries

## Preparing for backup
{: #prepare}

To prepare for backing up and restoring your data, complete the following steps:

1.  Complete any work that is in progress in your workspace.

    - Finish any in-progress annotation tasks. Only documents that have been annotated, adjudicated, and approved and promoted to ground truth can be backed up. If you do not finish the annotation work, you will lose any annotation effort that is in progress but not completely done.
    {: important}

    - If you created annotation tasks to track work that you want to do, but none of the annotation work has begun and will not take place until after the workspace is restored, then make a list of the outstanding annotation tasks. Be sure to note the document sets that you imported but that have not been added to the ground truth yet. Also, make a note of whom you assigned to annotate each document set. Re-upload these document sets and re-create the annotation tasks after the workspace is restored.
1.  Understand tokenizer use.

    For machine learning models, workspaces use the machine learning-based tokenizer by default. If you are using a dictionary-based tokenizer and have a specific need to continue doing so, you can configure the workspace to use the dictionary-based tokenizer when you restore it. For more information, see [Tokenizers](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-create-project#wks_tokenizer).
1.  Manage model resources.

    Your model, its versions, and snapshot data cannot be migrated. The resources (except read-only dictionaries) that you used to train those artifacts can be migrated. Therefore, after the migration, you can re-create the model. The model that is produced performs the same as models that you generated before the migration. They use the same resources for training.

    If you have a model that is already deployed and you plan to delete the workspace after you back it up, withdraw the model from deployment. You can rebuild and redeploy the model after you restore the workspace from the backup. For information about undeploying models, see [Undeploying machine learning models](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-publish-ml#pm-um) and [Undeploying rule-based models](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-wks_rule_publish#ramu-um).
    {: important}

    If you fail to withdraw the model from deployment, the result is an _orphaned_ deployed model. Orphaned deployed models continue to generate charges on your monthly bills.
    {: important}
1.  Manage read-only dictionary information.

    Read-only dictionaries cannot be migrated. Find out where the read-only dictionary was imported from, so you can re-upload it to your workspace after the migration.
1.  Make a list of current user roles.

    This step is optional. It is typically performed when a workspace is migrated across instances and the new workspace must be identical to the original workspace. If you want to migrate only the workspace data into a new workspace, you can skip this step.
    {: note}

    If you are migrating workspaces across different instances, consider making a list of users and their roles for the instance that you are backing up. Someone with the Admin role can print the list from the User Account Management page. After the workspaces are re-created on the new instance, someone with the Admin role must add the users and assign their roles.

    For more information about roles, see [User roles in {{site.data.keyword.knowledgestudioshort}}](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-roles).
1.  Make note of workspace information.

    While you still have access to the current instance, for each workspace that you want to migrate, make a note of the following information:
    - Workspace name
    - Workspace description
    - Workspace owner
    - Language
    - If you have any incomplete annotation tasks, because they can't be backed up or migrated, note the human annotators who are assigned to incomplete tasks in the workspace. Also note the annotation task details, such as the task name, due date, and which document sets are assigned to which users.

## Downloading artifacts
{: #export}

For each workspace that you want to migrate, download the following artifacts. Store them in a secure location from which you will be able to upload them into the new instance later.

- Type system
- Dictionaries

    **Note**:
    - Only editable dictionaries will be downloaded. You cannot download read-only dictionaries.
    - For dictionaries, entity type mappings are not migrated. After you restore these artifacts, you will need to map the dictionaries to entity types, as necessary.

- Documents

    For more information about how to download these artifacts so that they can be imported into a new workspace, see [Uploading resources from another workspace](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-exportimport).

## Recreating workspaces
{: #recreateproj}

In this step, the only setting that must match the setting of the original (downloaded) workspace is the language. The rest of the settings can differ from the settings of the original workspace.
{: note}

Re-create each workspace by copying the following information from the previous instance to the new one:

- Workspace name
- Workspace description
- Language of documents (this setting must match the setting in the original workspace)
- If you previously used a dictionary-based tokenizer in the workspace and have a valid need to continue using it, you must specify that you want to use the dictionary-based tokenizer instead of the default tokenizer when you create the workspace. For more information about the options, see [Tokenizers](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-create-project#wks_tokenizer).

    To use a dictionary-based tokenizer, expand the **Advanced Options** section of the "Create Workspace" window (in {{site.data.keyword.IBM_notm}} Marketplace, the "Create Workspace" window) and change the tokenizer setting.

## Restoring workspace data
{: #restoredata}

After re-creating the workspaces, upload the previously downloaded artifacts:

1.  Upload the type system from the previously created type system backup. For more information, see [Uploading resources from another workspace](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-exportimport).

    You must upload the type system before you can upload any other artifacts that you are moving from the backed up workspace.
    {: note}
1.  Upload the dictionaries from the previously created dictionary backup. For more information, see [Uploading resources from another workspace](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-exportimport).

    If you used any read-only dictionaries in the previous version of the workspace, re-upload them into this workspace from their original source.
1.  For dictionary pre-annotators, associate the dictionaries with an entity type. Dictionaries that don't have mappings for entity types will not apply annotations when you pre-annotate documents.
1.  Upload the documents that you downloaded from the previous version of the workspace into this version of the workspace. For more information, see [Uploading resources from another workspace](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-exportimport).

## Restoring models
{: #restoremodels}

At this point, all the artifacts that were used to train the model in the previous (backed up) version of the workspace are now available in this new instance.

To redeploy a machine learning model that you deployed in the previous instance, complete the following steps:

1.  [Train the machine learning model](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-train-ml).

    Do not run pre-annotators on annotated documents that you migrated to this workspace. They will lose annotations that were added by human annotators.
  {: note}
1.  After creating the model, deploy it again. For more information, see [Using the machine learning model](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-publish-ml).

To redeploy a rule-based model that you deployed in the previous instance, complete the following steps:

1.  [Create the rule-based model](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-wks_rule_train).
1.  [Deploy the rule-based model](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-wks_rule_publish).

## Restoring incomplete annotation tasks
{: #restoretasks}

If you had any annotation tasks that were created but not completed in the previous workspace, complete the following steps to re-create the incomplete annotation tasks:

1.  [Upload any documents](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-documents-for-annotation#wks_projadd) that have not been annotated yet but that you want to add to the ground truth to continue to improve the model.
1.  From the newly imported and unannotated documents, [create annotation sets](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutml_intro#wks_tutless_ml2).
1.  [Re-create the annotation tasks](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-annotate-documents#wks_hatask). Give the task the same name and an appropriate due date, and assign annotation sets to the appropriate human annotators.
