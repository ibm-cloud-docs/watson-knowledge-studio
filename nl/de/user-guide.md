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

Diese Dokumentation bezieht sich auf {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Die Dokumentation für die Vorgängerversion {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace kann über [diesen Link ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/docs/services/knowledge-studio/user-guide.html){: new_window} aufgerufen werden.
{: tip}

# Dokumente annotieren
{: #user-guide}

Die Informationen in diesem Abschnitt sollen Experten eines Fachgebiets dabei unterstützen, Dokumente aus ihrem Fachgebiet unter Verwendung des Ground Truth-Editors zu annotieren.
{: shortdesc}

## Auf Arbeitsbereiche zugreifen
{: #wks_access_for_annotator}

Sie einen Arbeitsbereich erst anzeigen, nachdem ein berechtigter Benutzer den Arbeitsbereich erstellt und Ihnen Zugriff auf den Arbeitsbereich erteilt hat.

Wenn ein Administrator Sie zu einer {{site.data.keyword.knowledgestudioshort}}-Instanz hinzufügt, wird Ihnen die Rolle des Annotatorbenutzers zugewiesen. Als Inhaber dieser Rolle dürfen Sie keinen Arbeitsbereich erstellen. Arbeitsbereiche müssen von einem Administrator erstellt werden. Anschließend muss der Administrator oder ein Projektleiter, der vom Administrator dem Arbeitsbereich zugeordnet wurde, die folgenden Schritte ausführen: 

1. Eine Annotationsgruppe erstellen und Ihnen zuordnen.
1. Eine Task erstellen, die Ihnen das Annotieren der zugehörigen Dokumente ermöglicht.

Sie können den Arbeitsbereich erst anzeigen, nachdem Ihnen eine Annotationstask zugeordnet wurde.

Wenn auf der Seite 'Arbeitsbereiche' keine Arbeitsbereiche angezeigt werden, obwohl Sie eingeladen wurden, an einem {{site.data.keyword.knowledgestudioshort}}-Arbeitsbereich mitzuwirken, bitten Sie die Person, von der Sie eingeladen wurden, die erforderlichen Schritte auszuführen.

## Best Practices für die Annotation
{: #wks_anno_bp}

Die vorliegenden Best Practices enthalten Anleitungen und Beispiele für den Einstieg in das Annotieren von Dokumenten.

- Annotieren Sie alle Dokumente vollständig und lückenlos.

    Der Prozess für maschinelles Lernen lernt aus Negativbeispielen (nicht annotierten Texten) ebenso wie aus annotierten Texten. Achten Sie daher sorgfältig darauf, was Sie annotieren und lassen Sie keine Lücken. Wenn Sie nur die ersten 5 von insgesamt 10 Dokumenten in einer Gruppe annotieren, lernt das Modell aus den nicht erfassten Annotationen in den letzten 5 Dokumenten, dass alle nicht erfassten Erwähnungen von Entitäten oder Beziehungen in diesen Dokumenten ignoriert werden sollen. Diese Unterlassung kann den gesamten Nutzen Ihrer gründlichen Arbeit an den ersten 5 Dokumenten zunichte machen.

- Konsistentes Annotieren ist mindestens genau so wichtig wie richtiges Annotieren.

    Manche Festlegungen in den Annotierungsrichtlinien sind unerheblich (z. B. ob die Ausstattungsvariante des Fahrzeugmodells Bestandteil des Modellnamens ist oder nicht, wie bei *Camry* oder *Camry LX*). Welche Richtlinie gewählt wird, fällt kaum ins Gewicht. Viel wichtiger ist, dass sich das Projektteam auf eine Richtlinie festlegt und sie beim Annotieren durchgängig anwendet.

- Beschriften Sie die Entitätserwähnungen nur an den Wortgrenzen, da die Suchfunktionen zur Erkennung von Erwähnungen auf der Granularitätsebene der Wortgrenzen arbeitet.because mention-detection search works at the word-token level of granularity.
- Beschriften Sie möglichst nur Entitätserwähnungen, die nicht mehr als zwei oder drei benachbarte Wörter umfassen.

    Dies ist nicht immer möglich oder einfach. Betrachten Sie die folgenden Beispiele:
    - Das Quellendokument enthält einen Satz, in dem (für die Zwecke der Anwendung, von der das Typsystem verwendet wird) das Problem und die zugehörige Ursache annotiert werden soll.

        ```
        Das elektronische Bauteil ist durchgebrannt, weil eine falsche Spannung angelegt wurde.
        ```
        {: screen}

        Es liegt nahe, das Problem und die Ursache wie folgt zu annotieren:

        ```
                    [PROBLEM]                           [URSACHE]
        ```
        {: screen}

        ```
        [Das elektronische Bauteil ist durchgebrannt,] [weil eine falsche Spannung angelegt wurde].
        ```
        {: screen}

        Es ist jedoch nicht empfehlenswert, solche langen Ausdrücke als Entitätstypen zu annotieren. Suchen Sie stattdessen die wichtigen Entitäten und geben Sie die Zuordnung dieser Entitäten zueinander an, indem Sie eine Beziehungserwähnung definieren.

        ```
               [POSITION]          [SYMPTOM]                [URSACHE]
        ```
        {: screen}

        ```
        Das [elektronische Bauteil] ist [durchgebrannt], weil eine [falsche Spannung] angelegt wurde.
        ```
        {: screen}

        ```
                      ^---istStatusVon--| |------verursachtDurch-------^
        ```
        {: screen}

    - Das Quellendokument enthält ein aufgespaltenes Verb, das annotiert werden soll. Wie kann nicht zusammenhängender Text als einzelner Entitätstyp annotiert werden? Indem jede Entitätserwähnung annotiert und beide durch eine Beziehungserwähnung als aufeinander bezogen gekennzeichnet werden.

        ```
                  [EREIGNIS_FOLGE]      [EREIGNIS_FOLGE]
        ```
        {: screen}

        ```
        Jedes Kind wartete an seiner Haustür, aber wir [holten] zuerst das jüngste Kind [ab].
        ```
        {: screen}

        ```
                            ^----aufgespaltenerTyp-----^
        ```
        {: screen}

- Vermeiden Sie Erwähnungen mit Überschneidungen, d. h. zwei verschiedene Entitätstypbezeichnungen, die auf einen einzelnen Ausdruck in einem Dokument angewendet werden. In dem Beispielsatz *Sie stiftete die Zeitschriften ihres Vaters der Willy-Brandt-Bibliothek.* entsteht eine Erwähnungsüberschneidung, wenn der einzelne Ausdruck *Willy-Brand-Bibliothek* mit Willy-Brandt=PERSON und Willy-Brandt-Bibliothek=POSITION annotiert wird. Der Ausdruck in diesem Satz bezieht sich mehr auf die Bibliothek als auf die Person, daher sollte nur die Bibliothek annotiert werden.

    Zum Decodieren solcher Strukturen sind mehrere parallele Aufrufe eines Modells für maschinelles Lernen erforderlich, da bei der Erkennung von Erwähnungen nur nach einer einzigen vorhandenen bzw. nicht vorhandenen Bezeichnung für jedes Worttoken gesucht wird.

- Legen Sie fest, wie das Team mit Listen und Pluralformen im laufenden Text umgehen soll. Beispiel: Im Typsystem KLUE werden die Entitätstypen PERSON und MENSCHEN verwendet, um Singular und Plural zu unterscheiden. Die Liste *Barack, Michelle, Malia und Sasha Obama* kann wahlweise wie folgt annotiert werden:

    - Annotieren Sie jedes Listenelement als einzelne Entitätserwähnung (*Barack*, *Michelle*, *Malia* und *Sasha Obama* sind einzelne Erwähnungen des Typs PERSON)
    - Annotieren Sie den ganzen Ausdruck als eine einzige Entitätserwähnung in Pluralform (*Barack, Michelle, Malia und Sasha Obama* ist eine einzige Erwähnung des Typs MENSCHEN).

    Keiner dieser beiden Ansätze ist für sich genommen besser als der andere. Sie sollten jedoch dafür sorgen, dass Ihr Team sich für einen davon entscheidet und diesen durchgängig auf alle Listen anwendet, die in den Dokumenten vorkommen.

- Eine Koreferenz wird verwendet, wenn Erwähnungen auf dieselbe Entität in der realen Welt verweisen. Beziehungen werden zwischen eigenständigen Entitäten verwendet. Daher sollten zwei Erwähnungen niemals durch eine Koreferenz und durch eine Beziehung verknüpft werden.

## Annotieren mit dem Ground Truth-Editor
{: #wks_hagte}

Wenn ein Annotatorbenutzer ein Dokument annotiert, wird das Dokument im Ground Truth-Editor geöffnet. Der Ground Truth-Editor ist ein grafisch orientiertes Tool, mit dem Annotatorbenutzer Bezeichnungen in Text einfügen.

Das Ziel der Annotatorbenutzer besteht darin, Erwähnungen, Beziehungen und koreferenzierte Erwähnungen zu beschriften, damit das Modell für maschinelles Lernen trainiert werden kann, diese Muster in neuen Texten zu erkennen. Annotieren Sie mit diesem Tool zumindest die Erwähnungen von Entitäten. Wenn die Anwendung, von der das resultierende Modell verwendet wird, keine Koreferenzen und Beziehungserwähnungen erkennen und extrahieren soll, dann müssen Sie keine Koreferenzen und Beziehungserwähnungen annotieren.

Die Konkordanz ist ein zusätzliches (optionales) Tool, mit dem Annotatorbenutzer das Annotieren häufig wiederholter Erwähnungen beschleunigen können.

Wählen Sie einen Modus für das manuelle Annotieren von Dokumenten aus:

- **Erwähnungsmodus**

    In diesem Modus ordnet der Annotatorbenutzer die im Typsystem definierten Entitätstypen aussagefähigen Wörtern oder Ausdrücken im Text zu. Beispiel: Allen Erwähnungen von Personennamen kann der Entitätstyp PERSON zugeordnet werden. Das Annotieren von Erwähnungen ist obligatorisch und muss vor dem Annotieren von Beziehungstypen und Koreferenzen für Erwähnungen durchgeführt werden.

    Der Annotatorbenutzer kann bei Bedarf mit dem Konkordanztool sicherstellen, dass identischer Text im ganzen Dokument und über Annotationsgruppen hinweg stets mit demselben Entitätstyp annotiert wird.

- **Beziehungsmodus**

    In diesem Modus verknüpft der Annotatorbenutzer Erwähnungen durch das Zuordnen eines Beziehungstyps, der im Typsystem definiert ist. Beispiel: Die Erwähnung 'John Smith' kann durch den Beziehungstyp 'beschäftigtBei' mit der Erwähnung '{{site.data.keyword.IBM_notm}}' verknüpft werden. Das Annotieren von Beziehungstypen ist optional und kann vor oder nach dem Annotieren von Erwähnungen als Koreferenzen erfolgen.

- **Koreferenzmodus**

    In diesem Modus identifiziert der Annotatorbenutzer Erwähnungen, die das gleiche Ding bezeichnen, um die durchgängige (konsistente) Verwendung von Annotationen zu gewährleisten, wenn nicht die gleichen Wörter verwendet werden. Beispiel: Die Erwähnung '{{site.data.keyword.IBM_notm}}' im ersten Satz, die Erwähnung 'International Business Machines' und die Erwähnung '{{site.data.keyword.IBM_notm}}' in einem späteren Satz bezeichnen dasselbe Ding und sollten daher alle mit demselben Entitätstyp (z. B. ORGANISATION) annotiert werden. Das Annotieren von Erwähnungen als Koreferenzen ist optional und kann vor oder nach dem Annotieren von Beziehungstypen erfolgen.

### Tipps zur Verwendung des Editors

- Speichern Sie den Arbeitsfortschritt regelmäßig.
- Wenn Ihnen ein Fehler unterläuft, können Sie die vorherige Aktion durch Drücken der Tastenkombination `Strg + Z` rückgängig machen. Um die widerrufene Aktion erneut auszuführen, drücken Sie die Tastenkombination `Strg + Y`. Sie können bis zu 10 Aktionen rückgängig machen, die Sie beim Bearbeiten des aktuellen Dokuments zuletzt ausgeführt haben. Nach dem Schließen des Dokuments ist dies nicht mehr möglich. Die Aktionen können nur in umgekehrter Reihenfolge widerrufen werden. Beim Widerrufen muss jeweils der Modus aktiviert sein, in dem die Aktion ursprünglich ausgeführt wurde. Aktionen, die mit dem Konkordanztool ausgeführt wurden, können nicht rückgängig gemacht werden.

## Entitätserwähnungen annotieren
{: #wks_haentity}

Beim Annotieren von Entitätserwähnungen wählt der Annotatorbenutzer eine Textzeichenfolge aus und ordnet eine Bezeichnung zu, die möglichst zutreffend beschreibt, was diese Textzeichenfolge darstellt. Als Bezeichnungen können die Entitätstypen zugeordnet werden, die im Typsystem des Arbeitsbereichs definiert sind.

### Informationen zu diesem Vorgang

Bevor Sie mit dem Annotieren der Entitätserwähnungen in einem Dokument beginnen, sollten Sie zunächst das ganze Dokument lesen. Auf diese Weise kann beim Annotieren der gesamte Kontext berücksichtigt werden. Dadurch erhalten Sie tiefere Einblicke in die Beziehungen zwischen Entitätserwähnungen und in die Koreferenzen, die möglicherweise bei weiteren Durchgängen durch das Dokument markiert werden sollten.

Wenn Sie ein Dokument zum Annotieren öffnen, können Sie bei Bedarf mit dem Konkordanztool zuerst wiederholt vorkommende Entitätserwähnungen annotieren und danach einzelne Entitätserwähnungen. Im Anschluss daran können Sie optional Beziehungserwähnungen und Koreferenzen in beliebiger Reihenfolge annotieren. Das Annotieren von Entitätserwähnungen ist obligatorisch. Ob Sie zusätzlich Beziehungserwähnungen und Koreferenzen annotieren, hängt vom Verwendungszweck Ihres Modells und den Anforderungen des betreffenden Fachgebiets ab. Solange Sie keine Koreferenzen angeben, wird jede Entitätserwähnung als eigenständige Entität eingestuft.

#### Tipps

- Kurze Entitätserwähnungen eignen sich besser zum Trainieren, da das Modell für maschinelles Lernen kürzere Muster leichter erkennen und mit den richtigen Annotationstoken versehen kann.
- Wenn Sie im Arbeitsbereich einen wörterverzeichnisbasierten Tokenizers verwenden und zusammengesetzte Begriffe und Interpunktion in Ihren Trainingsdaten verarbeiten möchten, können Sie die Betriffe zu einem Wörterverzeichnis hinzufügen und einen Wörterverzeichnisannotator zum Vorannotieren der Begriffe verwenden. Beispiel: Um Umbrüche für Begriffe, die Interpunktion enthalten, Umbrüche an Satzgrenzen zu vermeiden, fügen Sie Begriffe wie Yahoo! und Dr. zu einem Wörterverzeichnis hinzu. Falls Ihre Trainingsdaten Wörter mit Bindestrichen oder alphanumerische Akronyme wie Hi-C oder MS-60-70 enthalten, fügen Sie diese Begriffe ebenfalls zum Wörterverzeichnis hinzu. Wenn Vorkommen der Begriffe unabhgängig von der Groß-/Kleinschreibung annotiert werden, fügen Sie die Begriffe in Kleinschreibung hinzu (z. B. hi-c). Um Varianten zu annotieren, fügen Sie die Varianten als Oberflächenformen (z. B. MS-60-70 und MS 60 70) hinzu. **Wichtig**: Verwenden sie diese Vorgehensweise nicht, wenn Sie mit dem Standardtokenizer arbeiten.

### Vorgehensweise

So annotieren Sie Entitätserwähnungen in einem Dokument:

1. Melden Sie sich als Annotatorbenutzer an (oder als Administrator, dem Dokumente zum Annotieren zugeordnet wurden). Arbeitsbereiche mit Tasks, die Ihnen zugeordnet sind, werden angezeigt.
1. Öffnen Sie einen Arbeitsbereich und danach die Task, die Sie bearbeiten möchten. Die Ihnen zugeordneten Annotationsgruppen werden angezeigt.
1. Klicken Sie auf ein Dokument, um es zu öffnen. Das Dokument wird standardmäßig im Modus **Dokumentannotation** > **Erwähnung** geöffnet. In diesem Modus können Sie Entitätserwähnungen annotieren.
1. So annotieren Sie eine Entitätserwähnung:

    1. Klicken Sie auf ein Wort im Text, das Sie als Erwähnung eines bestimmten Entitätstyps aus dem Typsystem erkennen. Klicken Sie bei Entitätserwähnungen, die aus mehr als einem Wort bestehen, auf ein weiteres Wort oder ziehen Sie den Auswahlrahmen, um mehrere Wörter oder zusammengesetzte Wörter auszuwählen.
    1. Wählen Sie entweder im rechten Teilfenster den Entitätstyp aus, den Sie anwenden möchten, oder geben Sie die Tastenkombination für den Entitätstyp ein.

        Wenn bereits Annotationsrichtlinien mit dem Arbeitsbereich verknüpft waren und Sie Unterstützung beim Auswählen der zutreffenden Annotation benötigen, klicken Sie auf **Richtlinien anzeigen**. Wenn Sie über die entsprechenden Zugriffsberechtigungen für die Site verfügen, auf der die Richtlinien gehostet werden, können Sie die Richtlinien nach dem Öffnen aktualisieren (z. B. durch Hinzufügen von Erläuterungen und Beispielen).{: tip}

    1. Vermeiden Sie es, Erwähnungen mit Überschneidungen zu erstellen. Wenn jedoch eine Erwähnung mit Überschneidungen erforderlich ist, klicken Sie auf **Ersetzen**, um das Hinzufügen der Erwähnung zu vereinfachen. Eine Überschneidung tritt auf, wenn Sie mehr als eine Bezeichnung auf eine Entitätserwähnung anwenden. Prüfen Sie die folgenden Vorschläge:

        - Annotieren Sie 'Sub-Industrie' als eine Erwähnung und nicht nur 'Industrie' oder 'Sub'.
        - Erstellen Sie keine Annotation PERSON mit Überschneidung für das Element *JFK* in *JFK International Airport*. Die ganze Erwähnung *JFK International Airport* sollte nur als EINRICHTUNG bezeichnet werden.
        - Erstellen Sie für den Text *Chefs* keine zwei Annotationen (eine Annotation PERSON für *Chef* und eine Annotation MENSCHEN für *Chefs*. Annotieren Sie *Chefs* nur als Entitätstyp MENSCHEN.

        Wenn zu viele Erwähnungen mit Überschneidungen vorhanden sind, deutet dies in der Regel darauf hin, dass die Annotationsrichtlinien nicht eindeutig sind und durch bessere Beispiele für die Behandlung zusammengesetzter Wörter in Ihren Quellendaten ergänzt werden sollten.

    1. Um eine soeben hinzugefügte Annotation entfernen möchten, drücken Sie die Tastenkombination `Strg + Z`, um die Aktion rückgängig zu machen. Wenn Sie eine Entitätserwähnung zu einem späteren Zeitpunkt entfernen möchten, klicken Sie mit der linken Maustaste auf eine Erwähnung und drücken Sie die **Löschtaste** oder klicken Sie auf **Details anzeigen** und anschließend auf **X** neben dem zugewiesenen Entitätstyp für die Erwähnung.

1. Je nach Typsystem können Sie möglicherweise Attribute für eine Entitätserwähnung konfigurieren (z. B. zum Zuordnen einer Entitätsrolle oder eines Subtyps bzw. einer Erwähnungsklasse oder eines Typs). Wenn dies der Falls ist, wählen Sie eine Erwähnung aus und klicken Sie auf **Attributansicht**.

1. Durch Klicken auf **Speichern** können Sie Ihre Arbeit jederzeit speichern.

### Nächste Schritte

Nachdem Sie alle Entitätserwähnungen, Beziehungserwähnungen und Koreferenzen im Dokument nach Bedarf annotiert haben, ändern Sie den Dokumentstatus von **In Bearbeitung** in **Abgeschlossen**, klicken Sie auf **Speichern** und schließen Sie dann das Dokument.

Nachdem Sie alle Dokumente vollständig annotiert und als **Abgeschlossen** markiert haben, wird der Status der Annotationsgruppe in **Übergeben** geändert. Daran erkennen die Projektleiter, dass sie mit dem Beurteilen der Dokumente im Hinblick auf die Übereinstimmung zwischen den Annotatoren beginnen können, und die Dokument abzulehnen oder zu akzeptieren und in die Ground Truth hochzustufen.

## Wiederkehrende Erwähnungen annotieren
{: #wks_haconcordance}

Mit dem optionalen Konkordanztool können Sie mehrere Vorkommen einer Erwähnung auf einmal annotieren. Das Tool bietet die Möglichkeit, den gleichen Text innerhalb eines Dokuments und über Annotationsgruppen hinweg konsistent mit dem gleichen Entitätstyp zu annotieren. Mit diesem Tool können Sie die konsistente Annotierung in mehreren Dokumenten gewährleisten. Sie können beispielsweise im Erwähnungsmodus jedes Vorkommen der Erwähnung 'Verschlüsselung' einzeln annotieren oder mit dem Konkordanztool alle Vorkommen der Erwähnung 'Verschlüsselung' annotieren. Bei beiden Vorgehensweisen lernt das Modell aus dem Entitätstyp, den Sie auf die Erwähnung anwenden.

### Informationen zu diesem Vorgang

Obwohl das Konkordanztool optional ist, empfiehlt es sich, Erwähnungen in einem Dokument oder dokumentübergreifend mit diesem Tool zu annotieren, bevor Sie mit dem Annotieren von Erwähnungen in einzelnen Dokumenten beginnen. Wenn Sie mit dem Konkordanztool einen Entitätstyp auf eine Erwähnung anwenden, wendet das System diesen Entitätstyp auf alle entsprechenden Erwähnungen an und überschreibt dabei alle vorhandenen Entitätstypen, die einer entsprechenden Erwähnung zugeordnet sind. Zur Vermeidung von Konflikten werden Attribute (z. B. Rollen oder Subtypen) für vorhandene Entitätstypen entfernt, wenn mit dem Konkordanztool ein neuer Entitätstyp angewendet wird.

### Vorgehensweise

So annotieren Sie wiederkehrende Erwähnungen:

1. Melden Sie sich als Annotatorbenutzer an (oder als Administrator bzw. Projektleiter, dem Dokumente zum Annotieren zugeordnet wurden). Arbeitsbereiche mit Tasks, die Ihnen zugeordnet sind, werden angezeigt.
1. Öffnen Sie einen Arbeitsbereich und danach die Task, die Sie bearbeiten möchten. Die Ihnen zugeordneten Annotationsgruppen werden angezeigt.
1. Klicken Sie auf ein Dokument, um es zu öffnen. Das Dokument wird standardmäßig im Modus **Dokumentannotation** > **Erwähnungen** geöffnet.
1. Wenn Sie bisher noch keine Annotationen hinzugefügt haben, fügen Sie mindestens eine Annotation hinzu. Wählen Sie ein Wort oder eine Wortfolge aus, die die Erwähnung eines Entitätstyps aus Ihrem Typsystem repräsentiert, und ordnen Sie ihr den entsprechenden Typ zu. Klicken Sie auf **Speichern**, um Ihre Annotation zu speichern.
1. Wählen Sie ein einzelnes Vorkommen von wiederkehrendem Text aus, das Sie annotieren möchten, und klicken Sie anschließend auf **Konkordanz**.
1. Wählen Sie die Dokumente aus, auf den Sie den ausgewählten Entitätstyp anwenden möchten. Sie können die Annotationen in allen Dokumenten erstellen, die Ihnen zum Annotieren zugeordnet sind, in allen Dokumenten, mit deren Annotierung Sie bereits begonnen haben, oder in allen Dokumenten, mit deren Annotierung Sie noch nicht begonnen haben. Klicken Sie auf **Vorschau**, um die Annotationen anzuzeigen, die hinzugefügt werden.
1. Wenn Sie die Annotationen im größeren Kontext anzeigen möchten, klicken Sie auf die Symbole, um die Vorschau des Dokumentinhalts anzuzeigen, oder das Dokument in einem neuen Fenster zu öffnen.
1. Klicken Sie auf **Anwenden & überprüfen**, um die ausgewählten Entitätstypen auf Erwähnungen in den ausgewählten Dokumenten anzuwenden. Sie können die Annotationen, die hinzugefügt werden, anschließend überprüfen. Wenn eine Annotation in einem bestimmten Kontext nicht zutreffend ist, können Sie das betreffende Vorkommen entfernen, indem Sie auf das Symbol 'Bearbeiten' klicken und die Entitätstypzuordnung für die Erwähnung entfernen.
1. Wenn die Liste Der Annotationen Ihren Erwartungen entspricht, klicken Sie auf **Zurück zum Ground Truth-Editor**. 

### Ergebnisse

Die Erwähnungen im Dokument sind annotiert. Es gibt keine Möglichkeit, die Gruppe der Erwähnungen, die Sie mit dem Konkordanztool hinzugefügt haben, auf einmal zu entfernen. Sie müssen jede Erwähnung einzeln entfernen.

## Erwähnungen als Koreferenzen annotieren
{: #wks_hacoref}

Um Erwähnungen als Koreferenzen für dieselbe Entität zu annotieren, wählte der Annotatorbenutzer jedes Vorkommen einer Erwähnung aus, die auf dasselbe Ding verweist. Durch das Konzept der Koreferenz kann ein Modell leichter erkennen, dass Entitäten, die in unterschiedlicher Weise referenziert werden, derselben Entität zugeordnet werden sollen (z. B. der Name und die Abkürzung eines Bundesstates der Vereinigten Staaten, der Name und das Akronym eines Unternehmens oder ein Personenname und ein Pronomen, das auf diese Person verweist).

### Vorbereitungen

Sie müssen zuerst die Erwähnungen in einem Dokument annotieren, bevor Sie Koreferenzen angeben können.

### Informationen zu diesem Vorgang

Wenn Sie Erwähnungen als Koreferenzen annotieren, wird vom System eine Koreferenzkette erstellt. Mithilfe dieser Kette können Sie alle Erwähnungen im Kontext anzeigen und überprüfen, dass alle Vorkommen unter derselben Entität zusammengefasst werden können. Beispiel 'Barack', 'Michelle', 'er' und 'sie' gehören alle dem Entitätstyp PERSON an, aber 'Barack' und 'er' sind eine Entität, während 'Michelle' und 'sie' eine andere Entität sind. In diesem Beispiel erstellen Sie zwei Koreferenzketten.

Beim Erstellen einer Koreferenzkette müssen Sie Erwähnungen auswählen, die mit demselben Entitätstyp markiert wurden. In manchen Fällen kann es jedoch vorkommen, dass Sie Erwähnungen verschiedener Typen in dieselbe Koreferenzkette einschließen möchten. Dazu müssen  Sie mehrere Ketten erstellen und anschließend zusammenführen. Stellen Sie sich beispielsweise vor, dass Menschen gerne Kurzformen verwenden, um Wiederholungen im Text zu vermeiden. In einem Bericht über einen Verkehrsunfall ist möglicherweise 'Honda Accord Sedan 2004' der erste Hinweis auf ein Fahrzeug. Im weiteren Verlauf des Berichts bezeichnet der Autor das Fahrzeug als 'Accord' und später vielleicht einfach als 'Fahrzeug'. Wenn das Typsystem Einträge für Fahrzeughersteller, -modell und -typ enthält, könnten Sie mehrere Koreferenzketten für die einzelne Entitätstypen erstellen und diese anschließend zu einer konsolidierten Kette zusammenführen. Die zusammengeführte Kette hilft dem Modell für maschinelles Lernen zu erkennen, dass alle diese Erwähnungen auf dasselbe Ding verweisen.

Eine andere Methode zum Kombinieren von Erwähnungen verschiedener Entitätstypen ist das Erstellen einer Kette mit Erwähnungen eines einzigen Entitätstyps. Sie können nun auf eine Erwähnung eines anderen Entitätstyps klicken und anschließend auf die Kette, die Sie erstellt haben, um die Erwähnung zu der Kette hinzuzufügen.

Abhängig von Ihren Annotationsrichtlinien möchten Sie möglicherweise Koreferenzketten für Verben und Substantive erstellen, wenn die Verben dieselbe Instanz einer Aktion erwähnen. Wenn zum Beispiel zwei Erwähnungen des Verbs 'verschlüsselt' auf dasselbe Vorkommen von Verschlüsselung verweisen, können Sie die Erwähnungen als Koreferenzen annotieren. Wenn jedoch einer der Verweise auf 'verschlüsselt' ein allgemeiner Verweis ist oder wenn beide Vorkommen auf zwei verschiedene Verschlüsselungsvorgänge verweisen, sollten sie nicht als Koreferenzen annotiert werden. Wenn zwei verschiedene Verben auf dasselbe Vorkommen einer Aktion verweisen, kann es sinnvoll sein, die Erwähnungen als Koreferenzen zu annotieren. Beispiel: In der Aussage 'Er verschlüsselte das Dokument und versendete die Datei nach der Verarbeitung' könnten die Erwähnungen 'verschlüsselte' und 'Verarbeitung' als Koreferenzen annotiert werden, da sie auf dieselbe Instanz einer Aktion verweisen.

Die Konsistenz hat oberste Priorität. Entscheiden Sie, wie Koreferenzen annotiert werden sollen, und legen Sie die Regeln klar und deutlich (mit Beispielen) in Ihren Annotationsrichtlinien fest.

### Vorgehensweise

So annotieren Sie Erwähnungen als Koreferenzen:

1. Klicken Sie auf **Dokumentannotation** > **Koreferenzen**.
1. So erstellen Sie eine Koreferenzkette:

    1. Arbeiten Sie das Dokument durch und klicken Sie auf jede Erwähnung, die dasselbe Ding bezeichnet und mit demselben Entitätstyp beschriftet ist. Klicken Sie beispielsweise auf jedes Vorkommen von '{{site.data.keyword.IBM_notm}}', 'International Business Machines' und '{{site.data.keyword.IBM_notm}} Corp.', unter der Prämisse, dass alle diese Erwähnungen dem Entitätstyp ORGANISATION angehören.
    1. Doppelklicken Sie auf die letzte Erwähnung, die Sie zu der Kette hinzufügen möchten. In der Seitenleiste wird eine Koreferenzkette erstellt. Der Name der Kette stimmt mit der ersten Erwähnung überein, die Sie ausgewählt haben.
    1. Um alle Erwähnungen in einer Kette hervorzuheben und im Kontext zu überprüfen, bewegen Sie den Mauszeiger auf die Kette in der Seitenleiste.

1. In der Liste für einzelne Erwähnungen werden die Begriffe im Dokument angezeigt, die zwar annotiert, jedoch nicht zu einer Kette hinzugefügt wurden. Wenn Sie in der Liste eine Erwähnung finden, die in eine Kette gehört, können Sie diese Erwähnung von hier aus zu der Kette hinzufügen.

    1. Klicken Sie in der Liste für einzelne Erwähnungen in der Seitenleiste auf die betreffende Erwähnung.
    1. Wählen Sie in der Dropdown-Liste unterhalb der Beschreibung der Erwähnung die Nummer der Kette aus, zu der die Erwähnung hinzugefügt werden soll.
    1. Klicken Sie auf **Zusammenführen**, um die Erwähnung zur Kette hinzuzufügen, und klicken Sie anschließend auf **OK**.

    Die Erwähnung wird aus der Liste der einzelnen Erwähnungen entfernt und die Nummer der Kette, zu der sie jetzt gehört, wird im Dokument unterhalb der Erwähnung angezeigt.

1. Wenn Sie eine soeben hinzugefügte Koreferenzkette entfernen möchten, drücken Sie die Tastenkombination `Strg + Z`, um die Aktion rückgängig zu machen. Um eine Koreferenzkette später zu entfernen, klicken Sie in der Seitenleiste 'Koreferenzketten' auf das **X** neben der Kette, die Sie entfernen möchten. Um eine einzelne Erwähnung aus der Kette zu entfernen, klicken Sie auf die Koreferenz-ID, um ein Listenfenster mit den Erwähnungen in der Kette anzuzeigen, und klicken Sie anschließend auf das **X** neben der Erwähnung, die Sie entfernen möchten.
1. Durch Klicken auf **Speichern** können Sie Ihre Arbeit jederzeit speichern.

### Nächste Schritte

Nachdem Sie alle Entitätserwähnungen, Beziehungserwähnungen und Koreferenzen im Dokument nach Bedarf annotiert haben, ändern Sie den Dokumentstatus von **In Bearbeitung** in **Abgeschlossen**, klicken Sie auf **Speichern** und schließen Sie dann das Dokument.

Nachdem Sie alle Dokumente vollständig annotiert und als **Abgeschlossen** markiert haben, wird der Status der Annotationsgruppe in **Übergeben** geändert. Daran erkennen die Projektleiter, dass sie mit dem Beurteilen der Dokumente im Hinblick auf die Übereinstimmung zwischen den Annotatoren beginnen können, und die Dokument abzulehnen oder zu akzeptieren und in die Ground Truth hochzustufen.

## Beziehungen annotieren
{: #wks_harelation}

Beim Annotieren von Beziehungserwähnungen sucht der Annotatorbenutzer Textbelege für eine Beziehung zwischen zwei Entitätserwähnungen in einem Satz und wendet anschließend eine Bezeichnung an, die den Beziehungstyp möglichst zutreffend beschreibt. Als Bezeichnungen können Beziehungstypen angewendet werden, die im Typsystem des Arbeitsbereichs definiert sind.

### Vorbereitungen

Sie müssen zuerst Entitätserwähnungen in dem Dokument annotierten, bevor Sie Beziehungstypen zwischen ihnen definieren können.

### Informationen zu diesem Vorgang

Die Beziehungserwähnung kann nur definiert werden, wenn die Beziehung zwischen den beiden Entitätserwähnungen im Text explizit beschrieben wird. Explizite Textbelege können Possessive, Subjekt/Verb/Objekt-Strukturen oder Beifügungen sein. Im folgenden Beispielsatz ist es nicht zutreffend, die Beziehungserwähnung **EigentumVon** zwischen *Hund* und *Eigentümer* hinzuzufügen.

<pre><code>NICHT ZUTREFFEND: Der <u>Hund</u> bekam ein Leckerchen von seinem <u>Eigentümer</u>.</code></pre>

Die zutreffende Beziehungserwähnung besteht zwischen *seinem* und *Eigentümer*, da die Beziehung zwischen dem Hund und seinem Herrchen in diesem Teil des Satzes explizit definiert wird. *Eigentümer* kann der Eigentümer eines Hauses sein oder der Eigentümer eines anderen Hundes, aber der Text stellt klar, dass der am Anfang des Satzes erwähnte Hund Eigentum dieser Person ist.

<pre><code>ZUTREFFEND: Der Hund bekam ein Leckerchen von <u>seinem</u> <u>Eigentümer</u>.</code></pre>

<pre><code>                                |EigentumVon^</code></pre>

Die Forderung, dass beide Entitätserwähnungen und der Text, der den Typ der Beziehung zwischen ihnen definiert, im einem einzigen Satz enthalten sein müssen, erscheint möglicherweise sehr streng zu sein. Beachten Sie jedoch Folgendes: Wenn Sie im obigen Beispiel außerdem Koreferenzen im Dokument identifizieren, können Sie Beziehungserwähnungen in Sätzen identifizieren, die Wörter für informelle Entitätserwähnungen (z. B. Pronomen) enthalten. Beispiel: Der zweite der beiden Sätze *Mary hat Informatik studiert. Sie arbeitet für {{site.data.keyword.IBM_notm}}.* einen gültigen Textbeleg für eine Beziehung **beschäftigtBei** zwischen Mary und {{site.data.keyword.IBM_notm}} enthält. Die Koreferenz *Sie* wird als Verweis auf den Entitätstyp PERSON für *Mary* verstanden. Erst durch das Identifizieren einer Koreferenz zwischen *Mary* und *Sie* zusammen mit dem Identifizieren einer Beziehungserwähnung zwischen *Sie* und *{{site.data.keyword.IBM_notm}}* kann diese Beziehung vollständig erfasst werden. Die zutreffende Methode zum Annotieren dieser Beziehungserwähnung sieht so aus:

<pre><code>Mary[<i>#1</i>] hat Informatik studiert. <u>Sie</u>[<i>#1</i>] arbeitet für <u>IBM</u>.</code></pre>

<pre><code>                         |----beschäftigtBei----^</code></pre>

Die tiefgestellte Angabe [<i>#1</i>] gibt an, dass *Mary* und *Sie* zwei Glieder der ersten Koreferenzkette im Dokument sind.

### Vorgehensweise

So annotieren Sie Beziehungserwähnungen zwischen Entitätserwähnungen in einem Dokument:

1. Klicken Sie auf **Dokumentannotation** > **Beziehungen**.
1. So annotieren Sie eine Beziehung:

    1. Klicken Sie auf eine Entitätserwähnung im Text und anschließend auf eine Entitätserwähnung im selben Satz, die Sie mit der ersten Erwähnung verknüpfen möchten.
    1. Wählen Sie den Beziehungstyp, den Sie anwenden möchten, entweder in der rechten Seitenleiste aus oder geben Sie die Tastenkombination für den Beziehungstyp ein. Die Liste der verfügbaren Beziehungstypen wird durch die erste Entitätserwähnung eingeschränkt, die Sie auswählen, und sie wird zusätzlich durch die zweite Entitätserwähnung eingeschränkt. In manchen Fällen bleibt nur ein einziger Beziehungstyp übrig. Dennoch müssen Sie den Beziehungstyp, der angewendet werden soll, explizit auswählen.

        Wenn bereits Annotationsrichtlinien mit dem Arbeitsbereich verknüpft waren und Sie Unterstützung beim Auswählen der zutreffenden Annotation benötigen, klicken Sie auf **Richtlinien anzeigen**. Wenn Sie über die entsprechenden Zugriffsberechtigungen für die Site verfügen, auf der die Richtlinien gehostet werden, können Sie die Richtlinien nach dem Öffnen aktualisieren (z. B. durch Hinzufügen von Erläuterungen und Beispielen).{: tip}

1. Wenn Sie eine soeben hinzugefügte Beziehungserwähnung entfernen möchten, drücken Sie die Tastenkombination `Strg + Z`, um die Aktion rückgängig zu machen. Um eine Beziehungserwähnung später zu entfernen, können Sie mit der linken Maustaste auf den Beziehungstyp klicken und dann die **Löschtaste** drücken oder das **X** neben dem Beziehungstyp klicken.
1. Je nach Typsystem können Sie möglicherweise Attribute für eine Beziehung konfigurieren (z. B. zum Zuordnen einer Zeitform, Modalität oder Klasse für die Beziehung). Wenn dies der Fall ist, wählen Sie eine Beziehungsbezeichnung aus und klicken Sie auf **Attributansicht**.
1. Durch Klicken auf **Speichern** können Sie Ihre Arbeit jederzeit speichern.

### Nächste Schritte

Nachdem Sie alle Entitätserwähnungen, Beziehungserwähnungen und Koreferenzen im Dokument nach Bedarf annotiert haben, ändern Sie den Dokumentstatus von **In Bearbeitung** in **Abgeschlossen**, klicken Sie auf **Speichern** und schließen Sie dann das Dokument.

Nachdem Sie alle Dokumente vollständig annotiert und als **Abgeschlossen** markiert haben, wird der Status der Annotationsgruppe in **Übergeben** geändert. Daran erkennen die Projektleiter, dass sie mit dem Beurteilen der Dokumente im Hinblick auf die Übereinstimmung zwischen den Annotatoren beginnen können, und die Dokument abzulehnen oder zu akzeptieren und in die Ground Truth hochzustufen.

## Zugehörige Informationen

[Wörterverzeichnisse](/docs/services/watson-knowledge-studio/dictionaries.html)

[Fehlerbehebung im Ground Truth-Editor](/docs/services/watson-knowledge-studio/user-guide-help.html)

[Typsysteme](/docs/services/watson-knowledge-studio/typesystem.html)
