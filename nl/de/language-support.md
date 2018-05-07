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

Diese Dokumentation bezieht sich auf {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Die Dokumentation für die Vorgängerversion {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace kann über [diesen Link ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/docs/services/knowledge-studio/language-support.html){: new_window} aufgerufen werden.
{: tip}

# Sprachunterstützung
{: #language-support}

{{site.data.keyword.knowledgestudiofull}} unterstützt das Trainieren eines Modells in mehreren Sprachen.

Die Unterstützung für mehrere Sprachen bedeutet nicht, dass das Produkt in diese Sprachen übersetzt ist. Die Benutzerschnittstellen, die Nachrichten und die Dokumentation für {{site.data.keyword.knowledgestudioshort}} sind ausschließlich in englischer Sprache verfügbar.
{: shortdesc}

Sie können ein Modell in den folgenden Sprachen trainieren:

- Englisch (Standardsprache)
- Arabisch
- Portugiesisch (Brasilien)
- Chinesisch (vereinfacht)
- Niederländisch
- Französisch
- Deutsch
- Italienisch
- Japanisch
- Koreanisch
- Spanisch

Die Sprachunterstützung beinhaltet das Hinzufügen von Dokumenten in diesen Sprachen zu einem Arbeitsbereich, das Hinzufügen von Wörterverzeichnissen, das Vorannotieren, das Annotieren von Dokumenten mit dem Ground Truth-Editor und das Trainieren eines Modells für maschinelles Lernen. Wenn Sie eine Sprache auswählen, werden vom System sprachspezifische Vorlagen zum Verarbeiten von Wörterverzeichniseinträgen, zum Zerlegung von Text in Tokens und zum Segmentieren von Sätzen angewendet. Informationen zur Verarbeitung von Wörterverzeichnissen in verschiedenen Sprachen durch das System finden Sie unter [Wörterverzeichnisse](/docs/services/watson-knowledge-studio/dictionaries.html#wks_dictionaries).

> **Hinweis:** Der Regeleditor und das regelbasierte Modell können keinen bidirektionalen Text verarbeiten, d. h. diese Komponenten können nicht für Dokumente in arabischer Sprache verwendet werden.

> **Einschränkungen:**
>
> Aufgrund von Zeichenbeschränkungen in der zugrunde liegenden Technologie für maschinelles Lernen dürfen die Einträge im Typsystem keine Leerzeichen und nur die folgenden ASCII-Zeichen enthalten:
>
> - A bis Z und a bis z
> - 0 bis 9
> - Unterstreichungszeichen: _
>
> Außerdem gelten die folgenden Regeln:
>
> - Das erste Zeichen im Namen muss ein Buchstabe sein.
> - Ein Entitätstypname darf nicht länger als 64 Zeichen sein.
> - Ein Beziehungstypname darf nicht länger als 128 Zeichen sein.
>
> Dies bedeutet beispielsweise, dass ein Annotatorbenutzer beim Bearbeiten von japanischem Text im Ground Truth-Editor keine Entitätstyp- und Beziehungstypnamen in japanischer Sprache hinzufügen kann.

### Zugehörige Tasks

[Unterstützung für Arabisch konfigurieren](/docs/services/watson-knowledge-studio/language-support-arabic.html)
