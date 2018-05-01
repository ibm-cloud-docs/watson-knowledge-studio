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

この文書は、{{site.data.keyword.cloud}} 上の {{site.data.keyword.knowledgestudiofull}} に関するものです。以前のバージョンの {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 向けの資料を参照するには、[このリンクをクリック ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/docs/services/knowledge-studio/tutorials-create-project.html){: new_window} してください。
{: tip}

# {{site.data.keyword.knowledgestudioshort}} の開始
{: #wks_tutintro}

この {{site.data.keyword.knowledgestudiofull}} チュートリアルは、他のチュートリアルを開始する前に完了しておく必要がある前提条件タスクの実行に役立ちます。
{: shortdesc}

## 始めに
{: #prereq}

サポートされているブラウザーを使用していることを確認してください。詳しくは、『[ブラウザーの要件](/docs/services/watson-knowledge-studio/system-requirements.html)』を参照してください。

## サービス・インスタンスの作成
{: #instance}

1. まだ登録が済んでいなければ、[{{site.data.keyword.ibmid}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net){: new_window} に登録し、{{site.data.keyword.cloud_notm}} にログインします。
1. [「ダッシュボード」ページ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/dashboard/apps){: new_window}から、{{site.data.keyword.knowledgestudioshort}} プランに登録します。

  1. **「カタログ」**をクリックします。
  1. 検索フィールドで、**label:lite** フィルター (存在する場合) を削除し、`{{site.data.keyword.knowledgestudioshort}}` を検索します。
  1. **{{site.data.keyword.knowledgestudioshort}}** を選択します。
  1. [従量課金 (PAYG) アカウントまたはサブスクリプション・アカウント![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/docs/pricing/index.html){: new_window}がまだない場合は、{{site.data.keyword.knowledgestudioshort}} カタログ・ページで、**「アップグレード」**をクリックします。クレジット・カード情報の入力を求めるプロンプトが出されます。

    {{site.data.keyword.knowledgestudioshort}} 無料プランを選択した場合、クレジット・カードには課金されません。無料プランは、無料で無制限に使用できます。
{: tip}

1. プランに登録したら、{{site.data.keyword.knowledgestudioshort}} を起動します。

  このチュートリアルを実行するには、{{site.data.keyword.knowledgestudioshort}} で使用できるユーザー ID が少なくとも 1 つ必要です。このユーザー ID には、Admin 役割が必要です。無料プランに登録した場合は、唯一のユーザーとして Admin 役割を持ちます。ユーザー役割については、『[チームのアセンブル](/docs/services/watson-knowledge-studio/team.html)』を参照してください。

## 演習 1: ユーザー役割の割り当て
{: #wks_tutless1}

この演習では、{{site.data.keyword.knowledgestudioshort}} でユーザーに割り当てることができるさまざまな役割について学習します。

### この作業について

機械学習モデルを作成するには、対象分野の専門家、プロジェクト管理者、および統計モデルを理解して解釈できるユーザーからの入力が必要です。管理者は、各ユーザーが自分のタスクに対する適切な権限を持つよう、各ユーザーに役割を割り当てます。ユーザー役割について詳しくは、『[チームのアセンブル](/docs/services/watson-knowledge-studio/team.html)』を参照してください。

### 手順

1. 管理者 ID を使用して、{{site.data.keyword.knowledgestudioshort}}  にログインします。
1. 設定アイコンをクリックして、「サービスの詳細」ページを開きます。このページには、{{site.data.keyword.knowledgestudioshort}} ユーザーとして登録されているすべてのユーザー ID がリストされます。各ユーザー ID には、以下のいずれかの役割があります (有する権限が大きい順)。

    - Admin
    - ProjectManager
    - HumanAnnotator

    ユーザー役割について詳しくは、『[チームのアセンブル](/docs/services/watson-knowledge-studio/team.html)』を参照してください。

1. Admin 役割を持つユーザーが少なくとも 1 人存在することを確認してください。この役割を持つユーザー ID は、ワークスペースを作成でき、プロジェクト管理者としてもヒューマン・アノテーターとしても作業することができます。
1. 追加のユーザー ID にアクセスできる場合は、HumanAnnotator 役割を持つユーザーが少なくとも 2 人存在することを確認してください。

    > **注:** 実際のモデルの作成には、一般に、管理者またはプロジェクト管理者のほかに、複数のヒューマン・アノテーターが必要です。ただし、チュートリアルの目的では、単一のユーザー ID で作業を続行できます。

1. オプション: ユーザー ID に割り当てられた役割を変更します。ユーザー ID のテーブル行の**「アクション」**列にある**アカウント設定の変更**アイコンをクリックして、割り当てられているユーザー役割を変更します。

    > **注:** ユーザー ID をより大きな権限を持つ役割にアップグレードすることはできますが、Admin 役割または ProjectManager 役割を持つユーザーを HumanAnnotator 役割にダウングレードすることはできません。

## 演習 2: ワークスペースの作成
{: #wks_tutless2}

この演習では、{{site.data.keyword.knowledgestudioshort}} 内にワークスペースを作成する方法について学習します。

### この作業について

ワークスペースは、機械学習モデルの作成に必要なすべてのリソースを定義します。それらのリソースには、トレーニング文書、タイプ・システム、辞書、およびヒューマン・アノテーターによって追加されたアノテーションなどが含まれます。ワークスペースの作成について詳しくは、『[ワークスペースの作成](/docs/services/watson-knowledge-studio/create-project.html)』を参照してください。

### 手順

1. {{site.data.keyword.knowledgestudioshort}} 管理者として、{{site.data.keyword.cloud_notm}} [ダッシュボード ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/dashboard/apps/){:new_window} から、{{site.data.keyword.knowledgestudioshort}} サービスを起動します。
1. **「ワークスペースの作成」**をクリックします。
1. 新規ワークスペースの詳細を指定します。

    - **「ワークスペース名」**フィールドに、`My workspace` と入力します。
    - **「ワークスペースの説明」**フィールドに、`Watson Knowledge Studio tutorial workspace` と入力します。
    - **「文書の言語」**フィールドには、デフォルト値の **English** を使用します。このチュートリアルに使用するサンプル・ファイルは、英語で書かれています。

1. **「作成 (Create)」**をクリックします。

### 結果

ワークスペースが作成され、自動的に開きます。

### 次に行うこと

これで、タイプ・システムなどのワークスペース・リソースの構成を開始できるようになりました。

## 演習 3: タイプ・システムの作成
{: #wks_tutless3}

この演習では、{{site.data.keyword.knowledgestudioshort}} 内でタイプ・システムをアップロードおよび変更する方法について学習します。アノテーション・タスクを開始する前に、タイプ・システムを作成またはアップロードする必要があります。

### この作業について

タイプ・システムについて詳しくは、『[タイプ・システム](/docs/services/watson-knowledge-studio/typesystem.html#wks_typesystem)』を参照してください。

### 手順

1. <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/en-klue2-types.json" download>en-klue2-types.json<img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン" title="外部リンク・アイコン" class="style-scope doc-content"></a> ファイルを、ご使用のコンピューターにダウンロードします。このファイルには、例として、KLUE タイプ・システムが含まれています。
1. サイドバーから、**「アセットおよびツール」**>**「エンティティー・タイプ」**をクリックします。
1. 「エンティティー・タイプ」ページで、**「アップロード」**をクリックします。
1. コンピューターから `en-klue2-types.json` ファイルを選択して、**「アップロード」**をクリックします。アップロードされたタイプ・システムがテーブルに表示されます。
1. タイプ・システムを参照すると、アップロードされたデータを確認できます。
1. エンティティー・タイプを編集します。

    1. MONEY エンティティー・タイプを見つけます。
    1. テーブル行の任意の場所をダブルクリックして、エンティティー・タイプを編集します。
    1. **「役割」**列で、AWARD 役割の隣にある**役割の削除**アイコン ![_](images/wks_delete.jpg) をクリックします。

        ![エンティティー・タイプからの役割の削除を示す画面キャプチャー。](images/wks_tut_delete_role.jpg)

    1. **「保存 (Save)」**をクリックします。

### 次に行うこと

タイプ・システムに対する変更が完了したら、ワークスペースへの文書の追加を開始できます。

## 演習 4: 辞書の追加
{: #wks_tutless4}

この演習では、{{site.data.keyword.knowledgestudioshort}} でワークスペースに辞書を追加する方法について学習します。辞書は、機械学習モデルの作成時に、テキストに事前アノテーションを付けるために使用されます。

### この作業について

辞書について詳しくは、『[ワークスペースへの辞書の追加](/docs/services/watson-knowledge-studio/dictionaries.html#wks_projdictionaries)』を参照してください。

### 手順

1. <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/dictionary-items-organization.csv" download>`dictionary-items-organization.csv`<img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン" title="外部リンク・アイコン" class="style-scope doc-content"></a> ファイルを、ご使用のコンピューターにダウンロードします。このファイルには、{{site.data.keyword.knowledgestudioshort}} 辞書へのアップロードに適した辞書用語が CSV 形式で含まれています。
1. **「アセットおよびツール」**>**「事前アノテーター (Pre-annotators)」**サイドバーから、**「辞書」**タブを選択して、**「辞書の管理」**をクリックします。
1. **「辞書の作成」**をクリックして、辞書を追加します。

    > **注:** **「辞書のアップロード」**はクリックしないでください。これは、現状のままの形で使用する辞書をアップロードするために使用します。このチュートリアルでは、編集可能な新規の辞書を作成してから、その辞書に用語をアップロードします。

1. **「名前」**フィールドに `Test dictionary` と入力し、**「保存」**をクリックして (空の) 辞書を作成します。

    新しい辞書が作成され、編集用に自動的に開かれます。

1. 辞書ペインで、**「アップロード」**をクリックします。
1. 「辞書項目のアップロード (Upload Dictionary Entries)」ウィンドウで、コンピューターから `dictionary-items-organization.csv` ファイルを選択した後、**「アップロード」**をクリックします。ファイル内の用語が辞書にアップロードされます。
1. **「項目の追加」**をクリックして、新規用語を作成します。編集可能な行がテーブルの上部に追加されます。
1. **「表層形 (Surface Forms)」**列で、`IBM` と、`International Business Machines Corporation` を別々の行に入力します。(新しい表層形の入力を開始すると、追加の表層形用のスペースが下に追加されます。) `IBM` の横のラジオ・ボタンは選択されたままにしておきます。これは、`IBM` が見出し語であることを示します。
1. **「品詞」**列で、**「名詞」** を選択します。
1. **「保存 (Save)」**をクリックします。

    ![「辞書」ページの画面キャプチャー。1 つの辞書項目が選択されており、その表層形と品詞が強調表示されています。](images/wks_tutdict4.jpg)

### 次に行うこと

辞書を作成した後、それを使用して文書に事前アノテーションを付けることにより、ヒューマン・アノテーション・タスクを高速化することができます。

## チュートリアルの要約
{: #wks_tutsum}

{{site.data.keyword.knowledgestudioshort}} について学習しながら、ワークスペースを作成して、それに成果物を追加しました。

### 学習した演習

このチュートリアルを修了すると、以下の概念について学習したことになります。

- ワークスペース
- タイプ・システム
- 辞書
