---

copyright:
  years: 2020
lastupdated: "2020-08-31"

keywords: troubleshooting storage for knowledge studio, troubleshoot storage space limits

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

# How can I address storage space limits?
{: #wks_ts_storage}
{: troubleshoot}
{: support}

Depending on your subscription plan, you might reach the storage limit that is specified for your plan and be prevented from completing tasks.
{:shortdesc}

You might see a message about exceeding the allowed storage space when you attempt to perform one of these tasks:
{:tsSymptoms}

- Upload documents or dictionaries
- Deploy a model or version a model
- Run a pre-annotator on documents

The storage limit is met or exceeded if the action proceeds.
{:tsCauses}

The largest consumers of storage space are machine learning and rule-based models. To free up space, you can take the following actions:
{:tsResolve}

- Delete snapshot versions of any models that you do not expect to need to revert to.
- Delete any models that you do not need.
- If your models are too important to delete, consider upgrading your plan to one that provides a larger allotment of storage space.

After you remove models or model versions, wait an hour before you retry the action that resulted in the error message. It can take up to an hour for the storage space that you freed up to be available for use.

To manage your monthly bill, if the Admin role is assigned to you and you have a Premium or Standard account, you can set a storage limit on the Service Details page in {{site.data.keyword.knowledgestudioshort}}. To see the Service Details page and set the storage limit, from the top navigation bar in {{site.data.keyword.knowledgestudioshort}}, click the **Settings** icon, click the **View/modify service details** link, and then click the **Set storage limit** link.
{: tip}
