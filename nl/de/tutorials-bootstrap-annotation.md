---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-18"

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

Diese Dokumentation bezieht sich auf {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Die Dokumentation für die Vorgängerversion {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace kann über [diesen Link ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/docs/services/knowledge-studio/tutorials-bootstrap-annotation.html){: new_window} aufgerufen werden.
{: tip}

# Dokumente vorannotieren
{: #wks_tutboot_intro}

In diesem Lernprogramm erfahren Sie, wie Sie Dokumente vorannotieren können. Dabei wird der Annotationsprozess für Annotatorbenutzer gestartet.
{: shortdesc}

## Lernziele
{: #objectives}

Nach dem Durcharbeiten dieses Lernprogramms können Sie Dokumente mithilfe eines Modells für maschinelles Lernen vorannotieren.

Das Durcharbeiten dieses Lernprogramms dauert ungefähr 5 Minuten. Wenn Sie weitere Konzepte im Zusammenhang mit diesem Lernprogramm erkunden, kann das Durcharbeiten länger dauern.

## Vorbereitungen
{: #prereqs}

- Vergewissern Sie sich, dass Sie einen unterstützten Browser verwenden. Siehe [Browseranforderungen](/docs/services/watson-knowledge-studio/system-requirements.html).
- Sie haben die [Einführung in {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/tutorials-create-project.html) erfolgreich abgeschlossen. Sie umfasst das Erstellen eines Arbeitsbereichs, das Erstellen eines Typsystems und das Hinzufügen eines Wörterverzeichnisses.
- Sie haben [Modell für maschinelles Lernen erstellen](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html) erfolgreich abgeschlossen.
- Sie müssen über mindestens eine Benutzer-ID in der Rolle "Admin" oder "Projektleiter" verfügen. Informationen zu Benutzerrollen finden Sie in [Benutzerrollen in {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/roles.html).

## Ergebnisse
{: #results}

Nach Abschluss dieses Lernprogramms verfügen Sie über eine Gruppe teilweise annotierter Dokumente. Anschließend können Sie die Dokumente Annotatorbenutzern zuordnen, die das Annotieren der Dokumente zum Abschluss bringen sollen.

## Lerneinheit 1: Neue Dokumente mithilfe eines Modells für maschinelles Lernen vorannotieren
{: #wks_tutboot_ml}

In dieser Lerneinheit erfahren Sie, wie Dokumente mithilfe eines Modells für maschinelles Lernen in {{site.data.keyword.knowledgestudioshort}} vorannotiert werden.

### Informationen zu diesem Vorgang
{: #wks_tutboot_ml_about}

Nachdem Sie ein Modell für maschinelles Lernen trainiert haben, können Sie das Modell zum Vorannotieren neuer Dokumente verwenden, die Sie zum Korpus hinzufügen.

> **Achtung:** Wenden Sie keinen Vorannotator auf Dokumente an, die zwar von Annotatorbenutzern annotiert, aber noch nicht zur Ground Truth hinzugefügt wurden. Andernfalls werden all vorhandenen Annotationen aus den betreffenden Dokumenten entfernt.

In diesem Lernprogramm können Sie mithilfe der Datei `documents-ml.csv` eine zweite Dokumentgruppe hinzufügen. Fügen Sie die Datei `documents-new.csv` nicht erneut hinzu. Dies würde zu doppelten Dokumenten in der Ground Truth führen. Die Duplizierung verursacht folgende Probleme:

- Wenn die Annotationen in den doppelten Dokumenten nicht übereinstimmen, wird die Qualität des Modells für maschinelles Lernen beeinträchtigt.
- Wenn die Annotationen in den doppelten Dokumenten übereinstimmen, wird das Modell für maschinelles Lernen durch die doppelten Dateien übermäßig trainiert.

Weitere Informationen zum Vorannotieren von Dokumenten finden Sie unter [Annotationsprozess beschleunigen](/docs/services/watson-knowledge-studio/preannotation.html). Dort werden weitere Methoden des Vorannotierens beschrieben.

### Vorgehensweise
{: #wks_tutboot_ml_procedure}

1. Melden Sie sich bei {{site.data.keyword.knowledgestudioshort}} als Administrator an.
1. Laden Sie weitere Dokumente in den Arbeitsbereich hoch. Sie können die Datei <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/documents-ml.csv" download>`documents-ml.csv` <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link" class="style-scope doc-content"></a> verwenden.

    Weitere Informationen zum Hinzufügen von Dokumenten zu einem Arbeitsbereich finden Sie unter [Dokumente zum Annotieren hinzufügen](/docs/services/watson-knowledge-studio/documents-for-annotation.html).

1. Erstellen Sie eine Annotationsgruppe, die die Datei `documents-ml.csv` als Basisgruppe verwendet, und weisen Sie sie sich selbst (den Administrator) zu.

    Nachdem Sie die folgenden Schritte zum Vorannotieren der neuen Dokumente ausgeführt haben, können Sie die Annotationsgruppe anzeigen, um zu sehen, wie das Modell für maschinelles Lernen die Dokumente annotiert hat. Normalerweise werden die Annotationsgruppen mindestens einem Annotatorbenutzer zugeordnet. Weitere Informationen zum Erstellen und Zuordnen von Annotationsgruppen finden Sie unter [Dokumente zum Annotieren hinzufügen](/docs/services/watson-knowledge-studio/documents-for-annotation.html).

1. Um die neuen Dokumente vorab zu annotieren, klicken Sie auf **Modell für maschinelles Lernen** > **Versionen**. Klicken Sie dann auf **Dieses Modell ausführen**.
1. Wählen Sie die Dokumentgruppe aus, die Sie zum Korpus hinzugefügt haben (`documents-ml.csv`) und klicken Sie auf **Ausführen**.
1. Nachdem die Vorannotierung abgeschlossen ist, erstellen Sie eine Annotatorbenutzertask, die die erstellte Annotationsgruppe einbezieht.

    Weitere Informationen zum Erstellen einer Annotationstask finden Sie unter [Annotationen einrichten](/docs/services/watson-knowledge-studio/annotate-documents.html).

1. Um die Annotationen anzuzeigen, die vom Modell für maschinelles Lernen auf die neuen Dokumente angewendet wurden, öffnen Sie die Annotationstask.

    Da die neuen Dokumente mit dem Modell für maschinelles Lernen vorannotiert wurden, benötigt der Annotatorbenutzer weniger Zeit. Weitere Informationen zum Hinzufügen von Annotationen durch Annotatorbenutzer finden Sie unter [Dokumente annotieren](/docs/services/watson-knowledge-studio/user-guide.html).

### Ergebnisse
{: #wks_tutboot_ml_results}

Durch die Verwendung Ihres Modell für maschinelles Lernen zum Vorannotieren neuer Dokumentgruppen können Sie den Zeitaufwand der Annotatorbenutzer für die betreffenden Dokumente verringern.
