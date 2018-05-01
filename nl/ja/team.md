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

この文書は、{{site.data.keyword.cloud}} 上の {{site.data.keyword.knowledgestudiofull}} に関するものです。以前のバージョンの {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 向けの資料を参照するには、[このリンクをクリック ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/docs/services/knowledge-studio/team.html){: new_window} してください。
{: tip}

# チームのアセンブル
{: #team}

モデルの作成には、対象分野の専門家、プロジェクト管理者、および統計モデルを理解して解釈できるユーザーからの情報が必要です。ログインする必要のある個人ごとに、{{site.data.keyword.knowledgestudioshort}} にユーザーを追加する必要があります。
{: shortdesc}

**注**: 標準プランとプレミアム・プランに加入している場合にのみ、ユーザーを追加できます。無料プランは 1 ユーザーに制限されています。唯一のユーザーとして、そのユーザーに、最高の権限を持つ役割 (Admin の役割) が割り当てられます。

## 始めに

- サポートされるブラウザーを使用していることを確認してください。詳しくは、[ブラウザーの要件](/docs/services/watson-knowledge-studio/system-requirements.html)を参照してください。
- [{{site.data.keyword.knowledgestudioshort}} のインスタンスを作成します](/docs/services/watson-knowledge-studio/tutorials-create-project.html#instance)。
- 標準プランまたはプレミアム・プランに登録している場合、{{site.data.keyword.cloud_notm}} **「管理」**タブから、{{site.data.keyword.knowledgestudioshort}} にユーザーとして追加する必要があるその他のユーザーを組織に招待します。ユーザーの招待について詳しくは、[ユーザーの招待とアクセス権限の割り当て ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/docs/iam/iamuserinv.html){: new_window} を参照してください。

  **重要**:

  - 招待されるユーザーに、Cloud Foundry の**「開発者」**の役割が割り当てられていることを確認してください。詳しくは、[Cloud Foundry アクセス権限 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/docs/iam/cfaccess.html){: new_window} を参照してください。
  - {{site.data.keyword.knowledgestudioshort}} を起動した最初のユーザーが、{{site.data.keyword.knowledgestudioshort}} インスタンスの Admin の役割を付与されます。このタスクは、このタスクの実行者がプラン登録後に初めて {{site.data.keyword.knowledgestudioshort}} を起動するユーザーであること、すなわち、Admin の役割を保持していることを前提としています。

## この作業について

通常、以下の役割を果たすユーザーを追加します。

**注:** 無料プランに登録した場合、その他のユーザーを {{site.data.keyword.knowledgestudioshort}} のインスタンスに追加することはできません。代わりに、{{site.data.keyword.knowledgestudioshort}} を起動すると、自身がインスタンスに追加され、Admin の役割を与えられます。Admin の役割では、異なる役割に割り当てられたさまざまなユーザーによって通常実行されるような、多数の機能を実行できます。いろいろな分野のドメインの専門家が連携して機械学習モデルまたはルール・ベース・モデルを構築していく方法をテストできます。

- **HumanAnnotator**

    ヒューマン・アノテーターは、通常、特定のドメインの文書をレビューして、そのドメインにとって関心のあるエンティティーや関係を識別する対象分野の専門家です。これらのユーザーは、制限された方法でアプリケーションと対話します。彼らは、グランドトゥルース・エディターを使用して、自身に割り当てられた一連の文書にアノテーションを付けます。

- **ProjectManager**

    プロジェクト管理者は、ワークスペース成果物の作成や、モデルのトレーニング、作成、およびデプロイなどのタスクを実行することにより、モデルの作成を促進する人々です。プロジェクト管理者は、機械学習アノテーターを作成するために使用されるワークスペースを対象に、文書レビュー・タスクをヒューマン・アノテーターに割り振り、アノテーションの競合を解決し、グランドトゥルースに追加する文書を承認することで、文書アノテーション・プロセスの管理も行います。

## {{site.data.keyword.knowledgestudioshort}} でのユーザーの追加

{{site.data.keyword.cloud_notm}} 組織のユーザーを {{site.data.keyword.knowledgestudioshort}} に追加します。

**注**: 標準プランとプレミアム・プランに加入している場合にのみ、ユーザーを追加できます。無料プランは 1 ユーザーに制限されています。

{{site.data.keyword.knowledgestudioshort}} インスタンスにユーザーを追加するには、以下のようにします。

1. {{site.data.keyword.ibmid}} を使用して [{{site.data.keyword.cloud_notm}} ダッシュボード ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/dashboard/apps/){: new_window} にログインし、{{site.data.keyword.knowledgestudioshort}} を起動します。
1. **「設定」**アイコンをクリックし、次に**「サービス詳細の表示/変更 (View/modify service details)」**をクリックします。
1. **「マネージャー・ユーザー (Manager users)」**セクションで、追加するユーザーの {{site.data.keyword.ibmid}} を入力します。
1. ユーザーに付与する役割を選択します。

   注: ユーザーの役割を割り当てた後に役割をダウングレードすることはできません。したがって、Admin 役割および ProjectManager 役割を割り当てる際は、各役割が実行できるタスクを必ず理解しておいてください。

1. **「追加」**をクリックします。

## ユーザーの役割のアップグレード

ユーザーを {{site.data.keyword.knowledgestudioshort}} に追加した後、下位の役割を上位の役割にアップグレードできます。各タスクを実行するためには、以下で説明している役割がユーザーに割り当てられている必要があります。

**注**: 標準プランとプレミアム・プランに加入している場合にのみ、ユーザーをアップグレードできます。無料プランは 1 ユーザーに制限されており、そのユーザーには最上位の役割である Admin が既に割り当てられています。

> **重要: 上位の役割から下位の役割へのダウングレードは許可されていません。**

{{site.data.keyword.knowledgestudioshort}} ユーザーの役割をアップグレードするには、以下のようにします。

1. {{site.data.keyword.ibmid}} を使用して [{{site.data.keyword.cloud_notm}} ダッシュボード ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/dashboard/apps/){: new_window} にログインし、{{site.data.keyword.knowledgestudioshort}} を起動します。
1. 右上のナビゲーション・メニューから**「設定」**アイコン ![「設定」アイコン](images/settings.png) をクリックし、次に**「サービス詳細の表示/変更 (View/modify service details)」**をクリックします。「サービスの詳細 (Service Details)」ページの**「ユーザーの管理」**セクションには、この {{site.data.keyword.knowledgestudioshort}} のインスタンスのユーザーであるすべてのユーザー ID がリストされます。
1. 変更するユーザーの名前を見つけて、**「編集」**リンクをクリックします。

    {{site.data.keyword.knowledgestudioshort}} には、以下の役割があります。役割は、最も高い特権のレベルから最も低い特権のレベルの順序でリストしています。
    - **Admin**

      この役割のユーザーは、以下のタスクを実行できます。

        - サブスクリプションを管理する (フィーチャー、ストレージ、さらなるユーザーの追加など)。
        - 「サービスの詳細 (Service Details)」ページから、サブスクリプションへのアクセス権をユーザーに付与する。
        - サブスクリプション内のすべてのワークスペースを作成および管理する。
        - すべてのワークスペースのプロジェクト管理者またはヒューマン・アノテーターの役割に担当者を割り当てる。

    - **ProjectManager**

      この役割を持つユーザーは、以下のタスクを実行できます。

      - 追加された先のワークスペースを管理する。
      - ワークスペースにヒューマン・アノテーターを割り当てる。

      この役割を持つユーザーは、以下のタスクは実行できません。

      - ワークスペースを作成する。
      - 「サービスの詳細 (Service Details)」ページから、ユーザーのアクセス権限や役割を管理する。

    - **HumanAnnotator**

      この役割を持つユーザーは、ヒューマン・アノテーターの役割が割り当てられているワークスペース内の文書、および自身に割り当てられたアノテーション・タスクに関連付けられた文書セット内の文書にアノテーションを付けることができます。

      **重要:** **HumanAnnotator** の役割を持つユーザーに、{{site.data.keyword.knowledgestudioshort}} アプリケーション内でリストされるワークスペースが表示されるようにするためには、ワークスペースを作成し、ユーザーを文書セットに関連付け、アノテーション・タスクをユーザーに割り当てる必要があります。ユーザーが最初にアプリケーションにアクセスしたときにワークスペースが表示されるように、ユーザーの登録後すぐにワークスペースをセットアップしてください。ワークスペースのセットアップが終わったら、文書にアノテーションを付ける作業を開始できることをユーザーに通知することをお勧めします。

1. ユーザーの役割をクリックし、そのユーザーをアップグレードする役割を選択します。
1. オプション: {{site.data.keyword.knowledgestudioshort}} でのユーザーの管理が終了したら、Web ブラウザーを閉じてセッションを終了します。{{site.data.keyword.knowledgestudioshort}} ユーザー・インターフェースには、明示的にログアウトするためのアクションはありません。

## ユーザー・アカウントの非アクティブ化

後でユーザーの削除が必要になった場合は、前のステップに従って、「サービスの詳細 (Service Details)」ページを再度開きます。ユーザー ID のリストから、削除するユーザーを見つけ、**「非アクティブ化 (Deactivate)」**をクリックします。

> **重要**: アノテーションを付ける文書がユーザーに割り当てられているときに、そのユーザーのアカウントを非アクティブ化すると、アノテーションが影響を受けます。非アクティブ化されたユーザーによって行われたアノテーションが、グランドトゥルースにプロモートされなかった場合、それらのアノテーションは削除されます。

### 関連タスク

[アノテーション・セットの作成および割り当て](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projdocsets)
