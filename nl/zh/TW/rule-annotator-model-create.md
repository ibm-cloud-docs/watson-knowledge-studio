---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-19"

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

此文件適用於 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}。若要查看舊版 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 的文件，[請按一下此鏈結 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/docs/services/knowledge-studio/rule-annotator-model-create.html){: new_window}。
{: tip}

# 建立規則型模型
{: #wks_rule_train}

定義規則之後，您可以建立規則型模型。
{: shortdesc}

## 程序
{: #wks_rule_train_procedure}

若要建立規則型模型，請完成下列步驟：

1. 以 {{site.data.keyword.knowledgestudioshort}} 管理者或專案經理身分登入，並選取您的工作區。
1. 選取**規則型模型** > **版本** > **規則型模型**標籤。
2. 按一下**對映實體類型及類別**。
3. 將類型系統中的實體類型對映至您用來定義規則的一個以上類別。

  對映實體類型之後，您可以在建立機器學習模型的程序中，[部署規則型模型](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html)或用它來[預先註釋文件](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotrule)。

## 刪除規則型模型
{: #wks_rule_delete_model}

您無法刪除規則型模型。

您可以刪除用來開發規則型模型的工作區，但無法刪除模型本身。刪除模型並不是最佳方法。而是要重建針對它所定義的規則。編輯規則會直接變更規則型模型的行為。
