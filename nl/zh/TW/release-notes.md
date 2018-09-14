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

此文件適用於 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}。若要查看舊版 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 的文件，[請按一下此鏈結 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/docs/services/knowledge-studio/release-notes.html){: new_window}。
{: tip}

# 版本注意事項
{: #release-notes}

{{site.data.keyword.knowledgestudiofull}} 提供下列新增特性及變更。
{: shortdesc}

## 2018 年 8 月
{: #august2018}

### 新增特性及變更
{: #new-august2018}

- 引進一個新的選項，用於將「標準」方案實例從已淘汰的 {{site.data.keyword.IBM_notm}} Marketplace 平台自動移轉至 [{{site.data.keyword.cloud_notm}} 平台 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/blogs/bluemix/2017/12/watson-knowledge-studio-ibm-cloud/){: new_window}。如果您在已淘汰的平台上有「標準」實例，則將有移轉的選項。如需相關資訊，請參閱[移轉至 {{site.data.keyword.cloud_notm}}](/docs/services/watson-knowledge-studio/client-migration.html)。

## 2018 年 7 月
{: #july2018}

### 新增特性及變更
{: #new-july2018}

- 除了由 [Cloud Foundry* 組織 *![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/docs/iam/cfaccess.html){: new_window} 所管理的模型之外，**已部署的模型**頁面已更新為包括來自 [IAM* 資源群組* ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/docs/iam/users_roles.html){: new_window} 所管理之 {{site.data.keyword.knowledgestudioshort}} 實例的模型。

   您在「已部署的模型」頁面上看到的內容，取決於管理 {{site.data.keyword.knowledgestudioshort}} 實例的[地區 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/docs/resources/services_region.html){: new_window}。如果地區支援這兩種存取管理方法所管理的實例，則您會看到每一個方法的標籤。來自 IAM 所管理之實例的模型會列示在**資源群組**標籤上。來自 Cloud Foundry 所管理之實例的模型則會列示在**組織**標籤上。

  如果地區支援僅由其中一種存取管理方法管理的實例，則您只會看到一個模型清單，因為只有一個存取管理方法適用。

   若要檢視**已部署的模型**頁面，請從右上角功能表列的**設定**功能表中，按一下**管理已部署的模型**。如需在**已部署的模型**頁面上取消部署模型的相關資訊，請參閱[取消部署機器學習模型](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model)及[取消部署規則型模型](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model)。

- 導覽已變更，更能符合 {{site.data.keyword.knowledgestudioshort}} 工作流程。此外，也重組了下列功能：

    - 在舊版中，字典的管理已併入為「預先註釋程式」頁面的一部分。現在，字典的管理位於導覽的「資產」區段的「字典」頁面上。
    - 在舊版中，透過導覽的「文件註釋」區段中的「提及項目」、「關係」及「互相參照」標籤，來分配人工註釋功能。現在，此功能合併在導覽的「機器學習模型」區段中的「註釋作業」頁面下。
    - 若要管理人工註釋作業，請在舊版中，於「資產及工具」>「文件」頁面下找到「作業」標籤。現在，您可以在導覽的「機器學習模型」區段中的「註釋作業」頁面上，新增作業並管理現有作業。
    - 在舊版中，「規則」、「正規表示式」及「字典」頁面是導覽的「文件註釋」區段中的個別頁面。現在，此功能合併在導覽的「規則型模型」區段的「規則」頁面下。

    如需有關導覽變更的詳細資料，請參閱圖 1 和表 3。

![前一個導覽（左側）及新導覽（右側）的畫面擷取。](images/nav3-0718.svg "前一個導覽及新導覽的畫面擷取。變更的詳細資料列示在表 3 及先前的文字中。") 圖 1. 前一個導覽（左側）及新導覽（右側）的畫面擷取。

|特性|前一個位置|現行位置|
|---------|--------------------------|----------------------|
|註釋作業|資產及工具 > 文件 > 作業|機器學習模型 > 註釋作業|
|互相參照標籤|文件註釋|機器學習模型 > 註釋作業 > 作業 > 註釋集 > 文件|
|字典頁面（管理）|資產及工具 > 預先註釋程式 > 管理字典|資產|
|字典標籤（對映至規則型模型的類別）|文件註釋|規則型模型 > 規則|
|文件頁面|資產及工具|資產|
|「實體類型」頁面|資產及工具|資產|
|「提及項目」標籤|文件註釋|機器學習模型 > 註釋作業 > 作業 > 註釋集 > 文件|
|「效能」頁面|模型管理|機器學習模型|
|預先註釋程式頁面|資產及工具|機器學習模型 > 預先註釋|
|「正規表示式」標籤|文件註釋|規則型模型 > 規則|
|「關係類型」頁面|資產及工具|資產|
|「關係」標籤|文件註釋|機器學習模型 > 註釋作業 > 作業 > 註釋集 > 文件|
|「規則」標籤|文件註釋|規則型模型|
|「作業」標籤|資產及工具 > 文件|機器學習模型 > 註釋作業|
|版本頁面（機器學習模型）|模型管理|機器學習模型|
|版本頁面（規則型模型）|模型管理|規則型模型|
{: caption="表 3. 導覽變更（2018 年 7 月）" caption-side="top"}

## 2018 年 5 月
{: #may2018}

### 新增特性及變更
{: #new-may2018}

- 已修正導致雪梨地區中的服務實例未出現在美國南部地區的配置問題。
- 在「部署模型」視窗中，如果您要部署的地區同時支援{{site.data.keyword.iamlong}}*資源群組* 和 Cloud Foundry *空間*，則若要查看清單，您需要選擇服務實例使用的存取管理方法。如需 Cloud Foundry 及 {{site.data.keyword.iamshort}} 的相關資訊，請參閱[資源群組及存取管理 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/blogs/bluemix/2017/12/resource-groups-access-management/){: new_window}。
- 已在「服務詳細資料」頁面上新增資料收集設定。如需資料收集的相關資訊，請參閱[疑難排解、支援及常見問題](/docs/services/watson-knowledge-studio/troubleshooting.html#content)
- 已新增繁體中文支援。
- 具有 Admin 角色的使用者現在可以查看所使用的工作空間數目。「服務詳細資料」頁面上會提供此資訊。
- 再也無法將模型部署至 {{site.data.keyword.alchemylanguagefull}}。如需資訊，請參閱 [{{site.data.keyword.alchemyapishort}} 服務的淘汰 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/blogs/bluemix/2017/03/bye-bye-alchemyapi/){: new_window}。
- 現在，如果刪除工作區，將會要求您確認動作。我們希望這項確認可防止意外刪除。
- 說明文件包括有關資料隱私權的一些新詳細資料。深入閱讀[資訊安全](/docs/services/watson-knowledge-studio/information-security.html)。

## 2018 年 4 月
{: #april2018}

### 新增特性及變更
{: #new-april2018}

- {{site.data.keyword.knowledgestudioshort}}「免費」方案已取代為「精簡」方案。如需相關資訊，請參閱 [Go Lite with Watson {{site.data.keyword.knowledgestudioshort}} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/blogs/bluemix/2018/04/go-lite-watson-knowledge-studio/){: new_window}。

## 2018 年 3 月
{: #march2018}

### 新增特性及變更
{: #new-march2018}

- 提供**已部署的模型**頁面，您可以在其中檢視已部署至您有權存取之空間中服務的所有 {{site.data.keyword.knowledgestudioshort}}
模型。若要檢視**已部署的模型**頁面，請從右上角功能表列的**設定**功能表中，按一下**管理已部署的模型**。如需在**已部署的模型**頁面上取消部署及檢視模型的相關資訊，請參閱[取消部署機器學習模型](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model)及[取消部署規則型模型](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model)。
- 現在提供了 {{site.data.keyword.knowledgestudioshort}} 介面的法文翻譯。
- {{site.data.keyword.alchemylanguagefull}} 不再以預先註釋程式的形式來提供。您可以使用 {{site.data.keyword.nlushort}}
來預先註釋文件，而不是 {{site.data.keyword.alchemylanguageshort}}。如需相關資訊，請參閱[引導註釋](/docs/services/watson-knowledge-studio/preannotation.html)。

## 2017 年 12 月
{: #december2017}

### 新增特性及變更
{: #new-december2017}

- {{site.data.keyword.knowledgestudioshort}} 在 {{site.data.keyword.cloud_notm}} 上啟動。如需移轉程序與時間表的相關資訊，請參閱[移轉至 {{site.data.keyword.cloud_notm}}](/docs/services/watson-knowledge-studio/client-migration.html)。
- 重新設計的導覽。如需導覽變更的詳細資料，請參閱 2017 年 9 月版本注意事項中的[表 2](#september2017)。
- 已新增 {{site.data.keyword.nlufull}} 作為預先註釋程式。
- 已將使用者及儲存空間管理設定新增至「服務詳細資料」頁面。如需新增使用者的相關資訊，請參閱[組合團隊](/docs/services/watson-knowledge-studio/team.html)。如需設定儲存空間限制的相關資訊，請參閱[疑難排解 > 儲存空間問題](/docs/services/watson-knowledge-studio/troubleshooting.html#storage)。
- 已新增「效能」頁面，用作模型品質評估及如何改善品質的相關指引。

## 2017 年 11 月
{: #november2017}

### 變更
{: #new-november2017}

- 已修正下載語料庫中遺漏部分關係註釋的問題。
- 已修正無法從部署中撤銷模型的問題（如果其狀態為**無**）。
- 已修正韓文版本無法評估模型的問題。

## 2017 年 10 月
{: #october2017}

### 變更
{: #new-october2017}

- 已修正必須等到您重新整理 {{site.data.keyword.Bluemix_notm}} [實驗性](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)版本的瀏覽器視窗才會啟用**匯出**按鈕的問題。
- 已修正按鈕標籤及工具提示，以符合 {{site.data.keyword.Bluemix_notm}}
[實驗性](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)版本中的_上傳_ 及_下載_ 詞彙的變更。參照類型系統、文件及字典時，會使用這些詞彙，而非_匯入_ 及_匯出_。
- 已修正在 {{site.data.keyword.Bluemix_notm}} [實驗性](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)版本的「{{site.data.keyword.knowledgestudioshort}} 使用者帳戶管理」頁面上更新說明的延遲問題。
- 在介面的預先註釋區段中，進行了數個 GUI 變更，以釐清機器學習模型、規則型模型、字典及 {{site.data.keyword.alchemylanguagefull}}
的功能。已將按鈕標籤從**執行**變更為**預先註釋**，將視窗的標題從**執行註釋程式**變更為**執行預先註釋**，並且變更錯誤訊息以釐清在人工註釋文件之後您無法新增自動化註釋。
- 對於使用字典型記號器的專案或工作區，如果您匯入文件但無基準，請修正顯示空白句子的問題。

## 2017 年 9 月
{: #september2017}

### 新增特性及變更
{: #new-sept17}

- 已發行作為[實驗性](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)服務的 {{site.data.keyword.Bluemix}} 上 {{site.data.keyword.knowledgestudioshort}}
的新前端使用者體驗。變更包括重組導覽及新的模型效能分析頁面。如需導覽變更的摘要，請參閱已知問題中的表格。
- 已新增中文（簡體）及荷蘭文語言支援。

### 已知問題
{: #issues-sept17}

- 對於規則型模型，在您對映類別和實體類型之後，必須等到您重新整理瀏覽器視窗，才會啟用**匯出**按鈕。
- 對於 {{site.data.keyword.Bluemix_notm}} [實驗性](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)版本，部分文件術語不符合新的介面。文件符合 {{site.data.keyword.IBM_notm}} Marketplace 中的介面。[實驗性](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)版本中的下列詞彙已變更：

|{{site.data.keyword.IBM_notm}} Marketplace 中的詞彙|{{site.data.keyword.Bluemix_notm}} 中的詞彙|附註|
|----------|----------|----------|
|_專案_ |_工作區_ |此詞彙已變更，因為 {{site.data.keyword.Bluemix_notm}} 也使用_專案_ 一詞|
|_匯入_ 及_匯出_ |_上傳_ 及_下載_ |用於文件及實體類型的詞彙中時，詞彙_匯入_ 及_匯出_ 現在稱為_上傳_ 及_下載_。若是指將模型匯出至應用程式（例如
{{site.data.keyword.watson}} 瀏覽器）時，仍使用_匯出_ 一詞。|
{: caption="表 1. {{site.data.keyword.Bluemix_notm}} 版本的術語變更" caption-side="top"}

- 對於 {{site.data.keyword.Bluemix_notm}} [實驗性](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)版本，部分文件作業步驟不符合新的介面。文件符合 {{site.data.keyword.IBM_notm}} Marketplace 中的介面。下表彙總[實驗性](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)版本的導覽變更：

|特性|{{site.data.keyword.IBM_notm}} Marketplace 位置|{{site.data.keyword.Bluemix_notm}} 位置
|----------|----------|----------|
|「註釋程式元件」標籤|主要導覽|已不存在|
|混淆矩陣表格（「統計資料」標籤中）|註釋程式元件 > 詳細資料|模型管理 > 效能 > 詳細統計資料鏈結|
|「字典」標籤|主要導覽|資產及工具 > 預先註釋程式|
|「字典對映」頁面|註釋程式元件|資產及工具 > 預先註釋程式|
|「實體類型」標籤|類型系統|資產及工具 > 實體類型|
|基準編輯器|人工註釋|「文件註釋」標籤|
|「基準編輯器設定」標籤|人工註釋|設定 > 文件註釋設定|
|模型、執行及匯出|註釋程式元件|模型管理 > 版本|
|「規則」標籤|主要導覽|文件註釋 > 規則|
|「統計資料」標籤|註釋程式元件 > 詳細資料|模型管理 > 效能|
|摘要表格（「統計資料」標籤中）|註釋程式元件 > 詳細資料|模型管理 > 效能 > 詳細統計資料鏈結|
|「類型對映」標籤（用於規則型模型）|註釋程式元件 > 詳細資料|模型管理 > 版本 > 規則型模型類型對映|
{: caption="表 2. {{site.data.keyword.Bluemix_notm}} 版本的導覽變更" caption-side="top"}

## 2017 年 7 月
{: #july2017}

- 已修正在某些情況下會造成標頭消失的問題報告
- 已套用基礎架構元件的安全更新項目

## 2017 年 6 月
{: #june2017}

- 已改善在特定狀況下處理大量資料的穩定性
- 已修正裁定錯誤的問題報告

## 2017 年 5 月
{: #may2017}

- 已新增重新命名各種物件（例如專案、文件集等）的能力
- 已新增將 NLU 模型部署至特定 {{site.data.keyword.Bluemix}} 地區的能力
- 已改善顯示大型 IAA 表格的效能
- 已修正次要問題報告
- 已套用安全修正程式

## 2017 年 4 月
{: #april2017}

- 已改善 {{site.data.keyword.knowledgestudioshort}} 超值方案的穩定性
- 已新增商業度量值的使用分析

## 2017 年 4 月之前的版本

請參閱 [{{site.data.keyword.IBM_notm}} TechNotes #1986001
![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://www.ibm.com/support/docview.wss?uid=swg21986001){: new_window}。
