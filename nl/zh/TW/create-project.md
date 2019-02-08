---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-18"

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

此文件適用於 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}。若要查看舊版 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 的文件，[請按一下此鏈結 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/docs/services/knowledge-studio/create-project.html){: new_window}。
{: tip}

# 建立工作區
{: #create-project}

建置自訂模型的第一個步驟是建立工作區。
{: shortdesc}

## 關於本作業

對於您要建置及使用的每一個模型，您可以建立一個包含建置模型所需之構件和資源的單一工作區。然後，您可以訓練模型，以產生可部署至外部服務以供使用的自訂模型。

建立工作區之前，請先回答下列問題：

- **您要建立哪種類型的模型？**

    - 機器學習模型：使用統計方法來尋找文件中的實體及關係。此類型模型可隨著資料量的成長進行調整。
    - 規則型模型：使用宣告方法來尋找文件中的實體。這種類型的模型較可以預測，且更容易理解及維護。不過，它不會從新資料中學習。它只能尋找它被教育要尋找的型樣。

    > **附註：**您也可以建立一個同時包含一個規則型模型及一個機器學習模型的工作區。

- **哪些服務會使用模型？**

    如需可搭配使用自訂模型的其他 {{site.data.keyword.watson}} 服務的相關資訊，請參閱 [{{site.data.keyword.watson}} 服務整合](/docs/services/watson-knowledge-studio/index.html#wks_watsoninteg)。

## 程序

若要建立工作區，請完成下列步驟：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理者身分登入，然後按一下**建立工作區**。

    > **附註：**具有專案經理角色的人員可以執行幾乎所有作業，但建立工作區除外。管理者必須先建立工作區，並為其指派專案經理。

1. 為工作區提供名稱。請選擇一個反映您領域內容或模型用途的簡稱。如果您需要，稍後可以變更工作區名稱。
1. 識別工作區中文件的語言。您新增至工作區的文件以及您建立或上傳的字典，必須使用您指定的語言。
1. 選用項目：如果您要變更應用程式所用的記號器（即預設的機器學習型記號器），則可以展開**進階選項**區段，然後選擇**字典型記號器**。

    預設記號器比字典型記號器更高階；其使用機器學習，根據其以來源文件的語言所完成的統計學習，來識別來源文件中的記號。其會識別查準率較高的記號，因為其瞭解更自然且細微的語言型樣。字典型記號器會根據語言規則來識別記號。如需詳細資料，請參閱[記號器](/docs/services/watson-knowledge-studio/create-project.html#wks_tokenizer)。

1. 選用項目：如果您要將專案經理新增至工作區，則展開**進階選項**區段，然後從清單中選取要新增為專案經理的人員名稱。管理者稍後可以藉由編輯工作區來新增或移除專案經理。

    只會顯示您從「使用者帳戶管理」頁面中針對實例而指派給專案經理角色的人員名稱。如需新增使用者的相關資訊，請參閱[組合團隊](/docs/services/watson-knowledge-studio/team.html)。

    > **附註：**如果您使用「精簡」訂閱方案，請跳過此步驟。您無法新增其他使用者，因此您無法將任何人指派給專案經理角色。您不需要個別的專案經理。當您作為管理者時，可以執行專案經理一般會執行的所有作業。

1. 按一下**建立**。

## 下一步

建立工作區之後，您就可以開始配置工作區資源。

若要變更工作區說明或工作區名稱，或是要於稍後新增或移除專案經理，管理者可以編輯工作區。從 {{site.data.keyword.knowledgestudioshort}} 首頁，按一下工作區磚上的**顯示功能表**圖示，然後選擇**編輯**功能表選項。

**相關概念**：

[從其他工作區上傳資源](/docs/services/watson-knowledge-studio/exportimport.html)

**相關參考資料**：

[語言支援](/docs/services/watson-knowledge-studio/language-support.html)

## 記號器
{: #wks_tokenizer}

記號器會將字元分組成記號，將記號分組成句子。記號大概相等於單字。

記號器為了識別文件的記號而必須採取的動作，視文件的語言而有所不同。在英文中，記號通常相當於句子中以空格分隔的單字。不過，記號與單字不一定一對一相符；其他文字元素在某些情況下會被視為記號。例如，句子結尾的標點符號被視為記號，而縮寫形式通常會展開成兩個記號。在不使用空格的語言中（例如，中文），會使用較複雜的統計演算法來識別記號。

記號化程序很重要，因為它決定使用者在基準編輯器中可強調顯示註釋的字元群組。實體及關係提及項目的註釋通常會與記號界限對齊，且必須在句子內加上標籤；它們不能跨越句子界限。

### 支援的類型

{{site.data.keyword.knowledgestudioshort}} 支援下列記號器：

- **機器學習型記號器（預設值）**

    這是較高階的記號器，根據其以來源文件的語言所完成的統計學習，來識別來源文件中的記號。此記號器會尋找擷取更自然且細微的語言型樣的記號。您無法自訂此記號器。

- **字典型記號器**

    此記號器是以語言字典為基礎。它會尋找遵循來源文件語言規則的記號。只有進階使用者才能自訂此記號器。

您必須選擇在建立工作區時要使用的記號器。您無法於稍後切換至不同的記號器。為取得最佳結果，請使用預設記號器。只有想要透過唯一性字典機制來修改記號器行為的進階使用者，可以選擇字典型記號器。然後，他們可以藉由新增項目至字典的方式來予以自訂。不過，必須小心執行自訂作業，因為當您在字典中新增單字時，變更可能會以非預期的方式影響機器學習模型。

## 輸入、輸出及限制的摘要
{: #wks_formats}

不同的模型開發階段需要不同的輸入，且會產生不同的輸出。

針對模型開發程序的每一個階段，此表格彙總您所執行的一般活動、支援的輸入檔格式、可產生的輸出以及任何調整大小限制或其他需求。

### 所有模型類型

<table summary="此表格提供所有模型類型之輸入、輸出及限制的摘要。">
  <caption>表 1. 所有模型類型</caption>
  <tr>
    <th style="vertical-align:bottom; text-align:left" id="d25459e252">
作業</th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e254">
一般用法</th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e256">
支援的輸入格式</th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e258">
支援的輸出格式</th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e260">
限制及需求</th>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e252">
      <p>類型系統管理</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e254">
      <p>建立類型系統或上傳及修改現有的類型系統。</p>
      <p>定義您領域的實體類型及關係類型。</p>
      <p>您看不到類型系統的視覺效果。</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e256">
      <ul>
        <li>
          <p>從 {{site.data.keyword.knowledgestudioshort}} 工作區下載的 JSON 檔</p>
        </li>
        <li>
          <p>從「人工註釋工具 (HAT)」下載的 ZIP 檔</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e258">
      <ul>
        <li>
          <p>JSON</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e260">
      <p>為避免人工註釋的視覺超載，請定義 50 個以下的實體類型及 50 個以下的關係類型。</p>
      <p>上傳類型系統的檔案大小限制：20 MB</p>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e252">
      <p>字典管理</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e254">
      <p>以唯讀模式或將您從其他工作區下載的字典壓縮成一個 ZIP 檔，來上傳 CSV 字典檔。</p>
      <p>建立新的字典，然後上傳詞彙項目的 CSV 檔或向其新增詞彙項目。</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e256">
      <p>字典檔：</p>
      <ul>
        <li>
          <p>UTF-8 格式的 CSV 檔</p>
        </li>
        <li>
          <p>從其他工作區下載的字典的 ZIP 檔</p>
        </li>
      </ul>
      <p>詞彙項目檔：</p>
      <ul>
        <li>
          <p>UTF-8 格式的 CSV 檔</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e258">
      <ul>
        <li>
          <p>UTF-8 格式的 CSV 檔</p>
        </li>
        <li>
          <p>要在其他工作區中使用的字典的 ZIP 檔</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e260">
      <p>檔案大小限制：</p>
      <ul>
        <li>
          <p>每個 CSV 詞彙項目檔 1 MB</p>
        </li>
        <li>
          <p>每個 CSV 唯讀字典檔 16 MB</p>
        </li>
        <li>
          <p>每個字典 15,000 個項目（唯讀字典除外）</p>
        </li>
        <li>
          <p>每個工作區 64 個字典</p>
        </li>
      </ul>
    </td>
  </tr>
</table>

 {: #wks_formats__datasimpletable_xxj_qr5_2y}

### 機器學習模型

<table summary="此表格提供機器學習模型之輸入、輸出及限制的摘要。">
  <caption>表 2. 機器學習模型</caption>
  <tr>
    <th style="vertical-align:botton; text-align:left" id="d25459e331">作業</th>
    <th style="vertical-align:botton; text-align:left" id="d25459e333">一般用法</th>
    <th style="vertical-align:botton; text-align:left" id="d25459e335">支援的輸入格式</th>
    <th style="vertical-align:botton; text-align:left" id="d25459e337">支援的輸出格式</th>
    <th style="vertical-align:botton; text-align:left" id="d25459e339">限制及需求</th>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>文件管理</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
      <p>上傳有代表性的小型文件子集</p>
      <p>上傳包含先前由註釋人員、機器學習模型或 UIMA 分析引擎所新增之註釋的文件</p>
      <p>您無法從 {{site.data.keyword.ibmwatson_notm}} Explorer 汲取整個語料庫，以計算註釋的高價值文件。</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <ul>
        <li>
          <p>UTF-8 格式的 CSV 檔</p>
        </li>
        <li>
          <p>UTF-8 格式的文字</p>
        </li>
        <li>
          <p>包含從其他語料庫下載的文件的 ZIP 檔</p>
        </li>
        <li>
          <p>包含
UIMA
 CAS XMI 格式文件的 ZIP 檔</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <ul>
        <li>
          <p>文件的 ZIP 保存檔</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <ul>
        <li>
          <p>每個文件 40,000 個字元</p>
        </li>
        <li>
          <p>每個工作區 10,000 個文件</p>
        </li>
        <li>
          <p>每個工作區 1,000 個文件集（包括註釋集）</p>
        </li>
      </ul>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>預先註釋</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
       <p>使用字典或
{{site.data.keyword.nlufull}}
預先註釋程式來
提供人工註釋的起始點。</p>
       <p>您無法從 {{site.data.keyword.ibmwatson_notm}} Explorer 重新註釋語料庫。</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <p>原始文件。</p>
      <p><b>附註：</b>不要預先註釋註釋人員已註釋的文件，否則您將會失去由註釋人員所完成的工作。</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <p>部分已註釋的文件</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <p>無</p>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>文件註釋</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
      <p>管理人工註釋</p><p>註釋實體、關係及互相參照鏈結，以建立基準</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <p>註釋作業</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <p>基準</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <ul>
        <li>
          <p>每個工作區 256 個作用中註釋作業</p>
        </li>
      </ul>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>訓練與修正</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
      <p>訓練監督的機器學習模型，以從非結構化文字中擷取特定領域的資訊。</p><p>評估並改善監督的機器學習模型。</p>
      <p>您無法建立半監督或未監督的機器學習模型。</p>
      <p>您無法
執行廣泛的特性工程。</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <p>不適用</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <p>機器學習模型</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <ul>
        <li>
          <p>每個工作區 1 個機器學習模型</p>
        </li>
        <li>
          <p>每個工作區 10 個模型版本</p>
        </li>
        <li>
          <p>工作區數目上限依您的訂閱方案而定。</p>
        </li>
        <li>
          <p>每個月可以執行的訓練動作數目上限，依您的訂閱方案而定。</p>
        </li>
      </ul>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>發佈</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
      <p>發佈機器學習模型，以用於在其他 {{site.data.keyword.watson}} 應用程式中執行文字擷取。</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <p>不適用</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <ul>
        <li>
          <p>模型 ID（用於 {{site.data.keyword.nlufull}} 或 {{site.data.keyword.discoveryfull}}）</p>
        </li>
        <li>
          <p>ZIP 檔（用於 {{site.data.keyword.ibmwatson_notm}} Explorer）</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <p>若要部署至 {{site.data.keyword.watson}} 服務，您必須知道 {{site.data.keyword.cloud_notm}} 服務空間及實例名稱。</p>
    </td>
  </tr>
</table>

### 規則型模型

<table summary="此表格提供規則型模型之輸入、輸出及限制的摘要。">
  <caption>表 3. 規則型模型</caption>
  <tr>
    <th style="vertical-align:bottom; text-align:left" id="d25459e509">
作業</th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e511">
一般用法</th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e513">
支援的輸入格式</th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e515">
支援的輸出格式</th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e517">
限制及需求</th>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e509">
      <p>規則編輯器</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e511">
      <p>建立或上傳文件至規則編輯器，以從中定義類別、正規表示式及規則。</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e513">
      <ul>
        <li>
          <p>純文字（在編輯器中新增）</p>
        </li>
        <li>
          <p>UTF-8 格式的 CSV 檔</p>
        </li>
        <li>
          <p>從「所有」文件集複製</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e515">
      <p>無</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e517">
      <ul>
        <li>
          <p>每個工作區 1 個規則型模型</p>
        </li>
        <li>
          <p>每個文件 5,000 個字元</p>
        </li>
        <li>
          <p>每個工作區 100 個文件</p>
        </li>
        <li>
          <p>文件標題的大小上限是 256 個字元</p>
        </li>
        <li>
          <p>每個工作區 200 個規則</p>
        </li>
        <li>
          <p>每個工作區 400 個類別</p>
        </li>
        <li>
          <p>每個工作區 100 個正規表示式群組</p>
        </li>
        <li>
          <p>每個正規表示式群組 100 個正規表示式項目</p>
        </li>
        <li>
          <p>每個正規表示式項目 1,000 個字元</p>
        </li>
        <li>
          <p>每個工作區 5 個規則型模型版本</p>
        </li>
      </ul>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e509">
      <p>發佈</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e511">
      <p>發佈規則型模型，以用於在其他 {{site.data.keyword.watson}} 應用程式中執行型樣識別。</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e513">
      <p>不適用</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e515">
      <ul>
        <li>
          <p>模型 ID（用於 {{site.data.keyword.nlufull}} 或 {{site.data.keyword.discoveryfull}}）</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e517">
      <p>若要部署至 {{site.data.keyword.watson}} 服務，您必須知道 {{site.data.keyword.cloud_notm}} 服務空間及實例名稱。</p>
    </td>
  </tr>
</table>
