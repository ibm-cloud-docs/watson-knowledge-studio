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

この文書は、{{site.data.keyword.cloud}} 上の {{site.data.keyword.knowledgestudiofull}} に関するものです。以前のバージョンの {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 向けの資料を参照するには、[このリンクをクリック ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/docs/services/knowledge-studio/rule-annotator-model-use.html){: new_window} してください。
{: tip}

# ルール・ベース・モデルの使用
{: #wks_rule_publish}

{{site.data.keyword.knowledgestudioshort}} で作成したルール・ベース・モデルを他の {{site.data.keyword.watson}} アプリケーションで使用できるようにすることによって、モデルを活用します。
{: shortdesc}

**重要**: ルール・ベース・モデルをデプロイすると、それらのサービスで[試験的](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)機能としてモデルを使用可能にできます。

サービスで使用するためにモデルをデプロイするためには、事前にサービスへのサブスクリプションが必要です。{{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} サービスは、{{site.data.keyword.IBM_notm}} のクラウド・プラットフォームである {{site.data.keyword.Bluemix_notm}} 上でホストされます。プラットフォームについて詳しくは、[{{site.data.keyword.Bluemix_notm}} とは? ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.ng.bluemix.net/docs/overview/whatisbluemix.html){: new_window} を参照してください。いずれかの {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} サービスにサブスクライブするには、[{{site.data.keyword.Bluemix_notm}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.ng.bluemix.net/){: new_window} Web サイトからアカウントを作成します。

一部のサービスでは、{{site.data.keyword.Bluemix_notm}} スペース名やサービス・インスタンス名など、デプロイ先として計画しているサービス・インスタンスに関する詳細を把握しておく必要があります。スペース名やインスタンス名の情報は、{{site.data.keyword.Bluemix_notm}} 「サービス」ページから入手できます。

ルール・ベース・モデルを使用して、新規文書に事前にアノテーションを付けることもできます。詳しくは、[ルール・ベース・モデルを使用した文書の事前アノテーション付け](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotrule)を参照してください。

## AlchemyLanguage へのルール・ベース・モデルのデプロイ
{: #wks_rule_bluemix}

この機能により、アプリケーションが、デプロイされたルール・ベース・モデルを使用して、ドメイン内の文書からエンティティーを検索し、抽出できるようになります。

**重要**: これは現在、サービスの[試験的](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)機能です。

### 始めに

このカスタム・モデルを使用するには、{{site.data.keyword.alchemylanguageshort}} サービスの拡張プランが必要です。

### この作業について

このサービスにデプロイするには、{{site.data.keyword.IBM_notm}} {{site.data.keyword.alchemylanguageshort}} のアクセス・キーが必要です。

このキーは、カスタム・モデルを公開する権限があるアカウントに属している必要があります。そうでないと、モデルは正常にデプロイされても、モデルを使用できなくなります。

ルール・ベース・モデルをデプロイするときは、デプロイするモデルのバージョンを選択します。初めてモデルを {{site.data.keyword.alchemylanguageshort}} にデプロイするときに、キーを指定する必要があります。その後は、デプロイする複数のバージョンのモデルでそのキーを再使用できます。キーごとに、同時にデプロイできるモデルの最大数が決められています。

### 手順

ルール・ベース・モデルを {{site.data.keyword.alchemylanguageshort}} にデプロイするには、以下のようにします。

1. {{site.data.keyword.knowledgestudioshort}} 管理者またはプロジェクト管理者としてログインし、ワークスペースを選択します。
1. **「モデル管理 (Model Management)」** > **「バージョン (Versions)」** > **「ルール・ベース (Rule-based)」**タブを選択します。
1. デプロイするモデルのバージョンを選択します。

    モデルの作業バージョンが 1 つしかない場合は、**「デプロイメントのために保存 (Save for Deployment)」**をクリックして、現行モデルをデプロイメント用に保存します。**「デプロイメントのために保存 (Save for Deployment)」**をクリックすると、モデルのバージョンが作成され、現行バージョンの改善を続行しながら、1 つのバージョンをデプロイできます。バージョンの保存には、数分かかる場合があります。デプロイするためのオプションは、バージョンが作成されるまで表示されません。

1. **「デプロイ」**をクリックし、{{site.data.keyword.alchemylanguageshort}} へのデプロイを選択し、**「次へ」**をクリックします。
1. {{site.data.keyword.alchemylanguageshort}} から取得したキーを入力するか、再使用するキーを持つ、以前にデプロイされたバージョンのモデルを選択し、**「デプロイ」** をクリックします。キーが有効な場合は、モデル ID を含む確認が表示されます。この確認は、モデルがアプリケーションで使用できる状態にあることを意味するものではありません。
1. デプロイメント・プロセスには、数分かかる場合があります。デプロイメントの状況を確認するには、デプロイしたバージョンの横にある**「状況 (Status)」**をクリックします。モデルのデプロイがまだ進行中の場合、状況には「公開中 (publishing)」と示されます。デプロイメントが完了すると、デプロイメントが成功した場合は状況が「使用可能 (available)」に変わり、問題が発生した場合は「エラー (error)」に変わります。

    状況情報には、モデル ID、{{site.data.keyword.alchemyapishort}} キーの最後の 4 桁、およびデプロイメント・プロセスのログが含まれます。モデル ID (model_id) は、アプリケーションが機械学習モデルを呼び出す方法です。後からモデル ID にプログラマチックにアクセスする方法がないため、このモデル ID をメモしておいてください。{{site.data.keyword.alchemyapishort}} キーを使用して、キーごとのデプロイメントの数を追跡します。

### 次に行うこと

デプロイされたモデルを使用するには、モデル ID をアプリケーションの API 呼び出しにコピー・アンド・ペーストする必要があります。

> **重要:** `GET /info/models` {{site.data.keyword.alchemylanguageshort}} API 呼び出しを使用してプログラマチックにルール・ベース・モデルのモデル ID を取得することはできません。この呼び出しでは、機械学習モデルのモデル ID にはアクセスできますが、ルール・ベース・モデル ID にはアクセスできません。

この呼び出しでは、モデルで使用する {{site.data.keyword.alchemylanguageshort}} サービスと、{{site.data.keyword.alchemyapishort}} アクセス・キーも指定する必要があります。

以下のエンドポイントがサポートされます。

- **&lt;*input-type*&gt;GetRankedNamedEntities**

    model パラメーターで指定されたカスタム・モデルを使用して、提供された入力内で検出されたすべての既知のエンティティー・タイプへのメンションのリストを抽出します。サポートされる入力タイプには、テキスト、HTML、およびパブリック URL があります。API および使用する構文について詳しくは、[{{site.data.keyword.alchemylanguageshort}}&gt;Entities ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/smarterplanet/us/en/ibmwatson/developercloud/alchemy-language/api/v1/#entities){: new_window} を参照してください。

## IBM Watson Discovery へのルール・ベース・モデルのデプロイ
{: #wks_rule_discovery}

モデルをデプロイして、{{site.data.keyword.discoveryshort}} サービスを使用するアプリケーションが、文書のエンリッチ時にルール・ベース・モデルを使用してエンティティーを検索し、抽出できるようにします。

**重要**: これは現在、サービスの[試験的](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)機能です。

### 始めに

{{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}} サービス・インスタンスへの管理アクセス権限が必要なほか、それに関連付けられた {{site.data.keyword.Bluemix_notm}} スペース名およびインスタンス名を把握しておく必要があります。

### 手順

ルール・ベース・モデルを {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}} にデプロイするには、以下のステップを実行します。

1. {{site.data.keyword.knowledgestudioshort}} 管理者またはプロジェクト管理者としてログインし、ワークスペースを選択します。
1. **「モデル管理 (Model Management)」** > **「バージョン (Versions)」** > **「ルール・ベース (Rule-based)」**タブを選択します。
1. デプロイするモデルのバージョンを選択します。

    モデルの作業バージョンが 1 つしかない場合は、**「デプロイメントのために保存 (Save for Deployment)」**をクリックして、現行モデルをデプロイメント用に保存します。これによりモデルがバージョン化され、現行バージョンの改善を続行しながら、1 つのバージョンをデプロイできます。バージョンの保存には、数分かかる場合があります。デプロイするためのオプションは、バージョンが作成されるまで表示されません。

1. **「デプロイ」**をクリックし、{{site.data.keyword.discoveryshort}} へのデプロイを選択し、**「次へ」**をクリックします。
1. {{site.data.keyword.Bluemix_notm}} スペースとインスタンスを指定します。必要な場合、別の地域を選択します。
1. **「デプロイ」**をクリックします。
1. デプロイメント・プロセスには、数分かかる場合があります。デプロイメントの状況を確認するには、**「バージョン」**タブで、デプロイしたバージョンの横の**「状況 (Status)」**をクリックします。

    モデルのデプロイがまだ進行中の場合、状況には「公開中 (publishing)」と示されます。デプロイメントが完了すると、デプロイメントが成功した場合は状況が「使用可能 (available)」に変わり、問題が発生した場合は「エラー (error)」に変わります。

    モデルが使用可能になったら、モデル ID (model_id) をメモしておきます。この ID を {{site.data.keyword.discoveryshort}} サービスに提供して、サービスがカスタム・モデルを使用できるようにします。

### 次に行うこと

デプロイされたモデルを使用するには、{{site.data.keyword.discoveryshort}} サービスのエンリッチ構成プロセスの中で要求されたときにモデル ID を提供する必要があります。

## IBM Watson Natural Language Understanding へのルール・ベース・モデルのデプロイ
{: #wks_rule_nlu}

ルール・ベース・モデルをデプロイして、{{site.data.keyword.nlushort}} サービスを使用するアプリケーションがそのモデルを使用して、ドメインに関連するエンティティーを検索し、抽出できるようにします。

**重要**: これは現在、サービスの[試験的](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)機能です。

### 始めに

{{site.data.keyword.nlushort}} サービス・インスタンスへの管理アクセス権限が必要なほか、それに関連付けられた {{site.data.keyword.Bluemix_notm}} スペース名およびインスタンス名を把握しておく必要があります。

### 手順

ルール・ベース・モデルを {{site.data.keyword.nlushort}} にデプロイするには、以下のステップを実行します。

1. {{site.data.keyword.knowledgestudioshort}} 管理者またはプロジェクト管理者としてログインし、ワークスペースを選択します。
1. **「モデル管理 (Model Management)」** > **「バージョン (Versions)」** > **「ルール・ベース (Rule-based)」**タブを選択します。
1. デプロイするモデルのバージョンを選択します。

    モデルの作業バージョンが 1 つしかない場合は、**「デプロイメントのために保存 (Save for Deployment)」**をクリックして、現行モデルをデプロイメント用に保存します。これによりモデルがバージョン化され、現行バージョンの改善を続行しながら、1 つのバージョンをデプロイできます。バージョンの保存には、数分かかる場合があります。デプロイするためのオプションは、バージョンが作成されるまで表示されません。

1. **「デプロイ」**をクリックし、{{site.data.keyword.nlushort}} へのデプロイを選択し、**「次へ」**をクリックします。
1. {{site.data.keyword.Bluemix_notm}} スペースとインスタンスを指定します。必要な場合、別の地域を選択します。
1. **「デプロイ」**をクリックします。
1. デプロイメント・プロセスには、数分かかる場合があります。デプロイメントの状況を確認するには、**「バージョン」**タブで、デプロイしたバージョンの横の**「状況 (Status)」**をクリックします。

    モデルのデプロイがまだ進行中の場合、状況には「公開中 (publishing)」と示されます。デプロイメントが完了すると、デプロイメントが成功した場合は状況が「使用可能 (available)」に変わり、問題が発生した場合は「エラー (error)」に変わります。

    モデルが使用可能になったら、モデル ID (model_id) をメモしておきます。この ID を {{site.data.keyword.nlushort}} サービスに提供して、サービスがカスタム・モデルを使用できるようにします。

### 次に行うこと

デプロイされたモデルを使用するには、カスタム・モデルのモデル ID を `entities.model` パラメーターに指定する必要があります。

{{site.data.keyword.nlushort}} `GET /analyze` 要求でモデルを使用して、エンティティーを抽出できます。

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

## IBM Watson Explorer でのルール・ベース・モデルの活用
{: #wks_rule_export}

ルール・ベース・モデルの作成時に生成された PEAR ファイルをエクスポートして、{{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer で使用できるようにします。

### 手順

{{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer でルール・ベース・モデルを活用するには、以下のステップを実行します。

1. {{site.data.keyword.knowledgestudioshort}} 管理者またはプロジェクト管理者としてログインし、ワークスペースを選択します。
1. **「モデル管理 (Model Management)」** > **「バージョン (Versions)」** > **「ルール・ベース (Rule-based)」**タブを選択します。
1. **「現行モデルのエクスポート (Export current model)」**をクリックします。

    無料プランに加入している場合、エクスポート・オプションは使用できません。

    モデルは PEAR ファイルとして保存され、ファイルのダウンロードを求めるプロンプトが出されます。PEAR (処理エンジン・アーカイブ) ファイルは、UIMA コンポーネント用の UIMA 標準パッケージ化フォーマットです。モデルは、UIMA アプリケーション内で配布および再利用できるように、PEAR 形式で保存されます。

1. ファイルをローカル・システムにダウンロードします。
1. {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer アプリケーションから、PEAR ファイルをインポートします。
