---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-20"

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

此文件適用於 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}。若要查看舊版 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 的文件，[請按一下此鏈結 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/docs/services/knowledge-studio/backup-restore.html){: new_window}。
{: tip}

# 備份及還原資料
{: #backup-restore}

如果您需要備份及還原 {{site.data.keyword.knowledgestudioshort}} 的工作區，請執行這些作業。此外，如果您需要以手動的方式，將資料從某個 {{site.data.keyword.knowledgestudioshort}} 實例移轉至另一個實例（例如，當您從 {{site.data.keyword.IBM_notm}} Marketplace 上的實例移轉至 {{site.data.keyword.cloud_notm}} 上的實例時），請執行這些作業。
{: shortdesc}

_手動資料移轉_ 是指備份某個實例的資料，並在另一個實例上將其還原的程序。

**附註**：{{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud_notm}} 使用_工作區_ 一詞，而 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 使用_專案_ 一詞。功能是相同的。只是術語不同。

若要備份及還原您的資料，請完成下列步驟：

1. [瞭解哪些資料可以備份](#data)
1. [準備進行備份](#prepare)
1. [從現行實例中下載構件](#export)
1. [在新的實例上重建工作區](#recreateproj)
1. [還原工作區資料](#restoredata)
1. [還原模型](#restoremodels)
1. [還原所有不完整的註釋作業](#restoretasks)

## 可備份的資料
{: #data}

下列構件可手動備份及移轉：

- 可編輯的字典
- 類型系統
- 已核准的基準文件集

下列類型的構件不可手動備份及移轉：

- 進行中的人工註釋文件
- 註釋作業
- 模型及 Snapshot
- 唯讀字典

## 準備進行備份
{: #prepare}

若要準備進行備份及還原資料，請完成下列步驟：

1. 完成正在工作區中進行的任何工作。

    - > **重要事項：**完成所有進行中的註釋作業。只能備份已註釋、裁定以及核准並升級成基準的文件。如果您未完成註釋工作，將會遺失所有進行中但未完全完成的註釋工作。

    - 如果您已建立註釋作業來追蹤您要執行的工作，但沒有任何註釋工作已開始執行，要到還原工作區之後才會開始執行，則請建立一份未完成註釋作業清單。請務必記下您已匯入但尚未新增至基準的文件集。此外，請記下您指派要註釋每一個文件集的人員。您將需要在還原工作區之後，重新上傳這些文件集並重建註釋作業。

1. 瞭解記號器用法。

    對於機器學習模型，依預設工作區會使用機器學習型記號器。如果您是使用字典型記號器，且您的特殊需求是要繼續使用該記號器，則可以將工作區配置成在還原後使用字典型記號器。如需相關資訊，請參閱[記號器](/docs/services/watson-knowledge-studio/create-project.html#wks_tokenizer)。

1. 管理模型資源。

    您的模型、其版本及 Snapshot 資料皆無法移轉。您用來訓練這些構件的資源（唯讀字典除外）則可以移轉。因此，在移轉之後，您可以重建模型。產生的模型會與移轉之前所產生的模型執行相同的作業，因為用於訓練的資源都相同。

    **注意**：如果您有已部署的模型，且您計劃在備份之後刪除工作區，請從部署中撤銷該模型。從備份還原工作區之後，您可以重建及重新部署模型。如需取消部署模型的相關資訊，請參閱[取消部署機器學習模型](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model)及[取消部署規則型模型](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model)。

    **請注意，如果您無法從部署中撤銷模型，則結果是_孤立_ 已部署的模型。孤立的已部署模型會繼續在您的每月帳單上產生費用。**

1. 管理唯讀字典資訊。

    無法移轉唯讀的字典。找出唯讀字典的匯入來源，您就可以在移轉之後，將其重新上傳至您的工作區。

1. 建立現行使用者角色的清單。

    **附註**：此為選用步驟。一般而言，當工作區跨實例移轉，且新工作區必須與原始工作區相同時，才會執行此步驟。如果您只要將工作區資料移轉至新的工作區，則可以跳過此步驟。

    如果您要在不同的實例之間移轉工作區，請考量建立您所備份之實例的使用者及其角色清單。具有 Admin 角色的人員可以從「使用者帳戶管理」頁面列印該清單。在新實例上重建工作區之後，具有 Admin 角色的人員必須新增使用者並指派其角色。

    如需角色的相關資訊，請參閱 [{{site.data.keyword.knowledgestudioshort}} 中的使用者角色](/docs/services/watson-knowledge-studio/roles.html)。

1. 記下工作區資訊。

    當您仍有現行實例的存取權時，請針對您要移轉的每一個工作區，記下下列資訊：
    - 工作區名稱
    - 工作區說明
    - 工作區擁有者
    - 語言
    - 如果您有任何不完整的註釋作業（因為無法備份或移轉它們），請記下指派給工作區中不完整作業的註釋人員。另外，也請記下註釋作業詳細資料，例如，作業名稱、到期日以及哪些文件集指派給哪些使用者。

## 下載構件
{: #export}

請針對您要移轉的每一個工作區，下載下列構件。將它們儲存在安全位置，以於稍後可以將它們從該安全位置上傳到新的實例中。

- 類型系統
- 字典

  **附註**：
    - 只會下載可編輯的字典。您無法下載唯讀字典。
    - 對於字典，不會移轉實體類型對映。在還原這些構件之後，您必須視需要將字典對映至實體類型。

- 文件

  請參閱[從其他工作區上傳資源](/docs/services/watson-knowledge-studio/exportimport.html)，以取得如何下載這些構件以匯入至新工作區的相關資訊。

## 重建工作區
{: #recreateproj}

**附註**：在這個步驟中，語言是必須符合原始（已下載）工作區設定的唯一設定。其餘設定可與原始工作區的設定不同。

將前一個實例中的下列資訊複製到新的實例，以重建每一個工作區：

- 工作區名稱
- 工作區說明
- 文件的語言（此設定必須符合原始工作區中的設定）
- 如果您先前在工作區中使用字典型記號器，且需要繼續使用它，則必須在建立工作區時，指定您要使用字典型記號器，而非預設記號器。如需選項的相關資訊，請參閱[記號器](/docs/services/watson-knowledge-studio/create-project.html#wks_tokenizer)。

  若要使用字典型記號器，請展開「建立工作區」視窗的「進階選項」區段（位於 {{site.data.keyword.IBM_notm}} Marketplace 的「建立工作區」視窗），並變更記號器設定。

## 還原工作區資料
{: #restoredata}

在重建工作區之後，請上傳之前下載的構件：

1. 從先前建立的類型系統備份上傳類型系統。如需詳細資料，請參閱[從其他工作區上傳資源](/docs/services/watson-knowledge-studio/exportimport.html)。

  **附註**：您必須先上傳類型系統，才能上傳您從已備份工作區中移動的任何其他構件。

1. 從先前建立的字典備份上傳字典。如需詳細資料，請參閱[從其他工作區上傳資源](/docs/services/watson-knowledge-studio/exportimport.html)。

  如果您在舊版工作區中使用任何唯讀字典，請將它們從其原始來源重新上傳至這個工作區。

1. 對於字典預先註釋程式，請建立字典與實體類型的關聯。沒有實體類型對映的字典在您預先註解文件時不會套用註釋。

1. 將下載自舊版工作區的文件上傳至這個版本的工作區。
   如需詳細資料，請參閱[從其他工作區上傳資源](/docs/services/watson-knowledge-studio/exportimport.html)。

## 還原模型
{: #restoremodels}

此時，這個新實例現在可以使用在舊版（已備份）工作區中用來訓練模型的所有構件。

若要重新部署您已在先前實例中部署的機器學習模型，請完成下列步驟：

1. [訓練機器學習模型](/docs/services/watson-knowledge-studio/train-ml.html)。

  **附註**：不要在已移轉至這個工作區的已註釋文件上執行預先註釋程式，因為這會遺失這些文件中由註釋人員所新增的註釋。

1. 建立模型之後，請重新進行部署。如需詳細資料，請參閱[使用機器學習模型](/docs/services/watson-knowledge-studio/publish-ml.html)。

若要重新部署您已在先前實例中部署的規則型模型，請完成下列步驟：

1. [建立規則型模型](/docs/services/watson-knowledge-studio/rule-annotator-model-create.html)。
1. [部署規則型模型](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html)。

## 還原不完整的註釋作業
{: #restoretasks}

如果您有任何已建立但在前一個工作區中未完成的註釋作業，請完成下列步驟來重建不完整的註釋作業：

1. [上傳](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projadd)任何尚未註釋但想要新增至基準以繼續改善模型的文件。
1. 從新匯入且未註釋的文件中，[建立註釋集](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projdocsets)。
1. [重建註釋作業](/docs/services/watson-knowledge-studio/annotate-documents.html#wks_hatask)。為作業提供相同的名稱、適當的到期日，並將註釋集指派給適當的註釋人員。
