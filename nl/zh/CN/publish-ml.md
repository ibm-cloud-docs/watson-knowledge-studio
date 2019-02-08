---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-13"

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

本文档适用于 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}。要查看 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 先前版本的文档，请[单击此链接 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/docs/services/knowledge-studio/publish-ml.html){: new_window}。
{: tip}

# 使用机器学习模型
{: #publish-ml}

使通过 {{site.data.keyword.knowledgestudioshort}} 培训的机器学习模型可用于其他 {{site.data.keyword.watson}} 应用程序，以利用该模型。
{: shortdesc}

可以部署或导出机器学习模型。字典或 {{site.data.keyword.nlushort}} 预注释器只能用于对 {{site.data.keyword.knowledgestudioshort}} 内的文档进行预注释。

要能够部署模型以供服务使用，您必须预订该服务。{{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} 服务在 {{site.data.keyword.Bluemix_short}} 上托管，这是 {{site.data.keyword.IBM_notm}} 的云平台。请参阅[什么是 {{site.data.keyword.Bluemix_notm}}？![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.ng.bluemix.net/docs/overview/whatisbluemix.html){: new_window}，以获取有关该平台的更多信息。要预订其中一个 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} 服务，请在 [{{site.data.keyword.Bluemix_notm}} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.ng.bluemix.net/){: new_window} Web 站点中创建帐户。

对于某些服务，您必须了解计划部署到的服务实例的详细信息，例如 {{site.data.keyword.Bluemix_notm}} 空间名称和服务实例名称。空间和实例名称信息可从 {{site.data.keyword.Bluemix_notm}}“服务”页面获取。

您还可以使用机器学习模型对新文档进行预注释。请参阅[使用机器学习模型对文档进行预注释](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotsire)以了解详细信息。

## 将机器学习模型部署到 IBM Watson Discovery
{: #wks_madiscovery}

对模型的性能感到满意后，可以将其版本部署到 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}。通过此功能，应用程序可以使用部署的机器学习模型来扩充您从数据获取的洞察，以识别对于您的领域相关的概念和关系。

### 开始之前
{: #wks_madiscovery_prereqs}

您必须具有对 {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}} 服务实例的管理访问权，并且知道与其关联的 {{site.data.keyword.Bluemix_notm}} 空间和实例名称。

### 关于本任务
{: #wks_madiscovery_about}

部署机器学习模型时，请选择要部署的模型版本。

### 过程
{: #wks_madiscovery_procedure}

要将机器学习模型部署到 {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}，请完成以下步骤：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理员或项目经理身份登录，然后选择工作空间。
1. 选择**机器学习模型** > **版本**。
1. 选择要部署的模型版本。

    如果模型只有一个有效版本，请创建当前模型的快照。这将对模型进行版本控制（支持您部署一个版本），同时您可继续改进当前版本。在至少创建一个版本后，才会显示用于部署的选项。

    **注**：每个版本都只能部署在一个服务实例上。如果要将同一模型部署到多个实例上，请为每个实例创建一个版本。

1. 单击**部署**，选择将其部署到 {{site.data.keyword.discoveryshort}}，然后单击**下一步**。
1. 选择 {{site.data.keyword.Bluemix_notm}} 空间和实例。如果需要，请选择其他区域。
1. 单击**部署**。
1. 部署过程可能需要几分钟时间。要检查部署的状态，请单击**版本**选项卡上已部署版本旁边的**状态**。

    如果模型仍在部署中，状态会指示“正在发布”。部署完成后，如果部署成功，那么状态会更改为“可用”；如果发生问题，那么状态将更改为“错误”。

    模型标识可用后，请记下模型标识 (model_id)。您将需要向 {{site.data.keyword.discoveryshort}} 服务提供此标识，才能支持该服务使用定制模型。

### 后续步骤
{: #wks_madiscovery_next}

要使用部署的模型，必须在 {{site.data.keyword.discoveryshort}} 服务扩充配置过程中请求模型标识时提供该模型标识。有关更多详细信息，请参阅 [{{site.data.keyword.discoveryshort}} 服务文档 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/docs/services/discovery/integrate-wks.html){: new_window}。

## 将机器学习模型部署到 IBM Watson Natural Language Understanding
{: #wks_manlu}

对模型的性能感到满意后，可以将其版本部署到 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.nlushort}}。通过此功能，应用程序可以使用部署的机器学习模型来分析文本输入的语义特征，包括实体和关系。

### 开始之前
{: #wks_manlu_prereqs}

您必须具有要部署到的 {{site.data.keyword.nlushort}} 服务。您还必须知道与该服务关联的 {{site.data.keyword.Bluemix_notm}} 空间和实例名称。如果您不记得空间或实例名称，请通过登录到 {{site.data.keyword.Bluemix_notm}} 来查找这些名称。如果您没有 {{site.data.keyword.Bluemix_notm}} 帐户，请注册一个帐户。

### 关于本任务
{: #wks_manlu_about}

部署机器学习模型时，请选择要部署的模型版本。

### 过程
{: #wks_manlu_procedure}

要将机器学习模型部署到 {{site.data.keyword.nlushort}} 服务，请完成以下步骤：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理员或项目经理身份登录，然后选择工作空间。
1. 选择**机器学习模型** > **版本**。
1. 选择要部署的模型版本。

    如果模型只有一个有效版本，请创建当前模型的快照。这将对模型进行版本控制（支持您部署一个版本），同时您可继续改进当前版本。在至少创建一个版本后，才会显示用于部署的选项。

    **注**：每个版本都只能部署在一个服务实例上。如果要将同一模型部署到多个实例上，请为每个实例创建一个版本。

1. 单击**部署**，选择将其部署到 {{site.data.keyword.nlushort}}，然后单击**下一步**。
1. 选择 {{site.data.keyword.Bluemix_notm}} 空间和实例。如果需要，请选择其他区域。
1. 单击**部署**。
1. 部署过程可能需要几分钟时间。要检查部署的状态，请单击**版本**选项卡上已部署版本旁边的**状态**。如果模型仍在部署中，状态会指示“正在发布”。部署完成后，如果部署成功，那么状态会更改为“可用”；如果发生问题，那么状态将更改为“错误”。

    模型标识可用后，请记下模型标识 (model_id)。您将需要向 {{site.data.keyword.nlushort}} 服务提供此标识，才能支持该服务使用定制模型。

### 后续步骤
{: #wks_manlu_next}

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

有关更多详细信息，请参阅 [{{site.data.keyword.nlushort}} 文档 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/docs/services/natural-language-understanding/index.html){: new_window}。

## 取消部署模型
{: #undeploy-view-model}

如果要取消部署模型或查找模型标识，请查看**部署的模型**页面。

### 关于本任务
{: #wks_undeploy_about}

在“已部署的模型”页面上看到的内容取决于托管 {{site.data.keyword.knowledgestudioshort}} 实例的[区域 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/docs/resources/services_region.html){: new_window}。如果该区域支持由 [ IAM ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/docs/iam/users_roles.html){: new_window} 和 [Cloud Foundry ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/docs/iam/cfaccess.html){: new_window} 访问管理方法所管理的实例，那么您将看到每个方法的选项卡。由 IAM 管理的实例中的模型在**资源组**选项卡上列出。由 Cloud Foundry 管理的实例中的模型在**组织**选项卡上列出。

如果该区域仅支持由其中一个访问管理方法管理的实例，那么您只能看到一个模型列表，因为只有一种访问管理方法适用。

### 过程
{: #wks_deploy_procedure}

要取消部署模型或查找模型标识，请执行以下操作：

1. 启动 {{site.data.keyword.knowledgestudioshort}}。
1. 从右上角菜单栏中的**设置**菜单中，选择**管理部署的模型**。
1. 从已部署模型的列表中，找到要查看或取消部署的模型。
1. 要取消部署模型，请在该模型所在行的最后一列中，单击**取消部署模型**。
1. 要查找模型标识，请查看**模型标识**列。

或者，也可以从基于规则的模型和机器学习模型的“版本”页面中取消部署模型。

## 在 IBM Watson Explorer 中利用机器学习模型
{: #wks_maexport}

导出培训的机器学习模型，以便可以在 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer 中使用该模型。

### 开始之前
{: #wks_maexport_prereqs}

如果选择识别关系类型并对其进行注释，那么必须在导出模型之前，至少定义两种关系类型，并对参考标准中的关系实例进行注释。仅对一种关系类型进行定义和注释会导致 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer R11.0.1.0 中后续出现问题。

### 关于本任务
{: #wks_maexport_about}

现在，机器学习模型已培训为识别特定领域的实体和关系，因此您可以在 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer 中对其加以利用。

单击[此链接 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.youtube.com/watch?v=1VoS-xczBow&amp;feature=youtu.be){: new_window} 以观看不到 2 分钟的视频，该视频演示了如何导出模型并在 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer 中使用该模型。

### 过程
{: #wks_maexport_procedure}

要在 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer 中利用机器学习模型，请完成以下步骤。

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理员或项目经理身份登录，然后选择工作空间。
1. 选择**机器学习模型** > **版本**。
1. 单击**导出当前模型**。

    如果您有轻量套餐预订，那么没有导出选项可用。

    模型会另存为 ZIP 文件，系统会提示您下载该文件。

1. 将文件下载到本地系统。
1. 在 {{site.data.keyword.IBM_notm}}{{site.data.keyword.watson}} Explorer 应用程序中，导入模型。

    然后，可以将模型映射到 {{site.data.keyword.watson}} Explorer Content Analytics 中的机器学习模型。执行映射步骤后，在搜寻文档时，模型将查找模型所理解的实体和关系的实例。要了解如何在 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer 中导入和配置模型，请参阅描述集成的技术文档：[http://www.ibm.com/support/docview.wss?uid=swg27048147 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.ibm.com/support/docview.wss?uid=swg27048147){: new_window}。

#### 相关任务
{: #wks_maexport_related}

[从 {{site.data.keyword.watson}} Explorer Content Analytics 导出已分析的文档](/docs/services/watson-knowledge-studio/preannotation.html#wks_uimawexca)
