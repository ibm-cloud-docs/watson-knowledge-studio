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

此文件適用於 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}。如果要在 {{site.data.keyword.IBM_notm}} Marketplace 上查看舊版 {{site.data.keyword.knowledgestudioshort}} 的文件，[請按一下這個鏈結 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/docs/services/knowledge-studio/language-support-arabic.html){: new_window}。
{: tip}

# 配置阿拉伯文的支援
{: #wks_langsupp_ar}

請閱讀這些準則，以瞭解在阿拉伯文文件中，{{site.data.keyword.knowledgestudioshort}} 如何處理阿拉伯文的字元定型和數字定型。

## 關於此作業

在字元定型方面，阿拉伯文字母沒有大寫字母，但是字母可以變更形狀，視其在字串中的位置以及周圍字母而定。不同的作業系統與字碼頁轉換程式會以不同的方式來處理字母定型。無定型的儲存是 Windows 系統的標準；{{site.data.keyword.knowledgestudioshort}} 假設阿拉伯文文字在儲存時沒有定型。如果您想要將定型文字上傳至 {{site.data.keyword.knowledgestudioshort}}，您必須先使用標準工具（例如 International Components for Unicode (ICU) API）將文字轉換為無定型形式，（請參閱 [http://icu-project.org/apiref/icu4j/com/ibm/icu/text/ArabicShaping.html ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://icu-project.org/apiref/icu4j/com/ibm/icu/text/ArabicShaping.html){: new_window} 的 ArabicShaping Class），將文字轉換為無定型形式，

> **重要事項：**在部分情況下，缺少適當的阿拉伯文字元定型，可能會導致內容在基準編輯器中的顯示不正確。

在數字定型方面，{{site.data.keyword.knowledgestudioshort}} 將數字定型視為儲存空間層次的內容，類似於阿拉伯文內容在 iOS 平台上的處理方式。由於大量的阿拉伯文內容是在像是 Windows 的平台上建立，這些平台將數字定型視為顯示層次的內容，因此您需要轉換內容，使數字定型成為儲存空間層次的內容，或是在使用 {{site.data.keyword.knowledgestudioshort}} 時使用 Firefox 瀏覽器。Firefox 支援在瀏覽器層次明確設定數字定型喜好設定的能力，並且會對瀏覽器中顯示的所有內容強制顯示適當的顯示畫面。

## 程序

若要在 Firefox 瀏覽器中配置數字定型，請執行下列動作：

1. 在瀏覽器 URL 欄位中，輸入 **about:config**。如果您看到 Firefox 的警告，請按一下忽略警告的動作，然後繼續。如需編輯 **about:config** 內容的相關資訊，請參閱 [http://kb.mozillazine.org/About:config_entries ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://kb.mozillazine.org/About:config_entries){: new_window}。
1. 在搜尋過濾器欄位中鍵入 `bidi`。
1. 選取 **bidi.numeral** 內容（它會控制數字的顯示方式），然後按 Enter 鍵。
1. 視需要變更此內容的值。例如，輸入 `3`，然後按一下**確定**。

    - **0**：名詞性的數字（預設值）
    - **1**：一般環境定義數字
    - **2**：北印度文環境定義數字
    - **3**：阿拉伯數字
    - **4**：北印度文數字

    > **重要事項：**使用 **bidi.numeral** 內容時，Firefox 會完全忽略網頁內容中特定數字字元的字碼點。

### 相關參考資訊

[多重語言支援](/docs/services/watson-knowledge-studio/language-support.html)
