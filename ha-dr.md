---

copyright:
  years: 2019
lastupdated: "2019-03-19"

subcollection: watson-knowledge-studio

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

# High availability and disaster recovery
{: #ha-dr}

{{site.data.keyword.knowledgestudiofull}} is highly available within multiple {{site.data.keyword.cloud_notm}} locations (for example, Dallas and Washington, DC). However, recovering from potential disasters that affect an entire location requires planning and preparation.
{: shortdesc}

You are responsible for understanding your configuration, customization, and usage of the service. You are also responsible for being ready to re-create an instance of the service in a new location and to restore your data in any location. See [How do I ensure zero downtime?](/docs/overview?topic=overview-zero-downtime#zero-downtime) for more information.

## High availability
{: #hd-ha}

{{site.data.keyword.knowledgestudioshort}} supports high availability with no single point of failure. The service achieves high availability automatically and transparently by using the multi-zone region (MZR) feature provided by {{site.data.keyword.cloud_notm}}.

{{site.data.keyword.cloud_notm}} enables multiple zones that do not share a single point of failure within a single location. It also provides automatic load balancing across the zones within a region.

## Disaster recovery
{: #hd-dr}

Disaster recovery can become an issue if an {{site.data.keyword.cloud_notm}} location experiences a significant failure that includes the potential loss of data. Because MZR is not available across locations, you must wait for {{site.data.keyword.IBM_notm}} to bring a location back online if it becomes unavailable. If underlying data services are compromised by the failure, you must also wait for {{site.data.keyword.IBM_notm}} to restore those data services.

If a catastrophic failure occurs, {{site.data.keyword.IBM_notm}} might not be able to recover data from database backups. In this case, you need to restore your data to return your service instance to its most recent state. You can restore the data to the same or to a different location.

Your disaster recovery plan includes knowing, preserving, and being prepared to restore all data that is maintained on {{site.data.keyword.cloud_notm}}. This stored data includes the training data for your models.

Re-creating models from saved data takes time. You can maintain parallel service configurations in multiple locations to help eliminate the turnaround time associated with disaster recovery.
{: note}

### Disaster recovery for models
{: #hd-drm}

For models, understand which data can be backed up, restore and re-create necessary artifacts, and then retrain and redeploy the models.

#### Backing up data
{: #hd-bud}

Some data can be backed up, and some must be re-created:

1. [Understand which data can be backed up](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-backup-restore#data)

1. [Prepare for backup](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-backup-restore#prepare)

1. [Download artifacts from the current instance](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-backup-restore#export)


#### Restoring data, models, and tasks
{: #hd-res}

To recover from a disaster:

1. [Recreate workspaces on the new instance](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-backup-restore#recreateproj)

1. [Restore the workspace data](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-backup-restore#restoredata)

1. [Restore the models](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-backup-restore#restoremodels)

1. [Restore any incomplete annotation tasks](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-backup-restore#restoretasks)
