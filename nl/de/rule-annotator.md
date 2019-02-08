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

Diese Dokumentation bezieht sich auf {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Die Dokumentation für die Vorgängerversion {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace kann über [diesen Link![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/docs/services/knowledge-studio/rule-annotator.html){: new_window} aufgerufen werden.
{: tip}

# Regeln
{: #rule-annotator}

Erstellen Sie ein regelbasiertes Modell zum Erkennen von Mustern in Ihren Dokumenten. Verwenden Sie Regeln, um Muster zu erfassen, die in Dokumenten vorkommen und Informationen über die zugrunde liegenden Entitätstypen liefern.
{: shortdesc}

## Übersicht über Klassen

Beim Erstellen einer Regel verwenden Sie Klassen, um Informationstypen darzustellen. Diese Klassen sind mit Entitätstypen vergleichbar. Warum werden beim Definieren von Regeln nicht einfach Entiätstypen verwendet? Dies hat seinen Grund darin, dass beim Erstellen von Regeln Zwischenklassen definiert werden können, die nur dazu dienen, andere komplexere Klassen zu erstellen. Diese Zwischenklassen dienen lediglich als Mittel zum Zweck. Sie haben keine eigenständige Bedeutung. Zwischenklassen dienen im Verbund mit anderen Zwischenklassen zum Definieren einer effizienteren und vollständigeren Klasse. Eine Zwischenklasse ist zwar nötig, aber sie wird nicht im Rahmen eines Typsystems bereitgestellt. Damit das regelbasierte Modell zielführende Aufgaben wie das Vorannotieren von Dokumenten mit Entitätserwähnungen übernehmen kann, müssen Sie die komplexen Klassen, die Sie beim Erstellen von Regeln verwenden, den entsprechenden Entitätstypen aus dem Typsystem zuordnen.

Angenommen, Sie benötigen ein Modell, das Personennamen erkennen kann. Um ein Modell für maschinelles Lernen so zu trainieren, dass es Personennamen erkennen kann, annotieren Sie viele verschiedene Namen mit unterschiedlichen Schreibweisen in den Dokumenten einer Annotationsgruppe mit dem Entitätstyp `PERSON`. Um ein regelbasiertes Modell zum Erkennen von Personennamen zu trainieren, können Sie eine Regel definieren, die zum Angeben von Personennamen verwendete Textmuster beschreibt. Sie können beispielsweise eine Klasse `Vorname` und eine Klasse `Nachname` erstellen und mithilfe dieser Zwischenklassen eine Klasse `VollständigerName` definieren. Sie können Bedingungen definieren, um die Platzierung der Klasse `VollständigerName` in Relation zu gebräuchlichen Präfixen wie `Dr.` und gebräuchlichen Suffixen wie `a. D.` zu bestimmen. Bei der Verwendung des regelbasierten Modells wird die Klasse `VollständigerName` dem Entitätstyp `PERSON` zugeordnet.

Ein weiterer Grund, warum das Zuordnen von Zwischenklassen zu Entitäten in Ihrem Typsystem vermieden werden sollte, besteht darin, dass beim Vorannotieren von Dokumenten mit dem regelbasierten Modell und dem anschließenden Hinzufügen dieser Dokumente zur Ground Truth für das Trainieren eines Modells für maschinelles Lernen keine Regeln definiert werden sollen, die Entitätserwähnungen mit Überschneidungen erzeugen. Beispiel: Wenn die Zwischenklasse `Vorname` und die komplexe Klasse `VollständigerName` der Entität `PERSON` zugeordnet würden, würde das Vorkommen des Namens `John Doe, a. D.` zu einer Erwähnung mit Überschneidung führen.

## Tools im Regeleditor

Der Regeleditor stellt einige Tools bereit, die Sie beim Definieren von Regeln unterstützen.

- Wörterverzeichnis

    Fügen Sie ein Wörterverzeichnis hinzu und ordnen Sie diesem einen Klassennamen zu. Alle gefundenen Wörter, die mit Einträgen im Wörterverzeichnis übereinstimmen, werden automatisch mit der zugeordneten Klasse annotiert.

- Regulärer Ausdruck

    Ein regulärer Ausdruck (regular Expression, RegEx) ist eine Zeichenfolge, die ein Suchmuster definiert. Das Tool für reguläre Ausdrücke (regex) im Regeleditor erkennt Ausdrücke, die der Syntax `java.util.regex.Pattern` entsprechen. Hier ein einfaches Beispiel:
    `[A-Z][a-z]*`: Findet Wörter mit Großschreibung.

    `[A-Z]` findet alle Großbuchstaben (A bis Z) und `[a-z]*` findet alle Kleinbuchstaben (a bis z), die beliebig oft vorkommen. Der Stern (*) gibt die Anzahl der Wiederholungen (gar nicht oder beliebig oft) an.

    Sie können ein frei verfügbares, webbasiertes Dienstprogramm für reguläre Ausdrücke verwenden, um den richtigen Ausdruck zum Erfassen des gesuchten Musters zu finden.

    Angenommen, Ihre Dokumente enthalten verschiedene Referenzen, die den folgenden Ausdrücken ähneln:

    ```
    35-jähriger Fahrer
    16-jähriger Fahrschüler
    ```
    {: screen}

    Die Syntax `n-jähriger x` ist ein Muster, das in der Regel eine Person bezeichnet. Sie können eine Regel mit einem regulären Ausdruck definieren, der das Muster `n-jähriger x` findet, und die gefundenen Erwähnungen als Entitätstyp `PERSON` annotieren.
