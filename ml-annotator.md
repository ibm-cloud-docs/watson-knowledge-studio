---

copyright:
  years: 2015, 2021
lastupdated: "2021-11-15"

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

This documentation is for {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. To see the documentation for the previous version of {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [click this link](/docs/knowledge-studio?topic=knowledge-studio-ml_annotator).
{: tip}

# Machine learning model creation workflow
{: #ml_annotator}

Create a machine learning model that trains a model you can use to identify entities, coreferences, and relationships of interest in new documents.
{: shortdesc}

Understand the typical workflow for creating a machine learning model in {{site.data.keyword.knowledgestudioshort}}.

All the steps are performed by the project manager, except for the *Annotate documents* step, which is performed by the human annotator. Because human annotators are often subject matter experts, they might be consulted during the creation of workspace resources, such as the type system, also.

![The workflow for developing a machine learning model](images/wks-checklist.svg "Shows the key steps you must perform to create a model") Figure 1. The workflow for developing a machine learning model

## Steps to create or refine a model
{: #ml_annotator_steps}

| **Step** | **Description** |
| --- | --- |
| Create a workspace | See [Creating a workspace](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-create-project). A workspace contains the resources that are used to create the model, including:<br></br>**- Type system:** Upload or create the type system, and define the entity types and relation types that human annotators can apply when annotating text. The model process manager typically works with subject matter experts for your domain to define the type system. See [Establishing a type system](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-typesystem)<br></br>**- Source documents:** Create a corpus by uploading sample documents that are representative of your domain content into the workspace. See [Adding documents for annotation](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-documents-for-annotation). Partition the corpus into document sets, specify the percentage of documents that are shared among all document sets, and assign the document sets to human annotators.<br></br>**- Dictionaries:** Upload or create dictionaries for annotating text. You can choose to manually add dictionary entries or upload entries from a file, and then edit the entries. See [Creating dictionaries](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-dictionaries).|
| **Optional:** Pre-annotate documents | Pre-annotate documents according to the terms in the workspace dictionaries or based on rules that you define. See [Bootstrapping annotation](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-preannotation). |
| Annotate documents | <ol><li>Admins and project managers can annotate documents directly, without needing to create annotation tasks or go through the adjudication process. See [Annotating document sets directly](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-annotating-document-sets-directly).</li><li>The project manager generally assigns annotation tasks to human annotators, configures the inter-annotator agreement threshold, and provides annotation guidelines for the human annotators to follow. See [Creating an annotation task](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-annotate-documents#wks_hatask).</li><li>Human annotators use the ground truth editor to manually annotate documents. A human annotator identifies mentions of interest in your domain content and labels them with entity types. The human annotator also identifies relationships between mentions (for example, Mary is an employee of IBM) and how the mentions co-reference the same entity (such as an occurrence of "she" that refers to Mary). Refer to [Annotating documents](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-user-guide).</li></ol> |
| Adjudicate and promote documents | Accept or reject the ground truth that was generated by human annotators, and adjudicate any annotation differences to resolve conflicts. Evaluating the accuracy and consistency of the human annotation effort might be the responsibility of a senior human annotator or a user with stronger subject matter experience than the project manager. See [Adjudication](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-build-groundtruth#wks_haperform). |
| Train the model | Create the machine learning model. See [Creating a machine learning model](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-train-ml#wks_madocsets). |
| Evaluate the model | Evaluate the accuracy of the model. See [Evaluating annotations added by the model](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-train-ml#wks_matest). Depending on model accuracy, this step might result in the need to repeat earlier steps again and again until optimal accuracy is achieved. See [Analyzing machine learning model performance](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-evaluate-ml) for ideas about what to update based on common performance issues. |
| Publish the model | Export the model. See [Using the machine learning model](/docs/watson-knowledge-studio-data?topic=watson-knowledge-studio-data-publish-ml). |
