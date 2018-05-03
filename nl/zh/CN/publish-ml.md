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

本文档适用于 {{site.data.keyword.cloud}} 上的 {{site.data.keyword.knowledgestudiofull}}。要查看 {{site.data.keyword.IBM_notm}} Marketplace 上先前版本的 {{site.data.keyword.knowledgestudioshort}} 的文档，请[单击此链接 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/docs/services/knowledge-studio/publish-ml.html){: new_window}。
{: tip}

# 使用机器学习模型
{: #publish-ml}

使通过 {{site.data.keyword.knowledgestudioshort}} 培训的机器学习模型可用于其他 {{site.data.keyword.watson}} 应用程序，以利用该模型。
{: shortdesc}

可以部署或导出机器学习模型。字典或 {{site.data.keyword.nlushort}} 预注释器只能用于对 {{site.data.keyword.knowledgestudioshort}} 内的文档进行预注释。

要能够部署模型以供服务使用，您必须预订该服务。{{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} 服务在 {{site.data.keyword.Bluemix_short}} 上托管，这是 {{site.data.keyword.IBM_notm}} 的云平台。请参阅[什么是 {{site.data.keyword.Bluemix_notm}}？![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.ng.bluemix.net/docs/overview/whatisbluemix.html){: new_window}，以获取有关该平台的更多信息。要预订其中一个 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} 服务，请在 [{{site.data.keyword.Bluemix_notm}} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.ng.bluemix.net/){: new_window} Web 站点中创建帐户。

对于某些服务，您必须了解计划部署到的服务实例的详细信息，例如 {{site.data.keyword.Bluemix_notm}} 空间名称和服务实例名称。空间和实例名称信息可从 {{site.data.keyword.Bluemix_notm}}“服务”页面获取。

您还可以使用机器学习模型对新文档进行预注释。有关详细信息，请参阅[使用机器学习模型对文档进行预注释](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotsire)。

## 将机器学习模型部署到 AlchemyLanguage
{: #wks_mabluemix}

对模型的性能感到满意后，可以将其版本部署到 {{site.data.keyword.IBM_notm}} {{site.data.keyword.alchemylanguageshort}}。此功能需要您提供 {{site.data.keyword.alchemyapishort}} 访问密钥，它支持应用程序使用部署的机器学习模型对您领域中的文档进行注释。

### 开始之前

您必须具有 {{site.data.keyword.alchemylanguageshort}} 服务高级套餐才能部署和使用该模型。
>注：{{site.data.keyword.alchemylanguageshort}} 服务已弃用。除非您有现有套餐，否则无法将此模型部署到该服务。

### 关于本任务

部署机器学习模型时，请选择要部署的模型版本。要部署到此服务，您必须具有来自 {{site.data.keyword.IBM_notm}} {{site.data.keyword.alchemylanguageshort}} 的访问密钥。

该密钥必须属于有权发布定制模型的帐户，否则虽然会成功部署模型，但您将无法使用该模型。

首次将模型部署到 {{site.data.keyword.alchemylanguageshort}} 时，必须指定该密钥。然后，可以将该密钥复用于部署的模型的多个版本。每个密钥都具有可同时部署的最大模型数。

### 过程

要将机器学习模型部署到 {{site.data.keyword.alchemylanguageshort}}，请执行以下操作：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理员或项目经理身份登录，然后选择工作空间。
1. 选择**模型管理** > **版本** > **机器学习**选项卡。
1. 选择要部署的模型版本。

    如果模型只有一个有效版本，请创建当前模型的快照。这将对模型进行版本控制（支持您部署一个版本），同时您可继续改进当前版本。在至少创建一个版本后，才会显示用于部署的选项。

1. 单击**部署**，选择将其部署到 {{site.data.keyword.alchemylanguageshort}} 服务，然后单击**下一步**。
1. 输入从 {{site.data.keyword.alchemylanguageshort}} 中获取的密钥，或者选择模型的先前部署版本（具有要复用的密钥），然后单击**部署**。如果密钥有效，那么将显示包含模型标识的确认。此确认并不意味着该模型已准备就绪可供应用程序使用。
1. 部署过程可能需要几分钟时间。要检查部署的状态，请单击已部署版本旁边的**状态**。如果模型仍在部署中，状态会指示“正在发布”。部署完成后，如果部署成功，那么状态会更改为“可用”；如果发生问题，那么状态将更改为“错误”。

    状态信息包含模型标识、{{site.data.keyword.alchemyapishort}} 密钥的最后四位数以及部署过程的日志。模型标识 (model_id) 指示应用程序调用机器学习模型的方式。使用 {{site.data.keyword.alchemyapishort}} 密钥可跟踪每个密钥的部署数。

### 后续步骤

要使用部署的模型，必须将模型标识复制并粘贴到应用程序的 API 调用中。该调用还必须指定要与模型及其关联的 {{site.data.keyword.alchemyapishort}} 访问密钥配合使用的 {{site.data.keyword.alchemylanguageshort}} 高级套餐服务。支持以下端点：

- **&lt;*input-type*&gt;GetRankedNamedEntities**

    使用在模型参数中指定的定制模型，抽取在您提供的输入中找到的所有已知实体类型的提及项列表。支持的输入类型包括文本、HTML 或公共 URL。有关要使用的 API 和语法的更多信息，请参阅 [{{site.data.keyword.alchemylanguageshort}} &gt; Entities ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/smarterplanet/us/en/ibmwatson/developercloud/alchemy-language/api/v1/#entities){: new_window}。

- **&lt;*input-type*&gt;GetTypedRelations**

    使用在模型参数中指定的定制模型，抽取在您提供的输入中找到的已知关系的实例列表。有关要使用的 API 和语法的更多信息，请参阅 [{{site.data.keyword.alchemylanguageshort}} &gt; TypedRelations ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/smarterplanet/us/en/ibmwatson/developercloud/alchemy-language/api/v1/#typed-relations){: new_window}。

#### 示例

- 以下 API 调用将在 POST 主体中传递的文本字符串中查找已知实体类型。请求会指定已创建模型的标识，以及有权运行定制模型的 Alchemy API 密钥。

    ```bash
    curl -d 'text=Mary had a little lamb.'
    "https://gateway-a.watsonplatform.net/calls/text/TextGetRankedNamedEntities?
    showSourceText=1&
    model=44476a63-c55t-451f-ad3r-8b23c0f4628c&
    apikey=s3wee88r25wwe2p6442w99g8t77phll5323kkf3a&
    outputMode=json"
    ```
    {: pre}

    如果 `Mary` 和 `lamb` 是机器学习模型识别到的提及项，那么响应会返回这两项。

- 以下 API 调用将在 POST 主体中传递的文本字符串中查找已知关系。请求会指定已创建模型的标识，以及有权运行定制模型的 Alchemy API 密钥。

    ```bash
    curl -d 'text=Mary had a little lamb.'
    "https://gateway-a.watsonplatform.net/calls/text/TextGetTypedRelations?
    showSourceText=1&
    model=44476a63-c55t-451f-ad3r-8b23c0f4628c&
    apikey=s3wee88r25wwe2p6442w99g8t77phll5323kkf3a&
    outputMode=json"
    ```
    {: pre}

    如果机器学习模型识别到 `ownedBy` 关系，那么响应会返回该关系。

> **注**：包含了回车符以更好地为屏幕设置示例格式。不要在 API 语法中包含回车符。

有关更多信息，请参阅 [{{site.data.keyword.alchemylanguageshort}} 文档 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/watson/developercloud/doc/alchemylanguage/customizing.shtml){: new_window}。

#### 相关信息

[{{site.data.keyword.alchemylanguageshort}} 模型问题](/docs/services/watson-knowledge-studio/troubleshooting.html#wks_ts_deployed_model_deleted)

## 将机器学习模型部署到 IBM Watson Discovery
{: #wks_madiscovery}

对模型的性能感到满意后，可以将其版本部署到 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}。通过此功能，应用程序可以使用部署的机器学习模型来扩充您从数据获取的洞察，以识别对于您的领域相关的概念和关系。

### 开始之前

您必须具有对 {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}} 服务实例的管理访问权，并且知道与其关联的 {{site.data.keyword.Bluemix_notm}} 空间和实例名称。

### 关于本任务

部署机器学习模型时，请选择要部署的模型版本。

### 过程

要将机器学习模型部署到 {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}，请完成以下步骤：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理员或项目经理身份登录，然后选择工作空间。
1. 选择**模型管理** > **版本** > **机器学习**选项卡。
1. 选择要部署的模型版本。

    如果模型只有一个有效版本，请创建当前模型的快照。这将对模型进行版本控制（支持您部署一个版本），同时您可继续改进当前版本。在至少创建一个版本后，才会显示用于部署的选项。

1. 单击**部署**，选择将其部署到 {{site.data.keyword.discoveryshort}}，然后单击**下一步**。
1. 选择 {{site.data.keyword.Bluemix_notm}} 空间和实例。如果需要，请选择其他区域。
1. 单击**部署**。
1. 部署过程可能需要几分钟时间。要检查部署的状态，请单击**版本**选项卡上已部署版本旁边的**状态**。

    如果模型仍在部署中，状态会指示“正在发布”。部署完成后，如果部署成功，那么状态会更改为“可用”；如果发生问题，那么状态将更改为“错误”。

    模型标识可用后，请记下模型标识 (model_id)。您将需要向 {{site.data.keyword.discoveryshort}} 服务提供此标识，才能支持该服务使用定制模型。

### 后续步骤

要使用部署的模型，必须在 {{site.data.keyword.discoveryshort}} 服务扩充配置过程中请求模型标识时提供该模型标识。有关更多详细信息，请参阅 [{{site.data.keyword.discoveryshort}} 服务文档 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.ibm.com/watson/developercloud/doc/discovery/integrate-wks.shtml){: new_window}。

## 将机器学习模型部署到 IBM Watson Natural Language Understanding
{: #wks_manlu}

对模型的性能感到满意后，可以将其版本部署到 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.nlushort}}。通过此功能，应用程序可以使用部署的机器学习模型来分析文本输入的语义特征，包括实体和关系。

### 开始之前

您必须具有要部署到的 {{site.data.keyword.nlushort}} 服务。您还必须知道与该服务关联的 {{site.data.keyword.Bluemix_notm}} 空间和实例名称。如果您不记得空间或实例名称，请通过登录到 {{site.data.keyword.Bluemix_notm}} 来查找这些名称。如果您没有 {{site.data.keyword.Bluemix_notm}} 帐户，请注册一个帐户。

### 关于本任务

部署机器学习模型时，请选择要部署的模型版本。

### 过程

要将机器学习模型部署到 {{site.data.keyword.nlushort}} 服务，请完成以下步骤：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理员或项目经理身份登录，然后选择工作空间。
1. 选择**模型管理** > **版本** > **机器学习**选项卡。
1. 选择要部署的模型版本。

    如果模型只有一个有效版本，请创建当前模型的快照。这将对模型进行版本控制（支持您部署一个版本），同时您可继续改进当前版本。在至少创建一个版本后，才会显示用于部署的选项。

1. 单击**部署**，选择将其部署到 {{site.data.keyword.nlushort}}，然后单击**下一步**。
1. 选择 {{site.data.keyword.Bluemix_notm}} 空间和实例。如果需要，请选择其他区域。
1. 单击**部署**。
1. 部署过程可能需要几分钟时间。要检查部署的状态，请单击**版本**选项卡上已部署版本旁边的**状态**。如果模型仍在部署中，状态会指示“正在发布”。部署完成后，如果部署成功，那么状态会更改为“可用”；如果发生问题，那么状态将更改为“错误”。

    模型标识可用后，请记下模型标识 (model_id)。您将需要向 {{site.data.keyword.nlushort}} 服务提供此标识，才能支持该服务使用定制模型。

### 后续步骤

要使用部署的模型，必须在 `entities.model` 参数中指定定制模型的模型标识。

可以将模型与 {{site.data.keyword.nlushort}} `GET /analyze` 请求配合使用来抽取以下特征：

- **实体**

    以下命令查找使用 text 参数传递的语句中存在的实体：

    ```bash
    curl -G -u "3330af09-4b22-4f2d-a54c-1cb099df1fa8":"338rTJSvPVqeG"
    -d "version=2016-05-17"
    -d "text=Vehicle%201%2C%20a%201995%20Honda%20Civic%20was%20traveling%20north
    %20on%20a%20two%20lane%20undivided%20roadway%2C%20negotiating%20a%20curve%20to
    %20the%20left%20on%20an%20upgrade."
    -d "features=entities"
    -d "entities.model=10:7abc4c2f-5846-3334-b8f7-af5a6fad3398"
    "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze" -k
    ```
    {: pre}

    此服务返回在定制模型中定义的实体类型中找到的实例的 JSON 对象：

    ```javascript
    {
      "language": "en",
      "entities": [
        {
          "type": "MANUFACTURER",
          "text": "Honda",
          "count": 1
        },
        {
          "type": "MODEL",
          "text": "Civic",
          "count": 1
        },
        {
          "type": "VEHICLE",
          "text": "Vehicle 1",
          "count": 1
        },
        {
          "type": "STRUCTURE",
          "text": "two lane undivided roadway",
          "count": 1
        },
        {
          "type": "STRUCTURE",
          "text": "curve",
          "count": 1
        },
        {
          "type": "MODEL_YEAR",
          "text": "1995",
          "count": 1
        },
        {
          "type": "CONDITION",
          "text": "negotiating",
          "count": 1
        }
      ],
      "language": "en"
    }
    ```
    {: codeblock}

- **关系**

    以下命令查找使用 text 参数传递的语句中存在的关系：

    ```bash
    curl -G -u "3330af09-4b22-4f2d-a54c-1cb099df1fa8":"338rTJSvPVqeG"
    -d "version=2016-05-17"
    -d "text=Vehicle%201%2C%20a%201995%20Honda%20Civic%20was%20traveling%20north
    %20on%20a%20two%20lane%20undivided%20roadway%2C%20negotiating%20a%20curve%20to
    %20the%20left%20on%20an%20upgrade."
    -d "features=relations"
    -d "entities.model=10:7abc4c2f-5846-3334-b8f7-af5a6fad3398"
    "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze" -k
    ```
    {: pre}

    此服务返回在定制模型中定义的关系类型中找到的实例的 JSON 对象：

    ```javascript
    {
      "relations": [
        {
          "type": "timeOf",
          "sentence": "Vehicle 1, a 1995 Honda Civic was traveling north
           on a two lane undivided roadway, negotiating a curve to
           the left on an upgrade.",
          "score": 0.954254,
          "arguments": [
            {
              "text": "1995",
              "entities": [
                {
                  "type": "Date",
                  "text": "1995"
                }
              ]
            },
            {
              "text": "Honda Civic",
              "entities": [
                {
                  "type": "SportingEvent",
                  "text": "Honda Civic"
                }
              ]
            }
          ]
        },
        {
          "type": "locatedAt",
          "sentence": "Vehicle 1, a 1995 Honda Civic was traveling north
           on a two lane undivided roadway, negotiating a curve to
           the left on an upgrade.",
          "score": 0.40592,
          "arguments": [
            {
              "text": "negotiating",
              "entities": [
                {
                  "type": "EventMeeting",
                  "text": "negotiating"
                }
              ]
            },
            {
              "text": "roadway",
              "entities": [
                {
                  "type": "Facility",
                  "text": "roadway"
                }
              ]
            }
          ]
        }
      ],
      "language": "en"
    }
    ```
    {: codeblock}

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

## 在 IBM Watson Explorer 中利用机器学习模型
{: #wks_maexport}

导出培训的机器学习模型，以便可以在 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer 中使用该模型。

### 开始之前

如果选择识别关系类型并对其进行注释，那么必须在导出模型之前，至少定义两种关系类型，并对参考标准中的关系实例进行注释。仅对一种关系类型进行定义和注释会导致 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer R11.0.1.0 中后续出现问题。

### 关于本任务

现在，机器学习模型已培训为识别特定领域的实体和关系，因此您可以在 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer 中对其加以利用。

单击[此链接 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.youtube.com/watch?v=1VoS-xczBow&amp;feature=youtu.be){: new_window} 以观看不到 2 分钟的视频，该视频演示了如何导出模型并在 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer 中使用该模型。

### 过程

要在 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer 中利用机器学习模型，请完成以下步骤。

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理员或项目经理身份登录，然后选择工作空间。
1. 选择**模型管理** > **版本** > **机器学习**选项卡。
1. 单击**导出当前模型**。

    如果您有免费套餐预订，那么没有导出选项可用。

    模型会另存为 ZIP 文件，系统会提示您下载该文件。

1. 将文件下载到本地系统。
1. 在 {{site.data.keyword.IBM_notm}}{{site.data.keyword.watson}} Explorer 应用程序中，导入模型。

    然后，可以将模型映射到 {{site.data.keyword.watson}} Explorer Content Analytics 中的机器学习模型。执行映射步骤后，在搜寻文档时，模型将查找模型所理解的实体和关系的实例。要了解如何在 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer 中导入和配置模型，请参阅描述集成的技术文档：[http://www.ibm.com/support/docview.wss?uid=swg27048147 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.ibm.com/support/docview.wss?uid=swg27048147){: new_window}。

#### 相关任务

[从 {{site.data.keyword.watson}} Explorer Content Analytics 导出已分析的文档](/docs/services/watson-knowledge-studio/preannotation.html#wks_uimawexca)
