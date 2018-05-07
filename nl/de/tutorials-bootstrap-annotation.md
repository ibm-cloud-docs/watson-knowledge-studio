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

Diese Dokumentation bezieht sich auf {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Die Dokumentation für die Vorgängerversion {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace kann über [diesen Link ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/docs/services/knowledge-studio/tutorials-bootstrap-annotation.html){: new_window} aufgerufen werden.
{: tip}

# Annotationsprozess beschleunigen
{: #wks_tutboot_intro}

In diesem Lernprogramm erfahren Sie, wie Dokumente vorannotiert werden können, um die Arbeit der Annotatorbenutzer zu vereinfachen.
{: shortdesc}

## Lernziele

Nach dem Durcharbeiten dieses Lernprogramms können Sie Dokumente mithilfe eines Modells für maschinelles Lernen vorannotieren.

Das Durcharbeiten dieses Lernprogramms dauert ungefähr 5 Minuten. Wenn Sie weitere Konzepte im Zusammenhang mit diesem Lernprogramm erkunden, kann das Durcharbeiten länger dauern.

## Vorbereitungen

- Vergewissern Sie sich, dass Sie einen unterstützten Browser verwenden. Weitere Informationen finden Sie unter [Browseranforderungen](/docs/services/watson-knowledge-studio/system-requirements.html).
- Sie haben das [Lernprogramm: Arbeitsbereich erstellen](/docs/services/watson-knowledge-studio/tutorials-create-project.html) und das [Lernprogramm: Modell für maschinelles Lernen erstellen](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html) erfolgreich abgeschlossen.
- Sie verfügen über mindestens eine Benutzer-ID mit der Rolle 'Administrator' oder 'ProjectManager'. Informationen zu Benutzerrollen finden Sie unter [Team zusammenstellen](/docs/services/watson-knowledge-studio/team.html).

## Ergebnisse

Nach Abschluss dieses Lernprogramms verfügen Sie über eine Gruppe teilweise annotierter Dokumente. Anschließend können Sie die Dokumente Annotatorbenutzern zuordnen, die das Annotieren der Dokumente zum Abschluss bringen sollen.

## Lerneinheit 1: Neue Dokumente mithilfe eines Modells für maschinelles Lernen vorannotieren
{: #wks_tutboot_ml}

In dieser Lerneinheit erfahren Sie, wie Dokumente mithilfe eines Modells für maschinelles Lernen in {{site.data.keyword.knowledgestudioshort}} vorannotiert werden.

### Informationen zu diesem Vorgang

Nachdem Sie ein Modell für maschinelles Lernen trainiert haben, können Sie das Modell zum Vorannotieren neuer Dokumente verwenden, die Sie zum Korpus hinzufügen.

> **Achtung:** Wenden Sie keinen Vorannotator auf Dokumente an, die zwar von Annotatorbenutzern annotiert, aber noch nicht zur Ground Truth hinzugefügt wurden. Andernfalls werden all vorhandenen Annotationen aus den betreffenden Dokumenten entfernt.

In diesem Lernprogramm können Sie mithilfe der Datei `documents-ml.csv` eine zweite Dokumentgruppe hinzufügen. Fügen Sie die Datei `documents-new.csv` nicht erneut hinzu. Dies würde zu doppelten Dokumenten in der Ground Truth führen. Die Duplizierung verursacht folgende Probleme:

- Wenn die Annotationen in den doppelten Dokumenten nicht übereinstimmen, wird die Qualität des Modells für maschinelles Lernen beeinträchtigt.
- Wenn die Annotationen in den doppelten Dokumenten übereinstimmen, wird das Modell für maschinelles Lernen durch die doppelten Dateien übermäßig trainiert.

### Vorgehensweise

1. Melden Sie sich bei {{site.data.keyword.knowledgestudioshort}} als Administrator an.
1. Laden Sie weitere Dokumente in den Arbeitsbereich hoch. Sie können die Datei <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/documents-ml.csv" download>`documents-ml.csv`<img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link" class="style-scope doc-content"></a> verwenden.

    Details zum Hochladen von Dokumenten finden Sie unter [Modell für maschinelles Lernen erstellen > Dokumente zum Annotieren hinzufügen](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#tut_lessml1).

1. Erstellen Sie eine Annotationsgruppe mit der Datei `documents-ml.csv`.

    Ordnen Sie für die Zwecke dieses Lernprogramms die Annotationsgruppe Ihrer Benutzer-ID mit Administratorberechtigung zu. Nachdem das Modell für maschinelles Lernen ausgeführt und die neuen Dokumente vorannotiert wurden, können Sie die Annotationsgruppe anzeigen, um zu überprüfen, wie die Dokumente vom Modell für maschinelles Lernen vorannotiert wurden. Normalerweise werden die Annotationsgruppen mindestens einem Annotatorbenutzer zugeordnet. Weitere Informationen zum Erstellen von Annotationsgruppen finden Sie unter [Modell für maschinelles Lernen erstellen > Annotationsgruppen erstellen](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml2).

1. Wählen Sie in der Seitenleiste **Modellverwaltung** > **Versionen** die Registerkarte **Maschinelles Lernen** aus und klicken Sie auf **Dieses Modell ausführen**.
1. Wählen Sie die Dokumentgruppe aus, die Sie zum Korpus hinzugefügt haben (`documents-ml.csv`) und klicken Sie auf **Ausführen**.
1. Nachdem die Vorannotierung abgeschlossen ist, können Sie eine Annotatorbenutzertask erstellen und die neuen vorannotierten Dokumente mit Annotationen versehen.

    Details zum Erstellen einer Task und zum Annotieren von Dokumenten finden Sie unter [Modell für maschinelles Lernen erstellen > Annotationstask erstellen](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml4) und [Modell für maschinelles Lernen erstellen > Dokumente annotieren](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml5).

    In dieser Situation ist der Zeitaufwand für die Arbeit der Annotatorbenutzer geringer, da die Dokumente bereits mithilfe des Modells für maschinelles Lernen vorannotiert wurden.

### Ergebnisse

Durch die Verwendung Ihres Modell für maschinelles Lernen zum Vorannotieren neuer Dokumentgruppen können Sie den Zeitaufwand der Annotatorbenutzer für die betreffenden Dokumente verringern.
