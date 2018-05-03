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

本文档适用于 {{site.data.keyword.cloud}} 上的 {{site.data.keyword.knowledgestudiofull}}。要查看 {{site.data.keyword.IBM_notm}} Marketplace 上先前版本的 {{site.data.keyword.knowledgestudioshort}} 的文档，请[单击此链接 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/docs/services/knowledge-studio/release-notes.html){: new_window}。
{: tip}

# 发行说明
{: #release-notes}

为 {{site.data.keyword.knowledgestudiofull}} 提供了以下新功能和更改。
{: shortdesc}

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

- 针对作为[试验性](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)服务的 {{site.data.keyword.Bluemix}} 上的 {{site.data.keyword.knowledgestudioshort}} 发布了新的前端用户体验。更改包括已重组的导航和新的模型性能分析页面。有关导航更改的摘要，请参阅已知问题中的表。
- 添加了简体中文和荷兰语语言支持。

### 已知问题
{: #issues-sept17}

- 对于基于规则的模型，在映射类和实体类型之后，**导出**按钮在刷新浏览器窗口后才会启用。
- 对于 {{site.data.keyword.Bluemix_notm}} [试验性](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)发行版，其中一些文档术语与新界面不匹配。文档与 {{site.data.keyword.IBM_notm}} Marketplace 中的界面相匹配。在[试验性](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)发行版中更改了以下术语：

| {{site.data.keyword.IBM_notm}} Marketplace 中的术语| {{site.data.keyword.Bluemix_notm}} 中的术语| 注释|
|----------|----------|----------|
| _项目_| _工作空间_| 此术语已更改，因为 {{site.data.keyword.Bluemix_notm}} 同时使用术语_项目_|
| _导入_和_导出_| _上传_和_下载_| 术语_导入_和_导出_用于文档和实体类型时，现在称为_上传_和_下载_。但在指示将模型导出到应用程序（如 {{site.data.keyword.watson}} Explorer）时，仍然会使用术语_导出_。|
{: caption="表 1. {{site.data.keyword.Bluemix_notm}} 版本的术语更改" caption-side="top"}

- 对于 {{site.data.keyword.Bluemix_notm}} [试验性](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)发行版，某些文档任务步骤与新界面不匹配。文档与 {{site.data.keyword.IBM_notm}} Marketplace 中的界面相匹配。下表总结了[试验性](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)发行版的导航更改：

| 功能部件| {{site.data.keyword.IBM_notm}} Marketplace 位置| {{site.data.keyword.Bluemix_notm}} 位置
|----------|----------|----------|
|“注释器组件”选项卡| 主导航| 不再存在|
|“混淆矩阵”表（“统计信息”选项卡中）| “注释器组件”>“详细信息”| “模型管理”>“性能”>“详细统计信息”链接|
|“字典”选项卡| 主导航| “资产和工具”>“预注释器”|
|“字典映射”页面| 注释器组件| “资产和工具”>“预注释器”|
|“实体类型”选项| 类型系统| “资产和工具”>“实体类型”|
|参考标准编辑器| 人工注释| “文档注释”选项卡|
|参考标准编辑器的“设置”选项卡| 人工注释| “设置”>“文档注释设置”|
|模型（运行和导出）| 注释器组件| “模型管理”>“版本”|
|“规则”选项卡| 主导航| “文档注释”>“规则”|
|“统计信息”选项卡| “注释器组件”>“详细信息”| “模型管理”>“性能”|
|摘要表（“统计信息”选项卡中）| “注释器组件”>“详细信息”| “模型管理”>“性能”>“详细统计信息”链接|
|“类型映射”选项卡（对于基于规则的模型）| “注释器组件”>“详细信息”| “模型管理”>“版本”>“基于规则的模型类型映射”|
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
