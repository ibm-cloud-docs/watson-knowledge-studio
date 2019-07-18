---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-18"

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

This documentation is for {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. To see the documentation for the previous version of {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [click this link ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/docs/services/knowledge-studio?topic=knowledge-studio-wks_tutboot_intro){: new_window}.
{: tip}

# Pre-annotating documents
{: #wks_tutboot_intro}

This tutorial helps you understand how to pre-annotate documents, which bootstraps the annotation process of human annotation.
{: shortdesc}

## Learning objectives
{: #tba-obj}

After you complete this tutorial, you will know how to pre-annotate documents with a machine learning model.

This tutorial should take approximately 5 minutes to finish. If you explore other concepts related to this tutorial, it could take longer to complete.

## Before you begin
{: #tba-pr}

- You're using a supported browser. For information, see [Browser requirements](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-system-requirements).
- You successfully completed [Getting started with {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutintro), which covers creating a workspace, creating a type system, and adding a dictionary.
- You successfully completed [Creating a machine learning model](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutml_intro).
- You must have at least one user ID in either the Admin or Project Manager role. For information about user roles, see [User roles in {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-roles).

## Results
{: #results}

After completing this tutorial, you will have a set of partially annotated documents. Then, you can assign the documents to human annotators to finish the annotation work.

## Lesson 1: Pre-annotating new documents with a machine learning model
{: #wks_tutboot_ml}

In this lesson, you will learn how to use a machine learning model to pre-annotate documents in {{site.data.keyword.knowledgestudioshort}}.

### About this task
{: #wks_tutboot_ml_about}

After you train a machine learning model, you can use it to pre-annotate new documents that you add to the corpus.

> **Attention:** Do not run a pre-annotator on documents that have been annotated by humans, but not been added to the ground truth yet. If you do, all current annotations will be stripped from the documents.

In this tutorial, you can add a second set of documents by using the `documents-ml.csv` file. Do not re-add the `documents-new.csv` file, since this addition would result in duplicate documents in the ground truth. Duplication causes the following problems:

- If annotations on each document do not match, they lower the quality of the machine learning model.
- If annotations on each document match, they over-train the machine learning model on the duplicated files.

For more information about pre-annotating documents, see [Bootstrapping annotation](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-preannotation), which covers additional methods of pre-annotation.

### Procedure
{: #wks_tutboot_ml_procedure}

1. Log in to {{site.data.keyword.knowledgestudioshort}} as the administrator.
1. Upload more documents to the workspace. You can use the <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/documents-ml.csv" download>`documents-ml.csv` <img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a> file.

    For more information about adding documents to a workspace, see [Adding documents for annotation](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-documents-for-annotation).

1. Create an annotation set that uses the `documents-ml.csv` file as the base set, and assign it to yourself, the administrator.

    After you complete the following steps to pre-annotate the new documents, you can view the annotation set to see how the machine learning model annotated the documents. Typically, you assign annotation sets to one or more human annotators. For more information about creating and assigning annotation sets, see [Adding documents for annotation](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-documents-for-annotation).

1. To pre-annotate the new documents, click **Machine Learning Model** > **Versions**, and then click **Run this model**.
1. Select the document set that you added to the corpus, `documents-ml.csv`, and click **Run**.
1. After the pre-annotation is complete, create a human annotation task that includes the annotation set you created.

    For more information about creating an annotation task, see [Annotation setup](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-annotate-documents).

1. To view the annotations that were applied by the machine learning model to the new documents, open the annotation task.

    Because the new documents were pre-annotated with the machine learning model, human annotation requires less time. For more information about adding annotations by human annotators, see [Annotating documents](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-user-guide).

### Results
{: #wks_tutboot_ml_results}

By using your machine learning model to pre-annotate new document sets, you can expedite human annotation tasks for those documents.
