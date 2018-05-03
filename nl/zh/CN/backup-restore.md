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

本文档适用于 {{site.data.keyword.cloud}} 上的 {{site.data.keyword.knowledgestudiofull}}。要查看 {{site.data.keyword.IBM_notm}} Marketplace 上先前版本的 {{site.data.keyword.knowledgestudioshort}} 的文档，请[单击此链接 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/docs/services/knowledge-studio/backup-restore.html){: new_window}。
{: tip}

# 备份和复原数据
{: #backup-restore}

如果需要备份和复原 {{site.data.keyword.knowledgestudioshort}} 的工作空间，请执行这些任务。此外，如果需要执行从一个 {{site.data.keyword.knowledgestudioshort}} 实例到另一个实例的手动数据迁移（例如从 {{site.data.keyword.IBM_notm}} Marketplace 上的实例迁移到 {{site.data.keyword.cloud_notm}} 上的实例时），也请执行这些任务。
{: shortdesc}

_手动数据迁移_是备份一个实例中的数据并在另一个实例上复原这些数据的过程。

**注**：{{site.data.keyword.cloud_notm}} 上的 {{site.data.keyword.knowledgestudioshort}} 使用术语_工作空间_，而 {{site.data.keyword.IBM_notm}} Marketplace 上的 {{site.data.keyword.knowledgestudioshort}} 使用术语_项目_。这两个术语功能相同。只是术语表达不同而已。

要备份和复原数据，请完成以下步骤：

1. [了解可以备份的数据](#data)
1. [备份准备](#prepare)
1. [从当前实例中导出工件](#export)
1. [在新实例上重新创建工作空间](#recreateproj)
1. [复原工作空间数据](#restoredata)
1. [复原模型](#restoremodels)
1. [复原任何未完成的注释任务](#restoretasks)

## 可以备份的数据
{: #data}

可以手动备份和迁移以下工件：

- 可编辑的字典
- 类型系统
- 核准的参考标准文档集

无法手动备份和迁移以下类型的工件：

- 正在进行中的人工注释文档
- 注释任务
- 模型和快照
- 只读字典

## 备份准备
{: #prepare}

要准备备份和复原数据，请完成以下步骤：

1. 完成工作空间中正在进行中的任何工作。

    - >**重要信息**：完成任何正在进行中的注释任务。只能备份已注释、裁定、核准并升级为参考标准的文档。如果不完成注释工作，那么将丢失所有正在进行中但未全部完成的注释工作。

    - 如果创建了注释任务来跟踪要执行的工作，但尚未开始任何注释工作，并且要到复原工作空间之后才会开始注释，请创建未完成注释任务的列表。请确保记下已导入但尚未添加到参考标准的文档集。另外，请记下您将每个文档集分配给谁进行注释。复原工作空间后，需要重新上传这些文档集，并重新创建注释任务。

1. 了解记号化器的使用。

    对于机器学习模型，缺省情况下，工作空间使用基于机器学习的记号化器。如果您使用的是基于字典的记号化器，并且有明确需求要继续使用此记号化器，那么可以将工作空间配置为在复原工作空间时使用基于字典的记号化器。有关更多信息，请参阅[记号化器](/docs/services/watson-knowledge-studio/create-project.html#wks_tokenizer)。

1. 管理模型资源。

    无法迁移模型、其版本和快照数据。但可以迁移用于培训这些工件的资源（只读字典除外）。因此，在迁移之后，可以重新创建模型。生成的模型将与迁移之前生成的模型执行相同的操作，因为用于培训的资源是相同的。

    **注意**：如果您具有已部署的模型，并且计划在备份后删除工作空间，请从部署中撤销该模型。从备份复原工作空间后，可以重新构建并重新部署该模型。有关取消部署模型的信息，请参阅[取消部署机器学习模型](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model)和[取消部署基于规则的模型](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model)。

    **请注意，如果未能从部署中撤销模型，那么结果会产生_孤立_的部署模型。孤立的部署模型会继续在您的每月帐单上生成费用。**

1. 管理只读字典信息。

    无法迁移只读字典。请了解只读字典是从何处导入的，以便在迁移后可以将其重新上传到工作空间。

1. 创建当前用户角色的列表。

    **注**：此步骤是可选的。通常在跨实例迁移工作空间且新工作空间必须与原始工作空间完全相同时，才会执行此操作。如果要仅将工作空间数据迁移到新工作空间中，可以跳过此步骤。

    如果要跨不同实例迁移工作空间，请考虑为要备份的实例创建用户及其角色的列表。具有 Admin 角色的人员可以在“用户帐户管理”页面中打印该列表。在新实例上重新创建工作空间后，具有 Admin 角色的人员必须添加这些用户并分配其角色。

    有关角色的更多信息，请参阅[组建团队](/docs/services/watson-knowledge-studio/team.html)。

1. 记下工作空间信息。

    虽然您仍有权访问当前实例，但还是请针对要迁移的每个工作空间，记下以下信息：
    - 工作空间名称
    - 工作空间描述
    - 工作空间所有者
    - 语言
    - 如果有任何未完成的注释任务（这些任务由于无法备份或迁移而未完成），请记下分配给工作空间中的未完成任务的人类注释者。另请记下注释任务详细信息，例如任务名称、到期日期以及哪些文档集分配给哪些用户。

## 下载工件
{: #export}

对于要迁移的每个工作空间，请下载以下工件。将这些工件存储在安全的位置，日后可以将其上传到新实例中。

- 类型系统
- 字典

  **注**：将仅下载可编辑的字典。无法下载只读字典。

- 文档

  有关如何下载这些工件以便可将其导入到新工作空间中的信息，请参阅[从其他工作空间上传资源](/docs/services/watson-knowledge-studio/exportimport.html)。

## 重新创建工作空间
{: #recreateproj}

**注**：在此步骤中，唯一必须与原始（已下载）工作空间的设置相匹配的设置是语言。其余设置可以与原始工作空间的设置不同。

通过将以下信息从先前实例复制到新实例，重新创建每个工作空间：

- 工作空间名称
- 工作空间描述
- 文档的语言（此设置必须与原始工作空间中的设置相匹配）
- 如果先前在工作空间中使用了基于字典的记号化器，并且有合理的需求要继续使用此记号化器，那么必须指定您希望在创建工作空间时使用基于字典的记号化器，而不使用缺省记号化器。有关这些选项的更多信息，请参阅[记号化器](/docs/services/watson-knowledge-studio/create-project.html#wks_tokenizer)。

  要使用基于字典的记号化器，请展开“创建工作空间”窗口（在 {{site.data.keyword.IBM_notm}} Marketplace 中是“创建工作空间“窗口）的“高级选项”部分，然后更改记号化器设置。

## 复原工作空间数据
{: #restoredata}

重新创建工作空间后，请上传先前下载的工件：

1. 从先前创建的类型系统备份上传类型系统。
   有关详细信息，请参阅[从其他工作空间上传资源](/docs/services/watson-knowledge-studio/exportimport.html)。

  **注**：必须上传类型系统后，才能上传要从已备份工作空间中迁移的其他任何工件。

1. 从先前创建的字典备份上传字典。
   有关详细信息，请参阅[从其他工作空间上传资源](/docs/services/watson-knowledge-studio/exportimport.html)。

  如果在先前版本的工作空间中使用了任何只读字典，请将其从原始源重新上传到此工作空间。

  **注**：添加字典时，会自动创建字典预注释器。在运行预注释器时，将该字典与实体类型相关联。

1. 将您从先前版本的工作空间下载的文档上传到此版本的工作空间。
   有关详细信息，请参阅[从其他工作空间上传资源](/docs/services/watson-knowledge-studio/exportimport.html)。

## 复原模型
{: #restoremodels}

此时，用于培训先前（已备份）版本的工作空间中模型的所有工件现在都可用于此新实例。

要重新部署在先前实例中部署的机器学习模型，请完成以下步骤：

1. 培训机器学习模型。有关详细信息，请参阅[创建机器学习模型](/docs/services/watson-knowledge-studio/train-ml.html)。

  **注**：不要对迁移到此工作空间的已注释文档运行任何预注释器，因为这会导致文档丢失人类注释者在其中添加的任何注释。

1. 创建模型后，请对其进行重新部署。有关详细信息，请参阅[使用机器学习模型](/docs/services/watson-knowledge-studio/publish-ml.html)。

要重新部署在先前实例中部署的基于规则的模型，请完成以下步骤：

1. [创建基于规则的模型](/docs/services/watson-knowledge-studio/rule-annotator-model-create.html)。
1. [部署基于规则的模型](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html)。

## 复原未完成的注释任务
{: #restoretasks}

如果在先前的工作空间中有已创建但未完成的任何注释任务，请完成以下步骤来重新创建未完成的注释任务：

1. 上传尚未注释但希望添加到参考标准以继续改进模型的任何文档。
1. 从新导入且未注释的文档中，创建要注释的文档集。这些集现在称为_注释集_。有关详细信息，请参阅[创建和分配注释集](/docs/services/watson-knowledge-studio/document-for-annotation.html)。
1. 重新创建注释任务。为任务提供相同的名称、相应的到期日期，并将注释集分配给相应的人类注释者。
