---

copyright:
  years: 2015, 2018
lastupdated: "2018-04-04"

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

This documentation is for {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. To see the documentation for the previous version of {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [click this link ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/knowledge-studio/rule-annotator-model-use.html){: new_window}.
{: tip}

# Using the rule-based model
{: #wks_rule_publish}

Leverage a rule-based model that you created with {{site.data.keyword.knowledgestudioshort}} by making it available to other {{site.data.keyword.watson}} applications.
{: shortdesc}

**Attention**: You can deploy a rule-based model to make it available for use in these services as an [experimental](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) feature.

Before a model can be deployed for use by a service, you must have a subscription to the service. {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} services are hosted on {{site.data.keyword.Bluemix_notm}}, which is the cloud platform for {{site.data.keyword.IBM_notm}}. See [What is {{site.data.keyword.Bluemix_notm}}? ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.ng.bluemix.net/docs/overview/whatisbluemix.html){: new_window} for more information about the platform. To subscribe to one of the {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} services, create an account from the [{{site.data.keyword.Bluemix_notm}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.ng.bluemix.net/){: new_window} website.

For some of the services, you must know details about the service instance that you plan to deploy to, such as the {{site.data.keyword.Bluemix_notm}} space name and service instance name. The space and instance name information is available from the {{site.data.keyword.Bluemix_notm}} services page.

You can also pre-annotate new documents with the rule-based model. See [Pre-annotating documents with the rule-based model](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotrule) for details.

## Deploying a rule-based model to AlchemyLanguage
{: #wks_rule_bluemix}

This feature enables your applications to use the deployed rule-based model to find and extract entities from documents in your domain.

**Attention**: This is currently an [experimental](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) feature of the service.

### Before you begin

You must have the {{site.data.keyword.alchemylanguageshort}} service Advanced plan to use this custom model.

### About this task

To deploy to this service, you must have an access key from {{site.data.keyword.IBM_notm}} {{site.data.keyword.alchemylanguageshort}}.

The key must belong to an account that is authorized to publish custom models or the model will be deployed successfully, but you will not be able to use it.

When you deploy the rule-based model, you select the version of it that you want to deploy. You must specify the key the first time you deploy a model to {{site.data.keyword.alchemylanguageshort}}. You can then reuse the key with multiple versions of the model that you deploy. Each key has a maximum number of models that can be deployed at the same time.

### Procedure

To deploy a rule-based model to {{site.data.keyword.alchemylanguageshort}} :

1. Log in as a {{site.data.keyword.knowledgestudioshort}} administrator or project manager, and select your workspace.
1. Select the **Model Management** > **Versions** > **Rule-based** tab.
1. Choose the version of the model that you want to deploy.

    If there is only one working version of the model, save the current model for deployment by clicking **Save for Deployment**. Clicking **Save for Deployment** creates a version of the model, which enables you to deploy one version while you continue to improve the current version. Saving the version might take a few minutes. The option to deploy does not appear until after the version is created.

1. Click **Deploy**, choose to deploy it to {{site.data.keyword.alchemylanguageshort}} , and then click **Next**.
1. Either enter the key that you obtained from {{site.data.keyword.alchemylanguageshort}} or select a previously deployed version of the model that has a key that you want to reuse, and click **Deploy**. If the key is valid, a confirmation that contains the model ID is displayed. This confirmation does not mean that the model is ready for use by your applications.
1. The deployment process might take a few minutes. To check the status of the deployment, click **Status** next to the version that you deployed. If the model is still being deployed, the status indicates "publishing". After deployment completes, the status changes to "available" if the deployment was successful, or "error" if problems occurred.

    Status information includes the model ID, the last four digits of the {{site.data.keyword.alchemyapishort}} key, and a log of the deployment process. The model ID (model_id) is how your applications call the machine learning model. Make a note of this model ID because there is no programmatic way to access it later. Use the {{site.data.keyword.alchemyapishort}} key to keep track of the number of deployments per key.

### What to do next

To use the deployed model, you must copy and paste the model ID into your application's API call.

> **Attention:** You cannot use the `GET /info/models` {{site.data.keyword.alchemylanguageshort}} API call to get the model ID of rule-based models programmatically. You can access the model ID of machine learning models with this call, but not the rule-based model ID.

The call must also specify the {{site.data.keyword.alchemylanguageshort}} service that you want to use with the model and your {{site.data.keyword.alchemyapishort}} access key.

The following endpoint is supported:

- **&lt;*input-type*&gt;GetRankedNamedEntities**

    Uses the custom model that you specify in the model parameter to extract a list of mentions of all known entity types that it finds in the input that you provide. Supported input types include text, HTML, or a public URL. See [{{site.data.keyword.alchemylanguageshort}}&gt;Entities ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/smarterplanet/us/en/ibmwatson/developercloud/alchemy-language/api/v1/#entities){: new_window} for more information about the API and the syntax to use.

## Deploying a rule-based model to IBM Watson Discovery
{: #wks_rule_discovery}

Deploy the model to enable an application that uses the {{site.data.keyword.discoveryshort}} service to use the rule-based model to find and extract entities during document enrichment.

**Attention**: This is currently an [experimental](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) feature of the service.

### Before you begin

You must have administrative access to a {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}} service instance, and know the {{site.data.keyword.Bluemix_notm}} space and instance names that are associated with it.

### Procedure

To deploy a rule-based model to {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}} , complete the following steps:

1. Log in as a {{site.data.keyword.knowledgestudioshort}} administrator or project manager, and select your workspace.
1. Select the **Model Management** > **Versions** > **Rule-based** tab.
1. Choose the version of the model that you want to deploy.

    If there is only one working version of the model, save the current model for deployment by clicking **Save for Deployment**. This versions the model, which enables you to deploy one version, while you continue to improve the current version. Saving the version might take a few minutes. The option to deploy does not appear until after the version is created.

1. Click **Deploy**, choose to deploy it to {{site.data.keyword.discoveryshort}}, and then click **Next**.
1. Provide the {{site.data.keyword.Bluemix_notm}} space and instance. If necessary, select a different region.
1. Click **Deploy**.
1. The deployment process might take a few minutes. To check the status of the deployment, click **Status** on the **Versions** tab next to the version that you deployed.

    If the model is still being deployed, the status indicates "publishing". After deployment completes, the status changes to "available" if the deployment was successful, or "error" if problems occurred.

    Once available, make a note of the model ID (model_id). You will provide this ID to the {{site.data.keyword.discoveryshort}} service to enable the service to use your custom model.

### What to do next

To use the deployed model, you must provide the model ID when it is requested during the {{site.data.keyword.discoveryshort}} service enrichment configuration process.

## Deploying a rule-based model to IBM Watson Natural Language Understanding
{: #wks_rule_nlu}

Deploy the rule-based model to enable an application that uses the {{site.data.keyword.nlushort}} service to use the model to find and extract entities that are relevant to your domain.

**Attention**: This is currently an [experimental](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) feature of the service.

### Before you begin

You must be have administrative access to a {{site.data.keyword.nlushort}} service instance, and know the {{site.data.keyword.Bluemix_notm}} space and instance names that are associated with it.

### Procedure

To deploy a rule-based model to {{site.data.keyword.nlushort}} , complete the following steps:

1. Log in as a {{site.data.keyword.knowledgestudioshort}} administrator or project manager, and select your workspace.
1. Select the **Model Management** > **Versions** > **Rule-based** tab.
1. Choose the version of the model that you want to deploy.

    If there is only one working version of the model, save the current model for deployment by clicking **Save for Deployment**. This versions the model, which enables you to deploy one version, while you continue to improve the current version. Saving the version might take a few minutes. The option to deploy does not appear until after the version is created.

1. Click **Deploy**, choose to deploy it to {{site.data.keyword.nlushort}}, and then click **Next**.
1. Provide the {{site.data.keyword.Bluemix_notm}} space and instance. If necessary, select a different region.
1. Click **Deploy**.
1. The deployment process might take a few minutes. To check the status of the deployment, click **Status** on the **Versions** tab next to the version that you deployed.

    If the model is still being deployed, the status indicates "publishing". After deployment completes, the status changes to "available" if the deployment was successful, or "error" if problems occurred.

    Once available, make a note of the model ID (model_id). You will provide this ID to the {{site.data.keyword.nlushort}} service to enable the service to use your custom model.

### What to do next

To use the deployed model, you must specify the model ID of your custom model in the `entities.model` parameter.

You can use the model with the {{site.data.keyword.nlushort}} `GET /analyze` request to extract entities.

See the [{{site.data.keyword.nlushort}} documentation ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/doc/natural-language-understanding/index.html){: new_window} for more details.

## Undeploying models
{: #undeploy-view-model}

If you want to undeploy a model or find a model ID, view the **Deployed Models** page. The **Deployed Models** page shows all the {{site.data.keyword.knowledgestudioshort}} models that are deployed to services in the spaces that you have access to.

To undeploy models or find model IDs:

1. Log in as a {{site.data.keyword.knowledgestudioshort}} administrator or project manager, and select your workspace.
1. From the **Settings** menu in the top right menu bar, select **Manage deployed models**.
1. From the list of deployed models, find the model you want to view or undeploy.
1. To undeploy the model, from the last column of that row, click **Undeploy model**.
1. To find the model ID, see the **Model ID** column.

## Leveraging a rule-based model in IBM Watson Explorer
{: #wks_rule_export}

Export the PEAR file that is produced when the rule-based model is created so it can be used in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.

### Procedure

To leverage a rule-based model in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, complete the following steps.

1. Log in as a {{site.data.keyword.knowledgestudioshort}} administrator or project manager, and select your workspace.
1. Select the **Model Management** > **Versions** > **Rule-based** tab.
1. Click **Export current model**.

    If you have a free plan subscription, no export option is available.

    The model is saved as a PEAR file, and you are prompted to download the file. A PEAR (Processing Engine ARchive) file is the UIMA standard packaging format for UIMA components. The model is saved in PEAR format so it can be distributed and reused within UIMA applications.

1. Download the file to your local system.
1. From the {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer application, import the PEAR file.
