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

本文档适用于 {{site.data.keyword.cloud}} 上的 {{site.data.keyword.knowledgestudiofull}}。要查看 {{site.data.keyword.IBM_notm}} Marketplace 上先前版本的 {{site.data.keyword.knowledgestudioshort}} 文档，请[单击此链接 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/docs/services/knowledge-studio/language-support.html){: new_window}。
{: tip}

# 语言支持
{: #language-support}

{{site.data.keyword.knowledgestudiofull}} 支持使用多种语言培训模型。

支持多种语言并不意味着产品本身已翻译。{{site.data.keyword.knowledgestudioshort}} 用户界面、消息和文档仅提供英语版本。
{: shortdesc}

可以使用以下语言来培训模型：

- 英语（缺省语言）
- 阿拉伯语
- 巴西葡萄牙语
- 简体中文
- 荷兰语
- 法语
- 德语
- 意大利语
- 日语
- 韩国语
- 西班牙语

支持内容包括将使用这些语言的文档添加到工作空间、添加字典、运行预注释、使用参考标准编辑器对文档进行注释以及培训机器学习模型的能力。选择语言后，系统将应用特定于语言的模板来处理字典条目、文本记号化和语句分段。有关系统如何处理不同语言的字典的信息，请参阅[字典](/docs/services/watson-knowledge-studio/dictionaries.html#wks_dictionaries)。

> **注**：规则编辑器和基于规则的模型无法处理双向文本，因此不能用于阿拉伯语文档。

> **限制：**
>
> 由于底层机器学习技术中存在字符限制，因此类型系统中的条目不能包含空格，并且只能包含以下 ASCII 字符：
>
> - A 到 Z 和 a 到 z
> - 0 到 9
> - 下划线字符：_
>
> 以下规则也适用：
>
> - 名称中的第一个字符必须是字母字符。
> - 实体类型名称的长度不能超过 64 个字符。
> - 关系类型名称的长度不能超过 128 个字符。
>
> 因此，例如，人类注释者在参考标准编辑器中对日语文本进行注释时，可以应用的实体类型和关系类型名称将不会是日语。

### 相关任务

[配置阿拉伯语支持](/docs/services/watson-knowledge-studio/language-support-arabic.html)
