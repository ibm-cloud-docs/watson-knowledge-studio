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

Diese Dokumentation bezieht sich auf {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Die Dokumentation für die Vorgängerversion {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace kann über [diesen Link ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/docs/services/knowledge-studio/build-groundtruth.html){: new_window} aufgerufen werden.
{: tip}

# Ground Truth erstellen
{: #build-groundtruth}

Die Zielsetzung des Annotationsprojekts besteht darin, die Ground Truth zu erstellen, d. h. eine Sammlung mit geprüften Daten, um {{site.data.keyword.watson}} an ein bestimmtes Fachgebiet anzupassen. In {{site.data.keyword.knowledgestudioshort}} spielen Annotatorbenutzer, die in der Regel Fachleute des jeweiligen Fachgebiets sind, eine zentrale Rolle beim Festlegen der Ground Truth.
{: shortdesc}

Ein typischer Workflow umfasst die folgenden Schritte:

1. Annotatorbenutzer reichen annotierte Dokumente zum Überprüfen ein.
1. Der Projektleiter (möglicherweise ein besonders erfahrener Fachmann) prüft die Richtigkeit der Annotationen und vergleicht, wie konsistent Dokumente mit Überschneidungen zwischen den Annotationsgruppen von Annotatorbenutzern annotiert wurden.
1. Wenn der Score (Bewertung) für die Übereinstimmung der Annotatoren zu niedrig ist, lehnt der Projektleiter die Annotationsgruppe ab und gibt Sie zur Optimierung an den Annotatorbenutzer zurück. Beim Ablehnen einer Annotationsgruppe werden alle Dokumente der Gruppe wieder in den Bearbeitungsmodus versetzt.
1. Wenn der Projektleiter eine Annotationsgruppe genehmigt, werden alle Dokumente ohne Überschneidungen zwischen den Annotationsgruppen in die Ground Truth hochgestuft, d. h. die zugehörigen Annotationen können zum Trainieren des Modells verwendet werden.
1. Der Projektleiter prüft die Dokumente mit Überschneidungen und behebt die Annotationskonflikte. In dieser Phase, die als Beurteilung bezeichnet wird, kann das Team die Annotationsrichtlinien prüfen und überarbeiten, um Missverständnisse zu klären, die dazu geführt haben, dass Texte von verschiedenen Annotatorbenutzern unzutreffend oder inkonsistent annotiert wurden.

    In einigen Fällen kann ein Prozentsatz an Überschneidungen, der größer ist als der Überschneidungsprozentsatz für die Übereinstimmung der Annotatorbenutzer, zur Beurteilung der Unterschiede, für einen Projektleiter wünschenswert sein. Beispiel: Wenn die Übereinstimmung zwischen Annotatoren akzeptabel ist, kann der Projektleiter entscheiden, dass die betreffenden Annotationen in die Ground Truth hochgestuft werden können.

1. Nachdem der Projektleiter die Annotationskonflikte behoben hat, werden die genehmigten Annotationen in die Ground Truth hochgestuft.

Beachten Sie, dass beim Einsatz von Annotatorbenutzern immer Beurteilungen erforderlich sind. Die Annotationsrichtlinien können viel zur korrekten und konsistenten Annotierung von Text beitragen, doch selbst die besten Richtlinien lassen Spielraum für die Interpretation durch die Benutzer. Beim Erstellen der Ground Truth sollten Sie Zeit für die Schulung und Ausbildung der Annotatorbenutzer einplanen, um eine möglichst zutreffende Beurteilung beim Analysieren der fachspezifischen Inhalte zu ermöglichen.

## Übereinstimmung der Annotatoren
{: #wks_haiaa}

Nach dem Annotieren der Dokumente durch Annotatorbenutzer müssen Sie festlegen, welche Dokumente in die Ground Truth hochgestuft werden sollen. Überprüfen Sie zuerst die Scores für die Übereinstimmung der Annotatoren. Dokumente mit niedrigen Sores kommen in Betracht, abgelehnt und zur Optimierung an die Annotatorbenutzer zurückgegeben zu werden.

Bei der Berechnung der Scores für die Übereinstimmung der Annotatoren durchsucht das System alle Dokumente mit Überschneidungen in allen Annotationsgruppen der Task, unabhängig vom Status der Gruppen. Da Annotationen erst akzeptiert bzw. abgelehnt werden können, wenn Sie den Status 'Submitted' (Übergeben) aufweisen, sollte die Übereinstimmung der Annotatoren erst ausgewertet werden, nachdem alle Annotationsgruppen eingereicht wurden. Alternativ können Sie die Auswertung auf diejenigen Annotatorbenutzer begrenzen, die ihre abgeschlossenen Annotationsgruppen bereits eingereicht haben.

Die Scores für die Übereinstimmung der Annotatoren zeigen, wie unterschiedlich die einzelnen Erwähnungen, Beziehungen und Koreferenzketten von den Annotatorbenutzern annotiert wurden. Um die Scores anzuzeigen, können Sie zwei Annotatorbenutzer vergleichen (vergleichen Sie zum Beispiel alle von John eingefügten Annotationen für Erwähnungen mit den von Mary eingefügten Annotationen für Erwähnungen). Sie können die Scores auch vergleichen, indem Sie bestimmte Dokumente vergleichen (vergleichen Sie zum Beispiel die Beziehungsannotationen, die John in ein Dokument eingefügt hat, mit den Beziehungsannotationen, die Mary in dasselbe Dokument eingefügt hat).

Damit Bereiche, die untersucht werden sollten, leichter zu erkennen sind, werden Scores, die unter dem von Ihnen angegebenen Schwellenwert für die Übereinstimmung der Annotatoren liegen, rot hervorgehoben. In der Anfangsphase Ihres Annotationsprojekts fallen die Scores für Beziehungen häufig schlechter aus als die Scores für Erwähnungen. Dies ist darauf zurückzuführen, dass zutreffende Beziehungsannotationen erst möglich sind, nachdem die der Beziehung zugrunde liegenden Erwähnungen in Übereinstimmung gebracht wurden.

Der Score in der Spalte **Alle** ist ein *Fleiss' Kappa-Score*. Dieser Score gibt an, wie konsistent die gleiche Annotation von mehreren Annotatorbenutzern in allen Dokumenten mit Überschneidungen innerhalb der Task angewendet wurde. Der Wert kann bis 1 ansteigen und auf einen negativen Wert absinken. Er kann als Indikator für Schwachstellen in den Annotationsrichtlinien oder bei bestimmten Annotatorbenutzern dienen. Die folgenden Richtlinien (*Landis und Koch, 1977*) können als Ausgangspunkt zum Beurteilen der Gesamtleistung dienen. 

<table style="width:60%" summary="Diese Tabelle enthält allgemeine Richtlinien für die Übereinstimmung der Annotatoren, um die Gesamtleistung zu beurteilen.">
  <caption>Tabelle 1. Richtlinien für die Übereinstimmung der Annotatoren</caption>
  <tr>
    <th style="vertical-align:bottom; text-align:center" id="d12741e148">Score</th>
    <th style="vertical-align:bottom; text-align:center" id="d12741e150">Grad der Übereinstimmung</th>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:center" headers="d12741e148">&lt; 0</td>
    <td style="vertical-align:top; text-align:center" headers="d12741e150">Schlecht</td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:center" headers="d12741e148">0,01 - 0,20</td>
    <td style="vertical-align:top; text-align:center" headers="d12741e150">Gering</td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:center" headers="d12741e148">0,21 - 0,40</td>
    <td style="vertical-align:top; text-align:center" headers="d12741e150">Akzeptabel</td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:center" headers="d12741e148">0,41 - 0,60</td>
    <td style="vertical-align:top; text-align:center" headers="d12741e150">Mittel</td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:center" headers="d12741e148">0,61 - 0,80</td>
    <td style="vertical-align:top; text-align:center" headers="d12741e150">Erheblich</td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:center" headers="d12741e148">0,81 - 1,0</td>
    <td style="vertical-align:top; text-align:center" headers="d12741e150">Optimal</td>
  </tr>
</table>

Der Score in den übrigen Spalten ist eine *F1-Kennzahl*. Sie gibt den Konsistenzgrad der Annotationen von zwei Annotatorbenutzern an. Der Wert kann im Bereich von 0 bis 1 liegen, wobei der Score-Wert 1 eine absolute Übereinstimmung bezeichnet. Ab welchem Wert ein akzeptabler Grad der Übereinstimmung erreicht wird, hängt von den jeweiligen Daten des Fachgebiets und vom Typsystem ab. Als Beispiel werden hier die F1-Schwellenwerte angeführt, die Projektleiter als Mindestwerte für Projekte ansetzen, die auf dem Typsystem KLUE basieren:

- Erwähnungen mit Entitätstypen: 0,85
- Beziehungen: 0,8
- Koreferenzketten: 0,9

Die Interpretation des Scores ist von der Komplexität Ihres Typsystems, der Menge und Komplexität der annotierten Inhalte, der Erfahrung des Annotatorbenutzers und von weiteren Faktoren abhängig. Wenn in der Annotationstask beispielsweise Wortarten gekennzeichnet werden sollen, ist ein hoher Score zu erwarten, da die Wortarten klar definiert sind. Bei einer Task, die eine tiefergehende Textanalyse und die Interpretation durch Benutzer erfordert, dürften die Scores niedriger liegen, bis geeignete Maßnahmen zur Klärung von Mehrdeutigkeiten getroffen werden.

Ein Typsystem mit zahlreichen Entitäts- und Beziehungstypen bietet im Allgemeinen mehr Interpretationsspielraum und weist daher in der Anfangsphase der Modellentwicklung eine geringere Übereinstimmung der Annotatoren auf. Die Scores zeigen Ihnen zum Beispiel, welche Entitätstypen niedrige Werte aufweisen. Solche niedrigen Scores sind ein Hinweis darauf, dass die Annotationsrichtlinien verbessert werden müssen. Die Scores für den Vergleich zwischen zwei Annotatorbenutzern geben an, ob ein bestimmter Annotator durchgängig niedrigere Scores erreicht als andere Annotatoren. Dieser Annotator hat möglicherweise Probleme damit, die Richtlinien zu verstehen oder die Annotationstools zu verwenden, und sollte gegebenenfalls weitere Schulungen erhalten.

## Scores für die Übereinstimmung der Annotatoren überprüfen
{: #wks_haaccuracy}

Um festzulegen, welche Dokumente in die Ground Truth hochgestuft werden sollten, müssen Sie die Scores für die Übereinstimmung der Annotatoren überprüfen. Dokumente mit niedrigen Sores kommen in Betracht, abgelehnt und zur Optimierung an die Annotatorbenutzer zurückgegeben zu werden.

### Informationen zu diesem Vorgang
{: #wks_haaccuracy_about}

Beim Überprüfen der Übereinstimmung zwischen Annotatoren untersuchen Sie Dokumente, die von mehr als einem Annotatorbenutzer annotiert wurden. Wenn ein Dokument nicht von mehreren Annotationsgruppen und Annotatorbenutzern gemeinsam genutzt wird, kann kein Wert für die Übereinstimmung der Annotatoren berechnet werden. Stellen Sie beim Hinzufügen von Annotationsgruppen für eine Task sicher, dass die Gruppen, die verglichen werden sollen, dieselben Dokumente mit Überschneidungen enthalten. Um die Dokumente anzuzeigen, die in einer Annotationsgruppe enthalten sind, öffnen Sie die Seite **Assets** > **Dokumente** klicken Sie auf die Registerkarte **Annotationsgruppen** und klicken Sie anschließend auf die Namen der Gruppen.

Es kann vorkommen, dass keine Dokumente mit Überschneidungen gefunden werden. Dies kann zum Beispiel der Fall sein, wenn Sie in zwei Durchgängen Annotationsgruppen erstellen und diese zur selben Task hinzufügen. Obwohl die Annotationsgruppen fast zur gleichen Zeit erstellt wurden, enthalten sie keine gleichen Dokumente. Ein weiteres Beispiel: Wenn Sie Annotationsgruppen erstellen, die Dokumente mit Überschneidungen enthalten, aber für jede Annotationsgruppe eine eigene Task erstellen, anstatt alle Annotationsgruppen zu einer einzigen Tasks hinzuzufügen, werden keine Dokumente mit Überschneidungen gefunden und die Übereinstimmung der Annotatoren kann nicht berechnet werden.

### Vorgehensweise
{: #wks_haaccuracy_procedure}

So beurteilen Sie die Übereinstimmung der Annotationen von Annotatorbenutzern:

1. Melden Sie sich als {{site.data.keyword.knowledgestudioshort}}-Administrator oder -Projektleiter an und wählen Sie Ihren Arbeitsbereich aus.
1. Wählen Sie die Seite **Modell für maschinelles Lernen** > **Annotationstasks** aus und öffnen Sie die Task, die Sie auswerten möchten.
1. Klicken Sie auf **Übereinstimmung der Annotatoren berechnen**. In der Standardansicht werden Übereinstimmungswerte für die annotierten Erwähnungen von je zwei Annotatorbenutzern angezeigt. In der oberen Zeile wird die Gesamtkonsistenz zwischen jeweils zwei Annotatoren angegeben. Die Tabelle darunter gibt den Konsistenzgrad der Annotationen für bestimmte Erwähnungen im Text an, die von den einzelnen Annotatorpaaren eingefügt wurden.
1. Wenn Sie untersuchen möchten, wie konsistent Beziehungen und Koreferenzen von jeweils zwei Annotatorbenutzern annotiert wurden, wählen Sie im ersten Menü **Beziehung** oder **Koreferenz** aus.
1. Wenn Sie untersuchen möchten, wie konsistent Entitäten, Beziehungen oder Koreferenzen in bestimmten Dokumenten mit Überschneidungen von je zwei Annotatorbenutzern annotiert wurden, wählen Sie im zweiten Menü **Dokument** aus und wählen Sie anschließend das Annotatorpaar aus, das Sie bewerten möchten.
1. Nachdem Sie die Scores geprüft haben, können Sie entscheiden, ob Annotationsgruppen, die den Status 'Übergeben' aufweisen, akzeptiert oder abgelehnt werden sollen. Nachdem eine Annotationsgruppe übergeben wurde, wird neben dem Namen der Annotationsgruppe ein Kontrollkästchen angezeigt. Führen Sie eine der folgenden Aktionen aus:

    - Wenn die Scores für die Übereinstimmung der Annotatoren für eine Annotationsgruppe akzeptabel sind, wählen Sie das Kontrollkästchen aus und klicken Sie auf **Akzeptieren**. Dokumente, die keine Überschneidungen mit anderen Annotationsgruppen aufweisen, werden in die Ground Truth hochgestuft. Dokumente, die Überschneidungen aufweisen, müssen zuerst eine Beurteilung durchlaufen, damit die Konflikte behoben werden können.
    - Wenn die Scores für die Übereinstimmung der Annotatoren für eine Annotationsgruppe nicht akzeptabel sind, wählen Sie das Kontrollkästchen aus und klicken Sie auf **Ablehnen**. Die betreffende Annotationsgruppe muss erneut von einem Annotatorbenutzer bearbeitet werden, um die Annotationen zu verbessern.

## Beurteilung
{: #wks_haperform}

Wenn mehrere Annotatorbenutzer dasselbe Dokument bearbeiten, kann es erforderlich sein, Inkonsistenzen zwischen den Annotationen zu beheben, bevor die Annotationen in die Ground Truth hochgestuft werden. Dieser Prozess für die Konfliktlösung wird als Beurteilung bezeichnet.

Beim Prüfen und Genehmigen von Annotationsgruppen, die von Annotatorbenutzern eingereicht wurden, werden Dokumente, die keine Überschneidungen mit anderen Annotationsgruppen aufweisen, in die Ground Truth hochgestuft. Dokumente mit Überschneidungen sollten erst hochgestuft werden, nachdem die Annotationen auf Konflikte überprüft wurden. Wenn Sie Abweichungen zwischen Annotationen feststellen, müssen Sie entscheiden, wie die Konflikte gelöst werden sollen. Wählen Sie dazu entweder in den Annotationen, die von Annotatorbenutzern eingefügt wurden, die zutreffende Annotation aus oder wählen Sie eine andere Annotation aus, die angewendet werden soll.

Ein Dokument ist für die Beurteilung verfügbar, wenn mindestens eine der folgenden Bedingungen zutrifft:

- Der Projektleiter genehmigt gleichzeitig zwei oder mehr Annotationsgruppen in einer Task und dasselbe Dokument ist in mindestens zwei der Annotationsgruppen enthalten (Dokument mit Überschneidungen).
- Der Projektleiter genehmigt eine weitere Annotationsgruppe, bevor Dokumente in den zuvor genehmigten Annotationsgruppen beurteilt werden. Wenn Sie ein Dokument mit Überschneidungen zwischen Annotationsgruppe A und Annotationsgruppe B genehmigen, die Annotationen in die Ground Truth hochstufen und anschließend eine weitere Annotationsgruppe C genehmigen, in der das gleiche Dokument enthalten ist, werden die Annotationen des neu annotierten Dokuments automatisch in die Ground Truth hochgestuft, da keine Konflikte mehr bestehen. Dabei ist zu beachten, dass die hochgestuften Annotationen aus Annotationsgruppe C die Ground Truth ersetzen, die bei der Beurteilung der Dokumente mit Überschneidungen aus den Annotationsgruppen A und B erstellt wurde. Wenn Sie die Annotationsgruppe C genehmigen, bevor Sie die Annotationen aus den Annotationsgruppen A und B hochstufen, können die Dokumente mit Überschneidungen in Gruppe C auf Konflikte geprüft und beurteilt werden.

Der Zeitaufwand für die Beurteilung nimmt im Laufe der Zeit ab, wenn Sie Zeit in die Verbesserung der Annotationsrichtlinien investieren. Durch das Angeben von Beispielen und das Klären potenzieller Missverständnisse können Sie den Annotatorbenutzern helfen, aus Fehlern zu lernen und Konflikte künftig zu vermeiden.

Beispiele für abweichende Annotierungen durch Annotatorbenutzer:

- **Erwähnungen**

    - Annotator_1 annotiert einen Textbereich als Erwähnung, den Annotator_2 nicht als Erwähnung annotiert.
    - Der Index von Annotator_1 beginnt oder endet vor bzw. nach dem Index von Annotator_2 (eine partielle Überschneidung oder ein untergeordneter Textbereich liegt vor).
    - Annotator_1 ordnet einen anderen Entitätstyp zu als Annotator_2.

- **Beziehungen**

    - Annotator_1 erstellt eine Beziehung zwischen zwei Erwähnungen, Annotator_2 jedoch nicht.
    - Annotator_1 und Annotator_2 erstellen eine Beziehung zwischen denselben Erwähnungen, jedoch mit verschiedenen Beziehungstypen.
    - Annotator_1 und Annotator_2 erstellen eine Beziehung zwischen denselben Erwähnungen, jedoch in umgekehrter Reihenfolge (ein seltener Fall, da die Beziehung zwischen der ersten und der zweiten Erwähnung durch das Typsystem beschränkt wird).

- **Koreferenzketten**

    - Die Koreferenzkette von Annotator_1 schließt Erwähnungen ein (oder aus), die in der Koreferenzkette von Annotator_2 ausgeschlossen (oder eingeschlossen) werden. Die Übereinstimmung der Entitäten zwischen Annotator_1 und Annotator_2 sollte bewertet werden.

## Annotationskonflikte beheben
{: #wks_haadjudicate}

In der Beurteilungsphase können Sie Annotationskonflikte in Dokumenten mit Überschneidungen überprüfen, bevor die Annotationen in die Ground Truth hochgestuft werden. Sie können die Annotationen vergleichen, die von zwei Annotatorbenutzern hinzugefügt wurden. Außerdem können Sie die Annotationen von Annotatorbenutzern mit der aktuellen Ground Truth vergleichen.

### Vorbereitungen
{: #wks_haadjudicate_prereq}

Klicken Sie auf [diesen Link ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.youtube.com/watch?v=EbexfsuXxoQ&amp;feature=youtu.be){: new_window}, um ein dreiminütiges Video über das Beurteilen von Dokumenten abzuspielen.

### Informationen zu diesem Vorgang
{: #wks_haadjudicate_about}

Nachdem Annotatorbenutzer ihre Annotationstasks abgeschlossen haben, müssen sie die resultierenden Annotationsgruppen zum Überprüfen einreichen. Durch das Auswerten der Scores für die Übereinstimmung der Annotatoren können Sie erkennen, wie dasselbe Dokument von jeweils zwei Annotatoren annotiert wurde. Wenn der Score für die Übereinstimmung der Annotatoren akzeptabel ist, können Sie die Annotationsgruppe genehmigen. Wenn für ein Dokument in der Task keine Überschneidungen zwischen Annotationsgruppen bestehen, werden die Annotationen für das genehmigte Dokument in die Ground Truth hochgestuft. Falls für ein Dokument Überschneidungen zwischen Annotationsgruppen bestehen, sollten Sie das Dokument beurteilen und Konflikte zwischen den Annotationen beheben, bevor die Annotationen in die Ground Truth hochgestuft werden.

Beispiel: Beim Beurteilen eines Dokuments stellen Sie fest, dass ein Annotator die Erwähnung `Barack Obama` mit dem Entitätstyp `MenschenPerson` annotiert hat. Von einem anderen Annotator wurde derselbe Textbereich als zwei Erwähnungen mit dem Entitätstyp `Person` für `Barack` und dem Entitätstyp `Person` für `Obama` annotiert. Damit das Modell für maschinelles Lernen ordnungsgemäß trainiert werden kann, sollten Sie diese Inkonsistenz beheben.

{{site.data.keyword.knowledgestudioshort}} unterstützt die gleichzeitige Beurteilung von zwei Annotationsgruppen oder die Beurteilung einer Annotationsgruppe und der aktuellen Ground Truth. Wenn ein Dokument Überschneidungen mit mehr als zwei Annotationsgruppen aufweist, führen Sie eine Beurteilung der beiden Annotationsgruppen durch, denen Sie die größte Konfidenz beimessen (z. B. weil Sie größeres Vertrauen in die Annotatorbenutzer haben), um die Ground Truth für das Dokument zu ermitteln. Beurteilen Sie anschließend die übrigen Annotationsgruppen mithilfe der Ergebnisse der vorherigen Beurteilung.

### Vorgehensweise
{: #wks_haadjudicate_procedure}

So können Sie Dokumente mit Überschneidungen anzeigen und Konflikte beheben:

1. Melden Sie sich als {{site.data.keyword.knowledgestudioshort}}-Administrator oder -Projektleiter an und wählen Sie Ihren Arbeitsbereich aus.
1. Wählen Sie die Seite **Modell für maschinelles Lernen** > **Annotationstasks** aus und öffnen Sie die Task, die Sie auswerten möchten.
1. Vergewissern Sie sich, dass mindestens zwei Annotationsgruppen den Status **In Konflikt** aufweisen.
1. Klicken Sie auf **Dokumente mit Überschneidungen auf Konflikte prüfen**. Die Dokumente, die Konflikte aufweisen, werden angezeigt.
1. Wenn Sie die Konflikte in einem Dokument mit Überschneidungen ignorieren und die zugehörigen Annotationen ohne Beurteilung in die Ground Truth hochstufen möchten, klicken Sie auf **Akzeptieren**.
1. Wenn Sie mit dem Beheben der Konflikte in einem Dokument mit Überschneidungen beginnen möchten, klicken Sie auf **Auf Konflikte prüfen**.
1. Wenn drei oder mehr Kandidaten für die Beurteilung vorhanden sind (darunter auch Annotationsgruppen, die von Annotatorbenutzern annotiert wurden und die aktuelle Ground Truth), wählen Sie zwei Kandidaten aus, die Sie beurteilen möchten, und klicken Sie auf **Auf Konflikte prüfen**. Wenn nur zwei Kandidaten vorhanden sind, wird das Beurteilungstool automatisch gestartet.

    Im Beurteilungstool wird angezeigt, für wie viele Erwähnungen, Beziehungen und Koreferenzketten Konflikte bestehen. Konflikte zwischen Erwähnungen müssen behoben werden, bevor Sie mit dem Beheben der Konflikte zwischen Beziehungen oder zwischen Koreferenzketten fortfahren können.

1. Klicken Sie auf einen Satz, der Konflikte enthält, um ihn hervorzuheben. Um sich ganz auf nicht behobene Konflikte zu konzentrieren, können Sie das Kontrollkästchen **Gelöst** abwählen und sicherstellen, dass das Kontrollkästchen **Nicht gelöst** ausgewählt ist.
1. Klicken Sie auf einzelne Annotationen und anschließend auf **Akzeptieren** oder **Ablehnen**. Um eine Entscheidung zu widerrufen, die Sie gerade getroffen haben, drücken Sie die Tastenkombination Strg+Z.

    Sie können auch mehrere Annotationen auswählen und anschließend auf das entsprechende Kontrollkästchen klicken, um die ausgewählten Annotationen zu akzeptieren oder abzulehnen. Wenn Sie die Auswahl einer Annotation aufheben möchten, machen Sie Ihre Auswahlen rückgängig, indem Sie auf den Leerraum zwischen den Sätzen klicken oder die Taste **Esc** drücken.

    Wenn zuvor bereits Annotationsrichtlinien mit dem Projekt verknüpft waren und Sie das Auswählen der richtigen Annotation unterstützen möchten, klicken Sie auf **Richtlinien anzeigen**. Wenn Sie über die entsprechenden Zugriffsberechtigungen für die Site verfügen, auf der die Richtlinien gehostet werden, können Sie die Richtlinien nach dem Öffnen aktualisieren (z. B. durch Hinzufügen von Erläuterungen und Beispielen).
    {: tip}

1. Wenn Sie einen anderen Entitätstyp auf eine Erwähnung anwenden möchten, lehnen Sie die aktuelle Annotation ab, wählen Sie die Erwähnung (z. B. `Barack Obama`) aus und wählen Sie anschließend den richtigen Entitätstyp (z. B. `Person`) aus.
1. Fahren Sie mit dem Akzeptieren, Ablehnen bzw. Überarbeiten von weiteren Konflikten in dem Satz fort. Klicken Sie nach dem Beheben aller Konflikte in einem Satz auf den Link **Alle Annotationen auswählen** und klicken Sie anschließend auf **Akzeptieren**.
1. Klicken Sie auf das Pfeilsymbol, um mit dem nächsten Satz fortzufahren. Setzen Sie den Vorgang fort, bis alle Konflikte für Erwähnungen in dem Dokument behoben sind.

    Um die bisherige Arbeit zu speichern oder die aktuelle Beurteilungssitzung vorübergehend zu unterbrechen, können Sie jederzeit auf **Speichern** klicken. Um alle von Ihnen vorgenommenen Änderungen zu verwerfen, klicken Sie auf **Verwerfen**. Wenn Sie die zuvor gespeicherte Beurteilungssitzung fortsetzen möchten, klicken Sie auf **Fortsetzen**, um die Beurteilung von Konflikten an der Stelle wiederaufzunehmen, an der sie zuletzt unterbrochen wurde. Wenn die vorherige Beurteilungssitzung beendet wurde, müssen Sie eine neue Beurteilungssitzung starten.
    {: tip}

1. Wechseln Sie nach dem Beheben von Erwähnungskonflikten den Beurteilungsmodus, um Konflikte zwischen Annotationen für Beziehungen oder Koreferenzketten zu beheben.

    - Der Vorgang zum Beheben von Konflikten im Beziehungsmodus entspricht weitgehend dem Beheben von Erwähnungskonflikten. Die Konfliktbehebung wird nacheinander für einzelne Sätze durchgeführt.
    - Koreferenzketten können sich über mehrere Sätze erstrecken. Wenn Sie in den Modus für Koreferenzen wechseln, listet das System in einem Anzeigebereich auf der rechten Seite die von den einzelnen Annotatorbenutzern erstellten Koreferenzketten auf. Wählen Sie die Ketten aus, die Sie beurteilen möchten, und klicken Sie anschließend auf **Kette ablehnen** oder **Kette akzeptieren**, um Annotationen in einer Kette zu akzeptieren bzw. abzulehnen, oder klicken Sie auf **Ketten zusammenführen**, um zwei Ketten zusammenzuführen. Wenn Sie eine Erwähnung aus einer Koreferenzkette entfernen möchten, klicken Sie im Dokumentbereich auf das Löschsymbol (-) in der Beschriftung über der Erwähnung.

1. Nachdem alle Konflikte in dem Dokument behoben wurden, klicken Sie auf **In Ground Truth hochstufen**.
