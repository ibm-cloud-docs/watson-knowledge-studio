---

copyright:
  years: 2015, 2018
lastupdated: "2018-03-20"

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

本文档适用于 {{site.data.keyword.cloud}} 上的 {{site.data.keyword.knowledgestudiofull}}。要查看 {{site.data.keyword.IBM_notm}} Marketplace 上先前版本的 {{site.data.keyword.knowledgestudioshort}} 的文档，[请单击此链接 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/docs/services/knowledge-studio/tutorials-bootstrap-annotation.html){: new_window}。
{: tip}

# 引导注释
{: #wks_tutboot_intro}

本教程帮助您了解如何对文档进行预注释，从而简化人类注释者的注释作业。
{: shortdesc}

## 学习目标

在完成本教程后，您将了解如何使用机器学习模型对文档进行预注释。

完成本教程约需 5 分钟。如果要研究与本教程相关的其他概念，那么可能需要更长时间。

## 开始之前

- 使用受支持的浏览器。有关信息，请参阅[浏览器需求](/docs/services/watson-knowledge-studio/system-requirements.html)。
- 您已成功完成[教程：创建工作空间](/docs/services/watson-knowledge-studio/tutorials-create-project.html)和[教程：创建机器学习模型](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html)。
- 您必须至少有一个用户标识为 Admin 或 ProjectManager 角色。有关用户角色的信息，请参阅[组建团队](/docs/services/watson-knowledge-studio/team.html)。

## 结果

完成本教程后，您将有一组已部分注释的文档。然后，您可以将这些文档分配给人类注释者以完成注释工作。

## 第 1 课：使用机器学习模型对新文档进行预注释
{: #wks_tutboot_ml}

在本课程中，您将了解如何使用机器学习模型在 {{site.data.keyword.knowledgestudioshort}} 中对文档进行预注释。

### 关于本任务

在培训机器学习模型后，您可以将其用于对添加到语料库的新文档进行预注释。

> **注意：**请勿对已进行人工注释但尚未添加到参考标准的文档运行预注释器。如果这样做，那么将擦除文档中的所有当前注释。

在本教程中，您可以使用 `documents-ml.csv` 文件来添加第二组文档。请勿重新添加 `documents-new.csv` 文件，因为此添加将导致参考标准中出现重复的文档。重复会导致以下问题：

- 如果每个文档上的注释不匹配，那么会降低机器学习模型的质量。
- 如果每个文档上的注释均匹配，那么会在重复文件的上对机器学习模型进行过度培训。

### 过程

1. 以管理员身份登录到 {{site.data.keyword.knowledgestudioshort}}。
1. 将更多文档上传到工作空间。您可以使用 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/documents-ml.csv" download>`documents-ml.csv`<img src="../../icons/launch-glyph.svg" alt="外部链接图标" title="外部链接图标" class="style-scope doc-content"></a> 文件。

    有关如何上传文档的详细信息，请参阅[创建机器学习模型 > 添加文档以进行注释](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#tut_lessml1)。

1. 使用 `documents-ml.csv` 文件创建注释集。

    对于本教程，将注释集分配给您自己，即管理员。在运行机器学习模型来对新文档进行预注释后，您可以查看注释集以了解机器学习模型如何对其进行预注释。通常，将注释集分配给一个或多个人类注释者。有关创建注释集的更多信息，请参阅[创建机器学习模型 > 创建注释集](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml2)。

1. 从**模型管理** > **版本**侧边栏中，选择**机器学习**选项卡，然后单击**运行此模型**。
1. 选择添加到语料库 `documents-ml.csv` 的文档集，然后单击**运行**。
1. 在预注释完成后，您可以创建人工注释任务并对预注释的新文档进行注释。

    有关创建任务和注释文档的详细信息，请参阅[创建机器学习模型 > 创建注释任务](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml4)和[创建机器学习模型 > 注释文档](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml5)。

    在这种情况下，人工注释需要的时间更少，因为您已使用机器学习模型对文档进行预注释。

### 结果

通过使用机器学习模型对新文档集进行预注释，您可以加速这些文档的人工注释任务。
