---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-14"

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

この文書は、{{site.data.keyword.cloud}} 上の {{site.data.keyword.knowledgestudiofull}} に関するものです。 以前のバージョンの {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 向けの資料を参照するには、[このリンクをクリック ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/docs/services/knowledge-studio/rule-annotator-model-use.html){: new_window} してください。
{: tip}

# ルール・ベース・モデルの使用
{: #wks_rule_publish}

{{site.data.keyword.knowledgestudioshort}} で作成したルール・ベース・モデルを他の {{site.data.keyword.watson}} アプリケーションで使用できるようにすることによって、モデルを活用します。
{: shortdesc}

**重要**: ルール・ベース・モデルをデプロイすると、それらのサービスで[試験的](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)機能としてモデルを使用可能にできます。

サービスで使用するためにモデルをデプロイするためには、事前にサービスへのサブスクリプションが必要です。 {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} サービスは、{{site.data.keyword.IBM_notm}} のクラウド・プラットフォームである {{site.data.keyword.Bluemix_notm}} 上でホストされます。 プラットフォームについて詳しくは、[{{site.data.keyword.Bluemix_notm}} とは? ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.ng.bluemix.net/docs/overview/whatisbluemix.html){: new_window} を参照してください。 いずれかの {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} サービスにサブスクライブするには、[{{site.data.keyword.Bluemix_notm}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.ng.bluemix.net/){: new_window} Web サイトからアカウントを作成します。

一部のサービスでは、{{site.data.keyword.Bluemix_notm}} スペース名やサービス・インスタンス名など、デプロイ先として計画しているサービス・インスタンスに関する詳細を把握しておく必要があります。 スペース名やインスタンス名の情報は、{{site.data.keyword.Bluemix_notm}} 「サービス」ページから入手できます。

ルール・ベース・モデルを使用して、新規文書に事前にアノテーションを付けることもできます。 詳しくは、[ルール・ベース・モデルを使用した文書の事前アノテーション付け](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotrule)を参照してください。

## IBM Watson Discovery へのルール・ベース・モデルのデプロイ
{: #wks_rule_discovery}

モデルをデプロイして、{{site.data.keyword.discoveryshort}} サービスを使用するアプリケーションが、文書のエンリッチ時にルール・ベース・モデルを使用してエンティティーを検索し、抽出できるようにします。

**重要**: これは現在、サービスの[試験的](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)機能です。

### 始めに
{: #wks_rule_discovery_prereqs}

{{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}} サービス・インスタンスへの管理アクセス権限が必要なほか、それに関連付けられた {{site.data.keyword.Bluemix_notm}} スペース名およびインスタンス名を把握しておく必要があります。

### 手順
{: #wks_rule_discovery_procedure}

ルール・ベース・モデルを {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}} にデプロイするには、以下のステップを実行します。

1. {{site.data.keyword.knowledgestudioshort}} 管理者またはプロジェクト管理者としてログインし、ワークスペースを選択します。
1. **「ルール・ベース・モデル (Rule-based Model)」**>**「バージョン (Versions)」**>**「ルール・ベース・モデル (Rule-based Model)」**タブを選択します。
1. デプロイするモデルのバージョンを選択します。

    モデルの作業バージョンが 1 つしかない場合は、**「デプロイメントのために保存 (Save for Deployment)」**をクリックして、現行モデルをデプロイメント用に保存します。 これによりモデルがバージョン化され、現行バージョンの改善を続行しながら、1 つのバージョンをデプロイできます。 バージョンの保存には、数分かかる場合があります。 デプロイするためのオプションは、バージョンが作成されるまで表示されません。

    **注**: 各バージョンは、1 つのサービス・インスタンスにのみデプロイできます。同じモデルを複数のインスタンスにデプロイする場合は、インスタンスごとに 1 つのバージョンを作成します。

1. **「デプロイ」**をクリックし、{{site.data.keyword.discoveryshort}} へのデプロイを選択し、**「次へ」**をクリックします。
1. {{site.data.keyword.Bluemix_notm}} スペースとインスタンスを指定します。 必要な場合、別の地域を選択します。
1. **「デプロイ」**をクリックします。
1. デプロイメント・プロセスには、数分かかる場合があります。 デプロイメントの状況を確認するには、**「バージョン」**タブで、デプロイしたバージョンの横の**「状況 (Status)」**をクリックします。

    モデルのデプロイがまだ進行中の場合、状況には「公開中 (publishing)」と示されます。 デプロイメントが完了すると、デプロイメントが成功した場合は状況が「使用可能 (available)」に変わり、問題が発生した場合は「エラー (error)」に変わります。

    モデルが使用可能になったら、モデル ID (model_id) をメモしておきます。 この ID を {{site.data.keyword.discoveryshort}} サービスに提供して、サービスがカスタム・モデルを使用できるようにします。

### 次に行うこと
{: #wks_rule_discovery_next}

デプロイされたモデルを使用するには、{{site.data.keyword.discoveryshort}} サービスのエンリッチ構成プロセスの中で要求されたときにモデル ID を提供する必要があります。

## IBM Watson Natural Language Understanding へのルール・ベース・モデルのデプロイ
{: #wks_rule_nlu}

ルール・ベース・モデルをデプロイして、{{site.data.keyword.nlushort}} サービスを使用するアプリケーションがそのモデルを使用して、ドメインに関連するエンティティーを検索し、抽出できるようにします。

**重要**: これは現在、サービスの[試験的](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)機能です。

### 始めに
{: #wks_rule_prereqs}

{{site.data.keyword.nlushort}} サービス・インスタンスへの管理アクセス権限が必要なほか、それに関連付けられた {{site.data.keyword.Bluemix_notm}} スペース名およびインスタンス名を把握しておく必要があります。

### 手順
{: #wks_rule_procedure}

ルール・ベース・モデルを {{site.data.keyword.nlushort}} にデプロイするには、以下のステップを実行します。

1. {{site.data.keyword.knowledgestudioshort}} 管理者またはプロジェクト管理者としてログインし、ワークスペースを選択します。
1. **「ルール・ベース・モデル (Rule-based Model)」**>**「バージョン (Versions)」**>**「ルール・ベース・モデル (Rule-based Model)」**タブを選択します。
1. デプロイするモデルのバージョンを選択します。

    モデルの作業バージョンが 1 つしかない場合は、**「デプロイメントのために保存 (Save for Deployment)」**をクリックして、現行モデルをデプロイメント用に保存します。 これによりモデルがバージョン化され、現行バージョンの改善を続行しながら、1 つのバージョンをデプロイできます。 バージョンの保存には、数分かかる場合があります。 デプロイするためのオプションは、バージョンが作成されるまで表示されません。

    **注**: 各バージョンは、1 つのサービス・インスタンスにのみデプロイできます。同じモデルを複数のインスタンスにデプロイする場合は、インスタンスごとに 1 つのバージョンを作成します。

1. **「デプロイ」**をクリックし、{{site.data.keyword.nlushort}} へのデプロイを選択し、**「次へ」**をクリックします。
1. {{site.data.keyword.Bluemix_notm}} スペースとインスタンスを指定します。 必要な場合、別の地域を選択します。
1. **「デプロイ」**をクリックします。
1. デプロイメント・プロセスには、数分かかる場合があります。 デプロイメントの状況を確認するには、**「バージョン」**タブで、デプロイしたバージョンの横の**「状況 (Status)」**をクリックします。

    モデルのデプロイがまだ進行中の場合、状況には「公開中 (publishing)」と示されます。 デプロイメントが完了すると、デプロイメントが成功した場合は状況が「使用可能 (available)」に変わり、問題が発生した場合は「エラー (error)」に変わります。

    モデルが使用可能になったら、モデル ID (model_id) をメモしておきます。 この ID を {{site.data.keyword.nlushort}} サービスに提供して、サービスがカスタム・モデルを使用できるようにします。

### 次に行うこと
{: #wks_rule_next}

デプロイされたモデルを使用するには、カスタム・モデルのモデル ID を `entities.model` パラメーターに指定する必要があります。

{{site.data.keyword.nlushort}} `GET /analyze` 要求でモデルを使用して、エンティティーを抽出できます。

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

## IBM Watson Explorer でのルール・ベース・モデルの活用
{: #wks_rule_export}

ルール・ベース・モデルの作成時に生成された PEAR ファイルをエクスポートして、{{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer で使用できるようにします。

### 手順
{: #wks_rule_export_procedure}

{{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer でルール・ベース・モデルを活用するには、以下のステップを実行します。

1. {{site.data.keyword.knowledgestudioshort}} 管理者またはプロジェクト管理者としてログインし、ワークスペースを選択します。
1. **「ルール・ベース・モデル (Rule-based Model)」**>**「バージョン (Versions)」**>**「ルール・ベース・モデル (Rule-based Model)」**タブを選択します。
1. **「現行モデルのエクスポート (Export current model)」**をクリックします。

    ライト・プランに加入している場合、エクスポート・オプションは使用できません。

    モデルは PEAR ファイルとして保存され、ファイルのダウンロードを求めるプロンプトが出されます。 PEAR (処理エンジン・アーカイブ) ファイルは、UIMA コンポーネント用の UIMA 標準パッケージ化フォーマットです。 モデルは、UIMA アプリケーション内で配布および再利用できるように、PEAR 形式で保存されます。

1. ファイルをローカル・システムにダウンロードします。
1. {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer アプリケーションから、PEAR ファイルをインポートします。
