---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-17"

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

この文書は、{{site.data.keyword.cloud}} 上の {{site.data.keyword.knowledgestudiofull}} に関するものです。 以前のバージョンの {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 向けの資料を参照するには、[このリンクをクリック ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/docs/services/knowledge-studio/tutorials-create-rule-model.html){: new_window} してください。
{: tip}

# ルール・ベース・モデルの作成
{: #wks_tutrule_intro}

このチュートリアルは、文書内で定義したテキスト・パターンを検出するために使用できるルール・ベース・モデルの作成方法を理解するのに役立ちます。
{: shortdesc}

ここでは、パターン `month day, year` に一致する文書内のテキストを検出できるモデルを作成します。 例えば、このモデルは、*May 1, 2010* という日付参照を検出します。 ルール・パターン自体を定義する前に、パターンを作成するのに役立つ成果物を作成します。そのような成果物には、テキスト内で月のメンションを認識する辞書クラスと、年のメンションを認識する正規表現クラスが含まれます。

## 学習目標
{: #objectives}

このチュートリアルを完了すると、以下のタスクの実行方法が分かります。

- クラスの作成
- ルールを定義するための文書の追加
- 辞書とクラスの関連付け
- 文字のシーケンスをキャプチャーするための正規表現の定義
- ルールの定義

このチュートリアルを完了するには、約 30 分かかります。 このチュートリアルに関連する他の概念を調べると、完了までの時間が長くなる可能性があります。

## 始めに
{: #prereqs}

- サポートされているブラウザーを使用していることを確認してください。 詳しくは、『[ブラウザーの要件](/docs/services/watson-knowledge-studio/system-requirements.html)』を参照してください。
- [{{site.data.keyword.knowledgestudioshort}}の開始](/docs/services/watson-knowledge-studio/tutorials-create-project.html)が正常に完了しています。これにはワークスペースの作成、タイプ・システムの作成、辞書の追加が含まれます。
- Admin または Project Manager のいずれかの役割のユーザー ID を、少なくとも 1 つ持っている必要があります。 ユーザー役割については、[{{site.data.keyword.knowledgestudioshort}} のユーザー役割](/docs/services/watson-knowledge-studio/roles.html)を参照してください。

## 結果
{: #results}

ルール・ベース・モデルを作成した後、それを以下のいずれかの方法で使用して、文書内のテキスト・パターンを検出できます。

- 機械学習モデルを作成する前に、[文書に事前アノテーションを付ける](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotrule)
- 他の {{site.data.keyword.watson}} のサービスまたは製品に、[モデルをデプロイまたはエクスポートする](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html)

## 演習 1: 月の辞書の追加
{: #wks_tutless_rule1}

この演習では、{{site.data.keyword.knowledgestudioshort}} でワークスペースに辞書を追加する方法について学習します。 この辞書には、暦の月に関連する用語が含まれています。

### この作業について
{: #wks_tutless_rule1_about}

この後の演習では、この辞書に基づいてクラスを定義します。 このクラスを作成すると、文書内で検出された、この辞書内のすべての用語に、関連するクラス・タイプのメンションとして自動的にアノテーションが付きます。 辞書について詳しくは、『[ワークスペースへの辞書の追加](/docs/services/watson-knowledge-studio/dictionaries.html#wks_projdictionaries)』を参照してください。

### 手順
{: #wks_tutless_rule1_procedure}

1. <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/dictionary-items-month.csv" download>`dictionary-items-month.csv` <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン" title="外部リンク・アイコン" class="style-scope doc-content"></a> ファイルを、ご使用のコンピューターにダウンロードします。 このファイルには、{{site.data.keyword.knowledgestudioshort}} 辞書へのアップロードに適した辞書用語が CSV 形式で含まれています。
2. **「アセット (Assets)」**>**「辞書 (Dictionaries)」**をクリックします。
3. **「辞書の作成」**ボタンをクリックして、辞書を追加します。
4. **「名前」**フィールドに `Month dictionary` と入力し、**「保存」**をクリックして辞書を作成します。 新しい辞書が作成され、編集用に自動的に開かれます。
5. 辞書ペインで、**「アップロード」**をクリックします。
6. ご使用のコンピューターから `dictionary-items-month.csv` ファイルを選択して、**「アップロード」**をクリックします。

    ファイルから辞書に用語がインポートされます。

## 演習 2: サンプル文書の追加
{: #wks_tutless_rule2}

この演習では、定義するルールのタイプを示す言語パターンを含んだ文書を追加する方法について学習します。

### この作業について
{: #wks_tutless_rule2_about}

文書の追加について詳しくは、『[ルールを定義するための文書の追加](/docs/services/watson-knowledge-studio/rule-annotator-add-doc.html)』を参照してください。

### 手順
{: #wks_tutless_rule2_procedure}

1. <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/documents-new.csv" download>`documents-new.csv` <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン" title="外部リンク・アイコン" class="style-scope doc-content"></a> ファイルを、ご使用のコンピューターにダウンロードします。 このファイルには、アップロードに適したサンプル文書が含まれています。
1. **「ルール・ベース・モデル」**>**「ルール」**をクリックします。
1. **「文書 (Documents)」**ページ見出しの横にある**文書の追加**アイコンをクリックします。
1. **「CSV ファイルのアップロード」**タブをクリックします。
1. 前にコンピューターにダウンロードした `documents-new.csv` ファイルをクリックして参照し、**「アップロード」**をクリックします。

    文書のセットがメインの「文書」ページに表示されます。

    ![ ルール・エディターに追加された 14 個の文書のうちの 3 つを示しています。各文書のタイトルとそれぞれの冒頭からの抜粋を示しています。各文書の横に、その文書を削除するために使用できる削除アイコンも存在します。](images/rule-doc-add3.jpg "ルール・エディターに追加された 14 個の文書のうちの 3 つを示しています。各文書のタイトルとそれぞれの冒頭からの抜粋を示しています。各文書の横に、その文書を削除するために使用できる削除アイコンも存在します。")

## 演習 3: クラスの作成
{: #wks_tutless_rule3}

この演習では、ルールの定義時に使用するクラスの定義方法について学習します。

### この作業について
{: #wks_tutless_rule3_about}

クラスについて詳しくは、『[ルール](/docs/services/watson-knowledge-studio/rule-annotator.html)』を参照してください。

### 手順
{: #wks_tutless_rule3_procedure}

1. ワークスペースの**「ルール」**ページで、右側のパネルの**「クラス (Class)」**ヘッダーの横にある**クラスの追加**アイコンをクリックします。
1. クラス名として `DictMonth` と入力してから、**「追加」**をクリックします。

    新規クラスが「クラス」サイド・パネルに表示されます。

## 演習 4: 辞書とクラスの関連付け
{: #wks_tutless_rule4}

この演習では、ルール・エディターで辞書を使用する方法について学習します。

### 手順
{: #wks_tutless_rule4_procedure}

1. **「ルール・ベース・モデル (Rule-based Model)」**>**「ルール (Rules)」**をクリックしてから、**「辞書 (Dictionaries)」**タブをクリックします。
2. 前に作成した**「Month dictionary」**を選択します。
3. **「クラス」**リストから`「DictMonth」`を選択して、**「保存」**をクリックします。

    クラスが辞書に関連付けられます。

    ![「ルール (Rules)」ページの「辞書 (Dictionaries)」パネルで、DictMonth クラスが Month dictionary に関連付けられていることを示しています。](images/rule-dict-map2.jpg "「ルール (Rules)」ページの「辞書 (Dictionaries)」パネルで、DictMonth クラスが Month dictionary に関連付けられていることを示しています。")

### 結果
{: #wks_tutless_rule4_results}

ルール・エディターに関連付けられた文書の場合、辞書内の用語への参照には `DictMonth` クラスのメンションとしてアノテーションが付けられます。 次の演習では、これらの参照にアノテーションが付けられたことを確認します。

## 演習 5: 文書内のクラス・アノテーションの検出
{: #wks_tutless_rule5}

この演習では、ルール・エディター文書内でクラス・アノテーションを検出する方法について学習します。

### 手順
{: #wks_tutless_rule5_procedure}

1. **「ルール・ベース・モデル」**>**「ルール」**を選択します。
2. 「クラス」パネルで、前に定義した `DictMonth` クラスを見つけ、その横にある**文書内のアノテーションの検索**アイコンをクリックします。

    「アノテーションの検出 (Find Annotations)」ページが表示され、月へのテキスト参照を含んでいるすべての文書が表示されます。

3. `Technology - computerworld.com` 文書をクリックして、文書全体を表示します。 `February` というテキストが強調表示されていることに注意してください。これは、`DictMonth` クラスのメンションとしてアノテーションが付けられたことを意味します。

## 演習 6: 正規表現の定義
{: #wks_tutless_rule6}

この演習では、正規表現の定義方法について学習します。

### この作業について
{: #wks_tutless_rule6_about}

「`2009`」のような年のパターンを検出できる正規表現を定義します。

正規表現の定義について詳しくは、『[ルールの定義](/docs/services/watson-knowledge-studio/rule-annotator-define-rule.html)』を参照してください。

### 手順
{: #wks_tutless_rule6_procedure}

1. **「ルール」**ページで、右側のパネルから**「クラス (Class)」**の横にある**クラスの追加**アイコン ![「クラスの追加」アイコン](images/wks_tut_dict_add.jpg " ") をクリックします。
1. クラス名として `RegExpYear` と入力し、**「追加」**をクリックします。
1. **「Regex」**タブをクリックしてから、**「正規表現 (Regular Expressions)」**見出しの横にある**正規表現の作成**アイコンをクリックします。
1. **「項目の追加 (Add Entry)」**をクリックします。
1. **「正規表現 (Regular Expression)」**フィールドに次の式を入力します。この式は、`1900` と `2099` の間の年を検出します。

    ```
    (?:(?:19|20)[0-9]{2})
    ```
    {: screen}

1. **「最小ワード・トークン」**を `1` に、**「最大ワード・トークン」**を `1` に設定します。
1. **「追加」**をクリックして、この正規表現項目を保存します。
1. 正規表現名として `MyYearExp` と入力し、次に、**「クラス」** メニューから、前に定義した `RegExpYear` クラスを選択します。
1. **「保存 (Save)」**をクリックします。

    正規表現を保存した後、その正規表現がサンプル文書に自動的に適用されます。 正規表現で定義したパターンの直後にあるテキスト・ストリングには、`RegExpYear` クラスのメンションとしてアノテーションが付けられます。

1. 定義した式が時間の出現個所を正しくキャプチャーしているかどうかを検査するために、メンションを検索できます。 「クラス」パネルの **RegExpYear** クラスの横にある`文書内のアノテーションの検索`アイコンをクリックします。

    ![「ルール」ページの「クラス (Class)」パネルで、"RegExpYear" クラスの横にある拡大鏡アイコンの上にカーソルを移動している様子を示しています。](images/rule-regex-add5.jpg "横にある拡大鏡アイコンの上にカーソルを移動している様子を示しています")

    「アノテーションの検出 (Find Annotations)」ページが表示されます。 年のメンションの出現個所が、出現するサンプル文書内で強調表示されます。

    ![サンプル文書からの抜粋の中で強調表示された年のアノテーションを 8 つ示しています。](images/rule-regex-add6.jpg "サンプル文書からの抜粋の中で強調表示された年のアノテーションを 8 つ示しています。")

## 演習 7: ルールの定義
{: #unique_1166829415}

この演習では、ルールの定義方法について学習します。

### この作業について
{: #unique_1166829415_about}

月のメンションにアノテーションを付けるための辞書ベースのクラスが既に定義されています。 また、年を表す数値を検出する正規表現も定義しました。 ここでは、月とそれに続く数値、コンマ、そして年というシーケンスをキャプチャーするルールを定義します。 つまり、*September 21, 2016* のような日付式のルールを定義します。

ルールの定義について詳しくは、『[ルールの定義](/docs/services/watson-knowledge-studio/rule-annotator-define-rule.html)』を参照してください。

### 手順
{: #unique_1166829415_procedure}

1. **「ルール・ベース・モデル」**>**「ルール」**を選択し、`Technology - computerworld.com` 文書を開きます。
1. 文書内のテキスト `February 3, 2009` を選択します。 必ず、コンマも選択してください。

    ![文書内で選択されているテキスト "February 3, 2009" を示しています。](images/rule-add1.jpg "テキストを示しています")

2. **ルールの追加**アイコンをクリックします。

    ルール・エディターに、指定したルール・パターンの描写が表示されます。

    テキスト `February 3, 2009` が表示されます。 描写内のセルを接続している実線は、現在どのセルがパターンに含まれているかを示しています。
    - `DictMonth` クラスは、テキスト `February` ではなくルール・パターンの一部です。 この選択は推奨されます。このモデルでは、`February` というテキストだけではなく、日付パターン内の最初のトークンとして `DictMonth` クラスによってアノテーション付けされているすべての月を検出する必要があるからです。
    - ルールの最後で、既に `2009` という年に `RegExpYear` クラスのメンションとしてアノテーションが付けられています。 `RegExpYear` クラスは、数値 2009 ではなくルール・パターンの一部です。 この選択も推奨されます。このモデルでは、`2009` という特定のテキストだけではなく、日付パターン内の最後のトークンとして `RegExpYear` クラスによってアノテーション付けされているすべての年を検出する必要があるからです。

    数値 3 とその後のコンマ (,) は、パターン内の 2 番目と 3 番目のトークンとして示されています。 このパターンは現在指定されているので、このモデルは、月の第 3 日を指定している日付の出現個所だけを検出します。 しかし、このモデルでは、月の任意の日を指定した日付を検出したいので、次の作業は日のトークンのフィーチャー設定を変更することです。

3. `3` という日のセルの上で**テキスト**・アイコンをクリックして、トークンのフィーチャー設定を開きます。

    ![ユーザーがテキスト・フィーチャー設定アイコンをクリックしている様子を示しています。](images/rule-add4.jpg)

    現在、ルールは `3` というテキストに正確に一致するよう設定されています。 そうではなく、任意の数値に一致するようなルールにする必要があります。

4. **「文字タイプ: 数値 (Character Type : Numeric)」**を選択してから、**「テキスト: 3 (Text : 3)」**の選択をクリアすることにより、フィーチャー設定を数値に変更します。

    ![ユーザーが "3" のトークンのフィーチャー設定として「文字タイプ: 数値 (Character Type : Numeric)」オプションをクリックしている様子を示しています。](images/rule-add5.jpg "ユーザーがクリックしている様子を示しています")

    数値 `3` のセルの定義を変更しました。

    ![ "3" のトークンを表すセルの上に、任意の数値がパターン内のそのトークンに一致することを示す「文字タイプ (Character Type)」アイコンが付くようになりました。](images/rule-add6.jpg "次を表すセルを示しています ")

    **文字タイプ** アイコンは、その数値が正確に 3 である必要はなく、任意の数値でかまわないことを示しています。

5. コンマのトークンの設定は、何も変更しないでください。

    パターン内の 3 番目のトークンはコンマにする必要があるので、現在のフィーチャー設定である **「テキスト: ,」** は適切です。 フィーチャー設定のほかに、各トークンには繰り返し設定があります。 繰り返し設定は、トークンがテキスト内で何回まで繰り返されてもパターンと一致したことになるかを指定します。 **「必須 (正確に 1 つ)」**という現在の繰り返し設定は適切です。

    ![ 「正確に 1 つ (Exactly 1)」に設定されたコンマのトークンの繰り返し設定を示しています。](images/rule-add7.jpg "次のように設定されたコンマのトークンの繰り返し設定を示しています ")

6. パターン `DictMonth + numeric token + comma + RegExpYear` を表すクラスを割り当てます。

    文書から選択した 4 つのトークンを表す 4 つの空のセルに注目してください。 すべてのセルを選択するには、最初のセルを選択し、Shift キーを押しながら追加の各セルをクリックします。 クラス名として `RuleDate` と入力し、それをクリックして新規クラスを作成します。

    ![先頭の行にある 4 つのセルがすべて選択され、そのスパンが "RuleDate" クラスとして定義されている様子を示しています。](images/rule-add8.jpg "先頭の行にある 4 つのセルがすべて選択され、そのスパンが定義されている様子を示しています ")

7. **「ルール名」**フィールドに `MyDateRule` と入力し、**「保存」**をクリックします。

    ルールを保存した後、そのルールがサンプル文書に自動的に適用されます。 `Technology - computerworld.com` 文書がルール・エディターでまだ開かれている場合は、文書内の `February 3, 2009` というテキストに、RuleDate クラスのメンションとしてアノテーションが付けられたことが分かります。

    !["February 3, 2009" というテキストだけに "RuleDate" クラスのメンションであるというアノテーションが付いている "Technology - computerworld.com" 文書からのテキストを示しています。](images/rule-add10.jpg "テキストを示しています ")

    「クラス (Class)」パネルから `RuleDate` クラスの横にある**文書内のアノテーションの検索**アイコン ![検索を表す拡大鏡](images/filter_gray.png "検索を表す拡大鏡") をクリックして、サンプル文書に含まれる `RuleDate` クラスのメンションのすべての出現個所を検索できます。パターンを正しく定義したことを確認するために、すべての日付が正しくキャプチャーされているのを確認することをお勧めします。

    ![定義したばかりのルール・パターンに一致する日付が含まれる 2 つの文書を使用した「アノテーションの検出 (Find Annotations)」ページを示しています。](images/rule-add11.jpg "次を示しています ")

## 演習 8: ルール・ベース・モデルの作成
{: #wks_tutless_rule8}

この演習では、ルール・ベース・モデルの作成方法について学習します。

### この作業について
{: #wks_tutless_rule8_about}

ルール・ベース・モデルの作成について詳しくは、『[ルール・ベース・モデルの作成](/docs/services/watson-knowledge-studio/rule-annotator-model-create.html)』を参照してください。

### 手順
{: #wks_tutless_rule8_procedure}

1. **「ルール・ベース・モデル (Rule-based Model)」**>**「バージョン (Versions)」**を選択して、**「ルール・ベース・モデル・タイプ・マッピング (Rule-based model type mapping)」**タブをクリックします。

1. タイプ・システムから `DATE` エンティティーに `RuleDate` クラスをマップします。

    1. `DATE` エンティティーを見つけ、**「編集」**をクリックします。

        ![ユーザーが「ルール・ベース・モデル・タイプ・マッピング (Rule-based model type mapping)」タブで "DATE" エンティティー・タイプを対象に「編集 (Edit)」をクリックしている様子を示しています。](images/rule-anno2.jpg "ユーザーが「編集」をクリックしている様子を示しています ")

    1. リストから `RuleDate` クラスを選択して、**「保存」**をクリックします。

        ![ユーザーがリストから "RuleDate" クラスを選択している様子を示しています。](images/rule-anno3.jpg "ユーザーが選択している様子を示しています ")

1. ルール・ベース・モデルを使用して文書セットまたはアノテーション・セットに事前アノテーション付けを行うには、**「ルール・ベース・モデル (Rule-based Model)」**タブを選択し、**「このモデルを実行 (Run this model)」**をクリックします。

## チュートリアルの要約
{: #wks_tutrule_sum}

{{site.data.keyword.knowledgestudioshort}} について学習しながら、ルール・ベース・モデルを作成しました。

### 学習した演習
{: #lessons_learned}

このチュートリアルを修了すると、以下の概念について学習したことになります。

- クラス
- 正規表現
- ルール
