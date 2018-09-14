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

此文件適用於 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}。若要查看舊版 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 的文件，[請按一下此鏈結 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/docs/services/knowledge-studio/preannotation.html){: new_window}。
{: tip}

# 引導註釋
{: #preannotation}

藉由預先註釋工作區中的文件，來簡化註釋人員的工作。預先註釋程式是 {{site.data.keyword.knowledgestudioshort}} 字典、規則型模型或機器學習模型，您可以執行它們，以自動尋找並註釋提及項目。
{: shortdesc}

預先註釋可讓註釋人員的工作更輕鬆，因為它涵蓋直接明確的註釋，並開始進行註釋文件的工作。

用於預先註釋文件的方法絕不會限制您可以使用產生模型的方式。例如，只因為您使用 {{site.data.keyword.nlushort}} 服務來預先註釋文件，並不表示您必須將建置的最終機器學習模型部署至 {{site.data.keyword.nlushort}} 服務。預先註釋只表示用來引導人工註釋程序。

## 重要注意事項
{: #preannotation_notes}

- 絕不對註釋人員已註釋的文件執行預先註釋程式，因為這樣會移除註釋人員所新增的註釋。
- 您只能對文件執行一個預先註釋程式。如果您執行一個預先註釋程式，然後執行第二個預先註釋程式，則第二個預先註釋程式會移除第一個預先註釋程式所新增的註釋。請挑選最適合您使用案例的預先註釋方法，而且只使用一個預先註釋程式。

## 預先註釋方法
{: #preannotation_methods}

下列是可用的預先註釋程式：

- **{{site.data.keyword.nlushort}}**

    您可以使用預先註釋程式，自動在文件中尋找實體提及項目。如果您的來源文件具有一般的知識主題，則此預先註釋程式是您適用的良好選擇。例如，如果您是使用專注於特定領域（例如專利法研究）的高度特殊化文件，則字典預先註釋程式或規則型模型可能是更適當的選擇。

- **字典**

    使用您提供的詞彙字典，並建立與實體類型的關聯，以在文件中尋找實體類型的提及項目。此選項最適用於具有獨特或特殊化術語的領域，因為這個預先註釋程式不會分析以機器學習預先註釋程式執行方式使用詞彙的上下文；它反而會根據有顯著差別的詞彙，以具有可判讀的意義，而不論其使用詞彙的上下文。例如，將*石棉* 辨識為礦物實體類型，比判定為*壓扁* 實體類型更為容易，而此實體類型可能是蔬菜、運動或壓碎某個東西的動詞意義。

- **機器學習**

    使用機器學習模型來自動註釋文件。只有在您已使用 {{site.data.keyword.knowledgestudioshort}} 建立機器學習模型時，此選項才可供您使用。如果您新增文件集，則可以執行之前建立的機器學習註釋程式，以預先註釋新文件。如果新的文件集與原本用來訓練機器學習註釋程式的文件類似，則這可能是進行預先註釋的最佳選擇。

- **規則**

    使用規則型模型來自動註釋文件。只有在您已使用 {{site.data.keyword.knowledgestudioshort}} 建立規則型模型時，此選項才可供使用。如果您的文件包含可以從中衍生意義的一般記號型樣，則此模型可能是良好的選項。它可以納入字典預先註釋程式（如果啟用它的話）的部分函數，方法為識別其也會在文件中尋找之字典詞彙的類別類型。

或者，您也可以上傳已註釋的文件，並使用它們來開始訓練機器學習模型。您不能對上傳的已註釋文件執行預先註釋程式，否則現有註釋將從文件中除去，並僅取代為預先註釋程式所產生的註釋。

> **附註：**您*可以* 對已新增至基準作為現行工作區一部分的文件，執行預先註釋程式。系統不會除去已新增至文件、已檢閱、已接受，以及已升級至現行工作區內基準的註釋。

## 以 {{site.data.keyword.nlushort}} 預先註釋文件
{: #wks_preannotnlu}

您可以使用 {{site.data.keyword.nlushort}} 服務，來預先註釋您新增至語料庫的文件。

### 開始之前
{: #wks_preannotnlu_prereqs}

判斷 {{site.data.keyword.nlushort}} 預先註釋程式是否可能為您的使用案例新增值。請檢閱支援的 [{{site.data.keyword.nlushort}} 服務實體類型及子類型 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/docs/services/natural-language-understanding/entity-types.html){: new_window} 的清單，以判斷它們與類型系統中的類型之間是否有自然重疊。若有的話，請繼續執行此程序。若沒有，請選擇不同的預先註釋程式來使用。

### 關於本作業
{: #wks_preannotnlu_about}

{{site.data.keyword.nlushort}} 是透過自然語言處理程序提供文字分析的服務。當您使用 {{site.data.keyword.nlushort}} 預先註釋程式時，它會呼叫 {{site.data.keyword.nlushort}} 服務來尋找及註釋文件中的實體。

您必須指定您要服務尋找的實體類型，方法為將 {{site.data.keyword.nlushort}} 實體類型對映至已新增至 {{site.data.keyword.knowledgestudioshort}} 類型系統的 {{site.data.keyword.knowledgestudioshort}} 實體類型。只會尋找並註釋您所對映的實體類型提及項目。

### 程序
{: #wks_preannotnlu_procedure}

若要使用 {{site.data.keyword.nlushort}} 服務來預先註釋文件，請完成下列步驟：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理者身分登入，並選取您的工作區。
1. 選取**機器學習模型** > **預先註釋** > **Natural Language Understanding** 標籤。
1. 按一下**編輯**，將**實體類型**頁面上所定義的每一個實體類型對映至對應的 {{site.data.keyword.nlushort}} 實體類型。

    - {{site.data.keyword.nlushort}} 實體類型的下拉清單會預先移入 {{site.data.keyword.nlushort}} 服務所辨識的實體類型。
    - 您必須至少對映一個實體類型。
    - 您無法將 {{site.data.keyword.nlushort}} 實體類型對映至 {{site.data.keyword.knowledgestudioshort}} 實體角色，只能對映至 {{site.data.keyword.knowledgestudioshort}} 實體類型。
    - 您可以將多個 {{site.data.keyword.nlushort}} 實體類型對映至單一 {{site.data.keyword.knowledgestudioshort}} 實體類型，或其他方式。例如，允許下列對映：

    <table summary="實體類型的範例對映">
    <caption>表 1. 實體類型的範例對映</caption>
      <tr>
        <th style="vertical-align:bottom; text-align"left" id="d20428e292">Watson Knowledge Studio Entity Type</th>
        <th style="vertical-align:bottom; text-align"left" id="d20428e298">{{site.data.keyword.nlushort}} 實體類型</th>
      </tr>
      <tr>
        <td headers="d20428e292">
          ENGINEER<br/>
          SCIENTIST
        </td>
        <td headers="d20428e298">
          Person
        </td>
      </tr>
      <tr>
        <td headers="d20428e292">
          LOCATION
        </td>
        <td headers="d20428e298">
          CityTown<br/>
          Country
        </td>
      </tr>
    </table>
    {: #wks_preannotnlu__datasimpletable_cm1_y3g_fx}

1. 在對映您要套用的所有實體類型之後，請按一下**套用此預先註釋程式**。

    除非您至少對映一個實體類型，否則**套用此預先註釋程式**按鈕無法使用。

1. 選取您想要預先註釋的每一個文件集的勾選框。

    如果您是第一次執行此預先註釋程式，請先驗證預先註釋程式可以如預期找到對映實體提及項目。建立一個文件集，其中包含代表性文件，或來自每一個不同資料來源的文件。
    {: tip}

1. 按一下**執行**。

    如果您是執行預先註釋程式的驗證檢查，請開啟已註釋文件，並檢閱已新增的註釋。請確定已建立足夠的正確註釋數目。如果註釋正確，則您可以在更多及更大的文件集上重新執行註釋程式。如果註釋不正確，請考慮將不同的 {{site.data.keyword.nlushort}} 實體類型對映至您的類型。如果類型未自然重疊，則 {{site.data.keyword.nlushort}} 預先註釋程式不是供您使用的最佳預先註釋程式。

    預先註釋會套用至個別文件，而不會顧慮文件可能隸屬的各種文件集。在已選取文件集與未選取文件集之間重疊的文件，在這兩個文件集中將為已預先註釋。

1. 在您執行一次預先註釋程式之後，只要您想要使用預先註釋程式來預先註釋您新增至語料庫的文件集，您隨時都可以按一下**套用此預先註釋程式**。

    > **限制：**如果您編輯 {{site.data.keyword.nlushort}} 預先註釋程式的類型對映定義，則必須重建包括已預先註釋之文件集的註釋作業。以您對預先註釋程式對映定義所做之變更為基礎的預先註釋，無法套用至已指派給註釋作業的文件集。

### 結果
{: #wks_preannotnlu__export-warning}

由 {{site.data.keyword.nlushort}} 服務預先註釋之文件所產生的基準，無法直接在 {{site.data.keyword.knowledgestudioshort}} 之外使用。您可以下載基準（以不可讀取的格式表示），以將它從某個 {{site.data.keyword.knowledgestudioshort}} 工作區移至另一個工作區。您可以繼續開發基準，並用它來建置機器學習模型或規則型模型，然後部署此模型，以在 {{site.data.keyword.knowledgestudioshort}} 之外的服務中使用。

> **限制：**使用 {{site.data.keyword.nlushort}} 預先註釋的文件在下載時，會被遮蔽成無法讀取的格式。但是，那些文件中的所有註釋都會被遮蔽，包括由註釋人員新增至文件的註釋。

**相關資訊**：

[{{site.data.keyword.nlushort}} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/watson/services/natural-language-understanding/){: new_window}

## 以字典預先註釋文件
{: #wks_preannot}

若要協助註釋人員開始使用其註釋作業，您可以建立字典，並使用它來預先註釋您新增至語料庫的文件。

### 關於本作業
{: #wks_preannot_about}

當註釋人員開始使用已預先註釋的文件時，實體類型可能已根據字典項目標示一些提及項目。註釋人員可以變更或移除預先註釋的實體類型，並將實體類型指派給未註釋的提及項目。由字典進行的預先註釋不會註釋關係及互相參照。關係及互相參照必須由註釋人員註釋。

**附註**：此作業顯示如何建立可編輯的字典。如果您要使用唯讀字典來上傳及預先註釋文件，請按一下**建立字典**按鈕旁邊的**功能表**圖示。選取**上傳字典**。

### 程序
{: #wks_preannot_procedure}

若要建立可編輯字典並預先註釋文件，請執行下列動作：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理者身分登入，並選取您的工作區。
1. 選取**資產** > **字典**頁面。
1. 按一下**建立字典**，輸入名稱，然後按一下**儲存**。
1. 從**實體類型**清單中，選取要與字典相關聯的實體類型。
3. 新增字典的項目，或上傳包含字典詞彙的檔案。
4. 按一下**機器學習模型** > **預先註釋**。
5. 在**字典**標籤上，按一下**套用此預先註釋程式**。
6. 選取您想要預先註釋的每一個文件集的勾選框，然後按一下**執行**。

    預先註釋會套用至個別文件，而不會顧慮文件可能隸屬的各種文件集或註釋集。在已選取文件集與未選取文件集之間重疊的文件，在這兩個文件集中將為已預先註釋。

7. 在建立字典之後，只要您想要使用字典來預先註釋您新增至語料庫的其他文件集，請隨時按一下**執行**。

    > **限制：**如果您編輯字典來新增或移除項目，則必須重建包括已預先註釋之文件集的註釋作業。以您對字典註釋程式所做之變更為基礎的預先註釋，無法套用至已指派給註釋作業的註釋集。

**相關資訊**：

[建立字典](/docs/services/watson-knowledge-studio/dictionaries.html)

[開始使用 > 新增字典](/docs/services/watson-knowledge-studio/tutorials-create-project.html#wks_tutless4)

## 以機器學習模型預先註釋文件
{: #wks_preannotsire}

您可以使用現有機器學習模型，來預先註釋您新增至語料庫的文件。

### 關於本作業
{: #wks_preannotsire_about}

在註釋 10 到 30 個文件之後，可對資料進行機器學習模型訓練。這類最小訓練模型不應用於正式作業，但可用來預先註釋文件，以協助加速後續文件的人工註釋。例如，如果您在訓練機器學習模型之後將文件新增至語料庫，則可以使用此模型來預先註釋新的文件集。絕不在人員所註釋的同一文件上執行預先註釋程式。預先註釋程式會移除人工註釋。

### 程序
{: #wks_preannotsire_procedure}

若要使用現有機器學習模型來預先註釋文件，請執行下列動作：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理者身分登入，並選取您的工作區。
2. 選取**機器學習模型** > **版本**。
3. 若要預先註釋新文件，請按一下**執行此模型**。
4. 選取您想要預先註釋的每一個文件集的勾選框，然後按一下**執行**。

    預先註釋會套用至個別文件，而不會顧慮文件可能隸屬的各種文件集或註釋集。在已選取文件集與未選取文件集之間重疊的文件，在這兩個文件集中將為已預先註釋。

5. 只要您想要使用機器學習模型來預先註釋您新增至語料庫的文件集，您隨時都可以按一下**執行此模型**。

## 以規則型模型預先註釋文件
{: #wks_preannotrule}

您可以使用現有規則型模型，來預先註釋您新增至語料庫的文件。

### 程序
{: #wks_preannotrule_procedure}

若要使用規則型模型來預先註釋文件，請完成下列步驟：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理者身分登入，並選取您的工作區。
1. 選取**規則型模型** > **版本** > **規則型模型**標籤。
1. 如果尚未完成，請按一下**對映實體類型及類別**，將您已在 {{site.data.keyword.knowledgestudioshort}} 類型系統中定義的實體類型對映至一個以上的規則型模型類別。
2. 針對您要對映的每一個實體類型，按一下**編輯**。

    - **類別名稱**直欄的下拉清單會預先移入與規則型模型相關聯的類別。
    - 您必須至少將一個實體類型對映至類別。

3. 在**規則型模型**標籤上，按一下**執行此模型**。

    除非您至少對映一個實體類型，否則**執行此模型**按鈕無法使用。

4. 選取您要預先註釋的文件集或註釋集。請確定您選取的集合不包含具有人工註釋的文件。預先註釋程式會移除人工註釋。
5. 按一下**執行**。

    預先註釋會套用至個別文件，而不會顧慮文件可能隸屬的各種文件集。在已選取文件集與未選取文件集之間重疊的文件，在這兩個文件集中將顯示為已預先註釋。

6. 只要您想要使用規則型模型來預先註釋您新增至語料庫的其他文件集，您隨時都可以按一下**執行此模型**。

    > **限制：**如果您編輯規則型模型的實體類型至類別對映，則必須重建包括已預先註釋之文件集的註釋作業。以您對預先註釋程式對映定義所做之變更為基礎的預先註釋，無法套用至已指派給註釋作業的文件集。

## 上傳預先註釋的文件
{: #wks_uima}

您可以透過 Unstructured Information Management Architecture (UIMA) 分析引擎上傳預先註釋的文件，以快速開始訓練模型。

預先註釋的文件必須位於「UIMA 共用分析結構 (UIMA CAS XMI)」的 XMI 序列化表單中。您上傳的 ZIP 檔必須包括 UIMA TypeSystem 描述子檔案，以及將 UIMA 類型對映至 {{site.data.keyword.knowledgestudioshort}} 類型系統中實體類型的檔案。

UIMA CAS XMI 是 Apache UIMA 的標準格式。提供的準則可讓您以正確格式從 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer 中的已分析集合建立檔案。如果您使用另一個 Apache UIMA 實作，請根據您的目的來調整這些準則。不論您如何建立 XMI 檔案，每個人建立類型系統對映檔及 ZIP 檔的需求都相同。

如果您將匯入的文件指派給註釋人員，則在基準編輯器中會預先註釋文件，而且可能已註釋一些提及項目。因此，註釋人員有更多時間可以專注在將註釋準則套用至未標示的提及項目。或者，您也可以略過人工註釋步驟，並使用預先註釋的文件來立即開始訓練及評估機器學習模型。

### 從 Watson Explorer Content Analytics 匯出已分析的文件
{: #wks_uimawexca}

您可以匯出已在 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer Content Analytics 中搜索及分析的文件，並將分析的文件當作 XMI 檔上傳至 {{site.data.keyword.knowledgestudioshort}} 工作區。

#### 程序
{: #wks_uima_procedure}

若要從 {{site.data.keyword.watson}} Explorer Content Analytics 集合中取得已分析的文件，請執行下列動作：

1. 在 Web 瀏覽器中開啟 Content Analytics 管理主控台。
1. 在「集合」視圖上，展開您要從中匯出文件的集合。在「剖析及索引」窗格中，確保剖析及索引程序正在執行中，然後按一下**匯出已分析文件內容及 meta 資料**的箭頭圖示。
1. 在**已分析的文件匯出選項**區域中，選取**將文件匯出為 XML 檔**、選取**將 CAS 啟用為 XMI 格式匯出**勾選框、指定要寫入已匯出資料的輸出路徑，然後按一下**確定**。
1. 停止並重新啟動集合的剖析及索引服務，然後執行下列其中一個步驟：

    - 如果集合已在文件快取中包含您要用於訓練機器學習模型的索引文件，請重新啟動完整索引建置。
    - 如果集合未包含您要用於訓練機器學習模型的索引文件，請上傳文件、至少配置一個搜索器來搜索文件，然後啟動搜索器。

1. 在**匯出**區域中，檢查匯出要求的狀態。進度會指出匯出的文件數量。
1. 移至您在配置匯出選項時指定的輸出資料夾。當文件匯出為 XML 檔時，輸出資料夾名稱是基於匯出發生時的時間戳記。輸出資料夾包含 XMI 檔 (`*.xmi`) 及 UIMA TypeSystem 描述子檔案 (`exported_typesystem.xml`)。

#### 下一步
{: #wks_uimawexca__preUIMAimport}

您必須定義 UIMA 類型與 {{site.data.keyword.knowledgestudioshort}} 實體類型之間的對映。您也必須建立 ZIP 檔，其中包含將已分析資料上傳至 {{site.data.keyword.knowledgestudioshort}} 工作區所需的所有檔案。

**相關資訊**：

[匯出已搜索或已分析的文件 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ad.doc/iiysatexportca.htm){: new_window}

[已匯出文件的輸出路徑 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ad.doc/iiysaexportoutput.htm){: new_window}

### 從 Content Analytics Studio 匯出已分析的集合
{: #wks_uimawexstudio}

您可以從 {{site.data.keyword.watson}}Explorer Content Analytics Studio 匯出已分析文件的集合，並將分析的文件當作 XMI 檔上傳至 {{site.data.keyword.knowledgestudioshort}} 專案。

#### 程序
{: #wks_uimawexstudio_procedure}

若要從 Content Analytics Studio 集合中取得已分析的文件，請執行下列動作：

1. 啟動 Content Analytics Studio，並開啟 Studio 專案。
1. 在包含您要用於訓練機器學習模型之文件的資料夾上按一下滑鼠右鍵，並選取**分析集合**。
1. 選取 UIMA 管線配置檔。
1. 移至「集合分析」視圖，然後按一下「集合分析」視圖中的**儲存**圖示。指定要寫入所儲存結果的資料夾，並指定檔名。
1. 開啟您指定的資料夾。所儲存檔案的副檔名為 `.annotations`。
1. 將 `.annotations` 檔複製到本端檔案系統，然後將副檔名從 `.annotations` 重新命名為 `.zip`。
1. 解壓縮 ZIP 檔中的所有檔案。解壓縮的內容包括 XMI 檔 (`*.xmi`)、UIMA TypeSystem 描述子檔案 (`TypeSystem.xml`) 及其他檔案。

#### 下一步
{: #wks_uimawexstudio_next}

您必須定義 UIMA 類型與 {{site.data.keyword.knowledgestudioshort}} 實體類型之間的對映。您也必須建立 ZIP 檔，其中包含將已分析資料上傳至 {{site.data.keyword.knowledgestudioshort}} 工作區所需的所有檔案。

### 對映 UIMA 類型與實體類型
{: #wks_uimawexmap}

在將 XMI 檔上傳至 {{site.data.keyword.knowledgestudioshort}} 工作區之前，您必須定義 UIMA 類型與 {{site.data.keyword.knowledgestudioshort}} 實體類型之間的對映。

#### 開始之前
{: #wks_uimawexmap_prereqs}

{{site.data.keyword.knowledgestudioshort}} 工作區中的類型系統必須包括您要與 UIMA 類型相對映的實體類型。

#### 程序
{: #wks_uimawexmap_procedure}

若要對映 UIMA 類型與 {{site.data.keyword.knowledgestudioshort}} 實體類型，請執行下列動作：

1. 在包含 UIMA TypeSystem 描述子檔案的資料夾中建立一個名為 `cas2di.tsv` 的檔案，例如 `exported_typesystem.xml` 或 `TypeSystem.xml`。
1. 使用文字編輯器開啟 `cas2di.tsv` 檔案。檔案中的每一行都會指定單一對映。對映的格式視您要對映之註釋程式的註釋而定：

    - 您可以使用基本格式來建立對映：

        `UIMA_Type_Name[TAB]WKS_Entity_Type`

        下列範例定義使用 {{site.data.keyword.watson}} Explorer Content Analytics 中「具名實體識別」註釋程式所產生的 UIMA 類型與 {{site.data.keyword.knowledgestudioshort}} 類型系統中所定義實體類型之間的對映：

        ```
        com.ibm.langware.Organization  ORGANIZATION
        com.ibm.langware.Person  PERSON
        com.ibm.langware.Location  LOCATION
        ```
        {: screen}

        另一個範例定義在 {{site.data.keyword.watson}}Explorer Content Analytics Studio 中已建立之自訂註釋程式所產生的 UIMA 類型與 {{site.data.keyword.knowledgestudioshort}} 實體類型之間的對映：

        ```
        com.ibm.Person  PERSON
        com.ibm.Date  DATE
        ```
        {: screen}

    - 在 {{site.data.keyword.watson}} Explorer Content Analytics 中，您可以根據在「型樣配對器」註釋程式或「字典查閱」註釋程式中使用的資料類型來建立對映。在文字分析規則檔 (`*.pat`) 中，以種類屬性來代表資料類型。若要定義對映，請使用下列語法：

        ```
        com.ibm.takmi.nlp.annotation_type.ContiguousContext:category={FACET_PATH}[TAB]{WKS_ENTITY_TYPE}
        ```
        {: screen}

        下列適用於「型樣配對器」及「字典查閱」註釋程式的範例，會定義種類 $.mykeyword.product 與 {{site.data.keyword.knowledgestudioshort}} 實體類型 PRODUCT 之間的對映：

        ```
        com.ibm.takmi.nlp.annotation_type.ContiguousContext:category=$.mykeyword.product PRODUCT
        ```
        {: screen}

#### 下一步
{: #wks_uimawexmap_next}

您必須建立 ZIP 檔，其中包含將已分析資料上傳至 {{site.data.keyword.knowledgestudioshort}} 工作區所需的所有檔案。

**相關資訊**：

[「型樣配對器」註釋程式 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ta.doc/iiystapattmatch.htm){: new_window}

[「字典查閱」註釋程式 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ta.doc/iiystadictlookup.htm){: new_window}

[「具名實體識別」註釋程式 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ta.doc/iiystasystemt.htm){: new_window}

### 將 UIMA CAS XMI 檔上傳至工作區
{: #wks_uimaweximport}

若要使用您所下載的已註釋文件來訓練模型，您必須建立 ZIP 檔，其中包含上傳 XMI 檔所需的所有檔案，然後將 ZIP 檔上傳至 {{site.data.keyword.knowledgestudioshort}} 工作區。

#### 開始之前
{: #wks_uimaweximport_prereqs}

在上傳 ZIP 檔之前，請確保 {{site.data.keyword.knowledgestudioshort}} 工作區中的類型系統包括您已與 UIMA 類型相對映的實體類型。

> **警告：**UIMA 分析引擎容許跨句子的註釋。在 {{site.data.keyword.knowledgestudioshort}} 中，註釋必須存在於單一句子的界限內。如果您上傳的 XMI 檔包括跨句子的註釋，則那些註釋不會出現在基準編輯器中。

#### 程序
{: #wks_uimaweximport_procedure}

若要將預先註釋的文件上傳至 {{site.data.keyword.knowledgestudioshort}} 工作區，請執行下列動作：

1. 建立 ZIP 檔，其中包含 {{site.data.keyword.knowledgestudioshort}} 所需的所有檔案。

    1. 選取包含 XMI 檔、UIMA 類型系統描述子檔案及 `cas2di.tsv` 檔案的資料夾，或選取資料夾中的所有檔案。
    1. 建立包括所有檔案的 ZIP 檔。確定 `cas2di.tsv` 及 UIMA 類型系統描述子檔案儲存在 ZIP 檔的根目錄中。這些檔案不能儲存在 ZIP 檔內的子資料夾中，否則 {{site.data.keyword.knowledgestudioshort}} 無法讀取它們，而且不會匯入任何內容。

        在 Windows 中，您可以按一下滑鼠右鍵選取**傳送到**>**壓縮的 (zipped) 資料夾**。

1. 將 ZIP 檔上傳至 {{site.data.keyword.knowledgestudioshort}} 工作區。

    1. 以 {{site.data.keyword.knowledgestudioshort}} 管理者或專案經理身分登入，開啟您要新增文件的工作區，然後開啟**資產** > **文件**頁面。
    1. 按一下**上傳文件集**。
    1. 拖曳您建立的 ZIP 檔，或按一下來尋找並選取檔案。
    1. 選取勾選框，以指出 ZIP 檔包含 UIMA CAS XMI 檔。
    1. 按一下**上傳**。
