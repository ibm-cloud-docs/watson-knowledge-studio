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

此文件適用於 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}。如果要在 {{site.data.keyword.IBM_notm}} Marketplace 上查看舊版 {{site.data.keyword.knowledgestudioshort}} 的文件，[請按一下這個鏈結 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/docs/services/knowledge-studio/client-migration.html){: new_window}。
{: tip}

# 移轉至 IBM Cloud
{: #migrate}

在 2017 年 12 月 18 日，IBM 發表了 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud_notm}}，它標示了開始將所有 {{site.data.keyword.knowledgestudioshort}} 實例從 {{site.data.keyword.IBM_notm}} Marketplace 移轉至 {{site.data.keyword.cloud_notm}} 的處理程序。
{: shortdesc}

**附註**：{{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud_notm}} 使用_工作區_ 一詞，而 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 使用_專案_ 一詞。功能相同。只有術語不同。

## 程序與時間表
{: #process}

{{site.data.keyword.knowledgestudioshort}} 專案的移轉程序與時間表，取決於您目前的 [{{site.data.keyword.IBM_notm}} Marketplace 定價方案 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/us-en/marketplace/supervised-machine-learning/purchase#product-header-top){: new_window} 與帳戶類型，如下表所示：

| 方案及帳戶| 移轉程序| 移轉時間表|
|------|-------------------|--------------------|
| 免費方案| 客戶移轉實例和資料| 移轉必須在 2018 年 2 月 1 日（含）前完成。在 2018 年 2 月 2 日，將會清除 {{site.data.keyword.IBM_notm}} Marketplace 上所有免費方案，包括相關聯的專案資料。|
| 使用「隨收隨付制」帳戶的標準方案| 客戶移轉實例和資料| 移轉必須在 2018 年 6 月 29 日（含）前完成。在 2018 年 6 月 30 日，將會清除 {{site.data.keyword.IBM_notm}} Marketplace 上所有使用「隨收隨付制」帳戶的標準方案，包括相關聯的專案資料。| 按照合約的標準方案| 客戶移轉實例和資料。{{site.data.keyword.IBM_notm}} 更新合約。| 移轉必須在 2018 年 6 月 29 日（含）前完成。請聯絡您的 {{site.data.keyword.IBM_notm}} 指定客戶代表或聯絡 [{{site.data.keyword.cloud_notm}} 業務人員 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration)。|
| 按照合約的超值方案| {{site.data.keyword.IBM_notm}} 移轉實例和資料。{{site.data.keyword.IBM_notm}} 更新合約。| 移轉必須在 2018 年 6 月 29 日（含）前完成。請聯絡您的 {{site.data.keyword.IBM_notm}} 指定客戶代表或聯絡 [{{site.data.keyword.cloud_notm}} 業務人員 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration)。|
{: caption="表 1. 將 {{site.data.keyword.knowledgestudioshort}} 從 {{site.data.keyword.IBM_notm}} Marketplace 移轉至 {{site.data.keyword.cloud_notm}} 的程序與時間表" caption-side="top"}

## 免費方案的移轉
{: migratefree}

如果您有 {{site.data.keyword.knowledgestudioshort}} 免費方案，請完成下列步驟，將實例和專案從 {{site.data.keyword.IBM_notm}} Marketplace 移轉至 {{site.data.keyword.cloud_notm}}：

1. 如果您沒有 {{site.data.keyword.cloud_notm}} 帳戶，請在 [{{site.data.keyword.cloud_notm}} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://ibm.biz/wks_cloud){: new_window} 使用來自 {{site.data.keyword.IBM_notm}} Marketplace 的 {{site.data.keyword.ibmid}} 註冊。

   您的 {{site.data.keyword.ibmid}} 是您用來在 {{site.data.keyword.IBM_notm}} Marketplace 上登入 {{site.data.keyword.knowledgestudioshort}} 的 ID。

1. 登入 [{{site.data.keyword.cloud_notm}} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/dashboard/apps/){: new_window}。
1. 如果您在 {{site.data.keyword.cloud_notm}} 上沒有 {{site.data.keyword.knowledgestudioshort}} 實例，請在 [{{site.data.keyword.cloud_notm}} 型錄 {{site.data.keyword.knowledgestudioshort}} 頁面 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/catalog/services/knowledge-studio){: new_window} 建立一個。
1. 遵循[備份及還原](/docs/services/watson-knowledge-studio/backup-restore.html)程序，將專案手動從 {{site.data.keyword.IBM_notm}} Marketplace 實例移轉至 {{site.data.keyword.cloud_notm}} 上的實例。

  **附註**：如果您有已部署的模型，且計劃在備份之後刪除工作區，請從部署中撤銷該模型。從備份還原工作區之後，您可以重建及重新部署模型。如需取消部署模型的相關資訊，請參閱[取消部署機器學習模型](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model)及[取消部署規則型模型](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model)。

## 「隨收隨付制」帳戶的標準方案移轉
{: migratepaygo}

如果您有標準方案及[隨收隨付制 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/docs/pricing/billable.html){: new_window} 帳戶，請完成下列步驟，將實例和專案從 {{site.data.keyword.IBM_notm}} Marketplace 移轉至 {{site.data.keyword.cloud_notm}}：

1. 如果您沒有 {{site.data.keyword.cloud_notm}} 帳戶，請在 [{{site.data.keyword.cloud_notm}} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/){: new_window} 使用來自 {{site.data.keyword.IBM_notm}} Marketplace 的 {{site.data.keyword.ibmid}} 註冊。

   您的 {{site.data.keyword.ibmid}} 是您用來在 {{site.data.keyword.IBM_notm}} Marketplace 上登入 {{site.data.keyword.knowledgestudioshort}} 的 ID。

1. 登入 [{{site.data.keyword.cloud_notm}} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/dashboard/apps/){: new_window}。
1. 如果您在 {{site.data.keyword.cloud_notm}} 上沒有 {{site.data.keyword.knowledgestudioshort}} 實例，請在 [{{site.data.keyword.cloud_notm}} 型錄 {{site.data.keyword.knowledgestudioshort}} 頁面 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/catalog/services/knowledge-studio){: new_window} 建立一個。
1. 遵循[備份及還原](/docs/services/watson-knowledge-studio/backup-restore.html)程序，將專案手動從 {{site.data.keyword.IBM_notm}} Marketplace 實例移轉至 {{site.data.keyword.cloud_notm}} 上的實例。

  **附註**：如果您有已部署的模型，且計劃在備份之後刪除工作區，請從部署中撤銷該模型。從備份還原工作區之後，您可以重建及重新部署模型。如需取消部署模型的相關資訊，請參閱[取消部署機器學習模型](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model)及[取消部署規則型模型](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model)。

## 合約帳戶的標準方案移轉
{: migratecontract}

如果您有按照合約的 {{site.data.keyword.knowledgestudioshort}} 標準方案，請完成下列步驟更新合約，並將實例和專案從 {{site.data.keyword.IBM_notm}} Marketplace 移轉至 {{site.data.keyword.cloud_notm}}：

1. 若要更新您的合約，請聯絡您的 {{site.data.keyword.IBM_notm}} 指定客戶代表或聯絡 [{{site.data.keyword.cloud_notm}} 業務人員 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration)。
1. 在 {{site.data.keyword.cloud_notm}} 上更新合約之後，登入 [{{site.data.keyword.cloud_notm}} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/dashboard/apps/){: new_window}。
1. 如果您在 {{site.data.keyword.cloud_notm}} 上沒有 {{site.data.keyword.knowledgestudioshort}} 實例，請在 [{{site.data.keyword.cloud_notm}} 型錄 {{site.data.keyword.knowledgestudioshort}} 頁面 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/catalog/services/knowledge-studio){: new_window} 建立一個。
1. 遵循[備份及還原](/docs/services/watson-knowledge-studio/backup-restore.html)程序，將專案手動從 {{site.data.keyword.IBM_notm}} Marketplace 實例移轉至 {{site.data.keyword.cloud_notm}} 上的實例。

  **附註**：如果您有已部署的模型，且計劃在備份之後刪除工作區，請從部署中撤銷該模型。從備份還原工作區之後，您可以重建及重新部署模型。如需取消部署模型的相關資訊，請參閱[取消部署機器學習模型](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model)及[取消部署規則型模型](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model)。

## 合約帳戶的超值方案移轉
{: migratecontract}

如果您有按照合約的 {{site.data.keyword.knowledgestudioshort}} 超值方案，請聯絡您的 {{site.data.keyword.IBM_notm}} 指定客戶代表或聯絡 [{{site.data.keyword.cloud_notm}} 業務人員 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration)。在 {{site.data.keyword.cloud_notm}} 上更新合約之後，IBM 將會依您和 {{site.data.keyword.cloud_notm}} 之間協商的時間表來移轉您的資料。
