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

Diese Dokumentation bezieht sich auf {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Die Dokumentation für die Vorgängerversion {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace kann über [diesen Link ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/docs/services/knowledge-studio/improve-ml.html){: new_window} aufgerufen werden.
{: tip}

# Modell für maschinelles Lernen verbessern
{: #improve-ml}

Nachdem Sie die Problembereiche des Modells identifiziert haben, können Sie Maßnahmen ergreifen, um die Leistung des Modells zu verbessern.
{: shortdesc}

## Modellversionen erstellen
{: #wks_maversions}

Nach dem Erstellen eines Modells für maschinelles Lernen können Sie einen Snapshot erstellen, um eine Sicherungsversion der aktuellen Ressourcen aufzubewahren, damit sie in einer späteren Phase bei Bedarf wiederhergestellt werden können.

### Informationen zu diesem Vorgang
{: #wks_maversions_about}

Der F1-Score ist ein Indikator für die Qualität des Modells. Wenn die Leistungsbewertung für das Modell positiv ausfällt, kann es hilfreich sein, eine Version der Komponente zu speichern, bevor Änderungen an den Ressourcen vorgenommen werden. Falls die Änderungen zu einer schlechteren Leistung führen, können Sie auf eine gespeicherte Version zurückgreifen. Beim Wiederherstellen einer gespeicherten Version, werden alle Annotationstasks archiviert, da sie nicht länger gültig sind.

Sie können maximal 10 Versionen eines Arbeitsbereichs erstellen. Wenn dieser Grenzwert erreicht ist, müssen Sie ältere oder nicht mehr benötigte Versionen löschen, bevor eine neue Versionen erstellt werden kann.

Beim Erstellen einer neuen Version werden die folgenden Ressourcen erfasst:

- Typsystem
- Korpus
- Ground Truth
- Modell für maschinelles Lernen
- Auswertungsergebnisse des Modells für maschinelles Lernen

Die folgenden Ressourcen werden nicht erfasst:

- Annotationstasks, da sie keine permanenten Ressourcen sind und nur zum Festlegen der Ground Truth dienen
- Wörterverzeichnisse, da sie sehr umfangreich sein können und unterschiedliche Wörterverzeichnistypen auf verschiedene Arten verwaltet werden

### Vorgehensweise
{: #wks_maversions_procedure}

So können Sie Versionen der Modelle für maschinelles Lernen erstellen und wiederherstellen:

1. Melden Sie sich als {{site.data.keyword.knowledgestudioshort}}-Administrator oder -Projektleiter an und wählen Sie Ihren Arbeitsbereich aus.
1. Wählen Sie **Modell für maschinelles Lernen** > **Leistung** aus. Leistungsstatistikdaten zur aktuellen Version (als 'Version 1.0' bezeichnet) werden angezeigt.
1. Um einen Snapshot der aktuellen Version zu erstellen, klicken Sie auf **Modell für maschinelles Lernen** > **Versionen**. Klicken Sie dann auf **Snapshot erstellen**. Die Ressourcen der Version 1.0 werden eingefroren und die neue Version 1.1 wird zur aktuellen Version. Für jede neue Version, die Sie erstellen, wird die Nebenversionsnummer um eins erhöht (z. B. von 1.0 auf 1.1 und dann auf 1.2).
1. Überarbeiten Sie die Arbeitsbereichsressourcen nach Bedarf, und führen Sie ein erneutes Trainieren und Auswerten des Modells durch.
1. Wenn Sie mit der Leistung des Modells zufrieden sind und die neue Version speichern möchten, bevor Sie weitere Änderungen vornehmen, erstellen Sie erneut eine Version. Fahren Sie mit dem Überarbeiten der Ressourcen und dem Trainieren des Modells nach Bedarf fort und erstellen Sie für jede Iteration, die Sie aufbewahren möchten, eine neue Version.
1. Wenn die Leistung des überarbeiteten Modells nicht Ihren Erwartungen entspricht, können Sie eine vorherige Version wiederherstellen und anschließend weitere Tests vornehmen.

    1. Öffnen Sie die Seite **Assets** > **Wörterverzeichnisse** und laden Sie die Wörterverzeichnisse herunter, die im wiederhergestellten Modell wiederverwendet werden sollen.
    1. Klicken Sie auf **Modell für maschinelles Lernen** > **Versionen** und auf **Hochstufen** für die Version, die Sie wiederherstellen möchten. Die hochgestufte Version wird zur aktuellen Version und die Versionsnummer wird in 2.0 geändert. Beim Hochstufen einer Version wird die Hauptversionsnummer erhöht und die Nebenversionsnummer auf 0 gesetzt (z. B. von 1.1 auf 2.0).
    1. Öffnen Sie die Seite **Wörterverzeichnisse** und laden Sie die Wörterverzeichnisse hoch, die zuvor heruntergeladen wurden.
    1. Wenn nach dem Testen der neuen Version Änderungen in der Ground Truth erforderlich sind, öffnen Sie die Seite **Modell für maschinelles Lernen** > **Annotationstasks** und erstellen Sie eine neue Annotationstask.

## Typsystem ändern, ohne von Annotatorbenutzern erstellte Annotationen zu verlieren
{: #wks_projtypesysmod}

Beim Trainieren eines Modells machen die Leistungsstatistiken möglicherweise Änderungen erforderlich. Im Allgemeinen soll das Typsystem der Realität möglichst nahe kommen, bevor umfangreiche Annotationstasks gestartet werden. Wenn Sie das Typsystem ändern, nachdem die Annotatorbenutzer mit ihrer Arbeit begonnen haben, müssen die Annotatorbenutzer die bereits annotierten Dokumente erneut bearbeiten. Die Annotatorbenutzer müssen beurteilen, ob die Änderungen des Typsystems anwendbar sind.

### Informationen zu diesem Vorgang
{: #wks_projtypesysmod_about}

Dieser Prozess gibt das aktuelle Typsystem, die Tastenkombinationen für den Ground Truth-Editor und die Farbeinstellungen an alle Dokumentgruppen in einer Task weiter.

### Vorgehensweise
{: #wks_projtypesysmod_procedure}

So ändern Sie das Typsystem, ohne die bisherigen Arbeitsergebnisse der Annotatorbenutzer zu verlieren:

1. Ändern Sie das Typsystem, z. B. indem Sie Entitätstypen oder Beziehungstypen hinzufügen oder entfernen.
1. Entscheiden Sie, ob die Änderungen in bestehende Tasks der Annotatorbenutzer übernommen werden sollen.
1. Öffnen Sie auf jeder Seite **Modell für maschinelles Lernen** > **Annotationstasks** jede Task, die Sie aktualisieren möchten, und klicken Sie auf **Aktualisiertes Typsystem anwenden**.

    Wenn Sie Entitäts- oder Beziehungstypen aus dem Typsystem entfernt haben, werden alle Vorkommen der betreffenden Typen in den Dokumenten grau dargestellt. Diese ungültigen Typen werden vom Modell für maschinelles Lernen ignoriert. Sie können jedoch weiterhin Dokumentgruppen einreichen und genehmigen.

1. Informieren Sie die Annotatorbenutzer über die Änderungen im Typsystem.
1. Veranlassen Sie die Annotatorbenutzer, ihre Dokumente zu überarbeiten, damit das geänderte Typsystem angewendet wird. Wenn Sie beispielsweise neue Entitäts- oder Beziehungstypen hinzugefügt haben, müssen die Annotatorbenutzer ihre zugeordneten Dokumente überarbeiten und entsprechend annotieren.

    > **Hinweis:** Wenn die Task abgeschlossene Dokumente enthält, können diese von den Annotatorbenutzern erst bearbeitet werden, um Typsystemänderungen zu beurteilen, nachdem sie wieder in einen bearbeitbaren Status versetzt wurden. Zu diesem Zweck müssen die Annotatorbenutzer die betreffenden Dokumentgruppen einreichen, damit sie von Ihnen abgelehnt werden können.

**Zugehörige Konzepte**:
{: #wks_projtypesysmod_related}

[Typsysteme](/docs/services/watson-knowledge-studio/typesystem.html#wks_typesystem)

## Dokumentgruppen verwalten
{: #wks_mamanagedata}

Verwenden Sie geeignete Datensets, um das Modell zum richtigen Zeitpunkt zu testen und zu trainieren.

Die Dokumente, die Sie zum System hinzufügen, müssen beim Erstellen eines Modells für maschinelles Lernen den folgenden Datensets auf Systemebene zugeordnet werden:

- **Trainingsset**

    Eine Dokumentgruppe mit vorannotierten oder von Annotatorbenutzern annotierten Dokumenten, die zum Trainieren des Modells verwendet wird. Das Trainingsset dient dazu, im Modell für maschinelles Lernen die richtigen Annotationen einzurichten. Dazu gehört auch das Trainieren des Modells mithilfe von nicht annotiertem Text.

- **Testset**

    Eine Gruppe mit annotatierten Dokumenten, die zum Testen des trainierten Modells verwendet werden. Nachdem Sie einen Test mit der Testgruppe durchgeführt haben, führen Sie eine detaillierte Analyse zum Erkennen von Fehlern in den Ergebnissen durch. Die ausführliche Analyse unterstützt das Aufdecken und Beheben von Schwächen im aktuellen Modell.

- **Blinddatenset**

    Eine Gruppe annotierter Dokumente, die separat aufbewahrt und für laufende Tests des Systems verwendet werden, nachdem mehrere Test- und Optimierungsläufe durchgeführt wurden. Damit die Genauigkeit nicht beeinträchtigt wird (z. B. durch Änderungen, die allein auf Annotationen in bereits bekannten Dokumenten basieren), sollten Blinddaten verwendet werden, die den an der Modellerstellung mitwirkenden Benutzern unbekannt sind. Die gemeldeten Ergebnisse sollten ausschließlich von Tests stammen, die mit Blinddaten durchgeführt wurden. Befassen Sie sich nach einem Test mit dem Blinddatenset ausschließlich mit den höchsten Sore-Werten (z. B. mit den zusammenfassenden F1-Scores für Erwähnungen und Beziehungen). Zu viele Einzeldaten über die Leistung können sich nachteilig auf Ihre Entscheidungen im Hinblick auf die Verbesserung des Modells auswirken.

Das Ziel von {{site.data.keyword.knowledgestudioshort}} besteht darin, die effiziente Zusammenarbeit großer Teams bei der Erstellung von Modellen zu unterstützen. Das Produkt setzt voraus, dass Modelle von einem Team erstellt werden, zu dem eine Gruppe von Annotatorbenutzern und eine separate Person oder Gruppe gehören, die das Modell zusammenstellen, testen und optimieren. Aufgrund dieser Annahme ist die Anwendung so konzipiert, dass proportional bemessene Dokumentgruppierungen aus einer einzelnen Dokumentgruppe per Push-Operation an die Test-, Trainings- und Blinddatensets übertragen werden. Wenn Ihr Team jedoch nicht entsprechend aufgeteilt ist (d. h. die gleichen Personen arbeiten als Annotatorbenutzer und überprüfen die Testergebnisse des Modells im Detail), müssen Sie gegebenenfalls die Zuordnung der Dokumente in diesen Gruppen so anpassen, dass die Dokumente entsprechend getrennt werden.

### Wozu wird ein Blinddatenset benötigt?
{: #wks_mamanagedata_why}

Da Sie Testdaten verwenden, um die Genauigkeit des Modells im Detail zu bewerten, lernen Sie die Dokumente und ihre Beschaffenheit immer besser kennen. Beispielsweise erkennen Sie deutlich, welche Entitätstypen, Beziehungstypen und Texttypen in den Dokumenten vom Modell für maschinelles Lernen am besten erkannt werden und welche nicht. Dieses Wissen ist wichtig und hilft Ihnen, die richtigen Verbesserungen vorzunehmen, um das Typsystem zu optimieren, mit Trainingsdaten die Lücken zu füllen, Wörterverzeichnisse hinzuzufügen usw. Da die Testdokumente mehrfach (iterativ) verwendet werden, um das Modell zu verbessern, haben sie indirekte Auswirkungen auf das Trainieren des Modells. Aus diesem Grund ist ein blindes (unbekanntes) Datenset von großer Bedeutung.

### Wie kann ich steuern, welche Dokumente einer Gruppe zugeordnet werden?
{: #wks_mamanagedata_how}

Beim Erstellen eines Modells für maschinelles Lernen müssen Sie angeben, welcher Anteil der Dokumente aus der Gruppe den Trainings-, Test- und Blinddatensets zugeordnet werden sollen. {{site.data.keyword.knowledgestudioshort}} wendet automatisch das Verhältnis 70:23:7 auf die Dokumentgruppen an, die Sie zum Erstellen eines Modells für maschinelles Lernen verwenden. Sie können dieses Verhältnis ändern.

- Um eine Dokumentgruppe zum Trainingsset hinzuzufügen, die von Annotatorbenutzern annotiert wurde, geben Sie das Aufteilungsverhältnis 100:0:0 an.
- Nachdem ein Datenset zum Trainieren verwendet wurde, kann es zum Testen genutzt werden. Wenn Sie eine Dokumentgruppe nur zum Testen verwenden möchten, geben Sie ein Aufteilungsverhältnis von 0:100:0 an.
- Zum Blinddatenset sollten nur Dokumentgruppen hinzugefügt werden, die noch nicht zum Trainieren oder Testen verwendet wurden. Geben Sie dazu ein Aufteilungsverhältnis von 0:0:100 für die Dokumentgruppe an.

Ein Blinddatenset sollte nach wenigen Iterationen nicht weiter verwendet werden. Je häufiger ein Blinddatenset verwendet wird, umso weniger 'blind' (unbekannt) sind die darin enthaltenen Daten. Dies gilt auch für Ihre Testdaten. Anstatt die Datensets zu verwerfen, können sie für einen anderen Zweck verwendet werden. Gehen Sie dabei nach dem folgenden Migrationsablauf vor:

```
Blinddaten --> Testdaten --> Trainingsdaten
```
{: screen}

Wenn die Datensets migriert werden, können Sie neue unbekannte Dokumentgruppen als Blinddaten und als Testdaten hinzufügen. Stellen Sie jedoch sicher, dass immer eine Methode zum Bewerten der Genauigkeit über Modellversionen hinweg zur Verfügung steht. Ein Verfahren zum Erstellen einer Baseline ist das Anwenden einer vorherigen Modellversion auf die neuen Dokumentgruppen. Die Ergebnisse dieses Vorgangs liefern einen Basiswert zum Vergleichen mit der Ausführung neuerer Modelle auf dieselben Dokumentgruppen.
