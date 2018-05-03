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

本文档适用于 {{site.data.keyword.cloud}} 上的 {{site.data.keyword.knowledgestudiofull}}。要查看 {{site.data.keyword.IBM_notm}} Marketplace 上先前版本的 {{site.data.keyword.knowledgestudioshort}} 的文档，请[单击此链接 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/docs/services/knowledge-studio/troubleshooting.html){: new_window}。
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

在开始描述问题时，最显而易见的提问是“问题是什么？”。此提问可能看起来很简单；但是，您可以将它分解为多个更有针对性的提问，从而更详细地描述所发生的问题。这些提问可能包括：

- 谁或什么报告了问题？
- 错误代码和消息的内容是什么？
- 系统如何发生故障？例如，是循环、挂起、崩溃、性能下降还是结果不正确？

### 问题在何处出现？

确定问题来源并非总是很容易，但这是解决问题最重要的步骤之一。在报告组件和故障组件之间可能存在许多技术层。网络、磁盘和驱动程序只是调查问题时需要考虑的一小部分组件。

以下提问有助于您关注发生问题的位置，从而找出发生问题的层：

- 问题是特定于一个平台或操作系统，还是在多个平台或操作系统中都会出现？
- 当前环境和配置是否受支持？
- 是否所有用户都遇到此问题？
- （对于多站点安装。）是否所有站点都遇到此问题？

如果某一层报告了问题，此问题并不一定发生在该层。了解存在此问题的环境，也是确定问题来源的一部分。请花一些时间来完整描述问题环境，其中包括操作系统和版本、所有对应软件和版本以及硬件信息。确认您是在作为受支持配置的环境中运行；许多问题可回溯到软件的不兼容级别，这些不兼容级别不适合一起运行，或者未一起进行完全测试。

### 问题在何时出现？

制定引起失败的各个事件的详细时间线，尤其对于那些只发生一次的情况。通过倒推法最容易制定时间线：从报告错误的时间开始（时间要尽可能精确，甚至精确到毫秒），一直倒推到可用的日志和信息。通常，只需要倒推至诊断日志中找到的第一个可疑事件即可。


要制定事件的详细时间线，请回答下列提问：

- 该问题是否只在白天或晚上的某个时间发生？
- 该问题发生的频率是多少？
- 在报告该问题的时间之前的事件序列是什么？
- 该问题是否出现在环境更改（如升级或者安装软件或硬件）之后？

回答这些类型的提问可为您提供用于调查该问题的参照标准。

### 问题在何种情况下出现？

了解在问题发生时有哪些系统和应用程序正在运行，是故障诊断的一个重要部分。有关您环境的以下提问可以帮助您识别问题的根本原因：

- 该问题是否总是在执行同一个任务时发生？
- 是否需要发生一系列特定事件才会产生该问题？
- 是否有其他任何应用程序同时发生故障？


回答这些类型的提问可以帮助您解释该问题发生时所处的环境，并将任何依赖性关联起来。请记住，仅凭多个问题可能在差不多相同的时间发生，并不能断定这些问题一定相关。

### 问题是否可重现？

从故障诊断的角度来看，理想的问题是可重现的问题。通常，如果可以重现该问题，您就有更多的工具或过程可供使用，以帮助进行调查。因此，可以重现的问题通常更加易于调试和解决。

但是，可以重现的问题可能有一个缺点：如果该问题会对业务产生重大影响，那么您并不希望重现该问题。如果有可能，请在测试环境或开发环境中重现该问题，这通常使您在调查期间可获得更大的灵活性和控制能力。

- 问题是否可在测试系统上重现？
- 是否有多个用户或应用程序遇到同一类型的问题？
- 问题是否可以通过运行单个命令、一组命令或某个特定应用程序来重现？

## AlchemyLanguage 模型问题
{: #wks_ts_deployed_model_deleted}

### 问题

您无法部署 AlchemyLanguage 模型，或者虽然部署成功，但模型不可用。

### 症状

- 您已部署模型，但状态显示发生错误。
- 您已部署模型，并且状态指示该模型可用，但您无法使用该模型。
- 模型已成功部署并且之前曾正常工作，但现在无法正常工作。

### 原因

以下事件可能导致已部署的模型出现问题：

- 如果向 REST API 调用的 `apikey` 参数添加密钥时输入错误的 {{site.data.keyword.alchemyapishort}} 密钥，那么调用将失败。对于模型标识也是如此。最好是复制并粘贴模型标识和 API 密钥，以避免输入错误。
- 如果提供的 {{site.data.keyword.alchemyapishort}} 密钥无效或者未授权以用于部署定制模型，那么部署过程将指示模型已成功部署，但是您将无法使用此模型。
- 如果在 {{site.data.keyword.Bluemix}} 中使用 {{site.data.keyword.alchemylanguageshort}} 时删除了与 {{site.data.keyword.Bluemix_notm}} 中的 {{site.data.keyword.alchemyapishort}} 密钥相关联的所有服务实例，那么将从服务中除去引用该键的任何已部署的模型。{{site.data.keyword.Bluemix_notm}} 会定期检查已注册的模型是否与有效密钥相关联，并会删除无关联的任何模型。如果部署模型时所依据的密钥被删除，那么模型的状态将更改为 `error`。

### 解决问题

1. 检查部署的状态。

    以 {{site.data.keyword.knowledgestudioshort}} 管理员身份登录。在**模型管理** > **版本**页面上，查看**状态**列以检查部署的模型的状态。

1. 如果模型的部署状态为 `error` 或者状态为 `available`，但是在尝试使用时模型未正常工作，那么单击**取消部署**以从部署中撤销模型。
1. 重新部署模型。

    仅使用获得授权以部署模型的有效 {{site.data.keyword.alchemyapishort}} 密钥，并且在将模型标识和 API 密钥作为参数添加到 API 调用时，复制并粘贴该模型标识和 API 密钥。

**相关任务**：

[将机器学习模型部署到 {{site.data.keyword.IBM_notm}} {{site.data.keyword.alchemylanguageshort}}](/docs/services/watson-knowledge-studio/publish-ml.html#wks_mabluemix)

## 无法创建免费帐户
{: #wks_ts_free}

### 问题

您尝试创建免费帐户，却看到错误消息：`Error 331: We are unable to process your request. Please try again later or contact the {{site.data.keyword.IBM_notm}} Helpdesk.`

### 原因

{{site.data.keyword.knowledgestudioshort}} 不允许每个组织使用多个免费帐户。

### 解决问题

创建未包含在组织中的帐户。

如果需要将当前帐户用于免费试用，并且您的用户帐户与付费帐户相关联，那么可提交支持凭单。有关更多信息，请参阅[联系 {{site.data.keyword.IBM_notm}} 支持](/docs/services/watson-knowledge-studio/troubleshooting.html#ts_contactingibmsupport)。

如果需要将当前帐户用于免费试用并且用户帐户未与付费帐户相关联，请将问题发布到 [{{site.data.keyword.IBM_notm}} developerWorks Answers](https://developer.ibm.com/answers/topics/wks/)，并确保为问题添加标记 **WKS**。

## 无法访问应用程序
{: #wks_ts_access}

了解如何授权用户访问 {{site.data.keyword.knowledgestudioshort}} 和解决常见访问问题。

您必须具有 {{site.data.keyword.IBM_notm}} 用户注册凭证才能请求 {{site.data.keyword.IBM_notm}} {{site.data.keyword.knowledgestudioshort}} 实例。

### 管理员

每个 {{site.data.keyword.knowledgestudioshort}} 实例都具有关联的管理员角色。将为最初注册以使用该应用程序的人员自动授予管理员角色。管理员可以邀请其他人员。

有关如何邀请人员来使用应用程序实例的信息，请参阅[组建团队](/docs/services/watson-knowledge-studio/team.html)。

### 人类注释者

如果您受邀加入某人的 {{site.data.keyword.knowledgestudioshort}} 实例以充当人类注释者，那么您可能已收到电子邮件邀请。首先，如果您还没有 {{site.data.keyword.IBM_notm}} 注册凭证，那么必须向 {{site.data.keyword.IBM_notm}} 进行注册。在向 {{site.data.keyword.IBM_notm}} 进行注册并接受邀请后，将向您授予实例访问权。但是，在向您授予访问权后，实例的管理员或项目经理必须将您添加到工作空间并将注释任务分配给您，然后您才能开始注释文档。在向您分配任务之前，您无法在 {{site.data.keyword.knowledgestudioshort}} 实例中执行任何操作。要注释文档，请使用参考标准编辑器。使用 Google Chrome 浏览器以实现最佳性能。

有关使用参考标准编辑器的帮助，请参阅[注释文档](/docs/services/watson-knowledge-studio/user-guide.html)。

## 试验性服务：*试验性*是指什么？
{: #experimental}

有关试验性服务的信息，请参阅 [{{site.data.keyword.Bluemix_notm}} 文档](/docs/services/index.html#experimental_services)。有关试验性服务的完整详细信息，请参阅最新版本的 [{{site.data.keyword.Bluemix_notm}} 服务描述 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.ibm.com/software/sla/sladb.nsf/searchsaas/?searchview&searchorder=4&searchmax=0&query=IBM+Bluemix+Service+Description){: new_window}。

## 存储空间问题
{: #storage}

根据您的预订套餐，您可能会达到针对套餐指定的存储限制，从而被禁止执行想要完成的任务。

### 症状

在尝试执行以下某个任务时，可能会看到有关已超过允许的存储空间的消息：

- 上传文档或字典
- 部署模型或构建模型版本
- 在文档上运行预注释器

### 原因

已达到存储限制，或者如果操作继续将超出存储限制。

### 解决问题

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

### 开始之前

首先，查看是否为您遇到的问题记录了解决方案。在 [{{site.data.keyword.IBM_notm}} 支持门户网站 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/home/entry/portal){: new_window} 上搜索 {{site.data.keyword.knowledgestudioshort}}。在搜索结果页面上，单击**支持**选项卡以查看来自技术说明、{{site.data.keyword.IBM_notm}} 红皮书和文档的结果。单击**开发者**选项卡以查看来自 {{site.data.keyword.IBM_notm}} developerWorks 社区（例如，博客和论坛问题）的结果。

在尝试通过搜索 [{{site.data.keyword.IBM_notm}} 支持门户网站 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/home/entry/portal){: new_window} 查找答案或解决方案后，可联系 {{site.data.keyword.IBM_notm}} 支持。您所拥有的支持类型取决于服务类型。

- **免费套餐用户**

    通过询问开发者社区的伙伴成员，获取问题的帮助和答案。有关开发者社区的链接，请参阅目录中的**开发者社区**部分。

- **付费套餐用户**

    作为付费套餐用户，您也可以提问题并从其他用户的问题进行学习。论坛对所有人都开放，是入门的理想之选。有关链接，请参阅目录中的**开发者社区**部分。

    从 [{{site.data.keyword.IBM_notm}} Cloud 服务门户网站 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://watson.service-now.com/wcp){: new_window} 提交问题凭单。

    > **注：**您必须获得授权以向 {{site.data.keyword.IBM_notm}} 提交问题。

### 过程

要针对某个问题联系 {{site.data.keyword.IBM_notm}} 支持，请执行以下操作：

1. 定义问题，收集背景信息并确定问题的严重性。
1. 收集诊断信息（如果可能）。
1. 将问题提交至 {{site.data.keyword.IBM_notm}} 支持。有关联系人详细信息，请参阅[软件即服务支持指南 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www-01.ibm.com/software/support/acceleratedvalue/SaaS_Handbook_V18.pdf){: new_window}。
