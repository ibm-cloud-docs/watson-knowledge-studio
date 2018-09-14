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

此文件適用於 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}。若要查看舊版 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 的文件，[請按一下此鏈結 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/docs/services/knowledge-studio/team.html){: new_window}。
{: tip}

# 組合團隊
{: #team}

建立模型需要來自主題專家、專案經理，以及可瞭解並解譯統計模型之使用者的輸入。您必須針對需要登入的每一個人，在 {{site.data.keyword.knowledgestudioshort}} 中新增使用者。
{: shortdesc}

**附註**：只有「標準」方案及「超值」方案才能具有多位使用者。「精簡」方案限制為一位使用者。當您作為唯一使用者時，為該人員指派具有最高許可權的角色（admin 角色）。

## 開始之前

- 確定您使用支援的瀏覽器。如需相關資訊，請參閱[瀏覽器需求](/docs/services/watson-knowledge-studio/system-requirements.html)。
- [建立 {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/tutorials-create-project.html#instance) 的實例。
- 如果您已註冊「標準」或「超值」方案，請從 {{site.data.keyword.cloud_notm}} **管理**標籤中，邀請其他使用者加入您的組織，您想要將他們新增為 {{site.data.keyword.knowledgestudioshort}} 中的使用者。如需邀請使用者的相關資訊，請參閱[邀請使用者及指派存取權 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/docs/iam/iamuserinv.html){: new_window}。

  **重要事項**：確保受邀使用者具有 Cloud Foundry 開發人員角色。如需相關資訊，請參閱 [Cloud Foundry 存取權 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/docs/iam/cfaccess.html){: new_window}。

## 關於本作業

一般而言，您會新增使用者來填入註釋人員及專案經理的角色。如需說明，請參閱 [{{site.data.keyword.knowledgestudioshort}} 中的使用者角色](/docs/services/watson-knowledge-studio/roles.html)。

**附註：**

- 如果您註冊了「精簡」方案，則無法將其他人新增至您的 {{site.data.keyword.knowledgestudioshort}} 實例。而是，在啟動 {{site.data.keyword.knowledgestudioshort}} 時，會將您新增至實例，並授與 admin 角色。在 admin 角色中，您可以執行許多功能，這些功能通常由指派給不同角色的不同人員執行。您可以測試來自領域不同區域的專家如何合作，以建置機器學習模型或規則型模型。
- 第一個啟動 {{site.data.keyword.knowledgestudioshort}} 的使用者會被授與 {{site.data.keyword.knowledgestudioshort}} 實例的 admin 角色。此作業假設您是在註冊方案之後第一個啟動 {{site.data.keyword.knowledgestudioshort}} 的人員，這表示您具有 admin 角色。

## 新增 {{site.data.keyword.knowledgestudioshort}} 中的使用者

將 {{site.data.keyword.cloud_notm}} 組織中的使用者新增至 {{site.data.keyword.knowledgestudioshort}}。

若要將使用者新增至 {{site.data.keyword.knowledgestudioshort}} 實例，請執行下列動作：

1. 使用您的 {{site.data.keyword.ibmid}} 登入「[{{site.data.keyword.cloud_notm}} 儀表板」![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net){: new_window}，然後啟動 {{site.data.keyword.knowledgestudioshort}}。
1. 按一下**設定**圖示，然後按一下**管理服務詳細資料**。
1. 在**管理員使用者**區段中，輸入您要新增之使用者的 {{site.data.keyword.ibmid}}。
1. 選取您要提供給使用者的角色。如需可用角色的說明，請參閱 [{{site.data.keyword.knowledgestudioshort}} 中的使用者角色](/docs/services/watson-knowledge-studio/roles.html)。

  **附註**：在指派使用者角色之後，您無法將這些使用者角色降級，因此，在指派 admin 角色及專案經理角色時，請確定您瞭解每一個角色所能執行的作業。

1. 按一下**新增**。

## 升級使用者角色

將使用者新增至 {{site.data.keyword.knowledgestudioshort}} 之後，您可以將較低的角色升級為較高的角色。必須將下述角色指派給使用者，才能執行個別作業。

**附註**：只有「標準」方案及「超值」方案才能具有多位使用者。「精簡」方案限制為一位已具有最高角色 (admin) 的使用者。

> **注意：不允許從較高的角色降級為較低的角色。**

若要升級 {{site.data.keyword.knowledgestudioshort}} 使用者的角色，請執行下列動作：

1. 使用您的 {{site.data.keyword.ibmid}} 登入「[{{site.data.keyword.cloud_notm}} 儀表板」![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net){: new_window}，然後啟動 {{site.data.keyword.knowledgestudioshort}}。
1. 從右上角導覽功能表中，按一下**設定** 圖示 ![「設定」圖示](images/settings.png)，然後按一下**管理服務詳細資料**。「服務詳細資料」頁面的**管理使用者**區段，會列出屬於這個 {{site.data.keyword.knowledgestudioshort}} 實例之使用者的所有使用者 ID。
1. 尋找您要變更的使用者名稱，然後按一下**編輯**鏈結。
1. 按一下使用者的角色，選擇您要將該使用者升級為哪個角色。如需可用角色的說明，請參閱 [{{site.data.keyword.knowledgestudioshort}} 中的使用者角色](/docs/services/watson-knowledge-studio/roles.html)。

  **重要事項：**您必須建立工作區、建立使用者與文件集的關聯，並在具有註釋人員角色的使用者可以看到 {{site.data.keyword.knowledgestudioshort}} 應用程式中列出的任何工作區之前，將註釋作業指派給使用者。在使用者登錄之後，盡快設定工作區，以在第一次存取應用程式時，讓他們可以看到您的工作區。您可能想要在設定工作區之後通知使用者，讓他們知道他們可以開始註釋文件。

1. 選用項目：當您完成管理 {{site.data.keyword.knowledgestudioshort}} 中的使用者時，請關閉 Web 瀏覽器來結束此階段作業。{{site.data.keyword.knowledgestudioshort}} 使用者介面不會提供明確登出的動作。

## 取消啟動使用者帳戶

稍後，如果您要移除使用者，請遵循先前的步驟來開啟「服務詳細資料」頁面。從使用者 ID 清單中，尋找您要移除的使用者，然後按一下**取消啟動**。

> **注意**：如果使用者獲指派文件以進行註釋，且您已取消啟動其帳戶，則其註釋會受到影響。如果取消啟動的使用者所進行的註釋未升級成基準，則會刪除那些註釋。

### 相關作業

[建立及指派註釋集](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projdocsets)
