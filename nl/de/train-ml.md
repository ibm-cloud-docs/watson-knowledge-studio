---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-29"

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

Diese Dokumentation bezieht sich auf {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Die Dokumentation für die Vorgängerversion {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace kann über [diesen Link ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/docs/services/knowledge-studio/train-ml.html){: new_window} aufgerufen werden.
{: tip}

# Modell für maschinelles Lernen trainieren
{: #train-ml}

Zum Erstellen des Modells für maschinelles Lernen in {{site.data.keyword.knowledgestudiofull}} gehört das Trainieren des Modells und das Bewerten der Funktionsweise des Modells beim Annotieren von Test- und Blinddaten.
{: shortdesc}

## Modell für maschinelles Lernen erstellen
{: #wks_madocsets}

Beim Erstellen eines Modells für maschinelles Lernen wählen Sie die Dokumentgruppen aus, die zum Trainieren des Modells verwendet werden sollen, und geben an, welcher Anteil der Dokumente als Trainingsdaten, als Testdaten und als Blinddaten verwendet werden soll.

### Informationen zu diesem Vorgang
{: #wks_madocsets_about}

Mithilfe der Leistungsmetriken können Sie Methoden finden, um die Genauigkeit des Modells zu verbessern.

> **Einschränkung:** Für jede {{site.data.keyword.knowledgestudioshort}}-Instanz können nur drei Modelle für maschinelles Lernen auf einmal trainiert werden. Wenn Ihre Instanz mehrere Arbeitsbereiche enthält und derzeit bereits insgesamt 3 Modelle für maschinelles Lernen in anderen Arbeitsbereichen trainiert werden, wird Ihre Anforderung zum Trainieren des Modells für maschinelles Lernen in Ihrem Arbeitsbereich in die Warteschlange eingereiht, bis die anderen Trainingsprozesse abgeschlossen sind.

### Vorgehensweise
{: #wks_madocsets_procedure}

So erstellen Sie ein Modell für maschinelles Lernen:

1. Melden Sie sich als {{site.data.keyword.knowledgestudioshort}}-Administrator an und wählen Sie Ihren Arbeitsbereich aus.
1. Wählen Sie **Modell für maschinelles Lernen** > **Leistung** aus. 
1. Vergewissern Sie sich, dass alle Dokumentgruppen genehmigt und alle Annotationskonflikte durch Beurteilung behoben wurden. Nur Dokumente, die durch Beurteilung oder Genehmigung in die Ground Truth hochgestuft wurden, können zum Trainieren des Modells verwendet werden.
1. Klicken Sie auf **Trainieren und auswerten**.
1. Optional: Wenn Sie angeben möchten, wie Dokumente aus Ihren Dokumentgruppen zur Verwendung durch die Trainings-, Test- oder Blinddatensets auf Systemebene zugeordnet werden sollen, klicken Sie auf **Einstellungen bearbeiten**.

    Hilfe zum Festlegen der anzuwendenden Aufteilungsverhältnisse finden Sie unter [Dokumentgruppen verwalten](/docs/services/watson-knowledge-studio/improve-ml.html#wks_mamanagedata).

1. Optional: Ordnen Sie die Wörterverzeichnisse, die vom Modell für maschinelles Lernen zum Trainieren verwendet werden sollen, dem Entitätstyp der Wörterverzeichniseinträge zu.

    Wenn Sie einen wörterverzeichnisbasierten Vorannotator erstellt haben, wurde dieser Schritt bereits ausgeführt. Klicken Sie auf **Für wörterverzeichnisbasierten Vorannotator definierte Zuordnung wiederverwenden**, um die Zuordnung erneut zu verwenden, oder definieren Sie eine neue Zuordnung.

    Das Modell verwendet die Typinformationen der Wörterverzeichniseinträge als eine Komponente von zahlreichen linguistischen Analysefunktionen, die in das Training einbezogen werden.

1. Klicken Sie auf **Trainieren**, um das Modell zu trainieren, oder klicken Sie auf **Trainieren & auswerten**, um das Modell zu trainieren, die vom Modell für maschinelles Lernen hinzugefügten Annotationen auszuwerten und die Leistungsstatistik zu analysieren.

    > **Wichtig:** Das Trainieren eines Modells für maschinelles Lernen kann mehrere Minuten bis mehrere Stunden dauern, abhängig von der Anzahl der vorhandenen Annotationen der Annotatorbenutzer und von der Gesamtzahl der Wörter in allen Dokumenten.

1. Wählen Sie die Dokumentgruppen aus, die Sie zum Trainieren des Modells verwenden möchten.

    > **Hinweis:** Die Dokumentgruppen müssen mindestens 10 annotierte Dokumente enthalten.

1. Nachdem das Modell erstellt wurde, wählen Sie eine der folgenden Aktionen aus:

    <table summary="Jede Zeile in dieser Tabelle beschreibt eine Auswahloption.">
      <caption>Tabelle 1. Dokumentoptionen</caption>
      <tr>
        <th style="vertical-align:bottom; text-align"left" id="d33883e137-option">Option</th>
        <th style="vertical-align:bottom; text-align"left" id="d33883e137-desc">Beschreibung</th>
      </tr>
      <tr>
        <td style="vertical-align:top; text-align"left" headers="d33883e137-option" id="d33883e139">
          <p><strong>Log</strong></p>
        </td>
        <td style="vertical-align:top; text-align"left" headers="d33883e137-desc d33883e139">
          <p>Zeigen Sie die Protokolldatei an, um zu sehen, ob Probleme aufgetreten sind.</p>
        </td>
      </tr>
      <tr>
        <td style="vertical-align:top; text-align"left" headers="d33883e137-option" id="d33883e144">
          <p><strong>Details</strong></p>
        </td>
        <td style="vertical-align:top; text-align"left" headers="d33883e137-desc d33883e144">
          <p>Zeigen Sie die Leistungsstatistik für die Annotation an oder ändern Sie die Dokumentgruppen, die Sie zum Trainieren
              und Testen des Modells verwenden möchten, und erstellen Sie Snapshotversionen
              der Modellartefakte.</p>
        </td>
      </tr>
      <tr>
        <td style="vertical-align:top; text-align"left" headers="d33883e137-option" id="d33883e149">
          <p><strong>Export</strong></p>
        </td>
        <td style="vertical-align:top; text-align"left" headers="d33883e137-desc d33883e149">
          <p>Wenn Sie einen Standardplan oder einen Premium-Plan haben, können Sie eine <code>ZIP</code>-Datei in Ihr lokales System exportieren, die die Komponenten enthält, die zum Ausführen des Modells in einer Laufzeitumgebung für maschinelles Lernen erforderlich sind, z. B. {{site.data.keyword.watson}} Explorer.</p>
        </td>
      </tr>
    </table>

## Vom Modell hinzugefügte Annotationen auswerten
{: #wks_matest}

Sie können die Ground Truth-Ansicht der von Annotatorbenutzern hinzugefügten Annotationen mit den vom Modell hinzugefügten Annotationen vergleichen.

### Vorgehensweise
{: #wks_matest_procedure}

So werten Sie die vom Modell hinzugefügten Annotationen aus:

1. Wählen Sie **Modell für maschinelles Lernen** > **Leistung** > **Trainieren und auswerten** aus. Die Seite für Trainings-, Test- und Blinddatensets wird angezeigt.
1. Klicken Sie auf **Ground Truth anzeigen** für das Trainingsset oder Testset, um die Annotationen anzuzeigen, die durch das Vorannotieren und durch Annotatorbenutzer hinzugefügt wurden. Der Ground Truth-Editor wird geöffnet. Öffnen Sie einzelne Dokumente durch Klicken, um zu prüfen, wie die Erwähnungen, Beziehungen und Koreferenzen annotiert wurden.
1. Klicken Sie auf der Seite **Leistung** auf **Decodierungsergebnisse anzeigen**, um die Annotationen anzuzeigen, die vom Modell für maschinelles Lernen in den Dokumenten des Testsets hinzugefügt wurden. Diese Schaltfläche ist erst verfügbar, nachdem Sie das Modell ausgewertet haben. Beim Anzeigen der Ergebnisse können Sie erkennen, wie zutreffend die Erwähnungen, Beziehungen und koreferenzierten Erwähnungen in den Testdaten vom Modell für maschinelles Lernen beschriftet wurden.
1. Wenn Sie das Aufteilungsverhältnis der Dokumente zwischen den Trainings-, Test- und Blinddatensets ändern möchten, klicken Sie auf **Leistung** > **Trainieren und auswerten** > **Einstellungen bearbeiten**. Wenn die ersten Ergebnisse akzeptabel aussehen, können Sie gegebenenfalls die Anzahl der Dokumente im Testset erhöhen, um die Ergebnisse des Modells für maschinelles Lernen noch eingehender zu testen. Sie können das Verhältnis für die automatische Aufteilung der Dokumente für verschiedene Zwecke ändern oder Sie können bestimmte Dokumentgruppen auswählen, die als Trainingsdaten, Testdaten und Blinddaten verwendet werden sollen.
1. Wenn Sie Änderungen vorgenommen haben, klicken Sie auf **Trainieren & auswerten**, um das Modell erneut zu trainieren und die Annotationen erneut auszuwerten.

## Modell für maschinelles Lernen löschen
{: #wks_madelete}

Ein Modell für maschinelles Lernen kann nicht gelöscht werden.

Sie können den Arbeitsbereich löschen, der zum Entwickeln des Modells verwendet wurde, aber Sie können das Modell an sich nicht löschen. Das Löschen eines Modells ist keine empfehlenswerte Vorgehensweise. Stattdessen sollten die Artefakte zum Trainieren des Modells aktualisiert oder ersetzt werden. Auch ein Modell, das nicht die erwarteten Ergebnisse liefert, kann optimiert werden. Bei jedem Erstellen einer neuen Modellversion wird das Modell neu erstellt. Beim Trainieren der nächsten Version können Sie Artefakte wie Wörterverzeichnisse und das Typsystem bearbeiten und andere Annotationsgruppen verwenden.
