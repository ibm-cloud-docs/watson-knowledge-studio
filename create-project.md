---

copyright:
  years: 2015, 2022
lastupdated: "2022-03-14"

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

This documentation is for {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. To see the documentation for the previous version of {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [click this link](/docs/knowledge-studio?topic=knowledge-studio-create-project).
{: tip}

# Creating a workspace
{: #create-project}

The first step in building a custom model is to create a workspace.
{: shortdesc}

## About this task
{: #cp-att}

For each model that you want to build and use, you create a single workspace that contains the artifacts and resources needed to build the model. You then train the model to produce a custom model that can be deployed to an external service for use.

Before creating a workspace, answer these questions:

- **What type of model do you want to create?**

    - Machine learning model: Uses statistical approach to finding entities and relationships in documents. This type of model can adapt as the amount of data grows.
    - Rule-based model: Uses a declarative approach to finding entities in documents. This type of model is more predictable, and is easier to comprehend and maintain. However, it does not learn from new data. It can only find patterns it has been taught to look for.
    - Advanced Rules model: offers deeper customization for text analysis than rule-based models. See [Creating an advanced rules model](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-create-advanced-rules-model) for instructions.

    You can also create one workspace that contains both one rule-based model and one machine learning model.
    {: tip}

- **What services will use the model?**

    See [{{site.data.keyword.watson}} services integration](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-wks_overview_full#wks_watsoninteg) for information about the other {{site.data.keyword.watson}} services that custom models can be used with.

## Procedure
{: #cp-pr}

To create a workspace, complete the following steps:

1. Log in as a {{site.data.keyword.knowledgestudioshort}} administrator, and click **Create Workspace**.

    People with the project manager role can perform almost all tasks except creating a workspace. An administrator must create the workspace initially and assign project managers to it.
    {: tip}

1. Give the workspace a name. Choose a short name that reflects your domain content or the purpose of the model. If you need to, you can change the workspace name later.
1. Identify the language of the documents in your workspace. The documents that you add to the workspace, and the dictionaries that you create or upload, must be in the language that you specify.
1. Optional: If you want to change the tokenizer that is used by the application from the default machine learning-based tokenizer, then you can expand the **Advanced Options** section, and choose **Dictionary-based tokenizer**.

    The default tokenizer is more advanced than the dictionary-based tokenizer; it uses machine learning to identify the tokens in the source documents based on the statistical learning it has done in the language of the source documents. It identifies tokens with more precision because it understands the more natural and nuanced patterns of language. The dictionary-based tokenizer identifies tokens based on language rules. See [Tokenizers](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-create-project#wks_tokenizer) for more details.

1. Optional: If you want to add project managers to the workspace, then expand the **Advanced Options** section, and select the names of people you want to add as project managers from the list. The administrator can add or remove project managers later by editing the workspace.

    Only the names of people that you assigned to the project manager role from the User Account Management page for the instance are displayed. See [Assembling a team](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-team) for more information about adding users.

    If you have a Lite plan subscription, skip this step. You cannot add other users, so you cannot assign anyone to the project manager role. You do not need a separate project manager. As an administrator, you can perform all the tasks that a project manager would typically perform.
    {: tip}

1. Click **Create**.

## What to do next
{: #cp-ne}

After the workspace is created, you can start configuring the workspace resources.

To change the workspace description or workspace name, or to add or remove project managers later, an administrator can edit the workspace. From the {{site.data.keyword.knowledgestudioshort}} home page, click the **Show menu** icon on the workspace tile, and choose the **Edit** menu option.

**Related concepts**:

[Uploading resources from another workspace](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-exportimport)

**Related reference**:

[Language support](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-language-support)

## Tokenizers
{: #wks_tokenizer}

A tokenizer groups characters into tokens, and tokens into sentences. A token is loosely equivalent to a word.

The actions that a tokenizer must take to identify a document's tokens differ depending on the language of the document. In English, tokens are often equated to words as delimited by white spaces in a sentence. However, they do not always match one-to-one with words; other textual elements are considered tokens in some situations. For example, punctuation at the end of a sentence is considered a token, and contractions are often expanded into two tokens. In languages that do not use white spaces, such as Chinese, more complicated statistical algorithms are used to identify the tokens.

The tokenization process is important because it determines the groups of characters that users can highlight for annotation in the ground truth editor. Annotations of entity and relation mentions are generally aligned with token boundaries, and must be labeled within a sentence; they cannot span sentence boundaries.

### Supported types
{: #cp-st}

{{site.data.keyword.knowledgestudioshort}} supports the following tokenizers:

- **Machine learning-based tokenizer (default)**

    This is a more advanced tokenizer that identifies the tokens in the source documents based on the statistical learning it has done in the language of the source documents. This tokenizer finds tokens that capture the more natural and nuanced patterns of language. You cannot customize this tokenizer.

- **Dictionary-based tokenizer**

    This tokenizer is based on linguistic dictionaries. It finds tokens that follow the rules of the source document language. Only advanced users can customize this tokenizer.

You must choose the tokenizer that you want to use when you create the workspace. You cannot switch to a different tokenizer later. For best results, use the default tokenizer. Only advanced users who want to modify the tokenizer behavior through a deterministic dictionary mechanism can choose the dictionary-based tokenizer. They can then customize it by adding new entries to the dictionary. However, customization must be done carefully because when you add new words to the dictionary, the changes can impact the machine learning model in unintended ways.

## Summary of inputs, outputs, and limitations
{: #wks_formats}

Different stages of model development require different inputs and produce different outputs.

For each stage of the model development process, this table summarizes the typical activities that you perform, the supported input file formats, the outputs that can be produced, and any sizing limits or other requirements.

### All model types
{: #cp-amt}

Table 1: All model types
| **Task** | **Typical usage** | **Supported input formats** | **Supported output formats** | **Limits and requirements** |
| --- | --- | --- | --- | --- |
| Type system management | Create a type system or upload and modify an existing type system. Define entity types and relation types for your domain. You cannot see a visualization of the type system. | <ul><li>JSON file that you downloaded from a {{site.data.keyword.knowledgestudioshort}} workspace.</li><li>ZIP file that you downloaded from the Human Annotation Tool (HAT)</li></ul> | JSON | To avoid visual overload for human annotation, define no more than 50 entity types and 50 relation types. File size limitation for uploading a type system: 20 MB |
| Dictionary management | Upload a CSV dictionary file in read-only mode or a ZIP of dictionaries that you downloaded from another workspace. Create a new dictionary, and then upload a CSV file of term entries or add term entries to it. | Dictionary file: <ul><li>CSV file in UTF-8 format</li><li>ZIP of dictionaries downloaded from another workspace</li></ul>Term entries file:<ul><li>CSV file in UTF-8 format</li></ul> | <ul><li>CSV file in UTF-8 format</li><li>ZIP of dictionaries to use in another workspace</li></ul> | File size limitations:<ul><li>1 MB per CSV term entries file</li><li>16 MB per CSV read-only dictionary file</li><li>15,000 entries per dictionary, except a read-only dictionary</li><li>64 dictionaries per workspace</li></ul> |

 {: #wks_formats__datasimpletable_xxj_qr5_2y}

### Machine learning model
{: #cp-mlm}

Table 2: Machine learning model
| **Task** | **Typical usage** | **Supported input formats** | **Supported output formats** | **Limits and requirements** |
| --- | --- | --- | --- | --- |
| Document management | Upload a small, representative subset of documents Upload documents that contain annotations previously added by a human annotator, a machine learning model, or a UIMA analysis engine You cannot ingest the entire corpus from {{site.data.keyword.ibmwatson_notm}} Explorer for calculating high value documents for annotation. | <ul><li>CSV file in UTF-8 format</li><li>Text in UTF-8 format</li><li>HTML</li><li>PDF files (scanned and password-protected files are not supported)</li><li>Microsoft Word DOC or DOCX files (password-protected files are not supported)</li><li>ZIP file that contains documents downloaded from another workspace</li><li>ZIP file that contains documents in UIMA CAS XMI format</li></ul> | ZIP archive file of documents | <ul><li>40,000 characters per document</li><li>10,000 documents per workspace</li><li>1,000 document sets (including annotation sets) per workspace</li><li>5 MB per file and 200 MB per upload (TXT, PDF, DOC, DOCX, and HTML files)</li></ul> |
| Pre-annotation | Use a dictionary or {{site.data.keyword.nlufull}} pre-annotator to provide a starting point for human annotation.<br></br>You cannot re-annotate a corpus from {{site.data.keyword.ibmwatson_notm}} Explorer. | Raw documents.<br></br>**Note**:</b> Do not pre-annotate documents that a human annotator has already annotated, or you will lose the work done by the human annotator.| Partly-annotated documents | None |
| Document annotation | Manage human annotation. Annotate entities, relations, and coreference chains to create ground truth | Annotation task | Ground truth | <ul><li>256 active anntation tasks per workspace</li></ul> |
| Training and refinement | Train a supervised machine learning model to extract domain-specific information from unstructured text. Evaluate and improve a supervised machine learning model. You cannot create a semi-supervised or unsupervised machine learning model. You cannot do extensive feature engineering. | Not applicable | Machine learning model | <ul><li>1 machine learning model per workspace</li><li>10 model versions per workspace</li><li>Maximum number of workspaces is determined by your deployment.</li><li>The maximum number of training actions you can perform per month is determined by your deployment.</li></ul> |
| Publication | Export a machine learning model to use for performing text extraction in other Watson applications. | Not applicable | <ul><li>ZIP file</li></ul> | None |

### Rule-based model
{: #cp-rbm}

Table 3: Rule-based model
| **Task** | **Typical usage** | **Supported input formats** | **Supported output formats** | **Limits and requirements** |
| --- | --- | --- | --- | --- |
| Rule editor | Create or upload documents to the rule editor from which to define classes, regular expressions, and rules. | <ul><li>Plain text (added in editor)</li><li>CSV file in UTF-8 format</li><li>Copied from the All document set</li></ul> | None | <ul><li>1 rule-based model per workspace</li><li>5,000 characters per document</li><li>100 documents per workspace</li><li>Maximum size of document title is 256 characters</li><li>200 rules per workspace</li><li>400 classes per workspace</li><li>100 regular expression group per workspace</li><li>100 regular expression entries per regular expression group</li><li>1,000 characters per regular expression entry</li><li>5 rule-based model versions per workspace</li></ul> |
| Publication | Publish a rule-based model to use for performing pattern recognition in other Watson applications. | Not applicable | <ul><li>PEAR file</li></ul> | Rule-based models can currently be exported to IBM Watson Discovery only |
