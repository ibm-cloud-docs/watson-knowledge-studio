---

copyright:
  years: 2018
lastupdated: "2018-07-02"

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

# {{site.data.keyword.knowledgestudioshort}} 中的使用者角色
{: #roles}

{{site.data.keyword.knowledgestudiofull}} 角色用來組織一隊可建立機器學習或規則型模型的人員。
{: shortdesc}

## {{site.data.keyword.knowledgestudioshort}} 中角色的相關注意事項
{: #notes}

- {{site.data.keyword.knowledgestudioshort}} 中的使用者角色是在下列層次管理：
  - {{site.data.keyword.cloud}} 角色控制對 {{site.data.keyword.cloud_notm}} 服務的存取。{{site.data.keyword.knowledgestudioshort}} 使用 Cloud Foundry 來進行存取控制，這需要 {{site.data.keyword.knowledgestudioshort}} 使用者具備開發人員角色。如需相關資訊，請參閱 [Cloud Foundry 存取權 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/docs/iam/cfaccess.html){: new_window}。
  - {{site.data.keyword.knowledgestudioshort}} 角色控制對 {{site.data.keyword.knowledgestudioshort}} 功能的存取，如這個頁面所述。
- 不需要 {{site.data.keyword.knowledgestudioshort}} 角色，即可建立 {{site.data.keyword.knowledgestudioshort}} 的實例。不過，當人員建立 {{site.data.keyword.knowledgestudioshort}} 的實例時，第一個啟動 {{site.data.keyword.knowledgestudioshort}} 的使用者獲派 {{site.data.keyword.knowledgestudioshort}} admin 角色。
- 若要管理工作區，管理者必須將專案經理指派給工作區。
- 管理者和專案經理可以執行註釋人員的角色，但他們必須以註釋人員必須指派給註釋集的方式指派給註釋集。
- 指派之後，就無法將使用者角色從較高層次的許可權降級至較低層次的許可權。管理者無法降級至專案經理或註釋人員，而專案經理無法降級至註釋人員。如需新增使用者、升級角色及取消啟動使用者帳戶的相關資訊，請參閱[組合團隊](/docs/services/watson-knowledge-studio/team.html)。

## 角色說明
{: #descriptions}
下表說明 {{site.data.keyword.knowledgestudioshort}} 角色。依最高到最低許可權層次的順序來列出角色。

|角色|說明|
|------|-------------|
|Admin|負責管理作業，其中包括管理使用者、資源耗用及每月計費。在大型團隊設定中，管理者很少參與模型開發程序。|專案經理|負責指派給她或他的工作區的整體組織。作業包括建立類型系統、管理資產、管理註釋工作、評估機器學習模型，以及部署模型。這個角色中的使用者需要產業主題專業知識，因為他們會建立類型系統、教導註釋人員如何正確套用類型系統，以及評估模型的品質。|
|註釋人員|在指派給她或他的訓練文件中，執行實體提及項目及關係提及項目的標籤。工作會指派給註釋人員，並由專案經理監視。只要註釋人員沒有產業主題專門知識，專案經理就會教導他們如何正確套用類型系統。|
{:caption="表 1. 角色說明" caption-side="top"}

## 角色許可權
{: #permissions}

若要比較每一個角色的許可權，請參閱下表。每一列會列出一個許可權。如果角色具有該許可權，則角色直欄會以勾號 (&checkmark;) 標示。

|許可權|Admin|專案經理|註釋人員|
|------------|-------|-----------------|-----------------|
|管理使用者存取及角色| &checkmark; |  |  |
|管理工作區| &checkmark; |  |  |
|建立類型系統及註釋準則| &checkmark; | &checkmark; |  |
|上傳訓練文件| &checkmark; | &checkmark; |  |
|管理規則| &checkmark; | &checkmark; |  |
|預先註釋文件| &checkmark; | &checkmark; |  |
|管理註釋作業| &checkmark; | &checkmark; |  |
|使用人工註釋來解決註釋衝突（*裁定*）| &checkmark; | &checkmark; |  |
|訓練與評估機器學習模型| &checkmark; | &checkmark; |  |
|部署及取消部署模型至運行環境服務| &checkmark; | &checkmark; |  |
|執行文件註釋| &checkmark; | &checkmark; | &checkmark; |
{:caption="表 2. 角色許可權" caption-side="top"}
