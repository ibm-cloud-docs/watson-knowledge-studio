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

本文档适用于 {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}。要查看 {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace 先前版本的文档，请[单击此链接 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/docs/services/knowledge-studio/language-support-arabic.html){: new_window}。
{: tip}

# 配置阿拉伯语支持
{: #wks_langsupp_ar}

请阅读以下准则以了解 {{site.data.keyword.knowledgestudioshort}} 如何处理阿拉伯语文档中的阿拉伯语字符字型和数字字型。

## 关于本任务

对于字符字型，阿拉伯语字母表没有大写字母，但字母可以根据其在文本字符串和周围字母中的位置而改变形状。不同的操作系统和代码页转换程序以不同方式处理字母字型。存储未调整字型是 Windows 系统的标准处理方式，因此 {{site.data.keyword.knowledgestudioshort}} 假设阿拉伯语文本存储时未调整字型。如果要将已调整字型的文本上传到 {{site.data.keyword.knowledgestudioshort}}，那么必须先使用标准工具（例如 International Components for Unicode (ICU) API）将文本转换成未调整字型的形式（请参阅 ArabicShaping 类：[http://icu-project.org/apiref/icu4j/com/ibm/icu/text/ArabicShaping.html ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://icu-project.org/apiref/icu4j/com/ibm/icu/text/ArabicShaping.html){: new_window}）。

> **重要信息**：在某些情况下，缺少正确的阿拉伯语字符字型可能导致内容在参考标准编辑器中错误地显示。

对于数字字型，{{site.data.keyword.knowledgestudioshort}} 将数字字型视为存储级别属性，类似于在 iOS 平台上处理阿拉伯语内容的方式。由于许多阿拉伯语内容是在像 Windows 这样的平台上创建的，而这类平台将数字字型视为显示级别属性，因此在使用 {{site.data.keyword.knowledgestudioshort}} 时，需要转换内容以使数字字型成为存储级别属性，或者使用 Firefox 浏览器。Firefox 支持在浏览器级别显式设置数字字型首选项，并对浏览器中显示的所有内容强制执行相应的显示。

## 过程

要在 Firefox 浏览器中配置数字字型，请执行以下操作：

1. 在浏览器 URL 字段中，输入 **about:config**。如果显示来自 Firefox 的警告，请单击相应操作以忽略警告并继续。有关编辑 **about:config** 属性的信息，请参阅 [http://kb.mozillazine.org/About:config_entries ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://kb.mozillazine.org/About:config_entries){: new_window}。
1. 在搜索过滤器字段中，输入 `bidi`。
1. 选择用于控制数字显示方式的 **bidi.numeral** 属性，然后按 Enter 键。
1. 根据需要更改此属性的值。例如，输入 `3`，然后单击**确定**。

    - **0**：标称数字（缺省值）
    - **1**：常规上下文数字
    - **2**：印地语上下文数字
    - **3**：阿拉伯数字
    - **4**：印地语数字

    > **重要信息**：使用 **bi.numeral** 属性时，Firefox 会完全忽略 Web 页面内容中特定数字字符的代码点。

### 相关参考

[语言支持](/docs/services/watson-knowledge-studio/language-support.html)
