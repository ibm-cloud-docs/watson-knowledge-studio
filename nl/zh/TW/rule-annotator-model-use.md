---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-14"

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

此文件適用於 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}。若要查看舊版 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 的文件，[請按一下此鏈結 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/docs/services/knowledge-studio/rule-annotator-model-use.html){: new_window}。
{: tip}

# 使用規則型模型
{: #wks_rule_publish}

運用您以 {{site.data.keyword.knowledgestudioshort}} 建立的規則型模型，讓它可用於其他 {{site.data.keyword.watson}} 應用程式。
{: shortdesc}

**注意**：您可以部署規則型模型，讓它可在這些服務中當作[實驗性](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)功能來使用。

您必須先訂閱服務，才能部署模型以供服務使用。{{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} 服務在 {{site.data.keyword.Bluemix_notm}}（{{site.data.keyword.IBM_notm}} 的雲端平台）進行管理。請參閱[何謂 {{site.data.keyword.Bluemix_notm}}？ ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.ng.bluemix.net/docs/overview/whatisbluemix.html){: new_window}，以取得平台的相關資訊。若要訂閱其中一項 {{site.data.keyword.IBM_notm}}{{site.data.keyword.watson}} 服務，請從 [{{site.data.keyword.Bluemix_notm}} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.ng.bluemix.net/){: new_window} 網站建立一個帳戶。

對於某些服務，您必須知道計劃部署到其中的服務實例的相關詳細資料，例如 {{site.data.keyword.Bluemix_notm}} 空間名稱和服務實例名稱。空間和實例名稱資訊可從 {{site.data.keyword.Bluemix_notm}} 服務頁面取得。

您也可以使用規則型模型來預先註釋新文件。如需詳細資料，請參閱[使用規則型模型預先註釋文件](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotrule)。

## 將規則型模型部署至 IBM Watson Discovery
{: #wks_rule_discovery}

部署模型，讓使用 {{site.data.keyword.discoveryshort}} 服務的應用程式可以使用規則型模型，在文件強化期間尋找及擷取實體。

**注意**：目前這是服務的[實驗性](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)特性。

### 開始之前
{: #wks_rule_discovery_prereqs}

您必須具有 {{site.data.keyword.watson}}{{site.data.keyword.discoveryshort}} 服務實例的管理存取權，且知道與它相關聯的
{{site.data.keyword.Bluemix_notm}} 空間及實例名稱。

### 程序
{: #wks_rule_discovery_procedure}

若要將規則型模型部署至 {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}，請完成下列步驟：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理者或專案經理身分登入，並選取您的工作區。
1. 選取**規則型模型** > **版本** > **規則型模型**標籤。
1. 選擇您要部署的模型版本。

    如果模型只有一個工作版本，請按一下**儲存以進行部署**來儲存現行模型以進行部署。這會版本化模型（其可讓您部署一個版本），同時您可以繼續改善現行版本。儲存版本可能需要一些時間。除非已建立版本，否則不會出現部署選項。

    **附註**：每一個版本只能部署至一個服務實例。如果您要將相同的模型部署至多個實例，請為每一個實例建立一個版本。

1. 按一下**部署**，選擇將其部署至 {{site.data.keyword.discoveryshort}}，然後按**下一步**。
1. 提供 {{site.data.keyword.Bluemix_notm}} 空間及實例。必要的話，請選取不同的地區。
1. 按一下**部署**。
1. 部署程序可能需要一些時間。若要檢查部署的狀態，請按一下已部署版本旁的**版本**標籤上的**狀態**。

    如果模型仍在進行部署，則狀態會指出「發佈中」。部署完成之後，如果部署成功，則狀態會變更為「可用」；如果發生問題，則狀態會變更為「錯誤」。

    一旦可用之後，請記下模型 ID (model_id)。您會將此 ID 提供給 {{site.data.keyword.discoveryshort}} 服務，以讓服務使用您的自訂模型。

### 下一步
{: #wks_rule_discovery_next}

若要使用已部署的模型，您必須在 {{site.data.keyword.discoveryshort}}
服務強化配置程序期間要求模型 ID 時予以提供。

## 將規則型模型部署至 IBM Watson Natural Language Understanding
{: #wks_rule_nlu}

部署規則型模型，讓使用 {{site.data.keyword.nlushort}} 服務的應用程式可以使用此模型，來尋找及擷取與您領域相關的實體。

**注意**：目前這是服務的[實驗性](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)特性。

### 開始之前
{: #wks_rule_prereqs}

您必須具有 {{site.data.keyword.nlushort}} 服務實例的管理存取權，且知道與它相關聯的 {{site.data.keyword.Bluemix_notm}} 空間及實例名稱。

### 程序
{: #wks_rule_procedure}

若要將規則型模型部署至 {{site.data.keyword.nlushort}}，請完成下列步驟：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理者或專案經理身分登入，並選取您的工作區。
1. 選取**規則型模型** > **版本** > **規則型模型**標籤。
1. 選擇您要部署的模型版本。

    如果模型只有一個工作版本，請按一下**儲存以進行部署**來儲存現行模型以進行部署。這會版本化模型（其可讓您部署一個版本），同時您可以繼續改善現行版本。儲存版本可能需要一些時間。除非已建立版本，否則不會出現部署選項。

    **附註**：每一個版本只能部署至一個服務實例。如果您要將相同的模型部署至多個實例，請為每一個實例建立一個版本。

1. 按一下**部署**，選擇將其部署至 {{site.data.keyword.nlushort}}，然後按**下一步**。
1. 提供 {{site.data.keyword.Bluemix_notm}} 空間及實例。必要的話，請選取不同的地區。
1. 按一下**部署**。
1. 部署程序可能需要一些時間。若要檢查部署的狀態，請按一下已部署版本旁的**版本**標籤上的**狀態**。

    如果模型仍在進行部署，則狀態會指出「發佈中」。部署完成之後，如果部署成功，則狀態會變更為「可用」；如果發生問題，則狀態會變更為「錯誤」。

    一旦可用之後，請記下模型 ID (model_id)。您會將此 ID 提供給 {{site.data.keyword.nlushort}} 服務，以讓服務使用您的自訂模型。

### 下一步
{: #wks_rule_next}

若要使用已部署的模型，您必須在 `entities.model` 參數中指定自訂模型的模型 ID。

您可以使用此模型與 {{site.data.keyword.nlushort}} `GET /analyze` 要求搭配，來擷取實體。

如需詳細資料，請參閱 [{{site.data.keyword.nlushort}} 文件 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/docs/services/natural-language-understanding/index.html){: new_window}。

## 取消部署模型
{: #undeploy-view-model}

如果您要取消部署模型或尋找模型 ID，請檢視**已部署的模型**頁面。

### 關於本作業
{: #wks_undeploy_about}

您在「已部署的模型」頁面上看到的內容，取決於管理 {{site.data.keyword.knowledgestudioshort}} 實例的[地區 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/docs/resources/services_region.html){: new_window}。如果地區支援 [IAM ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/docs/iam/users_roles.html){: new_window} 及 [Cloud Foundry ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/docs/iam/cfaccess.html){: new_window} 存取管理方法所管理的實例，您會看到每個方法的標籤。來自 IAM 所管理之實例的模型會列示在**資源群組**標籤上。來自 Cloud Foundry 所管理之實例的模型則會列示在**組織**標籤上。

如果地區支援僅由其中一種存取管理方法管理的實例，則您只會看到一個模型清單，因為只有一個存取管理方法適用。

### 程序
{: #wks_deploy_procedure}

若要取消部署模型或尋找模型 ID，請執行下列動作：

1. 啟動 {{site.data.keyword.knowledgestudioshort}}。
1. 從右上角功能表列的**設定**功能表中，選取**管理已部署的模型**。
1. 從已部署的模型清單中，尋找您要檢視或取消部署的模型。
1. 若要取消部署模型，請從該列的最後一個直欄中，按一下**取消部署模型**。
1. 若要尋找模型 ID，請參閱**模型 ID** 直欄。

或者，您也可以從規則型模型及機器學習模型的「版本」頁面中取消部署模型。

## 在 IBM Watson Explorer 中運用規則型模型
{: #wks_rule_export}

匯出建立規則型模型時所產生的 PEAR 檔，以在 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer 中使用它。

### 程序
{: #wks_rule_export_procedure}

若要在 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer 中運用規則型模型，請完成下列步驟：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理者或專案經理身分登入，並選取您的工作區。
1. 選取**規則型模型** > **版本** > **規則型模型**標籤。
1. 按一下**匯出現行模型**。

    如果您有「精簡」訂閱方案，則沒有可用的匯出選項。

    此模型會儲存為 PEAR 檔，系統會提示您下載該檔案。PEAR（處理引擎保存檔）檔是 UIMA 元件的 UIMA 標準包裝格式。此模型是以 PEAR 格式儲存，因此可以分散在 UIMA 應用程式內並且重複使用。

1. 將檔案下載至本端系統。
1. 從 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer 應用程式中，匯入 PEAR 檔。
