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

Diese Dokumentation bezieht sich auf {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Die Dokumentation für die Vorgängerversion {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace kann über [diesen Link ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/docs/services/knowledge-studio/language-support-arabic.html){: new_window} aufgerufen werden.
{: tip}

# Unterstützung für Arabisch konfigurieren
{: #wks_langsupp_ar}

In den folgenden Informationen wird erläutert, wie Buchstaben- und Zahlenformen in Dokumenten in arabischer Sprache in {{site.data.keyword.knowledgestudioshort}} verarbeitet werden.

## Informationen zu diesem Vorgang

Das arabische Alphabet verwendet keine Großbuchstaben, aber die Form der Buchstaben ändert sich entsprechend der Position in einer Textzeichenfolge und den umgebenden Buchstaben. In unterschiedlichen Betriebssystemen und Codepagekonvertierungsprogrammen wird die Anpassung der Buchstabenform auf unterschiedliche Weise verarbeitet. In Windows-Systemen werden die Buchstaben standardmäßig ohne Formanpassung gespeichert und {{site.data.keyword.knowledgestudioshort}} setzt voraus, dass arabischer Text ohne angepasste Buchstabenformen gespeichert wird. Wenn Sie Text mit angepassten Buchstabenformen in {{site.data.keyword.knowledgestudioshort}} laden möchten, muss der Text zuerst mithilfe von Standardtools wie der ICU-API (ICU = International Components for Unicode) in ungeformte Buchstaben umgewandelt werden (siehe 'Class ArabicShaping' unter [http://icu-project.org/apiref/icu4j/com/ibm/icu/text/ArabicShaping.html ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://icu-project.org/apiref/icu4j/com/ibm/icu/text/ArabicShaping.html){: new_window}).

> **Wichtig:** In einigen Fällen kann das Fehlen der angepassten arabischen Zeichenformen dazu führen, dass Inhalte im Ground Truth-Editor nicht ordnungsgemäß dargestellt werden.

Die Anpassung der Zahlenformen (numerische Umsetzung) wird in {{site.data.keyword.knowledgestudioshort}} als Eigenschaft auf der Speicherebene verarbeitet, ähnlich wie bei der Verarbeitung arabischer Inhalte auf der iOS-Plattform. Da viele Inhalte in arabischer Sprache auf Plattformen wie Windows erstellt werden, in denen angepasste Zahlenformen als Eigenschaft auf der Anzeigeebene verarbeitet werden, müssen Sie entweder die Inhalte so umwandeln, dass die Zahlenformen als Eigenschaft auf der Speicherebene verarbeitet werden, oder Sie müssen für {{site.data.keyword.knowledgestudioshort}} einen Firefox-Browser verwenden. Firefox unterstützt das explizite Festlegen von Vorgaben für angepasste Zahlenformen auf der Browser-Ebene und erzwingt die entsprechende Darstellung aller Inhalte im Browser.

## Vorgehensweise

So konfigurieren Sie die angepasste numerische Umsetzung im Firefox-Browser:

1. Geben Sie **about:config** in das URL-Feld im Browser ein. Wenn in Firefox eine entsprechende Warnung angezeigt wird, klicken Sie auf die Aktion zum Ignorieren der Warnung und fahren Sie mit dem Vorgang fort. Informationen zum Bearbeiten der Eigenschaften für **about:config** finden Sie unter [http://kb.mozillazine.org/About:config_entries ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://kb.mozillazine.org/About:config_entries){: new_window}.
1. Geben Sie `bidi` in das Feld für den Suchfilter ein.
1. Wählen Sie die Eigenschaft **bidi.numeral** aus, die steuert, wie Zahlen angezeigt werden, und drücken Sie die Eingabetaste.
1. Ändern Sie den Wert für diese Eigenschaft nach Bedarf. Geben Sie z . B. `3` ein und klicken Sie dann auf **OK**.

    - **0**: Nominal numerals (der Standardwert)
    - **1**: Regular context numerals
    - **2**: Hindi context numerals
    - **3**: Arabic numerals
    - **4**: Hindi numerals

    > **Wichtig:** Wenn die Eigenschaft **bidi.numeral** verwendet wird, ignoriert Firefox den Codepunkt bestimmter Ziffern im Inhalt einer Webseite vollständig.

### Zugehörige Referenzinformationen

[Sprachunterstützung](/docs/services/watson-knowledge-studio/language-support.html)
