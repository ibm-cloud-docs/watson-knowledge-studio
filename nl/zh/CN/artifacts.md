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

本文档适用于 {{site.data.keyword.cloud}} 上的 {{site.data.keyword.knowledgestudiofull}}。要查看 {{site.data.keyword.IBM_notm}} Marketplace 上先前版本的 {{site.data.keyword.knowledgestudioshort}} 的文档，请[单击此链接 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/docs/services/knowledge-studio/artifacts.html){: new_window}。
{: tip}

# 工件类型
{: #artifacts}

首先，创建或上传工件以用于培训注释器。
{: shortdesc}

注释器可了解有关添加到工作空间的以下工件类型的信息：

- **类型系统**

    类型系统用于定义与您相关的实体以及实体之间的关系。请参阅[建立类型系统](/docs/services/watson-knowledge-studio/typesystem.html)。

- **字典**

    字典用于将应该由模型同等处理的词和短语分组在一起。请参阅[创建字典](/docs/services/watson-knowledge-studio/dictionaries.html)。

- **文档**

    根据您是要创建机器学习模型还是基于规则的模型，文档有不同的用途。有关更多信息，请参阅以下主题：
    - 机器学习模型文档：[添加用于注释的文档](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_t_docs_intro)
    - 基于规则的模型文档：[添加用于定义规则的文档](/docs/services/watson-knowledge-studio/rule-annotator-add-doc.html)

您可以从外部资源上传其中许多工件，包括从其他 {{site.data.keyword.knowledgestudioshort}} 工作空间下载的工件。有关从其他工作空间上传工件的信息，请参阅[从其他工作空间上传资源](/docs/services/watson-knowledge-studio/exportimport.html)。

有关工件的关键事实（例如，导入工件的大小限制和支持的文件类型）的信息，请参阅[输入、输出和限制摘要](/docs/services/watson-knowledge-studio/create-project.html#wks_formats)。

