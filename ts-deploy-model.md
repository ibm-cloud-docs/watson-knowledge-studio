---

copyright:
  years: 2021
lastupdated: "2021-04-26"

keywords: troubleshooting for knowledge studio, 

subcollection: watson-knowledge-studio

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:support: data-reuse='support'}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}
{:troubleshoot: data-hd-content-type='troubleshoot'}

<!-- You must add the troubleshoot content type in your attribute definitions AND on a new line under each troubleshooting topic H1 ID. -->

# How do I troubleshoot an error when deploying a model?
{: #wks_ts_exceeds_limit}
{: troubleshoot}
{: support}

You try to deploy a custom model, but it fails with an error if you exceed a machine learning model limit. {:shortdesc}

When you try to deploy your custom model, the following error appears in a dialog: “owner exceeds allowable model limit” 
{: tsSymptoms}

To resolve the error, you must reduce the number of models by either undeploying or deleting a model. 
{: tsResolve}

If you want to undeploy a model or find a model ID, view the Deployed Models page. See [Undeploying models](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-publish-ml#pm-um).

If the model does not show on the Deployed Models page, list the models in your Natural Language Understanding instance, and then delete the model with the [Natural Language Understanding API](/apidocs/natural-language-understanding#deletemodel).

1. Use list models method to get model id(s)
1. Use delete model method with model id

If you see an error message other than this one, check Cloud Status for any service outages, then go to Support Center for more options to get help.
