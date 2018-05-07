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

Diese Dokumentation bezieht sich auf {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Die Dokumentation für die Vorgängerversion {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace kann über [diesen Link ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/docs/services/knowledge-studio/rule-annotator-add-doc.html){: new_window} aufgerufen werden.
{: tip}

# Dokumente zum Definieren von Regeln hinzufügen
{: #wks_rule_anno_add}

Fügen Sie Dokumente mit linguistischen Mustern hinzu, die Regeltypen veranschaulichen, die Sie definieren möchten.
{: shortdesc}

Dokumente, die Sie zum Definieren von Regeln hinzufügen, werden getrennt von Dokumenten aufbewahrt, die Sie zum Annotieren hinzufügen. Der Zweck dieser Dokumente besteht allein darin, Ausgangsmaterial zum Erkennen von Mustern zu bereitzustellen. Diese Dokumente werden weder zum Trainieren verwendet noch heruntergeladen.

## Methoden zum Hinzufügen von Dokumenten im Regeleditor

- **Ein Textdokument im UTF-8-Format verfassen**

    Sie können Text, der ein Muster veranschaulicht, direkt im Regeleditor hinzufügen. Der Name, den Sie für das Dokument angeben, darf nicht länger als 256 Zeichen sein.

- **CSV-Datei hochladen**

    Laden Sie eine Datei im CSV-Format hoch, die den Dokumenttext enthält.

- **Dokument kopieren, das zum Annotieren importiert wurde**

    Wenn ein Dokument, das Teil einer Gruppe ist, die zu Annotationszwecken importiert wurde, Beispiele für Muster enthält, die Sie als Regeln erfassen möchten, können Sie das Dokument in den Regeleditor kopieren. Alle Änderungen, die Sie an dem Dokument vornehmen, wirken sich nicht auf die Originalversion des Dokuments aus, das zum Annotieren verwendet wird. Informationen zum Hochladen von Dokumenten finden Sie unter [Dokumente zu einem Arbeitsbereich hinzufügen](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projadd).

Wählen Sie zum Kopieren oder Hochladen Dokumente mit klar erkennbaren Mustern aus, die zum Identifizieren von Entitätstypen in Dokumenten hilfreich sind.
