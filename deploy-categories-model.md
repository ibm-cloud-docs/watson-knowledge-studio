---

copyright:
  years: 2019
lastupdated: "2019-03-20"

subcollection: watson-knowledge-studio

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:warning: .warning}
{:note: .note}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Deploying a custom categories model
{: #deploy-categories-model}

This tutorial describes how to deploy a custom categories model to {{site.data.keyword.nlushort}} or {{site.data.keyword.discoveryshort}}. 
{: shortdesc}

The custom categories feature is experimental. The feature might be unstable, change frequently in ways that are not compatible with earlier versions, and might be discontinued with short notice. This feature is not recommended for use in production environments.
{: warning}

## Before you begin
{: deploy-categories-model-before-you-begin}

1. Make sure you have a version of a custom categories model to deploy. For instructions, see [Creating a custom categories model](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-create-categories-model).
2. Custom categories models can be deployed only to services hosted in the **Dallas** location. If you don't already have one, create a [{{site.data.keyword.nlushort}}](https://{DomainName}/catalog/services/natural-language-understanding) or [{{site.data.keyword.discoveryshort}}](https://{DomainName}/catalog/services/discovery) service instance in the **Dallas** location.

## Procedure
{: #deploy-categories-model-procedure}

1. [Launch the {{site.data.keyword.knowledgestudioshort}} application](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutintro#launching-the-knowledge-studio-application).
2. Click on the categories workspace that contains the model that you want to deploy.
3. Click **Versions** in the left navigation menu.
4. Click **Deploy** next to the version that you want to deploy.
5. Follow the instructions to deploy the model to your service instance.
  1. Select the service that you want to deploy to and click **Next**.
  2. If you are deploying to a Cloud Foundry service instance, select **Spaces**. Otherwise, select **Resource groups**.
  3. Select the space or resource group that contains your service instance. If you don't know which to choose, you can browse your services from the [{{site.data.keyword.cloud_notm}} resources page](https://{DomainName}/resources).
  4. Select your service instance and click **Deploy**.
6. After the deploy is complete, copy the model ID that you receive. You will need to provide the model ID to use the custom model in {{site.data.keyword.nlushort}} and {{site.data.keyword.discoveryshort}}.


### Using the custom categories model
{: #using-the-custom-categories-model}

Use the model ID that you received as the value for the categories **model** option in {{site.data.keyword.nlushort}} and {{site.data.keyword.discoveryshort}}. For details and examples, see the following pages.
  - {{site.data.keyword.nlushort}}: [Customizing](/docs/services/natural-language-understanding?topic=natural-language-understanding-customizing)
  - {{site.data.keyword.discoveryshort}}: [Integrating with Watson Knowledge Studio](/docs/services/discovery?topic=discovery-integrating-with-wks#integrating-with-wks)
