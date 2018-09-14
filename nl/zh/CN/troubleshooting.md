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

本文档适用于 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}。要查看 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 先前版本的文档，请[单击此链接 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/docs/services/knowledge-studio/troubleshooting.html){: new_window}。
{: tip}

# 故障诊断、支持和常见问题及解答
{: #troubleshooting}

要找出并解决 {{site.data.keyword.IBM_notm}} 产品的问题，可使用故障诊断与支持信息。此信息包括有关使用随 {{site.data.keyword.IBM_notm}} 产品（包括 {{site.data.keyword.knowledgestudiofull}}）提供的问题确定资源的指示信息。
{: shortdesc}

## 对问题进行故障诊断的方法
{: #ts_overview}

*故障诊断*是一种解决问题的系统方法。故障诊断的目标是确定某些功能不按预期工作的原因以及解决问题的方法。某些常用方法可以帮助完成故障诊断任务。

故障诊断过程的第一步是完整地描述问题。问题描述帮助您和 {{site.data.keyword.IBM_notm}} 技术支持代表了解从何处开始查找问题原因。此步骤包括向自己进行以下基本提问：

- 问题的症状是什么？
- 问题在何处出现？
- 问题在何时出现？
- 问题在何种情况下出现？
- 问题是否可重现？

这些提问的答案通常会形成对问题的良好描述，从而有助于解决问题。

### 问题的症状是什么？
{: #ts_overview_symptoms}

在开始描述问题时，最显而易见的提问是“问题是什么？”。此提问可能看起来很简单；但是，您可以将它分解为多个更有针对性的提问，从而更详细地描述所发生的问题。这些提问可能包括：

- 谁或什么报告了问题？
- 错误代码和消息的内容是什么？
- 系统如何发生故障？例如，是循环、挂起、崩溃、性能下降还是结果不正确？

### 问题在何处出现？
{: #ts_overview_where}

确定问题来源并非总是很容易，但这是解决问题最重要的步骤之一。在报告组件和故障组件之间可能存在许多技术层。网络、磁盘和驱动程序只是调查问题时需要考虑的一小部分组件。

以下提问有助于您关注发生问题的位置，从而找出发生问题的层：

- 问题是特定于一个平台或操作系统，还是在多个平台或操作系统中都会出现？
- 当前环境和配置是否受支持？
- 是否所有用户都遇到此问题？
- （对于多站点安装。）是否所有站点都遇到此问题？

如果某一层报告了问题，此问题并不一定发生在该层。了解存在此问题的环境，也是确定问题来源的一部分。请花一些时间来完整描述问题环境，其中包括操作系统和版本、所有对应软件和版本以及硬件信息。确认您是在作为受支持配置的环境中运行；许多问题可回溯到软件的不兼容级别，这些不兼容级别不适合一起运行，或者未一起进行完全测试。

### 问题在何时出现？
{: #ts_overview_when}

制定引起失败的各个事件的详细时间线，尤其对于那些只发生一次的情况。通过倒推法最容易制定时间线：从报告错误的时间开始（时间要尽可能精确，甚至精确到毫秒），一直倒推到可用的日志和信息。通常，只需要倒推至诊断日志中找到的第一个可疑事件即可。


要制定事件的详细时间线，请回答下列提问：

- 该问题是否只在白天或晚上的某个时间发生？
- 该问题发生的频率是多少？
- 在报告该问题的时间之前的事件序列是什么？
- 该问题是否出现在环境更改（如升级或者安装软件或硬件）之后？

回答这些类型的提问可为您提供用于调查该问题的参照标准。

### 问题在何种情况下出现？
{: #ts_overview_conditions}

了解在问题发生时有哪些系统和应用程序正在运行，是故障诊断的一个重要部分。有关您环境的以下提问可以帮助您识别问题的根本原因：

- 该问题是否总是在执行同一个任务时发生？
- 是否需要发生一系列特定事件才会产生该问题？
- 是否有其他任何应用程序同时发生故障？


回答这些类型的提问可以帮助您解释该问题发生时所处的环境，并将任何依赖性关联起来。请记住，仅凭多个问题可能在差不多相同的时间发生，并不能断定这些问题一定相关。

### 问题是否可重现？
{: #ts_overview_reproduce}

从故障诊断的角度来看，理想的问题是可重现的问题。通常，如果可以重现该问题，您就有更多的工具或过程可供使用，以帮助进行调查。因此，可以重现的问题通常更加易于调试和解决。

但是，可以重现的问题可能有一个缺点：如果该问题会对业务产生重大影响，那么您并不希望重现该问题。如果有可能，请在测试环境或开发环境中重现该问题，这通常使您在调查期间可获得更大的灵活性和控制能力。

- 问题是否可在测试系统上重现？
- 是否有多个用户或应用程序遇到同一类型的问题？
- 问题是否可以通过运行单个命令、一组命令或某个特定应用程序来重现？

## 无法在轻量套餐上创建实例
{: #wks_ts_lite}

### 问题
{: #wks_ts_lite_problem}

您尝试在轻量套餐上创建 {{site.data.keyword.knowledgestudioshort}} 实例，并看到错误消息：`Error 331: We are unable to process your request.Please try again later or contact the {{site.data.keyword.IBM_notm}} Helpdesk.`

### 原因
{: #wks_ts_lite_causes}

{{site.data.keyword.knowledgestudioshort}} 不允许每个组织使用多个轻量套餐。

### 解决问题
{: #wks_ts_lite_resolve}

创建未包含在组织中的帐户。

如果您需要将当前帐户用于轻量套餐上的 {{site.data.keyword.knowledgestudioshort}} 实例，并且您的用户帐户与付费帐户相关联，那么可以创建案例。有关更多信息，请参阅[联系 {{site.data.keyword.IBM_notm}} 支持](/docs/services/watson-knowledge-studio/troubleshooting.html#ts_contactingibmsupport)。

如果您需要将当前帐户用于轻量套餐上的 {{site.data.keyword.knowledgestudioshort}} 实例，并且您的用户帐户未与付费帐户关联，请将您的问题发布到 [{{site.data.keyword.IBM_notm}} developerWorks Answers ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.ibm.com/answers/topics/watson-knowledge-studio/){: new_window}。将问题标记为 **WATSON-KNOWLEDGE-STUDIO**。

## 无法访问应用程序
{: #wks_ts_access}

了解如何授权用户访问 {{site.data.keyword.knowledgestudioshort}} 和解决常见访问问题。

您必须具有 {{site.data.keyword.IBM_notm}} 用户注册凭证才能请求 {{site.data.keyword.IBM_notm}} {{site.data.keyword.knowledgestudioshort}} 实例。

### 管理员
{: #wks_ts_access_administrator}

每个 {{site.data.keyword.knowledgestudioshort}} 实例都具有关联的管理员角色。将为最初注册以使用该应用程序的人员自动授予管理员角色。管理员可以邀请其他人员。

有关如何邀请人员来使用应用程序实例的信息，请参阅[组建团队](/docs/services/watson-knowledge-studio/team.html)。

### 人工注释者
{: #wks_ts_access_annotator}

如果您受邀加入某人的 {{site.data.keyword.knowledgestudioshort}} 实例以充当人工注释者，那么您可能已收到电子邮件邀请。首先，如果您还没有 {{site.data.keyword.IBM_notm}} 注册凭证，那么必须向 {{site.data.keyword.IBM_notm}} 进行注册。在向 {{site.data.keyword.IBM_notm}} 进行注册并接受邀请后，将向您授予实例访问权。但是，在向您授予访问权后，实例的管理员或项目经理必须将您添加到工作空间并将注释任务分配给您，然后您才能开始注释文档。在向您分配任务之前，您无法在 {{site.data.keyword.knowledgestudioshort}} 实例中执行任何操作。要注释文档，请使用参考标准编辑器。使用 Google Chrome 浏览器以实现最佳性能。

有关使用参考标准编辑器的帮助，请参阅[注释文档](/docs/services/watson-knowledge-studio/user-guide.html)。

## 数据收集
{: #content}

对于标准套餐（轻量、标准、Pro），缺省情况下，{{site.data.keyword.knowledgestudioshort}} 使用客户机数据来改进服务。此数据仅用于汇总。客户机数据不共享也不公开。

如果您有“管理员”角色，那么可以通过选择“服务详细信息”页面上的数据收集设置来更改此缺省行为。

对于高端套餐和 Dedicated 帐户，{{site.data.keyword.knowledgestudioshort}} 不使用客户机数据来改进服务。

有关更多信息，请参阅最新的 [{{site.data.keyword.knowledgestudioshort}} 服务描述 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/software/sla/sladb.nsf/searchsaas/?searchview&searchorder=4&searchmax=0&query=Knowledge+Studio){: new_window}。

## 试验性服务和功能部件：*试验性*是什么意思？
{: #experimental}

{{site.data.keyword.IBM_notm}} 发布试验性服务和功能部件，供您试用。这些服务可能不稳定，以与早期版本不兼容的方式频繁更改，并且随时可能会中断。建议不要将这些服务和功能部件用于生产环境。

有关试验性服务的更多信息，请参阅 [{{site.data.keyword.cloud_notm}} 文档 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/docs/get-support/servicessupport.html#s-services-exporcont){: new_window}。有关试验性服务的完整详细信息，请参阅最新版本的 [{{site.data.keyword.cloud_notm}} 服务描述 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/software/sla/sladb.nsf/sla/bm?OpenDocument){: new_window}。

## 存储空间问题
{: #storage}

根据您的预订套餐，您可能会达到针对套餐指定的存储限制，从而被禁止执行想要完成的任务。

### 症状
{: #storage_symptoms}

在尝试执行以下某个任务时，可能会看到有关已超过允许的存储空间的消息：

- 上传文档或字典
- 部署模型或构建模型版本
- 在文档上运行预注释器

### 原因
{: #storage_causes}

已达到存储限制，或者如果操作继续将超出存储限制。

### 解决问题
{: #storage_resolve}

存储空间的最大使用者是机器学习模型和基于规则的模型。要释放空间，可执行以下操作：

- 删除您认为不再需要还原至的任何模型的快照版本。
- 删除不需要的任何模型。
- 如果模型非常重要而不能删除，请考虑将套餐升级为可分配更大存储空间的套餐。

除去模型或模型版本后，请等待一个小时，然后再重试导致错误消息的操作。可能需要最多 1 小时，您释放的存储空间才可供使用。

为管理每月帐单，如果为您分配了 Admin 角色并且您具有“高端”或“标准”帐户，那么可在 {{site.data.keyword.knowledgestudioshort}} 中的“服务详细信息”页面上设置存储限制。要查看“服务详细信息”页面并设置存储限制，请从 {{site.data.keyword.knowledgestudioshort}} 中的顶部导航栏，单击**设置**图标，单击**查看/修改服务详细信息**链接，然后单击**设置存储限制**链接。
{: tip}

## 联系 IBM 支持
{: #ts_contactingibmsupport}

{{site.data.keyword.IBM_notm}} 支持机构提供有关产品缺陷的帮助，回答常见问题并帮助用户解决产品问题。

- **未与付费帐户关联的轻量套餐客户**

    通过询问开发者社区的伙伴成员，获取问题的帮助和答案。对于链接，请参阅目录底部的“开发者社区”部分。

- **与付费帐户关联的客户**

    作为与付费帐户关联的客户，您也可以提问，并从其他用户的问题中学习。开发者社区对所有人都开放，是入门的理想之选。对于链接，请参阅目录底部的“开发者社区”部分。

    **要联系 {{site.data.keyword.IBM_notm}} 支持：**

    您必须获得授权才能在 {{site.data.keyword.cloud_notm}} 服务门户网站上创建支持案例。

    1. 定义问题，收集背景信息并确定问题的严重性。
    1. 收集诊断信息（如果可能）。
    1. 在 [{{site.data.keyword.cloud_notm}} 服务门户网站上创建案例 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://watson.service-now.com/wcp){: new_window}。
