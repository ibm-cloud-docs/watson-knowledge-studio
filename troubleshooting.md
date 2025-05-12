---

copyright:
  years: 2015, 2022
lastupdated: "2022-05-26"

keywords: faqs, Frequently Asked Questions, Watson Knowledge Studio

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
{:faq: data-hd-content-type='faq'}

This documentation is for {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. To see the documentation for the previous version of {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [click this link](/docs/knowledge-studio?topic=knowledge-studio-troubleshooting).
{: tip}

# FAQs for {{site.data.keyword.knowledgestudioshort}}
{: #wks-faqs}

FAQs for {{site.data.keyword.knowledgestudiofull}} might include questions about data collection or plans. To find all FAQs for {{site.data.keyword.cloud}}, see our [FAQ library](/docs/faqs).
{: shortdesc}

## How do I set data collection options?
{: #content}
{: faq}

For Lite and Standard plans, by default, {{site.data.keyword.knowledgestudioshort}} uses client data to improve the service. This data is used only in aggregate. Client data is not shared or made public.

To prevent {{site.data.keyword.knowledgestudioshort}} from using client data, you must opt out by using at least one of two ways:

- Clear the **Data collection** checkbox on the Service Details page in the {{site.data.keyword.knowledgestudioshort}} application.
- As the owner of the {{site.data.keyword.knowledgestudioshort}} service instance, opt out of all data collection for Watson services at https://{DomainName}/watson/settings.

For Premium plans and Dedicated accounts, {{site.data.keyword.knowledgestudioshort}} does not use client data to improve the service.

For more information, see the latest [{{site.data.keyword.knowledgestudioshort}} service description](https://www.ibm.com/software/sla/sladb.nsf/searchsaas/?searchview&searchorder=4&searchmax=0&query=Knowledge+Studio){: external}.

## Can I deploy custom models across regions?
{: #wks_cr_deploy}
{: faq}

Deployment of models across regions is not supported. A custom model can only be deployed to the same region as your Knowledge Studio instance.

## Can I access Knowledge Studio with an API?
{: #wks_api_access}
{: faq}

At this time, there is no API to interact with {{site.data.keyword.knowledgestudioshort}}.
To launch the {{site.data.keyword.knowledgestudioshort}} application, you click **Launch tool** from within the Manage page for the {{site.data.keyword.knowledgestudioshort}} service instance in the {{site.data.keyword.cloud_notm}} console.  Or you can copy the tool URL and use it to launch the application directly.

## Can I change from a Standard to Lite plan?
{: #wks_plan}
{: faq}

Downgrading your plan for {{site.data.keyword.knowledgestudioshort}} is not supported.  You can, however, manage users, storage, billing, and usage with options such as setting limits or notifications. For information on these management options, refer to [Upgrading your pricing plan](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-upgrade).

## Why can't I create a new instance on the Lite plan?
{: #wks_ts_lite}
{: faq}

You can have only one instance of a Lite plan per service. To create a new instance, delete your existing Lite plan instance. Or upgrade your plan to create more instances of the {{site.data.keyword.knowledgestudioshort}} service.

## When are annotation tasks moved to archive?
{: #wks_archived}
{: faq}

When you revert to an older version of the machine learning model, all annotation tasks are archived because they are no longer valid. In other words, the tasks you were working on are archived because the previous model snapshot was promoted. {{site.data.keyword.knowledgestudioshort}} does not have a capability to re-activate an archived task. You can create new annotation tasks following the snapshot restoration.  To learn more, see [Making machine learning model improvements](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-improve-ml).

## How do I export and import a workspace?
{: #wks_backup}
{: faq}

You can backup and restore a workspace by following the steps in [Backing up and restoring data](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-backup-restore). These backup and restore tasks allow you to perform a manual data migration from one {{site.data.keyword.knowledgestudioshort}} instance to another, backing up your data from one instance and restoring it on another instance.

## Experimental services and features: What does experimental mean?
{: #experimental}
{: faq}

{{site.data.keyword.IBM_notm}} releases experimental services and features for you to try out. These services might be unstable, change frequently in ways that are not compatible with earlier versions, and might be discontinued with short notice. These services and features are not recommended for use in production environments.

For more information about experimental services, see the [{{site.data.keyword.cloud_notm}} documentation ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/docs/get-support/servicessupport.html#s-services-exporcont){: new_window}. For the full details of experimental services, see the latest version of the [{{site.data.keyword.cloud_notm}} Service Description ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/software/sla/sladb.nsf/sla/bm?OpenDocument){: new_window}.
