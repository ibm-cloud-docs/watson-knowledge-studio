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

この文書は、{{site.data.keyword.cloud}} 上の {{site.data.keyword.knowledgestudiofull}} に関するものです。以前のバージョンの {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 向けの資料を参照するには、[このリンクをクリック ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/docs/services/knowledge-studio/release-notes.html){: new_window} してください。
{: tip}

# リリース・ノート
{: #release-notes}

{{site.data.keyword.knowledgestudiofull}} には、以下の新機能と変更があります。
{: shortdesc}

## 2018 年 3 月
{: #march2018}

### 新機能および変更
{: #new-march2018}

- 自身がアクセスできるスペース内のサービスにデプロイ済みのすべての {{site.data.keyword.knowledgestudioshort}} モデルを表示できる**「デプロイ済みモデル (Deployed Models)」**ページが使用可能です。**「デプロイ済みモデル (Deployed Models)」**ページを表示するには、右上のメニュー・バーにある**「設定」**メニューから**「デプロイ済みモデルの管理 (Manage deployed models)」**をクリックします。**「デプロイ済みモデル (Deployed Models)」**ページでモデルをアンデプロイしたり、表示したりする方法については、[機械学習モデルのアンデプロイ](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model)および[ルール・ベース・モデルのアンデプロイ](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model)の説明を参照してください。
- フランス語に翻訳された {{site.data.keyword.knowledgestudioshort}} インターフェースが使用可能になりました。
- {{site.data.keyword.alchemylanguagefull}} は、事前アノテーターとして使用できなくなりました。{{site.data.keyword.alchemylanguageshort}} の代わりに、{{site.data.keyword.nlushort}} を使用して、文書に事前にアノテーションを付けることができます。詳しくは、[アノテーションのブートストラッピング](/docs/services/watson-knowledge-studio/preannotation.html)を参照してください。

## 2017 年 12 月
{: #december2017}

### 新機能および変更
{: #new-december2017}

- {{site.data.keyword.cloud_notm}} 上の {{site.data.keyword.knowledgestudioshort}} が立ち上げられました。マイグレーション・プロセスおよびスケジュールについては、[{{site.data.keyword.cloud_notm}} へのマイグレーション](/docs/services/watson-knowledge-studio/client-migration.html)を参照してください。
- ナビゲーションが再設計されました。ナビゲーションの変更について詳しくは、2017 年 9 月リリース・ノートの[表 2](#september2017) を参照してください。
- 事前アノテーターとして {{site.data.keyword.nlufull}} が追加されました。
- 「サービスの詳細」ページにユーザー管理およびストレージ管理の設定が追加されました。ユーザーの追加については、[チームのアセンブル](/docs/services/watson-knowledge-studio/team.html)を参照してください。ストレージ制限の設定については、[トラブルシューティング > ストレージ・スペースの問題](/docs/services/watson-knowledge-studio/troubleshooting.html#storage)を参照してください。
- モデルの品質評価や、品質を改善する方法に関するガイダンスを提供する「パフォーマンス」ページが追加されました。

## 2017 年 11 月
{: #november2017}

### 変更
{: #new-november2017}

- ダウンロードされたコーパス内で一部の関係アノテーションが欠落する問題が修正されました。
- モデルの状況が**「なし」**である場合、モデルをデプロイメントから撤回できなかった問題が修正されました。
- モデルを韓国語で評価できなかった問題が修正されました。

## 2017 年 10 月
{: #october2017}

### 変更
{: #new-october2017}

- {{site.data.keyword.Bluemix_notm}} [試験的](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)リリースで見られた、ブラウザーのウィンドウを最新表示するまで**「エクスポート」**ボタンが使用可能にならない問題が修正されました。
- {{site.data.keyword.Bluemix_notm}} [試験的](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)リリースに含まれたボタンのラベルやツールチップが、_アップロード_ や_ダウンロード_ という用語への変更に合わせて修正されました。タイプ・システム、文書、および辞書を指す場合、_インポート_ および_エクスポート_ の代わりにこれらの用語が使用されます。
- {{site.data.keyword.Bluemix_notm}} [試験的](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)リリースで見られた、{{site.data.keyword.knowledgestudioshort}} 「ユーザー・アカウント管理 (User Account Management)」ページで説明の更新が遅延するのが修正されました。
- インターフェースの事前アノテーション・セクションで、機械学習モデル、ルール・ベース・モデル、辞書、および {{site.data.keyword.alchemylanguagefull}} の機能を明確にするために、いくつかの GUI が変更されました。ボタン・ラベルを**「実行」**から**「事前アノテーション (Pre-annotate)」**に変更したほか、ウィンドウのタイトルを**「アノテーターの実行 (Run Annotator)」**から**「事前アノテーションの実行 (Run Pre-annotation)」**に変更しました。また、人間が文書にアノテーションを付けた後は、自動アノテーションを追加できないことを明確にするためにエラー・メッセージを変更しました。
- 辞書ベースのトークナイザーを使用するプロジェクトまたはワークスペースを対象に、グランドトゥルースのない文書をインポートした場合に空のセンテンスが表示される問題が修正されました。

## 2017 年 9 月
{: #september2017}

### 新機能および変更
{: #new-sept17}

- {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.Bluemix}} の新しいフロントエンド・ユーザー・エクスペリエンスが[試験的](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)サービスとしてリリースされました。変更には、再編成されたナビゲーションと新しいモデル・パフォーマンス分析ページが含まれます。ナビゲーションの変更の要約については、既知の問題の下にある表を参照してください。
- 中国語 (簡体字) およびオランダ語の言語サポートが追加されました。

### 既知の問題
{: #issues-sept17}

- ルール・ベース・モデルの場合、クラスおよびエンティティー・タイプをマップした後、ブラウザー・ウィンドウを最新表示するまで**「エクスポート」**ボタンが使用可能になりません。
- {{site.data.keyword.Bluemix_notm}} [試験的](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)リリースでは、資料の用語の一部が新しいインターフェースと一致しません。資料は、{{site.data.keyword.IBM_notm}} Marketplace のインターフェースと一致しています。[試験的](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)リリースでは、以下の用語が変更されました。

| {{site.data.keyword.IBM_notm}} Marketplace の用語 | {{site.data.keyword.Bluemix_notm}} の用語 | メモ |
|----------|----------|----------|
| _プロジェクト_ | _ワークスペース_ | {{site.data.keyword.Bluemix_notm}} も_プロジェクト_ という用語を使用しているため、この用語は変更されました。 |
| _インポート_ と_エクスポート_ | _アップロード_ と_ダウンロード_ | _インポート_ および_エクスポート_ という用語は、文書およびエンティティー・タイプに関して使用される場合、_アップロード_ および_ダウンロード_ と呼ばれるようになりました。モデルを {{site.data.keyword.watson}} Explorer などのアプリケーションにエクスポートすることを指す場合は、引き続き_エクスポート_ という用語が使用されます。|
{: caption="表 1. {{site.data.keyword.Bluemix_notm}} バージョンでの用語の変更" caption-side="top"}

- {{site.data.keyword.Bluemix_notm}} [試験的](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)リリースでは、資料にあるタスク・ステップの一部が新しいインターフェースと一致しません。資料は、{{site.data.keyword.IBM_notm}} Marketplace のインターフェースと一致しています。以下の表に、[試験的](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)リリースでのナビゲーションの変更を要約します。

| 機能 | {{site.data.keyword.IBM_notm}} Marketplace での場所 | {{site.data.keyword.Bluemix_notm}} での場所
|----------|----------|----------|
|「アノテーター・コンポーネント (Annotator Component)」タブ | メイン・ナビゲーション | 存在しなくなりました |
|「混同行列 (Confusion Matrix)」表 (「統計」タブ) | 「アノテーター・コンポーネント (Annotator Component)」 > 「詳細」 | 「モデル管理 (Model Management)」 > 「パフォーマンス」 > 「詳細統計 (Detailed Statistics)」リンク |
|「辞書 (Dictionaries)」タブ | メイン・ナビゲーション | 「アセット & ツール (Assets & Tools)」 > 「事前アノテーター (Pre-annotators)」 |
|「辞書マッピング (Dictionary Mapping)」ページ | アノテーター・コンポーネント (Annotator Component) | 「アセット & ツール (Assets & Tools)」 > 「事前アノテーター (Pre-annotators)」 |
|「エンティティー・タイプ」タブ | タイプ・システム | 「アセット & ツール (Assets & Tools)」 > 「エンティティー・タイプ」 |
|グランドトゥルース・エディター (Ground Truth Editor) | ヒューマン・アノテーション (Human Annotation) | 「文書アノテーション (Document Annotation)」タブ |
|グランドトゥルース・エディター (Ground Truth Editor) 「設定」タブ | ヒューマン・アノテーション (Human Annotation) | 「設定」 > 「文書アノテーション設定 (Document Annotation Settings)」 |
|モデル (実行およびエクスポート) | アノテーター・コンポーネント (Annotator Component) | 「モデル管理 (Model Management)」 > 「バージョン」 |
|「ルール」タブ | メイン・ナビゲーション | 「文書アノテーション (Document Annotation)」 > 「ルール」 |
|「統計」タブ | 「アノテーター・コンポーネント (Annotator Component)」 > 「詳細」 | 「モデル管理 (Model Management)」 > 「パフォーマンス」 |
|「サマリー」表 (「統計」タブ) | 「アノテーター・コンポーネント (Annotator Component)」 > 「詳細」 | 「モデル管理 (Model Management)」 > 「パフォーマンス」 > 「詳細統計 (Detailed Statistics)」リンク |
|「タイプ・マッピング (Type Mapping)」タブ (ルール・ベース・モデルの場合) | 「アノテーター・コンポーネント (Annotator Component)」 > 「詳細」 | 「モデル管理 (Model Management)」 > 「バージョン」 > 「ルール・ベース・モデルのタイプ・マッピング (Rule-based model type mapping)」 |
{: caption="表 2. {{site.data.keyword.Bluemix_notm}} バージョンでのナビゲーションの変更" caption-side="top"}

## 2017 年 7 月
{: #july2017}

- 一部のケースでヘッダーが消える原因となった問題を修正
- インフラストラクチャー・コンポーネントにセキュリティー更新を適用

## 2017 年 6 月
{: #june2017}

- 一定の条件下で大規模データを処理する際の安定度の向上
- 判定エラーに関する問題を修正

## 2017 年 5 月
{: #may2017}

- プロジェクト、文書セットなどのさまざまなオブジェクトを名前変更できる機能を追加
- NLU モデルを特定の {{site.data.keyword.Bluemix}} 地域にデプロイできる機能を追加
- IAA の大きな表を表示する際のパフォーマンス改善
- マイナーな問題を修正
- セキュリティー・フィックスの適用

## 2017 年 4 月
{: #april2017}

- {{site.data.keyword.knowledgestudioshort}} Premium の安定度の向上
- ビジネス・メトリックの使用分析の追加

## 2017 年 4 月より前のリリース

[{{site.data.keyword.IBM_notm}} 技術情報 #1986001 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://www.ibm.com/support/docview.wss?uid=swg21986001){: new_window} を参照してください。
