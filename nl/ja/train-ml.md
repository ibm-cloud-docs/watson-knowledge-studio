---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-29"

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

この文書は、{{site.data.keyword.cloud}} 上の {{site.data.keyword.knowledgestudiofull}} に関するものです。 以前のバージョンの {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 向けの資料を参照するには、[このリンクをクリック ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/docs/services/knowledge-studio/train-ml.html){: new_window} してください。
{: tip}

# 機械学習モデルのトレーニング
{: #train-ml}

{{site.data.keyword.knowledgestudiofull}} における機械学習モデルの作成には、機械学習モデルのトレーニングと、テスト・データおよびブラインド・データに対してアノテーションを付けたときのモデルのパフォーマンス評価が含まれます。
{: shortdesc}

## 機械学習モデルの作成
{: #wks_madocsets}

機械学習モデルを作成するときは、モデルのトレーニングに使用する文書セットを選択し、トレーニング・データ、テスト・データ、およびブラインド・データとして使用する文書のパーセンテージを指定します。

### この作業について
{: #wks_madocsets_about}

パフォーマンス・メトリックを検討することで、モデルの精度を高めるための方法を識別できます。

> **制限:** {{site.data.keyword.knowledgestudioshort}} インスタンスごとに一度にトレーニングできる機械学習モデルは 3 つに制限されます。 インスタンスに複数のワークスペースが含まれており、他のワークスペース内でトレーニング中の機械学習モデルの数が既に合計で 3 つある場合、ワークスペース内で機械学習モデルをトレーニングする要求は、他のトレーニング・プロセスが完了するまでキューに入れられます。

### 手順
{: #wks_madocsets_procedure}

機械学習モデルを作成するには、以下のようにします。

1. {{site.data.keyword.knowledgestudioshort}} 管理者としてログインし、ワークスペースを選択します。
1. **「機械学習モデル」** > **「パフォーマンス」**を選択します。
1. すべての文書セットが承認済みであること、およびすべてのアノテーションの競合が判定によって解決済みであることを確認してください。 判定または承認によってグランドトゥルースになった文書のみをモデルのトレーニングに使用できます。
1. **「トレーニングと評価 (Train and evaluate)」**をクリックします。
1. オプション: システム・レベルのトレーニング・セット、テスト・セット、またはブラインド・セットで使用する文書を文書セットから割り振る方法を指定するには、**「設定の編集 (Edit settings)」**をクリックします。

    適用する比率を決定する方法については、[文書セット管理](/docs/services/watson-knowledge-studio/improve-ml.html#wks_mamanagedata)を参照してください。

1. オプション: トレーニング時に機械学習モデルで使用する辞書を、辞書項目のエンティティー・タイプに関連付けます。

    辞書の事前アノテーターを作成した場合、このステップは既に実行済みです。 **「辞書の事前アノテーターに定義されているマッピングを再使用する (Reuse mapping that is defined for dictionary pre-annotator)」**をクリックして、そのマッピングを再使用するか、新しいマッピングを定義します。

    モデルは、トレーニング中に多くの言語分析上の特徴を検討しますが、その特徴の 1 つとして辞書用語のタイプ情報を使用します。

1. モデルをトレーニングする場合は**「トレーニング (Train)」**をクリックし、モデルをトレーニングし、機械学習モデルによって追加されたアノテーションを評価し、パフォーマンス統計を分析する場合は**「トレーニングと評価 (Train & Evaluate)」**をクリックします。

    > **重要:** 機械学習モデルのトレーニングには、人間によるアノテーションの数と、すべての文書にわたる単語の総数に応じて、数分から数時間かかる可能性があります。

1. モデルのトレーニングに使用する文書セットを選択します。

    > **注:** 文書セットには、アノテーションが付けられた、少なくとも 10 個の文書が含まれている必要があります。

1. モデルが作成されたら、以下のいずれかのアクションを選択します。

    <table summary="この表では行ごとに 1 つの選択可能なオプションを記述しています。">
      <caption>表 1. 文書のオプション</caption>
      <tr>
        <th style="vertical-align:bottom; text-align"left" id="d33883e137-option">Option</th>
        <th style="vertical-align:bottom; text-align"left" id="d33883e137-desc">説明</th>
      </tr>
      <tr>
        <td style="vertical-align:top; text-align"left" headers="d33883e137-option" id="d33883e139">
          <p><strong>Log</strong></p>
        </td>
        <td style="vertical-align:top; text-align"left" headers="d33883e137-desc d33883e139">
          <p>ログ・ファイルを表示して、問題が発生したかどうかを確認します。</p>
        </td>
      </tr>
      <tr>
        <td style="vertical-align:top; text-align"left" headers="d33883e137-option" id="d33883e144">
          <p><strong>Details</strong></p>
        </td>
        <td style="vertical-align:top; text-align"left" headers="d33883e137-desc d33883e144">
          <p>アノテーションのパフォーマンス統計を表示し、モデルのトレーニングとテストに
              使用する文書セットを変更し、モデル成果物のスナップショット・バージョンを
              作成します。</p>
        </td>
      </tr>
      <tr>
        <td style="vertical-align:top; text-align"left" headers="d33883e137-option" id="d33883e149">
          <p><strong>Export</strong></p>
        </td>
        <td style="vertical-align:top; text-align"left" headers="d33883e137-desc d33883e149">
          <p>標準プランまたはプレミアム・プランがある場合は、{{site.data.keyword.watson}} Explorer などの機械学習ランタイム環境でモデルを実行するために必要なコンポーネントが含まれているローカル・システムに、<code>ZIP</code> ファイルをエクスポートできます。</p>
        </td>
      </tr>
    </table>

## モデルによって追加されたアノテーションの評価
{: #wks_matest}

ヒューマン・アノテーターによって追加されたアノテーションのグランドトゥルース・ビューを、モデルによって追加されたアノテーションと比較できます。

### 手順
{: #wks_matest_procedure}

モデルによって追加されたアノテーションを評価するには、以下のようにします。

1. **「機械学習モデル (Machine Learning Model)」**>**「パフォーマンス (Performance)」**>**「トレーニングと評価 (Train and evaluate)」**を選択します。「トレーニング/テスト/ブラインド・セット (Training/Test/Blind Sets)」ページが表示されます。
1. トレーニング・セットまたはテスト・セットの**「グランドトゥルースの表示 (View Ground Truth)」**をクリックして、事前アノテーションおよびヒューマン・アノテーターによって追加されたアノテーションを表示します。 グランドトゥルース・エディターが開きます。 個々の文書をクリックして開き、メンション、関係、および同一指示されたメンションにどのようにアノテーションが付けられたかを確認します。
1. **「パフォーマンス (Performance)」**ページで、**「デコード結果の表示 (View Decoding Results)」**をクリックして、テスト・セット内の文書に機械学習モデルが追加したアノテーションを表示します。 このボタンは、モデルを評価して初めて使用可能になります。 結果を表示することにより、機械学習モデルがテスト・データ内のメンション、関係、および同一指示されたメンションにどの程度正しくラベルを付けることができたかを確認できます。
1. トレーニング・データ・セット、テスト・データ・セット、およびブラインド・データ・セットの間で文書を分割する方法を変更する場合は、**「パフォーマンス (Performance)」** > **「トレーニングと評価 (Train and evaluate)」** > **「設定の編集 (Edit settings)」**をクリックします。 例えば、初期の結果が受け入れ可能と思われる場合は、機械学習モデルの結果をさらにテストするために、テスト・セット内の文書の数を増やすことができます。 異なる目的に応じて文書を自動的に分割する比率を変更したり、トレーニング・データ、テスト・データ、およびブラインド・データとして使用する特定の文書セットを選択したりできます。
1. 何らかの変更を行った場合は、**「トレーニングと評価 (Train & Evaluate)」**をクリックして、モデルをリトレーニングし、アノテーションを再評価します。

## 機械学習モデルの削除
{: #wks_madelete}

機械学習モデルは削除できません。

モデルを開発するために使用したワークスペースは削除できますが、モデル自体を削除することはできません。 モデルの削除は最良の方法ではありません。 代わりに、モデルのトレーニングに使用される成果物を更新または置換してください。 モデルが期待どおりの結果を生成していない場合でも、モデルの改良を続行できます。 新規バージョンを作成するたび、モデルは新たに構築されます。 辞書やタイプ・システムなどの成果物を編集し、次のバージョンをトレーニングするときは、別のアノテーション・セットを使用するように選択できます。
