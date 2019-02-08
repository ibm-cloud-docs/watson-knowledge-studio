---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-19"

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

この文書は、{{site.data.keyword.cloud}} 上の {{site.data.keyword.knowledgestudiofull}} に関するものです。 前のバージョンの {{site.data.keyword.IBM_notm}} マーケットプレイス上の {{site.data.keyword.knowledgestudioshort}} に関する文書を参照するには、[このリンクをクリックしてください ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/docs/services/knowledge-studio/glossary.html){: new_window}。
{: tip}

# 用語集
{: #glossary}

この用語集には、{{site.data.keyword.knowledgestudioshort}} の用語および定義が含まれています。
{: shortdesc}

この用語集では、以下の相互参照が使用されています。

- 「*参照*」は、ある用語について優先される同義語を示すか、頭字語または省略語の完全形を示します。
- 「*も参照*」は、関連用語または対比される用語を示します。

[A](/docs/services/watson-knowledge-studio/glossary.html#gloss_A) [B](/docs/services/watson-knowledge-studio/glossary.html#gloss_B) [C](/docs/services/watson-knowledge-studio/glossary.html#gloss_C) [D](/docs/services/watson-knowledge-studio/glossary.html#gloss_D) [E](/docs/services/watson-knowledge-studio/glossary.html#gloss_E) [F](/docs/services/watson-knowledge-studio/glossary.html#gloss_F) [G](/docs/services/watson-knowledge-studio/glossary.html#gloss_G) [H](/docs/services/watson-knowledge-studio/glossary.html#gloss_H) [I](/docs/services/watson-knowledge-studio/glossary.html#gloss_I) [K](/docs/services/watson-knowledge-studio/glossary.html#gloss_K) [L](/docs/services/watson-knowledge-studio/glossary.html#gloss_L) [M](/docs/services/watson-knowledge-studio/glossary.html#gloss_M) [N](/docs/services/watson-knowledge-studio/glossary.html#gloss_N) [O](/docs/services/watson-knowledge-studio/glossary.html#gloss_O) [P](/docs/services/watson-knowledge-studio/glossary.html#gloss_P) [R](/docs/services/watson-knowledge-studio/glossary.html#gloss_R) [S](/docs/services/watson-knowledge-studio/glossary.html#gloss_S) [T](/docs/services/watson-knowledge-studio/glossary.html#gloss_T)

## A
{: #gloss_A}

- **正確度 (accuracy)**

    機械学習モデルによって生成されるアノテーションの正確さの指標。 [精度 (precision)](/docs/services/watson-knowledge-studio/glossary.html#gloss_P) および[リコール (recall)](/docs/services/watson-knowledge-studio/glossary.html#gloss_R) も参照。

- **正確度分析 (accuracy analysis)**

    機械学習モデルのスコアを分析して、正確度を向上させるために変更が必要かどうかを判断すること。

- **裁定 (adjudication)**

    異なるヒューマン・アノテーターが同じ文書に追加したアノテーションを比較することによってアノテーション競合を解決する反復プロセス。

- **分析エンジン (analysis engine)**

    UIMA Analysis Engine インターフェース仕様を実装する、文書などの成果物の分析とそれらに関する情報の推測を行うプログラム。 分析エンジンは、アノテーターと呼ばれるビルディング・ブロックから構成される。 分析エンジンは、単一のアノテーターを含む (プリミティブ分析エンジンと呼ばれる) か、複数のアノテーターを含む (集合分析エンジンと呼ばれる) ことができる。

- **アノテーション (annotation)**

    ある幅のテキストに関する情報。 例えば、あるアノテーションは、ある幅のテキストが会社名を表していることを示す。

- **アノテーション・セット (annotation set)**

    ヒューマン・アノテーションの場合、複数のヒューマン・アノテーターで作業負荷を分け合えるようにコーパスから取り出された文書の集合。 機械ベースのアノテーションの場合、ブラインド・データ、トレーニング・データ、またはテスト・データとして使用できる文書の集合。

- **アノテーション・プロセス管理者 (annotation process manager)**

    ワークスペースにおけるアノテーション・ライフサイクルの全アクティビティーの管理を担当する役割。 通常、ワークスペースに追加されたプロジェクト管理者がアノテーション・プロセス管理者のアクティビティーを実行する。

- **アノテーター (annotator)**

    [ヒューマン・アノテーター (human annotator)](/docs/services/watson-knowledge-studio/glossary.html#gloss_H) および[機械学習アノテーター (machine learning annotator)](/docs/services/watson-knowledge-studio/glossary.html#gloss_M) を参照。

- **属性 (attribute)**

    エンティティーを説明する、エンティティーの特性または特徴。例えば、従業員の電話番号は従業員の属性の 1 つである。

## B
{: #gloss_B}

- **ブラインド・データ (blind data)**

    グランド・トゥルースでアノテーションが付けられた文書のセット (例えば、質問と回答のペア、セマンティック・アノテーション、パッセージ判断など)。 ブラインド・データは、開発者によってリリースされたり、見られたりすることは決してなく、見られていないデータでのパフォーマンスを評価するためにシステムを定期的にテストするために使用される。 ブラインド・データでのテストは、既知の質問セットまたはアノテーションに過剰適合することによって正確度が損なわれることを防止する。 ブラインド・データで実行されたテストからのみの結果が報告される必要がある。 [テスト・データ (testing data)](/docs/services/watson-knowledge-studio/glossary.html#gloss_T) および[トレーニング・データ (training data)](/docs/services/watson-knowledge-studio/glossary.html#gloss_T) も参照。

## C
{: #gloss_C}

- **コンコーダンス (concordance)**

    文書全体で、および複数のアノテーション・セットにまたがって、同じメンションに同じエンティティー・タイプでアノテーションが付けられることを保証する手段を提供する。 コンコーダンスは、ヒューマン・アノテーターが各オカレンスに手動でラベルを付ける必要なく、同じメンションの複数のオカレンスでの整合性を確保するのを支援する。

- **コンフュージョン・マトリックス (confusion matrix)**

    アノテーションが付けられた文書セットの詳細な数値明細を提供する表。 この表は、機械学習モデルによって追加されたアノテーションをグランド・トゥルースのアノテーションと比較するために使用される。 この表は、[フォールス・ポジティブ (false positive)](/docs/services/watson-knowledge-studio/glossary.html#gloss_F)、[フォールス・ネガティブ (false negative)](/docs/services/watson-knowledge-studio/glossary.html#gloss_F)、[トゥルー・ポジティブ (true positive)](/docs/services/watson-knowledge-studio/glossary.html#gloss_T)、および[トゥルー・ネガティブ (true negative)](/docs/services/watson-knowledge-studio/glossary.html#gloss_T) の数を報告する。

- **照応 (coreference)**

    2 つの単語または句の間の関係で、両方が同じ人または物を指し、一方が他方の言語的先行詞である関係。 例えば、「She taught herself」という句の 2 つの代名詞の間には照応があるが、「She taught her」という句ではそうではない。 照応は、同じテキスト中の 2 つの等価なエンティティーをリンクする。

- **照応チェーン (coreference chain)**

    照応としてアノテーションが付けられたエンティティーのリスト。 メンションに照応としてアノテーションを付けると、システムによって照応チェーンが作成される。 文脈の中ですべてのメンションを確認して、オカレンスのすべてが同じエンティティー・タイプに属していることを検証する手段が、チェーンによって提供される。

- **コーパス (corpus)**

    ワークスペースに追加されて機械学習モデルのトレーニングに使用されたソース文書の集合。

- **整理 (curate)**

    特定のトピックに関連するコンテンツを選択、収集、保存、および保守すること。 整理は、データを信頼できる情報およびナレッジに変換し、データの価値を高める。

## D
{: #gloss_D}

- **辞書 (dictionary)**

    文書に事前にアノテーションを付けるために使用できる単語の集合。 文書テキスト中に辞書用語に一致する単語があるたびに、新規アノテーションが作成される。 1 つの機械学習モデルを、製薬に関する辞書や資産管理に関する辞書など、通常は分野別である 1 つ以上の独立した辞書と共に構成できる。 [見出し語 (lemma)](/docs/services/watson-knowledge-studio/glossary.html#gloss_L) および[表層形 (surface form)](/docs/services/watson-knowledge-studio/glossary.html#gloss_S) も参照。

- **辞書プレアノテーター (dictionary pre-annotator)**

    特定の単語セットに一致するメンションをテキスト内で識別するコンポーネント。 辞書プレアノテーターが分野固有の用語を使用してテキストに事前にアノテーションを付けることにより、ヒューマン・アノテーターはグランド・トゥルース文書のセットを早く準備できる。

- **文書セット (document set)**

    文書の集合。 一緒にインポートされた文書は 1 つの文書セットになる。 トレーニング目的のためにグループ (テスト、トレーニング、ブラインド) にまとめられた、アノテーションが付けられた文書は、文書セットとして生成される。

## E
{: #gloss_E}

- **エンティティー (entity)**

    1. エンティティー・タイプによってアノテーションが付けられたメンション。
    1. その情報が保管対象となる人、物、または概念。
    1. 人、場所、銀行口座などの実世界のオブジェクトについて保持される詳細一式。 エンティティーは一種の項目である。

- **エンティティー・タイプ (entity type)**

    文脈の考慮なしでメンションが表すエンティティーのタイプ。 例えば、メンション {{site.data.keyword.IBM_notm}} にエンティティー・タイプ ORGANIZATION でアノテーションを付けることができる。

    エンティティー・リレーションシップ・モデルでは、エンティティー・タイプは、人や場所の名前など、モデル化されるもの、またはメンションが指すものである。 異なるエンティティー・タイプは、「surname」または「home town」など、異なる属性セットを持ち、「lives in」のような関係を通して結合される。 各エンティティー・タイプは独立して存在し、一意的に識別できる。

## F
{: #gloss_F}

- **F1 スコア (F1 score)**

    精度とリコールの両方を考慮してスコアが計算される、テストの正確度の指標。 F1 スコアは、精度値とリコール値の加重平均であると解釈できる。 F1 スコアの最高の値は 1、最悪の値は 0 である。

- **フォールス・ネガティブ (false negative)**

    正しいが、正しくないと予測された、回答またはアノテーション。

- **フォールス・ポジティブ (false positive)**

    正しくないが、正しいと予測された、回答またはアノテーション。

- **フィーチャー (feature)**

    タイプのデータ・メンバーまたは属性。

- **フライス・カッパ・スコア (Fleiss Kappa score)**

    重複文書において複数のヒューマン・アノテーターがどの程度整合して同じアノテーションを適用したかを表す指標。 フライス・カッパ・スコアの最高の値は 1、最悪の値は 0 である。

## G
{: #gloss_G}

- **グランド・トゥルース (ground truth)**

    機械学習モデルを特定の分野に適応させるために使用される、ヒューマン・アノテーターによって追加されたアノテーションからなる入念に吟味されたデータの集合。 グランド・トゥルースは、機械学習モデルをトレーニングするため、モデルのパフォーマンス (精度およびリコール) を計測するため、および、パフォーマンス改善のためにどこに開発作業を集中させるべきかをヘッドルームを計算して判別するために使用される。 グランド・トゥルースにおける不正確さはそれを使用するコンポーネントでの不正確さと相関するため、グランド・トゥルースが正確であることは重要である。

## H
{: #gloss_H}

- **ヘッドルーム分析 (headroom analysis)**

    正確度分析の実行中に識別されたある種の問題への対処によって、正確度、精度、またはリコールの改善がどのくらい期待できるのかを判定するプロセス。

- **ヒューマン・アノテーター (human annotator)**

    メンション、エンティティー・タイプ関係、およびメンション照応を識別することによって、事前アノテーションの結果を検討、修正、および増補する、対象分野の専門家。 ヒューマン・アノテーターは、文脈の中でテキストを調べることによって、グランド・トゥルースの決定および機械学習モデルの正確度の改善を助ける。

## I
{: #gloss_I}

- **アノテーター間一致 (inter-annotator agreement)**

    複数の文書セットにある同じ文書へのアノテーションの付け方がどのくらい似ているのかを表す指標。

## K
{: #gloss_K}

- **ナレッジ・グラフ (knowledge graph)**

    タイプ付きエンティティー、それらの関係、プロパティー、および階層型分類構造を統合して、特定の分野の概念がどのように編成されているのを表すモデル。 構造化データ・ソースおよび非構造化データ・ソースからの入力と共にナレッジ・グラフ・ストアがロードされた後、ユーザーおよびアプリケーションはナレッジ・グラフにアクセスして、特定分野のナレッジの主要エレメントを探索したり、相互作用を探索したり、さらに関係を発見したりできる。

## L
{: #gloss_L}

- **見出し語 (lemma)**

    単語の正規形または標準形。 通常、見出し語は、非派生かつ非活用形式の名詞または動詞である。 例えば、用語「organizing」および「organized」の見出し語は「organize」である。 [辞書 (dictionary)](/docs/services/watson-knowledge-studio/glossary.html#gloss_D) および[表層形 (surface form)](/docs/services/watson-knowledge-studio/glossary.html#gloss_S) も参照。

## M
{: #gloss_M}

- **機械学習 (machine learning)**

    過去のデータから反復して学習し、新しいデータに接したときは自主的に適応する、データ分析手法。 機械学習の中核にある数学モデルはグランド・トゥルース入力から構築される。 トレーニングとサンプル入力データの改良により、モデルは新しいデータを分析するときに正確で反復可能な結果を生成できる。

- **機械学習アノテーター (machine learning annotator)**

    [機械学習モデル (machine learning model)](/docs/services/watson-knowledge-studio/glossary.html#gloss_M) を参照。

- **機械学習モデル (machine learning model)**

    グランド・トゥルースに基づいた統計モデルに従ってエンティティーおよびエンティティー関係を識別するコンポーネント。 モデルは、過去の経験 (トレーニング・データなど) を応用して、データの特性に基づいて将来の経験の正しい結果を判定または予測する。 このような過去の経験は、各回答候補またはエビデンスのフィーチャーのスコアを計算し、それを既知の結果と結合することにより、モデルの形式で取り込まれる。 *機械学習アノテーター (machine learning annotator)* と呼ばれることもある。

- **メンション (mention)**

    分野データと関連すると考えられる、ある幅のテキスト。 例えば、自動車に関するタイプ・システムでは、「airbag」、「Ford Explorer」、「child restraint system」などの用語のオカレンスが、関連するメンションとなり得る。

## N
{: #gloss_N}

- **固有表現 (named entity)**

    組織名、地名、著者名、病名など、明確に定義されたカテゴリーに分類される、ある分野の概念。

- **自然言語処理 (natural language processing)**

    人間の言語に対するコンピューターの理解能力を向上させることを目的として自然言語の処理や操作に特有の問題を研究する、人工知能および言語学の 1 分野。

## O
{: #gloss_O}

- **オントロジー (ontology)**

    関心のある領域に存在し得るオブジェクト、概念、およびその他のエンティティーと、それらの間の関係を表現するための明示的な形式の仕様。

## P
{: #gloss_P}

- **品詞 (part of speech (POS))**

    辞書の各項目には品詞 (POS) タグが割り当てられる。 例えば、「fly」という単語は動詞または名詞として識別できる。

- **パフォーマンス (performance)**

    例えば、質問への回答、関係の発見、テキストへのアノテーション付けなどでの、正確度、精度、およびリコールの観点での {{site.data.keyword.watson}} システムの計測。

- **事前アノテーション (pre-annotation)**

    人によるアノテーション付けの前に、文書のセットにアノテーションを付けるプロセス。 ルール・ベース・モデル、機械学習モデル、{{site.data.keyword.nlufull}}、または辞書を使用することによって、文書に事前にアノテーションを付けることができる。 事前アノテーションは、ヒューマン・アノテーターがグランド・トゥルース文書のセットをより迅速に準備するのを助けることができる。

- **精度 (precision)**

    関連する結果の比率を指定する計測。 精度は、ポジティブの予測値であり、正しかったポジティブ結果の数をすべてのポジティブ結果の数で除算することで決まる。 正確度は、精度およびリコールの両方を使用することによって最も適切に計測される。 [正確度 (accuracy)](/docs/services/watson-knowledge-studio/glossary.html#gloss_A) および[リコール (recall)](/docs/services/watson-knowledge-studio/glossary.html#gloss_R) も参照。

- **処理エンジン・アーカイブ (processing engine archive (PEAR))**

    Unstructured Information Management Architecture (UIMA) 分析エンジン、およびそれをカスタム分析に使用するために必要なすべてのリソースを含む、`.pear` アーカイブ・ファイル。

## R
{: #gloss_R}

- **リコール (recall)**

    すべての関連結果のうち、返された関連結果のパーセンテージを指定する計測。 リコールは、感度の指標であり、正しかったポジティブ結果の数を、返されるべきだったポジティブ結果の数で除算することで決まる。 正確度は、精度およびリコールの両方を使用することによって最も適切に計測される。 [正確度 (accuracy)](/docs/services/watson-knowledge-studio/glossary.html#gloss_A) および[精度 (precision)](/docs/services/watson-knowledge-studio/glossary.html#gloss_P) も参照。

- **関係 (relation)**

    エンティティー同士がどのように関連しているのかを反映するもので、通常は動詞。 例えば、「lives in」は個人と町の間の関係である。 関係は、同じセンテンス中の 2 つの異なるエンティティーをリンクする。

- **関係タイプ (relation type)**

    2 つのエンティティー間の単一方向の 2 項関係。 例えば、`Mary` `employedBy` {{site.data.keyword.IBM_notm}} は妥当な関係であり、{{site.data.keyword.IBM_notm}} `employedBy` `Mary` はそうではない。

- **役割 (role)**

    メンションの文脈に依存した意味を提供する属性。 例えば、「I went to {{site.data.keyword.IBM_notm}} today」という句では、{{site.data.keyword.IBM_notm}} がメンションであり、エンティティー・タイプは Organization であり、エンティティー・タイプの役割は Facility である。

- **ルール・セット (rule set)**

    テキストにアノテーションを付けるためのパターンを定義するルールのセット。 パターンが適合する場合、一致するアノテーションに対して当該ルールのアクションが実行される。 ルールは、通常、一致する必要のある条件、オプションの数量詞、一致したテキストが満たす必要のある追加制約のリスト、および、一致が発生したときに実行されるべきアクション (新規アノテーションの作成、既存アノテーションの変更など) を指定する。

## S
{: #gloss_S}

- **サブタイプ (subtype)**

    別のタイプ （スーパータイプ) を継承または実装するタイプ。

- **表層形 (surface form)**

    単語または連語ユニットがコーパス内で検出されるときの形式。 例えば、用語「organizing」および「organized」は、見出し語「organize」の表層形の一部である。 [辞書 (dictionary)](/docs/services/watson-knowledge-studio/glossary.html#gloss_D) および[見出し語 (lemma)](/docs/services/watson-knowledge-studio/glossary.html#gloss_L) も参照。

## T
{: #gloss_T}

- **テスト・データ (testing data)**

    取り込みおよびトレーニング後にシステム・メトリックを評価するために使用できる、アノテーションが付けられた文書のセット。 [ブラインド・データ (blind data)](/docs/services/watson-knowledge-studio/glossary.html#gloss_B) および[トレーニング・データ (training data)](/docs/services/watson-knowledge-studio/glossary.html#gloss_T) も参照。

- **トレーニング (train)**

    {{site.data.keyword.watson}} インスタンスを、特定の分野でシステムが機能できるようにするコンポーネント (例: コーパスのコンテンツ、機械学習モデルを生成するトレーニング・データ、プログラマチック・アルゴリズム、またはその他のグランド・トゥルース・コンポーネント) と共にセットアップし、次に、これらのコンポーネントに正確度分析に基づいて改善および更新を加えるプロセス。

- **トレーニング・データ (training data)**

    機械学習モデルのトレーニングに使用できる、アノテーションが付けられた文書のセット。 [ブラインド・データ (blind data)](/docs/services/watson-knowledge-studio/glossary.html#gloss_B) および[テスト・データ (testing data)](/docs/services/watson-knowledge-studio/glossary.html#gloss_T) も参照。

- **トゥルー・ネガティブ (true negative)**

    実際に正しくなく、正しくないと予測された、回答またはアノテーション。

- **トゥルー・ポジティブ (true positive)**

    実際に正しく、正しいと予測された、回答またはアノテーション。

- **タイプ・システム (type system)**

    タイプ・システムは、文書中で発見される可能性のあるオブジェクトのタイプを定義する。 タイプ・システムは、あり得るすべてのエンティティー・タイプおよびエンティティー・タイプ間の関係を定義する。 1 つのタイプ・システムに、異なるタイプをいくつでも定義できる。 タイプ・システムは、分野固有であり、アプリケーション固有である。
