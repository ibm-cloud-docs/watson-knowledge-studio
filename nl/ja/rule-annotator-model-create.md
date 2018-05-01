---

copyright:
  years: 2015, 2018
lastupdated: "2018-03-26"

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

この文書は、{{site.data.keyword.cloud}} 上の {{site.data.keyword.knowledgestudiofull}} に関するものです。以前のバージョンの {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 向けの資料を参照するには、[このリンクをクリック ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/docs/services/knowledge-studio/rule-annotator-model-create.html){: new_window} してください。
{: tip}

# ルール・ベース・モデルの作成
{: #wks_rule_train}

ルールを定義した後、ルール・ベース・モデルを作成できます。
{: shortdesc}

## 手順

ルール・ベース・モデルを作成するには、以下のステップを実行します。

1. {{site.data.keyword.knowledgestudioshort}} 管理者またはプロジェクト管理者としてログインし、ワークスペースを選択します。
1. **「モデル管理 (Model Management)」** > **「バージョン (Versions)」** > **「ルール・ベース (Rule-based)」**タブを選択します。
1. タイプ・システムに含まれるエンティティー・タイプを、ルールの定義に使用した 1 つ以上のクラスにマップします。

  エンティティー・タイプがマップされたら、機械学習モデルを作成するプロセスの中で、[ルール・ベース・モデルをデプロイしたり](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html)、モデルを使用して[文書に事前にアノテーションを付けたり](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotrule)できます。

## ルール・ベース・モデルの削除
{: #wks_rule_delete_model}

ルール・ベース・モデルは削除できません。

ルール・ベース・モデルを開発するために使用したワークスペースは削除できますが、モデル自体を削除することはできません。モデルの削除は最良の方法ではありません。代わりに、モデルに定義されているルールを再作成してください。ルールを編集することで、ルール・ベース・モデルの動作が直接変更されます。
