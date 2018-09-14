---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-16"

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

此文件適用於 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}。若要查看舊版 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 的文件，[請按一下此鏈結 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/docs/services/knowledge-studio/tutorials-create-project.html){: new_window}。
{: tip}

# 開始使用 {{site.data.keyword.knowledgestudioshort}}
{: #wks_tutintro}

本 {{site.data.keyword.knowledgestudiofull}} 指導教學可協助您執行必要作業，這些作業必須先完成，您才能啟動任何其他指導教學。
{: shortdesc}

## 開始之前
{: #prereq}

- 確認您使用支援的瀏覽器。如需相關資訊，請參閱[瀏覽器需求](/docs/services/watson-knowledge-studio/system-requirements.html)。
-  若要完成本指導教學，您必須至少具有一個可在 {{site.data.keyword.knowledgestudioshort}} 中使用的使用者 ID。這個使用者 ID 必須具有 Admin 角色。如果您註冊「精簡」方案，則當您作為唯一使用者時，您將具有 Admin 角色。如需使用者角色的相關資訊，請參閱[組合團隊](/docs/services/watson-knowledge-studio/team.html)。

## 建立服務實例
{: #instance}

1. 如果還沒有，請[註冊 {{site.data.keyword.ibmid}} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net){: new_window}，並登入 {{site.data.keyword.cloud_notm}}。
1. 從 {{site.data.keyword.cloud_notm}} {{site.data.keyword.watson}} [服務頁面 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/developer/watson/services){: new_window} 中，按一下 {{site.data.keyword.knowledgestudioshort}} 磚，然後註冊方案。
1. 在註冊方案之後，請從現有服務清單中，啟動 {{site.data.keyword.knowledgestudioshort}}。

## 課程 1：指派使用者角色
{: #wks_tutless1}

在本課程中，您將學習您可以指派給 {{site.data.keyword.knowledgestudioshort}} 中之使用者的不同角色。

### 關於本作業
{: #wks_tutless1_about}

建立機器學習模型需要來自主題專家、專案經理，以及可瞭解並解譯統計模型之使用者的輸入。管理者可將角色指派給每一位使用者，讓他們對其作業具有適當的權限。如需使用者角色的相關資訊，請參閱[組合團隊](/docs/services/watson-knowledge-studio/team.html)。

### 程序
{: #wks_tutless1_procedure}

1. 使用您的管理者 ID 登入 {{site.data.keyword.knowledgestudioshort}}。如果您具有現有 {{site.data.keyword.knowledgestudioshort}} 實例，則可從 {{site.data.keyword.cloud_notm}} {{site.data.keyword.watson}} [服務頁面 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/developer/watson/services){: new_window} 中找到它。
1. 按一下「設定」圖示，以開啟「服務詳細資料」頁面。此頁面會列出已登錄為 {{site.data.keyword.knowledgestudioshort}} 使用者的所有使用者 ID。每一個使用者 ID 都具有下列其中一個角色（以降冪排列所包括的許可權）：

    - Admin
    - 專案經理
    - 註釋人員

    如需使用者角色的相關資訊，請參閱 [{{site.data.keyword.knowledgestudioshort}} 中的使用者角色](/docs/services/watson-knowledge-studio/roles.html)。

1. 驗證至少有一位使用者具有 Admin 角色。具有此角色的使用者 ID 可以建立工作區，並作為專案經理或註釋人員。
1. 如果您可以存取其他使用者 ID，請驗證至少有兩位使用者具有「註釋人員」角色。

    > **附註：**除了管理者或專案經理之外，建立真實模型通常涉及多位註釋人員。不過，基於指導教學的目的，您可以繼續使用單一使用者 ID。

1. 選用項目：變更指派給使用者 ID 的角色。從表格的**動作**直欄中，按一下**編輯**鏈結，然後變更指派的使用者角色。

    > **附註：**您可以將使用者 ID 升級至具有更大許可權的角色，但您無法將具有 Admin 或「專案經理」角色的使用者降級至「註釋人員」角色。

## 課程 2：建立工作區
{: #wks_tutless2}

在本課程中，您將學習如何在 {{site.data.keyword.knowledgestudioshort}} 內建立工作區。

### 關於本作業
{: #wks_tutless2_about}

工作區定義建立機器學習模型所需的所有資源，包括訓練文件、類型系統、字典，以及註釋人員所新增的註釋。如需建立工作區的相關資訊，請參閱[建立工作區](/docs/services/watson-knowledge-studio/create-project.html)。

### 程序
{: #wks_tutless2_procedure}

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理者身分，從 {{site.data.keyword.cloud_notm}} [儀表板 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net){:new_window} 中啟動 {{site.data.keyword.knowledgestudioshort}} 服務。
1. 按一下**建立工作區**。
1. 指定新工作區的詳細資料：

    - 在**工作區名稱**欄位中，鍵入 `My workspace`。
    - 在**工作區說明**欄位中，鍵入 `Watson Knowledge Studio tutorial workspace`。
    - 在**文件語言**欄位中，使用預設值**英文**。您將用於本指導教學的範例檔案為英文版。

1. 按一下**建立**。

### 結果
{: #wks_tutless2_results}

即會建立工作區，並自動開啟。

### 下一步
{: #wks_tutless2_next}

您現在可以開始配置工作區資源，例如類型系統。

## 課程 3：建立類型系統
{: #wks_tutless3}

在本課程中，您將學習如何上傳及修改 {{site.data.keyword.knowledgestudioshort}} 內的類型系統。在開始任何註釋作業之前，您必須先建立或上傳類型系統。

### 關於本作業
{: #wks_tutless3_about}

如需類型系統的相關資訊，請參閱[類型系統](/docs/services/watson-knowledge-studio/typesystem.html#wks_typesystem)。

### 程序
{: #wks_tutless3_procedure}

1. 將 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/en-klue2-types.json" download>en-klue2-types.json <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示" title="外部鏈結圖示" class="style-scope doc-content"></a> 檔案下載至您的電腦。此檔案包含範例 KLUE 類型系統。
1. 按一下**資產** > **實體類型**。
1. 在「實體類型」頁面上，按一下**上傳**。
1. 從您的電腦上傳 `en-klue2-types.json` 檔案。上傳的類型系統即會顯示在表格中。
1. 瀏覽類型系統，讓您可以查看上傳的資料。
1. 編輯實體類型：

    1. 找出 MONEY 實體類型。
    1. 按兩下表格列中的任意處，以編輯實體類型。
    1. 在**角色**直欄中，按一下 AWARD 角色旁的**刪除角色** 圖示 ![「刪除角色」圖示。](images/wks_delete.jpg "「刪除角色」圖示。")。

        ![刪除實體類型中的角色的畫面擷取。](images/wks_tut_delete_role.jpg "顯示將游標移至「刪除角色」圖示上方的畫面擷取。")

    1. 按一下**儲存**。

### 下一步
{: #wks_tutless3_next}

在完成變更類型系統之後，您可以開始將文件新增至工作區。

## 課程 4：新增字典
{: #wks_tutless4}

在本課程中，您將學習如何將字典新增至 {{site.data.keyword.knowledgestudioshort}} 中的工作區。字典用於在建立機器學習模型時預先註釋文字。

### 關於本作業
{: #wks_tutless4_about}

如需字典的相關資訊，請參閱[將字典新增至工作區](/docs/services/watson-knowledge-studio/dictionaries.html#wks_projdictionaries)。

### 程序
{: #wks_tutless4_procedure}

1. 將 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/dictionary-items-organization.csv" download>`dictionary-items-organization.csv ` <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示" title="外部鏈結圖示" class="style-scope doc-content"></a> 檔案下載至您的電腦。此檔案包含 CSV 格式的字典詞彙，適用於上傳至 {{site.data.keyword.knowledgestudioshort}} 字典。
1. 按一下**資產** > **字典**。
1. 按一下**建立字典**來新增字典。

    > **附註：**不要按一下**上傳字典**，這是用來上傳您想要按原狀使用的字典。對於此指導教學，您將建立新的可編輯字典，然後將詞彙上傳至其中。

1. 在**名稱**欄位中，鍵入 `Test dictionary`，然後按一下**儲存**來建立（空白）字典。

    即會建立新的字典，並自動開啟以進行編輯。

1. 在字典窗格中，按一下**上傳**。
1. 從您的電腦上傳 `dictionary-items-organization.csv` 檔案。檔案中的詞彙即會上傳至字典。
1. 按一下**新增項目**來建立新的詞彙。即會在表格頂端新增可編輯列。
1. 在**表面形式**直欄中，於個別行上鍵入 `IBM` 及 `International Business Machines Corporation`。（當您開始鍵入新的表面形式時，會在下面新增一個空間，供其他表面形式使用。）讓 `IBM` 旁邊的圓鈕保持已選取狀態，這表示 `IBM` 是詞目。
1. 在**詞性**直欄中，選取**名詞**。
1. 按一下**儲存**。

    ![「字典」頁面的畫面擷取。已選取 "IBM" 字典項目，並強調顯示其表面形式及詞性。](images/wks_tutdict4.jpg "「字典」頁面的畫面擷取。已選取 "IBM" 字典項目，並強調顯示其表面形式及詞性。")

### 下一步
{: #wks_tutless4_next}

在建立字典之後，您可以使用它，藉由預先註釋文件來加速人工註釋作業。

## 指導教學摘要
{: #wks_tutsum}

學習 {{site.data.keyword.knowledgestudioshort}} 時，您已建立工作區並將構件新增至其中。

### 已學習的課程
{: #lessons_learned}

藉由完成本指導教學，您已學到下列概念：

- 工作區
- 類型系統
- 字典
