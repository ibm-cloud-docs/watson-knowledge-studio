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

此文件適用於 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}。若要查看舊版 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 的文件，[請按一下此鏈結 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/docs/services/knowledge-studio/tutorials-bootstrap-annotation.html){: new_window}。
{: tip}

# 引導註釋
{: #wks_tutboot_intro}

本指導教學協助您瞭解如何預先註釋文件，這可簡化註釋人員的註釋工作。
{: shortdesc}

## 學習目標

在完成本指導教學之後，您將知道如何使用機器學習模型來預先註釋文件。

大約需要 5 分鐘來完成本教學指導。如果您要探索與本指導教學相關的其他概念，將需要更多時間才能完成。

## 開始之前

- 您使用的是支援的瀏覽器。如需相關資訊，請參閱[瀏覽器需求](/docs/services/watson-knowledge-studio/system-requirements.html)。
- 您已順利完成[指導教學：建立工作區](/docs/services/watson-knowledge-studio/tutorials-create-project.html)及[指導教學：建立機器學習模型](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html)。
- 您必須至少有一個使用者 ID 為 Admin 或 ProjectManager 角色。如需使用者角色的相關資訊，請參閱[組合團隊](/docs/services/watson-knowledge-studio/team.html)。

## 結果

在完成本指導教學之後，您將會有一組局部註釋的文件。然後，您可以將這些文件指派給註釋人員，以完成註釋工作。

## 課程 1：使用機器學習模型預先註釋新文件
{: #wks_tutboot_ml}

在本課程中，您將學習如何使用機器學習模型在 {{site.data.keyword.knowledgestudioshort}} 中預先註釋文件。

### 關於本作業

訓練機器學習模型之後，您可使用此模型來預先註釋您新增至語料庫的新文件。

> **注意：**請不要對已由人工註釋、但尚未新增至基準的文件，執行預先註釋程式。如果這樣做，將會刪除文件中的所有現行註釋。

在本指導教學中，您可以使用 `documents-sentcsv` 檔案來新增第二組文件。請不要再次新增 `documents-new.csv` 檔案，因為此新增會導致基準中出現重複文件。重複會造成下列問題：

- 如果每一個文件上的註釋不符，它們會降低機器學習模型的品質。
- 如果每一個文件上的註釋相符，它們會在重複的檔案上過度訓練機器學習模型。

### 程序

1. 以管理者身分登入 {{site.data.keyword.knowledgestudioshort}}。
1. 將更多文件上傳至工作區。您可以使用 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/documents-ml.csv" download>`documents-ml.csv` <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示" title="外部鏈結圖示" class="style-scope doc-content"></a> 檔案。

    如需如何上傳文件的詳細資料，請參閱[建立機器學習模型 > 新增文件以進行註釋](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#tut_lessml1)。

1. 使用 `documents-sentcsv` 檔案來建立註釋集。

    對於本指導教學，請將註釋集指派給您自己（管理者）。在執行機器學習模型來預先註釋新文件之後，您可以檢視註釋集，以查看機器學習模型如何預先註釋。一般而言，您可以將註釋集指派給一個以上註釋人員。如需建立註釋集的相關資訊，請參閱[建立機器學習模型 > 建立註釋集](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml2)。

1. 從**模型管理** > **版本**資訊看板中，選取**機器學習**標籤，然後按一下**執行此模型**。
1. 選取您已新增至語料庫的文件集 (`documents-sentcsv`)，然後按一下**執行**。
1. 在預先註釋完成之後，您可以建立人工註釋作業，並註釋新的預先註釋文件。

    如需建立作業及註釋文件的詳細資料，請參閱[建立機器學習模型 > 建立註釋作業](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml4)及[建立機器學習模型 > 註釋文件](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml5)。

    在此狀況下，人工註釋需要較少的時間，因為您已使用機器學習模型預先註釋文件。

### 結果

使用您的機器學習模型來預先註釋新文件集，您可以加快那些文件的人工註釋作業。
