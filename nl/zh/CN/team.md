---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-18"

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

本文档适用于 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}。要查看 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 先前版本的文档，请[单击此链接 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/docs/services/knowledge-studio/team.html){: new_window}。
{: tip}

# 组建团队
{: #team}

创建模型需要主题专家、项目经理以及可理解并解释统计模型的用户提供输入。您必须在 {{site.data.keyword.knowledgestudioshort}} 中针对需要登录的每个人员添加用户。
{: shortdesc}

**注**：只有标准套餐和高端套餐可以有多个用户。轻量套餐仅限一个用户。作为唯一用户，该人员将分配有具备最高许可权的角色，即管理员角色。

## 开始之前

- 确保使用的是受支持的浏览器。有关信息，请参阅[浏览器需求](/docs/services/watson-knowledge-studio/system-requirements.html)。
- [创建 {{site.data.keyword.knowledgestudioshort}} 的实例](/docs/services/watson-knowledge-studio/tutorials-create-project.html#instance)。
- 如果已注册标准套餐或高端套餐，请在 {{site.data.keyword.cloud_notm}} 的**管理**选项卡中，邀请要添加为 {{site.data.keyword.knowledgestudioshort}} 中用户的其他用户加入组织。有关邀请用户的更多信息，请参阅[邀请用户和分配访问权 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/docs/iam/iamuserinv.html){: new_window}。

  **重要信息**：确保受邀用户有 Cloud Foundry 开发者角色。有关更多信息，请参阅 [Cloud Foundry 访问权 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/docs/iam/cfaccess.html){: new_window}。

## 关于本任务

通常要添加用户以填充人工注释者和项目经理的角色。有关描述，请参阅 [{{site.data.keyword.knowledgestudioshort}} 中的用户角色](/docs/services/watson-knowledge-studio/roles.html)。

**注：**

- 如果您已注册轻量套餐，那么不能将其他人添加到 {{site.data.keyword.knowledgestudioshort}} 的实例。而是会在您启动 {{site.data.keyword.knowledgestudioshort}} 时将您添加到实例并授予管理员角色。拥有管理员角色后，您可以执行通常会由分配给不同角色的不同人员执行的许多功能。您可以测试某个领域的不同区域的专家可以如何协作来构建机器学习模型或基于规则的模型。
- 将向第一个启动 {{site.data.keyword.knowledgestudioshort}} 的用户授予 {{site.data.keyword.knowledgestudioshort}} 实例的管理员角色。此任务假设您是在注册套餐后第一个启动 {{site.data.keyword.knowledgestudioshort}} 的人员，这意味着您具有管理员角色。

## 在 {{site.data.keyword.knowledgestudioshort}} 中添加用户

将用户从 {{site.data.keyword.cloud_notm}} 组织添加到 {{site.data.keyword.knowledgestudioshort}}。

要将用户添加到 {{site.data.keyword.knowledgestudioshort}} 实例，请执行以下操作：

1. 使用您的 {{site.data.keyword.ibmid}}登录到 [{{site.data.keyword.cloud_notm}}“仪表板”![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net){: new_window}，然后启动 {{site.data.keyword.knowledgestudioshort}}。
1. 单击**设置**图标，然后单击**管理服务详细信息**。
1. 在**管理用户**部分中，为要添加的用户输入 {{site.data.keyword.ibmid}}。
1. 选择要授予该用户的角色。有关可用的角色的描述，请参阅 [{{site.data.keyword.knowledgestudioshort}} 中的用户角色](/docs/services/watson-knowledge-studio/roles.html)。

  **注**：分配用户角色后，您无法对其进行降级，因此请确保您在分配管理员角色和项目经理角色时了解每个角色可以执行的任务。

1. 单击**添加**。

## 升级用户角色

将用户添加到 {{site.data.keyword.knowledgestudioshort}} 后，可以将较低的角色升级到更高的角色。用户必须分配有下述角色，才能执行相应的任务。

**注**：只有标准套餐和高端套餐可以有多个用户。轻量套餐仅限一个已经具有最高角色（管理员）的用户。

> **注意：不允许从较高的角色降级到较低的角色。**

要升级 {{site.data.keyword.knowledgestudioshort}} 用户的角色，请执行以下操作：

1. 使用您的 {{site.data.keyword.ibmid}}登录到 [{{site.data.keyword.cloud_notm}}“仪表板”![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net){: new_window}，然后启动 {{site.data.keyword.knowledgestudioshort}}。
1. 在右上角的导航菜单中，单击**设置**图标 ![“设置”图标](images/settings.png)，然后单击**管理服务详细信息**。“服务详细信息”页面中的**管理用户**部分列出了作为此 {{site.data.keyword.knowledgestudioshort}} 实例的用户的所有用户标识。
1. 查找要更改的用户的名称，然后单击**编辑**链接。
1. 单击用户的角色，然后选择要将该用户升级到的角色。有关可用的角色的描述，请参阅 [{{site.data.keyword.knowledgestudioshort}} 中的用户角色](/docs/services/watson-knowledge-studio/roles.html)。

  **重要信息**：必须创建工作空间，将用户与文档集相关联，并将注释任务分配给用户后，具有人工注释者角色的用户才能看到 {{site.data.keyword.knowledgestudioshort}} 应用程序中列出的任何工作空间。在用户注册后，请尽快设置工作空间，以便他们在首次访问应用程序时就能看到工作空间。设置工作空间后，您可能希望通知用户，让他们知道可以开始对文档进行注释。

1. 可选：在 {{site.data.keyword.knowledgestudioshort}} 中完成对用户的管理操作后，通过关闭 Web 浏览器来退出会话。{{site.data.keyword.knowledgestudioshort}} 用户界面未提供用于显式注销的操作。

## 停用用户帐户

日后，如果要除去用户，请执行先前的步骤以打开“服务详细信息”页面。在用户标识列表中，找到要除去的用户，然后单击**停用**。

> **注意**：如果用户分配有要对其进行注释的文档，而您停用了其帐户，那么会影响到这些用户的注释。如果已停用用户所做的注释未升级为参考标准，那么系统会删除这些注释。

### 相关任务

[创建和分配注释集](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projdocsets)
