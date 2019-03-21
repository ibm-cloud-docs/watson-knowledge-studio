---

copyright:
  years: 2015, 2018
lastupdated: "2018-09-11"

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

This documentation is for {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. To see the documentation for the previous version of {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [click this link ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/docs/services/knowledge-studio/create-project.html){: new_window}.
{: tip}

# Creating a workspace
{: #create-project}

The first step in building a custom model is to create a workspace.
{: shortdesc}

## About this task

For each model that you want to build and use, you create a single workspace that contains the artifacts and resources needed to build the model. You then train the model to produce a custom model that can be deployed to an external service for use.

Before creating a workspace, answer these questions:

- **What type of model do you want to create?**

    - Machine learning model: Uses statistical approach to finding entities and relationships in documents. This type of model can adapt as the amount of data grows.
    - Rule-based model: Uses a declarative approach to finding entities in documents. This type of model is more predictable, and is easier to comprehend and maintain. However, it does not learn from new data. It can only find patterns it has been taught to look for.
    - If you want to create a custom categories model, see [Creating a custom categories model](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-create-categories-model).

    > **Note:** You can also create one workspace that contains both one rule-based model and one machine learning model.

- **What services will use the model?**

    See [{{site.data.keyword.watson}} services integration](/docs/services/watson-knowledge-studio/index.html#wks_watsoninteg) for information about the other {{site.data.keyword.watson}} services that custom models can be used with.

## Procedure

To create a workspace, complete the following steps:

1. Log in as a {{site.data.keyword.knowledgestudioshort}} administrator, and click **Create Workspace**.

    > **Note:** People with the project manager role can perform almost all tasks except creating a workspace. An administrator must create the workspace initially and assign project managers to it.

1. Give the workspace a name. Choose a short name that reflects your domain content or the purpose of the model. If you need to, you can change the workspace name later.
1. Identify the language of the documents in your workspace. The documents that you add to the workspace, and the dictionaries that you create or upload, must be in the language that you specify.
1. Optional: If you want to change the tokenizer that is used by the application from the default machine learning-based tokenizer, then you can expand the **Advanced Options** section, and choose **Dictionary-based tokenizer**.

    The default tokenizer is more advanced than the dictionary-based tokenizer; it uses machine learning to identify the tokens in the source documents based on the statistical learning it has done in the language of the source documents. It identifies tokens with more precision because it understands the more natural and nuanced patterns of language. The dictionary-based tokenizer identifies tokens based on language rules. See [Tokenizers](/docs/services/watson-knowledge-studio/create-project.html#wks_tokenizer) for more details.

1. Optional: If you want to add project managers to the workspace, then expand the **Advanced Options** section, and select the names of people you want to add as project managers from the list. The administrator can add or remove project managers later by editing the workspace.

    Only the names of people that you assigned to the project manager role from the User Account Management page for the instance are displayed. See [Assembling a team](/docs/services/watson-knowledge-studio/team.html) for more information about adding users.

    > **Note:** If you have a Lite plan subscription, skip this step. You cannot add other users, so you cannot assign anyone to the project manager role. You do not need a separate project manager. As an administrator, you can perform all the tasks that a project manager would typically perform.

1. Click **Create**.

## What to do next

After the workspace is created, you can start configuring the workspace resources.

To change the workspace description or workspace name, or to add or remove project managers later, an administrator can edit the workspace. From the {{site.data.keyword.knowledgestudioshort}} home page, click the **Show menu** icon on the workspace tile, and choose the **Edit** menu option.

**Related concepts**:

[Uploading resources from another workspace](/docs/services/watson-knowledge-studio/exportimport.html)

**Related reference**:

[Language support](/docs/services/watson-knowledge-studio/language-support.html)

## Tokenizers
{: #wks_tokenizer}

A tokenizer groups characters into tokens, and tokens into sentences. A token is loosely equivalent to a word.

The actions that a tokenizer must take to identify a document's tokens differ depending on the language of the document. In English, tokens are often equated to words as delimited by white spaces in a sentence. However, they do not always match one-to-one with words; other textual elements are considered tokens in some situations. For example, punctuation at the end of a sentence is considered a token, and contractions are often expanded into two tokens. In languages that do not use white spaces, such as Chinese, more complicated statistical algorithms are used to identify the tokens.

The tokenization process is important because it determines the groups of characters that users can highlight for annotation in the ground truth editor. Annotations of entity and relation mentions are generally aligned with token boundaries, and must be labeled within a sentence; they cannot span sentence boundaries.

### Supported types

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

<table summary="This table provides a summary of input, output, and limitations for all model types.">
  <caption>Table 1. All model types</caption>
  <tr>
    <th style="vertical-align:bottom; text-align:left" id="d25459e252">
      Task
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e254">
      Typical usage
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e256">
      Supported input formats
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e258">
      Supported output formats
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e260">
      Limits and requirements
    </th>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e252">
      <p>Type system management</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e254">
      <p>Create a type system or upload and modify an existing type system.</p>
      <p>Define entity types and relation types for your domain.</p>
      <p>You cannot see a visualization of the type system.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e256">
      <ul>
        <li>
          <p>JSON file that you downloaded from a {{site.data.keyword.knowledgestudioshort}} workspace</p>
        </li>
        <li>
          <p>ZIP file that you downloaded from the Human Annotation Tool (HAT)</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e258">
      <ul>
        <li>
          <p>JSON</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e260">
      <p>To avoid visual overload for human annotation, define no more than 50 entity types and 50 relation types.</p>
      <p>File size limitation for uploading a type system: 20 MB</p>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e252">
      <p>Dictionary management</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e254">
      <p>Upload a CSV dictionary file in read-only mode or a ZIP of dictionaries that you downloaded from another workspace.</p>
      <p>Create a new dictionary, and then upload a CSV file of term entries or add term entries to it.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e256">
      <p>Dictionary file:</p>
      <ul>
        <li>
          <p>CSV file in UTF-8 format</p>
        </li>
        <li>
          <p>ZIP of dictionaries downloaded from another workspace</p>
        </li>
      </ul>
      <p>Term entries file:</p>
      <ul>
        <li>
          <p>CSV file in UTF-8 format</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e258">
      <ul>
        <li>
          <p>CSV file in UTF-8 format</p>
        </li>
        <li>
          <p>ZIP of dictionaries to use in another workspace</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e260">
      <p>File size limitations:</p>
      <ul>
        <li>
          <p>1 MB per CSV term entries file</p>
        </li>
        <li>
          <p>16 MB per CSV read-only dictionary file</p>
        </li>
        <li>
          <p>15,000 entries per dictionary, except a read-only dictionary</p>
        </li>
        <li>
          <p>64 dictionaries per workspace</p>
        </li>
      </ul>
    </td>
  </tr>
</table>

 {: #wks_formats__datasimpletable_xxj_qr5_2y}

### Machine learning model

<table summary="This table provides a summary of input, output, and limitations for the machine learning model.">
  <caption>Table 2. Machine learning model</caption>
  <tr>
    <th style="vertical-align:botton; text-align:left" id="d25459e331">Task</th>
    <th style="vertical-align:botton; text-align:left" id="d25459e333">Typical usage</th>
    <th style="vertical-align:botton; text-align:left" id="d25459e335">Supported input formats</th>
    <th style="vertical-align:botton; text-align:left" id="d25459e337">Supported output formats</th>
    <th style="vertical-align:botton; text-align:left" id="d25459e339">Limits and requirements</th>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>Document management </p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
      <p>Upload a small, representative subset of documents</p>
      <p>Upload documents that contain annotations previously added by a human annotator, a machine learning model, or a UIMA analysis engine</p>
      <p>You cannot ingest the entire corpus from {{site.data.keyword.ibmwatson_notm}} Explorer for calculating high value documents for annotation.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <ul>
        <li>
          <p>CSV file in UTF-8 format</p>
        </li>
        <li>
          <p>Text in UTF-8 format</p>
        </li>
        <li>
          <p>HTML</p>
        </li>
        <li>
          <p>PDF files (scanned and password-protected files are not supported)</p>
        </li>
        <li>
          <p>Microsoft Word DOC or DOCX files (password-protected files are not supported)</p>
        </li>
        <li>
          <p>ZIP file that contains documents downloaded from another workspace</p>
        </li>
        <li>
          <p>ZIP file that contains documents in UIMA CAS XMI format</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <ul>
        <li>
          <p>ZIP archive file of documents</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <ul>
        <li>
          <p>40,000 characters per document</p>
        </li>
        <li>
          <p>10,000 documents per workspace</p>
        </li>
        <li>
          <p>1,000 document sets (including annotation sets) per workspace</p>
        </li>
        <li>
          <p>5 MB per file and 200 MB per upload (TXT, PDF, DOC, DOCX, and HTML files)</p>
        </li>
      </ul>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>Pre-annotation</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
       <p>Use a dictionary or {{site.data.keyword.nlufull}} pre-annotator to provide a starting point for human annotation.</p>
       <p>You cannot re-annotate a corpus from {{site.data.keyword.ibmwatson_notm}} Explorer.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <p>Raw documents.</p>
      <p><b>Note:</b> Do not pre-annotate documents that a human annotator has already annotated, or you will lose the work done by the human annotator.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <p>Partly-annotated documents</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <p>None</p>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>Document annotation</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
      <p>Manage human annotation</p><p>Annotate entities, relations, and coreference chains to create ground truth</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <p>Annotation task</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <p>Ground truth</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <ul>
        <li>
          <p>256 active annotation tasks per workspace</p>
        </li>
      </ul>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>Training and refinement</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
      <p>Train a supervised machine learning model to extract domain-specific information from unstructured text.</p><p>Evaluate and improve a supervised machine learning model.</p>
      <p>You cannot create a semi-supervised or unsupervised machine learning model.</p>
      <p>You cannot do extensive feature engineering.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <p>Not applicable</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <p>Machine learning model</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <ul>
        <li>
          <p>1 machine learning model per workspace</p>
        </li>
        <li>
          <p>10 model versions per workspace</p>
        </li>
        <li>
          <p>Maximum number of workspaces is determined by your subscription plan.</p>
        </li>
        <li>
          <p>The maximum number of training actions you can perform per month is determined by your subscription plan.</p>
        </li>
      </ul>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>Publication</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
      <p>Publish a machine learning model to use for performing text extraction in other {{site.data.keyword.watson}} applications.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <p>Not applicable</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <ul>
        <li>
          <p>Model ID (for use in {{site.data.keyword.nlufull}} or {{site.data.keyword.discoveryfull}})</p>
        </li>
        <li>
          <p>ZIP file (for use in {{site.data.keyword.ibmwatson_notm}} Explorer)</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <p>To deploy to {{site.data.keyword.watson}} services, you must know the {{site.data.keyword.cloud_notm}} service space and instance names.</p>
    </td>
  </tr>
</table>

### Rule-based model

<table summary="This table provides a summary of input, output, and limitations for the rule-based model.">
  <caption>Table 3. Rule-based model</caption>
  <tr>
    <th style="vertical-align:bottom; text-align:left" id="d25459e509">
      Task
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e511">
      Typical usage
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e513">
      Supported input formats
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e515">
      Supported output formats
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e517">
      Limits and requirements
    </th>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e509">
      <p>Rule editor</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e511">
      <p>Create or upload documents to the rule editor from which to define classes, regular expressions, and rules.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e513">
      <ul>
        <li>
          <p>Plain text (added in editor)</p>
        </li>
        <li>
          <p>CSV file in UTF-8 format</p>
        </li>
        <li>
          <p>Copied from the All document set</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e515">
      <p>None</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e517">
      <ul>
        <li>
          <p>1 rule-based model per workspace</p>
        </li>
        <li>
          <p>5,000 characters per document</p>
        </li>
        <li>
          <p>100 documents per workspace</p>
        </li>
        <li>
          <p>Maximum size of document title is 256 characters</p>
        </li>
        <li>
          <p>200 rules per workspace</p>
        </li>
        <li>
          <p>400 classes per workspace</p>
        </li>
        <li>
          <p>100 regular expression group per workspace</p>
        </li>
        <li>
          <p>100 regular expression entries per regular expression group</p>
        </li>
        <li>
          <p>1,000 characters per regular expression entry</p>
        </li>
        <li>
          <p>5 rule-based model versions per workspace</p>
        </li>
      </ul>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e509">
      <p>Publication</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e511">
      <p>Publish a rule-based model to use for performing pattern recognition in other {{site.data.keyword.watson}} applications.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e513">
      <p>Not applicable</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e515">
      <ul>
        <li>
          <p>Model ID (for use in {{site.data.keyword.nlufull}} or {{site.data.keyword.discoveryfull}})</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e517">
      <p>To deploy to {{site.data.keyword.watson}} services, you must know the {{site.data.keyword.cloud_notm}} service space and instance names.</p>
    </td>
  </tr>
</table>
