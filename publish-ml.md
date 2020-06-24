---

copyright:
  years: 2015, 2020
lastupdated: "2020-06-24"

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

This documentation is for {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. To see the documentation for the previous version of {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [click this link](/docs/knowledge-studio?topic=knowledge-studio-publish-ml){: external}.
{: tip}

# Using the machine learning model
{: #publish-ml}

Leverage a machine learning model that you trained with {{site.data.keyword.knowledgestudioshort}} by making it available to other {{site.data.keyword.watson}} applications.
{: shortdesc}

You can deploy or export a machine learning model. A dictionary or {{site.data.keyword.nlushort}} pre-annotator can only be used to pre-annotate documents within {{site.data.keyword.knowledgestudioshort}}.

Before a model can be deployed for use by a service, you must have a subscription to the service. {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} services are hosted on {{site.data.keyword.Bluemix_short}}, which is the cloud platform for {{site.data.keyword.IBM_notm}}. See [What is {{site.data.keyword.cloud_notm}}?](/docs/overview)for more information about the platform. To subscribe to one of the {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} services, create an account from the [{{site.data.keyword.cloud_notm}}](https://{DomainName}/){: external} website.

For some of the services, you must know details about the service instance that you plan to deploy to, such as the {{site.data.keyword.cloud_notm}} space name and service instance name. The space and instance name information is available from the {{site.data.keyword.cloud_notm}} Services page.

You can also pre-annotate new documents with the machine learning model. See [Pre-annotating documents with the machine learning model](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-preannotation#wks_preannotsire) for details.

## Deploying a machine learning model to IBM Watson Discovery
{: #wks_madiscovery}

When you are satisfied with the performance of the model, you can deploy a version of it to {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}. This feature enables your applications to use the deployed machine learning model to enrich the insights that you get from your data to include the recognition of concepts and relations that are relevant to your domain.

### Before you begin
{: #wks_madiscovery_prereqs}

You must have administrative access to a {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}} service instance, and know the {{site.data.keyword.cloud_notm}} space and instance names that are associated with it.

### About this task
{: #wks_madiscovery_about}

When you deploy the machine learning model, you select the version of it that you want to deploy.

### Procedure
{: #wks_madiscovery_procedure}

To deploy a machine learning model to {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}, complete the following steps:

1. Log in as a {{site.data.keyword.knowledgestudioshort}} administrator or project manager, and select your workspace.
1. Select **Machine Learning Model** > **Versions**.
1. Choose the version of the model that you want to deploy.

    If there is only one working version of the model, create a snapshot of the current model. This versions the model, which enables you to deploy one version, while you continue to improve the current version. The option to deploy does not appear until you create at least one version.

    Each version can be deployed to any number of service instances. Each deployed instance of a model version is given a unique **Model ID**, but is identical in all other ways.
    {: tip}

1. Click **Deploy**, choose to deploy it to {{site.data.keyword.discoveryshort}}, and then click **Next**.
1. Select the {{site.data.keyword.cloud_notm}} space and instance. If necessary, select a different region.
1. Click **Deploy**.
1. The deployment process might take a few minutes. To check the status of the deployment, click **Status** on the **Versions** tab next to the version that you deployed.

    If the model is still being deployed, the status indicates "deploying". After deployment completes, the status changes to "available" or "deployed" if the deployment was successful, or "error" if problems occurred.

    Once available, make a note of the model ID (model_id). You will provide this ID to the {{site.data.keyword.discoveryshort}} service to enable the service to use your custom model.

### What to do next
{: #wks_madiscovery_next}

To use the deployed model, you must provide the model ID when it is requested during the {{site.data.keyword.discoveryshort}} service enrichment configuration process. For more information, see [Integrating with Watson Knowledge Studio](/docs/discovery?topic=discovery-integrating-with-wks) in the {{site.data.keyword.discoveryshort}} documentation.

## Deploying a machine learning model to IBM Watson Natural Language Understanding
{: #wks_manlu}

When you are satisfied with the performance of the model, you can deploy a version of it to {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.nlushort}}. This feature enables your applications to use the deployed machine learning model to analyze semantic features of text input, including entities and relations.

### Before you begin
{: #wks_manlu_prereqs}

You must have a {{site.data.keyword.nlushort}} service to deploy to. And you must know the {{site.data.keyword.cloud_notm}} space and instance names that are associated with the service. If you do not remember the space or instance names, find them by logging in to {{site.data.keyword.cloud_notm}}. If you do not have an {{site.data.keyword.cloud_notm}} account, sign up for an account.

### About this task
{: #wks_manlu_about}

When you deploy the machine learning model, you select the version of it that you want to deploy.

### Procedure
{: #wks_manlu_procedure}

To deploy a machine learning model to the {{site.data.keyword.nlushort}} service, complete the following steps:

1. Log in as a {{site.data.keyword.knowledgestudioshort}} administrator or project manager, and select your workspace.
1. Select **Machine Learning Model** > **Versions**.
1. Choose the version of the model that you want to deploy.

    If there is only one working version of the model, create a snapshot of the current model. This versions the model, which enables you to deploy a version, while you continue to improve the current version. The option to deploy does not appear until you create at least one version.

    Each version can be deployed to any number of service instances. Each deployed instance of a model version is given a unique **Model ID**, but is identical in all other ways.
    {: tip}

1. Click **Deploy**, choose to deploy it to {{site.data.keyword.nlushort}}, and then click **Next**.
1. Select the {{site.data.keyword.cloud_notm}} space and instance. If necessary, select a different region.
1. Click **Deploy**.
1. The deployment process might take a few minutes. To check the status of the deployment, click **Status** on the **Versions** tab next to the version that you deployed. If the model is still being deployed, the status indicates "publishing". After deployment completes, the status changes to "available" if the deployment was successful, or "error" if problems occurred.

    Once available, make a note of the model ID (model_id). You will provide this ID to the {{site.data.keyword.nlushort}} service to enable the service to use your custom model.

### What to do next
{: #wks_manlu_next}

You can list deployed model in the {{site.data.keyword.nlushort}} service instance by calling the following API method.

```sh
curl --user "apikey:{apikey}" "{url}/v1/models?version=2018-11-16"
```
{: pre}

Any deployed models will be returned in an array similar to the following one:

```javascript
{
  "models": [
    {
      "workspace_id": "{workspace_id}",
      "version_description": "{version_description}",
      "version": "{version}",
      "status": "available",
      "name": null,
      "model_id": "10:7abc4c2f-5846-3334-b8f7-af5a6fad3398",
      "language": "en",
      "description": null,
      "created": "2018-11-28T17:08:00.000000Z"
    }
  ]
}
```
{: codeblock}

The `{workspace_id}`, `{version_description}`, and `{version}` will all match the information listed on the **Versions** page of your {{site.data.keyword.knowledgestudioshort}} service instance.

To use the deployed model, you must specify the model ID of your custom model in the `entities.model` parameter of an **analyze** call.

You can use the model with the {{site.data.keyword.nlushort}} `GET /analyze` request to extract the following features:

- **entities**

    The following command finds the entities that are present in the sentence that is passed by using the text parameter:

    ```sh
    curl --user "apikey":"{apikey}" "{url}/v1/analyze?version=2018-09-21"
    --request POST
    --header "Content-Type: application/json"
    -d '{"text": "Vehicle 1, a 1995 Honda Civic was traveling north on a two lane
           undivided roadway, negotiating a curve to the left on an upgrade.",
            "features": {
              "entities": {
                "model": "your-model-id-here"
              }
            }
         }'
    ```
    {: pre}

    The service returns a JSON object of instances that it finds of entity types that are defined in the custom model:

    ```javascript
    {
      "language": "en",
      "entities": [
        {
          "type": "MANUFACTURER",
          "text": "Honda",
          "count": 1
        },
        {
          "type": "MODEL",
          "text": "Civic",
          "count": 1
        },
        {
          "type": "VEHICLE",
          "text": "Vehicle 1",
          "count": 1
        },
        {
          "type": "STRUCTURE",
          "text": "two lane undivided roadway",
          "count": 1
        },
        {
          "type": "STRUCTURE",
          "text": "curve",
          "count": 1
        },
        {
          "type": "MODEL_YEAR",
          "text": "1995",
          "count": 1
        },
        {
          "type": "CONDITION",
          "text": "negotiating",
          "count": 1
        }
      ],
      "language": "en"
    }
    ```
    {: codeblock}

- **relations**

    The following command finds the relationships that are present in the sentence that is passed by using the text parameter:

    ```sh
    curl --user "apikey":"{apikey}" "{url}/v1/analyze?version=2018-09-21"
    --request POST
    --header "Content-Type: application/json"
    -d '{"text": "Vehicle 1, a 1995 Honda Civic was traveling north on a two lane
           undivided roadway, negotiating a curve to the left on an upgrade.",
            "features": {
              "relations": {
                "model": "your-model-id-here"
              }
            }
         }'
    ```
    {: pre}

    The service returns a JSON object of instances that it finds of relation types that are defined in the custom model:

    ```javascript
    {
      "relations": [
        {
          "type": "timeOf",
          "sentence": "Vehicle 1, a 1995 Honda Civic was traveling north
           on a two lane undivided roadway, negotiating a curve to
           the left on an upgrade.",
          "score": 0.954254,
          "arguments": [
            {
              "text": "1995",
              "entities": [
                {
                  "type": "Date",
                  "text": "1995"
                }
              ]
            },
            {
              "text": "Honda Civic",
              "entities": [
                {
                  "type": "SportingEvent",
                  "text": "Honda Civic"
                }
              ]
            }
          ]
        },
        {
          "type": "locatedAt",
          "sentence": "Vehicle 1, a 1995 Honda Civic was traveling north
           on a two lane undivided roadway, negotiating a curve to
           the left on an upgrade.",
          "score": 0.40592,
          "arguments": [
            {
              "text": "negotiating",
              "entities": [
                {
                  "type": "EventMeeting",
                  "text": "negotiating"
                }
              ]
            },
            {
              "text": "roadway",
              "entities": [
                {
                  "type": "Facility",
                  "text": "roadway"
                }
              ]
            }
          ]
        }
      ],
      "language": "en"
    }
    ```
    {: codeblock}

See the [{{site.data.keyword.nlushort}} documentation](/docs/natural-language-understanding){: external} for more details.

## Deploying the same model version to multiple services
{: #wks_secdep}

If you wish to deploy a specific version of the same machine learning model to multiple {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} service instances, navigate to the **Versions** page and click the **Deploy** link on the row of the version that you want to deploy to an additional service.

## Undeploying models
{: #pm-um}

If you want to undeploy a model or find a model ID, view the **Deployed Models** page.

### About this task
{: #pm-att}

What you see on the Deployed Models page depends on the [region](/docs/resources?topic=resources-services_region)that hosts your {{site.data.keyword.knowledgestudioshort}} instance. If the region supports instances managed by [IAM](/docs/iam?topic=iam-userroles)and [Cloud Foundry](/docs/iam?topic=iam-cfaccess) access management methods, you see a tab for each method. Models from instances that are managed by IAM are listed on the **Resource Groups** tab. Models from instances that are managed by Cloud Foundry are listed on the **Organizations** tab.

If the region supports instances managed by only one of the access management methods, you see only one list of models, because only one access management method is applicable.

### Procedure
{: #pm-pr}

To undeploy models or find model IDs:

1. Launch {{site.data.keyword.knowledgestudioshort}}.
1. From the **Settings** menu in the top right menu bar, select **Manage deployed models**.
1. From the list of deployed models, find the model you want to view or undeploy.
1. To undeploy the model, from the last column of that row, click **Undeploy model**.
1. To find the model ID, see the **Model ID** column.

Alternatively, you can undeploy models from the Versions pages for rule-based models and machine learning models.

## Deleting a version
{: #wks_delete_model_version}

If you wish to delete a specific version a same machine learning model, navigate to the **Versions** page and click the **Delete** link on the row of the version that you want to delete.
**Note:** The **Delete** model version link is only active if there are no deployed models associated with it. **Undeploy** all associated models before deleting the a version.

## Leveraging a machine learning model in IBM Watson Explorer
{: #wks_maexport}

Export the trained machine learning model so it can be used in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.

### Before you begin
{: #wks_maexport_prereqs}

If you choose to identify relation types and annotate them, then you must define at least two relation types, and annotate instances of the relationships in the ground truth before you export the model. Defining and annotating only one relation type can cause subsequent issues in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, release 11.0.1.0.

### About this task
{: #wks_maexport_about}

Now that the machine learning model is trained to recognize entities and relationships for a specific domain, you can leverage it in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.

Click [this link](https://www.youtube.com/watch?v=1VoS-xczBow&amp;feature=youtu.be){: external} to watch a less than 2 minute video that illustrates how to export a model and use it in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.

### Procedure
{: #wks_maexport_procedure}

To leverage a machine learning model in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, complete the following steps.

1. Log in as a {{site.data.keyword.knowledgestudioshort}} administrator or project manager, and select your workspace.
1. Select **Machine Learning Model** > **Versions**.
1. Click **Export current model**.

    If you have a Lite plan subscription, no export option is available.

    The model is saved as a ZIP file, and you are prompted to download the file.

1. Download the file to your local system.
1. From the {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer application, import the model.

    You can then map the model to a machine learning model in {{site.data.keyword.watson}} Explorer Content Analytics. After you perform the mapping step, when you crawl documents, the model finds instances of the entities and relations that your model understands. To learn how to import and configure the model in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, see the technical document that describes the integration: [https://www.ibm.com/support/pages/node/597611](https://www.ibm.com/support/pages/node/597611){: external}.

#### Related tasks
{: #wks_maexport_related}

[Exporting analyzed documents from {{site.data.keyword.watson}} Explorer Content Analytics](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-preannotation#wks_uimawexca)
