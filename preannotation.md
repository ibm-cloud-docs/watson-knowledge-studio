---

copyright:
  years: 2015, 2025
lastupdated: "2025-05-06"

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

This documentation is for {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. To see the documentation for the previous version of {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [click this link](/docs/knowledge-studio?topic=knowledge-studio-preannotation).
{: tip}

# Bootstrapping annotation
{: #preannotation}

Simplify the job of the human annotator by pre-annotating the documents in a workspace. A pre-annotator is a {{site.data.keyword.knowledgestudioshort}} dictionary, rule-based model, or machine learning model that you can run to find and annotate mentions automatically.
{: shortdesc}

Pre-annotation makes the job of human annotators easier because it covers the straightforward annotations, and gets the job of annotating the documents underway.

The method that you use to pre-annotate documents in no way restricts the ways that you can use the resulting model. For example, just because you use the {{site.data.keyword.nlushort}} service to pre-annotate documents does not mean you must deploy the final machine learning model that you build to the {{site.data.keyword.nlushort}} service.

## Pre-annotation methods
{: #preannotation_methods}

The following pre-annotators are available:

- **{{site.data.keyword.nlushort}}**

    A pre-annotator that you can use to find mentions of entities in your documents automatically. If your source documents have general knowledge subject matter, then this pre-annotator is a good choice for you. If you are working with highly specialized documents that focus on a specific field, such as patent law research, for example, the dictionary pre-annotator or rule-based model might be a better choice.

- **Dictionary**

    Uses a dictionary of terms that you provide and associate with an entity type to find mentions of that entity type in the documents. This choice is best for fields with unique or specialized terminology because this pre-annotator does not analyze the context in which the term is used in the way a machine learning pre-annotator does; it instead relies on the term being distinct enough to have a decipherable meaning regardless of the context in which it is used. For example, it is easier to recognize *asbestos* as a mineral entity type than to determine the entity type of *squash*, which can refer to a vegetable, a sport, or a verb meaning to crush something.

  Dictionary pre-annotators do not recognize entity subtypes. Human annotators can specify entity subtypes for each pre-annotated mention by working on an [annotation task](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-annotate-documents#wks_hatask) with the pre-annotated document.

- **Machine learning**

    Uses a machine learning model to automatically annotate documents. This option is only available if you have created a machine learning model with {{site.data.keyword.knowledgestudioshort}} already. If you add a document set, you can run the machine learning annotator that you created previously to pre-annotate the new documents. If the new set of documents is similar to the documents that were used to train the machine learning annotator originally, then this is probably your best choice for pre-annotation.

- **Rule**

    Uses a rule-based model to automatically annotate documents. This option is only available if you have created a rule-based model with {{site.data.keyword.knowledgestudioshort}} already. If your documents contain common patterns of tokens from which you can derive meaning, this model might be a good choice. It can incorporate some of the function of the dictionary pre-annotator if you enable it, by identifying class types for dictionary terms that it finds in the documents also.

Alternatively, you can upload already-annotated documents, and use them to start training the machine learning model. You cannot run a pre-annotator on annotated documents that you upload or the existing annotations will be stripped from the documents and replaced with annotations produced by the pre-annotator only.

## Running multiple pre-annotators
{: #running-pre-annotators}

{{site.data.keyword.knowledgestudioshort}} allows you to run multiple pre-annotators at once. First, you need to prepare the pre-annotation methods that you want to use. For more information, see the following sections:

- [{{site.data.keyword.nlushort}}](#wks_preannotnlu)
- [Dictionaries](#wks_preannot)
- [Machine learning model](#wks_preannotsire)
- [Rules-based model](#wks_preannotrule)

### Configuring the order of pre-annotators
{: #preannotation-order}

When multiple pre-annotators are used, the first annotation made to a span of text is saved for the results, even if other pre-annotators attempt to annotate the same span of text later in the order. This doesn't apply to human annotations, which are preserved regardless of pre-annotation order.

For example, consider the example text `IBM Watson`. If a dictionary that is first in the order labels `IBM` as an `Organization` entity type, a machine learning model that is second in the order can't annotate `IBM Watson` as a `Software Brand` entity type because that would override the earlier annotation made to `IBM`.

You can view the current order of pre-annotators in the **Order** column on the **Machine Learning Model** > **Pre-annotation** page. To change the order, complete the following steps.

1. Click **Order Settings**.
1. Click the **Move up** and **Move down** arrow** buttons to move pre-annotation methods earlier or later in the order.
1. Click **Save**.
1. Double check the **Order** column on the **Pre-annotation** page to make sure that it matches the order that you want.

### Run pre-annotators
{: #run-pre-annotators}

1. After your pre-annotation methods are prepared and you have configured the order of your pre-annotators, click **Run Pre-annotators**.
1. Select the pre-annotators that you want to use, and then click **Next**.
1. If you want to erase existing annotations made by pre-annotators before running the pre-annotator, select **Wipe previous pre-annotation results**. Human annotations are preserved even if this is selected.
1. Select the document sets that you want to pre-annotate.
1. Click **Run**.

## Pre-annotating documents with {{site.data.keyword.nlushort}}
{: #wks_preannotnlu}

You can use the {{site.data.keyword.nlushort}} service to pre-annotate documents that you add to your corpus.

### Before you begin
{: #wks_preannotnlu_prereqs}

Determine whether the {{site.data.keyword.nlushort}} pre-annotator is likely to add value for your use case. Review the list of supported [{{site.data.keyword.nlushort}} service entity types and subtypes](/docs/natural-language-understanding?topic=natural-language-understanding-entity-types) to determine if there is a natural overlap between them and the types in your type system. If so, continue with this procedure. If not, choose a different pre-annotator to use.

### About this task
{: #wks_preannotnlu_about}

{{site.data.keyword.nlushort}} is a service that offers text analysis through natural language processing. When you use the {{site.data.keyword.nlushort}} pre-annotator, it calls the {{site.data.keyword.nlushort}} service to find and annotate entities in your documents.

You must specify the entity types that you want the service to look for by mapping the {{site.data.keyword.nlushort}} entity types to corresponding {{site.data.keyword.knowledgestudioshort}} entity types that you have added to the {{site.data.keyword.knowledgestudioshort}} type system. Only mentions of entity types that you map will be found and annotated.

### Procedure
{: #wks_preannotnlu_procedure}

To use the {{site.data.keyword.nlushort}} service to pre-annotate documents, complete the following steps:

1. Log in as a {{site.data.keyword.knowledgestudioshort}} administrator and select your workspace.
1. Go to the **Machine Learning Model** > **Pre-annotation** page.
1. Click the overflow menu button in the Natural Language Understanding row, and then click **Map entity types**.

    - The drop-down list of the {{site.data.keyword.nlushort}} entity types is pre-populated with entity types that are recognized by the {{site.data.keyword.nlushort}} service.
    - You must map at least one entity type.
    - You cannot map an {{site.data.keyword.nlushort}} entity type to a {{site.data.keyword.knowledgestudioshort}} entity role, only {{site.data.keyword.knowledgestudioshort}} entity types.
    - You can map more than one {{site.data.keyword.nlushort}} entity type to a single {{site.data.keyword.knowledgestudioshort}} entity type, or the other way around. For example, the following mappings are permitted:

    Table 1. Sample mapping of entity types
    | **Watson Knowledge Studio Entity Type** | **{{site.data.keyword.nlushort}} Entity Type** |
    | --- | --- |
    | ENGINEER<br></br>SCIENTIST | Person |
    | LOCATION | CityTown<br></br>Country |
    {: #wks_preannotnlu__datasimpletable_cm1_y3g_fx}

1. After mapping all the entity types that you want to apply, go the **Machine Learning Model** > **Pre-annotation** page. Click **Run Pre-annotators**.

1. Select {{site.data.keyword.nlushort}}, and then click **Next**.

    The {{site.data.keyword.nlushort}} annotator is not available until you map at least one entity type.

1. ore running the pre-annotator, select **Wipe previous pre-annotation results**. Human annotations are preserved even if this is selected.

1. Select the check box for each document set that you want to pre-annotate.

    If you are running this pre-annotator for the first time, first validate that the pre-annotator can find mentions of the mapped entities as expected. Create one document set that contains a representative document or documents from each distinct data source.
    {: tip}

1. Click **Run**.

    If you are doing a validation check of the pre-annotator, then open the annotated documents and review the annotations that were added. Make sure a sufficient number of accurate annotations were created. If the annotations are accurate, then you can run the annotator again on more and larger document sets. If the annotations are not accurate, then consider mapping different {{site.data.keyword.nlushort}} entity types to your types. If the types do not naturally overlap, then the {{site.data.keyword.nlushort}} pre-annotator is not the best pre-annotator for you to use.

    Pre-annotation is applied to individual documents without regard for the various document sets that a document might belong to. A document that overlaps between a selected document set and an unselected document set will be pre-annotated in both document sets.

### Results
{: #wks_preannotnlu__export-warning}

Ground truth that is produced by documents that were pre-annotated by the {{site.data.keyword.nlushort}} service cannot be used directly outside of {{site.data.keyword.knowledgestudioshort}}. You can download the ground truth (in non-readable form) to move it from one {{site.data.keyword.knowledgestudioshort}} workspace to another. And you can continue to develop the ground truth and use it to build a machine learning model or rule-based model that can be deployed for use in services outside of {{site.data.keyword.knowledgestudioshort}}.

Documents that were pre-annotated with {{site.data.keyword.nlushort}} are obscured into a non-readable format when they are downloaded. But, all annotations in those documents are obscured, including annotations that were added to the documents by human annotators.
{: important}

**Related information**:

[{{site.data.keyword.nlushort}}](https://www.ibm.com/watson/services/natural-language-understanding/){: external}

## Pre-annotating documents with a dictionary
{: #wks_preannot}

To help human annotators get started with their annotation tasks, you can create a dictionary and use it to pre-annotate documents that you add to the corpus.

### About this task
{: #wks_preannot_about}

When a human annotator begins work on documents that were pre-annotated, it is likely that a number of mentions will already be marked by entity types based on the dictionary entries. The human annotator can change or remove the pre-annotated entity types and assign entity types to unannotated mentions. Pre-annotation by a dictionary does not annotate relations, coreferences. Relations and coreferences must be annotated by human annotators.

This task shows you how to create a dictionary that is editable. If you want to upload and pre-annotate your documents with a read-only dictionary, click the **Menu** icon next to the **Create Dictionary** button, and then select **Upload Dictionary**.
{: tip}

### Procedure
{: #wks_preannot_procedure}

To create an editable dictionary and pre-annotate documents, follow these steps:

1. Log in as a {{site.data.keyword.knowledgestudioshort}} administrator and select your workspace.
1. Select the **Assets** > **Dictionaries** page.
1. Click **Create Dictionary**, enter a name, and then click **Save**.
1. From the **Entity type** list, select an entity type to associate with the dictionary.

    You can also associate an entity type with the dictionary from the **Machine Learning Model** > **Pre-annotation** page. Click the overflow menu button in the Dictionaries row in the page, then click **Map entity types**.
    {: note}
1. Add entries for the dictionary or upload a file that contains dictionary terms.
1. Go to the **Machine Learning Model** > **Pre-annotation** page.
1. Click **Run Pre-annotators**.
1. Select **Dictionaries**, and then click **Next**.
1. If you want to erase existing annotations made by pre-annotators before running the pre-annotator, select **Wipe previous pre-annotation results**. Human annotations are preserved even if this is selected.
1. Select the check box for each document set that you want to pre-annotate and click **Run**.

    Pre-annotation is applied to individual documents without regard for the various document sets or annotation sets that a document might belong to. A document that overlaps between a selected document set and an unselected document set will be pre-annotated in both document sets.

**Related information**:

- [Creating dictionaries](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-dictionaries)
- [Getting Started > Adding a dictionary](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutintro#wks_tutless4)

## Pre-annotating documents with the machine learning model
{: #wks_preannotsire}

You can use an existing machine learning model to pre-annotate documents that you add to your corpus.

### About this task
{: #wks_preannotsire_about}

After 10 to 30 documents are annotated, a machine learning model can be trained on the data. Don't use such a minimally trained model in production. However, you can use the model to pre-annotate documents to help speed up the human annotation of subsequent documents. For example, if you add documents to the corpus after you train a machine learning model, you can use the model to pre-annotate the new document sets. Never run a pre-annotator on the same documents that have been annotated by a person. Pre-annotators remove human annotation.

### Procedure
{: #wks_preannotsire_procedure}

To use an existing machine learning model to pre-annotate documents:

1. Log in as a {{site.data.keyword.knowledgestudioshort}} administrator and select your workspace.
1. Go to the **Machine Learning Model** > **Pre-annotation** page.
1. Click **Run Pre-annotators**.
1. Select **Machine Learning Model**, and then click **Next**.
1. If you want to erase existing annotations made by pre-annotators before running the pre-annotator, select **Wipe previous pre-annotation results**. Human annotations are preserved even if this is selected.
1. Select the check box for each document set that you want to pre-annotate and click **Run**.

    Pre-annotation is applied to individual documents without regard for the various document sets or annotation sets that a document might belong to. A document that overlaps between a selected document set and an unselected document set will be pre-annotated in both document sets.

## Pre-annotating documents with the rule-based model
{: #wks_preannotrule}



You can use an existing rule-based model to pre-annotate documents that you add to your corpus.

### Procedure
{: #wks_preannotrule_procedure}

To use the rule-based model to pre-annotate documents, complete the following steps:

1. Log in as a {{site.data.keyword.knowledgestudioshort}} administrator and select your workspace.
1. Go to the **Machine Learning Model** > **Pre-annotation** page.
1. Click the overflow menu button in the Rule-based Model row in the page, then click **Map entity types and classes** to map entity types that you defined in the {{site.data.keyword.knowledgestudioshort}} type system to one or more rule-based model classes.

    You can also open the mapping page by selecting the **Rule-based Model** > **Versions** > **Rule-based Model** tab.
    {: note}

1. Click **Edit** for each entity type you want to map.
    - The drop-down list of the **Class Name** column is pre-populated with classes that are associated with the rule-based model.
    - You must map at least one entity type to a class.
1. On the **Machine Learning Model** > **Pre-annotation** page, click **Run Pre-annotators**.

    The Rule-based Model option is not available until you map at least one entity type to a class.
1. If you want to erase existing annotations made by pre-annotators before running the pre-annotator, select **Wipe previous pre-annotation results**. Human annotations are preserved even if this is selected.
1. Select the document sets or annotation sets that you want to pre-annotate.
1. Click **Run**.

    Pre-annotation is applied to individual documents without regard for the various document sets that a document might belong to. A document that overlaps between a selected document set and an unselected document will appear pre-annotated in both document sets.

## Uploading pre-annotated documents
{: #wks_uima}

You can jump-start the training of your model by uploading documents that were pre-annotated through an Unstructured Information Management Architecture (UIMA) analysis engine.

The pre-annotated documents must be in the XMI serialization form of UIMA Common Analysis Structure (UIMA CAS XMI). The .zip file that you upload must include the UIMA TypeSystem descriptor file and a file that maps the UIMA types to entity types in your {{site.data.keyword.knowledgestudioshort}} type system.

UIMA CAS XMI is a standard format of Apache UIMA. Guidelines are provided for how to create files in the correct format from analyzed collections in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer. If you use another Apache UIMA implementation, adapt these guidelines for your purposes. Regardless of how you create the XMI files, the requirements for creating the type system mapping file and .zip file are the same for everyone.

If you assign the imported documents to human annotators, the documents appear pre-annotated in the ground truth editor and a number of mentions might already be annotated. The human annotator thus has more time to focus on applying the annotation guidelines to unmarked mentions. Alternatively, you can bypass the human annotation step and use the pre-annotated documents to immediately start training and evaluating a machine learning model.

### Exporting analyzed documents from Watson Explorer Content Analytics
{: #wks_uimawexca}

You can export documents that were crawled and analyzed in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer Content Analytics, and upload the analyzed documents as XMI files into a {{site.data.keyword.knowledgestudioshort}} workspace.

#### Procedure
{: #wks_uima_procedure}

To get analyzed documents from a {{site.data.keyword.watson}} Explorer Content Analytics collection, follow these steps:

1. Open the Content Analytics administration console in a web browser.
1. On the Collections view, expand the collection that you want to export documents from. In the Parse and Index pane, ensure that the parse and index process is running, and then click the arrow icon for **Export analyzed document content and metadata**.
1. In the **Analyzed document export options** area, select **Export documents as XML files**, select the **Enable CAS as XMI format export** check box, specify the output path for where the exported data is to be written, and click **OK**.
1. Stop and restart the parse and index services for the collection, and then do one of the following steps:

    - If the collection already contains indexed documents that you want to use for training the machine learning model in the document cache, restart a full index build.
    - If the collection does not contain indexed documents that you want to use for training the machine learning model, upload documents, configure at least one crawler to crawl the documents, and start the crawler.

1. In the **Export** area, check the status of the export request. The progress indicates how many documents are exported.
1. Go to the output folder that you specified when you configured export options. When documents are exported as XML files, the output folder name is based on the time stamp when the export occurs. The output folder contains XMI files (`*.xmi`) and the UIMA TypeSystem descriptor file (`exported_typesystem.xml`).

#### What to do next
{: #wks_uimawexca__preUIMAimport}

You must define a mapping between the UIMA types and {{site.data.keyword.knowledgestudioshort}} entity types. You must also create a .zip file that contains all the files that are required to upload the analyzed data into a {{site.data.keyword.knowledgestudioshort}} workspace.

**Related information**:

- [Exporting crawled or analyzed documents](https://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ad.doc/iiysatexportca.htm){: external}
- [Output paths for exported documents](https://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ad.doc/iiysaexportoutput.htm){: external}

### Exporting an analyzed collection from Content Analytics Studio
{: #wks_uimawexstudio}

You can export a collection of analyzed documents from {{site.data.keyword.watson}} Explorer Content Analytics Studio, and upload the analyzed documents as XMI files into a {{site.data.keyword.knowledgestudioshort}} project.

#### Procedure
{: #wks_uimawexstudio_procedure}

To get analyzed documents from a Content Analytics Studio collection, follow these steps:

1. Launch Content Analytics Studio and open the Studio project.
1. Right-click a folder that contains documents that you want to use for training a machine learning model and select **Analyze Collection**.
1. Select a UIMA pipeline configuration file.
1. Go to the Collection Analysis view and click the **Save** icon in the Collection Analysis view. Specify the folder where the saved results are to be written and specify the file name.
1. Open the folder that you specified. The file extension of the saved file is `.annotations`.
1. Copy the `.annotations` file to your local file system and rename the file extension from `.annotations` to `.zip`.
1. Extract all files from the .zip file. The extracted contents include XMI files (`*.xmi`), the UIMA TypeSystem descriptor file (`TypeSystem.xml`), and other files.

#### What to do next
{: #wks_uimawexstudio_next}

You must define a mapping between the UIMA types and {{site.data.keyword.knowledgestudioshort}} entity types. You must also create a .zip file that contains all of the files that are required to upload the analyzed data into a {{site.data.keyword.knowledgestudioshort}} workspace.

### Mapping UIMA types to entity types
{: #wks_uimawexmap}

Before you upload XMI files into a {{site.data.keyword.knowledgestudioshort}} workspace, you must define mappings between the UIMA types and {{site.data.keyword.knowledgestudioshort}} entity types.

#### Before you begin
{: #wks_uimawexmap_prereqs}

The type system in your {{site.data.keyword.knowledgestudioshort}} workspace must include the entity types that you want to map the UIMA types to.

#### Procedure
{: #wks_uimawexmap_procedure}

To map UIMA types to {{site.data.keyword.knowledgestudioshort}} entity types, follow these steps:

1. Create a file named `cas2di.tsv` in the folder that contains the UIMA TypeSystem descriptor file, such as `exported_typesystem.xml` or `TypeSystem.xml`.
1.  Open the `cas2di.tsv` file with a text editor. Each line in the file specifies a single mapping. The format of the mapping depends on which annotator's annotations you want to map:

    - You can create mappings by using the basic format:

        `UIMA_Type_Name[TAB]WKS_Entity_Type`

        The following example defines mappings between UIMA types produced by the Named Entity Recognition annotator in {{site.data.keyword.watson}} Explorer Content Analytics and entity types defined in a {{site.data.keyword.knowledgestudioshort}} type system:

        ```bash
        com.ibm.langware.Organization  ORGANIZATION
        com.ibm.langware.Person  PERSON
        com.ibm.langware.Location  LOCATION
        ```
        {: screen}

        Another example defines a mapping between UIMA types produced by custom annotator that was created in {{site.data.keyword.watson}} Explorer Content Analytics Studio and {{site.data.keyword.knowledgestudioshort}} entity types:

        ```bash
        com.ibm.Person  PERSON
        com.ibm.Date  DATE
        ```
        {: screen}

    - You can create mappings based on facets that are used in the Pattern Matcher annotator or Dictionary Lookup annotator in {{site.data.keyword.watson}} Explorer Content Analytics. In text analysis rule files (`*.pat`), the facet is represented as the category attribute. To define a mapping, use the following syntax:

        ```bash
        com.ibm.takmi.nlp.annotation_type.ContiguousContext:category={FACET_PATH}[TAB]{WKS_ENTITY_TYPE}
        ```
        {: screen}

        The following example, which applies to the Pattern Matcher and Dictionary Lookup annotators, defines a mapping between the category $.mykeyword.product and the {{site.data.keyword.knowledgestudioshort}} entity type PRODUCT:

        ```bash
        com.ibm.takmi.nlp.annotation_type.ContiguousContext:category=$.mykeyword.product PRODUCT
        ```
        {: screen}

#### What to do next
{: #wks_uimawexmap_next}

You must create a .zip file that contains all of the files that are required to upload the analyzed data into a {{site.data.keyword.knowledgestudioshort}} workspace.

**Related information**:

- [Pattern Matcher annotator](https://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ta.doc/iiystapattmatch.htm){: external}
- [Dictionary Lookup annotator](https://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ta.doc/iiystadictlookup.htm){: external}
- [Named Entity Recognition annotator](https://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ta.doc/iiystasystemt.htm){: external}

### Uploading UIMA CAS XMI files into a workspace
{: #wks_uimaweximport}

To use the pre-annotated documents that you downloaded to train a model, you must create a .zip file that contains all the files required to upload the XMI files, and then upload the .zip file into a {{site.data.keyword.knowledgestudioshort}} workspace.

#### Before you begin
{: #wks_uimaweximport_prereqs}

Before you upload the .zip file, ensure that the type system in your {{site.data.keyword.knowledgestudioshort}} workspace includes the entity types that you mapped the UIMA types to.

UIMA analysis engines allow annotations to span sentences. In {{site.data.keyword.knowledgestudioshort}}, annotations must exist within the boundaries of a single sentence. If the XMI files that you upload include annotations that span sentences, those annotations do not appear in the ground truth editor.
{: important}

#### Procedure
{: #wks_uimaweximport_procedure}

To upload pre-annotated documents into a {{site.data.keyword.knowledgestudioshort}} workspace, follow these steps:

1. Create a .zip file that contains all of the files that are required by {{site.data.keyword.knowledgestudioshort}}.

    1. Select the folder that contains the XMI files, UIMA type system descriptor file, and `cas2di.tsv` file, or select all of the files in the folder.
    1. Create a .zip file that includes all files. Make sure the `cas2di.tsv` and UIMA type system descriptor files are stored in the root directory of the .zip file. These files cannot be stored in a subfolder within the .zip file or {{site.data.keyword.knowledgestudioshort}} will not be able to read them, and nothing will be imported.

        In Windows, you can right-click and select **Send to** > **Compressed (zipped) folder**.

1. Upload the .zip file into a {{site.data.keyword.knowledgestudioshort}} workspace.

    1. Log in as a {{site.data.keyword.knowledgestudioshort}} administrator or project manager, open the workspace that you want to add the documents to, and open the **Assets**> **Documents** page.
    1. Click **Upload Document Sets**.
    1. Drag the .zip file that you created or click to locate and select the file.
    1. Select the check box to indicate that the .zip file contains UIMA CAS XMI files.
    1. Click **Upload**.
