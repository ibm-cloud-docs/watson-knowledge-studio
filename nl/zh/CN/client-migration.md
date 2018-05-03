---

copyright:
  years: 2015, 2018
lastupdated: "2018-03-14"

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

本文档适用于 {{site.data.keyword.cloud}} 上的 {{site.data.keyword.knowledgestudiofull}}。要查看 {{site.data.keyword.IBM_notm}} Marketplace 上先前版本的 {{site.data.keyword.knowledgestudioshort}} 的文档，请[单击此链接 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/docs/services/knowledge-studio/client-migration.html){: new_window}。
{: tip}

# 迁移到 IBM Cloud
{: #migrate}

2017 年 12 月 18 日，IBM 在 {{site.data.keyword.cloud_notm}} 上推出了 {{site.data.keyword.knowledgestudiofull}}，这标志着将所有 {{site.data.keyword.knowledgestudioshort}} 实例从 {{site.data.keyword.IBM_notm}} Marketplace 迁移到 {{site.data.keyword.cloud_notm}} 的过程的开始。
{: shortdesc}

**注**：{{site.data.keyword.cloud_notm}} 上的 {{site.data.keyword.knowledgestudioshort}} 使用术语_工作空间_，而 {{site.data.keyword.IBM_notm}} Marketplace 上的 {{site.data.keyword.knowledgestudioshort}} 使用术语_项目_。这两个术语功能相同。只是术语表达不同而已。

## 过程和安排
{: #process}

{{site.data.keyword.knowledgestudioshort}} 项目的迁移过程和安排取决于您当前在 [{{site.data.keyword.IBM_notm}} Marketplace 上的价格套餐 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/us-en/marketplace/supervised-machine-learning/purchase#product-header-top){: new_window} 和帐户类型，如下表中所示：

| 套餐和帐户| 迁移过程| 迁移安排|
|------|-------------------|--------------------|
| 免费套餐| 客户迁移实例和数据| 迁移必须在 2018 年 2 月 1 日或之前完成。2018 年 2 月 2 日，将清除 {{site.data.keyword.IBM_notm}} Marketplace 上的所有免费套餐，包括关联的项目数据。|
| 现买现付帐户的标准套餐| 客户迁移实例和数据| 迁移必须在 2018 年 6 月 29 日或之前完成。2018 年 6 月 30 日，将清除 {{site.data.keyword.IBM_notm}} Marketplace 上现买现付帐户的所有标准套餐，包括关联的项目数据。
| 依据合同的标准套餐| 客户迁移实例和数据。{{site.data.keyword.IBM_notm}} 更新合同。| 迁移必须在 2018 年 6 月 29 日或之前完成。请联系 {{site.data.keyword.IBM_notm}} 指定的客户代表或联系 [{{site.data.keyword.cloud_notm}} 销售 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration)。|
| 依据合同的高端套餐| {{site.data.keyword.IBM_notm}} 迁移实例和数据。{{site.data.keyword.IBM_notm}} 更新合同。| 迁移必须在 2018 年 6 月 29 日或之前完成。请联系 {{site.data.keyword.IBM_notm}} 指定的客户代表或联系 [{{site.data.keyword.cloud_notm}} 销售 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration)。|
{: caption="表 1. 将 {{site.data.keyword.knowledgestudioshort}} 从 {{site.data.keyword.IBM_notm}} Marketplace 迁移到 {{site.data.keyword.cloud_notm}} 的过程和安排" caption-side="top"}

## 免费套餐迁移
{: migratefree}

如果您具有 {{site.data.keyword.knowledgestudioshort}} 免费套餐，请完成以下步骤将实例和项目从 {{site.data.keyword.IBM_notm}} Marketplace 迁移到 {{site.data.keyword.cloud_notm}}：

1. 如果您没有 {{site.data.keyword.cloud_notm}} 帐户，请使用 {{site.data.keyword.IBM_notm}} Marketplace 中的 {{site.data.keyword.ibmid}} 注册 [{{site.data.keyword.cloud_notm}} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://ibm.biz/wks_cloud){: new_window}。

   {{site.data.keyword.ibmid}} 是您用于登录到 {{site.data.keyword.IBM_notm}} Marketplace 上的 {{site.data.keyword.knowledgestudioshort}} 的标识。

1. 登录到 [{{site.data.keyword.cloud_notm}} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/dashboard/apps/){: new_window}。
1. 如果在 {{site.data.keyword.cloud_notm}} 上没有 {{site.data.keyword.knowledgestudioshort}} 实例，请在 [{{site.data.keyword.cloud_notm}} 目录的 {{site.data.keyword.knowledgestudioshort}} 页面 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/catalog/services/knowledge-studio){: new_window} 上进行创建。
1. 执行[备份和复原](/docs/services/watson-knowledge-studio/backup-restore.html)过程，以手动方式将项目从 {{site.data.keyword.IBM_notm}} Marketplace 实例迁移到 {{site.data.keyword.cloud_notm}} 上的实例。

  **注**：如果您具有已部署的模型，并且计划在备份后删除工作空间，请从部署中撤销该模型。从备份复原工作空间后，可以重新构建并重新部署该模型。有关取消部署模型的信息，请参阅[取消部署机器学习模型](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model)和[取消部署基于规则的模型](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model)。

## 迁移现买现付帐户的标准套餐
{: migratepaygo}

如果您具有标准套餐和[现买现付 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/docs/pricing/billable.html){: new_window} 帐户，请完成以下步骤将实例和项目从 {{site.data.keyword.IBM_notm}} Marketplace 迁移到 {{site.data.keyword.cloud_notm}}：

1. 如果您没有 {{site.data.keyword.cloud_notm}} 帐户，请使用 {{site.data.keyword.IBM_notm}} Marketplace 中的 {{site.data.keyword.ibmid}} 注册 [{{site.data.keyword.cloud_notm}} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/cloud/){: new_window}。

   {{site.data.keyword.ibmid}} 是您用于登录到 {{site.data.keyword.IBM_notm}} Marketplace 上的 {{site.data.keyword.knowledgestudioshort}} 的标识。

1. 登录到 [{{site.data.keyword.cloud_notm}} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/dashboard/apps/){: new_window}。
1. 如果在 {{site.data.keyword.cloud_notm}} 上没有 {{site.data.keyword.knowledgestudioshort}} 实例，请在 [{{site.data.keyword.cloud_notm}} 目录的 {{site.data.keyword.knowledgestudioshort}} 页面 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/catalog/services/knowledge-studio){: new_window} 上进行创建。
1. 执行[备份和复原](/docs/services/watson-knowledge-studio/backup-restore.html)过程，以手动方式将项目从 {{site.data.keyword.IBM_notm}} Marketplace 实例迁移到 {{site.data.keyword.cloud_notm}} 上的实例。

  **注**：如果您具有已部署的模型，并且计划在备份后删除工作空间，请从部署中撤销该模型。从备份复原工作空间后，可以重新构建并重新部署该模型。有关取消部署模型的信息，请参阅[取消部署机器学习模型](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model)和[取消部署基于规则的模型](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model)。

## 迁移合同帐户的标准套餐
{: migratecontract}

如果您具有依据合同的 {{site.data.keyword.knowledgestudioshort}} 标准套餐，请完成以下步骤来更新合同，并将实例和项目从 {{site.data.keyword.IBM_notm}} Marketplace 迁移到 {{site.data.keyword.cloud_notm}}：

1. 要更新合同，请联系 {{site.data.keyword.IBM_notm}} 指定的客户代表或联系 [{{site.data.keyword.cloud_notm}} 销售 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration)。
1. 在 {{site.data.keyword.cloud_notm}} 上更新合同后，请登录到 [{{site.data.keyword.cloud_notm}} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/dashboard/apps/){: new_window}。
1. 如果在 {{site.data.keyword.cloud_notm}} 上没有 {{site.data.keyword.knowledgestudioshort}} 实例，请在 [{{site.data.keyword.cloud_notm}} 目录的 {{site.data.keyword.knowledgestudioshort}} 页面 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/catalog/services/knowledge-studio){: new_window} 上进行创建。
1. 执行[备份和复原](/docs/services/watson-knowledge-studio/backup-restore.html)过程，以手动方式将项目从 {{site.data.keyword.IBM_notm}} Marketplace 实例迁移到 {{site.data.keyword.cloud_notm}} 上的实例。

  **注**：如果您具有已部署的模型，并且计划在备份后删除工作空间，请从部署中撤销该模型。从备份复原工作空间后，可以重新构建并重新部署该模型。有关取消部署模型的信息，请参阅[取消部署机器学习模型](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model)和[取消部署基于规则的模型](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model)。

## 迁移合同帐户的高端套餐
{: migratecontract}

如果您具有依据合同的 {{site.data.keyword.knowledgestudioshort}} 高端套餐，请联系 {{site.data.keyword.IBM_notm}} 指定的客户代表或联系 [{{site.data.keyword.cloud_notm}} 销售 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration)。在 {{site.data.keyword.cloud_notm}} 上更新合同后，IBM 将根据您与 {{site.data.keyword.cloud_notm}} 之间协商的安排来迁移您的数据。
