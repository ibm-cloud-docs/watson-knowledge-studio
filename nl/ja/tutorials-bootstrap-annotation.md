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

この文書は、{{site.data.keyword.cloud}} 上の {{site.data.keyword.knowledgestudiofull}} に関するものです。 以前のバージョンの {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 向けの資料を参照するには、[このリンクをクリック ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/docs/services/knowledge-studio/tutorials-bootstrap-annotation.html){: new_window} してください。
{: tip}

# 文書に事前アノテーションを付ける
{: #wks_tutboot_intro}

このチュートリアルは、文書に事前アノテーションを付ける方法を理解するのに役立ちます。事前アノテーション付けを行うと、ヒューマン・アノテーションのアノテーション・プロセスが自動実行されます。
{: shortdesc}

## 学習目標
{: #objectives}

このチュートリアルを完了すると、機械学習モデルを使用して文書に事前アノテーションを付ける方法が分かります。

このチュートリアルを完了するには、約 5 分かかります。 このチュートリアルに関連する他の概念を調べると、完了までの時間が長くなる可能性があります。

## 始めに
{: #prereqs}

- サポートされているブラウザーを使用していることを確認してください。 詳しくは、『[ブラウザーの要件](/docs/services/watson-knowledge-studio/system-requirements.html)』を参照してください。
- [{{site.data.keyword.knowledgestudioshort}}の開始](/docs/services/watson-knowledge-studio/tutorials-create-project.html)が正常に完了しています。これにはワークスペースの作成、タイプ・システムの作成、辞書の追加が含まれます。
- [機械学習モデルの作成](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html)が正常に完了しています。
- Admin または Project Manager のいずれかの役割のユーザー ID を、少なくとも 1 つ持っている必要があります。 ユーザー役割については、[{{site.data.keyword.knowledgestudioshort}} のユーザー役割](/docs/services/watson-knowledge-studio/roles.html)を参照してください。

## 結果
{: #results}

このチュートリアルを完了すると、部分的にアノテーションが付けられた文書のセットが作成されます。 その後、文書をヒューマン・アノテーターに割り当てて、アノテーション作業を完了することができます。

## 演習 1: 機械学習モデルを使用した新規文書の事前アノテーション付け
{: #wks_tutboot_ml}

この演習では、機械学習モデルを使用して {{site.data.keyword.knowledgestudioshort}} で文書に事前アノテーションを付ける方法について学習します。

### この作業について
{: #wks_tutboot_ml_about}

機械学習モデルのトレーニングをした後、機械学習モデルを使用して、コーパスに追加する新規文書に事前アノテーションを付けることができます。

> **注意:** 人間によってアノテーションが付けられていても、まだグランドトゥルースに追加されていない文書に対しては、事前アノテーターを実行しないでください。 実行すると、現在のすべてのアノテーションが文書から除去されます。

このチュートリアルでは、`documents-ml.csv` ファイルを使用して 2 番目の文書セットを追加することができます。 `documents-new.csv` ファイルを再追加しないでください。再追加すると、グランドトゥルース内に文書の重複が生じます。 重複があると、以下の問題が発生します。

- 各文書のアノテーションが一致しない場合、機械学習モデルの品質が低下します。
- 各文書のアノテーションが一致する場合、重複したファイルに対する機械学習モデルが過学習されます。

文書の事前アノテーション付けについて詳しくは、[アノテーションのブートストラッピング](/docs/services/watson-knowledge-studio/preannotation.html)を参照してください。事前アノテーション付けの付加的な方式についても記載されています。

### 手順
{: #wks_tutboot_ml_procedure}

1. 管理者として {{site.data.keyword.knowledgestudioshort}} にログインします。
1. ワークスペースにさらに文書をアップロードします。 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/documents-ml.csv" download>`documents-ml.csv` <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン" title="外部リンク・アイコン" class="style-scope doc-content"></a> ファイルを使用できます。

    ワークスペースへの文書の追加について詳しくは、[アノテーション用の文書の追加](/docs/services/watson-knowledge-studio/documents-for-annotation.html)を参照してください。

1. `documents-ml.csv` ファイルを基本セットとして使用するアノテーション・セットを作成し、管理者 (自分) に割り当てます。

    以下のステップを完了して新しい文書に事前アノテーションを付けた後、アノテーション・セットを表示して、機械学習モデルによってどのように文書にアノテーションが付けられたかを確認できます。一般に、アノテーション・セットは 1 人以上のヒューマン・アノテーターに割り当てます。 アノテーション・セットの作成と割り当てについて詳しくは、[アノテーション用の文書の追加](/docs/services/watson-knowledge-studio/documents-for-annotation.html)を参照してください。

1. 新しい文書に事前アノテーションを付けるには、**「機械学習モデル (Machine Learning Model)」** > **「バージョン (Versions)」**をクリックしてから、**「このモデルを実行 (Run this model)」**をクリックします。
1. コーパスに追加した文書セット、`documents-ml.csv` を選択し、**「実行」**をクリックします。
1. 事前アノテーションが完了したら、作成したアノテーション・セットを含むヒューマン・アノテーション・タスクを作成します。

    アノテーション・タスクの作成について詳しくは、[アノテーションのセットアップ](/docs/services/watson-knowledge-studio/annotate-documents.html)を参照してください。

1. 機械学習モデルによって新しい文書に適用されたアノテーションを表示するには、アノテーション・タスクを開きます。

    新しい文書に機械学習モデルによる事前アノテーション付けが行われたので、ヒューマン・アノテーションで必要な時間が減ります。ヒューマン・アノテーターによるアノテーションの追加について詳しくは、[文書のアノテーション付け](/docs/services/watson-knowledge-studio/user-guide.html)を参照してください。

### 結果
{: #wks_tutboot_ml_results}

機械学習モデルを使用して新規文書セットに事前アノテーションを付けることにより、それらの文書のヒューマン・アノテーション・タスクを迅速に処理できます。
