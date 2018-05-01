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

此文件適用於 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}。如果要在 {{site.data.keyword.IBM_notm}} Marketplace 上查看舊版 {{site.data.keyword.knowledgestudioshort}} 的文件，[請按一下這個鏈結 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/docs/services/knowledge-studio/exportimport.html){: new_window}。
{: tip}

# 從另一個工作區上傳資源
{: #exportimport}

若要加速建立模型，您可以上傳從另一個工作區下載的資源，諸如文件（具有或不具有基準註釋）、類型系統及字典。
{: shortdesc}

能夠分別下載及上傳不同資源，讓您能彈性地設計和建立模型。例如，您可能會建立一個工作區來設計類型系統並執行人工註釋，然後建立另一個工作區，可能是在另一個具有不同使用者的 {{site.data.keyword.knowledgestudioshort}} 實例中，來訓練機器學習模型。能夠上傳資源（包括由註釋人員建立的基準），讓此情境變為可能。

您無法下載及上傳機器學習模型。您可以改為從一個工作區下載用來建立模型的所有構件，然後將它們上傳至新的工作區。從新的工作區中，您可以再次執行訓練來重建模型。新模型應該會產生與原始模型類似的結果，因為它們是使用相同的一組構件來進行訓練。

您下載的檔案與作業系統無關。您下載及上傳檔案所在的 {{site.data.keyword.knowledgestudioshort}} 實例不需要執行相同版本的 Linux。

## 類型系統
{: #wks_exportimport_expimp_type}

若要下載類型系統，請開啟**資產 & 工具** > **實體類型**頁面，然後按**下載類型**。系統會建立一個名為 `types-ID.json` 的檔案，並提示您將檔案下載至本端系統。如果要在新工作區中使用這個類型系統，請開啟**實體類型**頁面，並上傳您下載的 `JSON` 檔。

## 字典
{: #wks_exportimport_expimp_dict}

若要下載一個以上的字典，請選取**資產 & 工具** > **預先註釋程式** > **字典**標籤，然後按**下載字典**。對於您下載的每一個字典，系統會建立一個名為 `dictionary name_timestamp.csv` 的檔案、將檔案結合成一個名為 `workspace name_dictionary_timestamp.zip` 的 `ZIP` 檔，並提示您將檔案下載至本端系統。您也可以開啟字典然後按**下載**，來下載個別的字典。無法下載您已上傳作為字典 CSV 檔的僅供預覽字典。

將下載的字典上傳至新的工作區之前，您必須先從舊工作區下載類型系統，並將它上傳至新的工作區。類型系統和字典必須源自相同的 {{site.data.keyword.knowledgestudioshort}} 工作區，且類型系統必須在您上傳字典之前就存在於新的工作區。

若要上傳字典，請開啟**字典**標籤，然後新增您下載的 `CSV` 檔，或上傳 `ZIP` 檔。

## 文件
{: #wks_exportimport_expimp_doc}

若要下載您新增至語料庫的文件，請開啟**資產 & 工具** > **文件** > **文件集**標籤，然後按**下載文件集**。系統會建立一個名為 `corpus-ID.zip` 的檔案，並提示您將檔案下載至本端系統。`ZIP` 檔包含語料庫中的所有文件。新增至註釋集的註釋會包含在 ZIP 檔中，但只有在已核准註釋集並提升為基準之後，才會包含在內。

> **限制：**已預先註釋的任何文件，在下載時會模糊成為無法閱讀的格式。即使是那些文件中由註釋人員新增的註釋也無法閱讀。

將包含基準的文件上傳至新的工作區之前，您必須先從舊工作區下載類型系統，並將它上傳至新的工作區。類型系統和文件必須源自相同的 {{site.data.keyword.knowledgestudioshort}} 工作區，且類型系統必須在您上傳基準註釋之前就存在於新的工作區。

若要上傳文件，請開啟新工作區中的**文件集**標籤，按一下**上傳文件集**，然後選取您下載的語料庫 `ZIP` 檔。指定在按一下**上傳**之前，要上傳的文件是要包含還是排除基準註釋。只會上傳在下載文件之前就已提升為基準的註釋。

**相關概念**：

[類型系統](/docs/services/watson-knowledge-studio/artifacts.html#wks_typesystem)

[字典](/docs/services/watson-knowledge-studio/artifacts.html#wks_dictionaries)

[機器學習註釋人員的文件](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_t_docs_intro)

[規則型註釋人員的文件](/docs/services/watson-knowledge-studio/rule-annotator-add-doc.html)
