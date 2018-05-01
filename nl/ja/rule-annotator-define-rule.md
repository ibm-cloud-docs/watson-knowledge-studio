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

この文書は、{{site.data.keyword.cloud}} 上の {{site.data.keyword.knowledgestudiofull}} に関するものです。以前のバージョンの {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 向けの資料を参照するには、[このリンクをクリック ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/docs/services/knowledge-studio/rule-annotator-define-rule.html){: new_window} してください。
{: tip}

# ルールの定義
{: #wks_rule_creation}

ルール・エディターを使用して、ルールを定義します。
{: shortdesc}

## この作業について

予期しない上書きまたは重複が発生する可能性があるため、複数のユーザーがルール、クラス、および正規表現を同時に編集することは避けてください。

## 手順

ルールを定義するには、以下のステップを実行します。

1. {{site.data.keyword.knowledgestudioshort}} 管理者またはプロジェクト管理者としてログインし、**「ルール」**ページを開きます。
1. 「文書」の横にある正符号 (+) をクリックして、文書を追加します。

    詳しくは、[ルールを定義するための文書の追加](/docs/services/watson-knowledge-studio/rule-annotator-add-doc.html)を参照してください。

    例えば、次のような単一行のテキストを含む `My Document` という名前の文書を追加します。

    ```
    A 50-year-old driver was driving the 2017 Example Horizon.
    ```
    {: screen}

1. 正規表現を定義する場合、または辞書を追加する場合は、それに関連付けるクラスを作成します。

    1. **「クラス」**パネルで、「クラス」の横にある正符号 (+) をクリックします。
    1. クラス名を追加します。

        クラスを正規表現または辞書に関連付ける場合は、クラスの発生元を識別できるような名前をクラスに付けることを検討してください。例えば、正規表現を使用して、センテンス内の数値のパターンを定義する場合、AGE_REGEX という名前のクラスを作成できます。また、辞書を使用して、センテンス内の自動車メーカーにアノテーションを付ける場合には、MANUFACTURER_DICT という名前のクラスを追加できます。

        以下の命名規則に留意してください。
        - クラス名の先頭文字は英字でなければなりません。
        - クラスに追加する値には、次の英数字 ASCII 文字と下線文字のみを使用してください: A から Z、a から z、0 から 9。
        - 名前にスペースを含めることはできません。
        - 名前は 64 文字を超えることはできません。

1. オプション: 文書内のクラスに素早くアノテーションを付けるために、辞書をルール・エディターに関連付けることができます。辞書内の項目に一致する文書内の用語には、自動的に適切なクラスのアノテーションが付けられます。

    1. パネルの**「辞書 (Dictionaries)」**タブをクリックします。

        自身で作成した辞書がすべて表示されます。

        まだ辞書を追加していない場合は、メイン・ナビゲーション・バーから**「辞書 (Dictionaries)」**タブを開いて辞書を追加します。詳しくは、[辞書の作成](/docs/services/watson-knowledge-studio/dictionaries.html)を参照してください。

    1. 辞書をクリックし、その辞書のクラス関連を定義し、**「保存」**をクリックします。

        例えば、組織名を入れる辞書がある場合、それをルールに関連付けて、辞書に ORGANIZATION_DICT クラスを割り当てることができます。サンプル文書内に出現する組織名は、ORGANIZATION_DICT クラスのインスタンスとしてアノテーションが付けられます。

    後でルール・エディターから辞書の関連付けを削除する必要が発生した場合は、クラス・マッピングを削除できます。これを行うには、ドロップダウン・リストの先頭にある空のオプションを選択します。

1. オプション: ルールを構成するときに役立つ正規表現を定義するには、ナビゲーションから**「正規表現 (Regex)」**をクリックします。

    1. 「正規表現」の横にある正符号 (+) をクリックして、正規表現を追加します。
    1. 正規表現に名前を付けます。例えば、MyAgeRegex とします。

        名前は 64 文字を超えることはできません。

    1. 式をクラスに関連付けます。例えば、AGE_REGEX です。
    1. **「項目の追加 (Add Entry)」**をクリックします。
    1. 式を追加します。

        例えば、年齢を表す数値 (最大 99 まで) を取り込むには、`[0-9]{1,2}` を指定できます。*12:30 AM* のような、時間を表す式を取り込むには、以下のような正規表現を指定できます。

        ```
        (1[0-2]|0?[1-9]):([0-5][0-9])(\s+[AaPp][Mm])?
        ```
        {: screen}

        オプションで、ワード・トークンの最小数と最大数を変更できます。英語では、多くの場合トークンは、センテンス内の空白で区切られた語数と等しくなります。ただし、それらは必ずしも単語と 1 対 1 で一致するとは限りません。状況によっては、他のテキスト要素が、トークンと見なされます。例えば、用語 *50-year-old* に含まれるハイフンはそれぞれトークンとしてカウントされます。これは、この用語で使用されるトークンの総数が 5 であることを意味します。また、テキスト *12:30 PM* には 4 つのトークンが含まれます。(`12 | : | 30 | PM`)

        **「追加」**をクリックします。

    1. さらに式を追加する場合は、上記の 2 つのステップを繰り返します。
    1. **「保存 (Save)」**をクリックします。

    正規表現エディターが閉じられ、文書が表示されます。突き合わせ対象として、テキストに適用される正規表現に対して定義したクラスが表示されます。表示されない場合は、式を確認してください。検出されるべきテキストと一致するように修正する必要があるかもしれません。

    ![ルール・エディターで "Regex" タブが選択され、クラス "AGE_REGEX" に関連付けられた正規表現 "Age"、およびテキスト "50" が黄色で強調表示されている文書が示されています。強調表示されたテキストは、作成された正規表現と一致しています。](images/rule_step3.jpg)

1. ルールを定義するには、ナビゲーションから**「ルール」**をリックします。
1. ルールとして取り込むパターンを含む文書を開きます。例えば、`50-year-old` という句を含むサンプル・テキストが入った `My Document` というタイトルの文書を作成した場合、その文書を開きます。
1. 文書内のテキストから、取り込むパターンの良い例となる文字を選択します。例えば、以下の語とハイフン (-) を選択できます。

    ```
    50-year-old
    ```
    {: screen}

    文字を選択したら、ルールを追加できます。

1. **「ルール」**パネルで正符号 (+) をクリックします。

    ルール・エディターは、選択されたテキストを 2 層のセルとして表します。上部の層のセルは、基礎となるトークンのクラスにアノテーションを付ける場所です。下部の層は、トークンがパターンに参加するための条件を定義する場所です。

    ![文書からテキストを選択し、「ルール」パネル内で正符号をクリックした後に「ルールの作成」パネルがどのようになるかを示したルール・エディター。次のようなグラフィック・エレメントが表示されています: 用語「AGE」が入力された「ルール名」フィールド、「ルールの作成」パネル、および「クラス」パネル。「ルールの作成」パネルでは、点線のセルが上部に表示されています。選択されたテキストのトークンごとに 1 つのセルが表示されます。これらのセル内で、トークンのクラスにアノテーションを付けます。「ルールの作成」パネルの下部には、実線のセルが表示されます。各セルに、選択されたテキスト "50-year-old" のトークンが含まれます。トークンは、"50"、"-" (ハイフン)、"year"、"-"、および "old" です。各実線のセルの隣には 2 つのアイコンがあり、それらのアイコンを使用して、単語またはアノテーションの条件を調整できます。](images/rule_step4.jpg)

1. 各トークンがパターンに参加するための条件を定義します。

    下部の層のセルで、最初のトークンをクリックしてその条件を確認します。パターン内の現在位置で任意のトークンを使用できることを示すには、**「プロパティーを開く (Open Properties)」**をクリックし、**「任意のトークンの許可 (Allow any token)」**を選択します。**「プロパティーを閉じる (Close Properties)」**をクリックします。例にあるように、トークンが `AGE_REGEX` などの正規表現である場合、**「任意のトークンの許可 (Allow any token)」**は使用できません。

    > **注:** 各セルの繰り返し設定が 1 以下の場合、パターンに参加できるグループ・セルの最大数は 15 です。グループ・セルには、単一トークン、アノテーション、または任意のトークンが許可される場合のトークンが含まれます。パターンで許可されるトークン合計の最大数は 20 です。パターンを定義するとき、各セルの繰り返し設定を考慮に入れてください。例えば、各セルが 1 つ以下の繰り返し設定を持つ場合、15 個のトークンを含むパターンを定義できます。しかし、各トークンの繰り返し設定が 1 以上の場合、トークンは最大で 5 回まで繰り返すことができるため、パターンには 4 個を超えるトークンを定義できません。4 個のトークンが 5 回繰り返されると、許容される最大数の 20 になります。

    特定のタイプのトークンが必要であることを示すには、以下のタイプの条件設定を定義できます。
    - **繰り返し設定**: パターン内に現在のトークンを含める必要がある回数を指定します。繰り返し設定は変更できますが、トークンごとに指定できる繰り返し設定は 1 つのみです。オプションについて、以下の表で説明します。

    <table cellpadding="4" cellspacing="0" summary="" border="1" class="simpletable">
      <tr class="sthead">
        <th valign="bottom" align="left" id="d27028e471" class="stentry thleft thbot">設定オプション</th>
        <th valign="bottom" align="left" id="d27028e473" class="stentry thleft thbot">説明</th>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e471" class="stentry">
          <p class="p wrapper">必須 (正確に 1 つ)</p>
        </td>
        <td valign="top" headers="d27028e473" class="stentry">
          <p class="p wrapper">このトークンは、パターン内に 1 回存在する
            必要があります。このオプションはデフォルトで適用されますが、
            変更できます。</p></td>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e471" class="stentry">
          <p class="p wrapper">1 回以上繰り返し</p>
        </td>
        <td valign="top" headers="d27028e473" class="stentry">
          <p class="p wrapper">このトークンは、パターン内に 1 回以上存在
            しなければならず、さらに繰り返すことができます。</p>
        </td>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e471" class="stentry">
          <p class="p wrapper">0 回以上繰り返し</p>
        </td>
        <td valign="top" headers="d27028e473" class="stentry">
          <p class="p wrapper">このトークンは、オプションでパターン内で複数回
            繰り返すことができますが、必ずしも繰り返す必要はありません。</p>
        </td>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e471" class="stentry">
          <p class="p wrapper">0 回または 1 回発生</p>
        </td>
        <td valign="top" headers="d27028e473" class="stentry">
          <p class="p wrapper">このトークンはオプションです。</p>
        </td>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e471" class="stentry">
          <p class="p wrapper">拡張: _カスタム_</p>
        </td>
        <td valign="top" headers="d27028e473" class="stentry">
          <p class="p wrapper">このトークンは、ここで指定される回数だけ
            パターン内で繰り返す必要があります。カスタム
            繰り返し設定を定義するには、
            <b>「プロパティーを開く (Open Properties)」</b>を
            クリックし、**「拡張 (Advanced)」**を選択し、定義する繰り返しの正確な回数または繰り返しの範囲を選択します。</p>
          <p class="note">
            トークンに対して許可される繰り返しの最大数は 5 です。
            </p>
        </td>
      </tr>
    </table>

    - **フィーチャー設定 (Feature Setting)**: 少なくとも 1 つのフィーチャー設定を定義する必要があります。テキストがこのパターンに一致するために満たす必要がある条件の数に追加するフィーチャーをさらに追加できます。オプションについて、以下の表で説明します。

    <table cellpadding="4" cellspacing="0" summary="" border="1" class="simpletable">
      <tr class="sthead">
        <th valign="bottom" align="left" id="d27028e512" class="stentry thleft thbot">設定オプション</th>
        <th valign="bottom" align="left" id="d27028e514" class="stentry thleft thbot">追加する条件</th>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e512" class="stentry">
          <p class="p wrapper">テキスト</p>
        </td>
        <td valign="top" headers="d27028e514" class="stentry">
          <p class="p wrapper">このトークンのテキストと正確に一致
            しなければなりません。このオプションはデフォルトで適用されます。別の設定
            を条件として追加した場合、または「任意のトークン」設定を適用した場合にのみ、
            これを削除できます。</p>
        </td>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e512" class="stentry">
          <p class="p wrapper">長さ</p>
        </td>
        <td valign="top" headers="d27028e514" class="stentry">
          <p class="p wrapper">このトークンの文字長と一致
            しなければなりません。長さは、0 からカウントが始まり、先頭文字の
            前から数えられます。</p>
        </td>
      </tr>
    </table>

    残りのオプションは、トークンのタイプによって異なります。

    - **正規表現または辞書用語に一致しないアノテーションなしのトークン**: これらの設定は、アノテーションが付けられず、正規表現にも辞書用語にも一致しないトークンに使用できます。

    <table cellpadding="4" cellspacing="0" summary="" border="1" class="simpletable">
      <tr class="sthead">
        <th valign="bottom" align="left" id="d27028e535" class="stentry thleft thbot">設定オプション</th>
        <th valign="bottom" align="left" id="d27028e537" class="stentry thleft thbot">説明</th>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e535" class="stentry">
          <p class="p wrapper">品詞</p>
        </td>
        <td valign="top" headers="d27028e537" class="stentry">
          <p class="p wrapper">このトークンと同じ品詞でなければ
            なりません。以下のタイプがサポートされます。</p>
          <ul class="ul bullets">
            <li class="li">
              <p class="p wrapper">形容詞</p>
            </li>
            <li class="li">
              <p class="p wrapper">接置詞</p>
            </li>
            <li class="li">
              <p class="p wrapper">副詞</p>
            </li>
            <li class="li">
              <p class="p wrapper">接続詞</p>
            </li>
            <li class="li">
              <p class="p wrapper">限定詞</p>
            </li>
            <li class="li">
              <p class="p wrapper">間投詞</p>
            </li>
            <li class="li">
              <p class="p wrapper">名詞</p>
            </li>
            <li class="li">
              <p class="p wrapper">数詞</p>
            </li>
            <li class="li">
              <p class="p wrapper">代名詞</p>
            </li>
            <li class="li">
              <p class="p wrapper">残余</p>
            </li>
            <li class="li">
              <p class="p wrapper">動詞</p>
            </li>
          </ul>
        </td>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e535" class="stentry">
          <p class="p wrapper">見出し語</p>
        </td>
        <td valign="top" headers="d27028e537" class="stentry">
          <p class="p wrapper">このトークンと同じ見出し語が
            必要です。</p>
        </td>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e535" class="stentry">
          <p class="p wrapper">文字タイプ</p>
        </td>
        <td valign="top" headers="d27028e537" class="stentry">
          <p class="p wrapper">このトークンと同じ文字タイプが
            必要です。以下のタイプがサポートされます。</p>
          <ul class="ul bullets">
            <li class="li">
              <p class="p wrapper">Arabic: アラビア語文字のシーケンスが
                含まれます。</p>
            </li>
            <li class="li">
              <p class="p wrapper">ChineseNumeral: 漢数字のみが
                含まれます。</p>
            </li>
            <li class="li">
              <p class="p wrapper">ClauseEndingPunctuation:
                1 つの節またはセンテンスを次の節またはセンテンスから
                分離する句読点文字。</p>
            </li>
            <li class="li">
              <p class="p wrapper">Han: 漢字が含まれます。</p>
            </li>
            <li class="li">
              <p class="p wrapper">Hangul: 韓国のハングルの
                音節文字が含まれます。</p>
            </li>
            <li class="li">
              <p class="p wrapper">Hebrew: ヘブライ語の文字のシーケンスが
                含まれます。</p>
            </li>
            <li class="li">
              <p class="p wrapper">Hiragana: 日本のひらがな
                音節文字が含まれます。</p>
            </li>
            <li class="li">
              <p class="p wrapper">Ideographic: 表意文字、
                またはアイデアや物を表す記号が
                含まれます。</p>
            </li>
            <li class="li">
              <p class="p wrapper">Katakana: 日本のカタカナ
                音節文字が含まれます。</p>
            </li>
            <li class="li">
              <p class="p wrapper">Lowercase: 小文字の英字のみ
                が含まれます。</p>
            </li>
            <li class="li">
              <p class="p wrapper">Numeric: 数字のみが
                含まれます。</p>
            </li>
            <li class="li">
              <p class="p wrapper">Punctuation: テキスト内の
                句読点を示す 1 つ以上の文字。
               </p>
            </li>
            <li class="li">
              <p class="p wrapper">Syllabic: 音節文字が
                含まれます。</p>
            </li>
            <li class="li">
              <p class="p wrapper">Thai: タイ語の文字が
                含まれます。</p>
            </li>
            <li class="li">
              <p class="p wrapper">Titlecase: 単一の大文字の英字
                で始まり、その後に 1 つ以上の英小文字が続きます。</p>
            </li>
            <li class="li">
              <p class="p wrapper">Uppercase: 大文字の英字
                のみを含むトークン</p>
            </li>
          </ul>
        </td>
      </tr>
    </table>

    - **ルールの一致:**

    <table cellpadding="4" cellspacing="0" summary="" border="1" class="simpletable">
      <tr class="sthead">
        <th valign="bottom" align="left" id="d27028e617" class="stentry thleft thbot">設定オプション</th>
        <th valign="bottom" align="left" id="d27028e619" class="stentry thleft thbot">説明</th>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e617" class="stentry">
          <p class="p wrapper">ルールの一致</p>
        </td>
        <td valign="top" headers="d27028e619" class="stentry">
          <p class="p wrapper">指定されたクラスと一致する必要があります。
            クラスは、正規表現、辞書、またはルールから派生
            させることができます。例えば、ここに指定された
            クラスが正規表現から派生したものである場合、
            このトークンは、式の検索パターンと一致する
            必要があります。</p>
        </td>
      </tr>
    </table>

1. 辞書のアノテーションまたは正規表現の突き合わせから間接的に追加されたアノテーションを持つトークンの場合、パターンで、同じアノテーション・タイプの語、または代わりにアノテーションが付けられた実際の基本の語を必要とするかどうかを選択できます。

    下部の層のセルでは、水平線によってセル同士が接続されているため、どのセルがパターンに含まれているかを確認できます。アノテーションが適用された場所では、分割が見られます。元の単語を含むセルは、アノテーション・ラベルが付いたセルの下に表示されます。セルの一方のセット、またはもう一方のセットをクリックして、ラインのパスを変更し、パターンに含まれるセルを変更できます。

    例えば、パターンで年齢の正規表現と突き合わせをする代わりに、パターンで 50 を使用するように選択できます。

    ![「ルールの作成」パネルでの、ルール内でアノテーション "AGE_REGEX" を使用するトークン "50" の編集を示しています。デフォルトでは、"AGE_REGEX" アノテーションが使用されますが、パターンを編集して、基礎にある単語 "50" が代わりに使用されるようにできます。](images/rule_step5.jpg)

1. パターンの順序を設定したら、テキスト内のトークンにアノテーションを付けることができます。

    上部層のセルから、アノテーションを付けるトークンを表すセルをクリックし、それらにクラス・ラベルを適用します。複数のセルを選択するには、セルを 1 つクリックし、**Shift** キーを押しながら追加するセルをクリックします。

    選択したセルにクラスを割り当てます。割り当てるクラスが存在しない場合は、追加できます。クラス名を**「クラスの割り当て (Assign class)」**フィールドに入力し、**Enter** を押します。

    > **注:** 10 個を超えるクラスをルールに追加することはできません。

    ![「ルールの作成」セクションに、トークンをクリックすると開く「クラスの割り当て (Assign class)」ウィンドウが表示されています。ウィンドウには、新しいクラスの名前を入力するか、リストから既存のクラスを選択できるフィールドが表示されます。](images/rule_step6.jpg)

1. ルールに名前を付けます。

    ルール名は 64 文字を超えることはできません。

1. 「ルール」パネルで**「保存」**をクリックして、ルールを保存します。
