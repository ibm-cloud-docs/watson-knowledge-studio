---

copyright:
  years: 2015, 2018
lastupdated: "2018-04-06"

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

This documentation is for {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. To see the documentation for the previous version of {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [click this link ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/knowledge-studio/exportimport.html){: new_window}.
{: tip}

# Uploading resources from another workspace
{: #exportimport}

To accelerate the creation of a model, you can upload resources like documents (with or without ground truth annotations), a type system, and dictionaries that you downloaded from another workspace.
{: shortdesc}

The ability to separately download and upload different resources gives you flexibility when designing and creating a model. For example, you might create one workspace to design the type system and perform human annotation, and then create a separate workspace, perhaps in a separate instance of {{site.data.keyword.knowledgestudioshort}} with different users, to train the machine learning model. Being able to upload the resources, including the ground truth created by human annotators, makes this scenario possible.

You cannot download and upload a machine learning model. Instead, you can download all of the artifacts that were used to create the model from one workspace and upload them into a new workspace. From the new workspace, you can run training again to recreate the model. The new model should produce similar results to the original model because they were both trained with the same set of artifacts.

The files that you download are operating system-independent. The {{site.data.keyword.knowledgestudioshort}} instances where you download and upload files do not have to run the same version of Linux.

## Type systems
{: #wks_exportimport_expimp_type}

To download a type system, open the **Assets & Tools** > **Entity Types** page and click **Download Types**. The system creates a file named `types-ID.json` and prompts you to download the file to your local system. To use this type system in a new workspace, open the **Entity Types** page and upload the `JSON` file that you downloaded.

## Dictionaries
{: #wks_exportimport_expimp_dict}

To download one or more dictionaries, select the **Assets & Tools** > **Pre-annotators** > **Dictionaries** tab, and click **Download Dictionaries**. For each dictionary that you download, the system creates a file named `dictionary name_timestamp.csv`, combines the files into a `ZIP` file named `workspace name_dictionary_timestamp.zip`, and prompts you to download the file to your local system. You can also download an individual dictionary by opening the dictionary and clicking **Download**. Preview-only dictionaries that you uploaded as a dictionary CSV file cannot be downloaded.

Before you upload a downloaded dictionary into a new workspace, you must download the type system from the old workspace and upload it into the new workspace. The type system and dictionaries must originate from the same {{site.data.keyword.knowledgestudioshort}} workspace, and the type system must exist in the new workspace before you upload the dictionaries.

To upload dictionaries, open the **Dictionaries** tab and either add a `CSV` file that you downloaded or upload the `ZIP` file.

## Documents
{: #wks_exportimport_expimp_doc}

To download documents that you added to the corpus, open the **Assets & Tools** > **Documents** > **Document Sets** tab and click **Download Document Sets**. The system creates a file named `corpus-ID.zip` and prompts you to download the file to your local system. The `ZIP` file contains all documents in the corpus. Annotations that were added to annotation sets are included in the ZIP file, but only after the annotation sets have been approved and promoted to ground truth.

> **Restriction:** Any documents that were pre-annotated will be obscured into a non-readable format when they are downloaded. Even annotations in those documents that were added by human annotation are unreadable.

Before you upload documents that include ground truth into a new workspace, you must download the type system from the old workspace and upload it into the new workspace. The type system and documents must originate from the same {{site.data.keyword.knowledgestudioshort}} workspace, and the type system must exist in the new workspace before you upload the ground truth annotations.

To upload documents, open the **Document Sets** tab in the new workspace, click **Upload Document Sets** and select the corpus `ZIP` file that you downloaded. Specify whether you want the uploaded documents to include or exclude the ground truth annotations before you click **Upload**. Only annotations that were promoted to ground truth before the documents were downloaded will be uploaded.

**Related concepts**:

[Type systems](/docs/services/watson-knowledge-studio/artifacts.html#wks_typesystem)

[Dictionaries](/docs/services/watson-knowledge-studio/artifacts.html#wks_dictionaries)

[Documents for machine learning models](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_t_docs_intro)

[Documents for rule-based models](/docs/services/watson-knowledge-studio/rule-annotator-add-doc.html)
