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

この文書は、{{site.data.keyword.cloud}} 上の {{site.data.keyword.knowledgestudiofull}} に関するものです。 前のバージョンの {{site.data.keyword.IBM_notm}} マーケットプレイス上の {{site.data.keyword.knowledgestudioshort}} に関する文書を参照するには、[このリンクをクリックしてください ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/docs/services/knowledge-studio/ml-annotator.html){: new_window}。
{: tip}

# 機械学習モデル作成ワークフロー
{: #ml_annotator}

関心のあるエンティティー、照応、および関係を新しい文書内で識別するために使用できるモデルをトレーニングする、機械学習モデルを作成します。
{: shortdesc}

ここでは、{{site.data.keyword.knowledgestudioshort}} で機械学習モデルを作成するための標準的なワークフローについて説明します。

ヒューマン・アノテーターによって実行される*文書へのアノテーション付け* のステップを除いて、すべてのステップがプロジェクト管理者によって実行されます。 ヒューマン・アノテーターは対象分野の専門家であることが多いため、ワークスペース・リソース (タイプ・システムなど) の作成中に助言を求められることもあります。

![機械学習モデル開発のワークフロー](images/wks-checklist.svg "モデルを作成するために実行する必要のある主要ステップを示しています") 図 1. 機械学習モデル開発のワークフロー

<table summary="モデルの作成および詳細化">
  <caption>表 1. ワークフローの作成および詳細化</caption>
  <tr>
    <th style="vertical-align:bottom; text-align:left" id="d14771e70">ステップ</th>
    <th style="vertical-align:bottom; text-align:left" id="d14771e72">説明</th>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d14771e70">
      <p>ワークスペースの作成</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d14771e72">
      <p>『[ワークスペースの作成](/docs/services/watson-knowledge-studio/create-project.html)』を参照してください。 ワークスペースには、モデルの作成に使用されるリソースが含まれています。リソースには以下のものがあります。</p>
      <dl>
        <dt>タイプ・システム</dt>
        <dd>
          <p>タイプ・システムをアップロードまたは作成し、ヒューマン・アノテーターがテキストにアノテーションを付けるときに適用できるエンティティー・タイプおよび関係タイプを定義します。 通常、モデルのプロセス管理者と対象分野の専門家が協力してタイプ・システムを定義します。 『[タイプ・システムの設定](/docs/services/watson-knowledge-studio/typesystem.html)』を参照してください。</p>
        </dd>
        <dt>ソース文書</dt>
        <dd>
          <p>分野コンテンツの代表的なサンプル文書をワークスペースにアップロードすることによって、コーパスを作成します。 『[アノテーション用の文書の追加](/docs/services/watson-knowledge-studio/documents-for-annotation.html)』を参照してください。 コーパスを文書セットに分割し、すべての文書セットで共有される文書のパーセンテージを指定し、文書セットをヒューマン・アノテーターに割り当てます。 『[アノテーション・セットの作成および割り当て](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projdocsets)』を参照してください。</p>
        </dd>
        <dt>辞書</dt>
        <dd>
          <p>テキストにアノテーションを付けるための辞書をアップロードまたは作成します。 手動で辞書項目を追加するのか、ファイルから項目をアップロードするのかを選択でき、その後で項目を編集できます。 『[辞書の作成](/docs/services/watson-knowledge-studio/dictionaries.html)』を参照してください。</p>
        </dd>
      </dl>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d14771e70">
      <p><strong>オプション</strong>: 文書への事前アノテーション付け</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d14771e72">
      <p>ワークスペース辞書内の用語または {{site.data.keyword.nlushort}} タイプのメンションに従って、または、定義するルールに基づいて、文書に事前にアノテーションを付けます。 『[アノテーションのブートストラッピング](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotate)』を参照してください。</p>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d14771e70">
      <p>文書へのアノテーション付け</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d14771e72">
      <ol>
        <li>
          <p>プロジェクト管理者は、アノテーション・タスクをヒューマン・アノテーターに割り当て、アノテーター間一致しきい値を構成し、ヒューマン・アノテーターが順守するべきアノテーション・ガイドラインを提供します。 『[アノテーション・タスクの作成](/docs/services/watson-knowledge-studio/annotate-documents.html#wks_hatask)』を参照してください。</p>
        </li>
        <li>
          <p>ヒューマン・アノテーターは、グランド・トゥルース・エディターを使用して文書に手動でアノテーションを付けます。 ヒューマン・アノテーターは、分野コンテンツ内の関心のあるメンションを識別し、それらにエンティティー・タイプのラベルを付けます。 また、ヒューマン・アノテーターは、メンション間の関係 (例えば、Mary は IBM の従業員であるという関係) を識別し、同じエンティティーに対して複数のメンションがどのように照応するのか (Mary を意味する「she」のオカレンスなど) を識別します。 『[文書のアノテーション付け](/docs/services/watson-knowledge-studio/user-guide.html)』を参照してください。</p>
        </li>
      </ol>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d14771e70">
      <p>裁定と文書のプロモート</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d14771e72">
      <p>ヒューマン・アノテーターによって生成されたグランド・トゥルースを承認または拒否し、アノテーションが違っている場合は裁定して競合を解決します。 プロジェクト管理者よりも対象分野の経験が豊富なユーザーまたは上級ヒューマン・アノテーターが、ヒューマン・アノテーション作業の正確度と整合性の評価を担当することが推奨されます。 『[裁定](/docs/services/watson-knowledge-studio/build-groundtruth.html#wks_haperform)』を参照してください。</p>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d14771e70">
      <p>モデルのトレーニング</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d14771e72">
      <p>機械学習モデルを作成します。 『[機械学習モデルの作成](/docs/services/watson-knowledge-studio/train-ml.html#wks_madocsets)』を参照してください。</p>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d14771e70">
      <p>モデルの評価</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d14771e72">
      <p>モデルの正確度を評価します。 『[モデルによって追加されたアノテーションの評価](/docs/services/watson-knowledge-studio/train-ml.html#wks_matest)』を参照してください。 モデルの正確度によっては、このステップの結果、最適な正確度が得られるまで前のステップを何回も繰り返すことが必要になる場合があります。 一般的なパフォーマンス問題に基づいた更新内容については、『[機械学習モデルのパフォーマンスの分析](/docs/services/watson-knowledge-studio/evaluate-ml.html)』を参照してください。</p>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d14771e70">
      <p>モデルの公開</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d14771e72">
      <p>モデルをエクスポートまたはデプロイします。 『[機械学習モデルの使用](/docs/services/watson-knowledge-studio/publish-ml.html)』を参照してください。</p>
    </td>
  </tr>
</table>
