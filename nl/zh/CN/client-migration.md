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

本文档适用于 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}。要查看 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 先前版本的文档，请[单击此链接 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/docs/services/knowledge-studio/client-migration.html){: new_window}。
{: tip}

# 迁移到 IBM Cloud
{: #migrate}

2017 年 12 月 18 日，IBM 推出了 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud_notm}}，这标志着将所有 {{site.data.keyword.knowledgestudioshort}} 实例从 {{site.data.keyword.IBM_notm}} Marketplace 迁移到 [{{site.data.keyword.cloud_notm}} 平台 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/blogs/bluemix/2017/12/watson-knowledge-studio-ibm-cloud/){: new_window} 的过程开始。
{: shortdesc}

**注**：{{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud_notm}} 使用术语_工作空间_，而 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 使用术语_项目_。这两个术语功能相同。只是术语表达不同而已。

**注意**：如果您需要遵循 GDPR，那么必须迁移到 {{site.data.keyword.cloud_notm}} 平台。{{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 已引退，不再适用于要求符合欧盟的一般数据保护条例 (GDPR) (EU) 2016/679 的客户机。

## 流程
{: #process}

{{site.data.keyword.knowledgestudioshort}} 项目的迁移过程取决于 {{site.data.keyword.IBM_notm}} Marketplace 预订，如下表中所示。

| 预订 |迁移过程|详细信息|
|------|-------------------|--------------------|
| 具有自助服务预订的标准套餐 |客户迁移实例和数据| 尽快迁移以便可以访问 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud_notm}} 的最新版本。| 具有预订合同的标准套餐 | {{site.data.keyword.IBM_notm}} 会迁移预订合同。客户会迁移实例和数据。|请联系 {{site.data.keyword.IBM_notm}} 指定的客户代表或联系 [{{site.data.keyword.cloud_notm}} 销售 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration)。|
| 具有预订合同的高端套餐 | {{site.data.keyword.IBM_notm}} 会迁移预订合同。{{site.data.keyword.IBM_notm}} 会迁移实例和数据。|请联系 {{site.data.keyword.IBM_notm}} 指定的客户代表或联系 [{{site.data.keyword.cloud_notm}} 销售 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration)。|
{: caption="表 1. 将 {{site.data.keyword.knowledgestudioshort}} 从 {{site.data.keyword.IBM_notm}} Marketplace 迁移到 {{site.data.keyword.cloud_notm}} 的过程和安排" caption-side="top"}

## 标准套餐实例的自助迁移
{: migratestandard}

如果您有标准套餐，请完成以下步骤以将实例从 {{site.data.keyword.IBM_notm}} Marketplace 迁移到 {{site.data.keyword.cloud_notm}}：

1. 如果您没有 {{site.data.keyword.cloud_notm}} 帐户，请使用 {{site.data.keyword.IBM_notm}} Marketplace 中的 {{site.data.keyword.ibmid}} 注册 [{{site.data.keyword.cloud_notm}} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/registration/){: new_window}。

   {{site.data.keyword.ibmid}} 是您用于登录到 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 的标识。

2. 登录到 [{{site.data.keyword.cloud_notm}} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net){: new_window}。
3. 如果您的 {{site.data.keyword.cloud_notm}} 帐户是轻量帐户，请升级为付费帐户。有关付费帐户类型的更多信息，请参阅[帐户类型 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/docs/account/index.html){: new_window}。
4. 从 [{{site.data.keyword.cloud_notm}} 控制台 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/catalog/services/knowledge-studio){: new_window}，创建 {{site.data.keyword.knowledgestudioshort}} 标准套餐。
5. 按屏幕上的指示信息操作，表明您要将实例从 {{site.data.keyword.IBM_notm}} Marketplace 迁移到 {{site.data.keyword.cloud_notm}}。
6. 如果要迁移多个实例，请重复该过程。

## 高端套餐实例的迁移
{: migratesubscription}

如果有 {{site.data.keyword.knowledgestudioshort}} 高端套餐，请联系 {{site.data.keyword.IBM_notm}} 指定的客户代表或联系 [{{site.data.keyword.cloud_notm}} 销售 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration)。在将预订迁移到 {{site.data.keyword.cloud_notm}} 之后，IBM 将根据您与 {{site.data.keyword.IBM_notm}} 之间协商的安排来迁移您的数据。
