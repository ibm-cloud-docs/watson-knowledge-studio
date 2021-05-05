---

copyright:
  years: 2015, 2021
lastupdated: "2021-05-05"

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

This documentation is for {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. To see the documentation for the previous version of {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [click this link](/docs/knowledge-studio?topic=knowledge-studio-wks_rule_publish).
{: tip}

# Using the rule-based model
{: #wks_rule_publish}

Leverage a rule-based model that you created with {{site.data.keyword.knowledgestudioshort}} by making it available to other {{site.data.keyword.watson}} applications.
{: shortdesc}

You can deploy a rule-based model to make it available for use in these services as an [experimental](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-wks-faqs#experimental) feature.
{: note}

Before a model can be deployed for use by a service, you must have a subscription to the service. {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} services are hosted on {{site.data.keyword.Bluemix_notm}}, which is the cloud platform for {{site.data.keyword.IBM_notm}}. See [What is {{site.data.keyword.Bluemix_notm}}?](/docs/overview) for more information about the platform. To subscribe to one of the {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} services, create an account from the [{{site.data.keyword.Bluemix_notm}}](https://{DomainName}/){: external} website.

For some of the services, you must know details about the service instance that you plan to deploy to, such as the {{site.data.keyword.Bluemix_notm}} space name and service instance name. The space and instance name information is available from the {{site.data.keyword.Bluemix_notm}} services page.

You can also pre-annotate new documents with the rule-based model. See [Pre-annotating documents with the rule-based model](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-preannotation#wks_preannotrule) for details.

## Deploying a rule-based model to IBM Watson Discovery
{: #wks_rule_discovery}

Deploy the model to enable an application that uses the {{site.data.keyword.discoveryshort}} service to use the rule-based model to find and extract entities during document enrichment.

This is currently an [experimental](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-wks-faqs#experimental) feature of the service.
{: note}

### Before you begin
{: #wks_rule_discovery_prereqs}

You must have administrative access to a {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}} service instance, and know the {{site.data.keyword.Bluemix_notm}} space and instance names that are associated with it.

### Procedure
{: #wks_rule_discovery_procedure}

To deploy a rule-based model to {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}} , complete the following steps:

1. Log in as a {{site.data.keyword.knowledgestudioshort}} administrator or project manager, and select your workspace.
1. Select the **Rule-based Model** > **Versions** > **Rule-based Model** tab.
1. Choose the version of the model that you want to deploy.

    If there is only one working version of the model, save the current model for deployment by clicking **Save for Deployment**. This versions the model, which enables you to deploy one version, while you continue to improve the current version. Saving the version might take a few minutes. The option to deploy does not appear until after the version is created.

    **Note**: Each version can be deployed to only one service instance. If you want to deploy the same model to more than one instance, create a version for each instance.

1. Click **Deploy**, choose to deploy it to {{site.data.keyword.discoveryshort}}, and then click **Next**.
1. Provide the {{site.data.keyword.Bluemix_notm}} space and instance. If necessary, select a different region.
1. Click **Deploy**.
1. The deployment process might take a few minutes. To check the status of the deployment, click **Status** on the **Versions** tab next to the version that you deployed.

    If the model is still being deployed, the status indicates "publishing". After deployment completes, the status changes to "available" if the deployment was successful, or "error" if problems occurred.

    Once available, make a note of the model ID (model_id). You will provide this ID to the {{site.data.keyword.discoveryshort}} service to enable the service to use your custom model.

### What to do next
{: #wks_rule_discovery_next}

To use the deployed model, you must provide the model ID when it is requested during the {{site.data.keyword.discoveryshort}} service enrichment configuration process.

## Deploying a rule-based model to IBM Watson Natural Language Understanding
{: #wks_rule_nlu}

Uploading an advanced rules model to {{site.data.keyword.nlushort}} is deprecated. As of June 10, 2021, you will not be able to deploy advanced rules models to {{site.data.keyword.nlushort}}.
{: deprecated}

Deploy the rule-based model to enable an application that uses the {{site.data.keyword.nlushort}} service to use the model to find and extract entities that are relevant to your domain.

**Attention**: This is currently an [experimental](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-wks-faqs#experimental) feature of the service.

### Before you begin
{: #wks_rule_prereqs}

You must have administrative access to a {{site.data.keyword.nlushort}} service instance, and know the {{site.data.keyword.Bluemix_notm}} space and instance names that are associated with it.

### Procedure
{: #wks_rule_procedure}

To deploy a rule-based model to {{site.data.keyword.nlushort}} , complete the following steps:

1. Log in as a {{site.data.keyword.knowledgestudioshort}} administrator or project manager, and select your workspace.
1. Select the **Rule-based Model** > **Versions** > **Rule-based Model** tab.
1. Choose the version of the model that you want to deploy.

    If there is only one working version of the model, save the current model for deployment by clicking **Save for Deployment**. This versions the model, which enables you to deploy one version, while you continue to improve the current version. Saving the version might take a few minutes. The option to deploy does not appear until after the version is created.

    **Note**: Each version can be deployed to only one service instance. If you want to deploy the same model to more than one instance, create a version for each instance.

1. Click **Deploy**, choose to deploy it to {{site.data.keyword.nlushort}}, and then click **Next**.
1. Provide the {{site.data.keyword.Bluemix_notm}} space and instance. If necessary, select a different region.
1. Click **Deploy**.
1. The deployment process might take a few minutes. To check the status of the deployment, click **Status** on the **Versions** tab next to the version that you deployed.

    If the model is still being deployed, the status indicates "publishing". After deployment completes, the status changes to "available" if the deployment was successful, or "error" if problems occurred.

    Once available, make a note of the model ID (model_id). You will provide this ID to the {{site.data.keyword.nlushort}} service to enable the service to use your custom model.

### What to do next
{: #wks_rule_next}

To use the deployed model, you must specify the model ID of your custom model in the `entities.model` parameter.

You can use the model with the {{site.data.keyword.nlushort}} `GET /analyze` request to extract entities.

See the [{{site.data.keyword.nlushort}} documentation](/docs/natural-language-understanding) for more details.

## Undeploying models
{: #ramu-um}

If you want to undeploy a model or find a model ID, view the **Deployed Models** page.

### Procedure
{: #ramu-pr}

To undeploy models or find model IDs:

1. Launch {{site.data.keyword.knowledgestudioshort}}.
1. From the **Settings** menu in the top right menu bar, select **Manage deployed models**.
1. From the list of deployed models, find the model you want to view or undeploy.
1. To undeploy the model, from the last column of that row, click **Undeploy model**.
1. To find the model ID, see the **Model ID** column.

Alternatively, you can undeploy models from the Versions pages for rule-based models and machine learning models.

## Leveraging a rule-based model in IBM Watson Explorer
{: #wks_rule_export}

Export the PEAR file that is produced when the rule-based model is created so it can be used in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.

### Procedure
{: #wks_rule_export_procedure}

To leverage a rule-based model in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, complete the following steps.

1. Log in as a {{site.data.keyword.knowledgestudioshort}} administrator or project manager, and select your workspace.
1. Select the **Rule-based Model** > **Versions** > **Rule-based Model** tab.
1. Click **Export current model**.

    If you have a Lite plan subscription, no export option is available.

    The model is saved as a PEAR file, and you are prompted to download the file. A PEAR (Processing Engine ARchive) file is the UIMA standard packaging format for UIMA components. The model is saved in PEAR format so it can be distributed and reused within UIMA applications.

1. Download the file to your local system.
1. From the {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer application, import the PEAR file.
