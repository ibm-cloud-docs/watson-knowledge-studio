---

copyright:
  years: 2015, 2018
lastupdated: "2018-06-12"

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

This documentation is for {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. To see the documentation for the previous version of {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [click this link ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/knowledge-studio/rule-annotator-model-create.html){: new_window}.
{: tip}

# Creating the rule-based model
{: #wks_rule_train}

After defining rules, you can create a rule-based model.
{: shortdesc}

## Procedure
{: #wks_rule_train_procedure}

To create a rule-based model. complete the following steps:

1. Log in as a {{site.data.keyword.knowledgestudioshort}} administrator or project manager, and select your workspace.
1. Select the **Model Management** > **Versions** > **Rule-based** tab.
1. Map the entity types from your type system to one or more classes that you used to define rules.

  After the entity types are mapped, you can [deploy the rule-based model](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html) or use it to [pre-annotate documents](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotrule) in the process of creating a machine learning model.

## Deleting a rule-based model
{: #wks_rule_delete_model}

You cannot delete a rule-based model.

You can delete the workspace that was used to develop the rule-based model, but you cannot delete the model itself. Deleting a model is not the best approach. Instead, recreate the rules that are defined for it. Editing the rules directly changes the behavior of the rule-based model.
