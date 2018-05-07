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

Diese Dokumentation bezieht sich auf {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Die Dokumentation für die Vorgängerversion {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace kann über [diesen Link ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/docs/services/knowledge-studio/tutorials-create-rule-model.html){: new_window} aufgerufen werden.
{: tip}

# Regelbasiertes Modell erstellen
{: #wks_tutrule_intro}

In diesem Lernprogramm erfahren Sie, wie Sie ein regelbasiertes Modell erstellen können, mit dem Textmuster, die Sie definieren, in Dokumenten gefunden werden können.{: shortdesc}

Sie erstellen ein Modell, das in Dokumenten Text finden kann, der mit dem Muster `Tag des Monats, Jahr` übereinstimmt. Das erstellte Modell kann zum Beispiel die Datumsangabe *1. Mai 2010* finden. Bevor Sie das eigentliche Regelmuster definieren, erstellen Sie Artefakte zum Definieren des Musters. Dazu gehören eine Wörterverzeichnisklasse zum Erkennen der erwähnten Monate sowie eine Klasse für reguläre Ausdrücke zum Erkennen der erwähnten Jahre im Text.

## Lernziele

Nach dem Durcharbeiten dieses Lernprogramms können Sie die folgenden Tasks ausführen:

- Klassen erstellen
- Dokumente zum Definieren von Regeln hinzufügen
- Klassen für Wörterverzeichnisse zuordnen
- Reguläre Ausdrücke zum Erfassen von Zeichenfolgen definieren
- Regeln definieren

Das Durcharbeiten dieses Lernprogramms dauert ungefähr 30 Minuten. Wenn Sie weitere Konzepte im Zusammenhang mit diesem Lernprogramm erkunden, kann das Durcharbeiten länger dauern.

## Vorbereitungen

- Vergewissern Sie sich, dass Sie einen unterstützten Browser verwenden. Weitere Informationen finden Sie unter [Browseranforderungen](/docs/services/watson-knowledge-studio/system-requirements.html).
- Sie haben das [Lernprogramm: Arbeitsbereich erstellen](/docs/services/watson-knowledge-studio/tutorials-create-project.html) erfolgreich abgeschlossen.
- Sie verfügen über mindestens eine Benutzer-ID mit der Rolle 'Administrator' oder 'ProjectManager'. Informationen zu Benutzerrollen finden Sie unter [Team zusammenstellen](/docs/services/watson-knowledge-studio/team.html).

## Ergebnisse

Nachdem Sie das regelbasierte Modell erstellt haben, können Sie es auf eine der folgenden Arten verwenden, um Textmuster in Dokumenten zu finden:

- Sie können Ihre [Dokumente vorannotieren](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotrule), bevor Sie ein Modell für maschinelles Lernen erstellen
- Sie können das [Modell bereitstellen oder exportieren](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html), um es in anderen {{site.data.keyword.watson}}-Services oder -Produkten zu verwenden

## Lerneinheit 1: Wörterverzeichnis der Monate hinzufügen
{: #wks_tutless_rule1}

In dieser Lerneinheit erfahren Sie, wie Sie ein Wörterbuch zu einem Arbeitsbereich in {{site.data.keyword.knowledgestudioshort}} hinzufügen. Das Wörterbuch enthält Begriffe, die sich auf die Monate des Jahres beziehen.

### Informationen zu diesem Vorgang

In einer späteren Lerneinheit definieren Sie eine Klasse auf der Basis dieses Wörterverzeichnisses. Nach dem Erstellen dieser Klasse werden alle Begriffe aus dem Wörterverzeichnis, die in den Dokumenten gefunden werden, automatisch als Erwähnungen des Klassentyps annotiert. Weitere Informationen zu Wörterverzeichnissen finden Sie unter [Wörterverzeichnisse zu einem Arbeitsbereich hinzufügen](/docs/services/watson-knowledge-studio/dictionaries.html#wks_projdictionaries).

### Vorgehensweise

1. Laden Sie die Datei <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/dictionary-items-month.csv" download>`dictionary-items-month.csv` <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link" class="style-scope doc-content"></a> in Ihren Computer herunter. Diese Datei enthält Wörterverzeichnisbegriffe im CSV-Format, die in ein {{site.data.keyword.knowledgestudioshort}}-Wörterverzeichnis hochgeladen werden können.
1. Wählen Sie in der Seitenleiste **Assets & Tools** > **Vorannotatoren** die Registerkarte **Wörterverzeichnisse** aus und klicken Sie auf **Wörterverzeichnisse verwalten**.
1. Klicken Sie auf die Schaltfläche **Wörterverzeichnis erstellen**, um ein Wörterverzeichnis hinzuzufügen.
1. Geben Sie in das Feld **Name** die Zeichenfolge `Wörterverzeichnis der Monate` ein und klicken Sie auf **Speichern**, um das leere Wörterverzeichnis zu erstellen. Das neue Wörterverzeichnis wird erstellt und automatisch zum Bearbeiten geöffnet.
1. Klicken Sie im Wörterverzeichnisfenster auf **Hochladen**.
1. Wählen Sie im Fenster 'Wörterverzeichniseinträge hochladen' die Datei `dictionary-items-month.csv` auf Ihrem Computer aus und klicken Sie anschließend auf **Hochladen**.

    Die Begriffe aus der Datei werden in das Wörterverzeichnis importiert.

## Lerneinheit 2: Beispieldokumente hinzufügen
{: #wks_tutless_rule2}

In dieser Lerneinheit erfahren Sie, wie Sie Dokumente mit linguistischen Muster hinzufügen, die Regeltypen veranschaulichen, die Sie definieren möchten.

### Informationen zu diesem Vorgang

Weitere Informationen zum Hinzufügen von Dokumenten finden Sie unter [Dokumente zum Definieren von Regeln hinzufügen](/docs/services/watson-knowledge-studio/rule-annotator-add-doc.html).

### Vorgehensweise

1. Laden Sie die Datei <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/documents-new.csv" download>`documents-new.csv` <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link" class="style-scope doc-content"></a> in Ihren Computer herunter. Diese Datei enthält Beispieldokumente, die hochgeladen werden können.
1. Klicken Sie in der Seitenleiste auf **Dokumentannotation** > **Regeln**.
1. Klicken Sie auf das Symbol **Dokument hinzufügen** neben **Dokumente**.
1. Klicken Sie auf die Registerkarte **CSV-Datei hochladen**.
1. Klicken Sie, um die Datei `documents-new.csv` zu lokalisieren und auszuwählen, die Sie zuvor in Ihren Computer heruntergeladen haben, und klicken Sie anschließend auf **Hochladen**.

    Auf der Hauptseite für Dokumente wird eine Dokumentgruppe angezeigt.

    ![Zeigt drei der vierzehn Dokumente, die zum Regeleditor hinzugefügt wurden. Zeigt den Dokumenttitel sowie einen Auszug aus dem Anfang jedes Dokuments.](images/rule-doc-add3.jpg)

## Lerneinheit 3: Klassen erstellen
{: #wks_tutless_rule3}

In dieser Lerneinheit erfahren Sie, wie Sie Klassen definieren, die Sie später zum Definieren einer Regel verwenden werden.

### Informationen zu diesem Vorgang

Weitere Informationen zu Klassen finden Sie unter [Regeln](/docs/services/watson-knowledge-studio/rule-annotator.html).

### Vorgehensweise

1. Klicken Sie auf der Seite **Regeln** für Ihren Arbeitsbereich auf das Symbol **Klasse hinzufügen** neben **Klasse** in der rechten Seitenleiste.

1. Geben Sie `WörterverzMonate` als Namen für die Klasse ein und klicken Sie anschließend auf **Hinzufügen**.

    Die neue Klasse wird in der Seitenleiste 'Klasse' angezeigt.

## Lerneinheit 4: Einer Klasse ein Wörterverzeichnis zuordnen
{: #wks_tutless_rule4}

In dieser Lerneinheit erfahren Sie, wie ein Wörterverzeichnis im Regeleditor verwendet wird.

### Vorgehensweise

1. Wählen Sie in der Seitenleiste **Dokumentannotation** > **Wörterverzeichnisse** aus und klicken Sie anschließend auf das **Wörterverzeichnis der Monate**, das Sie zuvor erstellt haben.

1. Wählen Sie in der Liste **Klasse** den Eintrag `WörterverzMonate` aus und klicken Sie anschließend auf **Speichern**.

    Die Klasse wird dem Wörterverzeichnis zugeordnet.

    ![Zeigt die Klasse 'WörterverzMonate', die dem Wörterverzeichnis der Monate zugeordnet ist, in der Ansicht 'Wörterverzeichnisse' der Seite 'Regel'.](images/rule-dict-map2.jpg)

### Ergebnisse

In Dokumenten, die dem Regeleditor zugeordnet sind, werden alle Verweise auf Begriffe im Wörterverzeichnis als Erwähnungen der Klasse `WörterverzMonate` annotiert. In der nächsten Einheit wird nachgewiesen, dass diese Verweise annotiert wurden.

## Lerneinheit 5: Klassenannotationen in Dokumenten finden
{: #wks_tutless_rule5}

In dieser Lerneinheit erfahren Sie, wie Klassenannotationen in Dokumenten im Regeleditor lokalisiert werden.

### Vorgehensweise

1. Wählen Sie in der Seitenleiste **Dokumentannotation** > **Regeln** aus.
1. Lokalisieren Sie in der Ansicht 'Klasse' die Klasse `WörterverzMonate`, die Sie zuvor definiert haben, und klicken Sie neben dieser Klasse auf **Annotationen in Dokumenten suchen**.

    Die Seite 'Annotationen suchen' wird angezeigt. Auf dieser Seite werden alle Dokumente angezeigt, die Textverweise auf Monate enthalten.

1. Klicken Sie auf das Dokument `Technology - computerworld.com`, um das vollständige Dokument anzuzeigen. Beachten Sie, dass der Text `February` hervorgehoben ist, d. h. er wurde als Erwähnung der Klasse `WörterverzMonate` annotiert.

## Lerneinheit 6: Regulären Ausdruck definieren
{: #wks_tutless_rule6}

In dieser Lerneinheit erfahren Sie, wie ein regulärer Ausdruck definiert wird.

### Informationen zu diesem Vorgang

Sie definieren einen regulären Ausdruck, der Zeichenfolgemuster für Jahre (z. B. *2009*) findet.

Weitere Informationen zum Definieren regulärer Ausdrücke finden Sie unter [Regel definieren](/docs/services/watson-knowledge-studio/rule-annotator-define-rule.html).

### Vorgehensweise

1. Klicken Sie auf der Seite **Regeln** auf das Symbol **Klasse hinzufügen** (![_](images/wks_tut_dict_add.jpg)) neben **Klasse** in der rechten Seitenleiste.
1. Geben Sie `RegAusdruckJahr` als Namen für die Klasse ein und klicken Sie anschließend auf **Hinzufügen**.
1. Klicken Sie in der Seitenleiste auf **RegEx** und klicken Sie anschließend auf das Symbol **Regulären Ausdruck erstellen** neben **Reguläre Ausdrücke**.
1. Klicken Sie auf die Schaltfläche **Eintrag hinzufügen**.
1. Geben Sie den folgenden Ausdruck in das Feld **Regulärer Ausdruck** ein:

    ```
    (?:(?:19|20)[0-9]{2})
    ```
    {: screen}

    > **Hinweis:** Dieser reguläre Ausdruck findet Jahre zwischen 1900 und 2099.

1. Geben Sie für **Minimum für Worttokens** den Wert `1` und für **Maximum für Worttokens** den Wert `1` an.
1. Klicken Sie auf **Hinzufügen**, um den Eintrag mit dem regulären Ausdruck zu speichern.
1. Geben Sie `MeinAusdruckJahre` als Namen für den regulären Ausdruck an und wählen Sie anschließend im Menü **Klasse** die Klasse *RegAusdruckJahr* aus, die Sie zuvor definiert haben.
1. Klicken Sie auf **Speichern**.

    Nachdem Sie den regulären Ausdruck gespeichert haben, wird er automatisch auf die Beispieldokumente angewendet. Alle Textzeichenfolgen, die dem Muster entsprechen, das Sie im regulären Ausdruck definiert haben, werden als Erwähnungen der Klasse **RegAusdruckJahr** annotiert.

1. Um zu prüfen, ob der von Ihnen definierte Ausdruck die Zeitangaben korrekt erfasst, können Sie nach Erwähnungen suchen. Klicken Sie auf das Symbol **Annotationen in Dokumenten suchen** neben der Klasse **RegAusdruckJahr** in der Seitenleiste 'Klasse'.

    ![Zeigt, wie ein Benutzer auf das Lupensymbol neben der Klasse 'RegAusdruckJahr' in der Seitenleiste 'Klasse' auf der Seite 'Regel' klickt.](images/rule-regex-add5.jpg)

    Die Seite 'Annotationen suchen' wird angezeigt. Vorkommen der Erwähnungen von Jahresangaben in den Beispieldokumenten sind hervorgehoben.

    ![Zeigt die hervorgehobenen Jahreszahlen in Auszügen aus 8 Beispieldokumenten.](images/rule-regex-add6.jpg)

## Lerneinheit 7: Regel definieren
{: #unique_1166829415}

In dieser Lerneinheit erfahren Sie, wie eine Regel definiert wird.

### Informationen zu diesem Vorgang

Sie haben bereits einer wörterverzeichnisbasierte Klasse zum Annotieren der Erwähnungen von Monatsnamen erstellt. Außerdem haben Sie einen regulären Ausdruck definiert, um Zahlenwerte zu finden, die Jahreszahlen darstellen. Nun definieren Sie eine Regel, um eine Zeichenfolge mit Monat, Zahl, Komma und Jahr zu erfassen. Sie definieren eine Regel für Datumsausdrücke wie *September 21, 2016*.

Weitere Informationen zum Definieren von Regeln finden Sie unter [Regel definieren](/docs/services/watson-knowledge-studio/rule-annotator-define-rule.html).

### Vorgehensweise

1. Wählen Sie in der Seitenleiste **Dokumentannotation** > **Regeln** aus und öffnen Sie das Dokument `Technology - computerworld.com`.
1. Wählen Sie im Dokument den Text *February 3, 2009* aus. Stellen Sie sicher, dass auch das Komma ausgewählt ist.

    ![Zeigt den Text 'February 3, 2009' an, der im Dokument ausgewählt ist.](images/rule-add1.jpg)

1. Klicken Sie auf das Symbol **Regel hinzufügen**.

    Im Regeleditor wird eine Darstellung des von Ihnen angegebenen Regelmusters angezeigt.

    Der Text *February 3, 2009* ist sichtbar. Eine graue Verbindungslinie zwischen den Zellen zeigt an, welche Zellen momentan Teil des Musters sind.
    - Die Klasse *WörterverzMonate* ist Teil des Regelmusters (anstelle des Texts *February*). Diese Auswahl sollte bevorzugt verwendet werden, da das Modell jeden Monat, der mit der Klasse *WörterverzMonate* annotiert ist, als erstes Token im Datumsmuster finden soll und nicht nur den Text *February*.
    - Am Ende der Regel ist das Jahr *2009* bereits als eine Erwähnung der Klasse *RegAusdruckJahr* annotiert. Die Klasse *RegAusdruckJahr* ist Teil des Regelmusters (anstelle der Zahl 2009). Diese Auswahl sollte ebenfalls bevorzugt werden, da das Modell jede Jahreszahl, die mit der Klasse *RegAusdruckJahr* annotiert ist, als letztes Token im Datumsmuster finden soll, und nicht nur die Zahl *2009*.

    Die Zahl 3 und das darauf folgende Komma (,) werden als zweites und drittes Token im Muster angezeigt. Bei Verwendung des momentan definierten Musters findet das Modell nur Vorkommen von Datumsangaben, in denen der dritte Tag eines Monats angegeben ist. Das Modell soll jedoch Datumsangaben finden, die jeden beliebigen Tag des Monats enthalten.Im nächsten Schritt werden daher die Token-Einstellungen für den Tag geändert.

1. Klicken Sie über der Zelle für den Tag (`3`) auf das Symbol **Text**, um die Featureeinstellungen für das Token zu öffnen.

    ![Zeigt, wie ein Benutzer auf das Symbol für Textfeatureeinstellungen klickt.](images/rule-add4.jpg)

    Momentan ist die Regel so eingerichtet, dass der Text exakt mit der Zahl `3` übereinstimmen muss. Stattdessen soll jedoch eine beliebige Zahl als Übereinstimmung gefunden werden.

1. Ändern Sie die Featureeinstellung, indem Sie **Zeichentyp : Numerisch** auswählen und anschließend **Text : 3** abwählen.

    ![Zeigt, wie der Benutzer auf die Option 'Zeichentyp : Numerisch' als Featureeinstellung für das Token '3' klickt.](images/rule-add5.jpg)

    Sie haben die Definition für die Zelle mit der Zahl `3` geändert.

    ![Zeigt, dass über der Zelle für das Token '3' jetzt ein Symbol 'Aa' zu sehen ist. Dies bedeutet, dass jeder numerische Werte als Übereinstimmung für das Token in dem Muster gefunden werden kann.](images/rule-add6.jpg)

    Das Symbol **Aa** gibt an, dass anstelle der Zahl 3 jede beliebige Nummer vorkommen kann.

1. Lassen Sie die Einstellungen für das Komma-Token unverändert.

    Das dritte Token im Muster soll ein Komma sein, daher ist die aktuelle Featureeinstellung **text : ,** korrekt. Neben der Featureeinstellung verfügt jedes Token über eine Wiederholungseinstellung. Die Wiederholungseinstellung gibt an, wie oft das Token im Text wiederholt werden darf, damit eine Übereinstimmung mit dem Muster erkannt wird. Die aktuelle Wiederholungseinstellung **Erforderlich (genau 1)** ist ebenfalls korrekt.

    ![Zeigt die Wiederholungseinstellung für das Komma-Token mit dem Wert 'genau 1'. ](images/rule-add7.jpg)

1. Ordnen Sie eine Klasse zu, die das Muster `WörterverzMonate + numerisches Token + Komma + RegAusdruckJahr` repräsentiert.

    Beachten Sie die vier leeren Zellen für die vier Token, die Sie im Dokument ausgewählt haben. Wenn Sie alle Zellen auswählen möchten, wählen Sie die erste Zelle aus, drücken und halten Sie die Umschalttaste und klicken Sie nacheinander auf alle weiteren Zellen. Geben Sie `RegelDatum` als Namen für die Klasse ein und klicken Sie anschließend auf den Namen, damit die neue Klasse erstellt wird.

    ![Zeigt, dass alle vier Zellen in der oberen Zeile ausgewählt sind und der Bereich als Klasse 'RegelDatum' definiert wird.](images/rule-add8.jpg)

    Sie haben das Muster für die Regel erfolgreich definiert.

1. Geben Sie in das Feld **Regelname** die Zeichenfolge `MeineDatumsRegel` ein und klicken Sie auf **Speichern**.

    Nach dem Speichern wird die Regel automatisch auf die Beispieldokumente angewendet. Wenn das Dokument `Technology - computerworld.com` im Regeleditor noch geöffnet ist, können Sie erkennen, dass der Text `February 3, 2009` im Dokument jetzt als Erwähnung der Klasse 'RegelDatum' annotiert ist.

    ![Zeigt einen Textabschnitt im Dokument 'Technology - computerworld.com', in dem nur der Text 'February 3, 2009' als Erwähnung der Klasse 'RegelDatum' annotiert ist.](images/rule-add10.jpg)

    Sie können alle Vorkommen von Erwähnungen der Klasse 'RegelDatum' in den Beispieldokumenten suchen, indem Sie auf das Symbol **Annotation in Dokumenten suchen** (![ein Lupensymbol, das einen Suchvorgang darstellt](images/filter_gray.png)) neben der Klasse `RegelDatum` in der Anzeige 'Klasse' klicken. Es hat sich in der Praxis bewährt, zu überprüfen, ob alle Datumsangaben korrekt erfasst werden, um sicherzustellen, dass das Muster korrekt definiert wurde.

    ![Zeigt die Seite 'Annotationen finden' mit zwei Dokumenten, die Datumsangaben enthalten, die mit dem soeben definierten Regelmuster übereinstimmen.](images/rule-add11.jpg)

## Lerneinheit 8: Ein regelbasiertes Modell erstellen
{: #wks_tutless_rule8}

In dieser Lerneinheit erfahren Sie, wie ein regelbasiertes Modell erstellt wird.

### Informationen zu diesem Vorgang

Weitere Informationen zum Erstellen eines regelbasierten Modells finden Sie unter [Regelbasiertes Modell erstellen](/docs/services/watson-knowledge-studio/rule-annotator-model-create.html).

### Vorgehensweise

1. Wählen Sie in der Seitenleiste **Modellverwaltung** > **Versionen** aus und klicken Sie auf die Registerkarte **Typzuordnung für regelbasiertes Modell**.

1. Ordnen Sie die von Ihnen definierte Klasse `RegelDatum` der Entität `DATUM` aus dem Typsystem zu.

    1. Lokalisieren Sie die Entität **DATUM** und klicken Sie auf **Bearbeiten**.

        ![Zeigt, wie der Benutzer auf die Option 'Bearbeiten' für den Entitätstyp DATUM in der Registerkarte für Klassenzuordnung auf der Seite 'Annotatorkomponente' klickt.](images/rule-anno2.jpg)

    1. Wählen Sie in der Dropdown-Liste die Klasse `RegelDatum` aus und klicken Sie auf **Speichern**.

        ![Zeigt, wie der Benutzer die Klasse 'RegelDatum' in der Dropdown-Liste auswählt.](images/rule-anno3.jpg)

1. Um das regelbasierte Modell auszuführen, wählen Sie die Registerkarte **Regelbasiert** aus und klicken Sie auf **Dieses Modell ausführen**.

## Zusammenfassung des Lernprogramms
{: #wks_tutrule_sum}

Beim Kennenlernen von {{site.data.keyword.knowledgestudioshort}} haben Sie ein regelbasiertes Modell erstellt.

### Eingeübte Lerninhalte

Beim Durcharbeiten dieses Lernprogramms haben Sie die folgenden Konzepte kennengelernt:

- Klassen
- Reguläre Ausdrücke
- Regeln
