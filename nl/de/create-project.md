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

Diese Dokumentation bezieht sich auf {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Die Dokumentation für die Vorgängerversion {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace kann über [diesen Link ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/docs/services/knowledge-studio/create-project.html){: new_window} aufgerufen werden.
{: tip}

# Arbeitsbereich erstellen
{: #create-project}

Der erste Schritt beim Erstellen eines angepassten Modells ist das Erstellen eines Arbeitsbereichs.
{: shortdesc}

## Informationen zu diesem Vorgang

Für jedes Modell, das Sie erstellen und verwenden möchten, erstellen Sie einen einzelnen Arbeitsbereich, der die Artefakte und Ressourcen enthält, die zum Erstellen des Modells erforderlich sind. Anschließend trainieren Sie das Modell, um ein angepasstes Modell zu erstellen, das für die Verwendung durch einen externen Service bereitgestellt werden kann.

Vor dem Erstellen eines Arbeitsbereichs sollten Sie die folgenden Fragen beantworten:

- **Welchen Modelltyp möchten Sie erstellen?**

    - Modell für maschinelles Lernen: Verwendet den statistischen Ansatz zum Erkennen von Entitäten und Beziehungen in Dokumenten. Dieser Modelltyp kann an ein zunehmendes Datenvolumen angepasst werden.
    - Regelbasiertes Modell: Verwendet eine deklarative Methode zum Erkennen von Entitäten in Dokumenten. Dieser Modelltyp ist besser vorhersehbar und leichter zu verstehen und zu pflegen. Das Lernen aus neuen Daten ist bei diesem Modelltyp nicht möglich. Es kann nur nach bekannten (vorgegebenen) Mustern gesucht werden.

    > **Hinweis:** Sie können auch einen Arbeitsbereich erstellen, der ein regelbasiertes Modell und ein Modell für maschinelles Lernen enthält.

- **Von welchen Services wird das Modell verwendet?**

    Unter [Integration von {{site.data.keyword.watson}}-Services](/docs/services/watson-knowledge-studio/index.html#wks_watsoninteg) finden Sie Informationen zu weiteren {{site.data.keyword.watson}}-Services, mit denen angepasste Modelle verwendet werden können.

## Vorgehensweise

Führen Sie die folgenden Schritte aus, um einen Arbeitsbereich zu erstellen:

1. Melden Sie sich als {{site.data.keyword.knowledgestudioshort}}-Administrator an und klicken Sie auf **Arbeitsbereich erstellen**.

    > **Hinweis:** Benutzer mit der Rolle des Projektleiters können fast alle Tasks ausführen (ausgenommen das Erstellen eines Arbeitsbereichs). Ein Administrator muss den Arbeitsbereich erstellen und ihm Projektleiter zuordnen.

1. Geben Sie dem Arbeitsbereich einen Namen. Wählen Sie einen kurzen Namen, der auf den Inhalt des Fachgebiets oder den Zweck des Modells hinweist. Bei Bedarf können Sie den Namen des Arbeitsbereichs später ändern.
1. Geben Sie an, welche Sprache die Dokumente in Ihrem Arbeitsbereich verwenden sollen. Dokumente, die Sie zum Arbeitsbereich hinzufügen, oder Wörterverzeichnisse, die Sie erstellen oder hochladen, müssen in der von Ihnen angegebenen Sprache vorliegen.
1. Optional: Wenn die Anwendung anstelle des standardmäßigen Tokenizers für maschinelles Lernen einen anderen Tokenizer verwenden soll, erweitern Sie den Abschnitt **Erweiterte Optionen** und wählen Sie **Wörterverzeichnisbasierter Tokenizer** aus.

    Der Standardtokenizer ist leistungsfähiger als der wörterverzeichnisbasierte Tokenizer. Er nutzt die Ergebnisse des maschinellen Lernprozesses in der Sprache der Quellendokumente, um die Token in den Quellendokumenten zu identifizieren. Dies ermöglicht größere Genauigkeit beim Identifizieren der Token, da die stärker differenzierten Sprachmuster der natürlichen Sprache berücksichtigt werden können. Der wörterverzeichnisbasierte Tokenizer identifiziert Token mithilfe von Sprachregeln. Siehe [Tokenizer](/docs/services/watson-knowledge-studio/create-project.html#wks_tokenizer).

1. Optional: Wenn Sie Projektleiter zum Arbeitsbereich hinzufügen möchten, erweitern Sie den Abschnitt **Erweiterte Optionen** und wählen Sie in der Liste die Namen der Personen aus, die Sie als Projektleiter hinzufügen möchten. Der Administrator kann später durch das Bearbeiten des Arbeitsbereichs Projektleiter hinzufügen oder entfernen.

    Es werden nur die Namen der Personen angezeigt, denen Sie auf der Seite 'Benutzerkontoverwaltung' die Rolle des Projektleiters für diese Instanz zugeordnet haben. Weitere Informationen zum Hinzufügen von Benutzern finden Sie unter [Team zusammenstellen](/docs/services/watson-knowledge-studio/team.html).

    > **Hinweis:** Wenn Sie einen Lite-Plan abonniert haben, können Sie diesen Schritt überspringen. Unter einem kostenlosen Plan können Sie keine Benutzer hinzufügen und auch keinem Benutzer die Rolle des Projektleiters zuordnen. Sie benötigen keinen zusätzlichen Projektleiter. Als Administrator können Sie auch alle Tasks ausführen, die sonst ein Projektleiter ausführen würde.

1. Klicken Sie auf **Erstellen**.

## Nächste Schritte

Nachdem der Arbeitsbereich erstellt wurde, können Sie mit dem Konfigurieren der Arbeitsbereichsressourcen beginnen.

Ein Administrator kann den Arbeitsbereich jederzeit bearbeiten, um die Beschreibung oder den Namen des Arbeitsbereichs zu ändern und Projektleiter hinzuzufügen oder zu entfernen. Klicken Sie auf der Homepage von {{site.data.keyword.knowledgestudioshort}} auf das Symbol **Menü anzeigen** in der Kachel des Arbeitsbereichs und wählen Sie die Menüoption **Bearbeiten** aus.

**Zugehörige Konzepte**:

[Ressourcen aus einem anderen Arbeitsbereich hochladen](/docs/services/watson-knowledge-studio/exportimport.html)

**Zugehörige Referenzinformationen**:

[Sprachunterstützung](/docs/services/watson-knowledge-studio/language-support.html)

## Tokenizer
{: #wks_tokenizer}

Ein Tokenizer gruppiert Zeichen zu Token und Token zu Sätzen. Ein Token entspricht ungefähr einem Wort.

Welche Aktionen ein Tokenizer ausführen muss, um die Token in einem Dokument zu identifizieren, hängt von der Sprache des Dokuments ab. In der englischen Sprache entspricht ein Token meist einem Wort, das in einem Satz durch Leerzeichen begrenzt wird. Token stimmen jedoch nicht immer eins-zu-eins mit Wörtern überein. In manchen Fällen werden andere Textelemente als Token eingestuft. Beispielsweise wird die Interpunktion am Ende eines Satzes als Token eingestuft und Zusammenziehungen werden häufig in zwei Token aufgeteilt. In Sprachen, die keine Leerzeichen verwenden (z. B. Chinesisch), werden komplexere statistische Algorithmen verwendet, um die Token zu identifizieren.

Der Prozess für die Zerlegung in Token ist von grundlegender Bedeutung, da er die Zeichengruppen festlegt, die Benutzer im Ground Truth-Editor als Annotationen hervorheben können. Annotationen für Erwähnungen von Entitäten und Beziehungen werden im Allgemeinen nach Tokengrenzen ausgerichtet und müssen innerhalb eines Satzes beschriftet werden; sie dürfen nicht über Satzgrenzen hinausgehen.

### Unterstützte Typen

{{site.data.keyword.knowledgestudioshort}} unterstützt die folgenden Tokenizer:

- **Tokenizer für maschinelles Lernen (Standard)**

    Dieser intelligente Tokenizer identifiziert die Token in den Quellendokumenten basierend auf den Ergebnissen der statistischen Lernprozesses in der Sprache der Quellendokumente. Dieser Tokenizer findet Token mithilfe der stärker differenzierten Sprachmuster der natürlichen Sprache. Dieser Tokenizer kann nicht von Ihnen angepasst werden.

- **Wörterverzeichnisbasierter Tokenizer**

    Dieser Tokenizer basiert auf linguistischen Wörterverzeichnissen. Er findet Token, die den Regeln der Sprache in den Quellendokumenten entsprechen. Dieser Tokenizer kann von fortgeschrittenen Benutzern angepasst werden.

Beim Erstellen des Arbeitsbereichs müssen Sie auswählen, welcher Tokenizer verwendet werden soll. Sie können den Tokenizer später nicht mehr wechseln. Die besten Ergebnisse erzielen Sie mit dem Standardtokenizer. Nur fortgeschrittene Benutzer, die das Verhalten des Tokenizers durch einen deterministischen Wörterverzeichnismechanismus ändern wollen, sollten den wörterverzeichnisbasierten Tokenizer auswählen. Diese Benutzer können den Tokenizer anpassen, indem sie neue Einträge zum Wörterverzeichnis hinzufügen. Gehen Sie bei der Anpassung besonders sorgfältig vor, da neu hinzugefügte Wörter im Wörterverzeichnis zu unbeabsichtigten Änderungen des Modells für maschinelles Lernen führen können.

## Zusammenfassung der Eingaben, Ausgaben und Einschränkungen
{: #wks_formats}

Die verschiedenen Phasen der Modellentwicklung erfordern unterschiedliche Eingaben und liefern unterschiedliche Ausgaben.

Diese Tabelle enthält für jede Phase der Modellentwicklung eine Zusammenfassung der typischen Aktivitäten, die Sie ausführen, und der unterstützten Eingabedateiformate sowie der Ausgaben, die erzeugt werden können, und der Größenbeschränkungen und sonstigen Anforderungen.

### Alle Modelltypen

<table summary="Diese Tabelle fasst die Eingaben, Ausgaben und die Beschränkungen für alle Modelltypen zusammen.">
  <caption>Tabelle 1. Alle Modelltypen</caption>
  <tr>
    <th style="vertical-align:bottom; text-align:left" id="d25459e252">
      Task
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e254">
      Typische Verwendung
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e256">
      Unterstützte Eingabeformate
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e258">
      Unterstützte Ausgabeformate
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e260">
      Einschränkungen und Anforderungen
    </th>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e252">
      <p>Typsystemverwaltung</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e254">
      <p>Ein Typsystem erstellen oder ein vorhandenes Typsystem hochladen und ändern.</p>
      <p>Definieren Sie Entitätstypen
und Beziehungstypen für Ihr Fachgebiet.</p>
      <p>Es wird keine Darstellung des Typsystems
angezeigt.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e256">
      <ul>
        <li>
          <p>JSON-Datei, die Sie aus einem {{site.data.keyword.knowledgestudioshort}}-Arbeitsbereich heruntergeladen haben</p>
        </li>
        <li>
          <p>ZIP-Datei, die Sie aus dem Tool für Annotatorbenutzer (Human Annotation Tool, HAT) heruntergeladen haben</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e258">
      <ul>
        <li>
          <p>JSON</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e260">
      <p>Um eine unübersichtliche grafische Darstellung zu vermeiden, nicht mehr
als 50 Entitätstypen und 50 Beziehungstypen definieren.</p>
      <p>Begrenzte Dateigröße zum Hochladen eines Typsystems: 20 MB</p>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e252">
      <p>Wörterverzeichnisverwaltung</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e254">
      <p>Eine CSV-Wörterverzeichnisdatei im Lesezugriffsmodus hochladen oder eine ZIP-Datei mit Wörterverzeichnissen, die
Sie aus einem anderen Arbeitsbereich heruntergeladen haben.</p>
      <p>Neues Wörterverzeichnis erstellen und anschließend eine CSV-Datei mit
Begriffseinträgen hochladen oder Begriffseinträge in der Datei hinzufügen.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e256">
      <p>Wörterverzeichnisdatei:</p>
      <ul>
        <li>
          <p>CSV-Datei im UTF-8-Format</p>
        </li>
        <li>
          <p>ZIP-Datei mit Wörterverzeichnissen, die aus einem anderen Arbeitsbereich heruntergeladen wurde</p>
        </li>
      </ul>
      <p>Datei mit Begriffseinträgen:</p>
      <ul>
        <li>
          <p>CSV-Datei im UTF-8-Format</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e258">
      <ul>
        <li>
          <p>CSV-Datei im UTF-8-Format</p>
        </li>
        <li>
          <p>ZIP-Datei mit Wörterverzeichnissen für die Verwendung in einem anderen Arbeitsbereich</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e260">
      <p>Beschränkungen der Dateigröße</p>
      <ul>
        <li>
          <p>1 MB pro CSV-Datei mit Begriffseinträgen</p>
        </li>
        <li>
          <p>16 MB pro schreibgeschützte CSV-Wörterverzeichnisdatei</p>
        </li>
        <li>
          <p>15.000 Einträge pro Wörterverzeichnis, außer bei einem schreibgeschützten Wörterverzeichnis</p>
        </li>
        <li>
          <p>64 Wörterverzeichnisse pro Arbeitsbereich</p>
        </li>
      </ul>
    </td>
  </tr>
</table>

 {: #wks_formats__datasimpletable_xxj_qr5_2y}

### Modell für maschinelles Lernen

<table summary="Diese Tabelle fasst die Eingaben, Ausgaben und die Beschränkungen für das Modell für maschinelles Lernen zusammen.">
  <caption>Tabelle 2. Modell für maschinelles Lernen</caption>
  <tr>
    <th style="vertical-align:botton; text-align:left" id="d25459e331">Task</th>
    <th style="vertical-align:botton; text-align:left" id="d25459e333">Typische Verwendung</th>
    <th style="vertical-align:botton; text-align:left" id="d25459e335">Unterstützte Eingabeformate</th>
    <th style="vertical-align:botton; text-align:left" id="d25459e337">Unterstützte Ausgabeformate</th>
    <th style="vertical-align:botton; text-align:left" id="d25459e339">Einschränkungen und Anforderungen</th>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>Dokumentverwaltung </p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
      <p>Kleine repräsentative Teilgruppe der Dokumente hochladen</p>
      <p>Dokumente mit Annotationen hochladen,
die von einem Annotatorbenutzer hinzugefügt wurden, von einem Modell für maschinelles Lernen oder von einer UIMA-Analyseengine</p>
      <p>Es ist nicht möglich, den gesamten Korpus aus {{site.data.keyword.ibmwatson_notm}} Explorer einzupflegen, hochwertige Dokumente für die Annotation zu berechnen. </p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <ul>
        <li>
          <p>CSV-Datei im UTF-8-Format</p>
        </li>
        <li>
          <p>Text im UTF-8-Format</p>
        </li>
        <li>
          <p>ZIP-Datei mit Dokumenten, die aus einem anderen Korpus heruntergeladen wurden</p>
        </li>
        <li>
          <p>ZIP-Datei mit Dokumenten im UIMA CAS XMI-Format</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <ul>
        <li>
          <p>ZIP-Archivdatei mit Dokumenten</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <ul>
        <li>
          <p>40.000 Zeichen pro Dokument</p>
        </li>
        <li>
          <p>10.000 Dokumente pro Arbeitsbereich</p>
        </li>
        <li>
          <p>1.000 Dokumentgruppen (einschließlich Annotationsgruppen) pro Arbeitsbereich</p>
        </li>
      </ul>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>Vorannotation</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
       <p>Mit einem Wörterverzeichnis oder
dem Vorannotator von {{site.data.keyword.nlufull}} einen
Ausgangspunkt für Annotatorbenutzer bereitstellen.</p>
       <p>Ein Korpus aus {{site.data.keyword.ibmwatson_notm}} Explorer kann nicht erneut annotiert werden.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <p>Unformatierte Dokumente.</p>
      <p><b>Hinweis:</b> Beim
Vorannotieren von Dokumenten, die bereits  von einem Annotatorbenutzer annotiert wurden, geht das Arbeitsergebnis
des Annotatorbenutzers verloren.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <p>Teilweise annotierte Dokumente</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <p>Keine</p>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>Dokumentannotation</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
      <p>Arbeit der Annotatorbenutzer verwalten</p><p>Durch Annotieren von Entitäten, Beziehungen und Koreferenzketten
die Ground Truth erstellen</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <p>Annotationstask</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <p>Ground Truth</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <ul>
        <li>
          <p>256 aktive Annotationstasks pro Arbeitsbereich</p>
        </li>
      </ul>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>Training und Optimierung</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
      <p>Ein überwachtes Modell für maschinelles Lernen trainieren,
um fachspezifische Informationen aus unstrukturiertem Text zu extrahieren.</p><p>Ein überwachtes Modell für maschinelles Lernen auswerten und verbessern.</p>
      <p>Es kann kein teilweise oder gar nicht überwachtes Modell für maschinelles Lernen
erstellt werden.</p>
      <p>Es kann keine umfangreiche Entwicklungsarbeit
für Funktionen durchgeführt werden.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <p>Nicht zutreffend</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <p>Modell für maschinelles Lernen</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <ul>
        <li>
          <p>1 Modell für maschinelles Lernen pro Arbeitsbereich</p>
        </li>
        <li>
          <p>10 Modellversionen pro Arbeitsbereich</p>
        </li>
        <li>
          <p>Maximale Anzahl der Arbeitsbereiche wird durch den Abonnementplan festgelegt</p>
        </li>
        <li>
          <p>Maximale Anzahl der Trainingsaktionen, die pro Monat ausgeführt werden können, wird durch den Abonnementplan festgelegt</p>
        </li>
      </ul>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>Veröffentlichung</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
      <p>Veröffentlichen Sie ein Modell für maschinelles Lernen, das zum Durchführen der Textextraktion in anderen {{site.data.keyword.watson}}-Anwendungen verwendet werden soll.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <p>Nicht zutreffend</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <ul>
        <li>
          <p>Modell-ID (zur Verwendung in {{site.data.keyword.nlufull}} oder {{site.data.keyword.discoveryfull}})</p>
        </li>
        <li>
          <p>ZIP-Datei (zur Verwendung in {{site.data.keyword.ibmwatson_notm}} Explorer)</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <p>Für die Bereitstellung in den {{site.data.keyword.watson}}-Services müssen der {{site.data.keyword.cloud_notm}}-Servicebereich und die Instanznamen bekannt sein.</p>
    </td>
  </tr>
</table>

### Regelbasiertes Modell

<table summary="Diese Tabelle fasst die Eingaben, Ausgaben und die Beschränkungen für das regelbasierte Modell zusammen.">
  <caption>Tabelle 3. Regelbasiertes Modell</caption>
  <tr>
    <th style="vertical-align:bottom; text-align:left" id="d25459e509">
      Task
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e511">
      Typische Verwendung
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e513">
      Unterstützte Eingabeformate
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e515">
      Unterstützte Ausgabeformate
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e517">
      Einschränkungen und Anforderungen
    </th>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e509">
      <p>Regeleditor</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e511">
      <p>Dokumente im Regeleditor erstellen oder in den Regeleditor hochladen, aus denen Klassen, reguläre Ausdrücke und Regeln definiert werden sollen.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e513">
      <ul>
        <li>
          <p>Klartext (im Editor hinzugefügt)</p>
        </li>
        <li>
          <p>CSV-Datei im UTF-8-Format</p>
        </li>
        <li>
          <p>Aus allen Dokumentgruppen kopiert</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e515">
      <p>Keine</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e517">
      <ul>
        <li>
          <p>1 regelbasiertes Modell pro Arbeitsbereich</p>
        </li>
        <li>
          <p>5.000 Zeichen pro Dokument</p>
        </li>
        <li>
          <p>100 Dokumente pro Arbeitsbereich</p>
        </li>
        <li>
          <p>Maximale Größe des Dokumenttitels: 256 Zeichen</p>
        </li>
        <li>
          <p>200 Regeln pro Arbeitsbereich</p>
        </li>
        <li>
          <p>400 Klassen pro Arbeitsbereich</p>
        </li>
        <li>
          <p>100 Gruppen mit regulären Ausdrücken pro Arbeitsbereich</p>
        </li>
        <li>
          <p>100 Einträge für reguläre Ausdrücke pro Gruppe mit regulären Ausdrücken</p>
        </li>
        <li>
          <p>1.000 Zeichen pro Eintrag für regulären Ausdruck</p>
        </li>
        <li>
          <p>5 regelbasierte Modellversionen pro Arbeitsbereich</p>
        </li>
      </ul>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e509">
      <p>Veröffentlichung</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e511">
      <p>Veröffentlichen Sie ein regelbasiertes Modell, das für die Mustererkennung in anderen {{site.data.keyword.watson}}-Anwendungen verwendet werden soll. </p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e513">
      <p>Nicht zutreffend</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e515">
      <ul>
        <li>
          <p>Modell-ID (zur Verwendung in {{site.data.keyword.nlufull}} oder {{site.data.keyword.discoveryfull}})</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e517">
      <p>Für die Bereitstellung in den {{site.data.keyword.watson}}-Services müssen der {{site.data.keyword.cloud_notm}}-Servicebereich und die Instanznamen bekannt sein.</p>
    </td>
  </tr>
</table>
