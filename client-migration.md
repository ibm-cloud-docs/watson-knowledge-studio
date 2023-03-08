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
{:shortdesc: .shortdesc}

# Migrating to IBM Cloud
{: #migrate}

On December 18, 2017, IBM launched {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud_notm}}, which marks the beginning of the process to migrate all {{site.data.keyword.knowledgestudioshort}} instances from {{site.data.keyword.IBM_notm}} Marketplace to the [{{site.data.keyword.cloud_notm}} platform](https://www.ibm.com/watson/services/knowledge-studio-migration/?mhsrc=ibmsearch_a&mhq=Marketplace){: external}.
{: shortdesc}

{{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud_notm}} uses the term _workspace_, while {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace uses the term _project_. The functionality is the same. Only the terminology is different.
{: tip}

If you need to comply with GDPR, you must migrate to the {{site.data.keyword.cloud_notm}} platform. {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace has been retired and is not suitable for clients who require compliance with the European Union's General Data Protection Regulation (GDPR) (EU) 2016/679.
{: important}

## Before you begin
{: #before-you-begin}

- Determine the {{site.data.keyword.cloud_notm}} resource group you want to migrate your service to. See [Best practices for organizing resources in a resource group
](https://cloud.ibm.com/docs/resources?topic=resources-bp_resourcegroups) for tips. You will need to communicate the name and ID of the resource group to {{site.data.keyword.IBM_notm}} to begin the migration process.
- Decide which {{site.data.keyword.cloud_notm}} region to host your service instance in. View available regions on the [{{site.data.keyword.knowledgestudioshort}} catalog page](https://cloud.ibm.com/catalog/services/knowledge-studio).

## Process
{: #process}

Open a support ticket to start the migration process.

1.  Go to the [New support case](https://cloud.ibm.com/unifiedsupport/cases/add){: external} page in the Support Center.
1.  For the type of support, select **Technical**.
1.  In the **Offering** field, select **AI / Watson**.
1.  Leave the **Search offering resources** field blank.
1.  In the **Subject** field, enter `Migrate Watson Knowledge Studio to IBM Cloud`.
1.  In the **Description** field, include the following information.
    - Region in which your new service instance will be hosted, such as Dallas or Frankfurt
    - Resource group name
    - Resource group ID

After you submit the ticket, a support agent will contact you to schedule the migration.
