---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-13"

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

Diese Dokumentation bezieht sich auf {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Die Dokumentation für die Vorgängerversion {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace kann über [diesen Link ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/docs/services/knowledge-studio/preannotation.html){: new_window} aufgerufen werden.
{: tip}

# Annotationsprozess beschleunigen
{: #preannotation}

Sie können die Arbeit der Annotatorbenutzer vereinfachen, indem Sie die Dokumente in einem Arbeitsbereich vorannotieren. Ein Vorannotator ist ein Wörterverzeichnis, ein regelbasiertes Modell oder ein Modell für maschinelles Lernen in {{site.data.keyword.knowledgestudioshort}}, das Sie anwenden können, um Erwähnungen automatisch zu finden und zu annotieren.
{: shortdesc}

Das Vorannotieren erleichtert die Arbeit der Annotatorbenutzer, indem die offensichtlichen Annotationen vorab verarbeitet und das Annotieren der Dokumente beschleunigt wird.

Die zum Vorannotieren der Dokumente verwendete Methode verursacht keinerlei Einschränkungen für die Verwendung des resultierenden Modells. Beispiel: Wenn Sie den Service {{site.data.keyword.nlushort}} zum Vorannotieren von Dokumenten verwenden, bedeutet dies nicht, dass Sie das von Ihnen erstellte Modell für maschinelles Lernen im Service {{site.data.keyword.nlushort}} bereitstellen müssen. Die Vorannotierung dient lediglich dazu, den Annotierungsprozess durch die Annotationsbenutzer zu beschleunigen.

## Wichtige Hinweise
{: #preannotation_notes}

- Wenden Sie auf keinen Fall einen Vorannotator auf Dokumente an, die bereits von Annotatorbenutzern annotiert wurden, da sonst die von den Annotatorbenutzern hinzugefügten Annotationen verloren gehen.
- Sie können nur einen Vorannotator auf Dokumente anwenden. Wenn Sie einen Vorannotator anwenden und danach einen zweiten Vorannotator, entfernt der zweite Vorannotator die vom ersten Vorannotator hinzugefügten Annotationen. Wählen Sie die Methode zum Vorannotieren aus, die für Ihren Anwendungsfall am besten geeignet ist, und wenden Sie nur diesen einen Vorannotator an.

## Methoden für die Vorannotation
{: #preannotation_methods}

Die folgenden Vorannotatoren stehen zur Verfügung:

- **{{site.data.keyword.nlushort}}**

    Ein Vorannotator zum automatischen Finden von Entitätserwähnungen in Ihren Dokumenten. Wenn Ihre Quellendokumente Allgemeinwissen enthalten, ist dieser Vorannotator eine gute Wahl. Wenn Sie mit hoch spezialisierten Dokumenten aus einem bestimmten Fachgebiet arbeiten (z. B. Patentrecht) ist der wörterverzeichnisbasierte Vorannotator oder ein regelbasiertes Modell möglicherweise die bessere Wahl.

- **Wörterverzeichnis**

    Verwendet ein Wörterverzeichnis mit Begriffen, die Sie angeben und einem Entitätstyp zuordnen, um Erwähnungen dieses Entitätstyps in den Dokumenten zu finden. Dies ist die beste Wahl für Fachgebiete mit eindeutiger oder spezialisierter Terminologie, da dieser Vorannotator den Kontext, in dem ein Begriff verwendet wird, nicht auf die gleiche Weise analysiert, wie ein Vorannotator für maschinelles Lernen. Stattdessen wird vorausgesetzt, dass der Begriff eine eigenständige und erkennbare Bedeutung hat, und zwar unabhängig von dem Kontext, in dem er verwendet wird. Beispiel: *Asbest* lässt sich leichter einem Entitätstyp (z. B. mineralisches Material) zuordnen als der Begriff *Squash*, der ein Saftgetränk, eine Sportart oder ein Verb mit der Bedeutung 'zerdrücken'  bezeichnen kann.

- **Maschinelles Lernen**

    Verwendet ein Modell für maschinelles Lernen, um Dokumente automatisch zu annotieren. Diese Option ist nur verfügbar, wenn Sie bereits ein Modell für maschinelles Lernen mit {{site.data.keyword.knowledgestudioshort}} erstellt haben. Wenn Sie eine neue Dokumentgruppe hinzufügen, können Sie den bereits erstellten Annotator für maschinelles Lernen verwenden, um die neuen Dokumente zu annotieren. Wenn die neue Dokumentgruppe Ähnlichkeiten mit den Dokumenten aufweist, die ursprünglich zum Trainieren des Annotators für maschinelles Lernen verwendet wurden, eignet sich dieser Annotator vermutlich am besten zum Vorannotieren.

- **Regel**

    Verwendet ein regelbasiertes Modell zum automatischen Annotieren von Dokumenten. Diese Option ist nur verfügbar, wenn Sie bereits ein regelbasiertes Modell mit {{site.data.keyword.knowledgestudioshort}} erstellt haben. Wenn Ihre Dokumente häufig vorkommende Tokenmuster enthalten, aus der die Bedeutung abgeleitet werden kann, dann ist dieses Modell wahrscheinlich eine gute Wahl. Es kann einen Teil der Funktionalität des wörterverzeichnisbasierten Vorannotators einschließen, wenn Sie diese Funktionalität aktivieren, indem Sie Klassentypen für Begriffe im Wörterverzeichnis angeben, die im Dokument erkannt werden sollen.

Alternativ können sie bereits annotierte Dokumente hochladen und als Ausgangspunkt zum Trainieren des Modells für maschinelles Lernen verwenden. Ein Vorannotator darf nicht auf annotierte Dokumente angewendet werden, die Sie hochladen. Andernfalls werden die vorhandenen Annotationen in den Dokumenten entfernt und durch die Annotationen des Vorannotators ersetzt.

> **Hinweis:** Ein Vorannotator *kann* auf Dokumente angewendet werden, die zur Ground Truth für den aktuellen Arbeitsbereich hinzugefügt wurden. Es werden keine Annotationen entfernt, die im aktuellen Arbeitsbereich zu Dokumenten hinzugefügt sowie überprüft, akzeptiert und in die Ground Truth hochgestuft wurden.

## Dokumente mit {{site.data.keyword.nlushort}} vorannotieren
{: #wks_preannotnlu}

Sie können mit dem Service {{site.data.keyword.nlushort}} Dokumente vorannotieren, die Sie zu Ihrem Korpus hinzufügen.

### Vorbereitungen
{: #wks_preannotnlu_prereqs}

Stellen Sie fest, ob der Vorannotator für {{site.data.keyword.nlushort}} in Ihrem Anwendungsfall von Nutzen sein kann. Prüfen Sie die [Liste der vom Service {{site.data.keyword.nlushort}} unterstützten Entitätstypen und Subtypen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/docs/services/natural-language-understanding/entity-types.html){: new_window}, um festzustellen, ob sich diese Typen mit den Typen in Ihrem Typsystem überschneiden. Wenn dies zutrifft, fahren Sie mit der hier beschriebenen Prozedur fort. Ist dies nicht der Fall, verwenden Sie einen anderen Vorannotator.

### Informationen zu diesem Vorgang
{: #wks_preannotnlu_about}

Der Service {{site.data.keyword.nlushort}} ermöglicht die Textanalyse durch die Verarbeitung natürlicher Sprache. Wenn Sie den Vorannotator für {{site.data.keyword.nlushort}} verwenden, wird der Service {{site.data.keyword.nlushort}} aufgerufen, um Entitäten in Ihren Dokumenten zu finden und zu annotieren.

Sie müssen die Entitätstypen angeben, die der Service suchen soll, indem Sie die {{site.data.keyword.nlushort}}-Entitätstypen den entsprechenden {{site.data.keyword.knowledgestudioshort}}-Entitätstypen zuordnen, die Sie zum {{site.data.keyword.knowledgestudioshort}}-Typsystem hinzugefügt haben. Nur Erwähnungen der von Ihnen zugeordneten Entitätstypen werden gefunden und annotiert.

### Vorgehensweise
{: #wks_preannotnlu_procedure}

Führen Sie die folgenden Schritte aus, um den Service {{site.data.keyword.nlushort}} zum Vorannotieren von Dokumenten zu verwenden:

1. Melden Sie sich als {{site.data.keyword.knowledgestudioshort}}-Administrator an und wählen Sie Ihren Arbeitsbereich aus.
1. Wählen Sie die Registerkarte **Modell für maschinelles Lernen** > **Vorannotation** > **Natural Language Understanding** aus.
1. Klicken Sie auf **Bearbeiten**, um die auf der Seite **Entitätstypen** definierten Entitätstypen den entsprechenden Entitätstypen von {{site.data.keyword.nlushort}} zuzuordnen.

    - Die Dropdown-Liste der Entitätstypen von {{site.data.keyword.nlushort}} wird vorab mit Entitätstypen gefüllt, die von dem Service {{site.data.keyword.nlushort}} erkannt werden.
    - Sie müssen mindestens einen Entitätstyp zuordnen.
    - Sie dürfen keinen Entitätstyp von {{site.data.keyword.nlushort}} einer {{site.data.keyword.knowledgestudioshort}}-Entitätsrolle zuordnen. Nur {{site.data.keyword.knowledgestudioshort}}-Entitätstypen können zugeordnet werden.
    - Sie können mehr als einen Entitätstyp von {{site.data.keyword.nlushort}} einem einzelnen {{site.data.keyword.knowledgestudioshort}}-Entitätstyp zuordnen und umgekehrt. Beispielsweise sind die folgenden Zuordnungen zulässig:

    <table summary="Beispiel für das Zuordnen von Entitätstypen">
    <caption>Tabelle 1. Beispiel für das Zuordnen von Entitätstypen</caption>
      <tr>
        <th style="vertical-align:bottom; text-align"left" id="d20428e292">Watson Knowledge Studio Entity Type</th>
        <th style="vertical-align:bottom; text-align"left" id="d20428e298">Entitätstyp von {{site.data.keyword.nlushort}}</th>
      </tr>
      <tr>
        <td headers="d20428e292">
          ENTWICKLER<br/>
          SCIENTIST
        </td>
        <td headers="d20428e298">
          Person
        </td>
      </tr>
      <tr>
        <td headers="d20428e292">
          POSITION
        </td>
        <td headers="d20428e298">
          StadtDorf<br/>
          Land
        </td>
      </tr>
    </table>
    {: #wks_preannotnlu__datasimpletable_cm1_y3g_fx}

1. Nachdem alle Entitätstypen zugeordnet wurden, die Sie anwenden möchten, klicken Sie auf **Diesen Vorannotator anwenden**.

    Die Schaltfläche **Diesen Vorannotator anwenden** ist erst verfügbar, wenn Sie mindestens einen Entitätstyp zugeordnet haben.

1. Wählen Sie das Kontrollkästchen für jede Dokumentgruppe aus, die Sie vorannotieren möchten.

    Wenn Sie diesen Vorannotator zum ersten Mal ausführen, prüfen Sie zunächst, dass der Vorannotator die Erwähnungen der zugeordneten Entitäten wie erwartet finden kann. Erstellen Sie eine Dokumentgruppe mit mindestens einem repräsentativen Dokument aus jeder eigenständigen Datenquelle.
    {: tip}

1. Klicken Sie auf **Ausführen**.

    Wenn Sie eine Validierungsprüfung für den Vorannotator ausführen möchten, öffnen Sie die annotierten Dokumente und überprüfen Sie die hinzugefügten Annotationen. Vergewissern Sie sich, dass eine ausreichende Anzahl zutreffender Annotationen erstellt wurde. Wenn die Annotationen zutreffend sind, können Sie den Annotator erneut auf eine größere Menge von Dokumentgruppen oder auf umfangreichere Dokumentgruppen anwenden. Wenn die Annotationen nicht zutreffend sind, ziehen Sie in Betracht, Ihren Entitäten andere Entitätstypen von {{site.data.keyword.nlushort}} zuzuordnen. Wenn die Typen keine natürlichen Überschneidungen aufweisen, dann ist der Vorannotator für {{site.data.keyword.nlushort}} nicht die beste Wahl für Ihren Anwendungsfall.

    Die Vorannotierung wird auf einzelne Dokumente angewendet, und zwar unabhängig davon, welchen Dokumentgruppen ein Dokument angehört. Ein Dokument, das Überschneidungen mit einer ausgewählten Dokumentgruppe und einer nicht ausgewählten Dokumentgruppe aufweist, wird in beiden Dokumentgruppen vorannotiert.

1. Nachdem Sie den Vorannotator einmal ausgeführt haben, können Sie jederzeit auf **Diesen Vorannotator anwenden** klicken, um weitere Dokumente, die Sie zum Korpus hinzufügen, mit diesem Vorannotator zu bearbeiten.

    > **Einschränkung:** Wenn Sie die Typzuordnungsdefinition des Vorannotators von {{site.data.keyword.nlushort}} bearbeiten, müssen Sie die Annotationstasks, in denen die vorannotierten Dokumente enthalten sind, erneut erstellen. Vorannotationen auf der Basis der Änderungen, die Sie an der Vorannotatorzuordnung vorgenommen haben, können nicht auf Dokumentgruppen angewendet werden, die bereits einer Annotationstask zugeordnet sind.

### Ergebnisse
{: #wks_preannotnlu__export-warning}

Die aus Dokumenten, die durch den Service {{site.data.keyword.nlushort}} vorannotiert wurden, erstellte Ground Truth kann nicht sofort außerhalb von {{site.data.keyword.knowledgestudioshort}} verwendet werden. Sie können die Ground Truth (in nicht lesbarer Form) herunterladen und von einem {{site.data.keyword.knowledgestudioshort}}-Arbeitsbereich in einen anderen versetzen. Außerdem können Sie die Ground Truth weiter entwickeln und zum Erstellen eines Modells für maschinelles Lernen oder eines regelbasierten Modells verwenden, das für die Verwendung durch Services außerhalb von {{site.data.keyword.knowledgestudioshort}} bereitgestellt werden kann.

> **Einschränkung:** Dokumente, die mit {{site.data.keyword.nlushort}} vorannotiert wurden, werden unkenntlich gemacht und in einem nicht lesbaren Format heruntergeladen. Dabei werden alle Annotationen in diesen Dokumenten unkenntlich gemacht, einschließlich der Annotationen, die von Annotatorbenutzern hinzugefügt wurden.

**Zugehörige Informationen**:

[{{site.data.keyword.nlushort}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/watson/services/natural-language-understanding/){: new_window}

## Dokumente mit einem Wörterverzeichnis vorannotieren
{: #wks_preannot}

Als Hilfsmittel für die Annotationstasks der Annotatorbenutzer können Sie ein Wörterverzeichnis erstellen und zum Vorannotieren von Dokumenten verwenden, die Sie zum Korpus hinzufügen.

### Informationen zu diesem Vorgang
{: #wks_preannot_about}

Wenn ein Annotatorbenutzer mit dem Bearbeiten vorannotierter Dokumente beginnt, ist häufig bereits eine Reihe von Erwähnungen gemäß den Einträgen im Wörterverzeichnis mit Entitätstypen markiert. Der Annotatorbenutzer kann die vorannotierten Entitätstypen ändern oder entfernen und Entitätstypen für nicht annotierte Erwähnungen zuordnen. Beim Vorannotieren mithilfe eines Wörterverzeichnisses werden keine Beziehungen und Koreferenzen annotiert. Beziehungen und Koreferenzen müssen von Annotatorbenutzern annotiert werden.

**Hinweis**: In dieser Task wird gezeigt, wie ein bearbeitbares Wörterverzeichnis erstellt wird. Wenn Sie Dokumente hochladen und mit einem schreibgeschützten Wörterverzeichnis vorannotieren möchten, klicken Sie auf das **Menü**-Symbol neben der Schaltfläche **Wörterverzeichnis hochladen**. Wählen Sie **Wörterverzeichnis hochladen** aus.

### Vorgehensweise
{: #wks_preannot_procedure}

So können Sie ein bearbeitbares Wörterverzeichnis erstellen und Dokumente vorannotieren:

1. Melden Sie sich als {{site.data.keyword.knowledgestudioshort}}-Administrator an und wählen Sie Ihren Arbeitsbereich aus.
1. Wählen Sie die Seite **Assets** > **Wörterverzeichnisse** aus.
1. Klicken Sie auf **Wörterverzeichnis erstellen**, geben Sie einen Namen ein und klicken Sie anschließend auf **Speichern**.
1. Wählen Sie in der Liste **Entitätstyp** einen Entitätstyp aus, der dem Wörterverzeichnis zugeordnet werden soll.
3. Fügen Sie Einträge im Wörterverzeichnis hinzu oder laden Sie eine Datei mit Wörterverzeichniseinträgen hoch.
4. Klicken Sie auf **Modell für maschinelles Lernen** > **Vorannotation**.
5. Klicken Sie auf der Registerkarte **Wörterverzeichnisse** auf **Diesen Vorannotator anwenden**.
6. Wählen Sie das Kontrollkästchen für jede Dokumentgruppe aus, die Sie vorannotieren möchten, und klicken Sie auf **Ausführen**.

    Die Vorannotierung wird auf einzelne Dokumente angewendet, und zwar unabhängig davon, welchen Dokumentgruppen oder Annotationsgruppen ein Dokument angehört. Ein Dokument, das Überschneidungen mit einer ausgewählten Dokumentgruppe und einer nicht ausgewählten Dokumentgruppe aufweist, wird in beiden Dokumentgruppen vorannotiert.

7. Nachdem das Wörterverzeichnis erstellt wurde, können Sie jederzeit auf **Ausführen** klicken, um das Wörterverzeichnis zum Vorannotieren weiterer Dokumentgruppen zu verwenden, die Sie zum Korpus hinzufügen.

    > **Einschränkung:** Wenn Sie im Wörterverzeichnis Einträge hinzufügen oder entfernen, müssen Sie die Annotationstasks, in denen die vorannotierten Dokumentgruppen enthalten sind, erneut erstellen. Vorannotationen auf der Basis der Änderungen, die Sie an dem wörterverzeichnisbasierten Vorannotator vorgenommen haben, können nicht auf Annotationsgruppen angewendet werden, die bereits einer Annotationstask zugeordnet sind.

**Zugehörige Informationen**:

[Wörterverzeichnisse erstellen](/docs/services/watson-knowledge-studio/dictionaries.html)

[Einführung > Wörterverzeichnis hinzufügen](/docs/services/watson-knowledge-studio/tutorials-create-project.html#wks_tutless4)

## Dokumente mit dem Modell für maschinelles Lernen vorannotieren
{: #wks_preannotsire}

Sie können ein bestehendes Modell für maschinelles Lernen zum Vorannotieren von Dokumenten verwenden, die Sie zum Korpus hinzufügen.

### Informationen zu diesem Vorgang
{: #wks_preannotsire_about}

Nachdem etwa 10 bis 30 Dokumente annotiert wurden, kann ein Modell für maschinelles Lernen anhand der resultierenden Daten trainiert werden. Ein solches minimal trainiertes Modell sollte nicht in einer Produktionsumgebung verwendet werden. Es kann jedoch dazu verwendet werden, Dokumente vorab zu annotieren, um die Bearbeitung weiterer Dokumente durch die Annotatorbenutzer zu beschleunigen. Wenn Sie zum Beispiel nach dem Trainieren des Modells für maschinelles Lernen Dokumente zum Korpus hinzufügen, können Sie das Modell zum Vorannotieren der neuen Dokumentgruppen verwenden. Wenden Sie einen Vorannotator nicht auf Dokumente an, die von einem Annotatorbenutzer annotiert wurden. Vorannotatoren löschen die von Annotatorbenutzern hinzugefügten Annotationen.

### Vorgehensweise
{: #wks_preannotsire_procedure}

So können Sie ein bestehendes Modell für maschinelles Lernen zum Vorannotieren von Dokumenten verwenden:

1. Melden Sie sich als {{site.data.keyword.knowledgestudioshort}}-Administrator an und wählen Sie Ihren Arbeitsbereich aus.
2. Wählen Sie **Modell für maschinelles Lernen** > **Versionen** aus.
3. Um neue Dokumente vorab zu annotieren, klicken Sie auf **Dieses Modell ausführen**.
4. Wählen Sie das Kontrollkästchen für jede Dokumentgruppe aus, die Sie vorannotieren möchten, und klicken Sie auf **Ausführen**.

    Die Vorannotierung wird auf einzelne Dokumente angewendet, und zwar unabhängig davon, welchen Dokumentgruppen oder Annotationsgruppen ein Dokument angehört. Ein Dokument, das Überschneidungen mit einer ausgewählten Dokumentgruppe und einer nicht ausgewählten Dokumentgruppe aufweist, wird in beiden Dokumentgruppen vorannotiert.

5. Sie können jederzeit auf **Dieses Modell ausführen** klicken, um das Modell für maschinelles Lernen zum Vorannotieren weiterer Dokumentgruppen zu verwenden, die Sie zum Korpus hinzufügen.

## Dokumente mit dem regelbasierten Modell vorannotieren
{: #wks_preannotrule}

Sie können ein bestehendes regelbasiertes Modell zum Vorannotieren von Dokumenten verwenden, die Sie zum Korpus hinzufügen.

### Vorgehensweise
{: #wks_preannotrule_procedure}

Führen Sie die folgenden Schritte aus, um das regelbasierte Modell zum Vorannotieren von Dokumenten zu verwenden:

1. Melden Sie sich als {{site.data.keyword.knowledgestudioshort}}-Administrator an und wählen Sie Ihren Arbeitsbereich aus.
1. Wählen Sie die Registerkarte **Regelbasiertes Modell** > **Versionen** > **Regelbasiertes Modell** aus.
1. Falls noch nicht geschehen, klicken Sie auf **Entitätstypen und -klassen zuordnen**, um von Ihnen definierte Entitätstypen im {{site.data.keyword.knowledgestudioshort}}-Typsystem mindestens einer Klasse im regelbasierten Modell zuzuordnen.
2. Klicken Sie für jeden Entitätstyp, den Sie zuordnen möchten, auf **Bearbeiten**.

    - Die Dropdown-Liste in der Spalte **Klassenname** wird vorab mit Klassen gefüllt, die dem regelbasierten Modell zugeordnet sind.
    - Sie müssen mindestens einen Entitätstyp  einer Klasse zuordnen.

3. Klicken Sie auf der Registerkarte **Regelbasiertes Modell** auf **Dieses Modell ausführen**.

    Die Schaltfläche **Dieses Modell ausführen** ist erst verfügbar, wenn Sie mindestens einen Entitätstyp einer Klasse zugeordnet haben.

4. Wählen Sie die Dokumentgruppen oder Annotationsgruppen aus, die Sie vorab annotieren möchten. Stellen Sie sicher, dass die von Ihnen ausgewählten Gruppen keine Dokumente mit Annotationen von Annotatorbenutzern enthalten. Vorannotatoren löschen die von Annotatorbenutzern hinzugefügten Annotationen.
5. Klicken Sie auf **Ausführen**.

    Die Vorannotierung wird auf einzelne Dokumente angewendet, und zwar unabhängig davon, welchen Dokumentgruppen ein Dokument angehört. Ein Dokument, das Überschneidungen mit einer ausgewählten Dokumentgruppe und einer nicht ausgewählten Dokumentgruppe aufweist, wird in beiden Dokumentgruppen annotiert.

6. Sie können jederzeit auf **Dieses Modell ausführen** klicken, um dieses regelbasierte Modell zum Vorannotieren weiterer Dokumente zu verwenden, die Sie zum Korpus hinzufügen.

    > **Einschränkung:** Wenn Sie die Entitätstyp/Klasse-Zuordnung des regelbasierten Modells bearbeiten, müssen Sie die Annotationstasks, in denen die vorannotierten Dokumentgruppen enthalten sind, erneut erstellen. Vorannotationen auf der Basis der Änderungen, die Sie an der Vorannotatorzuordnung vorgenommen haben, können nicht auf Dokumentgruppen angewendet werden, die bereits einer Annotationstask zugeordnet sind.

## Vorannotierte Dokumente hochladen
{: #wks_uima}

Sie können das Trainieren Ihres Modells durch Hochladen von Dokumenten beschleunigen, die durch eine UIMA-Analyseengine vorannotiert wurden (UIMA = Unstructured Information Management Architecture).

Die vorannotierten Dokumente müssen das XMI-Serialisierungsformat der UIMA Common Analysis Structure (UIMA CAS XMI) aufweisen. Die ZIP-Datei, die Sie hochladen, muss die Deskriptordatei des UIMA-Typsystems enthalten und eine Datei zum Zuordnen der UIMA-Typen zu Entitätstypen in Ihrem {{site.data.keyword.knowledgestudioshort}}-Typsystem.

UIMA CAS XMI ist ein Standardformat von Apache UIMA. Anleitungen zum Erstellen von Dateien im korrekten Format aus analysierten Datensammlungen in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer werden bereitgestellt. Wenn Sie eine andere Implementierung von Apache UIMA verwenden, passen Sie diese Anleitungen für Ihre Zwecke an. Unabhängig von der Vorgehensweise beim Erstellen der XMI-Dateien sind die Voraussetzungen für die Erstellung der Typsystemzuordnungsdatei und der ZIP-Datei gleich.

Wenn Sie die importierten Dokumente Annotatorbenutzern zuweisen, werden die Dokumente im Ground Truth-Editor vorannotiert und eine Reihe von Erwähnungen ist möglicherweise bereits annotiert. Der Annotatorbenutzer kann sich daher verstärkt auf das Anwenden der Annotationsrichtlinien auf nicht markierte Erwähnungen konzentrieren. Alternativ können Sie die Bearbeitung durch Annotatorbenutzer überspringen und die vorannotierten Dokumente sofort zum Trainieren und Auswerten eines Modells für maschinelles Lernen verwenden.

### Analysierte Dokumente aus Watson Explorer Content Analytics exportieren
{: #wks_uimawexca}

Sie können Dokumente, die in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer Content Analytics durchsucht und analysiert wurden, exportieren und die analysierten Dokumente als XMI-Dateien in einen {{site.data.keyword.knowledgestudioshort}}-Arbeitsbereich hochladen.

#### Vorgehensweise
{: #wks_uima_procedure}

So rufen Sie analysierte Dokumente aus einer {{site.data.keyword.watson}} Explorer Content Analytics-Dokumentsammlung ab:

1. Öffnen Sie die Content Analytics-Administrationskonsole in einem Web-Browser.
1. Erweitern Sie in der Ansicht 'Sammlungen' die Sammlung, aus der Sie Dokumente exportieren möchten. Stellen Sie im Teilfenster 'Analysieren und indexieren' sicher, dass der Parsing- und Indexprozess aktiv ist und klicken Sie anschließend auf das Pfeilsymbol für **Analysierten Dokumentinhalt und Metadaten exportieren**.
1. Wählen Sie im Bereich **Exportoptionen für analysierte Dokumente** die Option **Dokumente als XML-Dateien exportieren** aus, wählen Sie das Kontrollkästchen **CAS im XMI-Format exportieren** aus, geben Sie den Ausgabepfad an, in den exportierte Daten geschrieben werden sollen, und klicken Sie auf **OK**.
1. Stoppen Sie die Parsing- und Indexservices für die Sammlung und führen Sie anschließend einen der folgenden Schritte aus:

    - Wenn die Sammlung bereits indexierte Dokumente enthält, die Sie zum Trainieren des Modells für maschinelles Lernen im Dokumentcache verwenden möchten, starten Sie die komplette Indexerstellung erneut.
    - Wenn die Sammlung keine indexierten Dokumente enthält, die Sie zum Trainieren des Modells für maschinelles Lernen verwenden möchten, laden Sie Dokumente hoch, konfigurieren Sie mindestens einen Crawler zum Durchsuchen der Dokumente und starten Sie den Crawler.

1. Überprüfen Sie im Bereich **Exportieren** den Status der Exportanforderung. Im Verarbeitungsfortschritt wird angegeben, wie viele Dokumente exportiert werden.
1. Wechseln Sie in den Ausgabeordner, den Sie beim Konfigurieren der Exportoptionen angegeben haben. Beim Exportieren von Dokumenten als XML-Dateien basiert der Name des Ausgabeordners auf der Zeitmarke des Exportvorgangs. Der Ausgabeordner enthält XMI-Dateien (`*.xmi`) und die Deskriptordatei des UIMA-Typsystems (`exportiertes_typsystem.xml`).

#### Nächste Schritte
{: #wks_uimawexca__preUIMAimport}

Sie müssen eine Zuordnung zwischen den UIMA-Typen und {{site.data.keyword.knowledgestudioshort}}-Entitätstypen definieren. Außerdem müssen Sie eine ZIP-Datei erstellen, die alle erforderlichen Dateien zum Hochladen der analysierten Daten in einen {{site.data.keyword.knowledgestudioshort}}-Arbeitsbereich enthält.

**Zugehörige Informationen**:

[Exportieren durchsuchter und analysierter Dokumente ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ad.doc/iiysatexportca.htm){: new_window}

[Ausgabepfade für exportierte Dokumente ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ad.doc/iiysaexportoutput.htm){: new_window}

### Analysierte Sammlung aus Content Analytics Studio exportieren
{: #wks_uimawexstudio}

Sie können eine Sammlung analysierter Dokumente aus {{site.data.keyword.watson}} Explorer Content Analytics Studio exportieren und die analysierten Dokumente als XMI-Dateien in ein {{site.data.keyword.knowledgestudioshort}}-Projekt hochladen.

#### Vorgehensweise
{: #wks_uimawexstudio_procedure}

So rufen Sie analysierte Dokumente aus einer Content Analytics Studio-Dokumentsammlung ab:

1. Starten Sie Content Analytics Studio und öffnen Sie das Studio-Projekt.
1. Klicken Sie mit der rechten Maustaste auf einen Ordner, der Dokumente enthält, die Sie zum Trainieren eines Modells für maschinelles Lernen verwenden möchten, und wählen Sie **Sammlung analysieren** aus.
1. Wählen Sie eine UIMA-Pipelinekonfigurationsdatei aus.
1. Wechseln Sie in die Analyseansicht für Dokumentsammlungen und klicken Sie auf das Symbol **Speichern**. Geben Sie den Ordner an, in den die gespeicherten Ergebnisse geschrieben werden sollen, und geben Sie den Dateinamen an.
1. Öffnen Sie den Ordner, den Sie angegeben haben. Die Dateierweiterung für gespeicherte Dateien lautet `.annotations`.
1. Kopieren Sie die Datei `.annotations` in Ihr lokales Dateisystem und ändern Sie die Dateierweiterung `.annotations` in `.zip`.
1. Extrahieren Sie alle Dateien aus der ZIP-Datei. Der extrahierte Inhalt umfasst XMI-Dateien (`*.xmi`), die Deskriptordatei des UIMA-Typsystems (`TypeSystem.xml`) und weitere Dateien.

#### Nächste Schritte
{: #wks_uimawexstudio_next}

Sie müssen eine Zuordnung zwischen den UIMA-Typen und {{site.data.keyword.knowledgestudioshort}}-Entitätstypen definieren. Außerdem müssen Sie eine ZIP-Datei erstellen, die alle erforderlichen Dateien zum Hochladen der analysierten Daten in einen {{site.data.keyword.knowledgestudioshort}}-Arbeitsbereich enthält.

### Entitätstypen den UIMA-Typen zuordnen
{: #wks_uimawexmap}

Vor dem Hochladen von XMI-Dateien in einen {{site.data.keyword.knowledgestudioshort}}-Arbeitsbereich müssen Sie Zuordnungen zwischen den UIMA-Typen und {{site.data.keyword.knowledgestudioshort}}-Entitätstypen definieren.

#### Vorbereitungen
{: #wks_uimawexmap_prereqs}

Das Typsystem in Ihrem {{site.data.keyword.knowledgestudioshort}}-Arbeitsbereich muss die Entitätstypen enthalten, denen Sie die UIMA-Typen zuordnen möchten.

#### Vorgehensweise
{: #wks_uimawexmap_procedure}

So ordnen Sie UIMA-Typen den {{site.data.keyword.knowledgestudioshort}}-Entitätstypen zu:

1. Erstellen Sie eine Datei mit dem Namen `cas2di.tsv` in dem Ordner, der die Deskriptordatei des UIMA-Typsystems enthält (z. B. `exportiertes_typsystem.xml` oder `TypeSystem.xml`.
1. Öffnen Sie die Datei `cas2di.tsv` in einem Texteditor. Jede Zeile in der Datei gibt eine einzelne Zuordnung an. Das Format der Zuordnung hängt davon ab, welche Annotationen des Annotators zugeordnet werden sollen:

    - Sie können Zuordnungen mit dem folgenden Basisformat erstellen:

        `UIMA_Typname[TAB]WKS_Entitätstyp`

        Im folgenden Beispiel werden Zuordnungen zwischen den vom Annotator für die Erkennung benannter Entitäten in {{site.data.keyword.watson}} Explorer Content Analytics erstellten UIMA-Typen und Entitätstypen definiert, die in einem {{site.data.keyword.knowledgestudioshort}}-Typsystem definiert sind:

        ```
        com.ibm.langware.Organization  ORGANISATION
        com.ibm.langware.Person  PERSON
        com.ibm.langware.Location  POSITION
        ```
        {: screen}

        In einem weiteren Beispiel wird eine Zuordnung zwischen den UIMA-Typen, die von einem mit {{site.data.keyword.watson}} Explorer Content Analytics Studio erstellten angepassten Annotator definiert wurden, und {{site.data.keyword.knowledgestudioshort}}-Entitätstypen definiert:

        ```
        com.ibm.Person  PERSON
        com.ibm.Date  DATUM
        ```
        {: screen}

    - Sie können Zuordnungen auf der Basis von Facetten erstellen, die im Annotator für Pattern Matcher oder im Annotator für Wörterverzeichnissuche in {{site.data.keyword.watson}} Explorer Content Analytics verwendet werden. In den Regeldateien der Textanalyse (`*.pat`) wird die Facette als Kategorieattribut dargestellt. Verwenden Sie die folgende Syntax, um eine Zuordnung zu definieren:

        ```
        com.ibm.takmi.nlp.annotation_type.ContiguousContext:category={FACETTENPFAD}[TAB]{WKS-ENTITÄTSTYP}
        ```
        {: screen}

        Im folgenden Beispiel werden der Annotator für Pattern Matcher und der Annotator für Wörterverzeichnissuche verwendet und es wird eine Zuordnung zwischen der Kategorie '$.mykeyword.product' und dem {{site.data.keyword.knowledgestudioshort}}-Entitätstyp PRODUKT definiert:

        ```
        com.ibm.takmi.nlp.annotation_type.ContiguousContext:category=$.mykeyword.product PRODUKT
        ```
        {: screen}

#### Nächste Schritte
{: #wks_uimawexmap_next}

Sie müssen eine ZIP-Datei erstellen, die alle erforderlichen Dateien zum Hochladen der analysierten Dateien in einen {{site.data.keyword.knowledgestudioshort}}-Arbeitsbereich enthält.

**Zugehörige Informationen**:

[Annotator für Pattern Matcher ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ta.doc/iiystapattmatch.htm){: new_window}

[Annotator für Wörterverzeichnissuche ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ta.doc/iiystadictlookup.htm){: new_window}

[Annotator für die Erkennung benannter Entitäten ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ta.doc/iiystasystemt.htm){: new_window}

### UIMA CAS XMI-Dateien in einen Arbeitsbereich hochladen
{: #wks_uimaweximport}

Wenn Sie die vorannotierten Dokumente, die Sie heruntergeladen haben, zum Trainieren eines Modells verwenden möchten, müssen Sie eine ZIP-Datei erstellen, die alle erforderlichen Dateien zum Hochladen der XMI-Dateien enthält, und diese ZIP-Datei in einen {{site.data.keyword.knowledgestudioshort}}-Arbeitsbereich hochladen.

#### Vorbereitungen
{: #wks_uimaweximport_prereqs}

Vergewissern Sie sich vor dem Hochladen der ZIP-Datei, dass das Typsystem in Ihrem {{site.data.keyword.knowledgestudioshort}}-Arbeitsbereich die Entitätstypen enthält, denen Sie die UIMA-Typen zugeordnet haben.

> **Warnung:** UIMA-Analyseengines ermöglichen Annotationen über Satzgrenzen hinweg. In {{site.data.keyword.knowledgestudioshort}} müssen die Annotationen innerhalb der Grenzen eines einzigen Satzes liegen. Wenn die XMI-Dateien, die Sie hochladen, Annotationen enthalten, die sich über mehrere Sätze erstrecken, werden diese Annotationen nicht im Ground Truth-Editor angezeigt.

#### Vorgehensweise
{: #wks_uimaweximport_procedure}

So laden Sie vorannotierte Dokumente in einen {{site.data.keyword.knowledgestudioshort}}-Arbeitsbereich hoch:

1. Erstellen Sie eine ZIP-Datei, die alle von {{site.data.keyword.knowledgestudioshort}} benötigten Dateien enthält.

    1. Wählen Sie einen Ordner aus, der die XMI-Dateien, die Deskriptordatei des UIMA-Typsystems und die Datei `cas2di.tsv` enthält, oder wählen Sie alle Dateien in dem Ordner aus.
    1. Erstellen Sie eine ZIP-Datei, die alle Dateien enthält. Stellen Sie sicher, dass die Datei `cas2di.tsv` und die Deskriptordatei des UIMA-Typsystems im Stammverzeichnis der ZIP-Datei abgelegt sind. Wenn diese Dateien in einem Unterordner der ZIP-Datei enthalten sind, können Sie von {{site.data.keyword.knowledgestudioshort}} nicht gelesen werden, d. h. es wird nichts importiert.

        Unter Windows können Sie mit der rechten Maustaste klicken und **Senden an** > **ZIP-komprimierter Ordner** auswählen.

1. Laden Sie die ZIP-Datei in einen {{site.data.keyword.knowledgestudioshort}}-Arbeitsbereich hoch.

    1. Melden Sie sich als {{site.data.keyword.knowledgestudioshort}}-Administrator oder -Projektleiter an, öffnen Sie den Arbeitsbereich, zu dem Sie die Dokumente hinzufügen möchten, und öffnen Sie die Seite **Assets** > **Dokumente**.
    1. Klicken Sie auf **Dokumentgruppen hochladen**.
    1. Ziehen Sie die ZIP-Datei, die Sie erstellt haben, oder klicken Sie, um die Datei zu lokalisieren und auszuwählen.
    1. Wählen Sie das Kontrollkästchen aus, um anzugeben, dass die ZIP-Datei UIMA CAS XMI-Dateien enthält.
    1. Klicken Sie auf **Hochladen**.
