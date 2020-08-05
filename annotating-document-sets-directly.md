---

copyright:
  years: 2015, 2020
lastupdated: "2020-08-03"

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

# Annotating document sets directly
{: #annotating-document-sets-directly}

Admins and project managers are able to annotate ground truth document sets directly without creating annotation tasks.
{: shortdesc}

## Procedure
{: #annotating-document-sets-procedure}

Annotations that you apply directly to document sets are not applied to active annotation tasks. To avoid unintended overwrites, do not annotate document sets that are involved in active annotation tasks.
{: note}

1. [Launch the {{site.data.keyword.knowledgestudioshort}} application](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutintro#launching-the-knowledge-studio-application).
1. [Add documents to your workspace.](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-documents-for-annotation#wks_projadd)
1. From your workspace menu, click **Machine Learning Model**, then click **Annotations.**
1. Click the **Ground Truth** tab.
1. Click **Annotate** next to the document set that you want to use.
1. Annotate your documents. See [Annotating documents](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-user-guide) for more details.
1. Click **Save** to update the document set with your annotations.

## What to do next
{: #annotating-document-sets-next}

- [Train a machine learning model](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-train-ml).

