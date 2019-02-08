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

この文書は、{{site.data.keyword.cloud}} 上の {{site.data.keyword.knowledgestudiofull}} に関するものです。 前のバージョンの {{site.data.keyword.IBM_notm}} マーケットプレイス上の {{site.data.keyword.knowledgestudioshort}} に関する文書を参照するには、[このリンクをクリックしてください ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/docs/services/knowledge-studio/create-project.html){: new_window}。
{: tip}

# ワークスペースの作成
{: #create-project}

カスタム・モデルを作成する最初のステップは、ワークスペースを作成することです。
{: shortdesc}

## この作業について

作成して使用するモデルごとに、モデルの作成に必要な成果物およびリソースを含むワークスペースを 1 つ作成します。 その後、モデルをトレーニングして、外部サービスにデプロイして使用できるカスタム・モデルを生成します。

ワークスペースを作成する前に、以下の質問に回答してください。

- **どのようなタイプのモデルを作成しますか?**

    - 機械学習モデル: 統計的手法を使用して、文書内のエンティティーおよび関係を見つけます。 このタイプのモデルは、データ量の増加に適応できます。
    - ルール・ベース・モデル: 宣言的手法を使用して、文書内のエンティティーを見つけます。 このタイプのモデルは、予測可能性が高く、理解および保守が容易です。 ただし、新しいデータから学習することはしません。 探すように教えられたパターンを見つけるだけです。

    > **注:** 1 つのルール・ベース・モデルと 1 つの機械学習モデルの両方を含んでいる 1 つのワークスペースを作成することもできます。

- **どのようなサービスがモデルを使用するようになりますか?**

    カスタム・モデルと共に使用できる他の {{site.data.keyword.watson}} サービスについては、『[{{site.data.keyword.watson}} サービスの統合](/docs/services/watson-knowledge-studio/index.html#wks_watsoninteg)』を参照してください。

## 手順

ワークスペースを作成するには、以下のステップを実行します。

1. {{site.data.keyword.knowledgestudioshort}} アドミニストレーターとしてログインし、**「ワークスペースの作成 (Create Workspace)」**をクリックします。

    > **注:** プロジェクト管理者の役割を持つユーザーは、ワークスペースの作成を除いて、ほとんどすべての作業を実行できます。 アドミニストレーターが最初にワークスペースを作成し、そのワークスペースにプロジェクト管理者を割り当てる必要があります。

1. ワークスペースに名前を付けます。 分野の内容またはモデルの目的を反映する短い名前を付けてください。 必要であれば後でワークスペース名を変更できます。
1. ワークスペース内の文書の言語を指定します。 ワークスペースに追加する文書、および、作成またはアップロードする辞書は、指定する言語でなければなりません。
1. オプション: 当アプリケーションで使用されるトークナイザーをデフォルトの機械学習ベースのトークナイザーから変更する場合は、**「詳細オプション (Advanced Options)」**セクションを展開し、**「辞書ベースのトークナイザー (Dictionary-based tokenizer)」**を選択します。

    デフォルトのトークナイザーは、辞書ベースのトークナイザーよりも高度です。デフォルトのトークナイザーは、ソース文書の言語で行われた統計的学習に基づき、機械学習を使用してソース文書内のトークンを識別します。 より自然な言語パターンや微妙なニュアンスを持つ言語パターンを理解しているため、より高い精度でトークンを識別できます。 辞書ベースのトークナイザーは、言語規則に基づいてトークンを識別します。 詳しくは、『[トークナイザー](/docs/services/watson-knowledge-studio/create-project.html#wks_tokenizer)』を参照してください。

1. オプション: プロジェクト管理者をワークスペースに追加したい場合、**「詳細オプション (Advanced Options)」**セクションを展開し、プロジェクト管理者として追加するユーザーの名前をリストから選択します。 アドミニストレーターは、後でワークスペースを編集して、プロジェクト管理者を追加または削除できます。

    インスタンスの「ユーザー・アカウント管理 (User Account Management)」ページからプロジェクト管理者の役割に割り当てたユーザーの名前のみが表示されます。 ユーザーの追加について詳しくは、『[チームのアセンブル](/docs/services/watson-knowledge-studio/team.html)』を参照してください。

    > **注:** ライト・プランのサブスクリプションをお持ちの場合は、このステップをスキップしてください。 他のユーザーを追加することはできないため、プロジェクト管理者の役割に誰かを割り当てることはできません。 別個のプロジェクト管理者は必要ありません。 アドミニストレーターとして、通常はプロジェクト管理者が実行する作業をすべて実行できます。

1. **「作成 (Create)」**をクリックします。

## 次に行うこと

ワークスペースが作成されたら、ワークスペース・リソースの構成を開始できます。

ワークスペースの説明またはワークスペース名を変更するため、または、後でプロジェクト管理者を追加または削除するために、アドミニストレーターはワークスペースを編集できます。 {{site.data.keyword.knowledgestudioshort}} ホーム・ページから、ワークスペースのタイル上にある**「メニューの表示 (Show menu)」**アイコンをクリックし、**「編集 (Edit)」**メニュー・オプションを選択します。

**関連概念**:

[別のワークスペースからのリソースのアップロード](/docs/services/watson-knowledge-studio/exportimport.html)

**関連リファレンス**:

[言語サポート](/docs/services/watson-knowledge-studio/language-support.html)

## トークナイザー
{: #wks_tokenizer}

トークナイザーは、文字をトークンにグループ化し、トークンをセンテンスにグループ化します。 トークンは単語とゆるやかに等価です。

トークナイザーが文書のトークンを識別するために実行する必要がある処理は、文書の言語によって異なります。 英語では、多くの場合トークンは、センテンス内の空白で区切られた語数と等しくなります。 ただし、必ず 1 対 1 で単語と一致するわけではありません。状況によっては、他のテキスト要素がトークンと見なされます。 例えば、センテンスの末尾にある句読点は 1 つのトークンと見なされ、縮約形は多くの場合 2 つのトークンに展開されます。 空白文字を使用しない中国語などの言語では、もっと複雑な統計的アルゴリズムがトークンを識別するために使用されます。

トークン化のプロセスは重要です。なぜなら、ユーザーがグランド・トゥルース・エディターでアノテーション付けのために強調表示できる文字グループがこれによって決定されるためです。 エンティティー・メンションおよび関係メンションのアノテーションは、トークン境界に位置合わせされるのが一般的であり、センテンス内でラベル付けされる必要があります。つまり、センテンス境界をまたがってはなりません。

### サポートされるタイプ

{{site.data.keyword.knowledgestudioshort}} では以下のトークナイザーがサポートされています。

- **機械学習ベースのトークナイザー (デフォルト)**

    これは、ソース文書の言語で行われた統計的学習に基づいてソース文書内のトークンを識別する、より高度なトークナイザーです。 このトークナイザーは、より自然な言語パターンや微妙なニュアンスを持つ言語パターンをキャプチャーするトークンを検出します。 このトークナイザーをカスタマイズすることはできません。

- **辞書ベースのトークナイザー**

    このトークナイザーは言語辞書に基づきます。 ソース文書言語の規則に従っているトークンが検出されます。 上級者のみがこのトークナイザーをカスタマイズできます。

ワークスペースを作成するときに、使用するトークナイザーを選択する必要があります。 後で別のトークナイザーに切り替えることはできません。 最良の結果を得るには、デフォルトのトークナイザーを使用してください。 決定論的辞書メカニズムを通してトークナイザーの動作を変更したい上級者のみが、辞書ベースのトークナイザーを選択でき、辞書に新規項目を追加してそれをカスタマイズできます。 ただし、辞書に新しい単語を追加するという変更が機械学習モデルに意図しない影響を与える可能性があるため、カスタマイズは慎重に行う必要があります。

## 入力、出力、および制限の要約
{: #wks_formats}

モデル開発の各段階は、それぞれ異なる入力を必要とし、異なる出力を生成します。

次の表は、モデル開発プロセスの各段階について、実行する標準的なアクティビティー、サポートされる入力ファイル・フォーマット、生成される可能性のある出力、 および、サイズ制限またはその他の要件を要約しています。

### すべてのモデル・タイプ

<table summary="この表には、すべてのモデル・タイプの、入力、出力、および制限が要約されています。">
  <caption>表 1. すべてのモデル・タイプ</caption>
  <tr>
    <th style="vertical-align:bottom; text-align:left" id="d25459e252">
      タスク
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e254">
      一般的な使用法
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e256">
      サポートされる入力フォーマット
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e258">
      サポートされる出力フォーマット
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e260">
      制限および要件
    </th>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e252">
      <p>タイプ・システムの管理</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e254">
      <p>タイプ・システムを作成するか、既存のタイプ・システムをアップロードして変更します。</p>
      <p>対象分野のエンティティー・タイプおよび関係タイプを定義します。</p>
      <p>タイプ・システムを視覚化して表示することはできません。</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e256">
      <ul>
        <li>
          <p>{{site.data.keyword.knowledgestudioshort}} ワークスペースからダウンロードした JSON ファイル</p>
        </li>
        <li>
          <p>Human Annotation Tool (HAT) からダウンロードした ZIP ファイル</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e258">
      <ul>
        <li>
          <p>JSON</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e260">
      <p>ヒューマン・アノテーションでの視覚的な過負荷を回避するため、定義するエンティティー・タイプは 50 個以下、関係タイプは 50 個以下にしてください。</p>
      <p>タイプ・システムのアップロードでのファイル・サイズ制限: 20 MB</p>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e252">
      <p>辞書の管理</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e254">
      <p>読み取り専用モードの CSV 辞書ファイルをアップロードするか、別のワークスペースからダウンロードした辞書の ZIP をアップロードします。</p>
      <p>新規辞書を作成し、その後で、用語項目の CSV ファイルをアップロードするか、用語項目を追加します。</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e256">
      <p>辞書ファイル:</p>
      <ul>
        <li>
          <p>UTF-8 形式の CSV ファイル</p>
        </li>
        <li>
          <p>別のワークスペースからダウンロードした辞書の ZIP</p>
        </li>
      </ul>
      <p>用語項目ファイル:</p>
      <ul>
        <li>
          <p>UTF-8 形式の CSV ファイル</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e258">
      <ul>
        <li>
          <p>UTF-8 形式の CSV ファイル</p>
        </li>
        <li>
          <p>別のワークスペースで使用するための辞書の ZIP</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e260">
      <p>ファイル・サイズ制限:</p>
      <ul>
        <li>
          <p>CSV 用語項目ファイル当たり 1 MB</p>
        </li>
        <li>
          <p>CSV 読み取り専用辞書ファイル当たり 16 MB</p>
        </li>
        <li>
          <p>辞書当たり 15,000 項目 (読み取り専用辞書を除く)</p>
        </li>
        <li>
          <p>ワークスペース当たり 64 辞書</p>
        </li>
      </ul>
    </td>
  </tr>
</table>

 {: #wks_formats__datasimpletable_xxj_qr5_2y}

### 機械学習モデル

<table summary="この表には、機械学習モデルの、入力、出力、および制限が要約されています。">
  <caption>表 2. 機械学習モデル</caption>
  <tr>
    <th style="vertical-align:botton; text-align:left" id="d25459e331">タスク</th>
    <th style="vertical-align:botton; text-align:left" id="d25459e333">一般的な使用法</th>
    <th style="vertical-align:botton; text-align:left" id="d25459e335">サポートされる入力フォーマット</th>
    <th style="vertical-align:botton; text-align:left" id="d25459e337">サポートされる出力フォーマット</th>
    <th style="vertical-align:botton; text-align:left" id="d25459e339">制限および要件</th>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>文書の管理 </p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
      <p>小さくて代表的な、文書のサブセットをアップロードします。</p>
      <p>ヒューマン・アノテーター、機械学習モデル、または UIMA 分析エンジンによって以前に追加されたアノテーションを含んでいる文書をアップロードします。</p>
      <p>アノテーション用に高い価値のある文書群を計算して {{site.data.keyword.ibmwatson_notm}} Explorer からコーパス全体を取り込むことはできません。</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <ul>
        <li>
          <p>UTF-8 形式の CSV ファイル</p>
        </li>
        <li>
          <p>UTF-8 形式のテキスト</p>
        </li>
        <li>
          <p>別のコーパスからダウンロードした文書を含む ZIP ファイル</p>
        </li>
        <li>
          <p>UIMA CAS XMI 形式の文書を含む ZIP ファイル</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <ul>
        <li>
          <p>文書の ZIP アーカイブ・ファイル</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <ul>
        <li>
          <p>文書当たり 40,000 文字</p>
        </li>
        <li>
          <p>ワークスペース当たり 10,000 文書</p>
        </li>
        <li>
          <p>ワークスペース当たり 1,000 文書セット (アノテーション・セットを含む)</p>
        </li>
      </ul>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>事前アノテーション</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
       <p>辞書または {{site.data.keyword.nlufull}} プレアノテーターを使用して、ヒューマン・アノテーション用の開始点を提供します。</p>
       <p>{{site.data.keyword.ibmwatson_notm}} Explorer からのコーパスにアノテーションを付け直すことはできません。</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <p>未加工の文書。</p>
      <p><b>注:</b> ヒューマン・アノテーターが既にアノテーションを付けた文書に事前アノテーション付けを行わないでください。もし行うと、ヒューマン・アノテーターによる作業が失われます。</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <p>部分的にアノテーションが付けられた文書</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <p>なし</p>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>文書アノテーション</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
      <p>ヒューマン・アノテーションを管理します。</p><p>グランド・トゥルースを作成するため、エンティティー、関係、および照応チェーンにアノテーションを付けます。</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <p>アノテーション・タスク</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <p>グランド・トゥルース</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <ul>
        <li>
          <p>ワークスペース当たり 256 個のアクティブなアノテーション・タスク</p>
        </li>
      </ul>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>トレーニングおよび改良</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
      <p>構造化されていないテキストから分野固有の情報を抽出するよう、監視対象の機械学習モデルをトレーニングします。</p><p>監視対象の機械学習モデルを評価し、改善します。</p>
      <p>半監視または非監視の機械学習モデルを作成することはできません。</p>
      <p>広範な特徴エンジニアリングを行うことはできません。</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <p>適用外</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <p>機械学習モデル</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <ul>
        <li>
          <p>ワークスペース当たり 1 機械学習モデル</p>
        </li>
        <li>
          <p>ワークスペース当たり 10 モデル・バージョン</p>
        </li>
        <li>
          <p>ワークスペースの最大数はサブスクリプション・プランによって決まります。</p>
        </li>
        <li>
          <p>1 カ月当たりに実行できるトレーニング・アクションの最大数は、サブスクリプション・プランによって決まります。</p>
        </li>
      </ul>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>公開</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
      <p>他の {{site.data.keyword.watson}} アプリケーションでテキスト抽出の実行に使用できるように、機械学習モデルを公開します。</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <p>適用外</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <ul>
        <li>
          <p>モデル ID ({{site.data.keyword.nlufull}} または {{site.data.keyword.discoveryfull}} で使用するため)</p>
        </li>
        <li>
          <p>ZIP ファイル ({{site.data.keyword.ibmwatson_notm}} Explorer で使用するため)</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <p>{{site.data.keyword.watson}} サービスにデプロイするには、{{site.data.keyword.cloud_notm}} サービスのスペース名およびインスタンス名を知っている必要があります。</p>
    </td>
  </tr>
</table>

### ルール・ベース・モデル

<table summary="この表には、ルール・ベース・モデルの、入力、出力、および制限が要約されています。">
  <caption>表 3. ルール・ベース・モデル</caption>
  <tr>
    <th style="vertical-align:bottom; text-align:left" id="d25459e509">
      タスク
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e511">
      一般的な使用法
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e513">
      サポートされる入力フォーマット
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e515">
      サポートされる出力フォーマット
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e517">
      制限および要件
    </th>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e509">
      <p>ルール・エディター</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e511">
      <p>クラス、正規表現、およびルールを定義する元になる文書を、作成するか、ルール・エディターにアップロードします。</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e513">
      <ul>
        <li>
          <p>プレーン・テキスト (エディターで追加されるもの)</p>
        </li>
        <li>
          <p>UTF-8 形式の CSV ファイル</p>
        </li>
        <li>
          <p>すべての文書セットからコピーされる</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e515">
      <p>なし</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e517">
      <ul>
        <li>
          <p>ワークスペース当たり 1 ルール・ベース・モデル</p>
        </li>
        <li>
          <p>文書当たり 5,000 文字</p>
        </li>
        <li>
          <p>ワークスペース当たり 100 文書</p>
        </li>
        <li>
          <p>文書タイトルの最大サイズは 256 文字です</p>
        </li>
        <li>
          <p>ワークスペース当たり 200 ルール</p>
        </li>
        <li>
          <p>ワークスペース当たり 400 クラス</p>
        </li>
        <li>
          <p>ワークスペース当たり 100 正規表現グループ</p>
        </li>
        <li>
          <p>正規表現グループ当たり 100 正規表現項目</p>
        </li>
        <li>
          <p>正規表現項目当たり 1,000 文字</p>
        </li>
        <li>
          <p>ワークスペース当たり 5 ルール・ベース・モデル・バージョン</p>
        </li>
      </ul>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e509">
      <p>公開</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e511">
      <p>他の {{site.data.keyword.watson}} アプリケーションでパターン認識の実行に使用できるようにルール・ベース・モデルを公開します。</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e513">
      <p>適用外</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e515">
      <ul>
        <li>
          <p>モデル ID ({{site.data.keyword.nlufull}} または {{site.data.keyword.discoveryfull}} で使用するため)</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e517">
      <p>{{site.data.keyword.watson}} サービスにデプロイするには、{{site.data.keyword.cloud_notm}} サービスのスペース名およびインスタンス名を知っている必要があります。</p>
    </td>
  </tr>
</table>
