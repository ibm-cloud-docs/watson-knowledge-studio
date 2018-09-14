---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-27"

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

# 信息安全
{: #information-security}

IBM 致力于为客户和合作伙伴提供创新的数据隐私、安全和监管解决方案。
{: shortdesc}

**注意：**
客户负责确保自己遵守各种法律和法规，包括欧盟一般数据保护条例。客户自行负责获取合格法律咨询机构有关可能影响客户业务的任何相关法律法规的识别和解释的建议，以及有关客户为符合此类法律法规的要求而可能需要采取的任何行动的建议。

此处描述的产品、服务和其他功能并非对于所有客户情况都适用，并且可能具有有限的可用性。IBM 不提供法律、核算或审计建议，也不表示或保证其服务或产品可以确保客户遵守任何法律或法规。

如果需要为已创建的 {{site.data.keyword.cloud}} {{site.data.keyword.watson}} 资源请求 GDPR 支持

- 在欧盟，请参阅[请求对在欧盟创建的 IBM Cloud Watson 资源的支持 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/docs/services/watson/getting-started-gdpr-sar.html#request-EU){: new_window}。
- 在欧盟以外的地区，请参阅[请求对欧盟以外的资源的支持 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/docs/services/watson/getting-started-gdpr-sar.html#request-non-EU){: new_window}。

## 欧盟一般数据保护条例 (GDPR)
{: #gdpr}

IBM 致力于为客户和合作伙伴提供创新的数据隐私、安全和监管解决方案，以协助用户实现 GDPR 合规性。

了解有关 IBM 自己的 GDPR 如何准备就绪的更多信息，以及我们的 GDPR 功能和产品如何支持您逐步实现合规性，请点击[此处 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.ibm.com/gdpr){: new_window}。

## {{site.data.keyword.knowledgestudioshort}} 中的 GDPR
{: #gdpr-wks}

{{site.data.keyword.knowledgestudiofull}} 提供了图形界面，通过该界面，您可以访问和删除包含数据的已上传工件。可以将以下工件上传到 {{site.data.keyword.knowledgestudioshort}}：
- 类型系统
- 字典
- 文档

如果收到要删除数据的请求，请完成以下步骤：
1. [删除适用的工件](/docs/services/watson-knowledge-studio/artifacts.html)。
2. [重新培训和重新部署模型](/docs/services/watson-knowledge-studio/train-ml.html)。
3. [删除使用已删除数据的模型先前版本](/docs/services/watson-knowledge-studio/improve-ml.html#wks_maversions)。
