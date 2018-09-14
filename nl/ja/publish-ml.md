---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-13"

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

この文書は、{{site.data.keyword.cloud}} 上の {{site.data.keyword.knowledgestudiofull}} に関するものです。 以前のバージョンの {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 向けの資料を参照するには、[このリンクをクリック ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/docs/services/knowledge-studio/publish-ml.html){: new_window} してください。
{: tip}

# 機械学習モデルの使用
{: #publish-ml}

{{site.data.keyword.knowledgestudioshort}} でトレーニングした機械学習モデルを他の {{site.data.keyword.watson}} アプリケーションで使用できるようにすることで、機械学習モデルを活用します。
{: shortdesc}

機械学習モデルはデプロイしたりエクスポートしたりできます。 辞書または {{site.data.keyword.nlushort}} 事前アノテーターを使用して事前にアノテーションを付けることができるのは、{{site.data.keyword.knowledgestudioshort}} 内の文書に限定されます。

サービスで使用するためにモデルをデプロイするためには、事前にサービスへのサブスクリプションが必要です。 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} サービスは、{{site.data.keyword.IBM_notm}} のクラウド・プラットフォームである {{site.data.keyword.Bluemix_short}} 上でホストされます。 プラットフォームについて詳しくは、[{{site.data.keyword.Bluemix_notm}} とは? ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.ng.bluemix.net/docs/overview/whatisbluemix.html){: new_window} を参照してください。 いずれかの {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} サービスにサブスクライブするには、[{{site.data.keyword.Bluemix_notm}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.ng.bluemix.net/){: new_window} Web サイトからアカウントを作成します。

一部のサービスでは、{{site.data.keyword.Bluemix_notm}} スペース名やサービス・インスタンス名など、デプロイ先として計画しているサービス・インスタンスに関する詳細を把握しておく必要があります。 スペース名やインスタンス名の情報は、{{site.data.keyword.Bluemix_notm}} 「サービス」ページから入手できます。

機械学習モデルを使用して、新規文書に事前にアノテーションを付けることもできます。 詳しくは、[機械学習モデルによる文書の事前アノテーション](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotsire)を参照してください。

## IBM Watson Discovery への機械学習モデルのデプロイ
{: #wks_madiscovery}

モデルのパフォーマンスに満足できたら、そのバージョンを {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}} にデプロイできます。 この機能により、アプリケーションが、デプロイされた機械学習モデルを使用して、データから得た洞察をエンリッチして、ドメインに関連がある概念や関係の認識を組み込むことができるようになります。

### 始めに
{: #wks_madiscovery_prereqs}

{{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}} サービス・インスタンスへの管理アクセス権限が必要なほか、それに関連付けられた {{site.data.keyword.Bluemix_notm}} スペース名およびインスタンス名を把握しておく必要があります。

### この作業について
{: #wks_madiscovery_about}

機械学習モデルをデプロイするときは、デプロイするモデルのバージョンを選択します。

### 手順
{: #wks_madiscovery_procedure}

機械学習モデルを {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}} にデプロイするには、以下のステップを実行します。

1. {{site.data.keyword.knowledgestudioshort}} 管理者またはプロジェクト管理者としてログインし、ワークスペースを選択します。
1. **「機械学習モデル」** > **「バージョン」**を選択します。
1. デプロイするモデルのバージョンを選択します。

    モデルの作業バージョンが 1 つしかない場合は、現在のモデルのスナップショットを作成します。 これによりモデルがバージョン化され、現行バージョンの改善を続行しながら、1 つのバージョンをデプロイできます。 デプロイするためのオプションは、少なくとも 1 つのバージョンを作成するまで表示されません。

    **注**: 各バージョンは、1 つのサービス・インスタンスにのみデプロイできます。同じモデルを複数のインスタンスにデプロイする場合は、インスタンスごとに 1 つのバージョンを作成します。

1. **「デプロイ」**をクリックし、{{site.data.keyword.discoveryshort}} へのデプロイを選択し、**「次へ」**をクリックします。
1. {{site.data.keyword.Bluemix_notm}} スペースとインスタンスを選択します。 必要な場合、別の地域を選択します。
1. **「デプロイ」**をクリックします。
1. デプロイメント・プロセスには、数分かかる場合があります。 デプロイメントの状況を確認するには、**「バージョン」**タブで、デプロイしたバージョンの横の**「状況 (Status)」**をクリックします。

    モデルのデプロイがまだ進行中の場合、状況には「公開中 (publishing)」と示されます。 デプロイメントが完了すると、デプロイメントが成功した場合は状況が「使用可能 (available)」に変わり、問題が発生した場合は「エラー (error)」に変わります。

    モデルが使用可能になったら、モデル ID (model_id) をメモしておきます。 この ID を {{site.data.keyword.discoveryshort}} サービスに提供して、サービスがカスタム・モデルを使用できるようにします。

### 次に行うこと
{: #wks_madiscovery_next}

デプロイされたモデルを使用するには、{{site.data.keyword.discoveryshort}} サービスのエンリッチ構成プロセスの中で要求されたときにモデル ID を提供する必要があります。 詳細については、[{{site.data.keyword.discoveryshort}} サービスの資料 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/docs/services/discovery/integrate-wks.html){: new_window} を参照してください。

## IBM Watson Natural Language Understanding への機械学習モデルのデプロイ
{: #wks_manlu}

モデルのパフォーマンスに満足できたら、そのバージョンを {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.nlushort}} にデプロイできます。 この機能により、アプリケーションが、デプロイされた機械学習モデルを使用して、エンティティーや関係を含め、テキスト入力の意味構造のフィーチャーを分析できるようになります。

### 始めに
{: #wks_manlu_prereqs}

デプロイ先となる {{site.data.keyword.nlushort}} サービスが必要です。 また、そのサービスに関連付けられている {{site.data.keyword.Bluemix_notm}} スペース名およびインスタンス名を把握しておく必要があります。 スペース名またはインスタンス名を覚えていない場合は、{{site.data.keyword.Bluemix_notm}} にログインして、見つけてください。 {{site.data.keyword.Bluemix_notm}} アカウントがない場合は、登録して、アカウントを作成してください。

### この作業について
{: #wks_manlu_about}

機械学習モデルをデプロイするときは、デプロイするモデルのバージョンを選択します。

### 手順
{: #wks_manlu_procedure}

機械学習モデルを {{site.data.keyword.nlushort}} サービスにデプロイするには、以下のステップを実行します。

1. {{site.data.keyword.knowledgestudioshort}} 管理者またはプロジェクト管理者としてログインし、ワークスペースを選択します。
1. **「機械学習モデル」** > **「バージョン」**を選択します。
1. デプロイするモデルのバージョンを選択します。

    モデルの作業バージョンが 1 つしかない場合は、現在のモデルのスナップショットを作成します。 これによりモデルがバージョン化され、現行バージョンの改善を続行しながら、1 つのバージョンをデプロイできます。 デプロイするためのオプションは、少なくとも 1 つのバージョンを作成するまで表示されません。

    **注**: 各バージョンは、1 つのサービス・インスタンスにのみデプロイできます。同じモデルを複数のインスタンスにデプロイする場合は、インスタンスごとに 1 つのバージョンを作成します。

1. **「デプロイ」**をクリックし、{{site.data.keyword.nlushort}} へのデプロイを選択し、**「次へ」**をクリックします。
1. {{site.data.keyword.Bluemix_notm}} スペースとインスタンスを選択します。 必要な場合、別の地域を選択します。
1. **「デプロイ」**をクリックします。
1. デプロイメント・プロセスには、数分かかる場合があります。 デプロイメントの状況を確認するには、**「バージョン」**タブで、デプロイしたバージョンの横の**「状況 (Status)」**をクリックします。 モデルのデプロイがまだ進行中の場合、状況には「公開中 (publishing)」と示されます。 デプロイメントが完了すると、デプロイメントが成功した場合は状況が「使用可能 (available)」に変わり、問題が発生した場合は「エラー (error)」に変わります。

    モデルが使用可能になったら、モデル ID (model_id) をメモしておきます。 この ID を {{site.data.keyword.nlushort}} サービスに提供して、サービスがカスタム・モデルを使用できるようにします。

### 次に行うこと
{: #wks_manlu_next}

デプロイされたモデルを使用するには、カスタム・モデルのモデル ID を `entities.model` パラメーターに指定する必要があります。

{{site.data.keyword.nlushort}} `GET /analyze` 要求でモデルを使用して、以下のフィーチャーを抽出できます。

- **エンティティー**

    以下のコマンドは、text パラメーターを使用して渡されたセンテンス内に存在するエンティティーを検出します。

    ```bash
    curl -G -u "3330af09-4b22-4f2d-a54c-1cb099df1fa8":"338rTJSvPVqeG"
    -d "version=2016-05-17"
    -d "text=Vehicle%201%2C%20a%201995%20Honda%20Civic%20was%20traveling%20north
    %20on%20a%20two%20lane%20undivided%20roadway%2C%20negotiating%20a%20curve%20to
    %20the%20left%20on%20an%20upgrade."
    -d "features=entities"
    -d "entities.model=10:7abc4c2f-5846-3334-b8f7-af5a6fad3398"
    "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze" -k
    ```
    {: pre}

    サービスは、カスタム・モデルに定義されているエンティティー・タイプを持つ、検出されたインスタンスの JSON オブジェクトを返します。

    ```javascript
    {
      "language": "en",
      "entities": [
        {
          "type": "MANUFACTURER",
          "text": "Honda",
          "count": 1
        },
        {
          "type": "MODEL",
          "text": "Civic",
          "count": 1
        },
        {
          "type": "VEHICLE",
          "text": "Vehicle 1",
          "count": 1
        },
        {
          "type": "STRUCTURE",
          "text": "two lane undivided roadway",
          "count": 1
        },
        {
          "type": "STRUCTURE",
          "text": "curve",
          "count": 1
        },
        {
          "type": "MODEL_YEAR",
          "text": "1995",
          "count": 1
        },
        {
          "type": "CONDITION",
          "text": "negotiating",
          "count": 1
        }
      ],
      "language": "en"
    }
    ```
    {: codeblock}

- **関係**

    以下のコマンドは、text パラメーターを使用して渡されたセンテンス内に存在する関係を検出します。

    ```bash
    curl -G -u "3330af09-4b22-4f2d-a54c-1cb099df1fa8":"338rTJSvPVqeG"
    -d "version=2016-05-17"
    -d "text=Vehicle%201%2C%20a%201995%20Honda%20Civic%20was%20traveling%20north
    %20on%20a%20two%20lane%20undivided%20roadway%2C%20negotiating%20a%20curve%20to
    %20the%20left%20on%20an%20upgrade."
    -d "features=relations"
    -d "entities.model=10:7abc4c2f-5846-3334-b8f7-af5a6fad3398"
    "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze" -k
    ```
    {: pre}

    サービスは、カスタム・モデルに定義されている関係タイプを持つ、検出されたインスタンスの JSON オブジェクトを返します。

    ```javascript
    {
      "relations": [
        {
          "type": "timeOf",
          "sentence": "Vehicle 1, a 1995 Honda Civic was traveling north
           on a two lane undivided roadway, negotiating a curve to
           the left on an upgrade.",
          "score": 0.954254,
          "arguments": [
            {
              "text": "1995",
              "entities": [
                {
                  "type": "Date",
                  "text": "1995"
                }
              ]
            },
            {
              "text": "Honda Civic",
              "entities": [
                {
                  "type": "SportingEvent",
                  "text": "Honda Civic"
                }
              ]
            }
          ]
        },
        {
          "type": "locatedAt",
          "sentence": "Vehicle 1, a 1995 Honda Civic was traveling north
           on a two lane undivided roadway, negotiating a curve to
           the left on an upgrade.",
          "score": 0.40592,
          "arguments": [
            {
              "text": "negotiating",
              "entities": [
                {
                  "type": "EventMeeting",
                  "text": "negotiating"
                }
              ]
            },
            {
              "text": "roadway",
              "entities": [
                {
                  "type": "Facility",
                  "text": "roadway"
                }
              ]
            }
          ]
        }
      ],
      "language": "en"
    }
    ```
    {: codeblock}

詳細については、[{{site.data.keyword.nlushort}} の資料 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/docs/services/natural-language-understanding/index.html){: new_window} を参照してください。

## モデルのアンデプロイ
{: #undeploy-view-model}

モデルをアンデプロイする場合、またはモデル ID を検索する場合は、**「デプロイ済みモデル (Deployed Models)」**ページを表示します。

### この作業について
{: #wks_undeploy_about}

「デプロイ済みモデル (Deployed Models)」ページに表示される内容は、{{site.data.keyword.knowledgestudioshort}} インスタンスをホストする [地域 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/docs/resources/services_region.html){: new_window} によって異なります。その地域が [IAM ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/docs/iam/users_roles.html){: new_window} および [Cloud Foundry ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/docs/iam/cfaccess.html){: new_window} アクセス管理方式によって管理されるインスタンスをサポートする場合は、その方式ごとに 1 つのタブが表示されます。IAM によって管理されるインスタンスに属するモデルは、**「リソース・グループ (Resource Groups)」**タブにリストされます。Cloud Foundry によって管理されるインスタンスに属するモデルは、**「組織 (Organizations)」**タブにリストされます。

その地域が 1 つのアクセス管理方式によってのみ管理されるインスタンスをサポートしている場合は、1 つのアクセス管理方式だけが適用可能なので、モデルのリストが 1 つだけ表示されます。

### 手順
{: #wks_deploy_procedure}

モデルをアンデプロイするか、モデル ID を検索するには、以下のようにします。

1. {{site.data.keyword.knowledgestudioshort}} を起動します。
1. 右上のメニュー・バーにある**「設定」**メニューから、**「デプロイ済みモデルの管理 (Manage deployed models)」**を選択します。
1. デプロイ済みモデルのリストから、表示またはアンデプロイするモデルを見つけます。
1. モデルをアンデプロイするには、その行の最後の列で**「モデルのアンデプロイ (Undeploy model)」**をクリックします。
1. モデル ID を見つけるには、**「モデル ID」**列を参照してください。

代わりの方法として、ルール・ベース・モデルと機械学習モデルにおいて、「バージョン (Versions)」ページからモデルをアンデプロイすることもできます。

## IBM Watson Explorer での機械学習モデルの活用
{: #wks_maexport}

{{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer で使用できるように、トレーニングした機械学習モデルをエクスポートします。

### 始めに
{: #wks_maexport_prereqs}

関係タイプを識別し、それらにアノテーションを付けようとする場合は、モデルをエクスポートする前に、少なくとも 2 つの関係タイプを定義し、グランドトゥルース内で関係のインスタンスにアノテーションを付ける必要があります。 1 つの関係タイプのみを定義し、アノテーションを付けた場合、この後、{{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer リリース 11.0.1.0 で問題が発生する可能性があります。

### この作業について
{: #wks_maexport_about}

特定のドメインのエンティティーおよび関係を認識するように機械学習モデルがトレーニングされたので、このモデルを {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer で活用できます。

[このリンク ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.youtube.com/watch?v=1VoS-xczBow&amp;feature=youtu.be){: new_window} をクリックすると、モデルをエクスポートし、それを {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer で使用する方法を示す 2 分弱のビデオを視聴できます。

### 手順
{: #wks_maexport_procedure}

{{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer で機械学習モデルを活用するには、以下のステップを実行します。

1. {{site.data.keyword.knowledgestudioshort}} 管理者またはプロジェクト管理者としてログインし、ワークスペースを選択します。
1. **「機械学習モデル」** > **「バージョン」**を選択します。
1. **「現行モデルのエクスポート (Export current model)」**をクリックします。

    ライト・プランに加入している場合、エクスポート・オプションは使用できません。

    モデルは ZIP ファイルとして保存され、ファイルのダウンロードを求めるプロンプトが出されます。

1. ファイルをローカル・システムにダウンロードします。
1. {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer アプリケーションから、モデルをインポートします。

    これで、モデルを {{site.data.keyword.watson}} Explorer Content Analytics の機械学習モデルにマップできます。 マッピング・ステップを実行した後、文書をクロールすると、モデルが認識するエンティティーおよび関係のインスタンスがモデルによって検出されます。 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer にモデルをインポートし、構成する方法については、統合について説明している技術資料 ([http://www.ibm.com/support/docview.wss?uid=swg27048147 ![外部リンク・アイコン](../../icons/launch-glyph.svg "リンク・アイコン")](http://www.ibm.com/support/docview.wss?uid=swg27048147){: new_window} を参照してください。

#### 関連タスク
{: #wks_maexport_related}

[{{site.data.keyword.watson}} Explorer Content Analytics からの分析済み文書のエクスポート](/docs/services/watson-knowledge-studio/preannotation.html#wks_uimawexca)
