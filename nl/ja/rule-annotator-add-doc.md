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

この文書は、{{site.data.keyword.cloud}} 上の {{site.data.keyword.knowledgestudiofull}} に関するものです。以前のバージョンの {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 向けの資料を参照するには、[このリンクをクリック ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/docs/services/knowledge-studio/rule-annotator-add-doc.html){: new_window} してください。
{: tip}

# ルールを定義するための文書の追加
{: #wks_rule_anno_add}

定義するルールのタイプの良い例となる言語パターンを含む文書を追加します。
{: shortdesc}

ルールを定義するために追加する文書は、アノテーション用に追加する文書とは別に保持されます。それらの用途は単に、サンプル・パターンをマイニングするためのものです。トレーニングのために使用されることも、ダウンロードされることもありません。

## ルール・エディターに文書を追加する方法

- **UTF-8 形式のテキスト文書を作成**

    パターンの良い例となるテキストを直接ルール・エディターに追加できます。文書に指定する名前は、256 文字を超えることはできません。

- **CSV ファイルをアップロード**

    文書テキストを含んだファイルを CSV 形式でアップロードします。

- **アノテーション用にインポートされた文書をコピー**

    アノテーション目的でインポートされたセットの一部である文書に、ルールとして取り込むパターンのサンプルが含まれている場合、その文書をルール・エディターにコピーできます。その文書に対して行う変更は、アノテーションに使用されているオリジナル・バージョンの文書には影響しません。文書のアップロードについては、[ワークスペースへの文書の追加](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projadd)を参照してください。

コピーまたはアップロードする文書については、文書内のエンティティー・タイプを識別するのに役立つ明確なパターンを含んでいる文書を選択してください。
