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

此文件適用於 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}。如果要在 {{site.data.keyword.IBM_notm}} Marketplace 上查看舊版 {{site.data.keyword.knowledgestudioshort}} 的文件，[請按一下這個鏈結 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/docs/services/knowledge-studio/client-migration.html){: new_window}。
{: tip}

# 移轉至 IBM Cloud
{: #migrate}

在 2017 年 12 月 18 日，IBM 發表了 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud_notm}}，它標示了開始將所有 {{site.data.keyword.knowledgestudioshort}} 實例從 {{site.data.keyword.IBM_notm}} Marketplace 移轉至 [{{site.data.keyword.cloud_notm}} 平台的處理程序 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/blogs/bluemix/2017/12/watson-knowledge-studio-ibm-cloud/){: new_window}。
{: shortdesc}

**附註**：{{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud_notm}} 使用_工作區_ 一詞，而 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 使用_專案_ 一詞。功能相同。只有術語不同。

**注意**：如果您需要符合 GDPR，則必須移轉至 {{site.data.keyword.cloud_notm}} 平台。{{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 已被淘汰，而且不適用於需要符合歐盟「一般資料保護規範 (GDPR)」(EU) 2016/679 的客戶。

## 處理程序
{: #process}

{{site.data.keyword.knowledgestudioshort}} 專案的移轉程序取決於 {{site.data.keyword.IBM_notm}} Marketplace 訂閱，如下表所示：

|訂閱|移轉程序|詳細資料|
|------|-------------------|--------------------|
|具有自助式訂閱的標準方案|客戶移轉實例和資料|盡快移轉以存取最新版本的 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud_notm}}。
|具有訂閱合約的標準方案| {{site.data.keyword.IBM_notm}} 會移轉訂閱合約。客戶會移轉實例及資料。|請聯絡您的 {{site.data.keyword.IBM_notm}} 指定客戶代表或聯絡 [{{site.data.keyword.cloud_notm}} 業務人員 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration)。|
|具有訂閱合約的超值方案| {{site.data.keyword.IBM_notm}} 會移轉訂閱合約。{{site.data.keyword.IBM_notm}} 會移轉實例及資料。|請聯絡您的 {{site.data.keyword.IBM_notm}} 指定客戶代表或聯絡 [{{site.data.keyword.cloud_notm}} 業務人員 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration)。|
{: caption="表 1. 將 {{site.data.keyword.knowledgestudioshort}} 從 {{site.data.keyword.IBM_notm}} Marketplace 移轉至 {{site.data.keyword.cloud_notm}} 的程序與時間表" caption-side="top"}

## 自行移轉標準方案實例
{: migratestandard}

如果您有「標準」方案，請完成下列步驟，將實例從 {{site.data.keyword.IBM_notm}} Marketplace 移轉至 {{site.data.keyword.cloud_notm}}：

1. 如果您沒有 {{site.data.keyword.cloud_notm}} 帳戶，請在 [{{site.data.keyword.cloud_notm}} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/registration/){: new_window} 使用來自 {{site.data.keyword.IBM_notm}} Marketplace 的 {{site.data.keyword.ibmid}} 註冊。

   您的 {{site.data.keyword.ibmid}} 是您用來在 {{site.data.keyword.IBM_notm}} Marketplace 上登入 {{site.data.keyword.knowledgestudioshort}} 的 ID。

2. 登入 [{{site.data.keyword.cloud_notm}} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}){: new_window}。
3. 如果您的 {{site.data.keyword.cloud_notm}} 帳戶為「精簡」帳戶，請升級至付費帳戶。如需付費帳戶類型的相關資訊，請參閱[帳戶類型 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/docs/account/index.html){: new_window}。
4. 從 [{{site.data.keyword.cloud_notm}} 主控台 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/catalog/services/knowledge-studio){: new_window} 中，建立 {{site.data.keyword.knowledgestudioshort}} 標準方案。
5. 遵循畫面上的指示，指出您想要將實例從 {{site.data.keyword.IBM_notm}} Marketplace 移轉至 {{site.data.keyword.cloud_notm}}。
6. 如果您有多個實例要進行移轉，請重複該程序。

## 移轉超值方案實例
{: migratesubscription}

如果您有 {{site.data.keyword.knowledgestudioshort}} 超值方案，請聯絡您的 {{site.data.keyword.IBM_notm}} 指定客戶代表或聯絡 [{{site.data.keyword.cloud_notm}} 業務人員 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration)。一旦訂閱移轉至 {{site.data.keyword.cloud_notm}}，IBM 就會依您與 {{site.data.keyword.IBM_notm}} 之間協商的排程來移轉您的資料。
