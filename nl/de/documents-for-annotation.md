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

Diese Dokumentation bezieht sich auf {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Die Dokumentation für die Vorgängerversion {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace kann über [diesen Link ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/docs/services/knowledge-studio/documents-for-annotation.html){: new_window} aufgerufen werden.
{: tip}

# Dokumente zum Annotieren hinzufügen
{: #documents-for-annotation}

Zum Trainieren eines Modells für maschinelles Lernen müssen Sie in Ihrem Arbeitsbereich Dokumente hinzufügen, die Wissen aus dem betreffenden Fachgebiet enthalten (z. B. Artikel aus Fachzeitschriften oder andere fachspezifische Texte).
{: shortdesc}

## Informationen zu diesem Vorgang
{: #annotation_about}

Zum Definieren von Regeln für das regelbasierte Modell fügen Sie Dokumente hinzu oder laden Dokumente hoch, aus denen Muster extrahiert und als Regeln definiert werden können. Siehe [Dokumente zum Definieren von Regeln hinzufügen](/docs/services/watson-knowledge-studio/rule-annotator-add-doc.html). In diesem Abschnitt wird beschrieben, wie Dokumente zum Annotieren hinzugefügt werden.

## Dokumente
{: #wks_sampledoc}

Zum Trainieren eines Modells für maschinelles Lernen müssen Sie Dokumente sammeln, die für den Inhalt des Fachgebiets repräsentativ und für Ihre Anwendung wertvoll sind.

Stellen Sie sicher, dass Ihre Trainingsdokumente für die relevanten Inhalte Ihres Fachgebiets repräsentativ sind. Mit anderen Worten: Die Dokumente müssen viele relevante Erwähnungen enthalten, die annotiert werden können. Halten Sie sich an die folgenden Richtlinien, um die besten Dokumente auszuwählen:

- Stellen Sie möglichst eine Dokumentgruppe zusammen, die insgesamt ca. 300.000 Wörter umfasst. Stellen Sie für ein komplexes Typsystem mehr Wörter bereit und für ein einfaches Typsystem weniger Wörter.
- Jedes Dokument sollte ungefähr ein bis zwei Seiten umfassen (am besten weniger als 2.000 Wörter oder knapp über 1.000 Wörter). In der Anfangsphase der Modellentwicklung sollte jedes Dokument möglichst nur wenige Absätze enthalten. Ein Annotatorbenutzer kann zwar Erwähnungen und Beziehungen in einem langen Dokument markieren, doch das Markieren von Koreferenzen in Dokumenten, die mehrere Seiten umfassen, kann sehr mühsam sein.
- Stellen Sie sicher, dass die Daten in den Dokumenten alle möglichen Entitätstypen, Untertypen und Rollen sowie die zwischen ihnen bestehenden Beziehungen abdecken. Eine hilfreiche Zielsetzung besteht darin, am Ende mindestens 50 Annotationen für jeden Entitätstyp und für jeden Beziehungstyp in der Dokumentsammlung zu haben.
- Noch einmal: Die Dokumente sollten die ganze Bandbreite des Fachgebiets repräsentieren, das von der Anwendung abgedeckt werden soll. Bei tendenziell ungleichmäßiger Häufigkeitsverteilung der Vorkommen von Entitäts- und Beziehungstypen sollten mindestens 50 Exemplare für jeden Typ (oder mehr für Entitätstypen, die meist in Form von Ausdrücken erwähnt werden) vorhanden sein.
- Die zum Trainieren des Modells erstellte Dokumentgruppe muss mindestens 10 annotierte Dokumente enthalten.

Wenn die Vorbereitungen zum Erstellen und Trainieren des Modells abgeschlossen sind, können Dokumente, die Sie zum Arbeitsbereich hinzufügen, in mehrere Gruppen aufgeteilt werden, die für Trainingsdaten, Testdaten und Blinddaten verwendet werden. Die separaten Datasets sind wichtig für die Bewertung der Leistung des Modells.

Sie können Dokumente mit den folgenden Formaten hinzufügen:

- Zweispaltige CSV-Datei im UTF-8-Format
- Textdateien im UTF-8-Format
- ZIP-Datei mit Dokumenten, die aus einem {{site.data.keyword.knowledgestudioshort}}-Arbeitsbereich heruntergeladen wurden
- ZIP-Datei mit Dateien im UIMA CAS XMI-Format

### CSV-Dateien
{: #wks_sampledoc__wks_samplecsv}

Sie können eine CSV-Datei mit zwei Spalten, die Beispieltext enthält, aus Ihrer lokalen Maschine hochladen. Laden Sie jeweils nur eine CSV-Datei hoch. In der ersten Spalte der CSV-Datei ist der Dateiname des Dokuments angegeben. Die zweite Spalte in der Datei enthält den Dokumenttext. Ein Beispiel für das erforderliche Format finden Sie in der Datei <a href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/documents-new.csv" download>`documents-new.csv ` <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link" class="style-scope doc-content"></a>, die in den Beispieldateien für das Lernprogramm enthalten ist.

### Dokumente aus einem anderen Watson Knowledge Studio-Arbeitsbereich
{: #wks_sampledoc__wks_samplecorpus}

Wenn Sie zuvor Dokumente aus einem {{site.data.keyword.knowledgestudioshort}}-Arbeitsbereich heruntergeladen haben, können Sie die von Ihnen heruntergeladene `ZIP`-Datei nun hochladen. Über eine Option können Sie angeben, ob die Ground Truth-Annotationen in der importierten Datei enthalten sein sollen.

Nachdem Dokumente mit Annotationen versehen wurden, werden die annotierten Dokumente im `JSON`-Format gespeichert. Die Formatierungssprache in den Dateien zeigt, wie der ursprüngliche Dokumenttext analysiert und mit Token versehen wurde und enthält Elemente für alle Annotationen, die von einem Annotatorbenutzer hinzugefügt wurden. Um die Modellgenauigkeit im Laufe der Zeit zu verbessern, können Sie diese Dateien in einen anderen Arbeitsbereich hochladen. Dabei bleiben alle vorhandenen Annotationen erhalten. Ein Annotatorbenutzer kann Annotationen in diesen Dokumenten überarbeiten, löschen und hinzufügen. Sie können aber auch auf die Annotierung durch Benutzer verzichten und die Dateien zum Erstellen von Dokumentgruppen für Trainings-, Test- und Blinddaten verwenden, um die Modellleistung zu bewerten und zu verbessern.

### UIMA CAS XMI-Dateien
{: #wks_sampledoc__samplexmi}

Als Hilfsmittel zum Trainieren eines Modells können Sie Dokumente hochladen, die von einer UIMA-Analyseengine vorannotiert wurden. Die vorannotierten Dateien müssen das XMI-Serialisierungsformat von UIMA Common Analysis Structure (UIMA CAS XMI-Format) aufweisen und als komprimierte ZIP-Datei vorliegen. Sie können beispielsweise Dokumente hochladen, die in einer {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer-Sammlung annotiert wurden.

Ein Annotatorbenutzer kann Annotationen in diesen Dokumenten überarbeiten, löschen und hinzufügen. Sie können aber auch auf die Annotierung durch Benutzer verzichten und die Dateien zum Erstellen von Dokumentgruppen für Trainings-, Test- und Blinddaten verwenden, um die Modellleistung zu bewerten und zu verbessern. Details zum Erstellen dieser Dateien und Voraussetzungen zum Hochladen der Dateien finden Sie unter [Vorannotierte Dokumente hochladen](/docs/services/watson-knowledge-studio/preannotation.html#wks_uima).

### Daten anonymisieren
{: #wks_anonymizing}

Wenn Sie ein optimiertes Modell für Ihre Daten erstellen möchten, ohne die Daten unverändert in {{site.data.keyword.knowledgestudioshort}} zu laden (aus Datenschutzgründen), können Sie alle personenbezogenen Informationen aus den Dokumenten entfernen und anschließend die anonymisierten Dokumente zum Trainieren des Modells verwenden. Verzichten Sie darauf, die Informationen zu redigieren oder global durch Variablen zu ersetzen. Die besten Ergebnisse können Sie erzielen, indem Sie die tatsächlichen Informationen durch fiktive Informationen des gleichen Typs ersetzen.

Beispiel: Wenn die personenbezogenen Daten, die Sie schützen möchten, Kundennamen sind, verzichten Sie darauf, jeden Namen zu redigieren oder durch eine Variable wie *BENUTZERNAME* zu ersetzen. Ersetzen Sie stattdessen jeden Namen durch einen fiktiven Namen und verwenden Sie dabei verschiedene typische Syntaxformen für Namen (z. B. *Lieschen Müller*, *Herr Schmitt*, *Dietrich* oder *Dr. h. c. Meier*. Sie können auch ein Script schreiben, das eine Auswahl von Vor- und Nachnamen bzw. von Titeln und Nachnamen miteinander verkettet und nur Nachnamen hinzufügt, um fiktive Namen zu erstellen, die anstelle der realen Benutzernamen in das Dokument eingefügt werden können. Das Ziel besteht darin, echte Werte in den Quellendokumenten so realitätsnah wie möglich zu simulieren. Wenn in den Dokumenten gleichlautender Text (BENUTZERNAME) verwendet oder Text redigiert wird, trainieren Sie damit ein Modell, das identische oder redigierte Namen erwartet. Schließlich soll das Modell bei der Anwendung auf neue Dokumente mit unbekanntem Namen in allen möglichen Varianten in der Lage sein, diese als Namen zu erkennen.

## Dokumente zu einem Arbeitsbereich hinzufügen
{: #wks_projadd}

Zum Trainieren eines Modells müssen Sie in Ihrem Arbeitsbereich Dokumente hinzufügen, die für die Inhalte Ihres Fachgebiets repräsentativ sind.

### Informationen zu diesem Vorgang
{: #wks_projadd_about}

Ein bewährtes Verfahren besteht darin, eine relativ kleine Sammlung von Dokumenten als Ausgangspunkt zu verwenden. Verwenden Sie diese Dokumente zum Schulen der Annotatorbenutzer (sofern Annotatorbenutzer zum Einsatz kommen) und zum Optimieren der Annotationsrichtlinien. Kleine Dokumente erleichtern den Annotatorbenutzern das Erkennen von Koreferenzketten innerhalb des Dokuments. Wenn die Genauigkeit der Annotationen zunimmt, können Sie weitere Dokumente zum Korpus hinzufügen, um das Training zu vertiefen.

### Vorgehensweise
{: #wks_projadd_procedure}

So fügen Sie Dokumente zu einem Arbeitsbereich hinzu:

1. Melden Sie sich als {{site.data.keyword.knowledgestudioshort}}-Administrator oder -Projektleiter an und wählen Sie Ihren Arbeitsbereich aus.
1. Wählen Sie die Registerkarte **Assets** > **Dokumente** > **Dokumentgruppen** aus.
1. Klicken Sie auf **Dokumentgruppen hochladen**, um Dokumente zum Korpus hinzuzufügen.
1. Laden Sie Dokumente in einem der folgenden Formate hoch. Sie können jeweils einen Dateityp hochladen.

    <table summary="Jede Zeile in dieser Tabelle beschreibt eine Auswahloption.">
      <caption>Tabelle 1. Auswahl hochladen</caption>
      <tr>
        <th style="vertical-align:bottom; text-align:left" id="d31095e284-option">
          Option
        </th>
        <th style="vertical-align:bottom; text-align:left" id="d31095e284-desc">
          Beschreibung
        </th>
      </tr>
      <tr>
        <td headers="d31095e284-option" id="d31095e286">
          <p><strong>CSV-Datei</strong></p>
        </td>
        <td headers="d31095e284-desc d31095e286">
          <p>Ziehen Sie eine einzelne CSV-Datei, die Ihre Beispieldokumente enthält, oder klicken Sie,
              um die Datei in Ihrem lokalen System zu lokalisieren, und klicken Sie anschließend auf <b>Hochladen</b>. In der ersten Spalte der CSV-Datei ist der Dateiname des Dokuments angegeben. Die zweite Spalte in der Datei enthält den Dokumenttext. Die CSV-Datei muss im UTF-8-Format vorliegen.</p>
        </td>
      </tr>
      <tr>
        <td headers="d31095e284-option" id="d31095e294">
          <p><strong>Textdateien</strong></p>
        </td>
        <td headers="d31095e284-desc d31095e294">
          <p>Ziehen Sie mindestens eine Textdatei aus Ihrem lokalen System oder klicken Sie, um die Datei(en) zu lokalisieren
              und auszuwählen, und klicken Sie anschließend auf <b>Hochladen</b>. Textdateien müssen im UTF-8-Format vorliegen.</p>
        </td>
      </tr>
      <tr>
        <td headers="d31095e284-option" id="d31095e316">
          <p><strong>ZIP-Datei</strong></p>
        </td>
        <td headers="d31095e284-desc d31095e316">
          <p>Wenn Sie zuvor Dokumente aus einem
              Watson Knowledge
              Studio-Arbeitsbereich
              heruntergeladen haben, ziehen Sie die
              <code>ZIP</code>-Datei mit den heruntergeladenen Dokumenten oder klicken Sie um die Datei zu lokalisieren
              und auszuwählen. Wenn Sie Annotationen einschließen möchten, die vor dem Herunterladen in den Dokumenten
              hinzugefügt wurden, stellen Sie sicher, dass die Option zum Einschließen der Ground Truth ausgewählt ist, bevor
              Sie auf <b>Hochladen</b> klicken. Es werden nur Annotationen importiert, die vor dem Herunterladen der Dokumente
              in die Ground Truth hochgestuft wurden. </p><p><b>Einschränkung:</b> Beim Importieren annotierter Dokumente
              werden die Dokumente erneut in Token aufgeteilt. Dieser Vorgang kann die Satzgrenzen verändern, die von
              Watson Knowledge
              Studio
              in den Dokumenten erkannt werden. Da Annotationen innerhalb von Sätzen definiert werden, können bei diesem Vorgang
              gegebenenfalls einige Annotationen ungültig gemacht werden. Führen Sie nach dem Hochladen von Dokumenten aus einem
              anderen Arbeitsbereich eine kurze Überprüfung der Annotationen durch, um eventuelle Abweichungen zu beheben.</p>
          <p>Sie müssen das Typsystem aus dem ursprünglichen Arbeitsbereich in den aktuellen Arbeitsbereich
              hochladen, bevor Sie Ground Truth-Annotationen hochladen können. Details hierzu finden Sie
              unter [Ressourcen aus einem anderen Arbeitsbereich hochladen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](exportimport.html){: new_window}.</p>
          <p>Wenn Sie zuvor annotierte Dokumente im
              UIMA CAS XMI-Format heruntergeladen haben, können Sie
              die <code>ZIP</code>-Datei mit den analysierten Inhalten hochladen. Geben Sie
              den gewünschten Inhaltstyp an, den Sie hochladen möchten, bevor Sie auf <b>Hochladen</b> klicken. Details zum Erstellen
              dieser Dateien und Voraussetzungen zum Hochladen der Dateien finden Sie unter [Vorannotierte Dokumente hochladen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](preannotation.html#wks_uima){: new_window}.</p>
        </td>
      </tr>
    </table>

1. Klicken Sie nach dem Hinzufügen der Dokumente auf die Dokumentnamen, um eine Vorschau anzuzeigen und zu überprüfen, dass der Inhalt OK ist. Überprüfen Sie beispielsweise, dass die Textdateien im UTF-8-Format vorliegen und keine diakritischen Zeichen, Zeichennormalisierungsprobleme oder falschen Satzumbrüche in den Dokumenten zu sehen sind. Falls Probleme vorliegen, müssen Sie die Dateien gegebenenfalls vorverarbeiten, bevor Sie zum Korpus hinzugefügt werden. Die Dokumente sollten möglichst fehlerfrei und korrekt formatiert sein, bevor die Annotierung mithilfe von Wörterverzeichnissen oder durch Annotatorbenutzer beginnt.

### Nächste Schritte
{: #wks_projadd_next}

Vor Beginn der Annotatorbenutzertasks sollten Sie den Korpus in mehrere Dokumentgruppen aufteilen und Annotatorbenutzer für die Dokumentgruppen zuordnen.

## Annotationsgruppen erstellen und zuordnen
{: #wks_projdocsets}

Teilen Sie die hinzugefügten Dokumente in Gruppen auf, damit sie von mehreren Annotatorbenutzern annotiert werden können. Wenn Sie Scores für die Übereinstimmung der Annotatoren anzeigen möchten, müssen Sie mindestens zwei Annotatorbenutzer zuordnen und einen Prozentwert für Dokumentüberschneidungen zwischen den Dokumentgruppen angeben.

### Vorbereitungen
{: #wks_projdocsets_prereqs}

- Sie müssen Dokumentgruppen hochladen, damit sie in Annotationsgruppen aufgeteilt werden können.
- Sie müssen in {{site.data.keyword.knowledgestudioshort}} Benutzerkonten für alle Annotatorbenutzer erstellen, die Dokumente in diesem Arbeitsbereich bearbeiten sollen.

### Informationen zu diesem Vorgang
{: #wks_projdocsets_about}

> **Achtung:** Wenn Sie mit dem Google Chrome-Browser arbeiten, können Sie keine größere Anzahl von Dateien (z. B. mehr als 300) hochladen, indem Sie die Dateien in einem Ordner auswählen. Verwenden Sie entweder den Firefox-Browser oder wählen Sie eine kleinere Anzahl Dateien aus und laden Sie die Dateien in mehreren Schritten hoch.

Sie können maximal 1.000 Annotationsgruppen pro Arbeitsbereich erstellen.

### Vorgehensweise
{: #wks_projdocsets_procedure}

So erstellen Sie eine Annotationsgruppe:

1. Melden Sie sich als {{site.data.keyword.knowledgestudioshort}}-Administrator oder -Projektleiter an und wählen Sie Ihren Arbeitsbereich aus.
1. Wählen Sie die Registerkarte **Assets** > **Dokumente** > **Annotationsgruppen** aus.
1. Klicken Sie auf **Annotationsgruppen erstellen**.

    1. Wählen Sie für die Basisgruppe als Dokumentsammlung, die Sie in Annotationsgruppen aufteilen möchten, entweder alle Dokumente im Korpus aus oder Dokumente, die vorher einer Dokumentgruppe zugeordnet wurden.

    1. Geben Sie als Wert für die Überschneidung einen Prozentsatz der Dokumente an, die Sie in jede Annotationsgruppe einschließen möchten. Die Scores für die Übereinstimmung der Annotatorbenutzer können nur berechnet werden, wenn mindestens zwei Annotatorbenutzer dieselben Dokumente annotieren. Beispiel: Wenn Sie einen Überschneidungswert von 20 % für einen Korpus angeben, der 30 Dokumente enthält, und den Korpus in 3 Dokumentgruppen aufteilen, werden 6 Dokumente (20 %) von allen Annotatorbenutzern annotiert. Die übrigen 24 Dokumente werden auf die 3 Annotatorbenutzer aufgeteilt (für jeden Benutzer 8 Dokumente). In diesem Beispiel erhält jeder Annotator insgesamt 14 Dokumente (6 + 8) zum Annotieren.

    > **Hinweis:** Eine Annotationsgruppe, die Sie zum Trainieren eines Modells für maschinelles Lernen verwenden möchten, muss mindestens 10 annotierte Dokumente enthalten.

    1. Wählen Sie einen Benutzernamen in der Liste der Annotatorbenutzer aus.

        > **Hinweis:** Wenn Sie einen Lite-Plan abonniert haben, ordnen Sie Ihre Benutzer-ID der Annotationsgruppe zu. Sie können keine weiteren Benutzer hinzufügen und ihnen die Rolle des Annotatorbenutzers zuordnen. Indem Sie sich selbst hinzufügen, können Sie die Rolle des Annotatorbenutzers übernehmen und testen, wie ein realer Annotatorbenutzer mit dem Ground Truth-Editor Dokumente annotieren würde.

    1. Ordnen Sie der Annotationsgruppe einen Namen zu.

        Ein bewährtes Verfahren zum Bewerten des Arbeitsfortschritts eines Annotatorbenutzers im Arbeitsbereich ist die Verwendung von Annotationsgruppennamen, an denen der für die Gruppe zugeordneten Annotatorbenutzer erkennbar ist. Sie können den Namen der Annotationsgruppe nicht mehr ändern, nachdem die Gruppe erstellt wurde.

1. Nachdem Sie alle Annotatorbenutzer zugeordnet haben, die an diesem Arbeitsbereich arbeiten werden, klicken Sie auf **Generieren**, um die Annotationsgruppen zu erstellen. Wenn sich ein Annotatorbenutzer beim Ground Truth-Editor anmeldet, werden nur die Annotationsgruppen angezeigt, die dem angemeldeten Benutzer zugeordnet sind.

**Zugehörige Tasks**:
{: #wks_related_tasks}

[Team zusammenstellen](/docs/services/watson-knowledge-studio/team.html)

## Dokumente löschen
{: #wks_deletedocs}

Sie können ein Dokument löschen, wenn Sie feststellen, dass es keinen fachspezifischen Text enthält, der für das Modell relevant ist.

Um ein Dokument zu löschen, wählen Sie die Option aus, die für Ihre Situation gilt:
- [Löschen eines Dokuments, das keiner Annotationstask zugeordnet wurde](#deletenotask)
- [Löschen eines Dokuments, das einer Annotationstask zugeordnet wurde, und wenn die von Annotatorbenutzern erstellte Annotation *noch nicht begonnen hat*](#deletenoanno)
- [Löschen eines Dokuments, das einer Annotationstask zugeordnet wurde, und wenn die von Annotatorbenutzern erstellte Annotation *begonnen hat*](#deleteanno)

### Löschen eines Dokuments, das keiner Annotationstask zugeordnet wurde
{: #deletenotask}

Wenn das Dokument, das Sie löschen möchten, keiner Annotationstask zugeordnet ist, führen Sie die folgenden Schritte aus, um das Dokument zu löschen.

#### Vorgehensweise
{: #deletenotaskp}

1. Melden Sie sich als {{site.data.keyword.knowledgestudioshort}}-Administrator an und wählen Sie Ihren Arbeitsbereich aus.
1. Wählen Sie die Registerkarte **Assets** > **Dokumente** > **Dokumentgruppen** aus.
2. Wählen Sie die Dokumentgruppe aus, die das zu löschende Dokument enthält. Die Dokumentgruppe wird geöffnet.
3. Lokalisieren Sie das Dokument, das Sie entfernen möchten und klicken Sie dann auf **Löschen**.

### Löschen eines Dokuments, das einer Annotationstask zugeordnet wurde, und wenn die von Annotatorbenutzern erstellte Annotation noch nicht begonnen hat
{: #deletenoanno}

Wenn das Dokument, das Sie löschen möchten, einer Annotationstask zugeordnet ist und die von Annotatorbenutzern erstellte Annotation *noch nicht begonnen hat*, führen Sie die folgenden Schritte aus, um das Dokument zu löschen.

#### Vorgehensweise
{: #deletenoannop}

1. Melden Sie sich als {{site.data.keyword.knowledgestudioshort}}-Administrator an und wählen Sie Ihren Arbeitsbereich aus.
1. Löschen Sie die Annotationstask:

  a. Öffnen Sie die Seite **Modell für maschinelles Lernen** > **Annotationstasks**.

  b. Suchen Sie die Annotationstask, der das Dokument zugeordnet ist, klicken Sie auf das Symbol **Menü anzeigen** in der Task und klicken Sie anschließend auf **Löschen**.

1. Löschen Sie das Dokument, wie im Abschnitt [Löschen eines Dokuments, das keiner Annotationstask zugeordnet wurde](#deletenotask) beschrieben.
1. Nach dem Löschen des Dokuments können Sie die Annotationstask neu erstellen und dieselbe Annotationsgruppe zuordnen, die nun ein Dokument weniger enthält.

### Löschen eines Dokuments, das einer Annotationstask zugeordnet wurde, und wenn die von Annotatorbenutzern erstellte Annotation begonnen hat
{: #deleteanno}

Wenn das Dokument, das Sie löschen möchten, einer Annotationstask zugeordnet ist und die von Annotatorbenutzern erstellte Annotation *begonnen hat*, führen Sie die folgenden Schritte aus, um das Dokument zu löschen.

**Achtung**: Löschen Sie keine Task, wenn die Benutzerannotation in Bearbeitung ist. Wenn Sie dies tun, verlieren Sie Ihre laufende Arbeit.

#### Vorgehensweise
{: #deleteannop}

1. Bitten Sie die Annotatorbenutzer, dass sie das nicht erwünschte Dokument ignorieren sollen. 
1. Wenn die Annotationsarbeit in den anderen Dokumenten abgeschlossen ist und die Annotatorbenutzer alle Dokumente zum Hinzufügen zur Ground Truth abgeschickt haben [prüfen und akzeptieren Sie die abgeschickten Dokumente](/docs/services/watson-knowledge-studio/build-groundtruth.html#wks_haaccuracy).
1. [Beheben Sie alle Annotationskonflikte](/docs/services/watson-knowledge-studio/build-groundtruth.html#wks_haadjudicate).
1. Wenn alle Dokumente Teil der Ground Truth sind und die Task abgeschlossen ist, löschen Sie die Task, wie in [Löschen eines Dokuments, das einer Annotationstask zugeordnet wurde, und wenn die von Annotatorbenutzern erstellte Annotation noch nicht begonnen hat](#deletenoannop) beschrieben.
1. Löschen Sie das Dokument, wie im Abschnitt [Löschen eines Dokuments, das keiner Annotationstask zugeordnet wurde](#deletenotask) beschrieben.

  **Hinweis**: Sie können bestätigen, dass die Annotationen zu den verbleibenden Dokumenten nicht verloren gehen, indem Sie die Dokumentgruppen herunterladen und die Dokumente im Ordner `gt` überprüfen.

## Datenmodell
{: #wks_datamodel}

Die Diagramme in diesem Abschnitt geben eine Übersicht über den Dokumentfluss in einem {{site.data.keyword.knowledgestudioshort}}-System und veranschaulichten die Unterschiede zwischen Dokumenten im Korpus, in einer Annotationstask und in der Ground Truth.

Der Korpus enthält Dokumente, die in Dokumentgruppen aufgeteilt sind:

- Ein Dokument ist im Grunde nur eine Ansammlung von Textzeichenfolgen.
- Eine Dokumentgruppe ist ein Verweis auf eine Reihe von Dokumenten. Die Dokumentgruppe enthält keine Kopien der Dokumente.
- Manche Dokumentgruppen verweisen möglicherweise auf ein einziges Dokument. Diese Einstellung können Sie mit dem Überschneidungsparameter steuern, den Sie beim Erstellen von Annotationsgruppen angeben.

![Diese Abbildung zeigt zwei Dokumentgruppen, die auf drei Dokumente verweisen. Die Dokumente sind auf die Gruppen verteilt.](images/wks_datacorpus.svg "Diese Abbildung zeigt zwei Dokumentgruppen, die auf drei Dokumente verweisen. Die Dokumente sind auf die Gruppen verteilt.") Abbildung 1. Diese Abbildung zeigt zwei Dokumentgruppen, die auf drei Dokumente verweisen. Die Dokumente sind auf die Gruppen verteilt.

Die Ground Truth beinhaltet die Annotationen (Erwähnungen, Beziehungen und koreferenzierte Erwähnungen), die in Dokumenten hinzugefügt wurden. Die Ground Truth ist für jedes Dokument einmalig.

![Diese Abbildung zeigt, dass die Ground Truth aus den Annotationen besteht, die zu Dokument 1, Dokument 2, Dokument 3 usw. hinzugefügt wurden.](images/wks_datagt.svg "Diese Abbildung zeigt, dass die Ground Truth aus den Annotationen besteht, die zu Dokument 1, Dokument 2, Dokument 3 usw. hinzugefügt wurde.") Abbildung 2. Diese Abbildung zeigt, dass die Ground Truth aus den Annotationen besteht, die zu Dokument 1, Dokument 2, Dokument 3 usw. hinzugefügt wurden.

Wenn Sie eine Annotationstask erstellen, werden Kopien der Annotationen für jedes Dokument in der Annotationstask erstellt, das Sie zu dieser Task hinzufügen. Annotatorbenutzer annotieren das Dokument. Die Annotationen sind voneinander und von der Ground Truth getrennt. Eine Annotationstask ist ein zeitbasiertes Konzept, das es Annotatorbenutzern ermöglicht, Text in abgegrenzten Bereichen zu annotieren. Im Gegensatz dazu ist die Ground Truth permanent und einmalig.

![Diese Abbildungen zeigen, dass der Projektleiter Annotationsgruppen erstellt und einer Annotationstask zuordnet. Die Annotatorbenutzer Dave und Phil annotieren Dokumente in den Gruppen, die ihnen zugeordnet sind.](images/wks_datatask.svg "Diese Abbildungen zeigen, dass der Projektleiter Annotationsgruppen erstellt und einer Annotationstask zuordnet. ") Abbildung 2. Diese Abbildung zeigt, dass der Projektleiter Annotationsgruppen erstellt und einer Annotationstask zuordnet. Die Annotatorbenutzer Dave und Phil annotieren Dokumente in den Gruppen, die ihnen zugeordnet sind.

Nachdem der Projektleiter Annotationsgruppen in einer Annotationstask genehmigt hat, werden die Annotationen in den Dokumenten, die sich nicht mit anderen Annotationsgruppen überschneiden, als Ground Truth festgelegt. Für Dokumente, die sich mit Annotationsgruppen überschneiden (in diesem Beispiel das Dokument 2), muss der Projektleiter die vorhandenen Konflikte beurteilen und beheben. Die Annotationen in Dokumenten mit Überschneidungen werden erst in die Ground Truth hochgestuft, nachdem Sie in der Beurteilungsphase genehmigt wurden.

Die Ground Truth wird anschließend zum Trainieren und Testen eines Modells für maschinelles Lernen verwendet oder als Basis für den nächsten Schritt der Modellentwicklung. Um Ground Truth in einem neuen Entwicklungsschritt zu verwenden, müssen Sie eine neue Annotationstask erstellen.

![Diese Abbildung zeigt, wie die von zwei Annotatorbenutzern hinzugefügten Annotation zur Ground Truth werden. Ein Dokument mit der Bezeichnung 'Dokument 2' wird von beiden Annotatorbenutzern annotiert. Die Annotationen in diesem Dokument mit Überschneidungen müssen beurteilt werden, bevor sie in die Ground Truth aufgenommen werden.](images/wks_datatruth.svg "Diese Abbildung zeigt, wie die von zwei Annotatorbenutzern hinzugefügten Annotationen zur Ground Truth werden. Ein Dokument mit der Bezeichnung 'Dokument 2' wird von beiden Annotatorbenutzern annotiert. Die Annotationen in diesem Dokument mit Überschneidungen müssen beurteilt werden, bevor sie in die Ground Truth aufgenommen werden.") Abbildung 3. Diese Abbildung zeigt, wie die von zwei Annotatorbenutzern hinzugefügten Annotationen zur Ground Truth werden. Ein Dokument mit der Bezeichnung 'Dokument 2' wird von beiden Annotatorbenutzern annotiert. Die Annotationen in diesem Dokument mit Überschneidungen müssen beurteilt werden, bevor sie in die Ground Truth aufgenommen werden.
