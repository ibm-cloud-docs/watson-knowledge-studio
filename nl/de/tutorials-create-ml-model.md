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

Diese Dokumentation bezieht sich auf {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Die Dokumentation für die Vorgängerversion {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace kann über [diesen Link ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/docs/services/knowledge-studio/tutorials-create-ml-model.html){: new_window} aufgerufen werden.
{: tip}

# Modell für maschinelles Lernen erstellen
{: #wks_tutml_intro}

In diesem Lernprogramm erfahren Sie mehr über den Prozess zum Erstellen eines Modells für maschinelles Lernen, das Sie bereitstellen und mit anderen {{site.data.keyword.watson}}-Services verwenden können.
{: shortdesc}

## Lernziele

Nach dem Durcharbeiten der Lerneinheiten in diesem Lernprogramm können Sie die folgenden Tasks ausführen:

- Dokumentgruppen erstellen
- Dokumente vorannotieren
- Tasks für Annotatorbenutzer erstellen
- Übereinstimmung der Annotatoren analysieren und Konflikte in annotierten Dokumenten beurteilen
- Annotatoren für maschinelles Lernen erstellen

Das Durcharbeiten dieses Lernprogramms dauert ungefähr 60 Minuten. Wenn Sie weitere Konzepte im Zusammenhang mit diesem Lernprogramm erkunden, kann das Durcharbeiten länger dauern.

## Vorbereitungen

- Vergewissern Sie sich, dass Sie einen unterstützten Browser verwenden. Weitere Informationen finden Sie unter [Browseranforderungen](/docs/services/watson-knowledge-studio/system-requirements.html).
- Sie haben das [Lernprogramm: Arbeitsbereich erstellen](/docs/services/watson-knowledge-studio/tutorials-create-project.html) erfolgreich abgeschlossen.
- Sie verfügen über mindestens eine Benutzer-ID mit der Rolle 'Administrator' oder 'ProjectManager'. 

    > **Hinweis:** Falls möglich, verwenden Sie in diesem Lernprogramm mehrere Benutzer-IDs für die Tasks des Modells für maschinelles Lernen (eine Benutzer-ID mit Administrator- oder Projektleiterberechtigungen und mindestens zwei Benutzer-IDs für Annotatorbenutzer). Die Verwendung mehrerer Benutzer-IDs ermöglicht eine besonders realitätsnahe Simulation eines tatsächlichen {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}}™ {{site.data.keyword.knowledgestudioshort}}-Arbeitsbereichs, in dem ein Projektleiter die von mehreren Annotatorbenutzern erstellten Annotationen koordnieren und beurteilen muss. Wenn Ihnen nur eine einzige Benutzer-ID zur Verfügung steht, können Sie dennoch die meisten Teile dieses Prozesses simulieren.

    Informationen zu Benutzerrollen finden Sie unter [Team zusammenstellen](/docs/services/watson-knowledge-studio/team.html).

## Ergebnisse

Nach Abschluss dieses Lernprogramms verfügen Sie über ein angepasstes Modell für maschinelles Lernen, das mit anderen {{site.data.keyword.watson}}-Services verwendet werden kann.

## Lerneinheit 1: Dokumente zum Annotieren hinzufügen
{: #tut_lessml1}

In dieser Lerneinheit erfahren Sie, wie Dokumente zu einem Arbeitsbereich in {{site.data.keyword.knowledgestudioshort}} hinzugefügt werden, die von Annotatorbenutzern annotiert werden können.

### Informationen zu diesem Vorgang

Weitere Informationen zum Hinzufügen von Dokumenten finden Sie unter [Dokument zu einem Arbeitsbereich hinzufügen](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projadd).

### Vorgehensweise

1. Laden Sie die Datei <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/documents-new.csv" download>`documents-new.csv`<img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link icon" class="style-scope doc-content"></a> in Ihren Computer herunter. Diese Datei enthält Beispieldokumente, die hochgeladen werden können.
1. Klicken Sie in Ihrem Arbeitsbereich in der Seitenleiste auf **Dokumente**.
1. Klicken Sie auf der Seite 'Dokumente' auf **Dokumentgruppen hochladen**.
1. Wählen Sie die Datei `documents-new.csv` auf Ihrem Computer aus und klicken Sie auf **Hochladen**. Die hochgeladene Datei wird in der Tabelle angezeigt.

### Nächste Schritte

Sie können nun den Korpus in mehrere Dokumentgruppen aufteilen und die Dokumentgruppen Annotatorbenutzern zuordnen.

## Lerneinheit 2: Annotationsgruppe erstellen
{: #wks_tutless_ml2}

In dieser Lerneinheit erfahren Sie, wie Annotationsgruppen in {{site.data.keyword.knowledgestudioshort}} erstellt werden.

### Informationen zu diesem Vorgang

Eine Annotationsgruppe ist eine Untergruppe von Dokumenten aus einer hochgeladenen Dokumentgruppe, die Sie einem Annotatorbenutzer zuordnen. Der Annotatorbenutzer annotiert die Dokumente in der Annotationsgruppe. Um später anhand der Scores für die Übereinstimmung der Annotatoren die von den einzelnen Annotatorbenutzern hinzugefügten Annotationen vergleichen zu können, müssen Sie mindestens zwei Annotatorbenutzer verschiedenen Annotationsgruppen zuordnen. Außerdem müssen Sie angeben, dass ein bestimmter Prozentsatz der Dokumente Überschneidungen zwischen den Gruppen aufweist.

> **Hinweis:** In einem echten Arbeitsbereich würden Sie so viele Annotationsgruppen wie nötig für die Anzahl der Annotatorbenutzer erstellen, die an diesem Arbeitsbereich arbeiten. In diesem Lernprogramm erstellen Sie lediglich zwei Annotationsgruppen. Wenn Sie nicht über mehrere Benutzer-IDs verfügen, können Sie beide Annotationsgruppen demselben Benutzer zuordnen.

Weitere Informationen zu Annotationsgruppen finden Sie unter [Annotationsgruppen erstellen und zuordnen](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projdocsets).

### Vorgehensweise

1. Klicken Sie in Ihrem Arbeitsbereich in der Seitenleiste auf **Dokumente**.
1. Klicken Sie auf **Annotationsgruppen erstellen**.

    Das Fenster 'Annotationsgruppen erstellen' wird geöffnet. In diesem Fenster werden standardmäßig die Basisgruppe (sie enthält alle Dokumente) und die Felder zum Angeben der Informationen für eine neue Annotationsgruppe angezeigt.

1. Klicken Sie auf **Neue Gruppe und Annotatorbenutzer hinzufügen**, um die Felder zum Definieren einer weiteren Annotationsgruppe hinzuzufügen. Durch mehrmaliges Klicken auf diese Option können Sie beliebig viele Annotationsgruppen hinzufügen. Für dieses Lernprogramm genügen zwei neue Gruppen.

    ![Screenshot der Seite 'Annotationsgruppen erstellen'](images/wks_tutdocset2.jpg)

1. Geben Sie in das Feld **Überschneidung** den Wert `100` ein. Dieser Wert gibt an, dass 100 Prozent der Dokumente aus der Basisgruppe in alle neuen Annotationsgruppen einbezogen werden sollen, damit sie von allen Annotatorbenutzern annotiert werden können.
1. Geben Sie für jede Annotationsgruppe, die Sie erstellen, die erforderlichen Informationen an.

    - Wählen Sie im Feld **Annotator** die Benutzer-ID eines Annotatorbenutzers aus, die der neuen Annotationsgruppe zugeordnet werden soll. Jede Annotationsgruppe sollte einem anderen Annotatorbenutzer zugeordnet werden.

        > **Hinweis:** Wenn Sie nur über eine einzige Administrator-ID verfügen, die für dieses Lernprogramm verwendet werden kann, ordnen Sie die betreffende Benutzer-ID allen Annotationsgruppen zu. In einem echten Arbeitsbereich können in der Regel mehrere Annotatorbenutzer zugeordnet werden, aber für die Zwecke dieses Lernprogramms kann der Administrator auch als Annotatorbenutzer agieren.

    - Geben Sie im Feld **Gruppenname** einen beschreibenden Namen für die Annotationsgruppe an (z. B. `Gruppe 1` oder `GruppeDave`).

1. Klicken Sie auf **Generieren**.

### Ergebnisse

Die neuen Annotationsgruppen werden erstellt und in der Registerkarte **Annotationsgruppen** auf der Seite 'Dokumente' angezeigt.

## Lerneinheit 3: Mit wörterverzeichnisbasiertem Annotator vorannotieren
{: #wks_tutless_ml3}

In dieser Lerneinheit herfahren Sie, wie ein wörterverzeichnisbasierter Annotator zum Vorannotieren von Dokumenten in {{site.data.keyword.knowledgestudioshort}} verwendet wird.

### Informationen zu diesem Vorgang

Das Vorannotieren von Dokumenten ist ein optionaler Schritt. Es lohnt sich, diesen Schritt auszuführen, da er die spätere Arbeit des Annotatorbenutzers erleichtert.

Weitere Informationen zum Vorannotieren mit wörterverzeichnisbasierten Annotatoren finden Sie unter [Dokumente mit dem wörterverzeichnisbasierten Vorannotator vorannotieren](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannot).

### Vorgehensweise

1. Klicken Sie in Ihrem Arbeitsbereich in der Seitenleiste **Assets & Tools** > **Vorannotatoren** auf **Wörterverzeichnisse verwalten**.

  Das Wörterverzeichnis `Testwörterverzeichnis` wird geöffnet.

1. Wählen Sie in der Liste **Entitätstyp** den Eintrag **ORGANISATION** aus, um den Entitätstyp ORGANISATION dem Wörterverzeichnis `Testwörterverzeichnis` zuzuordnen, das Sie in der Lerneinheit [Wörterverzeichnis hinzufügen](/docs/services/watson-knowledge-studio/tutorials-create-project.html#wks_tutless4) des Lernprogramms *Arbeitsbereich erstellen* erstellt haben.
1. Klicken Sie auf den rückwärts gerichteten Pfeil oben links, um zur Seite 'Vorannotatoren' zurückzukehren, und klicken Sie auf **Diesen Vorannotator anwenden**.
1. Klicken Sie auf der Seite 'Annotator ausführen' auf die entsprechenden Kontrollkästchen, um beide Annotationsgruppen (die Basisgruppe nicht eingeschlossen) auszuwählen, die Sie zuvor erstellt haben .
1. Klicken Sie auf **Ausführen**.

    ![Dieser Screenshot zeigt die Seite 'Annotator ausführen'. Die Schaltfläche 'Ausführen' ist hervorgehoben.](images/wks_tutanno3.jpg)

### Ergebnisse

Die Dokumente in den ausgewählten Gruppen werden mit dem von Ihnen erstellten wörterverzeichnisbasierten Annotator vorannotiert. Später können Sie denselben Annotator zum Vorannotieren weiterer Dokumentgruppen verwenden, indem Sie auf **Diesen Vorannotator anwenden** klicken.

## Lerneinheit 4: Annotationstask erstellen
{: #wks_tutless_ml4}

In dieser Lerneinheit erfahren Sie, wie Annotationstasks verwendet werden, um den Arbeitsfortschritt der Annotatorbenutzer in {{site.data.keyword.knowledgestudioshort}} zu überwachen.

### Informationen zu diesem Vorgang

Weitere Informationen zu Annotationstasks finden Sie unter [Annotationstask erstellen](/docs/services/watson-knowledge-studio/annotate-documents.html#wks_hatask).

### Vorgehensweise

1. Wählen Sie in Ihrem Arbeitsbereich in der Seitenleiste **Assets & Tools** > **Dokumente** die Registerkarte **Tasks** aus.
1. Klicken Sie auf der Seite 'Tasks' auf **Task hinzufügen**.
1. Geben Sie die Details für die Task an:

    - Geben Sie in das Feld **Taskname** die Zeichenfolge `Test` ein.
    - Wählen Sie im Feld **Termin** ein Datum aus, das in der Zukunft liegt.

1. Klicken Sie auf **Erstellen**.
1. Klicken Sie im Fenster 'Annotationsgruppen für Task hinzufügen' auf die entsprechenden Kontrollkästchen, um beide Annotationsgruppen auszuwählen, die Sie in [Lerneinheit 3: Mit wörterverzeichnisbasiertem Annotator vorannotieren](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml3) erstellt haben. Dadurch wird angegeben, dass innerhalb dieser Task beide Annotationsgruppen von den zugeordneten Annotatorbenutzern annotiert werden müssen.
1. Klicken Sie auf **Task erstellen**.
1. Wenn Sie später den Arbeitsfortschritt der Annotatorbenutzer anzeigen möchten, können Sie auf die Task klicken, um sie zu öffnen.

## Lerneinheit 5: Dokumente annotieren
{: #wks_tutless_ml5}

In dieser Lerneinheit erfahren Sie, wie der Ground Truth-Editor zum Annotieren von Dokumenten in {{site.data.keyword.knowledgestudioshort}} verwendet wird.

### Informationen zu diesem Vorgang

Weitere Informationen zur Arbeit der Annotatorbenutzer finden Sie unter [Annotieren mit dem Ground Truth-Editor](/docs/services/watson-knowledge-studio/user-guide.html#wks_hagte).

### Vorgehensweise

1. Melden Sie sich bei {{site.data.keyword.knowledgestudioshort}} als ein zugeordneter Annotatorbenutzer der Annotationstask an, die Sie in der [Lerneinheit 4: Annotationstask erstellen](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml4) erstellt haben.

    > **Hinweis:** Wenn Sie in diesem Lernprogramm nur auf eine einzige Benutzer-ID zugreifen können, können Sie unter der betreffenden Benutzer-ID auch die Aufgaben eines Annotatorbenutzers ausführen. Beachten Sie jedoch, dass in einem echten Arbeitsbereich mehrere verschiedene Annotatorbenutzer mit der Rolle 'HomanAnnotator' Annotationen hinzufügen.

1. Öffnen Sie den Arbeitsbereich `Mein Arbeitsbereich`.
1. Klicken Sie in der Seitenleiste auf **Dokumentannotation** > **Beziehungen**.
1. Öffnen Sie die Annotationstask `Test`, die Sie in der [Lerneinheit 4: Annotationstask erstellen](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml4) erstellt haben.
1. Blättern Sie zum Dokument *Technology - gmanews.tv* und klicken Sie auf das Dokument, um es zum Annotieren zu öffnen. Beachten Sie, dass der Begriff `IBM` bereits mit dem Entitätstyp ORGANISATION annotiert wurde. Diese Annotation wurde vom wörterverzeichnisbasierten Vorannotator in der [Lerneinheit 2: Annotationsgruppen erstellen](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html#wks_tutless_ml2) hinzugefügt. Diese Vorannotation ist korrekt und muss nicht geändert werden.

    ![Dieser Screenshot zeigt ein geöffnetes Dokument mit einer Vorannotation für 'IBM'.](images/wks_tut_preannotation.png)

1. So annotieren Sie eine Erwähnung:

    1. Klicken Sie auf das Symbol **Erwähnungen**, um mit dem Annotieren von Erwähnungen zu beginnen.
    1. Wählen Sie im Hauptteil des Dokuments den Text `Thomas Watson` aus.
    1. Klicken Sie in der Liste der Entitätstypen auf **PERSON**. Der Entitätstyp PERSON wird auf die ausgewählte Erwähnung angewendet.

        ![Dieser Screenshot zeigt, dass der Entitätstyp PERSON auf die Erwähnung 'Thomas Watson' angewendet wurde.](images/wks_tut_annotatemention3.png)

1. Klicken Sie in der Seitenleiste auf **Dokumentannotation** > **Beziehungen**, um mit dem Annotieren von Beziehungen zu beginnen.
1. Wählen Sie die Erwähnungen `Thomas Watson` und `IBM` in der angegebenen Reihenfolge aus. Um eine Erwähnung auszuwählen, klicken Sie auf die Entitätstypbeschriftung über dem Text.
1. Klicken Sie in der Liste der Beziehungstypen auf **founderOf**. Die beiden Erwähnungen werden durch eine Beziehung 'GründerVon' verbunden.

    ![Dieser Screenshot zeigt zwei Erwähnungen, die durch den Beziehungstyp 'GründerVon' verbunden sind.](images/wks_tut_annotaterelation.png)

1. Wählen Sie im Statusmenü die Option **Abgeschlossen** aus und klicken Sie anschließend auf die Schaltfläche **Speichern**.
1. Kehren Sie zur Liste der Dokumente zurück und klicken Sie auf **Alle Dokumente abschicken**, um die Dokumente zum Genehmigen einzureichen.

    > **Hinweis:** In einer realen Situation werden vor dem Abschicken viele weitere Annotationen erstellt und alle Dokumente in der Gruppe bearbeitet.

1. Melden Sie sich bei {{site.data.keyword.knowledgestudioshort}} als ein Annotatorbenutzer an, der einer anderen Dokumentgruppe in der Annotationstask zugeordnet ist.
1. Fügen Sie die gleichen Annotationen im Dokument *Technology - gmanews.tv* hinzu, aber verwenden Sie nun die Beziehung 'beschäftigtBei' anstelle der Beziehung 'GründerVon'.

  Die Anmeldung mit einer anderen Benutzer-ID ist erforderlich, um in der nächsten Lerneinheit die Übereinstimmung zwischen Annotatoren zu veranschaulichen. Vervollständigen Sie die Annotierung und klicken Sie auf **Alle Dokumente abschicken**.

## Lerneinheit 6: Übereinstimmung der Annotatoren analysieren
{: #wks_tutless_ml6}

In dieser Lerneinheit erfahren Sie, wie die Arbeitsergebnisse mehrerer Annotatorbenutzer in {{site.data.keyword.knowledgestudioshort}} verglichen werden.

### Informationen zu diesem Vorgang

Um festzustellen, ob verschiedene Annotatorbenutzer die Dokumente mit Überschneidungen konsistent annotieren, überprüfen Sie die Scores für die Übereinstimmung der Annotatoren (Inter-Annotator Agreement, `IAA`).

Bei der Berechnung der IAA-Scores durchsucht {{site.data.keyword.knowledgestudioshort}} alle Dokumente mit Überschneidungen in allen Dokumentgruppen der Task, unabhängig vom Status der Dokumentgruppen. Die IAA-Scores zeigen, wie unterschiedlich die Erwähnungen, Beziehungen und Koreferenzketten von verschiedene Annotatorbenutzer annotiert wurden. Es wird empfohlen, die IAA-Scores regelmäßig zu überprüfen, um sicherzustellen, dass die Annotatorbenutzer konsistente Annotationen erstellen.

In diesem Lernprogramm wurden alle Dokumentgruppen von den Annotatorbenutzern zur Genehmigung eingereicht. Wenn die Scores für die Übereinstimmung der Annotatoren akzeptabel sind, können Sie die Dokumentgruppen genehmigen. Wenn Sie eine Dokumentgruppe ablehnen, wird sie zur Optimierung an den Annotatorbenutzer zurückgegeben.

### Vorgehensweise

1. Melden Sie sich bei {{site.data.keyword.knowledgestudioshort}} als Administrator an, wählen Sie **Assets & Tools** > **Dokumente** aus und klicken Sie auf die Task `Test`.

  In der Spalte **Status** wird angezeigt, dass die Dokumentgruppen eingereicht wurden.

1. Klicken Sie auf **Übereinstimmung der Annotatoren berechnen**.
1. Rufen Sie die IAA-Scores für Erwähnungen, Beziehungen und Koreferenzketten auf, indem Sie auf das erste Menü klicken. Sie können auch die Übereinstimmung für einzelne Annotatorbenutzerpaare anzeigen. Beispiel: Sie können alle von Dave hinzugefügten Annotationen mit allen von Phil hinzugefügten Annotationen vergleichen. Außerdem können Sie die Übereinstimmung für bestimmte Dokumente anzeigen. Beispiel: Sie können die Annotation von Dave für ein Dokument mit den Annotation von Phil für das gleiche Dokument vergleichen. Im Allgemeinen sollte der Score-Wert bei 0,8 liegen (der Wert 1 bedeutet absolute Übereinstimmung). Da in diesem Lernprogramm nur zwei Entitätstypen annotiert wurden, ist für die meisten Entitätstypen der Score 'N/A' (nicht zutreffend) angegeben, d. h. aufgrund fehlender Informationen kann kein Score vergeben werden.

    *Abbildung 1. Scores für die Übereinstimmung der Annotatorbenutzer Dave and Phil überprüfen*

    ![Dieser Screenshot zeigt die Scores für die Übereinstimmung der Annotatoren für eine Task](images/wks_tutiaa2.gif)

1. Nach dem Überprüfen der Scores können Sie entscheiden, ob Sie Dokumentgruppen, die den Status `Abgeschickt` aufweisen, genehmigen oder ablehnen wollen. Nachdem eine Dokumentgruppe abgeschickt wurde, wird neben dem Namen der Gruppe ein Kontrollkästchen angezeigt. Führen Sie eine der folgenden Aktionen aus:

    - Wenn die Scores für eine Dokumentgruppe akzeptabel sind, wählen Sie das Kontrollkästchen aus und klicken Sie auf **Akzeptieren**. Dokumente, die keine Überschneidungen mit anderen Dokumentgruppen aufweisen, werden in die Ground Truth hochgestuft. Dokumente, die Überschneidungen aufweisen, müssen zuerst eine Beurteilung durchlaufen, damit die Konflikte behoben werden können. Akzeptieren Sie für dieses Lernprogramms beide Dokumentgruppen. 
    - Wenn die Scores für eine Dokumentgruppe nicht akzeptabel sind, wählen Sie das Kontrollkästchen aus und klicken Sie auf **Ablehnen**. Das betreffende Dokument muss vom Annotatorbenutzer erneut bearbeitet werden, um die Annotationen zu verbessern.

### Ergebnisse

Beim Auswerten der Scores für die Übereinstimmung der Annotatoren konnten Sie erkennen, dass dasselbe Dokument von verschiedenen Annotatorbenutzerpaaren annotiert wurde. Wenn der Score für die Übereinstimmung der Annotatoren akzeptabel war, haben Sie die betreffende Dokumentgruppe akzeptiert.

## Lerneinheit 7: Konflikte in annotierten Dokumenten beurteilen
{: #wks_tutless_ml7}

In dieser Lerneinheit erfahren Sie, wie Konflikte in Dokumenten beurteilt werden, die Überschneidungen zwischen Dokumentgruppen in {{site.data.keyword.knowledgestudioshort}} aufweisen.

### Informationen zu diesem Vorgang

Wenn Sie eine Dokumentgruppe genehmigen, werden nur diejenigen Dokumente, die keine Überschneidungen mit anderen Dokumentgruppen aufweisen, in die Ground Truth hochgestuft. Wenn ein Dokument Überschneidungen mit mehreren Dokumentgruppen aufweist, müssen Sie alle Annotationskonflikte beurteilen und beheben, bevor das Dokument in die Ground Truth hochgestuft werden kann.

### Vorgehensweise

1. Melden Sie sich bei {{site.data.keyword.knowledgestudioshort}} als Administrator an, wählen Sie **Assets & Tools** > **Dokumente** aus und klicken Sie auf die Task `Test`.
1. Stellen Sie sicher, dass beide Dokumentgruppen genehmigt wurden.
1. Klicken Sie auf **Dokumente mit Überschneidungen auf Konflikte prüfen**.

    Es wird angezeigt, welche Dokumente mit Überschneidungen von mehr als einem Annotatorbenutzer annotiert wurden.

1. Um festzustellen, ob Konflikte zwischen den Annotationen der verschiedenen Annotatorbenutzer bestehen, klicken Sie auf **Auf Konflikte prüfen**.
1. Im Beurteilungsmodus wird angezeigt, wie viele Annotationen Konflikte aufweisen, und Sie können Annotationen entfernen oder ersetzen, bevor Sie die Dokumente in die Ground Truth hochstufen.
1. Für die Zwecke dieses Lernprogramms können Sie davon ausgehen, dass Sie alle Konflikte behoben und die Änderungen akzeptiert haben. Klicken Sie auf **In Ground Truth hochstufen**. Wiederholen Sie diese Schritte, um Konflikte in der zweiten Dokumentgruppe zu beheben.

    Alternativ können Sie ein Dokument in die Ground Truth hochstufen, indem Sie auf der Seite 'Dokumente' auf **Akzeptieren** klicken.

### Ergebnisse

Nachdem Sie die Annotationskonflikte behoben und die Dokumente in die Ground Truth hochgestuft haben, können Sie die Dokumente zum Trainieren des Modells für maschinelles Lernen verwenden.

## Lerneinheit 8: Ein Modell für maschinelles Lernen erstellen
{: #wks_tutless_ml8}

In dieser Lerneinheit erfahren Sie, wie ein Modell für maschinelles Lernen in {{site.data.keyword.knowledgestudioshort}} erstellt wird.

### Informationen zu diesem Vorgang

Beim Erstellen eines Modells für maschinelles Lernen wählen Sie die Dokumentgruppen aus, die Sie zum Trainieren des Modells verwenden möchten. Außerdem geben Sie an, welcher Prozentsatz der Dokumente als Trainingsdaten, Testdaten und Blinddaten verwendet werden soll. Nur Dokumente, die durch Beurteilung oder Genehmigung in die Ground Truth hochgestuft wurden, können zum Trainieren des Modells für maschinelles Lernen verwendet werden.

### Vorgehensweise

1. Melden Sie sich bei {{site.data.keyword.knowledgestudioshort}} als Administrator an.
1. Klicken Sie in der Seitenleiste **Modellverwaltung** > **Leistung** auf **Trainieren und auswerten**.
1. Wählen Sie die Dokumentgruppen aus, die zum Erstellen eines Modells für maschinelles Lernen verwendet werden sollen. Klicken Sie auf das Häkchen neben den Namen der betreffenden Dokumentgruppen.
1. Wählen Sie die beiden Annotationsgruppen zum Erstellen Ihrer Test-, Trainings- und Blinddaten aus. Klicken Sie anschließend auf **Trainieren &amp; auswerten**.

    > **Hinweis:** Das Trainieren kann abhängig von der Anzahl der durch Annotatorbenutzer hinzugefügten Annotationen und der Gesamtzahl der Wörter in den Dokumenten von mehr als zehn Minuten bis mehrere Stunden dauern.

1. Nachdem das Modell für maschinelles Lernen trainiert wurde, können Sie es exportieren oder detaillierte Informationen zur Leistung des Modells anzeigen, indem Sie auf den Link **Detaillierte Statistik** klicken, der über jedem Diagramm angezeigt wird.
1. Um die Seite für Trainings-, Test- und Blinddaten anzuzeigen, klicken Sie auf die Schaltfläche **Trainieren und auswerten**.
1. Um die Dokumente anzuzeigen, die von den Annotatorbenutzern bearbeitet wurden, klicken Sie auf **Ground Truth anzeigen**.
1. Um die Annotationen anzuzeigen, die von dem trainierten Modell für maschinelles Lernen in derselben Dokumentgruppe hinzugefügt wurden, klicken Sie auf **Decodierungsergebnisse anzeigen**.
1. Um Details zu Genauigkeit, Vollständigkeit und F1-Scores für das Modell für maschinelles Lernen anzuzeigen, wählen Sie die Seite 'Leistung' aus.
1. Klicken Sie auf den Link **Detaillierte Statistik**, der über jedem Diagramm angezeigt wird. Auf diesen Statistikseiten können Sie mithilfe der entsprechenden Optionsfelder die Scores für Erwähnungen, Beziehungen und Koreferenzketten anzeigen.

    Zum Analysieren der Leistung können Sie eine Zusammenfassung der Statistikdaten für Entitätstypen, Beziehungstypen und Koreferenzketten anzeigen. Außerdem können Sie die Statistikdaten analysieren, die in einer Fehlermatrix dargestellt werden, indem Sie **Fehlermatrix** in dem Menü auswählen, das standardmäßig die **Zusammenfassung** anzeigt. Anhand der *Fehlermatrix* können Sie die vom Modell für maschinelles Lernen hinzugefügten Annotationen mit den Annotationen in der Ground Truth vergleichen.

    > **Hinweis:** In diesem Lernprogramm haben Sie Dokumente nur mit einem einzigen Wörterverzeichnis für Organisationen annotiert. Daher wird für die meisten Entitätstypen der Score `0` oder `N/A` (nicht zutreffend) angezeigt, mit Ausnahme des Typs `ORGANISATION`. Die Scores sind niedrig, doch das war zu erwarten, da weder Annotationen von Annotatorbenutzern noch Korrekturen vorgenommen wurden.

    *Abbildung 2. Optionen auf der Seite 'Statistik' für ein Modell für maschinelles Lernen*

    ![Dieser Screenshot zeigt die Seite 'Statistik'](images/wks_tutanno9.gif)

1. Wählen Sie in der Seitenleiste **Modellverwaltung** > **Versionen** aus. Auf der Seite 'Versionen' können Sie einen Snapshot des Modells und der für die Erstellung des Modells verwendeten Ressourcen (mit Ausnahme von Wörterverzeichnissen und Annotationstasks) erstellen. Sie können beispielsweise einen Snapshot erstellen, bevor Sie das Modell erneut trainieren. Wenn die Leistungswerte nach dem erneuten Trainieren schlechter sind, können Sie die frühere Version hochstufen und die Versionen mit den schlechteren Ergebnissen löschen.

### Ergebnisse

Sie haben ein Modell für maschinelles Lernen erstellt, trainiert und die Leistung des Modells durch Annotieren von Test- und Blinddaten ausgewertet. Durch Überprüfen der Leistungsmetriken können Sie Methoden finden, um die Genauigkeit des Modells für maschinelles Lernen zu verbessern.

## Zusammenfassung des Lernprogramms
{: #wks_tutml_sum}

Beim Kennenlernen von {{site.data.keyword.knowledgestudioshort}} haben Sie ein Modell für maschinelles Lernen erstellt.

### Eingeübte Lerninhalte

Beim Durcharbeiten dieses Lernprogramms haben Sie die folgenden Konzepte kennengelernt:

- Dokumentgruppen
- Modelle für maschinelles Lernen
- Annotatorbenutzertasks
- Übereinstimmung der Annotatoren und Beurteilung
