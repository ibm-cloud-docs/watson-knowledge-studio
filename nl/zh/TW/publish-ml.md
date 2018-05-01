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

此文件適用於 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}。若要查看舊版 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 的文件，[請按一下此鏈結 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/docs/services/knowledge-studio/publish-ml.html){: new_window}。
{: tip}

# 使用機器學習模型
{: #publish-ml}

運用您以 {{site.data.keyword.knowledgestudioshort}} 訓練的機器學習模型，讓它可用於其他 {{site.data.keyword.watson}} 應用程式。
{: shortdesc}

您可以部署或匯出機器學習模型。字典或 {{site.data.keyword.nlushort}} 預先註釋程式只能用來在 {{site.data.keyword.knowledgestudioshort}} 內預先註釋文件。

您必須先訂閱服務，才能部署模型以供服務使用。{{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} 服務在 {{site.data.keyword.Bluemix_short}}（{{site.data.keyword.IBM_notm}} 的雲端平台）進行管理。請參閱[何謂 {{site.data.keyword.Bluemix_notm}}？ ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.ng.bluemix.net/docs/overview/whatisbluemix.html){: new_window}，以取得平台的相關資訊。若要訂閱其中一項 {{site.data.keyword.IBM_notm}}{{site.data.keyword.watson}} 服務，請從 [{{site.data.keyword.Bluemix_notm}} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.ng.bluemix.net/){: new_window} 網站建立一個帳戶。

對於某些服務，您必須知道計劃部署到其中的服務實例的相關詳細資料，例如 {{site.data.keyword.Bluemix_notm}} 空間名稱和服務實例名稱。空間和實例名稱資訊可從 {{site.data.keyword.Bluemix_notm}} 服務頁面取得。

您也可以使用機器學習模型來預先註釋新文件。如需詳細資料，請參閱[使用機器學習模型預先註釋文件](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotsire)。

## 將機器學習模型部署至 AlchemyLanguage
{: #wks_mabluemix}

當此模型的效能符合您的要求時，您可以將這個版本部署至 {{site.data.keyword.IBM_notm}} {{site.data.keyword.alchemylanguageshort}}。此特性（需要您提供 {{site.data.keyword.alchemyapishort}} 存取金鑰）可讓您的應用程式使用已部署的機器學習模型來註釋您領域中的文件。

### 開始之前

您必須具有 {{site.data.keyword.alchemylanguageshort}} 服務的「進階」方案，才能部署及使用模型。
>附註：{{site.data.keyword.alchemylanguageshort}} 服務已被淘汰。您無法將此模型部署至服務，除非您具有現有方案。

### 關於本作業

部署機器學習模型時，您可以選取要部署的版本。若要部署至此服務，您必須具有 {{site.data.keyword.IBM_notm}}{{site.data.keyword.alchemylanguageshort}} 的存取金鑰。

此金鑰必須屬於已獲授權發佈自訂模型的帳戶，或將順利部署的模型，但您無法使用它。

您必須在第一次將模型部署至 {{site.data.keyword.alchemylanguageshort}} 時，指定此金鑰。然後，您才能重複使用此金鑰與所部署之模型的多個版本搭配。每一個金鑰都會限制可同時部署的模型數目上限。

### 程序

若要將機器學習模型部署至 {{site.data.keyword.alchemylanguageshort}}，請執行下列動作：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理者或專案經理身分登入，並選取您的工作區。
1. 選取**模型管理** > **版本** > **機器學習**標籤。
1. 選擇您要部署的模型版本。

    如果模型只有一個工作版本，請建立現行模型的 Snapshot。這會版本化模型（其可讓您部署一個版本），同時您可以繼續改善現行版本。除非您至少建立一個版本，否則不會出現部署選項。

1. 按一下**部署**，選擇將其部署至 {{site.data.keyword.alchemylanguageshort}} 服務，然後按**下一步**。
1. 輸入您從 {{site.data.keyword.alchemylanguageshort}} 取得的金鑰，或選取先前所部署的模型版本（該模型具有您要重複使用的金鑰），然後按一下**部署**。如果該金鑰有效，即會顯示一個包含模型 ID 的確認。這項確認並不表示模型已備妥可供應用程式使用。
1. 部署程序可能需要一些時間。若要檢查部署的狀態，請按一下已部署版本旁的**狀態**。如果模型仍在進行部署，則狀態會指出「發佈中」。部署完成之後，如果部署成功，則狀態會變更為「可用」；如果發生問題，則狀態會變更為「錯誤」。

    狀態資訊包括模型 ID 、{{site.data.keyword.alchemyapishort}} 金鑰的最後四個數字，以及部署程序的日誌。模型 ID (model_id) 是應用程式呼叫機器學習模型的方式。請使用 {{site.data.keyword.alchemyapishort}} 金鑰來追蹤每個金鑰的部署次數。

### 下一步

若要使用已部署的模型，您必須複製模型 ID 並將其貼入應用程式的 API 呼叫。該呼叫還必須指定您要與模型及其相關 {{site.data.keyword.alchemyapishort}} 存取金鑰搭配使用的 {{site.data.keyword.alchemylanguageshort}} 進階方案服務。以下是支援的端點：

- **&lt;*input-type*&gt;GetRankedNamedEntities**

    使用您在模型參數中指定的自訂模型，以擷取它在所提供輸入中找到的所有已知實體類型的提及項目清單。支援的輸入類型包括文字、HTML 或公用 URL。如需 API 及要使用之語法的相關資訊，請參閱 [{{site.data.keyword.alchemylanguageshort}}&gt;實體 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/smarterplanet/us/en/ibmwatson/developercloud/alchemy-language/api/v1/#entities){: new_window}。

- **&lt;*input-type*&gt;GetTypedRelations**

    使用您在模型參數中指定的自訂模型，來擷取它在所提供輸入中找到的已知關係的實例清單。如需 API 及要使用之語法的相關資訊，請參閱 [{{site.data.keyword.alchemylanguageshort}}&gt;TypedRelations ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/smarterplanet/us/en/ibmwatson/developercloud/alchemy-language/api/v1/#typed-relations){: new_window}。

#### 範例

- 下列 API 呼叫會在傳入 POST 內文的字串中尋找已知的實體類型。此要求指定所建立的模型 ID，以及有權執行自訂模型的 Alchemy API 金鑰。

    ```bash
    curl -d 'text=Mary had a little lamb.'
    "https://gateway-a.watsonplatform.net/calls/text/TextGetRankedNamedEntities?
    showSourceText=1&
    model=44476a63-c55t-451f-ad3r-8b23c0f4628c&
    apikey=s3wee88r25wwe2p6442w99g8t77phll5323kkf3a&
    outputMode=json"
    ```
    {: pre}

    如果那些是您的機器學習模型所辨識的提及項目，則回應會傳回 `Mary` 和 `lamb`。

- 下列 API 呼叫會在傳入 POST 內文的字串中尋找已知的關係。此要求指定所建立的模型 ID，以及有權執行自訂模型的 Alchemy API 金鑰。

    ```bash
    curl -d 'text=Mary had a little lamb.'
    "https://gateway-a.watsonplatform.net/calls/text/TextGetTypedRelations?
    showSourceText=1&
    model=44476a63-c55t-451f-ad3r-8b23c0f4628c&
    apikey=s3wee88r25wwe2p6442w99g8t77phll5323kkf3a&
    outputMode=json"
    ```
    {: pre}

    如果您的機器學習模型可辨識該關係，則回應會傳回 `ownedBy`。

> **附註：**包括換行字元，可讓您更適當地格式化畫面的範例。不要在 API 語法中包括換行字元。

如需相關資訊，請參閱 [{{site.data.keyword.alchemylanguageshort}} 文件 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/watson/developercloud/doc/alchemylanguage/customizing.shtml){: new_window}。

#### 相關資訊

[{{site.data.keyword.alchemylanguageshort}} 模型問題](/docs/services/watson-knowledge-studio/troubleshooting.html#wks_ts_deployed_model_deleted)

## 將機器學習模型部署至 IBM Watson Discovery
{: #wks_madiscovery}

當此模型的效能符合您的要求時，您可以將這個版本部署至 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}。此特性可讓您的應用程式使用已部署的機器學習模型，來強化從資料取得的見解，以包括與您領域相關的概念及關係的識別。

### 開始之前

您必須具有 {{site.data.keyword.watson}}{{site.data.keyword.discoveryshort}} 服務實例的管理存取權，且知道與它相關聯的 {{site.data.keyword.Bluemix_notm}} 空間及實例名稱。

### 關於本作業

部署機器學習模型時，您可以選取要部署的版本。

### 程序

若要將機器學習模型部署至 {{site.data.keyword.watson}}{{site.data.keyword.discoveryshort}}，請完成下列步驟：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理者或專案經理身分登入，並選取您的工作區。
1. 選取**模型管理** > **版本** > **機器學習**標籤。
1. 選擇您要部署的模型版本。

    如果模型只有一個工作版本，請建立現行模型的 Snapshot。這會版本化模型（其可讓您部署一個版本），同時您可以繼續改善現行版本。除非您至少建立一個版本，否則不會出現部署選項。

1. 按一下**部署**，選擇將其部署至 {{site.data.keyword.discoveryshort}}，然後按**下一步**。
1. 選取 {{site.data.keyword.Bluemix_notm}} 空間及實例。必要的話，請選取不同的地區。
1. 按一下**部署**。
1. 部署程序可能需要一些時間。若要檢查部署的狀態，請按一下已部署版本旁的**版本**標籤上的**狀態**。

    如果模型仍在進行部署，則狀態會指出「發佈中」。部署完成之後，如果部署成功，則狀態會變更為「可用」；如果發生問題，則狀態會變更為「錯誤」。

    一旦可用之後，請記下模型 ID (model_id)。您會將此 ID 提供給 {{site.data.keyword.discoveryshort}} 服務，以讓服務使用您的自訂模型。

### 下一步

若要使用已部署的模型，您必須在 {{site.data.keyword.discoveryshort}} 服務強化配置程序期間要求模型 ID 時予以提供。如需詳細資料，請參閱 [{{site.data.keyword.discoveryshort}} 服務文件 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://www.ibm.com/watson/developercloud/doc/discovery/integrate-wks.shtml){: new_window}。

## 將機器學習模型部署至 IBM Watson Natural Language Understanding
{: #wks_manlu}

當此模型的效能符合您的要求時，您可以將這個版本部署至 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.nlushort}}。此特性可讓您的應用程式使用已部署的機器學習模型，來分析文字輸入的語意特性，包括實體及關係。

### 開始之前

您必須具有要部署至其中的 {{site.data.keyword.nlushort}} 服務。而且您必須知道與服務相關聯的 {{site.data.keyword.Bluemix_notm}} 空間及實例名稱。如果您不記得空間或實例名稱，請登入 {{site.data.keyword.Bluemix_notm}} 來尋找它們。如果您沒有 {{site.data.keyword.Bluemix_notm}} 帳戶，請註冊申請一個帳戶。

### 關於本作業

部署機器學習模型時，您可以選取要部署的版本。

### 程序

若要將機器學習模型部署至 {{site.data.keyword.nlushort}} 服務，請完成下列步驟：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理者或專案經理身分登入，並選取您的工作區。
1. 選取**模型管理** > **版本** > **機器學習**標籤。
1. 選擇您要部署的模型版本。

    如果模型只有一個工作版本，請建立現行模型的 Snapshot。這會版本化模型（其可讓您部署一個版本），同時您可以繼續改善現行版本。除非您至少建立一個版本，否則不會出現部署選項。

1. 按一下**部署**，選擇將其部署至 {{site.data.keyword.nlushort}}，然後按**下一步**。
1. 選取 {{site.data.keyword.Bluemix_notm}} 空間及實例。必要的話，請選取不同的地區。
1. 按一下**部署**。
1. 部署程序可能需要一些時間。若要檢查部署的狀態，請按一下已部署版本旁的**版本**標籤上的**狀態**。如果模型仍在進行部署，則狀態會指出「發佈中」。部署完成之後，如果部署成功，則狀態會變更為「可用」；如果發生問題，則狀態會變更為「錯誤」。

    一旦可用之後，請記下模型 ID (model_id)。您會將此 ID 提供給 {{site.data.keyword.nlushort}} 服務，以讓服務使用您的自訂模型。

### 下一步

若要使用已部署的模型，您必須在 `entities.model` 參數中指定自訂模型的模型 ID。

您可以使用此模型與 {{site.data.keyword.nlushort}} `GET /analyze` 要求搭配，以擷取下列特性：

- **實體**

    下列指令會尋找使用 text 參數傳遞之句子中存在的實體：

    ```bash
    curl -G -u "3330af09-4b22-4f2d-a54c-1cb099df1fa8":"338rTJSvPVqeG"
    -d "version=2016-05-17"
    -d "text=Vehicle%201%2C%20a%201995%20Honda%20Civic%20was%20traveling%20north
    %20on%20a%20two%20lane%20undivided%20roadway%2C%20negotiating%20a%20curve%20to
    %20the%20left%20on%20an%20upgrade."
    -d "features=entities"
    -d "entities.model=10:7abc4c2f-5846-3334-b8f7-af5a6fad3398"
    "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze" -k
    ```
    {: pre}

    該服務會傳回實例的 JSON 物件（它找到在自訂模型中所定義的實體類型）。

    ```javascript
    {
      "language": "en",
      "entities": [
        {
          "type": "MANUFACTURER",
          "text": "Honda",
          "count": 1
        },
        {
          "type": "MODEL",
          "text": "Civic",
          "count": 1
        },
        {
          "type": "VEHICLE",
          "text": "Vehicle 1",
          "count": 1
        },
        {
          "type": "STRUCTURE",
          "text": "two lane undivided roadway",
          "count": 1
        },
        {
          "type": "STRUCTURE",
          "text": "curve",
          "count": 1
        },
        {
          "type": "MODEL_YEAR",
          "text": "1995",
          "count": 1
        },
        {
          "type": "CONDITION",
          "text": "negotiating",
          "count": 1
        }
      ],
      "language": "en"
    }
    ```
    {: codeblock}

- **關係**

    下列指令會尋找使用 text 參數傳遞之句子中存在的關係：

    ```bash
    curl -G -u "3330af09-4b22-4f2d-a54c-1cb099df1fa8":"338rTJSvPVqeG"
    -d "version=2016-05-17"
    -d "text=Vehicle%201%2C%20a%201995%20Honda%20Civic%20was%20traveling%20north
    %20on%20a%20two%20lane%20undivided%20roadway%2C%20negotiating%20a%20curve%20to
    %20the%20left%20on%20an%20upgrade."
    -d "features=relations"
    -d "entities.model=10:7abc4c2f-5846-3334-b8f7-af5a6fad3398"
    "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze" -k
    ```
    {: pre}

    該服務會傳回實例的 JSON 物件（它找到在自訂模型中所定義的關係類型）。

    ```javascript
    {
      "relations": [
        {
          "type": "timeOf",
          "sentence": "Vehicle 1, a 1995 Honda Civic was traveling north
           on a two lane undivided roadway, negotiating a curve to
           the left on an upgrade.",
          "score": 0.954254,
          "arguments": [
            {
              "text": "1995",
              "entities": [
                {
                  "type": "Date",
                  "text": "1995"
                }
              ]
            },
            {
              "text": "Honda Civic",
              "entities": [
                {
                  "type": "SportingEvent",
                  "text": "Honda Civic"
                }
              ]
            }
          ]
        },
        {
          "type": "locatedAt",
          "sentence": "Vehicle 1, a 1995 Honda Civic was traveling north
           on a two lane undivided roadway, negotiating a curve to
           the left on an upgrade.",
          "score": 0.40592,
          "arguments": [
            {
              "text": "negotiating",
              "entities": [
                {
                  "type": "EventMeeting",
                  "text": "negotiating"
                }
              ]
            },
            {
              "text": "roadway",
              "entities": [
                {
                  "type": "Facility",
                  "text": "roadway"
                }
              ]
            }
          ]
        }
      ],
      "language": "en"
    }
    ```
    {: codeblock}

如需詳細資料，請參閱 [{{site.data.keyword.nlushort}} 文件 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/watson/developercloud/doc/natural-language-understanding/index.html){: new_window}。

## 取消部署模型
{: #undeploy-view-model}

如果您要取消部署模型或尋找模型 ID，請檢視**已部署的模型**頁面。**已部署的模型**頁面會顯示已部署至您有權存取之空間中服務的所有 {{site.data.keyword.knowledgestudioshort}} 模型。

若要取消部署模型或尋找模型 ID，請執行下列動作：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理者或專案經理身分登入，並選取您的工作區。
1. 從右上角功能表列的**設定**功能表中，選取**管理已部署的模型**。
1. 從已部署的模型清單中，尋找您要檢視或取消部署的模型。
1. 若要取消部署模型，請從該列的最後一個直欄中，按一下**取消部署模型**。
1. 若要尋找模型 ID，請參閱**模型 ID** 直欄。

## 在 IBM Watson Explorer 中運用機器學習模型
{: #wks_maexport}

匯出經過訓練的機器學習模型，以在 {{site.data.keyword.IBM_notm}}{{site.data.keyword.watson}} Explorer 中使用它。

### 開始之前

如果您選擇識別關係類型並註釋它們，則必須至少定義兩個關係類型，並在您匯出模型之前在基準中註釋關係的實例。定義及註釋唯一的關係類型，可能會在 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer 11.0.1.0 版中造成後續的問題。

### 關於本作業

既然機器學習模型已經過訓練可辨識特定領域的實體及關係，您就可以在 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer 中運用它。

按一下[此鏈結 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.youtube.com/watch?v=1VoS-xczBow&amp;feature=youtu.be){: new_window}，觀看一部不到 2 分鐘的影片，其說明如何匯出模型，以及如何在 {{site.data.keyword.IBM_notm}}{{site.data.keyword.watson}} Explorer 中使用它。

### 程序

若要在 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer 中運用機器學習模型，請完成下列步驟。

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理者或專案經理身分登入，並選取您的工作區。
1. 選取**模型管理** > **版本** > **機器學習**標籤。
1. 按一下**匯出現行模型**。

    如果您使用免費訂閱方案，則沒有匯出選項可供使用。

    此模型會儲存為 ZIP 檔，系統會提示您下載該檔案。

1. 將檔案下載至本端系統。
1. 從 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer 應用程式中，匯入模型。

    然後，您可以將模型對映至 {{site.data.keyword.watson}} Explorer Content Analytics 中的機器學習模型。執行對映步驟之後，當您搜索文件時，此模型會尋找您的模型所瞭解的實體及關係的實例。若要瞭解如何在 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer 中匯入及配置此模型，請參閱用於說明整合的技術文件：[http://www.ibm.com/support/docview.wss?uid=swg27048147 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://www.ibm.com/support/docview.wss?uid=swg27048147){: new_window}。

#### 相關作業

[從 {{site.data.keyword.watson}} Explorer Content Analytics 匯出已分析的文件](/docs/services/watson-knowledge-studio/preannotation.html#wks_uimawexca)
