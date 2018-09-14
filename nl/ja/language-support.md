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

この文書は、{{site.data.keyword.cloud}} 上の {{site.data.keyword.knowledgestudiofull}} に関するものです。 前のバージョンの {{site.data.keyword.IBM_notm}} マーケットプレイス上の {{site.data.keyword.knowledgestudioshort}} に関する文書を参照するには、[このリンクをクリックしてください ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/docs/services/knowledge-studio/language-support.html){: new_window}。
{: tip}

# 言語サポート
{: #language-support}

{{site.data.keyword.knowledgestudiofull}} は、モデルのトレーニングをいくつかの言語でサポートしています。

複数言語のサポートは、製品自体が翻訳されることを意味しません。 {{site.data.keyword.knowledgestudioshort}} のユーザー・インターフェース、メッセージ、および資料は、英語でのみ提供されています。
{: shortdesc}

以下の言語でモデルをトレーニングできます。

- 英語 (デフォルト言語)
- アラビア語
- ブラジル・ポルトガル語
- 中国語 (簡体字)
- オランダ語
- フランス語
- ドイツ語
- イタリア語
- 日本語
- 韓国語
- スペイン語

サポートには、ワークスペースへのこれらの言語の文書の追加、辞書の追加、事前アノテーションの実行、グランド・トゥルース・エディターを使用した文書へのアノテーション付け、および、機械学習モデルのトレーニングを行う機能が含まれています。 言語を選択すると、辞書項目の処理、テキストのトークン化、およびセンテンスの分割に、言語固有のテンプレートが適用されるようになります。 さまざまな言語の辞書がどのように処理されるのかについては、『[辞書](/docs/services/watson-knowledge-studio/dictionaries.html#wks_dictionaries)』を参照してください。

> **注:** ルール・エディターおよびルール・ベース・モデルは、双方向テキストを処理できないため、アラビア語の文書に使用することはできません。

> **制約事項:**
>
> 基礎にある機械学習テクノロジーでの文字制限のため、タイプ・システム内の項目はスペースを含むことができず、以下の ASCII 文字のみを含むことができます。
>
> - A から Z、および a から z
> - 0 から 9
> - 下線文字: _
>
> 次の規則も適用されます。
>
> - 名前の先頭文字は英字でなければなりません。
> - エンティティー・タイプ名の長さは 64 文字以下でなければなりません。
> - 関係タイプ名の長さは 128 文字以下でなければなりません。
>
> したがって、例えば、ヒューマン・アノテーターがグランド・トゥルース・エディターで日本語テキストにアノテーションを付ける際、適用可能なエンティティー・タイプ名および関係タイプ名は日本語ではありません。

### 関連タスク

[アラビア語サポートの構成](/docs/services/watson-knowledge-studio/language-support-arabic.html)
