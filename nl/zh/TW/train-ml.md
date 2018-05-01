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

此文件適用於 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}。若要查看舊版 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 的文件，[請按一下此鏈結 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/docs/services/knowledge-studio/train-ml.html){: new_window}。
{: tip}

# 訓練機器學習模型
{: #train-ml}

在 {{site.data.keyword.knowledgestudiofull}} 中，建立機器學習模型涉及訓練機器學習模型，以及評估在註釋測試資料及盲目資料時的模型執行程度。
{: shortdesc}

## 建立機器學習模型
{: #wks_madocsets}

建立機器學習模型時，請選取要用來訓練模型的文件集，並指定要用作訓練資料、測試資料及盲目資料的文件百分比。

### 關於本作業

藉由探索效能度量值，您可以識別用來改善模型正確性的方式。

> **限制：**每個 {{site.data.keyword.knowledgestudioshort}} 實例每次只能訓練三個機器學習註釋程式。如果您的實例包含多個工作區，而且正在其他工作區中訓練之機器學習註釋程式的數目，總計已有 3 個，則在其他訓練程序完成之前，您要在工作區中訓練機器學習模型的要求將排入佇列。

### 程序

若要建立機器學習模型，請執行下列動作：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理者身分登入，並選取您的工作區。
1. 選取**模型管理** > **效能**。
1. 驗證已核准所有文件集，並且已透過裁定解決所有註釋衝突。只有已透過裁定或核准變成基準的文件，才能用來訓練模型。
1. 按一下**訓練並評估**。
1. 選用項目：若要指定您要如何配置文件集中要由系統層次訓練集、測試集或盲目集使用的文件，請按一下**編輯設定**。

    請參閱[文件集管理](/docs/services/watson-knowledge-studio/improve-ml.html#wks_mamanagedata)，以協助判定要套用哪些比例。

1. 選用項目：將您要機器學習模型在訓練期間使用的所有字典，與字典項目的實體類型相關聯。

    如果已建立字典預先註釋程式，則您已執行此步驟。請按一下**重複使用針對字典預先註釋程式定義的對映**，以重複使用或定義新的對映。

    此模型會使用字典詞彙的類型資訊，作為在訓練期間其考慮的眾多語言分析特性中的一個特性。

1. 按一下**訓練**來訓練模型，或按一下**訓練並評估**來訓練模型、評估機器學習模型所新增的註釋，以及分析效能統計資料。

    > **重要事項：**訓練機器學習模型可能需要數分鐘或幾小時的時間，視存在的人工註釋數目及所有文件中的總字數而定。

1. 選取您要用於訓練模型的文件集。

    > **附註：**文件集必須至少包含 10 個已註釋的文件。

1. 在建立模型之後，請選取下列其中一個動作：

    <table border="1" frame="hsides" rules="rows" cellpadding="4" cellspacing="0" summary="此表格中的每一列說明一個選項。" class="simpletable choicetable choicetableborder">
      <thead><tr><th id="d33883e137-option" valign="bottom" align="left" class="ncol thleft thbot">選項</th>
          <th id="d33883e137-desc" valign="bottom" align="left" class="ncol thleft thbot">說明</th></tr></thead>
      <tbody><tr class="strow chrow"><td valign="top" headers="d33883e137-option" id="d33883e139" class="stentry choption ncol"><p class="p wrapper"><strong>日誌</strong></p></td>
          <td valign="top" headers="d33883e137-desc d33883e139" class="stentry chdesc ncol"><p class="p wrapper">檢視日誌檔，以查看是否發生任何問題。</p></td>
        </tr>
        <tr class="strow chrow"><td valign="top" headers="d33883e137-option" id="d33883e144" class="stentry choption ncol"><p class="p wrapper"><strong>詳細資料</strong></p></td>
          <td valign="top" headers="d33883e137-desc d33883e144" class="stentry chdesc ncol"><p class="p wrapper">檢視註釋效能統計資料、變更您要用於訓練及測試模型的文件集，以及建立模型構件的 Snapshot 版本。</p></td>
        </tr>
        <tr class="strow chrow"><td valign="top" headers="d33883e137-option" id="d33883e149" class="stentry choption ncol"><p class="p wrapper"><strong>匯出</strong></p></td>
          <td valign="top" headers="d33883e137-desc d33883e149" class="stentry chdesc ncol"><p class="p wrapper">將 <code>ZIP</code> 檔案匯出至本端系統，其中包含要在機器學習運行環境中執行之模型所需的元件。</p></td>
        </tr>
      </tbody>
    </table>

## 評估模型所新增的註釋
{: #wks_matest}

您可以將註釋人員所新增之註釋的基準視圖與模型所新增的註釋進行比較。

### 程序

若要評估模型所新增的註釋，請執行下列動作：

1. 選取**模型管理** > **效能** > **訓練並評估**。即會顯示「訓練/測試/盲目集」頁面。
1. 對訓練集或測試集按一下**檢視基準**，以查看透過預先註釋和註釋人員所新增的註釋。即會開啟基準編輯器。按一下以開啟個別文件，並查看提及項目、關係及互相參照之提及項目的註釋方式。
1. 在**效能**頁面上，按一下**檢視解碼結果**，以查看機器學習模型新增至測試集中之文件的註釋。只有在您評估模型之後，才能使用此按鈕。藉由檢視結果，您可以查看在測試資料中，機器學習模型標示為提及項目、關係及互相參照之提及項目的程度。
1. 如果您要變更訓練、測試與盲目資料集之間的文件劃分方式，請按一下**效能** > **訓練並評估** > **編輯設定**。例如，如果起始結果似乎可接受，則您可能想要增加測試集中的文件數，以進一步測試機器學習模型的結果。您可以變更基於不同用途自動劃分文件的比率，也可以選取特定文件集作為訓練資料、測試資料及盲目資料。
1. 如果您進行任何變更，請按一下**訓練並評估**來重新訓練模型，並重新評估註釋。

## 刪除機器學習模型
{: #wks_madelete}

您無法刪除機器學習模型。

您可以刪除用來開發模型的工作區，但無法刪除模型本身。刪除模型並不是最佳方法。請改為更新或取代用來訓練模型的構件。即使模型並未產生您預期的結果，您仍可以繼續改進。每次建立新版本時，即會重新建置模型。您可以編輯字典及類型系統之類的構件，並選擇在訓練下一版本時使用不同的註釋集。
