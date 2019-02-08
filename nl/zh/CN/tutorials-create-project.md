---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-16"

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

本文档适用于 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}。要查看 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 先前版本的文档，请[单击此链接 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/docs/services/knowledge-studio/tutorials-create-project.html){: new_window}。
{: tip}

# {{site.data.keyword.knowledgestudioshort}} 入门
{: #wks_tutintro}

本 {{site.data.keyword.knowledgestudiofull}} 教程帮助您执行在开始任何其他教程前必须完成的先决条件任务。
{: shortdesc}

## 开始之前
{: #prereq}

- 确认您正在使用受支持的浏览器。有关信息，请参阅[浏览器需求](/docs/services/watson-knowledge-studio/system-requirements.html)。
-  要完成本教程，您必须至少具有一个可在 {{site.data.keyword.knowledgestudioshort}} 中使用的用户标识。此用户标识必须具有 Admin 角色。如果您已注册轻量套餐，那么作为唯一用户，您具有管理员角色。有关用户角色的信息，请参阅[组建团队](/docs/services/watson-knowledge-studio/team.html)。

## 创建服务实例
{: #instance}

1. 如果尚未登录，[请注册 {{site.data.keyword.ibmid}} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}){: new_window}，并登录到 {{site.data.keyword.cloud_notm}}。
1. 从 {{site.data.keyword.cloud_notm}} {{site.data.keyword.watson}} [服务页面 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/developer/watson/services){: new_window}，单击 {{site.data.keyword.knowledgestudioshort}} 磁贴，然后注册套餐。
1. 在注册套餐后，从现有服务列表中启动 {{site.data.keyword.knowledgestudioshort}}。

## 第 1 课：分配用户角色
{: #wks_tutless1}

在本课程中，您将了解可在 {{site.data.keyword.knowledgestudioshort}} 中分配给用户的不同角色。

### 关于本任务
{: #wks_tutless1_about}

创建机器学习模型需要主题专家、项目经理以及可理解并解释统计模型的用户提供输入。管理员将角色分配给每个用户，以便他们具有其任务的相应权限。有关用户角色的更多信息，请参阅[组建团队](/docs/services/watson-knowledge-studio/team.html)。

### 过程
{: #wks_tutless1_procedure}

1. 使用管理员标识登录到 {{site.data.keyword.knowledgestudioshort}}。如果有现有 {{site.data.keyword.knowledgestudioshort}} 实例，那么可以从 {{site.data.keyword.cloud_notm}} {{site.data.keyword.watson}} [服务页面 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/developer/watson/services){: new_window} 找到该实例。
1. 单击“设置”图标以打开“服务详细信息”页面。该页面列出注册为 {{site.data.keyword.knowledgestudioshort}} 用户的所有用户标识。每个用户标识都具有以下角色之一（按所包含许可权的递减顺序）：

    - 管理员
    - 项目经理
    - 人工注释者

    有关用户角色的信息，请参阅 [{{site.data.keyword.knowledgestudioshort}} 中的用户角色](/docs/services/watson-knowledge-studio/roles.html)。

1. 请验证是否至少有一个用户具有“管理员”角色。具有此角色的用户标识可创建工作空间并充当项目经理或人工注释者。
1. 如果您有权访问其他用户标识，请验证是否至少有两个用户具有人工注释者角色。

    > **注：**创建现实模型通常涉及多个人工注释者以及一名管理员或项目经理。但是，针对本教程的用途，您可以使用单个用户标识继续。

1. 可选：更改分配给用户标识的角色。从表的**操作**列中，单击**编辑**链接，然后更改已分配给用户的角色。

    > **注：**您可以将用户标识升级为具有更高许可权的角色，但是无法将具有管理员或项目经理角色的用户降级为人工注释者角色。

## 第 2 课：创建工作空间
{: #wks_tutless2}

在本课程中，您将学习如何在 {{site.data.keyword.knowledgestudioshort}} 中创建工作空间。

### 关于本任务
{: #wks_tutless2_about}

工作空间定义创建机器学习模型所需的所有资源，包括培训文档、类型系统、字典以及由人工注释者添加的注释。有关创建工作空间的更多信息，请参阅[创建工作空间](/docs/services/watson-knowledge-studio/create-project.html)。

### 过程
{: #wks_tutless2_procedure}

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理员身份从 {{site.data.keyword.cloud_notm}} [仪表板 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}){:new_window}，启动 {{site.data.keyword.knowledgestudioshort}} 服务。
1. 单击**创建工作空间**。
1. 指定新工作空间的详细信息：

    - 在**工作空间名称**字段中，输入 `My workspace`。
    - 在**工作空间描述**字段中，输入 `Watson Knowledge Studio tutorial workspace`。
    - 在**文档语言**字段中，使用缺省值**英语**。将用于本教程的样本文件使用的是英语。

1. 单击**创建**。

### 结果
{: #wks_tutless2_results}

将创建并自动打开工作空间。

### 后续步骤
{: #wks_tutless2_next}

现在，您可以开始配置工作空间资源，例如，类型系统。

## 第 3 课：创建类型系统
{: #wks_tutless3}

在本课程中，您将学习如何在 {{site.data.keyword.knowledgestudioshort}} 中上传和修改类型系统。必须在开始任何注释任务之前创建或上传类型系统。

### 关于本任务
{: #wks_tutless3_about}

有关类型系统的更多信息，请参阅[类型系统](/docs/services/watson-knowledge-studio/typesystem.html#wks_typesystem)。

### 过程
{: #wks_tutless3_procedure}

1. 将 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/en-klue2-types.json" download>en-klue2-types.json<img src="../../icons/launch-glyph.svg" alt="外部链接图标" title="外部链接图标" class="style-scope doc-content"></a> 文件下载到计算机。此文件包含一个示例 KLUE 类型系统。
1. 单击**资产** > **实体类型**。
1. 在“实体类型”页面上，单击**上传**。
1. 从计算机上传 `en-klue2-types.json` 文件。将在表中显示上传的类型系统。
1. 浏览类型系统，以便可查看上传的数据。
1. 编辑实体类型：

    1. 找到 MONEY 实体类型。
    1. 双击表行中的任意位置以编辑实体类型。
    1. 在**角色**列中，单击 AWARD 角色旁边的**删除角色**图标 ![“删除角色”图标。](images/wks_delete.jpg "“删除角色”图标。")。

        ![从实体类型中删除角色的截屏。](images/wks_tut_delete_role.jpg "显示光标悬停在“删除角色”图标上方时的截屏。")

    1. 单击**保存**。

### 后续步骤
{: #wks_tutless3_next}

完成对类型系统的更改后，可以开始向工作空间添加文档。

## 第 4 课：添加字典
{: #wks_tutless4}

在本课程中，您将学习如何在 {{site.data.keyword.knowledgestudioshort}} 中向工作空间添加字典。字典用于在创建机器学习模型时对文本进行预注释。

### 关于本任务
{: #wks_tutless4_about}

有关字典的更多信息，请参阅[向工作空间添加字典](/docs/services/watson-knowledge-studio/dictionaries.html#wks_projdictionaries)。

### 过程
{: #wks_tutless4_procedure}

1. 将 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/dictionary-items-organization.csv" download>`dictionary-items-organization.csv` <img src="../../icons/launch-glyph.svg" alt="外部链接图标" title="外部链接图标" class="style-scope doc-content"></a> 文件下载到计算机。此文件包含 CSV 格式的字典术语，适合上传到 {{site.data.keyword.knowledgestudioshort}} 字典。
1. 单击**资产** > **字典**。
1. 单击**创建字典**以添加字典。

    > **注：**请勿单击**上传字典**，这用于上传您想要按原样使用的字典。对于本教程，您将创建新的可编辑字典，然后向其上传术语。

1. 在**名称**字段中，输入 `Test dictionary`，然后单击**保存**以创建（空）字典。

    这样将创建新字典并自动打开该字典以进行编辑。

1. 在字典窗格中，单击**上传**。
1. 从计算机上传 `dictionary-items-organization.csv` 文件。这会将文件中的术语上传到字典中。
1. 单击**添加条目**以创建新术语。将在表的顶部添加一个可编辑的行。
1. 在**表面形式**列中，在单独的行中分别输入 `IBM` 和 `International Business Machines Corporation`。（在开始输入新的表面形式时，在下方添加了一个空格，以用于另一个表面形式。）将 `IBM` 旁边的单选按钮保持选中状态，这指示 `IBM` 是词元。
1. 在**词性**列中，选择**名词**。
1. 单击**保存**。

    ![“字典”页面的截屏。"IBM" 字典条目处于选中状态，其表面形式和词性已突出显示。](images/wks_tutdict4.jpg "“字典”页面的截屏。"IBM" 字典条目处于选中状态，其表面形式和词性已突出显示。")

### 后续步骤
{: #wks_tutless4_next}

创建字典后，您可以将其用于通过对文档进行预注释来加快人工注释任务。

## 教程小结
{: #wks_tutsum}

在学习 {{site.data.keyword.knowledgestudioshort}} 时，您创建了工作空间并向其添加了工件。

### 已学课程
{: #lessons_learned}

通过完成本教程，您学习了以下概念：

- 工作空间
- 类型系统
- 字典
