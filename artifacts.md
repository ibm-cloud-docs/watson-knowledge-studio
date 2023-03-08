---

copyright:
  years: 2015, 2023
lastupdated: "2023-03-08"

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

# Types of artifacts
{: #artifacts}

First create or upload artifacts to use to train the models.
{: shortdesc}

The models learn about the following types of artifacts that you add to the workspace:

- **Type system**

    A type system defines the entities and relationships between entities that matter to you. See [Establishing a type system](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-typesystem).

- **Dictionaries**

    A dictionary groups together words and phrases that should be treated equivalently by a model. See [Creating dictionaries](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-dictionaries).

- **Documents**

    Documents serve a different purpose depending on whether you are creating a machine learning model or a rule-based model. See the following topics for more information:
    - Machine learning model documents: [Adding documents for annotation](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-documents-for-annotation)
    - Rule-based model documents: [Adding documents for defining rules](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-wks_rule_anno_add)

You can upload many of these artifacts from external resources, including artifacts that you downloaded from other {{site.data.keyword.knowledgestudioshort}} workspaces. See [Uploading resources from another workspace](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-exportimport) for information about uploading artifacts from other workspaces.

See [Summary of inputs, outputs, and limitations](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-create-project#wks_formats) for key facts about artifacts, such as size limits and supported file types for imported artifacts.
