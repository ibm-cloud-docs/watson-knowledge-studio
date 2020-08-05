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

This documentation is for {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. To see the documentation for the previous version of {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [click this link](/docs/knowledge-studio?topic=knowledge-studio-wks_rule_train).
{: tip}

# Creating the rule-based model
{: #wks_rule_train}

After defining rules, you can create a rule-based model.
{: shortdesc}

## Procedure
{: #wks_rule_train_procedure}

To create a rule-based model. complete the following steps:

1. Log in as a {{site.data.keyword.knowledgestudioshort}} administrator or project manager, and select your workspace.
1. Select the **Rule-based Model** > **Versions** > **Rule-based Model** tab.
1. Click **Map entity types and classes**.
1. Map the entity types from your type system to one or more classes that you used to define rules.

  After the entity types are mapped, you can [deploy the rule-based model](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-wks_rule_publish) or use it to [pre-annotate documents](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-preannotation#wks_preannotrule) in the process of creating a machine learning model.

## Deleting a rule-based model
{: #wks_rule_delete_model}

You cannot delete a rule-based model.

You can delete the workspace that was used to develop the rule-based model, but you cannot delete the model itself. Deleting a model is not the best approach. Instead, recreate the rules that are defined for it. Editing the rules directly changes the behavior of the rule-based model.
