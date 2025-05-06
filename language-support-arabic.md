---

copyright:
  years: 2015, 2020
lastupdated: "2020-08-04"

subcollection: watson-knowledge-studio

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:deprecated: .deprecated}
{:important: .important}
{:note: .note}
{:tip: .tip}
{:preview: .preview}
{:beta: .beta}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}

This documentation is for {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. To see the documentation for the previous version of {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [click this link](/docs/knowledge-studio?topic=knowledge-studio-wks_langsupp_ar).
{: tip}

# Configuring support for Arabic
{: #wks_langsupp_ar}

Read these guidelines to understand how {{site.data.keyword.knowledgestudioshort}} handles Arabic character shaping and numeric shaping in Arabic documents.

## About this task
{: #lsa-att}

With respect to character shaping, the Arabic alphabet does not have capital letters, but letters can change shape depending on their position in the text string and the surrounding letters. Different operating systems and code page conversion programs handle letter shaping in different ways. Unshaped storage is a standard for Windows systems, and {{site.data.keyword.knowledgestudioshort}} presumes that Arabic text is stored unshaped. If you want to upload shaped text into {{site.data.keyword.knowledgestudioshort}}, you must first convert the text to unshaped form by using standard tools, such as the International Components for Unicode (ICU) API (see the ArabicShaping Class at [http://icu-project.org/apiref/icu4j/com/ibm/icu/text/ArabicShaping.html](http://icu-project.org/apiref/icu4j/com/ibm/icu/text/ArabicShaping.html){: external}).

In some cases, lack of proper Arabic character shaping might cause content to be displayed incorrectly in the ground truth editor.
{: important}

With respect to numeric shaping, {{site.data.keyword.knowledgestudioshort}} treats numeric shaping as a storage-level property, similar to how Arabic content is handled on the iOS platform. Because a lot of Arabic content is created on platforms like Windows, which treat numeric shaping as a display-level property, you need to either convert content to make numeric shaping a storage-level property or use a Firefox browser when you use {{site.data.keyword.knowledgestudioshort}}. Firefox supports the ability to set numeric shaping preferences explicitly at the browser level and enforce the appropriate display for all content shown in the browser.

## Procedure
{: #lsa-pr}

To configure numeric shaping in the Firefox browser:

1. In the browser URL field, enter **about:config**. If you are shown a warning from Firefox, click the action to disregard the warning and continue. For information about editing **about:config** properties, see [http://kb.mozillazine.org/About:config_entries](http://kb.mozillazine.org/About:config_entries){: external}.
1. Type `bidi` in the search filter field.
1. Select the **bidi.numeral** property, which controls how numerals are displayed, and press Enter.
1. Change the value of this property as required. For example, enter `3` and then click **OK**.

    - **0**: Nominal numerals (the default value)
    - **1**: Regular context numerals
    - **2**: Hindi context numerals
    - **3**: Arabic numerals
    - **4**: Hindi numerals

    When the **bidi.numeral** property is used, Firefox completely ignores the code point of specific digit characters in the content of a web page.
    {: important}o

### Related reference
{: #lsa-rr}

[Language support](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-language-support)
