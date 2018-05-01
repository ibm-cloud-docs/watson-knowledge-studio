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

この文書は、{{site.data.keyword.cloud}} 上の {{site.data.keyword.knowledgestudiofull}} に関するものです。以前のバージョンの {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 向けの資料を参照するには、[このリンクをクリック ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/docs/services/knowledge-studio/tutorials-bootstrap-annotation.html){: new_window} してください。
{: tip}

# アノテーションのブートストラッピング
{: #wks_tutboot_intro}

このチュートリアルは、文書に事前アノテーションを付ける方法を理解するのに役立ちます。この事前アノテーション付けにより、ヒューマン・アノテーターのアノテーション・ジョブが簡素化されます。
{: shortdesc}

## 学習目標

このチュートリアルを完了すると、機械学習モデルを使用して文書に事前アノテーションを付ける方法が分かります。

このチュートリアルを完了するには、約 5 分かかります。このチュートリアルに関連する他の概念を調べると、完了までの時間が長くなる可能性があります。

## 始めに

- サポートされているブラウザーを使用していることを確認してください。詳しくは、『[ブラウザーの要件](/docs/services/watson-knowledge-studio/system-requirements.html)』を参照してください。
- 『[チュートリアル: ワークスペースの作成](/docs/services/watson-knowledge-studio/tutorials-create-project.html)』、および『[チュートリアル: 機械学習モデルの作成](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html)』が正常に完了しました。
- Admin または ProjectManager のいずれかの役割のユーザー ID を、少なくとも 1 つ持っている必要があります。ユーザー役割については、『[チームのアセンブル](/docs/services/watson-knowledge-studio/team.html)』を参照してください。

## 結果

このチュートリアルを完了すると、部分的にアノテーションが付けられた文書のセットが作成されます。その後、文書をヒューマン・アノテーターに割り当てて、アノテーション作業を完了することができます。

## 演習 1: 機械学習モデルを使用した新規文書の事前アノテーション付け
{: #wks_tutboot_ml}

この演習では、機械学習モデルを使用して {{site.data.keyword.knowledgestudioshort}} で文書に事前アノテーションを付ける方法について学習します。

### この作業について

機械学習モデルのトレーニングをした後、機械学習モデルを使用して、コーパスに追加する新規文書に事前アノテーションを付けることができます。

> **注意:** 人間によってアノテーションが付けられていても、まだグランドトゥルースに追加されていない文書に対しては、事前アノテーターを実行しないでください。実行すると、現在のすべてのアノテーションが文書から除去されます。

このチュートリアルでは、`documents-ml.csv` ファイルを使用して 2 番目の文書セットを追加することができます。`documents-new.csv` ファイルを再追加しないでください。再追加すると、グランドトゥルース内に文書の重複が生じます。重複があると、以下の問題が発生します。

- 各文書のアノテーションが一致しない場合、機械学習モデルの品質が低下します。
- 各文書のアノテーションが一致する場合、重複したファイルに対する機械学習モデルが過学習されます。

### 手順

1. 管理者として {{site.data.keyword.knowledgestudioshort}} にログインします。
1. ワークスペースにさらに文書をアップロードします。               <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/documents-ml.csv" download>`documents-ml.csv`<img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン" title="外部リンク・アイコン" class="style-scope doc-content"></a> ファイルを使用できます。

    文書をアップロードする方法について詳しくは、『[機械学習モデルの作成 > アノテーション用の文書の追加](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#tut_lessml1)』を参照してください。

1. `documents-ml.csv` ファイルを使用してアノテーション・セットを作成します。

    このチュートリアルでは、アノテーション・セットを自分自身 (管理者) に割り当てます。機械学習モデルを実行して新規文書に事前アノテーションを付けた後、アノテーション・セットを表示して、機械学習モデルによってどのように文書に事前アノテーションが付けられたかを確認できます。一般に、アノテーション・セットは 1 人以上のヒューマン・アノテーターに割り当てます。アノテーション・セットの作成について詳しくは、『[機械学習モデルの作成 > アノテーション・セットの作成](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml2)』を参照してください。

1. **「モデル管理」** > **「バージョン」**サイドバーから**「機械学習」**タブを選択して、**「このモデルを実行」**をクリックします。
1. コーパスに追加した文書セット、`documents-ml.csv` を選択し、**「実行」**をクリックします。
1. 事前アノテーションが完了したら、ヒューマン・アノテーション・タスクを作成し、新規の事前アノテーション付き文書にアノテーションを付けることができます。

    タスクの作成および文書のアノテーション付けについて詳しくは、『[機械学習モデルの作成 > アノテーション・タスクの作成](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml4)』および『[機械学習モデルの作成 > 文書のアノテーション付け](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml5)』を参照してください。

    このシチュエーションでは、機械学習モデルを使用して文書に事前アノテーションを付けたので、ヒューマン・アノテーションに要する時間が短縮されます。

### 結果

機械学習モデルを使用して新規文書セットに事前アノテーションを付けることにより、それらの文書のヒューマン・アノテーション・タスクを迅速に処理できます。
