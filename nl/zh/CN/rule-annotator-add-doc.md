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

本文档适用于 {{site.data.keyword.cloud}} 上的 {{site.data.keyword.knowledgestudiofull}}。要查看 {{site.data.keyword.IBM_notm}} Marketplace 上先前版本的 {{site.data.keyword.knowledgestudioshort}} 文档，请[单击此链接 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/docs/services/knowledge-studio/rule-annotator-add-doc.html){: new_window}。
{: tip}

# 添加用于定义规则的文档
{: #wks_rule_anno_add}

使用说明您要定义的规则类型的语言模式来添加文档。
{: shortdesc}

添加用于定义规则的文档与添加进行注释的文档会保持分开。用于定义规则的文档的唯一用途是用来挖掘模式的示例。这类文档不会用于培训，也从不供下载。

## 可以向规则编辑器添加文档的方式

- **编写 UTF-8 格式的文本文档**

    可以将用于说明模式的文本添加到规则编辑器中。为文档指定的名称长度不能超过 256 个字符。

- **上传 CSV 文件**

    上传包含文档文本的 CSV 格式的文件。

- **复制已导入用于注释的文档**

    如果文档集内已导入用于注释用途的某个文档包含要作为规则捕获的模式的示例，那么可以将该文档复制到规则编辑器。对该文档所做的任何更改都不会影响正在用于注释的文档的原始版本。有关上传文档的信息，请参阅[向工作空间添加文档](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projadd)。

对于复制或上传的文档，请选择包含不同模式的文档，以帮助识别文档中的实体类型。
