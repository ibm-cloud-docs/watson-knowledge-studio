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

この文書は、{{site.data.keyword.cloud}} 上の {{site.data.keyword.knowledgestudiofull}} に関するものです。前のバージョンの {{site.data.keyword.IBM_notm}} マーケットプレイス上の {{site.data.keyword.knowledgestudioshort}} に関する文書を参照するには、[このリンクをクリックしてください ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/docs/services/knowledge-studio/language-support-arabic.html){: new_window}。
{: tip}

# アラビア語サポートの構成
{: #wks_langsupp_ar}

以下のガイドラインを読んで、{{site.data.keyword.knowledgestudioshort}} がアラビア語文書中の文字変形および数字変形をどのように処理するのかを理解してください。

## この作業について

文字変形に関して、アラビア語のアルファベットには大文字はありませんが、テキスト・ストリング中の位置および周囲の文字によって文字の形が変わることがあります。さまざまな方法で文字変形を処理する、さまざまなオペレーティング・システムおよびコード変換プログラムがあります。Windows システムでは非変形保管が標準であり、{{site.data.keyword.knowledgestudioshort}} は、アラビア語テキストが非変形で保管されていると仮定します。変形テキストを {{site.data.keyword.knowledgestudioshort}} にアップロードしたい場合は、標準ツールを使用して、まずテキストを非変形フォームに変換する必要があります。標準ツールには、International Components for Unicode (ICU) API などがあります ([http://icu-project.org/apiref/icu4j/com/ibm/icu/text/ArabicShaping.html ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://icu-project.org/apiref/icu4j/com/ibm/icu/text/ArabicShaping.html){: new_window} で ArabicShaping Class を参照してください)。

> **重要:** アラビア語の文字変形が適切でないことが原因で、グランド・トゥルース・エディターでコンテンツが正しく表示されないことがあります。

数字変形に関して、{{site.data.keyword.knowledgestudioshort}} は、数字変形を保管レベルのプロパティーとして扱います。これは iOS プラットフォームでアラビア語コンテンツが扱われる方法と似ています。多くのアラビア語コンテンツは、数字変形を表示レベルのプロパティーとして扱う Windows のようなプラットフォームで作成されるため、数字変形を保管レベルのプロパティーにするようにコンテンツを変換するか、あるいは、{{site.data.keyword.knowledgestudioshort}} を使用するときには Firefox ブラウザーを使用する必要があります。Firefox は、数字変形プリファレンスをブラウザー・レベルで明示的に設定して、ブラウザーで表示されるすべてのコンテンツに対して適切な表示を強制する機能をサポートします。

## 手順

Firefox ブラウザーで数字変形を構成するには、次のようにします。

1. ブラウザー URL フィールドに **about:config** と入力します。Firefox からの警告が表示される場合、警告を無視して続行するアクションをクリックします。**about:config** プロパティーの編集については、[http://kb.mozillazine.org/About:config_entries ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://kb.mozillazine.org/About:config_entries){: new_window} を参照してください。
1. 検索フィルターのフィールドに `bidi` と入力します。
1. 数字の表示方法を制御する **bidi.numeral** プロパティーを選択し、Enter を押します。
1. このプロパティーの値を必要に応じて変更します。例えば、`3` と入力し、**「OK」**をクリックします。

    - **0**: 普通の数字 (デフォルト値)
    - **1**: 通常の文脈の数字
    - **2**: ヒンディ語の文脈の数字
    - **3**: アラビア数字
    - **4**: ヒンディ数字

    > **重要:** **bidi.numeral** プロパティーが使用されている場合、Firefox は、Web ページのコンテンツ内の特定の数字のコード・ポイントを完全に無視します。

### 関連リファレンス

[複数言語サポート](/docs/services/watson-knowledge-studio/language-support.html)
