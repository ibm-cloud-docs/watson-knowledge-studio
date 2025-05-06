---

copyright:
  years: 2016, 2020
lastupdated: "2020-06-19"

subcollection: watson-knowledge-studio

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:note: .note}
{:important: .important}
{:tip: .tip}
{:download: .download}
{:table: .aria-labeledby="caption"}

# {{site.data.keyword.cloudaccesstrailshort}} events
{: #activity-tracker-events}

Use the {{site.data.keyword.cloudaccesstrailfull}} service to track how users and applications interact with {{site.data.keyword.knowledgestudioshort}} in {{site.data.keyword.cloud}}.
{: shortdesc}

The {{site.data.keyword.cloudaccesstrailfull_notm}} service records user-initiated activities that change the state of a service in {{site.data.keyword.cloud_notm}}. For more information, see the  {{site.data.keyword.at_full_notm}} getting started tutorial [{{site.data.keyword.cloudaccesstrailshort}}](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-getting-started).



## List of events
{: #events}

| Action | Description |
|:-----------------|:-----------------|
| `knowledge-studio.user.create` | Add or activate a user from the **Service Details** page |
| `knowledge-studio.user.update` | Edit a user and click **Apply** from the **Service Details** page (This includes both changing role and description)|
| `knowledge-studio.user.delete` | Deactivate a user from the **Service Details** page |
| `knowledge-studio.document-set.create` | Import documents from the **Documents** page |
| `knowledge-studio.document.delete` | Delete a single document from the **Documents** page |
| `knowledge-studio.document-set.delete` | Delete documents by document set from the **Documents** page |
| `knowledge-studio.rule-document.create` | Create a rule document (Mutliple IDs are created if a *.csv* file is imported)|
| `knowledge-studio.rule-document.update` | Update a rule document |
| `knowledge-studio.rule-document.delete` | Delete a rule document |
| `knowledge-studio.annotation.update` | Save annotation in the ground truth editor |
| `knowledge-studio.preannotation.start` | Save annotation using pre-annotator |
| `knowledge-studio.ml-training.start` | Start training a machine learning model |
| `knowledge-studio.dictionary.create` | Create a dictionary or import dictionaries (*.zip*)|
| `knowledge-studio.preview-only-dictionary.create` | Import a preview only dictionary (*.csv*)|
| `knowledge-studio.dictionary.update` | Edit a dictionary (Create, edit, delete the dictionary entries and import *.csv* file into the dictionary)|
| `knowledge-studio.dictionary.delete` | Delete a dictionary |
| `knowledge-studio.workspace.delete` | Delete a workspace |
{: caption="Actions that generate events" caption-side="top"}

## Where to view the events
{: #where-to-view-events}

{{site.data.keyword.cloudaccesstrailshort}} events are available in the {{site.data.keyword.cloudaccesstrailshort}} **account domain** that is available in the {{site.data.keyword.cloud_notm}} region where the events are generated.
