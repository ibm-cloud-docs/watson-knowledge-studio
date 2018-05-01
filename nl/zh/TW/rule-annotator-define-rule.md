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

此文件適用於 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}。若要查看舊版 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 的文件，[請按一下此鏈結 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/docs/services/knowledge-studio/rule-annotator-define-rule.html){: new_window}。
{: tip}

# 定義規則
{: #wks_rule_creation}

使用規則編輯器來定義規則。
{: shortdesc}

## 關於本作業

避免讓多位使用者同時編輯規則、類別及正規表示式，因為這樣可能會導致非預期的改寫或複製。

## 程序

若要定義規則，請完成下列步驟：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理者或專案經理身分登入，並開啟**規則**頁面。
1. 按一下「文件」旁的加號 (+)，以新增文件。

    如需詳細資料，請參閱[新增文件以定義規則](/docs/services/watson-knowledge-studio/rule-annotator-add-doc.html)。

    例如，您可能會新增一個包含下列這一行文字且名為 `My Document` 的文件：

    ```
    A 50-year-old driver was driving the 2017 Example Horizon.
    ```
    {: screen}

1. 如果您計劃定義正規表示式或新增字典，請建立要與其相關聯的類別。

    1. 從**類別**畫面中，按一下「類別」旁的加號 (+)。
    1. 新增類別名稱。

        如果您將建立類別與正規表示式或字典的關聯，請考量命名類別，以讓您識別其來源。例如，如果您計劃使用正規表示式來定義句子中的數字型樣，您可以建立一個名為 AGE_REGEX 的類別。如果您計劃使用字典來註釋句子中的汽車製造商，您可以新增一個名為 MANUFACTURER_DICT 的類別。

        請記住下列命名規則：
        - 類別名稱中的第一個字元必須是字母。
        - 在新增至類別的值中，只使用下列英數 ASCII 字元及底線字元：A 到 Z、a 到 z、0 到 9。
        - 名稱不得包含空格。
        - 名稱長度不得超過 64 個字元。

1. 選用：若要快速註釋文件中的類別，您可以建立字典與規則編輯器的關聯。文件中與字典中的項目相符的詞彙，會自動註釋適當的類別。

    1. 按一下畫面中的**字典**標籤。

        即會顯示您所建立的任何字典。

        如果尚未新增字典，請從主要導覽列中開啟**字典**標籤來新增字典。如需相關資訊，請參閱[建立字典](/docs/services/watson-knowledge-studio/dictionaries.html)。

    1. 按一下字典，為其定義類別關聯，然後按一下**儲存**。

        例如，如果您有一個包含組織名稱的字典，您可以建立它與規則的關聯，並將 ORGANIZATION_DICT 類別指派給它。您的範例文件中所出現的任何組織名稱都會註釋為 ORGANIZATION_DICT 類別的實例。

    如果您稍後想要移除規則編輯器中的字典關聯，則可以移除類別對映。若要這樣做，請從下拉清單的頂端選擇空的選項。

1. 選用：若要定義正規表示式來協助您建構規則，請按一下導覽中的**正規表示式**。

    1. 按一下「正規表示式」旁的加號 (+)，以新增正規表示式。
    1. 命名正規表示式。例如，MyAgeRegex。

        名稱長度不得超過 64 個字元。

    1. 建立表示式與類別的關聯。例如，AGE_REGEX。
    1. 按一下**新增項目**。
    1. 新增表示式。

        例如，若要擷取代表年齡（最多 99 歲）的數字，您可以指定 `[0-9]{1,2}`。若要擷取時間的表示式，例如 *12:30 AM*，您可以指定此正規表示式：

        ```
        (1[0-2]|0?[1-9]):([0-5][0-9])(\s+[AaPp][Mm])?
        ```
        {: screen}

        您可以選擇性地變更單字記號數目的下限及上限。在英文中，記號通常相當於句子中以空格分隔的單字。不過，記號與單字不一定一對一相符；其他文字元素在某些情況下會被視為記號。例如，*50-year-old* 詞彙中的連字號每一個都計為一個記號，這表示此詞彙中使用的記號總數為 5。而文字 *12:30 PM* 包含 4 個記號。(`12 | : | 30 | PM`)

        按一下**新增**。

    1. 如果您要新增其他表示式，請重複前兩個步驟。
    1. 按一下**儲存**。

    即會關閉正規表示式編輯器，並會顯示文件。您應該會看到針對套用至想要與其相比對的文字的正規表示式所定義的類別。如果您沒有看到，請檢查您的表示式。可能需要予以修訂，使其符合您想要尋找的文字。

    ![顯示已選取 "Regex" 標籤的規則編輯器、與類別 "AGE_REGEX" 相關聯且稱為 "Age" 的正規表示式，以及顯示以黃色強調顯示文字 "50" 的文件。該強調顯示的文字與所建立的正規表示式相符。](images/rule_step3.jpg)

1. 若要定義規則，請按一下導覽中的**規則**。
1. 使用您要擷取為規則的型樣來開啟文件。例如，如果您已建立標題為 `My Document` 的文件，且範例文字包含詞組 `50-year-old`，請開啟該文件。
1. 從文件的文字中，選取說明您要擷取之型樣的字元。例如，您可以選取下列單字及連字號 (-)：

    ```
    50-year-old
    ```
    {: screen}

    選取字元之後，您就可以新增規則。

1. 按一下**規則**畫面中的加號 (+)。

    規則編輯器代表您選取作為兩層儲存格的文字。最上層的儲存格是您可在其中註釋基本記號的類別的位置。較低層的儲存格是您定義記號加入型樣的條件的位置。

    ![規則編輯器顯示在您選取文件中的文字並按一下「規則」畫面中的加號之後，「建立規則」畫面內容呈現的樣子。會顯示下列圖形元素：輸入詞彙 "AGE" 的「規則名稱」欄位、「建立規則」畫面及「類別」畫面。在「建立規則」畫面中，含虛線的儲存格沿著頂端顯示。針對所選文字的每一個記號顯示一個儲存格。在這些儲存格中，您可以註釋記號的類別。沿著「建立規則」畫面的底端，顯示含實線的儲存格。每一個儲存格都包含所選文字 "50-year-old" 的記號。記號包含 "50"、"-"（連字號）、"year"、"-" 及 "old"。每一個實線儲存格旁都有兩個圖示，您可用來調整單字或註釋的條件。](images/rule_step4.jpg)

1. 定義每一個記號加入型樣的條件。

    在底層儲存格中，按一下第一個記號以檢閱其條件。如果您要指出任何記號都可以用在型樣的現行位置，請按一下**開啟內容**，然後選取**容許任何記號**。按一下**關閉內容**。如果記號是一個正規表示式，例如範例中的 `AGE_REGEX`，則**容許任何記號**無法使用。

    > **附註：**當每一個儲存格的重複設定是 1 或更少時，可加入型樣中的群組儲存格數目上限為 15。群組儲存格包括單一記號、註釋或容許任何記號的記號。型樣中容許的記號總數上限為 20。定義型樣時，請考量每一個儲存格的重複設定。例如，當每一個儲存格的重複設定是 1 或更少時，您可以定義一個包括 15 個記號的型樣。但是，如果每一個儲存格的重複設定為 1 或更多時，則可在型樣中定義不超過 4 個的記號，因為對於每一個儲存格而言，記號最多可以重複 5 次。重複 5 次的四個記號可讓您達到最多 20 個的容許值。

    若要指出需要特定的記號類型，您可以定義下列的條件設定類型：
    - **重複設定**：指定現行記號必須內含在型樣中的次數。您可以變更重複設定，但每個記號只能指定一個重複設定。下表說明這些選項。

    <table cellpadding="4" cellspacing="0" summary="" border="1" class="simpletable">
      <tr class="sthead">
        <th valign="bottom" align="left" id="d27028e471" class="stentry thleft thbot">設定選項</th>
        <th valign="bottom" align="left" id="d27028e473" class="stentry thleft thbot">說明</th>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e471" class="stentry">
          <p class="p wrapper">必要（正好為 1）</p>
        </td>
        <td valign="top" headers="d27028e473" class="stentry">
          <p class="p wrapper">此記號必須存在於型樣中一次。依預設，會套用此選項，但可以變更。</p></td>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e471" class="stentry">
          <p class="p wrapper">重複 1 次以上</p>
        </td>
        <td valign="top" headers="d27028e473" class="stentry">
          <p class="p wrapper">此記號必須至少存在於型樣中一次，且可重複多次。</p>
        </td>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e471" class="stentry">
          <p class="p wrapper">重複 0 次以上</p>
        </td>
        <td valign="top" headers="d27028e473" class="stentry">
          <p class="p wrapper">此記號可以選擇性地在型樣中重複多次，但不一定要重複。</p>
        </td>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e471" class="stentry">
          <p class="p wrapper">出現 0 或 1 次</p>
        </td>
        <td valign="top" headers="d27028e473" class="stentry">
          <p class="p wrapper">這個記號是選用的。</p>
        </td>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e471" class="stentry">
          <p class="p wrapper">進階：_自訂_</p>
        </td>
        <td valign="top" headers="d27028e473" class="stentry">
          <p class="p wrapper">此記號必須在此型樣中重複此處所指定的次數。若要定義自訂重複設定，請按一下<b>開啟內容</b>，選取**進階**，然後選取您要定義的一或多個重複次數的確切數目。</p>
          <p class="note">
記號所容許的重複次數上限為 5。</p>
        </td>
      </tr>
    </table>

    - **特性設定**：必須至少定義其中一個特性設定。您可以新增其他特性，新增至符合此型樣的文字必須符合的條件數目。下表說明這些選項。

    <table cellpadding="4" cellspacing="0" summary="" border="1" class="simpletable">
      <tr class="sthead">
        <th valign="bottom" align="left" id="d27028e512" class="stentry thleft thbot">設定選項</th>
        <th valign="bottom" align="left" id="d27028e514" class="stentry thleft thbot">它的新增條件</th>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e512" class="stentry">
          <p class="p wrapper">文字</p>
        </td>
        <td valign="top" headers="d27028e514" class="stentry">
          <p class="p wrapper">必須符合此記號中的確切文字。依預設，會套用此選項。您可以移除它，但只有在您將不同設定新增為條件或套用任何記號設定時才能進行。</p>
        </td>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e512" class="stentry">
          <p class="p wrapper">長度</p>
        </td>
        <td valign="top" headers="d27028e514" class="stentry">
          <p class="p wrapper">必須符合此記號的字元長度。從第一個字元前面的 0 開始計算長度。</p>
        </td>
      </tr>
    </table>

    選項的其餘部分取決於記號的類型。

    - **不符合正規表示式或字典詞彙的未註釋記號**：這些設定可用於未註釋且不符合正規表示式或字典詞彙的記號。

    <table cellpadding="4" cellspacing="0" summary="" border="1" class="simpletable">
      <tr class="sthead">
        <th valign="bottom" align="left" id="d27028e535" class="stentry thleft thbot">設定選項</th>
        <th valign="bottom" align="left" id="d27028e537" class="stentry thleft thbot">說明</th>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e535" class="stentry">
          <p class="p wrapper">詞性</p>
        </td>
        <td valign="top" headers="d27028e537" class="stentry">
          <p class="p wrapper">必須是與此記號相同的詞性。下列是支援的類型：</p>
          <ul class="ul bullets">
            <li class="li">
              <p class="p wrapper">形容詞</p>
            </li>
            <li class="li">
              <p class="p wrapper">預先詞</p>
            </li>
            <li class="li">
              <p class="p wrapper">副詞</p>
            </li>
            <li class="li">
              <p class="p wrapper">連接詞</p>
            </li>
            <li class="li">
              <p class="p wrapper">限定詞</p>
            </li>
            <li class="li">
              <p class="p wrapper">感嘆詞</p>
            </li>
            <li class="li">
              <p class="p wrapper">名詞</p>
            </li>
            <li class="li">
              <p class="p wrapper">數字</p>
            </li>
            <li class="li">
              <p class="p wrapper">代名詞</p>
            </li>
            <li class="li">
              <p class="p wrapper">餘數</p>
            </li>
            <li class="li">
              <p class="p wrapper">動詞</p>
            </li>
          </ul>
        </td>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e535" class="stentry">
          <p class="p wrapper">詞目</p>
        </td>
        <td valign="top" headers="d27028e537" class="stentry">
          <p class="p wrapper">必須具有與此記號相同的詞目。</p>
        </td>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e535" class="stentry">
          <p class="p wrapper">字元類型</p>
        </td>
        <td valign="top" headers="d27028e537" class="stentry">
          <p class="p wrapper">必須具有與此記號相同的字元類型。下列是支援的類型：</p>
          <ul class="ul bullets">
            <li class="li">
              <p class="p wrapper">阿拉伯文：包含一連串的阿拉伯文字元</p>
            </li>
            <li class="li">
              <p class="p wrapper">中文數字：只包含中文數字</p>
            </li>
            <li class="li">
              <p class="p wrapper">子句結束標點符號：區隔某一個子句或句子與下一個子句或句子的標點符號字元</p>
            </li>
            <li class="li">
              <p class="p wrapper">漢字：包含漢字字元</p>
            </li>
            <li class="li">
              <p class="p wrapper">韓字：包含韓國韓字音節字元</p>
            </li>
            <li class="li">
              <p class="p wrapper">希伯來字：包含一連串希伯來字元</p>
            </li>
            <li class="li">
              <p class="p wrapper">平假名：包含日文平假名音節字元</p>
            </li>
            <li class="li">
              <p class="p wrapper">表意文字：包含表示構想或事物的表意文字或符號</p>
            </li>
            <li class="li">
              <p class="p wrapper">片假名：包含日文片假名音節字元</p>
            </li>
            <li class="li">
              <p class="p wrapper">小寫：只包含小寫英文字母</p>
            </li>
            <li class="li">
              <p class="p wrapper">數字：只包含數值字元</p>
            </li>
            <li class="li">
              <p class="p wrapper">標點符號：在文字中提供標點符號的一個以上字元</p>
            </li>
            <li class="li">
              <p class="p wrapper">音節：包含音節字元</p>
            </li>
            <li class="li">
              <p class="p wrapper">泰文：包含泰文字元</p>
            </li>
            <li class="li">
              <p class="p wrapper">首字母大寫：開頭為單一大寫英文字母，後面接著一個以上的小寫英文字母</p>
            </li>
            <li class="li">
              <p class="p wrapper">大寫：僅包含大寫英文字母的記號</p>
            </li>
          </ul>
        </td>
      </tr>
    </table>

    - **規則符合：**

    <table cellpadding="4" cellspacing="0" summary="" border="1" class="simpletable">
      <tr class="sthead">
        <th valign="bottom" align="left" id="d27028e617" class="stentry thleft thbot">設定選項</th>
        <th valign="bottom" align="left" id="d27028e619" class="stentry thleft thbot">說明</th>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e617" class="stentry">
          <p class="p wrapper">規則符合</p>
        </td>
        <td valign="top" headers="d27028e619" class="stentry">
          <p class="p wrapper">必須符合具名的類別。請記住，類別可能衍生自正規表示式、字典或規則。例如，如果這裡所指定的類別衍生自正規表示式，則此記號必須符合表示式的搜尋型樣。</p>
        </td>
      </tr>
    </table>

1. 如果記號具有從字典註釋或正規表示式比對而間接新增的註釋，您可以選擇型樣是需要含相同註釋類型的任何字還是改為註釋的實際基本字。

    在較低層儲存格中，您可以查看哪些儲存格內含在型樣中，因為有一條水平線會將它們彼此連接起來。在套用註釋的情況下，會進行分割。含原始單字的儲存格會顯示在含註釋標籤的儲存格下方。您可以按某一組儲存格或另一組儲存格來變更該行的路徑，從而變更內含在型樣中的儲存格。

    例如，您可以選擇讓型樣使用 50，而不是讓它符合年齡正規表示式。

    ![顯示編輯記號 "50"（其在規則中使用 "AGE_REGEX" 註釋）的「建立規則」畫面。依預設，會使用 "AGE_REGEX" 註釋，但您可以編輯型樣，以改用基本字 "50"。](images/rule_step5.jpg)

1. 設定型樣順序之後，您可以在文字中註釋記號。

    從最上層儲存格中，按一下代表您要註釋之記號的儲存格，然後將類別標籤套用至這些記號。若要選取多個儲存格，請按一下其中一個，按 **Shift** 鍵，然後按一下其他儲存格。

    將類別指派給選取的一或多個儲存格。如果您要指派的類別不存在，可以予以新增。在**指派類別**欄位中鍵入類別名稱，然後按 **Enter** 鍵。

    > **附註：**您無法為規則新增 10 個以上的類別。

    ![顯示按一下記號時所開啟的「指派類別」視窗的「建立規則」區段。該視窗會顯示一個欄位，您可以在其中輸入新類別的名稱，或從清單中選取現有類別。](images/rule_step6.jpg)

1. 命名規則。

    規則名稱長度不得超過 64 個字元。

1. 按一下「規則」畫面中的**儲存**，以儲存規則。
