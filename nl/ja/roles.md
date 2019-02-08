---

copyright:
  years: 2018
lastupdated: "2018-07-02"

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

# {{site.data.keyword.knowledgestudioshort}} のユーザー役割
{: #roles}

{{site.data.keyword.knowledgestudiofull}} の役割は、機械学習モデルまたはルール・ベース・モデルを作成するユーザーのチームを編成するために使用されます。
{: shortdesc}

## {{site.data.keyword.knowledgestudioshort}} の役割に関する注
{: #notes}

- {{site.data.keyword.knowledgestudioshort}} のユーザー役割は、以下のレベルで管理されます。
  - {{site.data.keyword.cloud}} の役割は、{{site.data.keyword.cloud_notm}} サービスへのアクセスを制御します。{{site.data.keyword.knowledgestudioshort}} では、アクセス制御に Cloud Foundry を使用しますが、この場合、{{site.data.keyword.knowledgestudioshort}} ユーザーが開発者の役割を持っている必要があります。詳しくは、[Cloud Foundry アクセス権限 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/docs/iam/cfaccess.html){: new_window} を参照してください。
  - {{site.data.keyword.knowledgestudioshort}} の役割は、このページで説明されているように、{{site.data.keyword.knowledgestudioshort}} 機能へのアクセスを制御します。
- {{site.data.keyword.knowledgestudioshort}} のインスタンスを作成する場合、{{site.data.keyword.knowledgestudioshort}} 役割は必要ありません。ただし、個人が {{site.data.keyword.knowledgestudioshort}} のインスタンスを作成する場合は、{{site.data.keyword.knowledgestudioshort}} を起動する最初のユーザーに {{site.data.keyword.knowledgestudioshort}} の管理者の役割が割り当てられます。
- ワークスペースを管理するには、管理者がそのワークスペースにプロジェクト管理者を割り当てる必要があります。
- 管理者とプロジェクト管理者は、ヒューマン・アノテーターの役割を実行できます。ただし、ヒューマン・アノテーターをアノテーション・セットに割り当てる必要がある場合と同じ方法で、アノテーション・セットに割り当てる必要があります。
- ユーザー役割は、いったん割り当てられると、上位レベルから下位レベルの権限にダウングレードすることはできません。管理者をプロジェクト管理者やヒューマン・アノテーターにダウングレードしたり、プロジェクト管理者をヒューマン・アノテーターにダウングレードしたりすることはできません。ユーザーの追加、役割のアップグレード、およびユーザー・アカウントの非活動化については、[チームのアセンブル](/docs/services/watson-knowledge-studio/team.html)を参照してください。

## 役割の説明
{: #descriptions}
次の表に、{{site.data.keyword.knowledgestudioshort}} の役割の説明を示します。役割は、最上位レベルの権限から最低レベルの権限の順にリストされています。

| 役割 | 説明 |
|------|-------------|
| Admin | 管理タスクを担当します。これには、ユーザー、リソース使用量、月額課金の管理の作業が含まれます。大規模チームの設定では、管理者がモデル開発プロセスに参加することはほとんどありません。
| プロジェクト管理者 | 自分が割り当てられているワークスペースの編成全体を担当します。タスクには、タイプ・システムの作成、アセットの管理、アノテーション作業の管理、機械学習モデルの評価、モデルのデプロイが含まれます。この役割のユーザーは、タイプ・システムの作成、タイプ・システムの正しい適用方法に関するヒューマン・アノテーターへの指導、モデルの品質評価を行う必要があるため、業界の対象分野の専門知識を必要とします。|
| ヒューマン・アノテーター | 自分が割り当てられているトレーニング文書に含まれるエンティティー・メンションと関係メンションのラベル付けを行います。この作業は、ヒューマン・アノテーターに割り当てられ、プロジェクト管理者によってモニターされます。ヒューマン・アノテーターは、プロジェクト管理者からタイプ・システムの正しい適用方法を指導されるまで、業界の対象分野の専門知識を持っていない場合があります。|
{:caption="表 1. 役割の説明" caption-side="top"}

## 役割の権限
{: #permissions}

各役割の権限を比較するには、次の表を参照してください。各行に 1 つの権限がリストされています。役割にその権限がある場合は、役割列にチェック・マーク (&checkmark;) が付いています。

| 権限 | Admin | プロジェクト管理者 | ヒューマン・アノテーター |
|------------|-------|-----------------|-----------------|
| ユーザーのアクセス権限と役割の管理 | &checkmark; |  |  |
| ワークスペースの管理 | &checkmark; |  |  |
| タイプ・システムとアノテーション・ガイドラインの作成 | &checkmark; | &checkmark; |  |
| トレーニング文書のアップロード | &checkmark; | &checkmark; |  |
| ルールの管理 | &checkmark; | &checkmark; |  |
| 文書の事前アノテーション付け | &checkmark; | &checkmark; |  |
| アノテーション・タスクの管理 | &checkmark; | &checkmark; |  |
| ヒューマン・アノテーションとのアノテーション競合の解決 (*裁定*) | &checkmark; | &checkmark; |  |
| 機械学習モデルのトレーニングと評価 | &checkmark; | &checkmark; |  |
| ランタイム・サービスに対するモデルのデプロイとアンデプロイ | &checkmark; | &checkmark; |  |
| 文書アノテーションの実行 | &checkmark; | &checkmark; | &checkmark; |
{:caption="表 2. 役割の権限" caption-side="top"}
