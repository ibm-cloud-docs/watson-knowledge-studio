---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-13"

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

## 將機器學習模型部署至 IBM Watson Discovery
{: #wks_madiscovery}

當此模型的效能符合您的要求時，您可以將這個版本部署至 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}。此特性可讓您的應用程式使用已部署的機器學習模型，來強化從資料取得的見解，以包括與您領域相關的概念及關係的識別。

### 開始之前
{: #wks_madiscovery_prereqs}

您必須具有 {{site.data.keyword.watson}}{{site.data.keyword.discoveryshort}} 服務實例的管理存取權，且知道與它相關聯的 {{site.data.keyword.Bluemix_notm}} 空間及實例名稱。

### 關於本作業
{: #wks_madiscovery_about}

部署機器學習模型時，您可以選取要部署的版本。

### 程序
{: #wks_madiscovery_procedure}

若要將機器學習模型部署至 {{site.data.keyword.watson}}{{site.data.keyword.discoveryshort}}，請完成下列步驟：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理者或專案經理身分登入，並選取您的工作區。
1. 選取**機器學習模型** > **版本**。
1. 選擇您要部署的模型版本。

    如果模型只有一個工作版本，請建立現行模型的 Snapshot。這會版本化模型（其可讓您部署一個版本），同時您可以繼續改善現行版本。除非您至少建立一個版本，否則不會出現部署選項。

    **附註**：每一個版本只能部署至一個服務實例。如果您要將相同的模型部署至多個實例，請為每一個實例建立一個版本。

1. 按一下**部署**，選擇將其部署至 {{site.data.keyword.discoveryshort}}，然後按**下一步**。
1. 選取 {{site.data.keyword.Bluemix_notm}} 空間及實例。必要的話，請選取不同的地區。
1. 按一下**部署**。
1. 部署程序可能需要一些時間。若要檢查部署的狀態，請按一下已部署版本旁的**版本**標籤上的**狀態**。

    如果模型仍在進行部署，則狀態會指出「發佈中」。部署完成之後，如果部署成功，則狀態會變更為「可用」；如果發生問題，則狀態會變更為「錯誤」。

    一旦可用之後，請記下模型 ID (model_id)。您會將此 ID 提供給 {{site.data.keyword.discoveryshort}} 服務，以讓服務使用您的自訂模型。

### 下一步
{: #wks_madiscovery_next}

若要使用已部署的模型，您必須在 {{site.data.keyword.discoveryshort}} 服務強化配置程序期間要求模型 ID 時予以提供。如需詳細資料，請參閱 [{{site.data.keyword.discoveryshort}} 服務文件 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/docs/services/discovery/integrate-wks.html){: new_window}。

## 將機器學習模型部署至 IBM Watson Natural Language Understanding
{: #wks_manlu}

當此模型的效能符合您的要求時，您可以將這個版本部署至 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.nlushort}}。此特性可讓您的應用程式使用已部署的機器學習模型，來分析文字輸入的語意特性，包括實體及關係。

### 開始之前
{: #wks_manlu_prereqs}

您必須具有要部署至其中的 {{site.data.keyword.nlushort}} 服務。而且您必須知道與服務相關聯的 {{site.data.keyword.Bluemix_notm}} 空間及實例名稱。如果您不記得空間或實例名稱，請登入 {{site.data.keyword.Bluemix_notm}} 來尋找它們。如果您沒有 {{site.data.keyword.Bluemix_notm}} 帳戶，請註冊申請一個帳戶。

### 關於本作業
{: #wks_manlu_about}

部署機器學習模型時，您可以選取要部署的版本。

### 程序
{: #wks_manlu_procedure}

若要將機器學習模型部署至 {{site.data.keyword.nlushort}} 服務，請完成下列步驟：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理者或專案經理身分登入，並選取您的工作區。
1. 選取**機器學習模型** > **版本**。
1. 選擇您要部署的模型版本。

    如果模型只有一個工作版本，請建立現行模型的 Snapshot。這會版本化模型（其可讓您部署一個版本），同時您可以繼續改善現行版本。除非您至少建立一個版本，否則不會出現部署選項。

    **附註**：每一個版本只能部署至一個服務實例。如果您要將相同的模型部署至多個實例，請為每一個實例建立一個版本。

1. 按一下**部署**，選擇將其部署至 {{site.data.keyword.nlushort}}，然後按**下一步**。
1. 選取 {{site.data.keyword.Bluemix_notm}} 空間及實例。必要的話，請選取不同的地區。
1. 按一下**部署**。
1. 部署程序可能需要一些時間。若要檢查部署的狀態，請按一下已部署版本旁的**版本**標籤上的**狀態**。如果模型仍在進行部署，則狀態會指出「發佈中」。部署完成之後，如果部署成功，則狀態會變更為「可用」；如果發生問題，則狀態會變更為「錯誤」。

    一旦可用之後，請記下模型 ID (model_id)。您會將此 ID 提供給 {{site.data.keyword.nlushort}} 服務，以讓服務使用您的自訂模型。

### 下一步
{: #wks_manlu_next}

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

## 在 IBM Watson Explorer 中運用機器學習模型
{: #wks_maexport}

匯出經過訓練的機器學習模型，以在 {{site.data.keyword.IBM_notm}}{{site.data.keyword.watson}} Explorer 中使用它。

### 開始之前
{: #wks_maexport_prereqs}

如果您選擇識別關係類型並註釋它們，則必須至少定義兩個關係類型，並在您匯出模型之前在基準中註釋關係的實例。定義及註釋唯一的關係類型，可能會在 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer 11.0.1.0 版中造成後續的問題。

### 關於本作業
{: #wks_maexport_about}

既然機器學習模型已經過訓練可辨識特定領域的實體及關係，您就可以在 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer 中運用它。

按一下[此鏈結 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.youtube.com/watch?v=1VoS-xczBow&amp;feature=youtu.be){: new_window}，觀看一部不到 2 分鐘的影片，其說明如何匯出模型，以及如何在 {{site.data.keyword.IBM_notm}}{{site.data.keyword.watson}} Explorer 中使用它。

### 程序
{: #wks_maexport_procedure}

若要在 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer 中運用機器學習模型，請完成下列步驟。

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理者或專案經理身分登入，並選取您的工作區。
1. 選取**機器學習模型** > **版本**。
1. 按一下**匯出現行模型**。

    如果您有「精簡」訂閱方案，則沒有可用的匯出選項。

    此模型會儲存為 ZIP 檔，系統會提示您下載該檔案。

1. 將檔案下載至本端系統。
1. 從 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer 應用程式中，匯入模型。

    然後，您可以將模型對映至 {{site.data.keyword.watson}} Explorer Content Analytics 中的機器學習模型。執行對映步驟之後，當您搜索文件時，此模型會尋找您的模型所瞭解的實體及關係的實例。若要瞭解如何在 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer 中匯入及配置此模型，請參閱用於說明整合的技術文件：[http://www.ibm.com/support/docview.wss?uid=swg27048147 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://www.ibm.com/support/docview.wss?uid=swg27048147){: new_window}。

#### 相關作業
{: #wks_maexport_related}

[從 {{site.data.keyword.watson}} Explorer Content Analytics 匯出已分析的文件](/docs/services/watson-knowledge-studio/preannotation.html#wks_uimawexca)
