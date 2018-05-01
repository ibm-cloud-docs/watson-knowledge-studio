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

この文書は、{{site.data.keyword.cloud}} 上の {{site.data.keyword.knowledgestudiofull}} に関するものです。{{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} マーケットプレイスの以前のバージョン用の資料を参照するには、[このリンクをクリックしてください![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/docs/services/knowledge-studio/preannotation.html){: new_window}。
{: tip}

# アノテーションのブートストラッピング
{: #preannotation}

ワークスペース内の文書の事前アノテーション付けを実行することにより、ヒューマン・アノテーターのジョブを簡素化します。事前アノテーターは、{{site.data.keyword.knowledgestudioshort}} の辞書、ルール・ベース・モデル、または機械学習モデルです。これを実行して、メンションを自動的に検出してアノテーションを付けることができます。
{: shortdesc}

事前アノテーションにより単純なアノテーション付けが行われ、文書にアノテーションを付けるジョブが進められるので、ヒューマン・アノテーターのジョブを容易にします。

文書の事前アノテーション付けに使用する方法によって、結果として作成されたモデルの使用方法が制限されることはありません。例えば、文書の事前アノテーション付けに {{site.data.keyword.nlushort}} サービスを使用したからといって、作成した最終機械学習モデルを {{site.data.keyword.nlushort}} サービスにデプロイしなければならないわけではありません。事前アノテーションは、ヒューマン・アノテーション・プロセスをブートストラップすることのみを目的としています。

## 重要事項

- ヒューマン・アノテーターがアノテーションを付けた文書には事前アノテーターを実行しないでください。ヒューマン・アノテーターによって追加されたアノテーションが削除されます。
- 文書に対して実行できる事前アノテーターは 1 つのみになります。ある事前アノテーターを実行し、それから 2 番目の事前アノテーターを実行すると、2 番目の事前アノテーターは、最初のアノテーターによって追加されたアノテーションを削除します。ユース・ケースに最適な事前アノテーション方法を選択し、その 1 つの事前アノテーターのみを使用してください。

## 事前アノテーション方法

使用可能な事前アノテーターは以下のとおりです。
>**注**: {{site.data.keyword.alchemylanguageshort}} サービスは非推奨になりました。詳しくは、[Retirement of {{site.data.keyword.alchemyapishort}} service ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/blogs/bluemix/2017/03/bye-bye-alchemyapi/){: new_window} を参照してください。

- **{{site.data.keyword.nlushort}}**

    文書内でのエンティティーについてのメンションを自動的に検出するために使用できる事前アノテーター。ソース文書に、一般知識の内容が含まれている場合は、この事前アノテーターが適しています。例えば、特許法の研究などの特定の分野に焦点を当てた、高度に専門化した文書を扱う場合は、辞書の事前アノテーターやルール・ベース・モデルの方がより良い選択である可能性があります。

- **辞書**

    指定した用語の辞書を使用し、エンティティー・タイプに関連付けて、文書内でそのエンティティー・タイプについてのメンションを検出します。この事前アノテーターは、機械学習事前アノテーターのように、用語が使用されているコンテキストを分析するのではなく、用語が使用されているコンテキストに関係なく、判読可能な意味を持つのに十分な、他と区別できる特徴を持つ用語に依存するため、固有の用語や専門用語がある分野にとって最適の選択です。例えば、野菜、スポーツ、または何かを押しつぶすという意味の動詞について言及する可能性がある *squash* のエンティティー・タイプを判断するよりも、*asbestos* を鉱物のエンティティー・タイプと認識する方が容易です。

- **機械学習**

    機械学習モデルを使用して、自動的に文書にアノテーションを付けます。このオプションは、{{site.data.keyword.knowledgestudioshort}} を使用して既に機械学習モデルを作成している場合にのみ利用できます。新規文書セットを追加する場合、以前に作成した機械学習アノテーターを実行して、新規文書の事前アノテーション付けを実行できます。新規文書セットが、最初に機械学習アノテーターのトレーニングに使用した文書と類似している場合は、これが事前アノテーションの最適の選択と考えられます。

- **ルール**

    ルール・ベース・モデルを使用して、自動的に文書にアノテーションを付けます。このオプションは、{{site.data.keyword.knowledgestudioshort}} を使用して既にルール・ベース・モデルを作成している場合にのみ利用できます。文書に、意味の取り出しに使用できるトークンの共通パターンが含まれている場合は、このモデルを選択することをお勧めします。また、辞書事前アノテーターの機能を使用可能にした場合、文書内で検出した辞書用語のクラス・タイプを識別することにより、機能の一部を取り込むこともできます。

あるいは、既にアノテーションが付けられた文書をアップロードし、それらを使用して機械学習モデルのトレーニングを開始することもできます。アップロードするアノテーション付き文書に対して事前アノテーターを実行することはできません。実行すると、既存のアノテーションが文書から除去され、事前アノテーターで作成されたアノテーションのみに置き換えられます。

> **注:** 現在のワークスペースの一部としてグラウンド・トゥルースに追加された文書に対して事前アノテーターを実行*できます*。現在のワークスペース内で文書に追加され、レビューされ、受け入れられ、グラウンドトゥルースにプロモートされたアノテーションは除去されません。

## {{site.data.keyword.nlushort}} を使用した文書の事前アノテーション付け
{: #wks_preannotnlu}

{{site.data.keyword.nlushort}} サービスを使用して、コーパスに追加した文書の事前アノテーション付けを実行できます。

### 始めに

{{site.data.keyword.nlushort}} 事前アノテーターが、ユース・ケース用の値を追加する可能性があるかどうかを判別します。サポートされる [{{site.data.keyword.nlushort}} サービスのエンティティー・タイプおよびサブタイプ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン ")](https://console.bluemix.net/docs/services/natural-language-understanding/entity-types.html){: new_window} のリストを確認して、それらと、タイプ・システム内のタイプの間に自然な重複があるかどうかを判別します。ある場合は、この手順を続行します。ない場合は、別の事前アノテーターを選択して使用してください。

### この作業について

{{site.data.keyword.nlushort}} は、自然言語処理によってテキスト分析を提供するサービスです。{{site.data.keyword.nlushort}} 事前アノテーターを使用すると、{{site.data.keyword.nlushort}} サービスが呼び出されて文書内のエンティティーを検出し、アノテーションを付けます。

{{site.data.keyword.nlushort}} のエンティティー・タイプを、{{site.data.keyword.knowledgestudioshort}} タイプ・システムに追加した対応する {{site.data.keyword.knowledgestudioshort}} エンティティー・タイプにマップすることによって、サービスで検索するエンティティー・タイプを指定する必要があります。マップしたエンティティー・タイプについてのメンションのみが検出されてアノテーションが付けられます。

### 手順

{{site.data.keyword.nlushort}} サービスを使用して文書の事前アノテーション付けを行うには、以下の手順を実行してください。

1. {{site.data.keyword.knowledgestudioshort}} 管理者としてログインし、ワークスペースを選択します。
1. **「アセットおよびツール (Assets & Tools)」** > **「事前アノテーター (Pre-annotators)」** > **「Natural Language Understanding」**タブを選択します。
1. **「編集 (Edit)」**をクリックして、**「エンティティー・タイプ (Entity Types)」**ページに定義されている各エンティティー・タイプを、対応する {{site.data.keyword.nlushort}} のエンティティー・タイプにマップします。

    - {{site.data.keyword.nlushort}} エンティティー・タイプのドロップダウン・リストには、{{site.data.keyword.nlushort}} サービスによって認識されるエンティティー・タイプが事前に取り込まれています。
    - 少なくとも 1 つのエンティティー・タイプをマップする必要があります。
    - {{site.data.keyword.nlushort}} エンティティー・タイプを {{site.data.keyword.knowledgestudioshort}} エンティティー役割にマップすることはできません。{{site.data.keyword.knowledgestudioshort}} エンティティー・タイプのみになります。
    - 複数の {{site.data.keyword.nlushort}} エンティティー・タイプを単一の {{site.data.keyword.knowledgestudioshort}} エンティティー・タイプ (またはその逆に) マップできます。例えば、以下のマッピングが許可されます。

    <table cellpadding="4" cellspacing="0" summary="エンティティー・タイプのサンプル・マッピング" border="1" class="simpletable"><tr class="sthead"><th valign="bottom" align="left" id="d20428e292" class="stentry thleft thbot">Watson Knowledge Studio のエンティティー・タイプ</th>
        <th valign="bottom" align="left" id="d20428e298" class="stentry thleft thbot">{{site.data.keyword.nlushort}} のエンティティー・タイプ</th>
      </tr>
      <tr class="strow"><td valign="top" headers="d20428e292" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">ENGINEER (エンジニア)</p></li>
            <li class="li"><p class="p wrapper">SCIENTIST (科学者)</p></li>
          </ul>
        </td>
        <td valign="top" headers="d20428e298" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">Person (人)</p></li>
          </ul></td>
      </tr>
      <tr class="strow"><td valign="top" headers="d20428e292" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">LOCATION (場所)</p></li></td>
        <td valign="top" headers="d20428e298" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">CityTown (市区町村)</p></li>
            <li class="li"><p class="p wrapper">Country (国)</p></li>
          </ul>
        </td>
      </tr>
    </table>
    {: #wks_preannotnlu__datasimpletable_cm1_y3g_fx}

1. 適用するすべてのエンティティー・タイプをマッピングしたら、**「この事前アノテーターを適用 (Apply This Pre-annotator)」**をクリックします。

    **「この事前アノテーターを適用 (Apply This Pre-annotator)」**ボタンは、少なくとも 1 つのエンティティー・タイプをマップするまでは選択できません。

1. 事前アノテーション付けを実行する各文書セットのチェック・ボックスを選択します。

    この事前アノテーターを初めて実行している場合は、まず、事前アノテーターが、マップされたエンティティーについてのメンションを予期どおりに検出できることを確認します。それぞれ異なるデータ・ソースの代表的な文書を 1 つ以上含む文書セットを 1 つ作成します。
    {: tip}

1. **「実行 (Run)」**をクリックします。

    事前アノテーターの妥当性検査を行う場合は、アノテーション済みの文書を開き、追加されたアノテーションを確認します。十分な数の正確なアノテーションが作成されていることを確認してください。アノテーションが正確な場合は、より多くの大規模な文書セットでアノテーターを再実行できます。アノテーションが正確でない場合は、異なる {{site.data.keyword.nlushort}} エンティティー・タイプを、ご使用のタイプにマップすることを検討してください。タイプが自然に重複しない場合、{{site.data.keyword.nlushort}} 事前アノテーターは、使用するのに最適な事前アノテーターではありません。

    事前アノテーションは、文書が属している可能性のあるさまざまな文書セットに関係なく、個々の文書に適用されます。選択した文書セットと選択していない文書セットの間で重複している文書は、両方の文書セットで事前アノテーション付けが実行されます。

1. 事前アノテーターを一度実行したら、いつでも**「この事前アノテーターを適用 (Apply This Pre-annotator)」**をクリックすると、そのアノテーターを使用して、コーパスに追加した追加の文書セットの事前アノテーション付けを実行できます。

    > **制約事項:** {{site.data.keyword.nlushort}} 事前アノテーターのタイプ・マッピング定義を編集したら、事前アノテーション済みの文書セットを含むアノテーション・タスクを再作成する必要があります。事前アノテーターのマッピング定義に対して行った変更に基づく事前アノテーションを、既にアノテーション・タスクに割り当てられている文書セットに適用することはできません。

### 結果
{: #wks_preannotnlu__export-warning}

{{site.data.keyword.nlushort}} サービスによって事前アノテーション付けが実行された文書によって作成されたグラウンド・トゥルースを、{{site.data.keyword.knowledgestudioshort}} の外部で直接使用することはできません。グラウンド・トゥルースは (読み取り不能形式で) ダウンロードして、ある {{site.data.keyword.knowledgestudioshort}} ワークスペースから別のワークスペースに移動できます。そして、グラウンド・トゥルースの生成を継続し、それを使用して、{{site.data.keyword.knowledgestudioshort}} の外部のサービスでの使用のためにデプロイできる機械学習モデルやルール・ベース・モデルを作成できます。

> **制約事項:** {{site.data.keyword.nlushort}} を使用して事前アノテーションが付けられた文書は、ダウンロードされると読み取り不能形式になります。しかし、ヒューマン・アノテーターによって文書に追加されたアノテーションを含め、それらの文書内のすべてのアノテーションが読み取り不能になります。

**関連情報**:

[{{site.data.keyword.nlushort}}![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/watson/services/natural-language-understanding/){: new_window}

## 辞書を使用した文書の事前アノテーション付け
{: #wks_preannot}

ヒューマン・アノテーターによるアノテーション・タスクの開始を助けるために、辞書を作成し、それを使用して、コーパスに追加した文書の事前アノテーション付けを実行できます。

### この作業について

ヒューマン・アノテーターが事前アノテーション済みの文書の作業を開始すると、辞書の項目に基づくエンティティー・タイプによって、多くのメンションに既にマークが付けられる可能性が高くなります。ヒューマン・アノテーターは、事前アノテーションが付けられたエンティティー・タイプを変更または削除し、アノテーションが付けられていないメンションにエンティティー・タイプを割り当てることができます。辞書による事前アノテーションは、関係および照応にはアノテーションを付けません。関係および照応は、ヒューマン・アノテーターがアノテーションを付ける必要があります。

**注**: このタスクでは、編集可能な辞書の作成方法を示します。読み取り専用辞書を使用して文書をアップロードし、事前アノテーション付けを実行する場合は、**「アセットおよびツール (Assets & Tools)」** > **「事前アノテーター (Pre-annotators)」** > **「辞書 (Dictionaries)」**タブにある**「辞書のアップロード (Upload Dictionary)」**ボタンをクリックします。

### 手順

編集可能な辞書を作成して文書の事前アノテーション付けを実行するには、以下のようにします。

1. {{site.data.keyword.knowledgestudioshort}} 管理者としてログインし、ワークスペースを選択します。
1. **「アセットおよびツール (Assets & Tools)」** > **「事前アノテーター (Pre-annotators)」** > **「辞書 (Dictionaries)」**タブを選択します。
1. **「辞書の管理 (Manage Dictionaries)」**をクリックし、次に**「辞書の作成 (Create Dictionary)」**をクリックします。
1. **「エンティティー・タイプ (Entity type)」**リストから、辞書に関連付けるエンティティー・タイプを選択します。
1. 辞書の項目を追加するか、辞書の用語を含むファイルをアップロードします。
1. **「事前アノテーター (Pre-annotators)」**ページに戻り、**「辞書 (Dictionaries)」**タブで**「この事前アノテーターを適用 (Apply This Pre-annotator)」**をクリックします。
1. 事前アノテーション付けを実行する各文書セットのチェック・ボックスを選択し、**「実行 (Run)」**をクリックします。

    事前アノテーションは、文書が属している可能性のあるさまざまな文書セットやアノテーション・セットに関係なく、個々の文書に適用されます。選択した文書セットと選択していない文書セットの間で重複している文書は、両方の文書セットで事前アノテーション付けが実行されます。

1. 辞書が作成された後は、その辞書を使用して、コーパスに追加した追加の文書セットの事前アノテーション付けを実行するときはいつでも、**「実行 (Run)」**をクリックできます。

    > **制約事項:** 辞書を編集して項目を追加または削除する場合は、事前アノテーション済みの文書セットを含むアノテーション・タスクを再作成する必要があります。辞書アノテーターに対して行った変更に基づく事前アノテーションは、既にアノテーション・タスクに割り当てられている文書セットには適用できません。

**関連情報**:

[辞書](/docs/services/watson-knowledge-studio/dictionaries.html#wks_dictionaries)

[「開始 (Getting Started)」>「辞書の追加 (Adding a dictionary)」](/docs/services/watson-knowledge-studio/tutorials-create-project.html#wks_tutless4)

## 機械学習モデルを使用した文書の事前アノテーション付け
{: #wks_preannotsire}

既存の機械学習モデルを使用して、コーパスに追加した文書の事前アノテーション付けを実行できます。

### この作業について

10 個から 30 個の文書にアノテーションを付けたら、そのデータで機械学習モデルをトレーニングできます。このような最小トレーニング・モデルは、実動で使用するのではなく、後続文書のヒューマン・アノテーションの時間短縮に役立つ事前アノテーション・モデルとして使用できます。例えば、機械学習モデルをトレーニングした後に文書をコーパスに追加した場合、そのモデルを使用して新しい文書セットの事前アノテーション付けを実行できます。事前アノテーターは、人によってアノテーションが付けられたのと同じ文書には実行しないでください。事前アノテーターによって、ヒューマン・アノテーションが削除されます。

### 手順

既存の機械学習モデルを使用して文書の事前アノテーション付けを実行するには、以下のようにします。

1. {{site.data.keyword.knowledgestudioshort}} 管理者としてログインし、ワークスペースを選択します。
1. **「モデル管理 (Model Management)」** > **「バージョン (Versions)」** > **「機械学習 (Machine Learning)」**タブを選択します。
1. **「このモデルを実行 (Run this model)」**をクリックします。
1. 事前アノテーション付けを実行する各文書セットのチェック・ボックスを選択し、**「実行 (Run)」**をクリックします。

    事前アノテーションは、文書が属している可能性のあるさまざまな文書セットやアノテーション・セットに関係なく、個々の文書に適用されます。選択した文書セットと選択していない文書セットの間で重複している文書は、両方の文書セットで事前アノテーション付けが実行されます。

1. 機械学習モデルを使用して、コーパスに追加した追加文書セットの事前アノテーション付けを実行するときはいつでも、** 「このモデルを実行 (Run this model)」**をクリックできます。

## ルール・ベース・モデルを使用した文書の事前アノテーション付け
{: #wks_preannotrule}

既存のルール・ベース・モデルを使用して、コーパスに追加した文書の事前アノテーション付けを実行できます。

### 手順

ルール・ベース・モデルを使用して文書の事前アノテーション付けを実行するには、以下の手順を実行してください。

1. {{site.data.keyword.knowledgestudioshort}} 管理者としてログインし、ワークスペースを選択します。
1. **「モデルの管理 (Model Management)」** > **「バージョン (Versions)」** > **「ルール・ベース (Rule-based)」**タブを選択します。
1. **「エンティティー・タイプおよびクラスのマップ (Map entity types and classes)」**をクリックして、{{site.data.keyword.knowledgestudioshort}} タイプ・システムに定義したエンティティー・タイプを 1 つ以上のルール・ベース・モデル・クラスにマップします (まだ実行していない場合)。

    - **「クラス名 (Class Name)」**列のドロップダウン・リストには、ルール・ベース・モデルに関連付けられたクラスが事前に取り込まれています。
    - 少なくとも 1 つのエンティティー・タイプをクラスにマップする必要があります。

1. **「ルール・ベース (Rule-based)」**タブで**「このモデルを実行 (Run this model)」**をクリックし、次に事前アノテーション付けを実行する文書セットまたはアノテーション・セットを選択します。選択するセットに、ヒューマン・アノテーションが追加された文書が含まれていないことを確認してください。事前アノテーターによって、ヒューマン・アノテーションが削除されます。

    **「このモデルを実行 (Run this model)」**ボタンは、少なくとも 1 つのエンティティー・タイプをクラスにマップするまでは選択できません。

1. 事前アノテーション付けを実行する各文書セットのチェック・ボックスを選択します。
1. **「実行 (Run)」**をクリックします。

    事前アノテーションは、文書が属している可能性のあるさまざまな文書セットに関係なく、個々の文書に適用されます。選択した文書セットと選択していない文書セットの間で重複している文書は、両方の文書セットで事前アノテーション付けが実行されているように表示されます。

1. ルール・ベース・モデルを使用して、コーパスに追加した追加文書セットの事前アノテーション付けを実行するときはいつでも、**「このモデルを実行 (Run this model)」**をクリックできます。

    > **制約事項:** ルール・ベース・モデルのエンティティー・タイプとクラスのマッピングを編集した場合は、事前アノテーション済み文書セットを含むアノテーション・タスクを再作成する必要があります。事前アノテーターのマッピング定義に対して行った変更に基づく事前アノテーションを、既にアノテーション・タスクに割り当てられている文書セットに適用することはできません。

## 事前アノテーション付けが実行された文書のアップロード
{: #wks_uima}

Unstructured Information Management Architecture (UIMA) 分析エンジンを使用して事前アノテーション付けが実行された文書をアップロードすることにより、モデルのトレーニングを素早く始動できます。

事前アノテーション済み文書は、UIMA Common Analysis Structure (UIMA CAS XMI)　の XMI シリアライゼーション形式でなければなりません。アップロードする ZIP ファイルには、UIMA TypeSystem 記述子ファイルと、UIMA タイプを {{site.data.keyword.knowledgestudioshort}} タイプ・システム内のエンティティー・タイプにマップするファイルが含まれている必要があります。

UIMA CAS XMI は、Apache UIMA の標準形式です。{{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer 内の分析済みコレクションから正しいフォーマットでファイルを作成する方法に関するガイドラインが提供されています。別の Apache UIMA 実装を使用する場合は、目的に応じてこれらのガイドラインを調整してください。XMI ファイルの作成方法に関係なく、タイプ・システム・マッピング・ファイルと ZIP ファイルを作成するための要件は、どのユーザーでも同じです。

インポートされた文書をヒューマン・アノテーターに割り当てると、文書はグラウンド・トゥルース・エディターで事前アノテーション済みのように表示され、多数のメンションに既にアノテーションが付けられている可能性があります。したがって、ヒューマン・アノテーターは、マークが付いていないメンションにアノテーション・ガイドラインを適用することを重点的にさらに多くの時間を割くことができます。あるいは、ヒューマン・アノテーション手順をバイパスし、事前アノテーション付けが実行された文書を使用して、機械学習モデルのトレーニングと評価を即時に開始することもできます。

### Watson Explorer Content Analytics からの分析済み文書のエクスポート
{: #wks_uimawexca}

{{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer Content Analytics でクロールおよび分析された文書をエクスポートし、分析された文書を XMI ファイルとして {{site.data.keyword.knowledgestudioshort}} ワークスペースにアップロードできます。

#### 手順

{{site.data.keyword.watson}} Explorer Content Analytics コレクションから分析済み文書を取得するには、以下のようにします。

1. Content Analytics 管理コンソールを Web ブラウザーで開きます。
1. 「コレクション」ビューで、文書のエクスポート元のコレクションを展開します。「解析および索引」ペインで、解析および索引処理が実行中であることを確認し、次に**「分析済み文書のコンテンツとメタデータをエクスポートします」**の矢印アイコンをクリックします。
1. **「分析された文書のエクスポート・オプション」**域で**「文書を XML ファイルとしてエクスポート」**を選択し、**「CAS の XMI フォーマットでのエクスポートを使用可能にする」**チェック・ボックスを選択し、エクスポートしたデータの書き込み先の出力パスを指定し、**「OK」**をクリックします。
1. コレクションの解析サービスおよび索引サービスを停止して再始動してから、以下のいずれかの手順を実行します。

    - コレクションが、機械学習モデルのトレーニングに使用する索引付き文書を文書キャッシュ内に既に含んでいる場合は、索引のフルビルドを再始動します。
    - コレクションに、機械学習モデルのトレーニングに使用する索引付き文書が含まれていない場合は、文書をアップロードし、文書をクロールするクローラーを少なくとも 1 つ構成し、クローラーを開始します。

1. **「エクスポート」**域で、エクスポート要求の状況を確認します。進行状況に、エクスポートされている文書の数が示されます。
1. エクスポート・オプションを構成したときに指定した出力フォルダーに移動します。文書を XML ファイルとしてエクスポートするとき、出力フォルダー名は、エクスポートが行われた時点のタイム・スタンプに基づいて付けられます。出力フォルダーには、XMI ファイル (`*.xmi`) と UIMA TypeSystem 記述子ファイル (`exported_typesystem.xml`) が含まれています。

#### 次に行うこと
{: #wks_uimawexca__preUIMAimport}

UIMA タイプと {{site.data.keyword.knowledgestudioshort}} エンティティー・タイプの間のマッピングを定義する必要があります。また、分析されたデータを {{site.data.keyword.knowledgestudioshort}} ワークスペースにアップロードするために必要なすべてのファイルを含む ZIP ファイルも作成する必要があります。

**関連情報**:

[Exporting crawled or analyzed documents![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ad.doc/iiysatexportca.htm){: new_window}

[Output paths for exported documents![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ad.doc/iiysaexportoutput.htm){: new_window}

### 分析されたコレクションの Content Analytics Studio からのエクスポート
{: #wks_uimawexstudio}

分析された文書のコレクションを {{site.data.keyword.watson}} Explorer Content Analytics Studio からエクスポートし、分析された文書を XMI ファイルとして {{site.data.keyword.knowledgestudioshort}} プロジェクトにアップロードできます。

#### 手順

分析された文書を Content Analytics Studio コレクションから取得するには、以下のようにします。

1. Content Analytics Studio を起動し、Studio プロジェクトを開きます。
1. 機械学習モデルのトレーニングに使用する文書を含むフォルダーを右クリックし、**「コレクションの分析 (Analyze Collection)」**を選択します。
1. UIMA パイプライン構成ファイルを選択します。
1. 「コレクション分析 (Collection Analysis)」ビューに移動し、「コレクション分析 (Collection Analysis)」ビューで**「保存 (Save)」**アイコンをクリックします。保存した結果を書き込むフォルダーを指定し、ファイル名を指定します。
1. 指定したフォルダーを開きます。保存ファイルのファイル拡張子は、`.annotations` です。
1. `.annotations` ファイルをローカル・ファイル・システムにコピーし、ファイル拡張子を `.annotations` から `.zip` に名前変更します。
1. ZIP ファイルからすべてのファイルを解凍します。解凍されたコンテンツには、XMI ファイル (`*.xmi`)、UIMA TypeSystem 記述子ファイル (`TypeSystem.xml`)、およびその他のファイルが含まれます。

#### 次に行うこと

UIMA タイプと {{site.data.keyword.knowledgestudioshort}} エンティティー・タイプの間のマッピングを定義する必要があります。また、分析されたデータを {{site.data.keyword.knowledgestudioshort}} ワークスペースにアップロードするために必要なすべてのファイルを含む ZIP ファイルも作成する必要があります。

### UIMA タイプからエンティティー・タイプへのマッピング
{: #wks_uimawexmap}

XMI ファイルを {{site.data.keyword.knowledgestudioshort}} ワークスペースにアップロードする前に、UIMA タイプと {{site.data.keyword.knowledgestudioshort}} エンティティー・タイプの間のマッピングを定義する必要があります。

#### 始めに

{{site.data.keyword.knowledgestudioshort}} ワークスペース内のタイプ・システムには、UIMA タイプをマップするエンティティー・タイプが含まれている必要があります。

#### 手順

UIMA タイプを {{site.data.keyword.knowledgestudioshort}} エンティティー・タイプにマップするには、以下のようにします。

1. UIMA TypeSystem 記述子ファイル (`exported_typesystem.xml` または `TypeSystem.xml` など) を含むフォルダー内に `cas2di.tsv` という名前のファイルを作成します。
1. テキスト・エディターで `cas2di.tsv` ファイルを開きます。ファイル内の各行は、1 つのマッピングを指定しています。マッピングのフォーマットは、どのアノテーターのアノテーションをマップするかによって異なります。

    - 以下の基本フォーマットを使用してマッピングを作成できます。

        `UIMA_Type_Name[TAB]WKS_Entity_Type`

        以下の例は、{{site.data.keyword.watson}} Explorer Content Analytics の固有表現抽出アノテーターによって作成された UIMA タイプと、{{site.data.keyword.knowledgestudioshort}} タイプ・システムで定義されたエンティティー・タイプの間のマッピングを定義します。

        ```
        com.ibm.langware.Organization  ORGANIZATION
        com.ibm.langware.Person  PERSON
        com.ibm.langware.Location  LOCATION
        ```
        {: screen}

        もう 1 つの例は、{{site.data.keyword.watson}} Explorer Content Analytics Studio で作成されたカスタム・アノテーターによって作成された UIMA タイプと、{{site.data.keyword.knowledgestudioshort}} エンティティー・タイプの間のマッピングを定義します。

        ```
        com.ibm.Person  PERSON
        com.ibm.Date  DATE
        ```
        {: screen}

    - {{site.data.keyword.watson}} Explorer Content Analytics 内のパターン・マッチャー・アノテーターまたは辞書ルックアップ・アノテーターで使用されるファセットに基づいてマッピングを作成できます。テキスト分析ルール・ファイル (`*.pat`) で、ファセットはカテゴリー属性として表されます。マッピングを定義するには、以下の構文を使用します。

        ```
        com.ibm.takmi.nlp.annotation_type.ContiguousContext:category={FACET_PATH}[TAB]{WKS_ENTITY_TYPE}
        ```
        {: screen}

        以下の例は、パターン・マッチャー・アノテーターと辞書ルックアップ・アノテーターに適用され、カテゴリー $.mykeyword.product と {{site.data.keyword.knowledgestudioshort}} エンティティー・タイプ PRODUCT の間のマッピングを定義します。

        ```
        com.ibm.takmi.nlp.annotation_type.ContiguousContext:category=$.mykeyword.product PRODUCT
        ```
        {: screen}

#### 次に行うこと

分析されたデータを {{site.data.keyword.knowledgestudioshort}} ワークスペースにアップロードするために必要なすべてのファイルを含む ZIP ファイルを作成する必要があります。

**関連情報**:

[Pattern Matcher annotator![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ta.doc/iiystapattmatch.htm){: new_window}

[Dictionary Lookup annotator![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ta.doc/iiystadictlookup.htm){: new_window}

[Named Entity Recognition annotator![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ta.doc/iiystasystemt.htm){: new_window}

### ワークスペースへの UIMA CAS XMI ファイルのアップロード
{: #wks_uimaweximport}

ダウンロードした事前アノテーション済み文書を使用してモデルをトレーニングするには、XMI ファイルのアップロードに必要なすべてのファイルを含む ZIP ファイルを作成し、その ZIP ファイルを {{site.data.keyword.knowledgestudioshort}} ワークスペースにアップロードする必要があります。

#### 始めに

ZIP ファイルをアップロードする前に、{{site.data.keyword.knowledgestudioshort}} ワークスペース内のタイプ・システムに、UIMA タイプをマップしたエンティティー・タイプが含まれていることを確認してください。

> **警告:** UIMA 分析エンジンでは、アノテーションが複数のセンテンスにまたがって存在することが許可されます。{{site.data.keyword.knowledgestudioshort}} では、アノテーションは 1 つのセンテンスの境界内に存在する必要があります。アップロードする XMI ファイルに、複数のセンテンスにまたがるアノテーションが含まれている場合、それらのアノテーションはグラウンド・トゥルース・エディターには表示されません。

#### 手順

事前アノテーション済み文書を {{site.data.keyword.knowledgestudioshort}} ワークスペースにアップロードするには、以下のようにします。

1. {{site.data.keyword.knowledgestudioshort}} に必要なすべてのファイルを含む ZIP ファイルを作成します。

    1. XMI ファイル、UIMA タイプ・システム記述子ファイル、および `cas2di.tsv` ファイルを含むフォルダーを選択するか、フォルダー内のすべてのファイルを選択します。
    1. すべてのファイルを含む ZIP ファイルを作成します。`cas2di.tsv` ファイルと UIMA タイプ・システム記述子ファイルが ZIP ファイルのルート・ディレクトリーに保管されていることを確認します。これらのファイルは ZIP ファイル内のサブフォルダーに保管できません。サブフォルダーに保管すると、{{site.data.keyword.knowledgestudioshort}} がそれらを読み取れず、何もインポートされません。

        Windows では、右クリックし、**「送る」** > **「圧縮 (zip 形式) フォルダー」**を選択できます。

1. ZIP ファイルを {{site.data.keyword.knowledgestudioshort}} ワークスペースにアップロードします。

    1. {{site.data.keyword.knowledgestudioshort}} 管理者またはプロジェクト管理者としてログインし、文書を追加するワークスペースを開き、**「アセットおよびツール (Assets & Tools)」** > **「文書 (Documents)」** ページを開きます。
    1. **「文書セットのアップロード (Upload Document Sets)」**をクリックします。
    1. 作成した ZIP ファイルをドラッグするか、クリックしてファイルを見つけて選択します。
    1. ZIP ファイルに UIMA CAS XMI ファイルが含まれていることを示すためのチェック・ボックスを選択します。
    1. **「アップロード (Upload)」**をクリックします。
