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

本文档适用于 {{site.data.keyword.cloud}} 上的 {{site.data.keyword.knowledgestudiofull}}。要查看 {{site.data.keyword.IBM_notm}} Marketplace 上先前版本的 {{site.data.keyword.knowledgestudioshort}} 的文档，请[单击此链接 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/docs/services/knowledge-studio/rule-annotator-model-use.html){: new_window}。
{: tip}

# 使用基于规则的模型
{: #wks_rule_publish}

使通过 {{site.data.keyword.knowledgestudioshort}} 创建的基于规则的模型可用于其他 {{site.data.keyword.watson}} 应用程序，以利用该模型。
{: shortdesc}

**注**：可以部署基于规则的模型，使其可在这些服务中作为[试验性](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)功能使用。

要能够部署模型以供服务使用，您必须预订该服务。{{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} 服务在 {{site.data.keyword.Bluemix_notm}} 上托管，这是 {{site.data.keyword.IBM_notm}} 的云平台。请参阅[什么是 {{site.data.keyword.Bluemix_notm}}？![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.ng.bluemix.net/docs/overview/whatisbluemix.html){: new_window}，以获取有关该平台的更多信息。要预订其中一个 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} 服务，请在 [{{site.data.keyword.Bluemix_notm}} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.ng.bluemix.net/){: new_window} Web 站点中创建帐户。

对于某些服务，您必须了解计划部署到的服务实例的详细信息，例如 {{site.data.keyword.Bluemix_notm}} 空间名称和服务实例名称。空间和实例名称信息可从 {{site.data.keyword.Bluemix_notm}}“服务”页面获取。

您还可以使用基于规则的模型对新文档进行预注释。有关详细信息，请参阅[使用基于规则的模型对文档进行预注释](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotrule)。

## 将基于规则的模型部署到 AlchemyLanguage
{: #wks_rule_bluemix}

通过此功能，应用程序可以使用部署的基于规则的模型在领域中的文档中查找并抽取实体。

**注意**：目前，这是服务的[试验性](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)功能。

### 开始之前

您必须具有 {{site.data.keyword.alchemylanguageshort}} 服务高级套餐才能使用此定制模型。

### 关于本任务

要部署到此服务，您必须具有来自 {{site.data.keyword.IBM_notm}} {{site.data.keyword.alchemylanguageshort}} 的访问密钥。

该密钥必须属于有权发布定制模型的帐户，否则虽然会成功部署模型，但您将无法使用该模型。

部署基于规则的模型时，请选择要部署的模型版本。首次将模型部署到 {{site.data.keyword.alchemylanguageshort}} 时，必须指定该密钥。然后，可以将该密钥复用于部署的模型的多个版本。每个密钥都具有可同时部署的最大模型数。

### 过程

要将基于规则的模型部署到 {{site.data.keyword.alchemylanguageshort}}，请执行以下操作：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理员或项目经理身份登录，然后选择工作空间。
1. 选择**模型管理** > **版本** > **基于规则**选项卡。
1. 选择要部署的模型版本。

    如果模型只有一个有效版本，请通过单击**保存用于部署**来保存当前模型以用于部署。单击**保存用于部署**将创建模型版本，这支持您部署一个版本，同时您可继续改进当前版本。保存版本可能需要几分钟时间。创建版本之后，才会显示用于部署的选项。

1. 单击**部署**，选择将其部署到 {{site.data.keyword.alchemylanguageshort}}，然后单击**下一步**。
1. 输入从 {{site.data.keyword.alchemylanguageshort}} 中获取的密钥，或者选择模型的先前部署版本（具有要复用的密钥），然后单击**部署**。如果密钥有效，那么将显示包含模型标识的确认。此确认并不意味着该模型已准备就绪可供应用程序使用。
1. 部署过程可能需要几分钟时间。要检查部署的状态，请单击已部署版本旁边的**状态**。如果模型仍在部署中，状态会指示“正在发布”。部署完成后，如果部署成功，那么状态会更改为“可用”；如果发生问题，那么状态将更改为“错误”。

    状态信息包含模型标识、{{site.data.keyword.alchemyapishort}} 密钥的最后四位数以及部署过程的日志。模型标识 (model_id) 指示应用程序调用机器学习模型的方式。请记下此模型标识，因为日后无法通过编程方式访问此标识。使用 {{site.data.keyword.alchemyapishort}} 密钥可跟踪每个密钥的部署数。

### 后续步骤

要使用部署的模型，必须将模型标识复制并粘贴到应用程序的 API 调用中。

> **注意**：不能使用`GET /info/models` {{site.data.keyword.alchemylanguageshort}} API 调用通过编程方式获取基于规则的模型的模型标识。可以通过此调用来访问机器学习模型的模型标识，但不能访问基于规则的模型的标识。

该调用还必须指定要与该模型和您的 {{site.data.keyword.alchemyapishort}} 访问密钥配合使用的 {{site.data.keyword.alchemylanguageshort}} 服务。

支持以下端点：

- **&lt;*input-type*&gt;GetRankedNamedEntities**

    使用在模型参数中指定的定制模型，抽取在您提供的输入中找到的所有已知实体类型的提及项列表。支持的输入类型包括文本、HTML 或公共 URL。有关要使用的 API 和语法的更多信息，请参阅 [{{site.data.keyword.alchemylanguageshort}} &gt; Entities ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/smarterplanet/us/en/ibmwatson/developercloud/alchemy-language/api/v1/#entities){: new_window}。

## 将基于规则的模型部署到 IBM Watson Discovery
{: #wks_rule_discovery}

部署模型以支持使用 {{site.data.keyword.discoveryshort}} 服务的应用程序通过基于规则的模型在文档扩充期间查找并抽取实体。

**注意**：目前，这是服务的[试验性](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)功能。

### 开始之前

您必须具有对 {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}} 服务实例的管理访问权，并且知道与其关联的 {{site.data.keyword.Bluemix_notm}} 空间和实例名称。

### 过程

要将基于规则的模型部署到 {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}，请完成以下步骤：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理员或项目经理身份登录，然后选择工作空间。
1. 选择**模型管理** > **版本** > **基于规则**选项卡。
1. 选择要部署的模型版本。

    如果模型只有一个有效版本，请通过单击**保存用于部署**来保存当前模型以用于部署。这将对模型进行版本控制（支持您部署一个版本），同时您可继续改进当前版本。保存版本可能需要几分钟时间。创建版本之后，才会显示用于部署的选项。

1. 单击**部署**，选择将其部署到 {{site.data.keyword.discoveryshort}}，然后单击**下一步**。
1. 提供 {{site.data.keyword.Bluemix_notm}} 空间和实例。如果需要，请选择其他区域。
1. 单击**部署**。
1. 部署过程可能需要几分钟时间。要检查部署的状态，请单击**版本**选项卡上已部署版本旁边的**状态**。

    如果模型仍在部署中，状态会指示“正在发布”。部署完成后，如果部署成功，那么状态会更改为“可用”；如果发生问题，那么状态将更改为“错误”。

    模型标识可用后，请记下模型标识 (model_id)。您将需要向 {{site.data.keyword.discoveryshort}} 服务提供此标识，才能支持该服务使用定制模型。

### 后续步骤

要使用部署的模型，必须在 {{site.data.keyword.discoveryshort}} 服务扩充配置过程中请求模型标识时提供该模型标识。

## 将基于规则的模型部署到 IBM Watson Natural Language Understanding
{: #wks_rule_nlu}

部署基于规则的模型以支持使用 {{site.data.keyword.nlushort}} 服务的应用程序通过该模型来查找并抽取与领域相关的实体。

**注意**：目前，这是服务的[试验性](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)功能。

### 开始之前

您必须具有对 {{site.data.keyword.nlushort}} 服务实例的管理访问权，并且知道与其关联的 {{site.data.keyword.Bluemix_notm}} 空间和实例名称。

### 过程

要将基于规则的模型部署到 {{site.data.keyword.nlushort}}，请完成以下步骤：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理员或项目经理身份登录，然后选择工作空间。
1. 选择**模型管理** > **版本** > **基于规则**选项卡。
1. 选择要部署的模型版本。

    如果模型只有一个有效版本，请通过单击**保存用于部署**来保存当前模型以用于部署。这将对模型进行版本控制（支持您部署一个版本），同时您可继续改进当前版本。保存版本可能需要几分钟时间。创建版本之后，才会显示用于部署的选项。

1. 单击**部署**，选择将其部署到 {{site.data.keyword.nlushort}}，然后单击**下一步**。
1. 提供 {{site.data.keyword.Bluemix_notm}} 空间和实例。如果需要，请选择其他区域。
1. 单击**部署**。
1. 部署过程可能需要几分钟时间。要检查部署的状态，请单击**版本**选项卡上已部署版本旁边的**状态**。

    如果模型仍在部署中，状态会指示“正在发布”。部署完成后，如果部署成功，那么状态会更改为“可用”；如果发生问题，那么状态将更改为“错误”。

    模型标识可用后，请记下模型标识 (model_id)。您将需要向 {{site.data.keyword.nlushort}} 服务提供此标识，才能支持该服务使用定制模型。

### 后续步骤

要使用部署的模型，必须在 `entities.model` 参数中指定定制模型的模型标识。

可以将模型与 {{site.data.keyword.nlushort}} `GET /analyze` 请求配合使用来抽取实体。

有关更多详细信息，请参阅 [{{site.data.keyword.nlushort}} 文档 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/watson/developercloud/doc/natural-language-understanding/index.html){: new_window}。

## 取消部署模型
{: #undeploy-view-model}

如果要取消部署模型或查找模型标识，请查看**部署的模型**页面。**部署的模型**页面显示部署到您有权访问的空间中的服务的所有 {{site.data.keyword.knowledgestudioshort}} 模型。

要取消部署模型或查找模型标识，请执行以下操作：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理员或项目经理身份登录，然后选择工作空间。
1. 从右上角菜单栏中的**设置**菜单中，选择**管理部署的模型**。
1. 从已部署模型的列表中，找到要查看或取消部署的模型。
1. 要取消部署模型，请在该模型所在行的最后一列中，单击**取消部署模型**。
1. 要查找模型标识，请查看**模型标识**列。

## 在 IBM Watson Explorer 中利用基于规则的模型
{: #wks_rule_export}

导出创建基于规则的模型时生成的 PEAR 文件，使该文件可在 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer 中使用。

### 过程

要在 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer 中利用基于规则的模型，请完成以下步骤。

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理员或项目经理身份登录，然后选择工作空间。
1. 选择**模型管理** > **版本** > **基于规则**选项卡。
1. 单击**导出当前模型**。

    如果您有免费套餐预订，那么没有导出选项可用。

    模型会另存为 PEAR 文件，系统会提示您下载该文件。PEAR（处理引擎归档）文件是 UIMA 组件的 UIMA 标准封装格式。模型以 PEAR 格式保存，因此可以在 UIMA 应用程序中对其进行分发和复用。

1. 将文件下载到本地系统。
1. 在 {{site.data.keyword.IBM_notm}}{{site.data.keyword.watson}} Explorer 应用程序中，导入 PEAR 文件。
