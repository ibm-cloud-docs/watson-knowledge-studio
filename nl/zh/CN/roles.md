---

copyright:
  years: 2018
lastupdated: "2018-07-02"

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

# {{site.data.keyword.knowledgestudioshort}} 中的用户角色
{: #roles}

{{site.data.keyword.knowledgestudiofull}} 角色用于组织创建机器学习模型或基于规则的模型的人员团队。
{: shortdesc}

## 有关 {{site.data.keyword.knowledgestudioshort}} 中角色的注释
{: #notes}

- {{site.data.keyword.knowledgestudioshort}} 中的用户角色在以下级别进行管理：
  - {{site.data.keyword.cloud}} 角色控制对 {{site.data.keyword.cloud_notm}} 服务的访问。{{site.data.keyword.knowledgestudioshort}} 将 Cloud Foundry 用于访问控制，这就需要 {{site.data.keyword.knowledgestudioshort}} 用户具有开发者角色。有关更多信息，请参阅 [Cloud Foundry 访问权 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/docs/iam/cfaccess.html){: new_window}。
  - {{site.data.keyword.knowledgestudioshort}} 角色控制对 {{site.data.keyword.knowledgestudioshort}} 功能的访问，如本页面中所述。
- 创建 {{site.data.keyword.knowledgestudioshort}} 的实例时不需要 {{site.data.keyword.knowledgestudioshort}} 角色。但是，当某个人员创建 {{site.data.keyword.knowledgestudioshort}} 的实例时，会向第一个要启动 {{site.data.keyword.knowledgestudioshort}} 的用户分配 {{site.data.keyword.knowledgestudioshort}} 管理员角色。
- 要管理工作空间，需要由管理员将项目经理分配到该工作空间。
- 管理员和项目经理可以充当人工注释者角色，但必须将其分配给注释集，正如必须将人工注释者分配给注释集。
- 分配用户角色后，用户角色无法从较高级别降级为较低级别的许可权。管理员无法降级为项目经理或人工注释者，项目经理无法降级为人工注释者。有关添加用户、升级角色和取消激活用户帐户的信息，请参阅[组成团队](/docs/services/watson-knowledge-studio/team.html)。

## 角色描述
{: #descriptions}
下表中描述了 {{site.data.keyword.knowledgestudioshort}} 角色。角色按最高到最低许可权级别的顺序列出。

|角色 |描述|
|------|-------------|
|管理员|负责管理任务，包括管理用户、资源消耗和每月费用。在大型团队设置中，管理员很少参与模型开发过程。
|项目经理|负责自己所分配到的工作空间的总体组织。任务包括创建类型系统，管理资产，管理注释工作，评估机器学习模型以及部署模型。此角色的用户需要与行业主题相关的专业知识，因为他们创建类型系统，培训人工注释者如何正确应用类型系统，并评估模型质量。|
|人工注释者|在自己所分配到的培训文档中执行实体提及项和关系提及项的标记工作。该工作分配给人工注释者并由项目经理进行监视。人工注释者可以没有与行业主题相关的专业知识，只要项目经理教会他们如何正确应用类型系统即可。|
{:caption="表 1. 角色描述" caption-side="top"}

## 角色许可权
{: #permissions}

要比较每个角色的许可权，请参阅下表。每行都列出一种许可权。如果某角色具有该许可权，那么角色列将标记为带有复选标记 (&checkmark;)。

|许可权|管理员|项目经理|人工注释者|
|------------|-------|-----------------|-----------------|
|管理用户访问权和角色| &checkmark; |  |  |
|管理工作空间| &checkmark; |  |  |
|创建类型系统和注释准则| &checkmark; | &checkmark; |  |
|上传培训文档| &checkmark; | &checkmark; |  |
|管理规则| &checkmark; | &checkmark; |  |
|对文档进行预注释| &checkmark; | &checkmark; |  |
|管理注释任务| &checkmark; | &checkmark; |  |
|解决与人工注释的注释冲突（*裁定*）| &checkmark; | &checkmark; |  |
|对机器学习模型进行培训和评估| &checkmark; | &checkmark; |  |
|部署和取消部署模型到运行时服务| &checkmark; | &checkmark; |  |
|执行文档注释| &checkmark; | &checkmark; | &checkmark; |
{:caption="表 2. 角色许可权" caption-side="top"}
