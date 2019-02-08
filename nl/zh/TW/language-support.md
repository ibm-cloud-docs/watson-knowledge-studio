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

此文件適用於 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}。如果要在 {{site.data.keyword.IBM_notm}} Marketplace 上查看舊版 {{site.data.keyword.knowledgestudioshort}} 的文件，[請按一下這個鏈結 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/docs/services/knowledge-studio/language-support.html){: new_window}。
{: tip}

# 語言支援
{: #language-support}

{{site.data.keyword.knowledgestudiofull}} 提供以數種語言訓練模型的支援。

支援多種語言不表示產品本身已翻譯。{{site.data.keyword.knowledgestudioshort}} 使用者介面、訊息及文件僅提供英文版本。
{: shortdesc}

您可以用下列語言來訓練模型：

- 英文（預設語言）
- 阿拉伯文
- 巴西葡萄牙文
- 簡體中文
- 荷蘭文
- 法文
- 德文
- 義大利文
- 日文
- 韓文
- 西班牙文

支援包括能夠新增這些語言的文件到工作區、新增字典、執行預先註釋、使用基準編輯器來註釋文件，以及訓練機器學習模型。選取語言時，系統會套用語言特定範本來處理字典項目、文字記號化及句子分段。如需系統如何處理不同語言的字典的相關資訊，請參閱[字典](/docs/services/watson-knowledge-studio/dictionaries.html#wks_dictionaries)。

> **附註：**規則編輯器和規則型模型無法處理雙向文字，因此無法與阿拉伯文文件搭配使用。

> **限制：**
>
> 因為基礎機器學習技術中的字元限制，類型系統中的項目不能包含空格，且只能包含下列 ASCII 字元：
>
> - A 到 Z 與 a 到 z
> - 0 到 9
> - 底線字元 _
>
> 也適用下列規則：
>
> - 名稱中的第一個字元必須是字母。
> - 實體類型名稱長度不能超出 64 個字元。
> - 關係類型名稱長度不能超出 128 個字元。
>
> 因此，例如，當註釋人員在基準編輯器中註釋日文時，可套用的實體類型和關係類型名稱不會是日文。

### 相關作業

[配置阿拉伯文的支援](/docs/services/watson-knowledge-studio/language-support-arabic.html)
