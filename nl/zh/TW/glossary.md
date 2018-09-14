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

此文件適用於 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}。若要查看舊版 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 的文件，[請按一下此鏈結 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/docs/services/knowledge-studio/glossary.html){: new_window}。
{: tip}

# 名詞解釋
{: #glossary}

本名詞解釋包括 {{site.data.keyword.knowledgestudioshort}} 的詞彙及定義。
{: shortdesc}

本名詞解釋使用下列交互參照：

- *請參閱* 可讓您從詞彙參照偏好的同義字，或從字首語或縮寫參照已定義的完整形式。
- *另請參閱* 可讓您參照相關或對照的詞彙。

[三劃](/docs/services/watson-knowledge-studio/glossary.html#gloss_3) [四劃](/docs/services/watson-knowledge-studio/glossary.html#gloss_4) [五劃](/docs/services/watson-knowledge-studio/glossary.html#gloss_5) [六劃](/docs/services/watson-knowledge-studio/glossary.html#gloss_6) [七劃](/docs/services/watson-knowledge-studio/glossary.html#gloss_7) [八劃](/docs/services/watson-knowledge-studio/glossary.html#gloss_8) [九劃](/docs/services/watson-knowledge-studio/glossary.html#gloss_9) [十劃](/docs/services/watson-knowledge-studio/glossary.html#gloss_10) 
[十一劃](/docs/services/watson-knowledge-studio/glossary.html#gloss_11) [十二劃](/docs/services/watson-knowledge-studio/glossary.html#gloss_12) [十三劃](/docs/services/watson-knowledge-studio/glossary.html#gloss_13) [十四劃](/docs/services/watson-knowledge-studio/glossary.html#gloss_14) [十六劃](/docs/services/watson-knowledge-studio/glossary.html#gloss_16) [十九劃](/docs/services/watson-knowledge-studio/glossary.html#gloss_19) [二十一劃](/docs/services/watson-knowledge-studio/glossary.html#gloss_21) [F](/docs/services/watson-knowledge-studio/glossary.html#gloss_F)

## 三劃
{: #gloss_3}

- **子類型 (subtype)**

    這是延伸或實作另一種類型的類型；超類型。

## 四劃
{: #gloss_4}

- **互相參照 (coreference)**

    兩個單字或詞組之間的關係，兩者都參照相同的人員或事物，而其中一個作為另一個的語言先行詞。例如，詞組 "She taught herself" 中的兩個代名詞之間有互相參照，但是詞組 "She taught her" 中則未互相參照。互相參照會鏈結相同文字中兩個相等的實體。
    
- **互相參照鏈結 (coreference chain)**

    註釋為互相參照的實體清單。當您將提及項目註釋為互相參照時，系統會建立一個互相參照鏈結。該鏈結提供一種方式，讓您檢視上下文中的所有提及項目，並驗證所有出現項目都屬於同一個實體類型。
    
- **分析引擎 (analysis engine)**

    該程式用來分析構件（例如文件）及推斷其相關資訊，並實作「UIMA 分析引擎」介面規格。分析引擎是從稱為註釋程式的構成要素所建構的。分析引擎可以包含單一註釋程式（稱為基本分析引擎）或多個註釋程式（稱為聚集分析引擎）。
    
- **文件集 (document set)**

    文件集合。一起匯入的文件會成為一個文件集。為訓練目的（測試、訓練、盲目）而分組在一起的已註釋文件會產生為文件集。

## 五劃
{: #gloss_5}

- **本體 (ontology)**

    明確且正式的表示法規格，用來表示物件、概念以及某些感興趣區域與其間關係中可能存在的其他實體。

- **正確性 (accuracy)**

    測量機器學習模型所產生之註釋的正確性。另請參閱[查準率 (precision)](/docs/services/watson-knowledge-studio/glossary.html#gloss_9) 及[查全率 (recall)](/docs/services/watson-knowledge-studio/glossary.html#gloss_9)。

- **正確性分析 (accuracy analysis)**

    分析機器學習模型分數，以判定是否需要變更以提高正確性。

## 六劃
{: #gloss_6}

- **字典 (dictionary)**

    可用來預先註釋文件的單字集合。系統會為文件文字中每一個符合字典內詞彙的單字建立新的註釋。機器學習模型可使用一個以上的獨立字典來進行配置，這些字典一般都屬於特定領域，例如，化學藥品字典以及財富管理字典。另請參閱[詞目 (lemma)](/docs/services/watson-knowledge-studio/glossary.html#gloss_12) 及[表面形式 (surface form)](/docs/services/watson-knowledge-studio/glossary.html#gloss_8)

- **字典預先註釋程式 (dictionary pre-annotator)**

    此元件用來識別文字中符合特定字組的提及項目。使用特定領域的術語來預先註釋文字，讓字典預先註釋程式可加快註釋人員準備一組基準文件的速度。

- **自然語言處理 (natural language processing)**

    這是一個人工智慧及語言化的欄位，用來研究自然語言在處理和操作上所固有的問題，並要求增加電腦的能力以瞭解人類語言。

## 七劃
{: #gloss_7}

- **角色 (role)**

    該屬性提供提及項目的上下文意義。例如，在詞組 "I went to {{site.data.keyword.IBM_notm}} today" 中，{{site.data.keyword.IBM_notm}} 是提及項目，「組織」是實體類型，而「機構」是實體類型的角色。

## 八劃
{: #gloss_8}

- **具名實體 (named entity)**

    這是指領域中屬於明確定義種類的概念，例如，組織、位置、作者或疾病的名稱。

- **盲目資料 (blind data)**

    以基準註釋的一組文件，例如問題與答案配對、語意註釋及段落判斷。開發人員絕不會發行或看見盲目資料，該資料用來定期測試系統，以評估所看不到資料的效能。對盲目資料進行測試，可避免因為過度配適到已知問題集或註釋而降低正確性。所報告的結果應該只來自在盲目資料上執行的測試。另請參閱[測試資料 (testing data)](/docs/services/watson-knowledge-studio/glossary.html#gloss_12) 及[訓練資料 (training data)](/docs/services/watson-knowledge-studio/glossary.html#gloss_10)。

- **知識圖 (knowledge graph)**

    此模型合併類型化實體、其關係、內容及階層式分類架構，用來代表給定領域的概念組織。以來自結構化及非結構化資料來源的輸入載入知識圖儲存庫之後，使用者及應用程式可以存取知識圖，以探索特定領域的重要知識元素、探索互動，以及發現其他關係。

- **空餘空間分析 (headroom analysis)**

    此程序藉由解決在執行正確性分析時所識別到的一些問題類別，來判定可以預期的正確性、查準率或查全率的改善空間有多大。

- **表面形式 (surface form)**

    單字或多字單元在語料庫中發現時的形式。例如，詞目 'organize' 的一些表面形式為詞彙 'organizing' 及 'organized'。另請參閱[字典 (dictionary)](/docs/services/watson-knowledge-studio/glossary.html#gloss_6) 及[詞目 (lemma)](/docs/services/watson-knowledge-studio/glossary.html#gloss_12)。

## 九劃
{: #gloss_9}

- **查全率 (recall)**

    此測量指定傳回的相關結果數佔所有可用相關結果數的百分比。查全率是一種靈敏度測量，是由正確的正數結果數目除以應該傳回的正數結果數目所決定的。同時使用查準率及查全率，是測量正確性的最佳方式。另請參閱[精準度 (accuracy)](/docs/services/watson-knowledge-studio/glossary.html#gloss_A) 及[查準率 (precision)](/docs/services/watson-knowledge-studio

- **查準率 (precision)**

    此測量指定相關結果的比例。查準率是一個正數預測值，是由正確的正數結果數目除以所有正數結果數目所決定的。同時使用查準率及查全率，是測量正確性的最佳方式。另請參閱[正確性 (accuracy)](/docs/services/watson-knowledge-studio/glossary.html#gloss_5) 及[查全率 (recall)](/docs/services/watson-knowledge-studio/glossary.html#gloss_9)。

## 十劃
{: #gloss_10}

- **效能 (performance)**

    在回答問題、探索關係或註釋文字時（舉例說明），測量 {{site.data.keyword.watson}} 系統的正確性、查準率及查全率。

- **特性 (feature)**

    類型的資料成員或屬性。

- **真否定 (true negative)**

    實際上不正確的答案或註釋，且預測為不正確。

- **真肯定 (true positive)**

    實際上正確的答案或註釋，且預測為正確。

- **訓練 (train)**

    這個程序會使用可讓系統在特定領域中運作的元件（例如：語料庫內容、產生機器學習模型的訓練資料、程式化演算法或其他基準元件）來設定 {{site.data.keyword.watson}} 實例，然後根據正確性分析來改善及更新這些元件。

- **訓練資料 (training data)**

    一組已註釋的文件，可用來訓練機器學習模型。另請參閱[盲目資料 (blind data)](/docs/services/watson-knowledge-studio/glossary.html#gloss_8) 及[測試資料 (testing data)](/docs/services/watson-knowledge-studio/glossary.html#gloss_12)。

## 十一劃
{: #gloss_11}

- **基準 (ground truth)**

    用來讓機器學習模型適應特定領域的一組已審查資料（包含註釋人員所新增的註釋）。基準用來訓練機器學習模型、測量模型效能（查準率及查全率）以及計算空餘空間，以決定開發工作的焦點要放在哪裡才能提高效能。基準的正確性很重要，因為基準不正確會造成使用該基準的元件也不正確。

- **混淆矩陣 (confusion matrix)**

    提供已註釋文件集之詳細數字分析的表格。此表格用來比較機器學習模型所新增之註釋與基準中的註釋。此表格會報告[誤肯定 (false positives)](/docs/services/watson-knowledge-studio/glossary.html#gloss_14)、[誤否定 (false negatives)](/docs/services/watson-knowledge-studio/glossary.html#gloss_14)。

- **處理引擎保存檔 (processing engine archive, PEAR)**

    此為 `.pear` 保存檔，包括 Unstructured Information Management Architecture (UIMA) 分析引擎，以及使用該引擎來進行自訂分析時所需的所有資源。

- **規則集 (rule set)**

    一組規則，定義用來註釋文字的型樣。如果套用型樣，則會對相符的註釋執行規則的動作。規則一般會指定必須符合的條件、選用限量元、符合文字必須履行的其他限制清單，以及發生相符時要採取的動作，例如，建立新註釋或修改現有註釋。

## 十二劃
{: #gloss_12}

- **提及項目 (mention)**

    您在領域資料中視為相關的一段文字。例如，在關於汽車的類型系統中，出現的詞彙諸如「安全氣囊」、Ford Explorer 及「兒童防制系統」可能都是相關的提及項目。

- **測試資料 (testing data)**

    一組已註釋的文件，可用來在汲取及訓練之後評估系統度量。另請參閱[盲目資料 (blind data)](/docs/services/watson-knowledge-studio/glossary.html#gloss_8) 及[訓練資料 (training data)](/docs/services/watson-knowledge-studio/glossary.html#gloss_10)。

- **策劃 (curate)**

    選取、收集、保留及維護與特定主題相關的內容。策劃會建立資料、維護資料並將值新增至資料；它會將資料轉換成受信任的資訊與知識。

- **裁定 (adjudication)**

    藉由比較不同註釋人員新增至相同文件的註釋，來解決註釋衝突的反覆運算程序。

- **註釋 (annotation)**

    某段文字的相關資訊。例如，註釋可能指出某段文字代表公司名稱。

- **註釋人員 (human annotator)**

    主題專家，藉由識別提及項目、實體類型關係及提及項目互相參照，來檢閱、修改及擴增預先註釋的結果。藉由檢查上下文中的文字，註釋人員可協助判斷基準，並提高機器學習模型的正確性。

- **註釋人員內部協議 (inter-annotator agreement)**

    測量某文件在兩個以上文件集中的註釋相似度。

- **註釋程式 (annotator)**

    請參閱[註釋人員 (human annotator)](/docs/services/watson-knowledge-studio/glossary.html#gloss_12) 及[機器學習註釋程式 (machine learning annotator)](/docs/services/watson-knowledge-studio/glossary.html#gloss_16)。

- **註釋程序管理員 (annotation process manager)**

    該角色負責管理工作區內的完整註釋生命週期活動。新增至工作區的專案經理通常會執行註釋程序管理員的活動。

- **註釋集 (annotation set)**

    在人工註釋中，這是從語料庫（容許多位註釋人員共用工作負載）中擷取的文件集合。在機器型註釋中，這是可作為盲目資料、訓練資料或測試資料的文件集合。

- **詞目 (lemma)**

    單字的正規化或標準形式。一般而言，詞目是名詞或動詞的未衍生及未變形形式。例如，詞彙 'organizing' 及 'organized' 的詞目為 'organize'。另請參閱[字典 (dictionary)](/docs/services/watson-knowledge-studio/glossary.html#gloss_6) 及[表面形式 (surface form)](/docs/services/watson-knowledge-studio/gloss_8)。

- **詞性 (part of speech, POS)**

    在字典中，會指派詞性 (POS) 標籤給個別的詞彙項目。例如，「快速移動」這個單字可識別為動詞或名詞。

- **詞語索引 (concordance)**

    提供一種方式來確保相同的提及項目在整個文件中以及各註釋集間都註釋相同的實體類型。「詞語索引」可協助確保多次出現提及項目的一致性，而不需要註釋人員在每一次出現時手動加上標籤。

## 十三劃
{: #gloss_13}

- **預先註釋 (pre-annotation)**

    在人工註釋之前對一組文件進行註釋的程序。可以使用規則型模型、機器學習模型、{{site.data.keyword.nlufull}} 或字典來預先註釋文件。預先註釋可協助註釋人員更快地準備一組基準文件。

- **實體 (entity)**

    1. 實體類型所註釋的提及項目。

    1. 儲存其相關資訊的人員、物件或概念。

    1. 這是所保留的有關現實物件（如人員、位置或銀行帳戶）的一組詳細資料。實體是一種項目。

## 十四劃
{: #gloss_14}

- **實體類型 (entity type)**

    提及項目在不考慮上下文的情況下所代表的實體類型。例如，實體類型 ORGANIZATION 可能會註釋 {{site.data.keyword.IBM_notm}} 這個提及項目。

    在實體關係模型中，實體類型是要建模的事物或提及項目所參照的事物，例如人員或工作區的名稱。不同的實體類型有不同的屬性集，例如「暱稱」或「故鄉」，並透過「住在」之類的關係來連接。實體類型單獨存在，且可以唯一地識別。

- **語料庫 (corpus)**

    已新增至工作區並用來訓練機器學習模型的來源文件集合。

- **誤否定 (false negative)**

    正確的答案或註釋，但預測為不正確。

- **誤肯定 (false positive)**

    不正確的答案或註釋，但預測為正確。

## 十六劃
{: #gloss_16}

- **機器學習 (machine learning)**

    資料分析方法，可從過往資料進行反覆運算學習，並在公開給新資料時獨立適應。機器學習核心的數學模型是從基準輸入進行建置。透過訓練及修正範例輸入資料，模型可以在分析新資料時提供準確且可重複的結果。

- **機器學習註釋程式 (machine learning annotator)**

    請參閱[機器學習模型 (machine learning model)](/docs/services/watson-knowledge-studio/glossary.html#gloss_16)。

- **機器學習模型 (machine learning model)**

    此元件根據以基準為基礎的統計模型，來識別實體及實體關係。此模型會套用過去的經驗（例如，訓練資料），根據資料的性質來判斷或預測未來體驗的正確結果。這些過去的經驗是透過計算每一個候選答案或證明的特性分數，並結合已知的結果，以模型的形式進行擷取。有時稱為*機器學習註釋程式*。

## 十九劃
{: #gloss_19}

- **關係 (relation)**

    一般是個動詞，反映實體與另一個實體的相關程度。例如，「住在」是人員與城鎮之間的關係。關係會鏈結兩個在相同句子中的不同實體。

- **關係類型 (relation type)**

    兩個實體之間的二進位單向關係。例如，`Mary` `employedBy` {{site.data.keyword.IBM_notm}} 是有效的關係；{{site.data.keyword.IBM_notm}} `employedBy` `Mary` 則不是。

- **類型系統 (type system)**

    類型系統會定義可在文件中探索到的物件類型。類型系統會定義所有可能的實體類型以及實體類型之間的關係。您可以在類型系統中定義任何數量的不同類型。一般而言，類型系統屬於特定領域及特定應用程式。

## 二十一劃
{: #gloss_21}

- **屬性 (attribute)**

    用來說明實體的實體特徵或特質；例如，員工電話號碼即是其中一個員工屬性。

## F
{: #gloss_F}

- **F1 分數 (F1 score)**

    測量測試的正確性，同時考量查準率及查全率來計算分數。F1 分數可以解譯為查準率與查全率值的加權平均。F1 分數的最佳值為 1，最差值為 0。

- **Fleiss Kappa 分數 (Fleiss Kappa score)**

    測量在重疊的文件之間，多位註釋人員套用相同註釋的一致程度。Fleiss Kappa 分數的最佳值為 1，最差值為 0。
