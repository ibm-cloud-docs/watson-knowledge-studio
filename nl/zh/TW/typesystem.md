---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-19"

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

此文件適用於 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}。若要查看舊版 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 的文件，[請按一下此鏈結 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/docs/services/knowledge-studio/typesystem.html){: new_window}。
{: tip}

# 建立類型系統
{: #typesystem}

類型系統控制內容的註釋方式。
{: shortdesc}

## 類型系統
{: #wks_typesystem}

類型系統定義領域內容中有趣的事物，您想要使用註釋來標示這些事物。類型系統控制如何定義可以標示的實體類型來註釋內容，以及如何標示不同實體之間的關係。模型程序管理程式通常會與您領域的主題專家合作，以定義類型系統。

在 {{site.data.keyword.knowledgestudioshort}} 中，您可以從頭開始建立類型系統，或上傳現有類型系統。若要快速啟動工作區，您可能要上傳已針對類似領域建立的類型系統。然後，您可以編輯類型系統，以新增或移除實體類型，或重新定義關係類型。

提供根據 *KLUE* 類型系統的範例類型系統，供您與 {{site.data.keyword.knowledgestudioshort}} 指導教學搭配使用。KLUE 代表 Knowledge from Language Understanding and Extraction，是由 {{site.data.keyword.IBM_notm}} Research 根據新聞文章集合的分析所衍生的。您可以從<a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/en-klue2-types.json" download>這裡 <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示" title="外部鏈結圖示" class="style-scope doc-content"></a> 下載範例 KLUE 類型系統。

諸如冶金、地質學、市場情報、生命科學、電子健康記錄和腫瘤學等領域的許多產業，都出版領域專用術語的字典或本體論。請考量參照此類型的資源，以瞭解您可能想要在自己的類型系統中定義實體類型的概念。

### 提及項目
{: #wks_typesystem__wks_typesystemS2}

提及項目是您在領域資料中視為相關的任何文字範圍。例如，在關於汽車的類型系統中，出現的詞彙諸如`安全氣囊`、`Ford Explorer` 及`兒童防制系統` 可能都是相關的提及項目。

### 實體類型
{: #wks_typesystem__wks_typesystemS3}

實體類型是您對實際事物進行分類的方式。實體提及項目是該類型的事物範例。例如，`President Obama` 提及項目可以註釋為 `PERSON` 實體類型。提及項目 `{{site.data.keyword.IBM_notm}}` 可以註釋為 `ORGANIZATION` 實體類型。實體通常是名詞，但也可以是動詞，只要動詞對於基於將使用類型系統的應用程式目的而進行的擷取很重要。例如，對於關於汽車的類型系統，`EVENT_CRASH` 可能是有效的實體類型，因此，可以註釋句子 `The car hit the barrier.` 中的 `hit` 這個字。

註釋工作區的目標是要在文件中使用每一個提及項目所屬的事物類型來註釋每一個提及項目。在依實體類型將提及項目分類之後，標示的文字範圍即稱為實體。

您使用 {{site.data.keyword.knowledgestudioshort}} 建置的類型系統可包括下列實體類型屬性。這些屬性可協助限定文字中的提及項目，但機器學習模型不會將其標示為實體類型。例如，如果實體類型 `ORGANIZATION` 具有稱為 `COMMERCIAL` 的實體子類型，則 `COMMERCIAL` 不會自行標示為實體類型。

- **角色**

    依出現提及項目的上下文限定提及項目。例如，在聲明 `the students went to France` 中的提及項目 `France` 是以實體類型 `GPE` 加以標示，因為 `France` 是地理政治實體。但是，因為此上下文中的 `France` 也是旅行學生的目的地，所以會藉由新增屬性來限定實體類型，在此情況下，指的是角色 `LOCATION`。對於另一個範例，提及項目 `Lawyers` 可能是以實體類型 `PEOPLE` 進行標示，也可能藉由角色 `OCCUPATION` 進行標示。

- **實體子類型**

    將實體類型進一步分類。例如，實體類型 `ORGANIZATION` 可能包括子類型 `COMMERISY`、`GOMENT`、`MILITARY` 及 `EDUCATION`。

- **提及項目類型**

    依特定詞性限定提及項目：
    - **NAM**：此提及項目是專有名稱，例如人員名稱或組織名稱。
    - **NOM**：此提及項目是名詞（一般名詞），例如*公司* 或*總裁*。
    - **PRO**：此提及項目是代名詞，例如*他*、*我們* 或*它*。
    - **NONE**：其他三種提及項目類型，沒有一個適用。

- **提及項目類別**

    藉由指出提及項目是特定、一般，還是否定來限定提及項目：
    - **SPC**：此提及項目是特定的，通常包括英文單字 *the*，例如 *the book* 或 *the hurricane occurred in September*。在這些範例中，提及項目 *book* 及 *hurricane* 將以屬性 **SPC** 進行註釋。
    - **GEN**：此提及項目是一般的，例如 *a book* 或 *hurricanes usually occur in the fall*。在這些範例中，提及項目 *book* 及 *hurricanes* 將以屬性 **GEN** 進行註釋。
    - **NEG**：此提及項目是否定的，例如 *no book* 的參照。當您訓練模型時，演算法可以同時從負面及正面範例中學習，因此務必標示這兩種類型的提及項目。

### 關係類型
{: #wks_typesystem__wks_typesystemS4}

關係類型定義兩個實體之間的二進位排序關係。如需關係提及項目存在，文字必須明確定義關係，並將兩個實體的提及項目連結在一起，而且必須在單一句子內進行。例如，句子 `Mary works for {{site.data.keyword.IBM_notm}}` 是 `employedBy` 關係類型的文字證明。

對於部分關係類型，實體提及項目的順序至關重要。例如，`employedBy` 關係類型容許實體類型 `PERSON` 或 `PEOPLE` 作為關係中的第一個提及項目，而 `ORGANIZATION` 或 **GPE** 作為第二個提及項目，但不是其他方法。`Mary` `employedBy` `{{site.data.keyword.IBM_notm}}` 是有效的關係。`{{site.data.keyword.IBM_notm}}` `employedBy` `Mary` 則不是。對於某些關係類型，例如 `spouseOf`、`colleague` 或 `sibling`，順序並不重要。當您定義順序並不重要的關係類型時，最佳作法是將資訊新增至註釋準則，以規則化表示式類型的使用方式。注意這類對稱關係的慣例是，指出在文字中第一個出現的實體提及項目應該是關係中的第一個提及項目。

**相關概念**：

[從其他工作區上傳資源](/docs/services/watson-knowledge-studio/exportimport.html)

## 將類型系統新增至工作區
{: #wks_projtypesys}

在開始任何註釋作業之前，您必須先建立或上傳類型系統。

### 關於本作業

下列命名規則適用於類型系統項目：

- 名稱不得包含空格。
- 在新增至類型系統的值中，只使用下列英數 ASCII 字元及底線字元：`A` 到 `Z`、`a` 到 `z`、`0` 到 `9`。
- 實體或關係類型名稱中的第一個字元必須是字母。
- 實體類型名稱長度不得超過 64 個字元。
- 關係類型名稱長度不得超過 128 個字元。

依照慣例，實體類型名稱是以大寫字元 (`ORGANIZATION`) 指定，而關係類型名稱是以駝峰式大小寫 (`employedBy`) 來指定。但是，這個慣例是選用的。

### 程序

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理者或專案經理身分登入，開啟**資產** > **實體類型**頁面。
1. 選擇下列其中一種方法來建立類型系統：

    - 上傳現有類型系統：

        1. 在**實體類型**標籤上，按一下**上傳**。

            如果您先前從 {{site.data.keyword.knowledgestudioshort}} 工作區下載類型系統，則會以 `JSON` 格式下載類型系統。您可以上傳此類型系統，以快速開始建立工作區。如需詳細資料，請參閱[從其他工作區上傳資源](/docs/services/watson-knowledge-studio/exportimport.html)。

            > **附註：**不論類型系統的原點為何，其中的項目都必須符合先前列出的命名規則。

        1. 新增、編輯及刪除實體類型和關係類型，其方式與您從頭開始建立類型系統時所做的方式相同。

    - 從頭開始建立類型系統：

        1. 在**實體類型**標籤上，按一下**新增實體類型**。
        1. 指定敘述性實體類型名稱，請記住實體類型是一種標籤，用於註釋領域內容中的重要文字範圍（提及項目）。保持簡短的名稱與代表性，讓註釋人員可以輕鬆地記住它。

            您也可以選擇性地定義實體類型的角色及子類型：
            - 角色可協助在出現提及項目的上下文中限定實體類型。例如，提及項目 `Software Engineer` 可能是以實體類型 `PEOPLE` 進行標示，而且在此上下文中，藉由角色 `OCCUPATION` 進行標示。如需相關資訊，請參閱[何時定義角色](/docs/services/watson-knowledge-studio/typesystem.html#wks_typesystem_roles)。
            - 子類型可協助將實體類型進一步分類。例如，實體類型 `GOVERNMENT` 可能具有 `MILITARY` 及 `CIVILIAN` 子類型。

            > **附註：**藉由定義實體的角色或子類型，您可以向將在註釋時建立類型資訊與提及項目之關聯的人員提供其他選項。註釋人員可以套用一個註釋，只指定實體類型，或指定實體類型加上您現在所定義的角色或子類型。

            嘗試定義足夠的實體類型，以擷取您要註釋的主要概念，但不要擷取太多實體類型，讓註釋人員難以正確地套用標籤。

        1. 按一下**提及項目類別**及**提及項目類型**，以檢視預設提及項目類別和提及項目類型。您無法編輯這些值。

            屬性的目的在於協助依每一個提及項目所屬的事物類型來標示每一個提及項目。提及項目類型指出提及項目是名稱、名詞，還是代名詞，而提及項目類別則指出提及項目是特定、一般，還是否定。

        1. 開啟**資產** > **關係類型**頁面，指定兩個提及項目彼此之間的關係。

            關係類型中第一個與第二個實體之間的順序通常是相關的。例如，`PERSON` 實體可以是 `ORGANIZATION` 實體或地理政治實體 (**GPE**) 的員工，例如 `Mary` `employedBy` `{{site.data.keyword.IBM_notm}}`，但人員無法雇用組織及地理政治實體。當註釋人員按一下基準編輯器中的實體時，可用關係類型的清單是由類型系統中定義的項目控制。

            請不要定義關係屬性。機器學習模型不會使用它們。此模型僅使用關係類型及順序，會忽略關係屬性。

        1. 請使用**編輯**及**刪除**圖示來修改實體類型及其關聯的關係類型，或從類型系統中刪除實體類型或關係類型。

            如果您刪除關係類型定義中使用的實體，則也會刪除關係類型定義。

**相關作業**：

[在不失去人工註釋的情況下修改類型系統](/docs/services/watson-knowledge-studio/improve-ml.html#wks_projtypesysmod)

## 類型系統建立準則
{: #wks_typesys_guidelines}

{{site.data.keyword.knowledgestudioshort}} 中任何類型系統的目的在於定義如何註釋文字範圍。如果您選擇從頭開始建立類型系統，請遵循以下這些準則。

專注在建立實體類型及關係類型的庫存，以涵蓋將使用此類型系統之應用程式所需的資訊。不涵蓋不需要的事物。不要分割類型或進行應用程式不需要的區別。例如，如果來源文件包含 `Murder on the Orient Express made headlines` 這個句子，則您如何定義實體類型以擷取句子中的重要資訊，取決於將使用您利用類型系統所建置之模型的應用程式類型。

- 若為文學應用程式，您可以建立擷取下列資訊的類型：

    ```
               [NOVEL][CRITICAL_RECEPTION]
    ```
    {: screen}

    ```
    [Murder on the Orient Express][made headlines]
    ```
    {: screen}

- 若為公共安全應用程式，您可以建立下列類型：

    ```
    [EVENT_CRIME][LOCATION]
    ```
    {: screen}

    ```
      [Murder] on the [Orient Express] made headlines
    ```
    {: screen}

結構通常是基於從中擷取資訊之文件的特徵，但應該一律根據應用程式實際將透過那些文件使用的資訊進行調節。例如，您可以建立一個應用程式，以從醫療記錄中獲得見解。若要建置類型系統，請開始查看病患記錄，以明白必須擷取的資訊類型。病患記錄可能全都包含了一個說明病患午餐吃什麼的欄位。不過，如果應用程式不使用該資訊，請不要將它新增至類型系統。在決定省略時，請認識到這表示患者記錄的這些區段將保持為未註釋狀態。這是沒問題的，甚至是預期的。

提及項目會註釋文字範圍；它們不會取代文字。類型系統不是領域的本體。預期有一般實體類型，例如 `MEDICATION_NAME`，而不是具有每一種藥物類型的實體類型。文件文字將繼續包含特定的藥物名稱。將只是利用識別其類型的註釋來加強它，這可讓您更容易以程式化的方式尋找及擷取資訊。

開始時，請定義 10 到 40 個實體類型及關係類型。如果將在工作區工作的註釋人員在領域中不是高度專業化的人員，請留在低端範圍。不要定義超過 50 個。

在您的團隊開始任何人工註釋作業之前，計劃會花費大量時間來定義類型系統。當團隊開始註釋文件時，從小型文件集開始，可能不超過 50 個。最初只註釋提及項目、檢查結果，並視需要修正您的註釋準則及類型系統。當提及項目註釋的結果符合您的要求時，請繼續註釋關係及互相參照。

進行基礎工作來定義一組實體類型及提及項目註釋準則時，請避免將大量氣力投入在註釋關係提及項目上。提及項目變更將復原關係註釋工作。請花一些時間來定義一組關係類型及其容許的實體類型配對，以在完成實體類型庫存之前，先考量關係類型需求。

預期類型系統會隨著嘗試對其進行註釋之人員的經歷而發展。如果您在建立人工註釋作業之後修訂類型系統，則必須決定是否要將變更套用至每一個作業。如果您套用變更，則註釋人員必須重新造訪他們先前所註釋的文件。

測試模型時，您可以檢閱統計資料，其會顯示實體類型與關係類型在範例文件中發生的頻率。請務必檢閱這些統計資料。為了確保應用程式收到足夠的上下文，以正確地註釋大型文件集合，您的測試資料必須包括最重要實體類型與關係類型的大型取樣。

> **重要事項：**在訓練第一個模型之後，您可能需要根據效能統計資料來進行修改。不過，若要為機器註釋建立可靠的統計模型，在開始大規模的註釋作業之前，您希望類型系統盡可能接近最終類型系統。

## 何時定義角色
{: #wks_typesystem_roles}

使用角色可讓您定義更精確的實體類型。

每一個您新增的實體都有一個角色。除非您予以變更，否則角色名稱會與實體名稱相同。您可以選擇為實體定義不同角色，以擷取更細微的提及項目用法。角色所套用的單字或詞組實際上是實體類型的範例，但在句子中，它扮演另一種實體類型的角色。例如，在詞組 `the White House vetoed the bill` 中，如果我們同時註釋實體類型 `FACILITY` 及角色 `ORGANIZATION` 或 `PERSON`，則可以擷取更精確地 `White House` 的意義。White House 是建築物 (`FACILITY`)，但在此建構中代表政府 (`ORGANIZATION`) 或美國總統 (`PERSON`)。實體類型加上角色標籤會在文字中建立更精確的提及項目分類。

角色也可以提供您用來擷取關係資訊的方法，而不必依賴使用重疊的提及項目。例如，您可能想要註釋文字 `31-year-old male`，讓它能夠擷取年齡屬性是 31 歲、性別屬性是男性的人員所參照的想法。藉由檢查此文字，我們判定 `31-year-old` 是年齡，`male` 是性別，它們一起表示某個人。您正在處理 3 個實體類型，基本上是：`AGE`、`GENDER` 及 `PERSON`。其表示方式是將 `31-year-old` 註釋為 `AGE`、將 `male` 註釋為 `GENDER`，而且因為遺漏 `PERSON` 的不同提及項目，但 `male` 已代表人員，所以單字 `male` 可以具有角色 `PERSON`。然後，您可以擷取 `PERSON` 角色與要擷取之人員的所有屬性之間的關係。例如，您可以在 `PERSON` 角色與 `AGE` 提及項目之間定義 `hasAttribute` 關係。因為您已將 `GENDER` 實體類型及 `PERSON` 角色類型標籤同時套用至相同的單字 `male`，所以您無法在兩者之間定義 `hasAttribute` 關係。不過，兩個標籤套用至相同提及項目的事實會彼此關聯。機器學習模型會考量此關聯，而您不必定義 hasAttribute 關係類型，以明確地叫出該關係。

類似範例是詞組 `2008 Ford F-150` 用作 `2008 Ford F-150 truck` 的速記。在這裡，`2008` 會註釋為 `MODEL_YEAR` 實體類型、`Ford` 註釋為 `MANUFACTURER` 實體類型，並將 `MODEL` 實體類型提供給 `F-150`。但是，由於遺漏單字 `truck`，`F-150` 也代表車輛。指出 `the F-150` 就像是指出 `the truck`。除了其 `MODEL` 實體類型外，您還可以將 `VEHICLE` 角色新增至提及項目來擷取該用法。然後，您可以在 `VEHICLE` 角色與 `MANUFACTURER` 和 `MODEL_YEAR` 實體提及項目之間定義 `hasAttribute` 關係。

### 角色與子類型有何不同？

實體子類型用於將實體類型的庫存分層為階層。例如，如果您在乎區分 40 個事物，但在邏輯上它們是 10 組 4（`VITALSIGN_BLOODPRESSURE`、`VITALSIGN_HEARTRATE`、`MEDICATION_DOSAGE`、`MEDICATION_FREQUENCY`），則您可以將它們建構為類型及子類型，這會產生更精簡的功能表，但卻會對標示程序帶來深度層次及麻煩事件。基於資訊擷取的目的，類型及子類型的組合可以與批次類型和不含子類型的批次類型交換。對照下，套用角色的單字或詞組是某個實體類型的範例，但它扮演另一種實體類型的角色，以及不是其他類型之子類型的角色。

### 如何處理角色？

{{site.data.keyword.knowledgestudioshort}} 機器學習模型會為其在來源文件中找到之實體的每一個提及項目定義分類器標籤，方法為連結實體類型與角色值。提供角色值時，您可以建立更精確的標籤。訓練資料中找到的某個標籤類型的每一個實例群組，會形成一組更一致的提及項目。挑戰在於，藉由選擇更精確，您還必須同意提供更多的訓練資料，以確保模型妥善執行。但是，您提供的訓練資料越多，模型就會越好。因此，如果您不在意執行其他註釋，則使用角色可讓您獲得更好的結果。

舉例來說，假設在來源文件中出現下列句子，而且我們想要擷取 `Acme`（其中 `Acme` 是著名的卡車製造商）、`sedan` 及 `truck` 作為類似實體，因為它們全都參照實體車輛：

- a) `The Acme crashed into the concrete barrier.`
- b) `The sedan crashed into the concrete barrier.`
- c) `The Acme A-160 truck crashed into the concrete barrier.`

您可以使用兩種方式來處理類型系統設計：

1. 定義兩個實體類型：`MANUFACTURER` 及 `VEHICLE`。對於 `MANUFACTURER` 實體，除了預設 `MANUFACTURER` 角色外，定義可以使用的 `VEHICLE` 角色。

    使用此類型系統時，這些句子會註釋如下：
    - a) `Acme` 會註釋為 `MANUFACTURER` 實體，但具有角色 `VEHICLE`，因為它它參照實際的車輛。因此，其內部標籤是 `MANUFACTURER-VEHICLE`。
    - b) `sedan` 會註釋為實體類型 `VEHICLE`。已自動指派 `VEHICLE` 角色，因為未定義其他角色。
    - c) `Acme` 會註釋為實體類型 `MANUFACTURER`，而 `truck` 會註釋為實體類型 `VEHICLE`。未指派任何角色，因此會使用預設角色。

1. 定義兩個沒有角色的實體類型：`MANUFACTURER` 及 `VEHICLE`。

    使用此類型系統時，這些句子會註釋如下：
    - a) `Acme` 會註釋為實體類型 `VEHICLE`。
    - b) `sedan` 會註釋為實體類型 `VEHICLE`。
    - c) `Acme` 會註釋為實體類型 `MANUFACTURER`，而 `truck` 會註釋為實體類型 `VEHICLE`。

兩個不同的類型系統的執行方式？假設註釋人員已註釋一組文件。在註釋傳遞之後，會在訓練語料庫中識別下列手動標示為實體的訓練事件：

- **類型系統 1**

    ```
    MANUFACTURER-MANUFACTURER 800 events
    MANUFACTURER-VEHICLE 200 events
    VEHICLE-VEHICLE 400 events
    ```
    {: screen}

- **類型系統 2**

    ```
    MANUFACTURER 800 events
    VEHICLE 200 + 400 = 600 events
    ```
    {: screen}

模型處理新文件時，很可能 `Acme` 大部分時間都標示為 `MANUFACTURER`，因為單字的拼寫是強大的功能，而且單字 `Acme` 可能定義在 `MANUFACTURER` 字典中。它會取得許多上下文，以不同方式標示它。如果我們使用類型系統 1，只有 200 個 `MANUFACTURER-VEHICLE` 訓練事件，當與類型系統 2 中的 600 個 `VEHICLE` 事件相比時，這是劣勢。不過，類型系統 1 中的訓練事件叢集全都相當一致，這可產生更好的效能。對於類型系統 2，`VEHICLE` 的一組 600 個訓練事件實際上是由兩個不交集的叢集所組成：一個包含參照實際車輛的製造商名稱，例如 `Acme` 及 `Ford`，另一個包含車輛類型，例如 `sedan`、`SUV` 及 `truck`。直覺上，這兩個叢集各自都是一致的，但藉由將它們混合在一起，這會降低訓練叢集，並呈現一個更難解決的問題。如果您繼續執行註釋，並新增更多訓練事件，則類型系統 1 中的效能會越來越好，然而，解決您使用類型系統 2 所得到的兩個不交集叢集的問題，並不會由於更多的訓練而改善。
