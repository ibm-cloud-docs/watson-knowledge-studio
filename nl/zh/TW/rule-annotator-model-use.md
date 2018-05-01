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

此文件適用於 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}。若要查看舊版 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 的文件，[請按一下此鏈結 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/docs/services/knowledge-studio/rule-annotator-model-use.html){: new_window}。
{: tip}

# 使用規則型模型
{: #wks_rule_publish}

運用您以 {{site.data.keyword.knowledgestudioshort}} 建立的規則型模型，讓它可用於其他 {{site.data.keyword.watson}} 應用程式。
{: shortdesc}

**注意**：您可以部署規則型模型，讓它可在這些服務中當作[實驗性](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)功能來使用。

您必須先訂閱服務，才能部署模型以供服務使用。{{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} 服務在 {{site.data.keyword.Bluemix_notm}}（{{site.data.keyword.IBM_notm}} 的雲端平台）進行管理。如需平台的相關資訊，請參閱[何謂 {{site.data.keyword.Bluemix_notm}}？ ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.ng.bluemix.net/docs/overview/whatisbluemix.html){: new_window}。若要訂閱其中一項 {{site.data.keyword.IBM_notm}}{{site.data.keyword.watson}} 服務，請從 [{{site.data.keyword.Bluemix_notm}} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.ng.bluemix.net/){: new_window} 網站建立一個帳戶。

對於某些服務，您必須知道計劃部署到其中的服務實例的相關詳細資料，例如 {{site.data.keyword.Bluemix_notm}} 空間名稱和服務實例名稱。空間和實例名稱資訊可從 {{site.data.keyword.Bluemix_notm}} 服務頁面取得。

您也可以使用規則型模型來預先註釋新文件。如需詳細資料，請參閱[使用規則型模型預先註釋文件](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotrule)。

## 將規則型模型部署至 AlchemyLanguage
{: #wks_rule_bluemix}

此特性可讓您的應用程式使用已部署的規則型模型，從領域中的文件尋找及擷取實體。

**注意**：目前這是服務的[實驗性](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)特性。

### 開始之前

您必須具有 {{site.data.keyword.alchemylanguageshort}} 服務的「進階」方案，才能使用此自訂模型。

### 關於本作業

若要部署至此服務，您必須具有
{{site.data.keyword.IBM_notm}}{{site.data.keyword.alchemylanguageshort}} 的存取金鑰。

此金鑰必須屬於已獲授權發佈自訂模型的帳戶，或將順利部署的模型，但您無法使用它。

部署規則型模型時，您可以選取要部署的版本。您必須在第一次將模型部署至 {{site.data.keyword.alchemylanguageshort}} 時，指定此金鑰。然後，您才能重複使用此金鑰與所部署之模型的多個版本搭配。每一個金鑰都會限制可同時部署的模型數目上限。

### 程序

若要將規則型模型部署至 {{site.data.keyword.alchemylanguageshort}}，請執行下列動作：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理者或專案經理身分登入，並選取您的工作區。
1. 選取**模型管理** > **版本** > **規則型**標籤。
1. 選擇您要部署的模型版本。

    如果模型只有一個工作版本，請按一下**儲存以進行部署**來儲存現行模型以進行部署。按一下**儲存以進行部署**會建立一個模型版本，讓您可以在部署某個版本的同時繼續改善現行版本。儲存版本可能需要一些時間。除非已建立版本，否則不會出現部署選項。

1. 按一下**部署**，選擇將其部署至 {{site.data.keyword.alchemylanguageshort}}，然後按**下一步**。
1. 輸入您從 {{site.data.keyword.alchemylanguageshort}} 取得的金鑰，或選取先前所部署的模型版本（該模型具有您要重複使用的金鑰），然後按一下**部署**。如果該金鑰有效，即會顯示一個包含模型
ID 的確認。這項確認並不表示模型已備妥可供應用程式使用。
1. 部署程序可能需要一些時間。若要檢查部署的狀態，請按一下已部署版本旁的**狀態**。如果模型仍在進行部署，則狀態會指出「發佈中」。部署完成之後，如果部署成功，則狀態會變更為「可用」；如果發生問題，則狀態會變更為「錯誤」。

    狀態資訊包括模型 ID 、{{site.data.keyword.alchemyapishort}} 金鑰的最後四個數字，以及部署程序的日誌。模型 ID (model_id)
是應用程式呼叫機器學習模型的方式。請記下這個模型 ID，因為之後沒有程式化方式可存取它。請使用 {{site.data.keyword.alchemyapishort}} 金鑰來追蹤每個金鑰的部署次數。

### 下一步

若要使用已部署的模型，您必須複製模型 ID 並將其貼入應用程式的 API 呼叫。

> **注意：**您無法使用 `GET /info/models` {{site.data.keyword.alchemylanguageshort}} API 呼叫，以程式設計方式取得規則型模型的模型 ID。您可以使用此呼叫來存取機器學習模型的模型 ID，但不能存取規則型模型 ID。

該呼叫還必須指定您要與模型及 {{site.data.keyword.alchemyapishort}} 存取金鑰搭配使用的 {{site.data.keyword.alchemylanguageshort}} 服務。

下列是支援的端點：

- **&lt;*input-type*&gt;GetRankedNamedEntities**

    使用您在模型參數中指定的自訂模型，以擷取它在所提供輸入中找到的所有已知實體類型的提及項目清單。支援的輸入類型包括文字、HTML 或公用 URL。如需 API 及要使用之語法的相關資訊，請參閱 [{{site.data.keyword.alchemylanguageshort}}&gt;實體 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/smarterplanet/us/en/ibmwatson/developercloud/alchemy-language/api/v1/#entities){: new_window}。

## 將規則型模型部署至 IBM Watson Discovery
{: #wks_rule_discovery}

部署模型，讓使用 {{site.data.keyword.discoveryshort}} 服務的應用程式可以使用規則型模型，在文件強化期間尋找及擷取實體。

**注意**：目前這是服務的[實驗性](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)特性。

### 開始之前

您必須具有 {{site.data.keyword.watson}}{{site.data.keyword.discoveryshort}} 服務實例的管理存取權，且知道與它相關聯的
{{site.data.keyword.Bluemix_notm}} 空間及實例名稱。

### 程序

若要將規則型模型部署至 {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}，請完成下列步驟：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理者或專案經理身分登入，並選取您的工作區。
1. 選取**模型管理** > **版本** > **規則型**標籤。
1. 選擇您要部署的模型版本。

    如果模型只有一個工作版本，請按一下**儲存以進行部署**來儲存現行模型以進行部署。這會版本化模型（其可讓您部署一個版本），同時您可以繼續改善現行版本。儲存版本可能需要一些時間。除非已建立版本，否則不會出現部署選項。

1. 按一下**部署**，選擇將其部署至 {{site.data.keyword.discoveryshort}}，然後按**下一步**。
1. 提供 {{site.data.keyword.Bluemix_notm}} 空間及實例。必要的話，請選取不同的地區。
1. 按一下**部署**。
1. 部署程序可能需要一些時間。若要檢查部署的狀態，請按一下已部署版本旁的**版本**標籤上的**狀態**。

    如果模型仍在進行部署，則狀態會指出「發佈中」。部署完成之後，如果部署成功，則狀態會變更為「可用」；如果發生問題，則狀態會變更為「錯誤」。

    一旦可用之後，請記下模型 ID (model_id)。您會將此 ID 提供給 {{site.data.keyword.discoveryshort}} 服務，以讓服務使用您的自訂模型。

### 下一步

若要使用已部署的模型，您必須在 {{site.data.keyword.discoveryshort}}
服務強化配置程序期間要求模型 ID 時予以提供。

## 將規則型模型部署至 IBM Watson Natural Language Understanding
{: #wks_rule_nlu}

部署規則型模型，讓使用 {{site.data.keyword.nlushort}} 服務的應用程式可以使用此模型，來尋找及擷取與您領域相關的實體。

**注意**：目前這是服務的[實驗性](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)特性。

### 開始之前

您必須具有 {{site.data.keyword.nlushort}} 服務實例的管理存取權，且知道與它相關聯的 {{site.data.keyword.Bluemix_notm}} 空間及實例名稱。

### 程序

若要將規則型模型部署至 {{site.data.keyword.nlushort}}，請完成下列步驟：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理者或專案經理身分登入，並選取您的工作區。
1. 選取**模型管理** > **版本** > **規則型**標籤。
1. 選擇您要部署的模型版本。

    如果模型只有一個工作版本，請按一下**儲存以進行部署**來儲存現行模型以進行部署。這會版本化模型（其可讓您部署一個版本），同時您可以繼續改善現行版本。儲存版本可能需要一些時間。除非已建立版本，否則不會出現部署選項。

1. 按一下**部署**，選擇將其部署至 {{site.data.keyword.nlushort}}，然後按**下一步**。
1. 提供 {{site.data.keyword.Bluemix_notm}} 空間及實例。必要的話，請選取不同的地區。
1. 按一下**部署**。
1. 部署程序可能需要一些時間。若要檢查部署的狀態，請按一下已部署版本旁的**版本**標籤上的**狀態**。

    如果模型仍在進行部署，則狀態會指出「發佈中」。部署完成之後，如果部署成功，則狀態會變更為「可用」；如果發生問題，則狀態會變更為「錯誤」。

    一旦可用之後，請記下模型 ID (model_id)。您會將此 ID 提供給 {{site.data.keyword.nlushort}} 服務，以讓服務使用您的自訂模型。

### 下一步

若要使用已部署的模型，您必須在 `entities.model` 參數中指定自訂模型的模型 ID。

您可以使用此模型與 {{site.data.keyword.nlushort}} `GET /analyze` 要求搭配，來擷取實體。

如需詳細資料，請參閱
[{{site.data.keyword.nlushort}}
文件 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/watson/developercloud/doc/natural-language-understanding/index.html){: new_window}。

## 取消部署模型
{: #undeploy-view-model}

如果您要取消部署模型或尋找模型 ID，請檢視**已部署的模型**頁面。**已部署的模型**頁面會顯示已部署至您有權存取之空間中服務的所有 {{site.data.keyword.knowledgestudioshort}} 模型。

若要取消部署模型或尋找模型 ID，請執行下列動作：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理者或專案經理身分登入，並選取您的工作區。
1. 從右上角功能表列的**設定**功能表中，選取**管理已部署的模型**。
1. 從已部署的模型清單中，尋找您要檢視或取消部署的模型。
1. 若要取消部署模型，請從該列的最後一個直欄中，按一下**取消部署模型**。
1. 若要尋找模型 ID，請參閱**模型 ID** 直欄。

## 在 IBM Watson Explorer 中運用規則型模型
{: #wks_rule_export}

匯出建立規則型模型時所產生的 PEAR 檔，以在 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer 中使用它。

### 程序

若要在 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer 中運用規則型模型，請完成下列步驟：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理者或專案經理身分登入，並選取您的工作區。
1. 選取**模型管理** > **版本** > **規則型**標籤。
1. 按一下**匯出現行模型**。

    如果您使用免費訂閱方案，則沒有匯出選項可供使用。

    此模型會儲存為 PEAR 檔，系統會提示您下載該檔案。PEAR（處理引擎保存檔）檔是 UIMA 元件的 UIMA 標準包裝格式。此模型是以 PEAR 格式儲存，因此可以分散在 UIMA 應用程式內並且重複使用。

1. 將檔案下載至本端系統。
1. 從 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer 應用程式中，匯入 PEAR 檔。
