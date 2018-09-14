---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-09"

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

本文档适用于 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}。要查看 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 先前版本的文档，请[单击此链接 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/docs/services/knowledge-studio/release-notes.html){: new_window}。
{: tip}

# 发行说明
{: #release-notes}

为 {{site.data.keyword.knowledgestudiofull}} 提供了以下新功能和更改。
{: shortdesc}

## 2018 年 8 月
{: #august2018}

### 新增功能和更改
{: #new-august2018}

- 引入了一个新选项，用于将标准套餐实例从不推荐使用的 {{site.data.keyword.IBM_notm}} Marketplace 平台自动迁移到 [ {{site.data.keyword.cloud_notm}} 平台 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/blogs/bluemix/2017/12/watson-knowledge-studio-ibm-cloud/){: new_window}。如果您在不推荐使用的平台上有标准实例，那么您将可以选择迁移。有关更多信息，请参阅[迁移到 {{site.data.keyword.cloud_notm}}](/docs/services/watson-knowledge-studio/client-migration.html)。

## 2018 年 7 月
{: #july2018}

### 新增功能和更改
{: #new-july2018}

- **已部署的模型**页面已更新，包含 {{site.data.keyword.knowledgestudioshort}} 实例中的模型，这些实例由 [IAM *资源组*管理 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/docs/iam/users_roles.html){: new_window}，此外还包含由 [Cloud Foundry *组织*管理的模型 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/docs/iam/cfaccess.html){: new_window}。

   在“已部署的模型”页面上看到的内容取决于托管 {{site.data.keyword.knowledgestudioshort}} 实例的[区域 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/docs/resources/services_region.html){: new_window}。如果该区域支持由两种访问管理方法管理的实例，那么您将看到每个方法的选项卡。由 IAM 管理的实例中的模型在**资源组**选项卡上列出。由 Cloud Foundry 管理的实例中的模型在**组织**选项卡上列出。

  如果该区域仅支持由其中一个访问管理方法管理的实例，那么您只能看到一个模型列表，因为只有一种访问管理方法适用。

   要查看**部署的模型**页面，请从右上角菜单栏中的**设置**菜单中，单击**管理部署的模型**。有关在**已部署的模型**页面上取消部署模型的信息，请参阅[取消部署机器学习模型](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model)和[取消部署基于规则的模型](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model)。

- 导航已更改，以便更好地与 {{site.data.keyword.knowledgestudioshort}} 工作流程保持一致。此外，重组了以下功能：

    - 在先前版本中，字典的管理包含在“预注释器”页面中。现在，字典的管理位于导航的“资产”部分的“字典”页面上。
    - 在先前的版本中，人工注释功能分布在导航的“文档注释”部分的“提及项”、“关系”、“指代”选项卡中。现在，该功能合并到了导航的“机器学习模型”部分中的“注释任务”页面下。
    - 要管理人工注释任务，在先前版本中，您可以在“资产和工具 > 文档”页面下找到“任务”选项卡。现在，您可以在导航的“机器学习模型”部分中的“注释任务”页面上添加任务和管理现有任务。
    - 在先前版本中，“规则”、“正则表达式”和“字典”页面是导航的“文档注释”部分中的单独页面。现在，该功能合并到了导航的“基于规则的模型”部分中的“规则”页面下。

    有关导航更改的更多详细信息，请参阅图 1 和表 3。

![先前导航（左侧）和新导航（右侧）的截屏。](images/nav3-0718.svg "先前导航和新导航的截屏。更改的详细信息在表 3 和上述文本中列出。") 图 1. 先前导航（左侧）和新导航（右侧）的截屏。

|功能部件| 先前的位置 | 当前位置|
|---------|--------------------------|----------------------|
|注释任务|资产和工具 > 文档 > 任务 |机器学习模型 > 注释任务|
| “指代”选项卡 | 文档注释|机器学习模型 > 注释任务 > 任务 > 注释集 > 文档|
| “字典”页面（管理）|资产和工具 > 预注释器 > 管理字典 |资产|
|“字典”选项卡（映射到基于规则的模型的类）| 文档注释|基于规则的模型 > 规则|
|“文档”页面|资产和工具|资产|
|“实体类型”页面|资产和工具|资产|
|“提及项”选项卡| 文档注释|机器学习模型 > 注释任务 > 任务 > 注释集 > 文档|
|“性能”页面|模型管理|机器学习模型|
|“预注释器”页面|资产和工具|机器学习模型 > 预注释|
|“正则表达式”选项卡| 文档注释|基于规则的模型 > 规则|
|“关系类型”页面|资产和工具|资产|
|“关系”选项卡| 文档注释|机器学习模型 > 注释任务 > 任务 > 注释集 > 文档|
|“规则”选项卡| 文档注释|基于规则的模型|
|“任务”选项卡|资产和工具 > 文档  |机器学习模型 > 注释任务|
|“版本”页面（机器学习模型）|模型管理|机器学习模型|
|“版本”页面（基于规则的模型）|模型管理|基于规则的模型|
{: caption="表 3. 导航更改（2018 年 7 月）" caption-side="top"}

## 2018 年 5 月
{: #may2018}

### 新增功能和更改
{: #new-may2018}

- 已修正一个配置问题，该问题导致悉尼区域中的服务实例未出现在美国南部区域。
- 在“部署模型”窗口中，如果您要部署到的区域同时支持 {{site.data.keyword.iamlong}} *资源组*和 Cloud Foundry *空间*，那么您将需要选择服务实例使用的访问管理方法来查看列表。有关 Cloud Foundry 和 {{site.data.keyword.iamshort}} 的更多信息，请参阅[资源组和访问管理 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/blogs/bluemix/2017/12/resource-groups-access-management/){: new_window}。
- 在“服务详细信息”页面上添加了数据收集设置。有关数据收集的更多信息，请参阅[故障诊断、支持和常见问题](/docs/services/watson-knowledge-studio/troubleshooting.html#content)
- 添加了中文（繁体）语言支持。
- 具有“管理”角色的用户现在可以查看已使用的工作空间数。此信息在“服务详细信息”页面上可用。
- {{site.data.keyword.alchemylanguagefull}} 不能再作为部署模型的目标。有关信息，请参阅 [{{site.data.keyword.alchemyapishort}} 服务引退 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/blogs/bluemix/2017/03/bye-bye-alchemyapi/){: new_window}。
- 现在，如果您删除工作空间，那么将要求您确认操作。我们希望通过此确认防止意外删除。
- 文档中包含有关数据隐私的一些新详细信息。阅读[信息安全](/docs/services/watson-knowledge-studio/information-security.html)以了解更多信息。

## 2018 年 4 月
{: #april2018}

### 新增功能和更改
{: #new-april2018}

- {{site.data.keyword.knowledgestudioshort}} 免费套餐已替换为轻量套餐。有关更多信息，请参阅 [Go Lite with Watson {{site.data.keyword.knowledgestudioshort}} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/blogs/bluemix/2018/04/go-lite-watson-knowledge-studio/){: new_window}。

## 2018 年 3 月
{: #march2018}

### 新增功能和更改
{: #new-march2018}

- 提供了**部署的模型**页面，其中可查看部署到您有权访问的空间中的服务的所有 {{site.data.keyword.knowledgestudioshort}} 模型。要查看**部署的模型**页面，请从右上角菜单栏中的**设置**菜单中，单击**管理部署的模型**。有关在**部署的模型**页面上取消部署和查看模型的信息，请参阅[取消部署机器学习模型](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model)和[取消部署基于规则的模型](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model)。
- 现在提供了法语翻译版本的 {{site.data.keyword.knowledgestudioshort}} 界面。
- {{site.data.keyword.alchemylanguagefull}} 不再作为预注释器提供。您可以使用 {{site.data.keyword.nlushort}} 代替 {{site.data.keyword.alchemylanguageshort}} 对文档进行预注释。有关更多信息，请参阅[引导注释](/docs/services/watson-knowledge-studio/preannotation.html)。

## 2017 年 12 月
{: #december2017}

### 新增功能和更改
{: #new-december2017}

- 在 {{site.data.keyword.cloud_notm}} 上推出了 {{site.data.keyword.knowledgestudioshort}}。有关迁移过程和安排的信息，请参阅[迁移到 {{site.data.keyword.cloud_notm}}](/docs/services/watson-knowledge-studio/client-migration.html)。
- 重新设计了导航。有关导航更改的详细信息，请参阅 2017 年 9 月发行说明中的[表 2](#september2017)。
- 添加了 {{site.data.keyword.nlufull}} 作为预注释器。
- 向“服务详细信息”页面添加了用户和存储管理设置。有关添加用户的信息，请参阅[组建团队](/docs/services/watson-knowledge-studio/team.html)。有关设置存储限制的信息，请参阅[故障诊断 > 存储空间问题](/docs/services/watson-knowledge-studio/troubleshooting.html#storage)。
- 添加了“性能”页面，以提供模型质量评估和有关如何提高质量的指导信息。

## 2017 年 11 月
{: #november2017}

### 更改
{: #new-november2017}

- 修复了下载的语料库中缺少某些关系注释的问题。
- 修复了模型在状态为**无**时无法从部署中撤销的问题。
- 修复了无法针对韩国语评估模型的问题。

## 2017 年 10 月
{: #october2017}

### 更改
{: #new-october2017}

- 修复了在 {{site.data.keyword.Bluemix_notm}} [试验性](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)发行版中，刷新浏览器窗口之后才会启用**导出**按钮的问题。
- 修复了按钮标签和工具提示，以匹配 {{site.data.keyword.Bluemix_notm}} [试验性](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)发行版中术语_上传_和_下载_的更改。引用类型系统、文档和字典时，将使用这两个术语，而不使用_导入_和_导出_。
- 修复了 {{site.data.keyword.Bluemix_notm}} [试验性](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)发行版中 {{site.data.keyword.knowledgestudioshort}}“用户帐户管理”页面上更新描述存在延迟的问题。
- 在界面的预注释部分中，进行了一些 GUI 更改，以阐明机器学习模型、基于规则的模型、字典和 {{site.data.keyword.alchemylanguagefull}} 的功能。已将按钮标签从**运行**更改为**预注释**，将窗口的标题从**运行注释器**更改为**运行预注释**，并且更改了错误消息以阐明在人员对文档进行注释后无法添加自动注释。
- 对于使用基于字典的记号化器的项目或工作空间，修复了导入不带参考标准的文档时显示空语句的问题。

## 2017 年 9 月
{: #september2017}

### 新增功能和更改
{: #new-sept17}

- 针对作为[试验性](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)服务的 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.Bluemix}} 发布了新的前端用户体验。更改包括已重组的导航和新的模型性能分析页面。有关导航更改的摘要，请参阅已知问题中的表。
- 添加了简体中文和荷兰语语言支持。

### 已知问题
{: #issues-sept17}

- 对于基于规则的模型，在映射类和实体类型之后，**导出**按钮在刷新浏览器窗口后才会启用。
- 对于 {{site.data.keyword.Bluemix_notm}} [试验性](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)发行版，其中一些文档术语与新界面不匹配。文档与 {{site.data.keyword.IBM_notm}} Marketplace 中的界面相匹配。在[试验性](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)发行版中更改了以下术语：

|{{site.data.keyword.IBM_notm}} Marketplace 中的术语|{{site.data.keyword.Bluemix_notm}} 中的术语|注释|
|----------|----------|----------|
|_项目_|_工作空间_|此术语已更改，因为 {{site.data.keyword.Bluemix_notm}} 同时使用术语_项目_|
|_导入_和_导出_|_上传_和_下载_|术语_导入_和_导出_用于文档和实体类型时，现在称为_上传_和_下载_。但在指示将模型导出到应用程序（如 {{site.data.keyword.watson}} Explorer）时，仍然会使用术语_导出_。|
{: caption="表 1. {{site.data.keyword.Bluemix_notm}} 版本的术语更改" caption-side="top"}

- 对于 {{site.data.keyword.Bluemix_notm}} [试验性](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)发行版，某些文档任务步骤与新界面不匹配。文档与 {{site.data.keyword.IBM_notm}} Marketplace 中的界面相匹配。下表总结了[试验性](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)发行版的导航更改：

|功能部件|{{site.data.keyword.IBM_notm}} Marketplace 位置|{{site.data.keyword.Bluemix_notm}} 位置
|----------|----------|----------|
|“注释器组件”选项卡|主导航|不再存在|
|“混淆矩阵”表（“统计信息”选项卡中）|“注释器组件”>“详细信息”|“模型管理”>“性能”>“详细统计信息”链接|
|“字典”选项卡|主导航|“资产和工具”>“预注释器”|
|“字典映射”页面|注释器组件|“资产和工具”>“预注释器”|
|“实体类型”选项|类型系统|“资产和工具”>“实体类型”|
|参考标准编辑器|人工注释|“文档注释”选项卡|
|参考标准编辑器的“设置”选项卡|人工注释|“设置”>“文档注释设置”|
|模型（运行和导出）|注释器组件|“模型管理”>“版本”|
|“规则”选项卡|主导航|“文档注释”>“规则”|
|“统计信息”选项卡|“注释器组件”>“详细信息”|“模型管理”>“性能”|
|摘要表（“统计信息”选项卡中）|“注释器组件”>“详细信息”|“模型管理”>“性能”>“详细统计信息”链接|
|“类型映射”选项卡（对于基于规则的模型）|“注释器组件”>“详细信息”|“模型管理”>“版本”>“基于规则的模型类型映射”|
{: caption="表 2. {{site.data.keyword.Bluemix_notm}} 版本的导航更改" caption-side="top"}

## 2017 年 7 月
{: #july2017}

- 修复了在某些情况下导致标题消失的缺陷
- 针对基础架构组件应用了安全性更新

## 2017 年 6 月
{: #june2017}

- 提高了在特定条件下处理大型数据的稳定性
- 修复了裁定错误的缺陷

## 2017 年 5 月
{: #may2017}

- 添加了重命名各种对象（例如，项目、文档集等）的功能
- 添加了将 NLU 模型部署到特定 {{site.data.keyword.Bluemix}} 区域的功能
- 提高了为 IAA 显示大型表的性能
- 修复了不严重的缺陷
- 应用了安全性修订

## 2017 年 4 月
{: #april2017}

- 提高了 {{site.data.keyword.knowledgestudioshort}} Premium 的稳定性
- 添加了针对业务度量值的使用情况分析

## 2017 年 4 月之前的发行版

请参阅 [{{site.data.keyword.IBM_notm}} 技术说明 #1986001 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.ibm.com/support/docview.wss?uid=swg21986001){: new_window}。
