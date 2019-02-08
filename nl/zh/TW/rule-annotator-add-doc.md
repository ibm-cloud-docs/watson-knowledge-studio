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

此文件適用於 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}。若要查看舊版 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 的文件，[請按一下此鏈結 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/docs/services/knowledge-studio/rule-annotator-add-doc.html){: new_window}。
{: tip}

# 新增文件以定義規則
{: #wks_rule_anno_add}

新增具有說明您要定義之規則類型的語言型樣的文件。
{: shortdesc}

將您為了定義規則而新增的文件與您為了註釋而新增的文件分開。其唯一目的就是要用於型樣的探勘範例。既不會將它們用於訓練，也不會下載它們。

## 將文件新增至規則編輯器的方法

- **以 UTF-8 格式編寫文字文件**

    您可以將說明型樣的文字直接新增至規則編輯器。您指定給文件的名稱長度不得超過 256 個字元。

- **上傳 CSV 檔**

    上傳包含文件文字的 CSV 格式檔案。

- **複製已匯入的文件以進行註釋**

    如果文件是基於註釋目的而匯入之文件集的一部分，且包含您要擷取為規則的型樣範例，則您可以將文件複製到規則編輯器。您對文件所做的任何變更都不會影響用於註釋之文件的原始版本。如需上傳文件的相關資訊，請參閱[將文件新增至工作區](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projadd)。

對於您複製或上傳的文件，請選擇包含不同型樣的文件，這有助於識別文件中的實體類型。
