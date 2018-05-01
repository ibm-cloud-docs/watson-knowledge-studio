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

この文書は、{{site.data.keyword.cloud}} 上の {{site.data.keyword.knowledgestudiofull}} に関するものです。以前のバージョンの {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 向けの資料を参照するには、[このリンクをクリック ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/docs/services/knowledge-studio/publish-ml.html){: new_window} してください。
{: tip}

# 機械学習モデルの使用
{: #publish-ml}

{{site.data.keyword.knowledgestudioshort}} でトレーニングした機械学習モデルを他の {{site.data.keyword.watson}} アプリケーションで使用できるようにすることで、機械学習モデルを活用します。
{: shortdesc}

機械学習モデルはデプロイしたりエクスポートしたりできます。辞書または {{site.data.keyword.nlushort}} 事前アノテーターを使用して事前にアノテーションを付けることができるのは、{{site.data.keyword.knowledgestudioshort}} 内の文書に限定されます。

サービスで使用するためにモデルをデプロイするためには、事前にサービスへのサブスクリプションが必要です。{{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} サービスは、{{site.data.keyword.IBM_notm}} のクラウド・プラットフォームである {{site.data.keyword.Bluemix_short}} 上でホストされます。プラットフォームについて詳しくは、[{{site.data.keyword.Bluemix_notm}} とは? ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.ng.bluemix.net/docs/overview/whatisbluemix.html){: new_window} を参照してください。いずれかの {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} サービスにサブスクライブするには、[{{site.data.keyword.Bluemix_notm}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.ng.bluemix.net/){: new_window} Web サイトからアカウントを作成します。

一部のサービスでは、{{site.data.keyword.Bluemix_notm}} スペース名やサービス・インスタンス名など、デプロイ先として計画しているサービス・インスタンスに関する詳細を把握しておく必要があります。スペース名やインスタンス名の情報は、{{site.data.keyword.Bluemix_notm}} 「サービス」ページから入手できます。

機械学習モデルを使用して、新規文書に事前にアノテーションを付けることもできます。詳しくは、[機械学習モデルによる文書の事前アノテーション](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotsire)を参照してください。

## AlchemyLanguage への機械学習モデルのデプロイ
{: #wks_mabluemix}

モデルのパフォーマンスに満足できたら、そのバージョンを {{site.data.keyword.IBM_notm}} {{site.data.keyword.alchemylanguageshort}} にデプロイできます。この機能では、{{site.data.keyword.alchemyapishort}} アクセス・キーを提供する必要があり、この機能により、アプリケーションが、デプロイされた機械学習モデルを使用してドメイン内の文書にアノテーションを付けることができるようになります。

### 始めに

モデルをデプロイし、使用するには、{{site.data.keyword.alchemylanguageshort}} サービスの拡張プランが必要です。
>注: {{site.data.keyword.alchemylanguageshort}} サービスは非推奨になりました。既存のプランがない場合は、このモデルをサービスにデプロイすることはできません。

### この作業について

機械学習モデルをデプロイするときは、デプロイするモデルのバージョンを選択します。このサービスにデプロイするには、{{site.data.keyword.IBM_notm}} {{site.data.keyword.alchemylanguageshort}} のアクセス・キーが必要です。

このキーは、カスタム・モデルを公開する権限があるアカウントに属している必要があります。そうでないと、モデルは正常にデプロイされても、モデルを使用できなくなります。

初めてモデルを {{site.data.keyword.alchemylanguageshort}} にデプロイするときに、キーを指定する必要があります。その後は、デプロイする複数のバージョンのモデルでそのキーを再使用できます。キーごとに、同時にデプロイできるモデルの最大数が決められています。

### 手順

機械学習モデルを {{site.data.keyword.alchemylanguageshort}} にデプロイするには、以下のようにします。

1. {{site.data.keyword.knowledgestudioshort}} 管理者またはプロジェクト管理者としてログインし、ワークスペースを選択します。
1. **「モデル管理 (Model Management)」** > **「バージョン (Versions)」** > **「機械学習 (Machine learning)」**タブを選択します。
1. デプロイするモデルのバージョンを選択します。

    モデルの作業バージョンが 1 つしかない場合は、現在のモデルのスナップショットを作成します。これによりモデルがバージョン化され、現行バージョンの改善を続行しながら、1 つのバージョンをデプロイできます。デプロイするためのオプションは、少なくとも 1 つのバージョンを作成するまで表示されません。

1. **「デプロイ」**をクリックし、{{site.data.keyword.alchemylanguageshort}} サービスへのデプロイを選択し、**「次へ」**をクリックします。
1. {{site.data.keyword.alchemylanguageshort}} から取得したキーを入力するか、再使用するキーを持つ、以前にデプロイされたバージョンのモデルを選択し、**「デプロイ」** をクリックします。キーが有効な場合は、モデル ID を含む確認が表示されます。この確認は、モデルがアプリケーションで使用できる状態にあることを意味するものではありません。
1. デプロイメント・プロセスには、数分かかる場合があります。デプロイメントの状況を確認するには、デプロイしたバージョンの横にある**「状況 (Status)」**をクリックします。モデルのデプロイがまだ進行中の場合、状況には「公開中 (publishing)」と示されます。デプロイメントが完了すると、デプロイメントが成功した場合は状況が「使用可能 (available)」に変わり、問題が発生した場合は「エラー (error)」に変わります。

    状況情報には、モデル ID、{{site.data.keyword.alchemyapishort}} キーの最後の 4 桁、およびデプロイメント・プロセスのログが含まれます。モデル ID (model_id) は、アプリケーションが機械学習モデルを呼び出す方法です。{{site.data.keyword.alchemyapishort}} キーを使用して、キーごとのデプロイメントの数を追跡します。

### 次に行うこと

デプロイされたモデルを使用するには、モデル ID をアプリケーションの API 呼び出しにコピー・アンド・ペーストする必要があります。この呼び出しでは、モデルで使用する {{site.data.keyword.alchemylanguageshort}} 拡張プランのサービスとそれに関連付けられた {{site.data.keyword.alchemyapishort}} アクセス・キーも指定する必要があります。以下のエンドポイントがサポートされています。

- **&lt;*input-type*&gt;GetRankedNamedEntities**

    model パラメーターで指定されたカスタム・モデルを使用して、提供された入力内で検出されたすべての既知のエンティティー・タイプへのメンションのリストを抽出します。サポートされる入力タイプには、テキスト、HTML、およびパブリック URL があります。API および使用する構文について詳しくは、[{{site.data.keyword.alchemylanguageshort}}&gt;Entities ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/smarterplanet/us/en/ibmwatson/developercloud/alchemy-language/api/v1/#entities){: new_window} を参照してください。

- **&lt;*input-type*&gt;GetTypedRelations**

    model パラメーターで指定されたカスタム・モデルを使用して、提供された入力内で検出された既知の関係のインスタンスのリストを抽出します。API および使用する構文について詳しくは、[{{site.data.keyword.alchemylanguageshort}}&gt;TypedRelations ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/smarterplanet/us/en/ibmwatson/developercloud/alchemy-language/api/v1/#typed-relations){: new_window} を参照してください。

#### 例

- 以下の API 呼び出しは、POST 本体で渡されたテキスト・ストリング内で既知のエンティティー・タイプを探します。要求には、作成されたモデルの ID と、カスタム・モデルを実行する権限を持つ Alchemy API 鍵を指定します。

    ```bash
    curl -d 'text=Mary had a little lamb.'
    "https://gateway-a.watsonplatform.net/calls/text/TextGetRankedNamedEntities?
    showSourceText=1&
    model=44476a63-c55t-451f-ad3r-8b23c0f4628c&
    apikey=s3wee88r25wwe2p6442w99g8t77phll5323kkf3a&
    outputMode=json"
    ```
    {: pre}

    ご使用の機械学習モデルによって `Mary` と `lamb` へのメンションが認識される場合、応答では、それらが返されます。

- 以下の API 呼び出しは、POST 本体で渡されたテキスト・ストリング内で既知の関係を探します。要求には、作成されたモデルの ID と、カスタム・モデルを実行する権限を持つ Alchemy API 鍵を指定します。

    ```bash
    curl -d 'text=Mary had a little lamb.'
    "https://gateway-a.watsonplatform.net/calls/text/TextGetTypedRelations?
    showSourceText=1&
    model=44476a63-c55t-451f-ad3r-8b23c0f4628c&
    apikey=s3wee88r25wwe2p6442w99g8t77phll5323kkf3a&
    outputMode=json"
    ```
    {: pre}

    ご使用の機械学習モデルによって `ownedBy` という関係が認識される場合、応答では、この関係が返されます。

> **注:** 例には、表示画面に合わせて見やすいフォーマットにするために、復帰が組み込まれています。API 構文には復帰を含めないでください。

詳しくは、[{{site.data.keyword.alchemylanguageshort}} 資料 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/watson/developercloud/doc/alchemylanguage/customizing.shtml){: new_window} を参照してください。

#### 関連情報

[{{site.data.keyword.alchemylanguageshort}} モデルの問題](/docs/services/watson-knowledge-studio/troubleshooting.html#wks_ts_deployed_model_deleted)

## IBM Watson Discovery への機械学習モデルのデプロイ
{: #wks_madiscovery}

モデルのパフォーマンスに満足できたら、そのバージョンを {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}} にデプロイできます。この機能により、アプリケーションが、デプロイされた機械学習モデルを使用して、データから得た洞察をエンリッチして、ドメインに関連がある概念や関係の認識を組み込むことができるようになります。

### 始めに

{{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}} サービス・インスタンスへの管理アクセス権限が必要なほか、それに関連付けられた {{site.data.keyword.Bluemix_notm}} スペース名およびインスタンス名を把握しておく必要があります。

### この作業について

機械学習モデルをデプロイするときは、デプロイするモデルのバージョンを選択します。

### 手順

機械学習モデルを {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}} にデプロイするには、以下のステップを実行します。

1. {{site.data.keyword.knowledgestudioshort}} 管理者またはプロジェクト管理者としてログインし、ワークスペースを選択します。
1. **「モデル管理 (Model Management)」** > **「バージョン (Versions)」** > **「機械学習 (Machine learning)」**タブを選択します。
1. デプロイするモデルのバージョンを選択します。

    モデルの作業バージョンが 1 つしかない場合は、現在のモデルのスナップショットを作成します。これによりモデルがバージョン化され、現行バージョンの改善を続行しながら、1 つのバージョンをデプロイできます。デプロイするためのオプションは、少なくとも 1 つのバージョンを作成するまで表示されません。

1. **「デプロイ」**をクリックし、{{site.data.keyword.discoveryshort}} へのデプロイを選択し、**「次へ」**をクリックします。
1. {{site.data.keyword.Bluemix_notm}} スペースとインスタンスを選択します。必要な場合、別の地域を選択します。
1. **「デプロイ」**をクリックします。
1. デプロイメント・プロセスには、数分かかる場合があります。デプロイメントの状況を確認するには、**「バージョン」**タブで、デプロイしたバージョンの横の**「状況 (Status)」**をクリックします。

    モデルのデプロイがまだ進行中の場合、状況には「公開中 (publishing)」と示されます。デプロイメントが完了すると、デプロイメントが成功した場合は状況が「使用可能 (available)」に変わり、問題が発生した場合は「エラー (error)」に変わります。

    モデルが使用可能になったら、モデル ID (model_id) をメモしておきます。この ID を {{site.data.keyword.discoveryshort}} サービスに提供して、サービスがカスタム・モデルを使用できるようにします。

### 次に行うこと

デプロイされたモデルを使用するには、{{site.data.keyword.discoveryshort}} サービスのエンリッチ構成プロセスの中で要求されたときにモデル ID を提供する必要があります。詳細については、[{{site.data.keyword.discoveryshort}} サービスの資料 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://www.ibm.com/watson/developercloud/doc/discovery/integrate-wks.shtml){: new_window} を参照してください。

## IBM Watson Natural Language Understanding への機械学習モデルのデプロイ
{: #wks_manlu}

モデルのパフォーマンスに満足できたら、そのバージョンを {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.nlushort}} にデプロイできます。この機能により、アプリケーションが、デプロイされた機械学習モデルを使用して、エンティティーや関係を含め、テキスト入力の意味構造のフィーチャーを分析できるようになります。

### 始めに

デプロイ先となる {{site.data.keyword.nlushort}} サービスが必要です。また、そのサービスに関連付けられている {{site.data.keyword.Bluemix_notm}} スペース名およびインスタンス名を把握しておく必要があります。スペース名またはインスタンス名を覚えていない場合は、{{site.data.keyword.Bluemix_notm}} にログインして、見つけてください。{{site.data.keyword.Bluemix_notm}} アカウントがない場合は、登録して、アカウントを作成してください。

### この作業について

機械学習モデルをデプロイするときは、デプロイするモデルのバージョンを選択します。

### 手順

機械学習モデルを {{site.data.keyword.nlushort}} サービスにデプロイするには、以下のステップを実行します。

1. {{site.data.keyword.knowledgestudioshort}} 管理者またはプロジェクト管理者としてログインし、ワークスペースを選択します。
1. **「モデル管理 (Model Management)」** > **「バージョン (Versions)」** > **「機械学習 (Machine learning)」**タブを選択します。
1. デプロイするモデルのバージョンを選択します。

    モデルの作業バージョンが 1 つしかない場合は、現在のモデルのスナップショットを作成します。これによりモデルがバージョン化され、現行バージョンの改善を続行しながら、1 つのバージョンをデプロイできます。デプロイするためのオプションは、少なくとも 1 つのバージョンを作成するまで表示されません。

1. **「デプロイ」**をクリックし、{{site.data.keyword.nlushort}} へのデプロイを選択し、**「次へ」**をクリックします。
1. {{site.data.keyword.Bluemix_notm}} スペースとインスタンスを選択します。必要な場合、別の地域を選択します。
1. **「デプロイ」**をクリックします。
1. デプロイメント・プロセスには、数分かかる場合があります。デプロイメントの状況を確認するには、**「バージョン」**タブで、デプロイしたバージョンの横の**「状況 (Status)」**をクリックします。モデルのデプロイがまだ進行中の場合、状況には「公開中 (publishing)」と示されます。デプロイメントが完了すると、デプロイメントが成功した場合は状況が「使用可能 (available)」に変わり、問題が発生した場合は「エラー (error)」に変わります。

    モデルが使用可能になったら、モデル ID (model_id) をメモしておきます。この ID を {{site.data.keyword.nlushort}} サービスに提供して、サービスがカスタム・モデルを使用できるようにします。

### 次に行うこと

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

詳細については、[{{site.data.keyword.nlushort}} の資料 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/watson/developercloud/doc/natural-language-understanding/index.html){: new_window} を参照してください。

## モデルのアンデプロイ
{: #undeploy-view-model}

モデルをアンデプロイする場合、またはモデル ID を検索する場合は、**「デプロイ済みモデル (Deployed Models)」**ページを表示します。**「デプロイ済みモデル (Deployed Models)」**ページには、自身がアクセスできるスペース内のサービスにデプロイ済みのすべての {{site.data.keyword.knowledgestudioshort}} モデルが表示されます。

モデルをアンデプロイするか、モデル ID を検索するには、以下のようにします。

1. {{site.data.keyword.knowledgestudioshort}} 管理者またはプロジェクト管理者としてログインし、ワークスペースを選択します。
1. 右上のメニュー・バーにある**「設定」**メニューから、**「デプロイ済みモデルの管理 (Manage deployed models)」**を選択します。
1. デプロイ済みモデルのリストから、表示またはアンデプロイするモデルを見つけます。
1. モデルをアンデプロイするには、その行の最後の列で**「モデルのアンデプロイ (Undeploy model)」**をクリックします。
1. モデル ID を見つけるには、**「モデル ID」**列を参照してください。

## IBM Watson Explorer での機械学習モデルの活用
{: #wks_maexport}

{{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer で使用できるように、トレーニングした機械学習モデルをエクスポートします。

### 始めに

関係タイプを識別し、それらにアノテーションを付けようとする場合は、モデルをエクスポートする前に、少なくとも 2 つの関係タイプを定義し、グランドトゥルース内で関係のインスタンスにアノテーションを付ける必要があります。1 つの関係タイプのみを定義し、アノテーションを付けた場合、この後、{{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer リリース 11.0.1.0 で問題が発生する可能性があります。

### この作業について

特定のドメインのエンティティーおよび関係を認識するように機械学習モデルがトレーニングされたので、このモデルを {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer で活用できます。

[このリンク ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.youtube.com/watch?v=1VoS-xczBow&amp;feature=youtu.be){: new_window} をクリックすると、モデルをエクスポートし、それを {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer で使用する方法を示す 2 分弱のビデオを視聴できます。

### 手順

{{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer で機械学習モデルを活用するには、以下のステップを実行します。

1. {{site.data.keyword.knowledgestudioshort}} 管理者またはプロジェクト管理者としてログインし、ワークスペースを選択します。
1. **「モデル管理 (Model Management)」** > **「バージョン (Versions)」** > **「機械学習 (Machine learning)」**タブを選択します。
1. **「現行モデルのエクスポート (Export current model)」**をクリックします。

    無料プランに加入している場合、エクスポート・オプションは使用できません。

    モデルは ZIP ファイルとして保存され、ファイルのダウンロードを求めるプロンプトが出されます。

1. ファイルをローカル・システムにダウンロードします。
1. {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer アプリケーションから、モデルをインポートします。

    これで、モデルを {{site.data.keyword.watson}} Explorer Content Analytics の機械学習モデルにマップできます。マッピング・ステップを実行した後、文書をクロールすると、モデルが認識するエンティティーおよび関係のインスタンスがモデルによって検出されます。{{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer にモデルをインポートし、構成する方法については、統合について説明している技術資料 ([http://www.ibm.com/support/docview.wss?uid=swg27048147 ![外部リンク・アイコン](../../icons/launch-glyph.svg "リンク・アイコン")](http://www.ibm.com/support/docview.wss?uid=swg27048147){: new_window} を参照してください。

#### 関連タスク

[{{site.data.keyword.watson}} Explorer Content Analytics からの分析済み文書のエクスポート](/docs/services/watson-knowledge-studio/preannotation.html#wks_uimawexca)
