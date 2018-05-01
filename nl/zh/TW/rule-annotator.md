---

copyright:
  years: 2015, 2018
lastupdated: "2018-03-20"

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

此文件適用於 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}。若要查看舊版 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 的文件，[請按一下此鏈結 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/docs/services/knowledge-studio/rule-annotator.html){: new_window}。
{: tip}

# 規則
{: #rule-annotator}

建立一個可識別文件中型樣的規則型模型。使用規則來擷取文件中出現的型樣，並傳送基本實體類型的相關資訊。
{: shortdesc}

## 類別概觀

建構規則時，您可以使用類別來代表資訊類型。這些類別與實體類型類似。所以，為什麼不會在定義規則時使用實體類型呢？因為在建置規則時，您可以定義只用來建置其他更複雜類別的中介類別。這些中介類別僅供使用。它們本身並不好用。中介類別可搭配其他中介類別一起使用，以定義更有用且完整的類別。中介類別是必要的，但不是顯示為屬於類型系統的項目。若要讓規則型模型執行類似實體提及項目的預先註釋文件的有用作業，您必須將在規則建立期間所使用的複式類別對映至類型系統中的對等實體類型。

例如，您要一個能辨識人員姓名的模型。為了訓練機器學習模型來辨識人員的名稱，您可以在註釋集中以 `PERSON`
實體類型來註釋在文件中以各種格式所撰寫的許多不同名稱，然後訓練模型來辨識人員的名稱。若要建立規則型模型來辨識人員名稱，您可以定義一個規則，說明用來撰寫人員名稱的文字型樣。因此，您可以建立
`FirstName` 類別及 `LastName` 類別，然後使用這些中介類別來定義 `FullName` 類別。您可以定義條件來判斷
`FullName` 類別的位置是否與一般字首（例如 `Dr.`）及一般字尾（例如 `Jr.`）有關。使用規則型模型時，`FullName`
類別即會對映至 `PERSON` 實體類型。

避免將中介類別對映至您類型系統中之實體的另一個原因為：如果您以規則型模型預先註釋文件，然後將其新增至您的「基準」來訓練機器學習模型，您就不會想以其將產生重疊實體提及項目的這種方式來定義規則。例如，如果您要將中介類別 `FirstName`
及複式類別 `FullName` 同時對映至 `PERSON` 實體，則 `John Doe, Jr` 的出現項目會導致重疊提及項目。

## 規則編輯器工具

規則編輯器提供一些可協助您定義規則的工具。

- 字典

    新增字典並指派一個類別名稱給它。在字典中找到符合項目的任何單字，都會自動註釋已指派的類別。

- 正規表示式

    正規表示式 (regex) 是定義搜尋型樣的字元序列。規則編輯器中包括的 regex 工具可辨識遵循
`java.util.regex.Pattern` 語法的表示式。以下是基本範例：`[A-Z][a-z]*`：尋找大寫單字。

    `[A-Z]` 會比對任何大寫英文字母（A 到 Z），而 `[a-z]*` 會比對任何小寫英文字母（a 到 z）零次以上。星號 (*) 是定義重複設定（零次以上）的字元。

    請考量使用免費的 Web 型正規表示式公用程式，來協助您判斷要用來擷取要尋找之型樣的正確表示式。

    例如，您的文件可能有數個參照與下列詞組類似：

    ```
    35-year-old driver
    16-year-old learner
    ```
    {: screen}

    語法 `n-year-old x` 是典型代表人員的型樣。您可以定義正規表示式規則來尋找符合 `n-year-old x`
型樣的詞組，然後將它們註釋為 `PERSON` 實體提及項目。
