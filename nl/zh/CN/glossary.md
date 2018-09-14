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

本文档适用于 {{site.data.keyword.cloud}} 上的 {{site.data.keyword.knowledgestudiofull}}。要查看 {{site.data.keyword.IBM_notm}} Marketplace 上先前版本的 {{site.data.keyword.knowledgestudioshort}} 文档，请[单击此链接 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/docs/services/knowledge-studio/glossary.html){: new_window}。
{: tip}

# 词汇表
{: #glossary}

本词汇表包含 {{site.data.keyword.knowledgestudioshort}} 的术语和定义。
{: shortdesc}

在本词汇表中使用了以下交叉引用：

- *请参阅*用于将您从某个术语引向某个首选同义词，或者从首字母缩略词或缩写引向已定义的完整形式。
- *另请参阅*指引您查看相关术语或对照术语。

 [B](/docs/services/watson-knowledge-studio/glossary.html#gloss_B) [C](/docs/services/watson-knowledge-studio/glossary.html#gloss_C) [F](/docs/services/watson-knowledge-studio/glossary.html#gloss_F) [G](/docs/services/watson-knowledge-studio/glossary.html#gloss_G) [H](/docs/services/watson-knowledge-studio/glossary.html#gloss_H) [J](/docs/services/watson-knowledge-studio/glossary.html#gloss_J) [K](/docs/services/watson-knowledge-studio/glossary.html#gloss_K) [L](/docs/services/watson-knowledge-studio/glossary.html#gloss_L) [M](/docs/services/watson-knowledge-studio/glossary.html#gloss_M) [P](/docs/services/watson-knowledge-studio/glossary.html#gloss_P) [R](/docs/services/watson-knowledge-studio/glossary.html#gloss_R) [S](/docs/services/watson-knowledge-studio/glossary.html#gloss_S) [T](/docs/services/watson-knowledge-studio/glossary.html#gloss_T)
 [W](/docs/services/watson-knowledge-studio/glossary.html#gloss_W)
 [X](/docs/services/watson-knowledge-studio/glossary.html#gloss_X)
 [Y](/docs/services/watson-knowledge-studio/glossary.html#gloss_Y)
 [Z](/docs/services/watson-knowledge-studio/glossary.html#gloss_Z)
 [F](/docs/services/watson-knowledge-studio/glossary.html#gloss_f1)

## [B]
{: #gloss_B}

- **本体 (ontology)**

    某个相关领域中可能存在的对象、概念和其他实体及其之间关系的一种明确正式的表示。

- **表面形式 (surface form)**

    在语料库中找到的词或多词单元的形式。例如，词元“organize”的一些表面形式是术语“organizing”和“organized”。另请参阅[字典 (dictionary)](/docs/services/watson-knowledge-studio/glossary.html#gloss_Z) 和[词元 (lemma)](/docs/services/watson-knowledge-studio/glossary.html#gloss_C)。


## [C]
{: #gloss_C}

- **裁定 (adjudication)**

    一个迭代式过程，通过比较不同的人工注释者添加到同一文档的注释来解决注释冲突。

- **参考标准 (ground truth)**

    已检查数据的集合，由人工注释者添加的注释组成，用于调整机器学习模型以适应特定领域。参考标准用于培训机器学习模型，度量模型性能（精确和召回率），并计算空余空间以决定开发工作的重点应该放在哪里才能提高性能。参考标准的准确性至关重要，因为参考标准中的不准确之处与使用该参考标准的组件的不准确之处相关。

- **测试数据 (testing data)**

    一组已注释的文档，可用于在获取数据和培训后对系统度量值求值。另请参阅[盲区数据 (blind data)](/docs/services/watson-knowledge-studio/glossary.html#gloss_M) 和[培训数据 (training data)](/docs/services/watson-knowledge-studio/glossary.html#gloss_P)。

- **处理引擎归档 (processing engine archive, PEAR)**

    一个 `.pear` 归档文件，包含非结构化信息管理体系结构 (UIMA) 分析引擎以及将其用于定制分析所需的所有资源。

- **词性 (part of speech, POS)**

    在字典中，会对单独的词项指定词性 (POS) 标记。例如，单词“fly”可标识为动词或名词。

- **词语索引 (concordance)**

    这种方法用于确保在整个文档内以及在各个注释集之间使用相同实体类型对同一提及项进行注释。词语索引有助于确保多次出现的提及项的一致性，而无需人工注释者手动标注每次出现的提及项。

- **词元 (lemma)**

    标准化形式或规范形式的词。通常，词元是非派生和未变形形式的名词或动词。例如，术语“organizing”和“organized”的词元是“organize”。另请参阅[字典 (dictionary)](/docs/services/watson-knowledge-studio/glossary.html#gloss_D) 和[表面形式 (surface form)](/docs/services/watson-knowledge-studio/glossary.html#gloss_S)。

## [F]
{: #gloss_F}

- **分析引擎 (analysis engine)**

    一个程序，用于分析工件（如文档），推断有关工件的信息，以及实现 UIMA 分析引擎接口规范。分析引擎是通过称为注释器的构建块来构造的。分析引擎可以包含单个注释器（称为基本分析引擎）或多个注释器（称为聚集分析引擎）。

## [G]
{: #gloss_G}

- **功能 (feature)**

    类型的数据成员或属性。

- **关系 (relation)**

    通常是反映实体如何彼此相关的动词。例如，“lives in”是人员和城镇之间的关系。关系用于链接同一语句中的两个不同实体。

- **关系类型 (relation type)**

    两个实体之间的二元单向关系。例如，`Mary` `employedBy` {{site.data.keyword.IBM_notm}} 是有效关系；{{site.data.keyword.IBM_notm}} `employedBy` `Mary` 不是有效关系。

- **管理 (curate)**

    选择、收集、保留和维护与特定主题相关的内容。管理可建立和维护数据并使数据增值；它将数据转换为可信的信息和知识。

- **规则集 (rule set)**

    一组规则，定义用于注释文本的模式。如果某个模式适用，那么会对匹配的注释执行规则的操作。规则通常指定必须匹配的条件、可选量词、匹配文本必须满足的其他约束的列表以及发生匹配时要执行的操作（例如，创建新注释或修改现有注释）。

## [H]
{: #gloss_H}

- **混淆矩阵 (confusion matrix)**

    提供已注释文档集的详细数字细目的表。此表用于比较机器学习模型添加的注释与参考标准中的注释。此表报告[假正 (false positive)](/docs/services/watson-knowledge-studio/glossary.html#gloss_J)、[假负 (false negative)](/docs/services/watson-knowledge-studio/glossary.html#gloss_J)、[真正 (true positive)](/docs/services/watson-knowledge-studio/glossary.html#gloss_Z) 和[真负 (true negative)](/docs/services/watson-knowledge-studio/glossary.html#gloss_Z) 的数量。

## [J]
{: #gloss_J}

- **机器学习 (machine learning)**

    一种数据分析方法，用于以迭代方式从过去的数据中进行学习，并在向新数据公开时进行独立调整。作为机器学习核心的数学模型是根据参考标准输入构建的。通过培训和优化示例输入数据，模型可以在分析新数据时交付准确、可重复的结果。

- **机器学习模型 (machine learning model)**

    一个组件，用于根据基于参考标准的统计模型来识别实体和实体关系。该模型应用过去的经验（例如，培训数据）基于数据特征来确定或预测未来体验的正确结果。通过计算每个候选答案或证据的特征得分，然后结合已知的结果，采用模型形式来捕获这些过去的经验。有时称为*机器学习注释器 (machine learning annotator)*。

- **机器学习注释器 (machine learning annotator)**

    请参阅[机器学习模型 (machine learning model)](/docs/services/watson-knowledge-studio/glossary.html#gloss_J)。

- **假负 (false negative)**

    正确但预测为不正确的答案或注释。

- **假正 (false positive)**

    不正确但预测为正确的答案或注释。

- **角色 (role)**

    一个属性，用于提供提及项的上下文相关含义。例如，在短语“I went to {{site.data.keyword.IBM_notm}} today”中，{{site.data.keyword.IBM_notm}} 是提及项，Organization 是实体类型，Facility 是实体类型的角色。

- **精度 (precision)**

    一种指定相关结果比例的度量。精度是正预测值，确定方式是正确的正结果数除以所有正结果数。准确性的最佳度量方式是使用精度和召回率。另请参阅[准确性 (accuracy)](/docs/services/watson-knowledge-studio/glossary.html#gloss_Z) 和[召回率 (recall)](/docs/services/watson-knowledge-studio/glossary.html#gloss_Z)。

## [K]
{: #gloss_K}

- **空余空间分析 (headroom analysis)**

    这是通过解决在执行准确性分析时识别到的某类问题来确定准确性、精度或召回率改进程度的过程。

## [L]
{: #gloss_L}

- **类型系统 (type syste)**

    类型系统定义可以在文档中发现的对象的类型。类型系统定义所有可能的实体类型以及实体类型之间的关系。您可以在类型系统中定义任意数目的不同类型。类型系统通常特定于领域，并且特定于应用程序。

## [M]
{: #gloss_M}

- **盲区数据 (blind data)**

    使用参考标准注释的一组文档，例如问答对、语义注释和段落判断。盲区数据永远不会由开发者发布，也无法供其查看；盲区数据用于定期测试系统以评估无法查看的数据的性能。针对盲区数据进行测试可避免因对已知问题集或注释进行过度拟合而污染准确性。报告的结果应该仅来自对盲区数据运行的测试。另请参阅[测试数据 (testing data)](/docs/services/watson-knowledge-studio/glossary.html#gloss_C) 和[培训数据 (training data)](/docs/services/watson-knowledge-studio/glossary.html#gloss_P)。

- **命名实体 (named entity)**

    领域中的一个概念，属于定义明确的类别，例如组织、位置、作者或疾病的名称。

## [P]
{: #gloss_P}

- **培训 (train)**

    这是使用支持系统在特定领域中运行的组件（例如：语料库内容、用于生成机器学习模型的培训数据、编程算法或其他参考标准组件）设置 {{site.data.keyword.watson}} 实例，然后根据准确性分析对这些组件进行改进和更新的过程。

- **培训数据 (training data)**

    一组已注释的文档，可用于培训机器学习模型。另请参阅[盲区数据 (blind data)](/docs/services/watson-knowledge-studio/glossary.html#gloss_B) 和[测试数据 (testing data)](/docs/services/watson-knowledge-studio/glossary.html#gloss_T)。

## [R]
{: #gloss_R}

- **人工注释者 (human annotator)**

    一个主题专家，通过识别提及项、实体类型关系和提及项指代来复查、修改和扩充预注释的结果。人工注释者通过在上下文中检查文本，帮助确定参考标准并提高机器学习模型的准确性。

## [S]
{: #gloss_S}

- **实体 (entity)**

    1. 通过实体类型进行注释的提及项。
    1. 存储其相关信息的人员、对象或概念。
    1. 保留的有关现实世界对象（如人员、位置或银行账户）的一组详细信息。实体是一种项。

- **实体类型 (entity type)**

    提及项表示的实体类型，而不考虑上下文。例如，提及项 {{site.data.keyword.IBM_notm}} 可通过实体类型 ORGANIZATION 进行注释。

    在实体/关系模型中，实体类型是要建模的对象或提及项引用的对象，例如人员或位置的名称。不同的实体类型具有不同的属性集（例如，“surname”或“home town”），并且通过关系（如“lives in”）进行连接。实体类型独立存在，且可唯一标识。

- **属性 (attribute)**

    用于描述实体的实体特征或特性；例如，员工的电话号码就是员工属性之一。

## [T]
{: #gloss_T}

- **提及项 (mention)**

    在领域数据中视为相关的某一范围的文本。例如，在有关汽车的类型系统中，出现的“airbag”、“Ford Explorer”和“child restraint system”等术语可能是相关的提及项。

## [W]
{: #gloss_W}

- **文档集 (document set)**

    文档的集合。一起导入的文档会成为文档集。出于培训用途而分组在一起的已注释文档（测试、培训和盲区）也会生成为文档集。

## [X]
{: #gloss_X}

- **性能 (performance)**

    这是 {{site.data.keyword.watson}} 系统的准确性、精度和召回率方面的度量，例如在回答问题、发现关系或注释文本时。

## [Y]
{: #gloss_Y}

- **语料库 (corpus)**

    已添加到工作空间并用于培训机器学习模型的源文档的集合。

- **预注释 (pre-annotation)**

    这是在人工注释之前对一组文档进行注释的过程。可以使用基于规则的模型、机器学习模型、{{site.data.keyword.nlufull}} 或字典对文档进行预注释。预注释可以帮助人工注释者更快地准备一组参考标准文档。

## [Z]
{: #gloss_Z}

- **召回率 (recall)**

    一种度量，用于指定返回的相关结果在所有可用相关结果中所占百分比。召回率是敏感度度量，确定方式是正确的正结果数除以应该返回的正结果数。准确性的最佳度量方式是使用精度和召回率。另请参阅[准确性 (accuracy)](/docs/services/watson-knowledge-studio/glossary.html#gloss_Z) 和[精度 (precision)](/docs/services/watson-knowledge-studio/glossary.html#gloss_J)。

- **真负 (true negative)**

    实际不正确且预测为不正确的答案或注释。

- **真正 (true positive)**

    实际正确且预测为正确的答案或注释。

- **知识图 (knowledge graph)**

    一种模型，整合了有类型实体、其关系、其属性和分层分类法来表示给定领域的概念组织。将来自结构化和非结构化数据源的输入装入到知识图存储库后，用户和应用程序可以访问知识图来浏览特定领域的关键知识元素、探索交互情况并发现其他关系。

- **指代 (coreference)**

    两个词或短语之间的关系，这两个词或短语指的是同一个人或事物，并且其中一个是另一个的语言先行词。例如，短语“She taught herself”中的两个代词之间存在指代，但在短语“She taught her”中不存在指代。指代用于链接同一文本中的两个等效实体。

- **指代链 (coreference chain)**

    注释为指代的实体的列表。将提及项注释为指代时，系统将创建指代链。通过该链，您可查看上下文中的所有提及项，并验证所有出现的提及项是否都属于同一实体类型。

- **注释 (annotation)**

    有关特定文本范围的信息。例如，注释可能指示某一范围的文本表示公司名称。

- **注释过程管理者 (annotation process manager)**

    一个角色，负责管理工作空间内的完整注释生命周期活动。添加到工作空间的项目经理通常会执行注释过程管理者的活动。

- **注释集 (annotation set)**

    在人工注释中，是指从语料库中抽取的文档集合，这些文档允许工作负载由多个人工注释者共享。在基于机器的注释中，是指可用作盲区数据、培训数据或测试数据的文档集合。

- **注释器/注释者 (annotator)**

    请参阅[人工注释者 (human annotator)](/docs/services/watson-knowledge-studio/glossary.html#gloss_R) 和[机器学习注释器 (machine learning annotator)](/docs/services/watson-knowledge-studio/glossary.html#gloss_J)。

- **注释者间一致性 (inter-annotator agreement)**

    这是对两个或更多文档集内某个文档进行注释的类似程度的度量。

- **准确性 (accuracy)**

    这是机器学习模型所生成的注释的正确性度量。另请参阅[精度 (precision)](/docs/services/watson-knowledge-studio/glossary.html#gloss_J) 和[召回率 (recall)](/docs/services/watson-knowledge-studio/glossary.html#gloss_Z)。

- **准确性分析 (accuracy analysis)**

    分析机器学习模型分数，以确定是否需要进行更改以提高准确性。

- **子类型 (subtype)**

    一种类型，用于扩展或实现另一种类型；超类型。

- **自然语言处理 (natural language processing)**

    人工智能和语言学的一个领域，研究自然语言的处理和操作过程中固有的问题，旨在提高计算机理解人类语言的能力。

- **字典 (dictionary)**

    可用于对文档进行预注释的词的集合。将为文档文本中与字典中的术语相匹配的每个词创建一个新注释。可以使用一个或多个独立字典（通常是特定于领域的字典，例如药品字典和财富管理字典）来配置机器学习模型。另请参阅[词元 (lemma)](/docs/services/watson-knowledge-studio/glossary.html#gloss_C) 和[表面形式 (surface form)](/docs/services/watson-knowledge-studio/glossary.html#gloss_B)。

- **字典预注释器 (dictionary pre-annotator)**

    一个组件，用于标识文本中与一组特定词匹配的提及项。字典预注释器使用特定于领域的术语来对文本进行预注释，可以使人工注释者能够更快地准备好一组参考标准文档。


## F
{: #gloss_f1}

- **F1 分数 (F1 score)**

    一种测试准确性的度量，同时考虑精度和召回率来计算分数。F1 分数可以解释为精度和召回率值的加权平均值。F1 分数的最佳值为 1，最差值为 0。

- **Fleiss Kappa 分数 (Fleiss Kappa score)**

    这是多个人工注释者对重叠文档应用同一注释的一致程度的度量。Fleiss Kappa 分数的最佳值为 1，最差值为 0。


