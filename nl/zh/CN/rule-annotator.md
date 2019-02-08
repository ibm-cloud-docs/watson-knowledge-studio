---

copyright:
  years: 2015, 2018
lastupdated: "2018-03-20"

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

本文档适用于 {{site.data.keyword.cloud}} 上的 {{site.data.keyword.knowledgestudiofull}}。要查看 {{site.data.keyword.IBM_notm}} Marketplace 上先前版本的 {{site.data.keyword.knowledgestudioshort}} 的文档，请[单击此链接 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/docs/services/knowledge-studio/rule-annotator.html){: new_window}。
{: tip}

# 规则
{: #rule-annotator}

创建可以识别文档中模式的基于规则的模型。使用规则可捕获文档中发生的模式，并传达有关底层实体类型的信息。
{: shortdesc}

## 类概述

构造规则时，使用类来表示信息类型。这些类与实体类型类似。那么，在定义规则时为什么不直接使用实体类型呢？原因是在构建规则时，可以定义仅用于构建其他更复杂类的中间类。这些中间类仅用作一种工具。它们本身并没有什么用。中间类要与其他中间类配合使用，以定义更有用、更完整的类。中间类是必需的，但并不作为类型系统的一部分公开。要使基于规则的模型能够执行有用的操作（例如对具有实体提及项的文档进行预注释），必须将规则创建期间使用的复杂类映射到类型系统中的等效实体类型。

例如，您需要一个可以识别人员姓名的模型。为了培训机器学习模型来识别人员的姓名，您将使用 `PERSON` 实体类型对注释集内文档中以各种格式编写的许多不同名称进行注释，然后培训模型以识别人员姓名。要创建基于规则的模型以识别人员姓名，请定义规则来描述用于编写人员姓名的文本模式。因此，您可能会创建 `FirstName` 类和 `LastName` 类，并使用这些中间类来定义 `FullName` 类。可以定义一些条件来确定 `FullName` 类相对于常用前缀（例如 `Dr.`）和常用后缀（例如 `Jr.`）的位置。使用基于规则的模型时，`FullName` 类将映射到 `PERSON` 实体类型。

避免将中间类映射到类型系统中的实体的另一个原因是，如果使用基于规则的模型对文档进行预注释，然后将这些文档添加到参考标准中以用于培训机器学习模型，那么您并不希望在定义规则时会生成重叠实体提及项。例如，如果要将中间类 `FirstName` 和复杂类 `FullName` 映射到 `PERSON` 实体，那么出现 `John Doe, Jr.` 时会导致重叠提及项。

## 规则编辑器工具

规则编辑器提供了一些可帮助您定义规则的工具。

- 字典

    添加字典并为其分配类名。如果找到的任何词与字典中的条目相匹配，会自动使用分配的类对这些词进行注释。

- 正则表达式

    正则表达式 (regex) 是用于定义搜索模式的字符序列。包含在规则编辑器中的 regex 工具可识别遵循 `java.util.regex.Pattern` 语法的表达式。下面是一个基本示例：
    `[A-Z][a-z]*`：查找大写首字母的词。

    `[A-Z]` 与任何大写字母（A 到 Z）匹配，`[a-z]*` 与任何小写字母（a 到 z）匹配零次或更多次。星号 (*) 是用于定义重复设置（零次或更多次）的字符。

    请考虑使用基于 Web 的免费正则表达式实用程序，帮助您确定用于捕获要查找的模式的正确表达式。

    例如，文档可能具有类似于以下短语的多个引用：

    ```
    35-year-old driver
    16-year-old learner
    ```
    {: screen}

    语法 `n-year-old x` 是通常表示人员的模式。可以定义正则表达式规则来查找与 `n-year-old x` 模式相匹配的短语，然后将其注释为 `PERSON` 实体提及项。
