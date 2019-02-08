---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-16"

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

Diese Dokumentation bezieht sich auf {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Die Dokumentation für die Vorgängerversion {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace kann über [diesen Link ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/docs/services/knowledge-studio/tutorials-create-project.html){: new_window} aufgerufen werden.
{: tip}

# Einführung in {{site.data.keyword.knowledgestudioshort}}
{: #wks_tutintro}

In diesem Lernprogramm für {{site.data.keyword.knowledgestudiofull}} erfahren Sie, wie vorausgesetzte Tasks ausgeführt werden, die abgeschlossen sein müssen, bevor Sie die weiteren Lernprogramme durcharbeiten können.
{: shortdesc}

## Vorbereitungen
{: #prereq}

- Stellen Sie sicher, dass ein unterstützter Browser verwendet wird. Siehe [Browseranforderungen](/docs/services/watson-knowledge-studio/system-requirements.html).
-  Zum Durcharbeiten dieses Lernprogramms benötigen Sie mindestens eine Benutzer-ID, die Sie in {{site.data.keyword.knowledgestudioshort}} verwenden können. Die Benutzer-ID muss über die Administratorrolle verfügen. Wenn Sie sich als einziger Benutzer für einen Lite-Plan registrieren, haben Sie die Rolle 'Admin'. Informationen zu Benutzerrollen finden Sie unter [Team zusammenstellen](/docs/services/watson-knowledge-studio/team.html).

## Serviceinstanz erstellen
{: #instance}

1. Falls noch nicht geschehen, [registrieren Sie sich für eine {{site.data.keyword.ibmid}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}){: new_window} und melden Sie sich bei {{site.data.keyword.cloud_notm}} an.
1. Klicken Sie auf der {{site.data.keyword.cloud_notm}} {{site.data.keyword.watson}} [-Serviceseite ![External link icon](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/developer/watson/services){: new_window} auf die {{site.data.keyword.knowledgestudioshort}}-Kachel und melden Sie sich für einen Plan an.
1. Nachdem Sie sich für einen Plan angemeldet haben, starten Sie von der Liste der Services {{site.data.keyword.knowledgestudioshort}}.

## Lerneinheit 1: Benutzerrollen zuordnen
{: #wks_tutless1}

In dieser Lerneinheit erfahren Sie mehr über die verschiedenen Rollen, die Sie Benutzern in {{site.data.keyword.knowledgestudioshort}} zuordnen können.

### Informationen zu diesem Vorgang
{: #wks_tutless1_about}

Für die Erstellung eines Modells für maschinelles Lernen sind Eingaben von Fachleuten des jeweiligen Fachgebiets, von Projektleitern und von Benutzern erforderlich, die statistische Modelle verstehen und interpretieren können. Administratoren ordnen den Benutzern die entsprechenden Rollen zu, damit sie die erforderlichen Berechtigungen für ihre Tasks besitzen. Weitere Informationen zu Benutzerrollen finden Sie unter [Team zusammenstellen](/docs/services/watson-knowledge-studio/team.html).

### Vorgehensweise
{: #wks_tutless1_procedure}

1. Melden Sie sich bei {{site.data.keyword.knowledgestudioshort}} mit Ihrer Administrator-ID an. Wenn Sie über eine vorhandene {{site.data.keyword.knowledgestudioshort}}-Instanz verfügen, finden Sie sie auf der {{site.data.keyword.cloud_notm}}{{site.data.keyword.watson}}[-Serviceseite ![External link icon](../../icons/launch-glyph.svg "Symbol für externen Link") ](https://{DomainName}/developer/watson/services){: new_window}.
1. Klicken Sie auf das Symbol 'Einstellungen', um die Seite 'Servicedetails' zu öffnen. Auf dieser Seite werden alle Benutzer-IDs aufgelistet, die als {{site.data.keyword.knowledgestudioshort}}-Benutzer registriert sind. Jede Benutzer-ID verfügt über eine der folgenden Rollen (mit abnehmendem Umfang der Berechtigungen aufgelistet):

    - Admin (Administrator)
    - Projektleiter
    - Annotatorbenutzer

    Informationen zu Benutzerrollen finden Sie in [Benutzerrollen in {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/roles.html).

1. Stellen Sie sicher, dass mindestens ein Benutzer über die Administratorrolle verfügt. Eine Benutzer-ID mit dieser Rolle kann Arbeitsbereiche erstellen und als Projektleiter oder Annotatorbenutzer agieren.
1. Wenn Sie Zugriff auf zusätzliche Benutzer-IDs haben, stellen Sie sicher, dass mindestens zwei Benutzer mit der Rolle 'Annotatorbenutzer' vorhanden sind.

    > **Hinweise:** An der Erstellung eines Modells wirken in der Praxis normalerweise mehrere Annotatorbenutzer sowie ein Administrator oder Projektleiter mit. Für die Zwecke dieses Lernprogramms genügt jedoch eine einzige Benutzer-ID.

1. Optional: Ändern Sie die Rolle, die einer Benutzer-ID zugeordnet ist. Klicken Sie in der Spalte **Aktion** der Tabelle auf den Link **Bearbeiten** und ändern Sie anschließend die zugeordnete Benutzerrolle.

    > **Hinweis:** Sie können für eine Benutzer-ID eine Rolle mit umfangreicheren Berechtigungen festlegen, aber Sie können einen Benutzer mit der Administrator- oder Projektleiterrolle nicht auf die Rolle 'Annotatorbenutzer' herabstufen.

## Lerneinheit 2: Arbeitsbereich erstellen
{: #wks_tutless2}

In dieser Lerneinheit erfahren Sie, wie ein Arbeitsbereich in {{site.data.keyword.knowledgestudioshort}} erstellt wird.

### Informationen zu diesem Vorgang
{: #wks_tutless2_about}

In einem Arbeitsbereich werden alle Ressourcen definiert, die zum Erstellen eines Modells für maschinelles Lernen erforderlich sind. Dazu gehören Trainingsdokumente, das Typsystem, Wörterverzeichnisse und Annotationen, die von Annotatorbenutzern hinzugefügt werden. Weitere Informationen zur Erstellung von Arbeitsbereichen finden Sie unter [Arbeitsbereich erstellen](/docs/services/watson-knowledge-studio/create-project.html).

### Vorgehensweise
{: #wks_tutless2_procedure}

1. Starten Sie als {{site.data.keyword.knowledgestudioshort}}-Administrator über Ihr {{site.data.keyword.cloud_notm}}-[Dashboard ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}){:new_window} den {{site.data.keyword.knowledgestudioshort}}-Service.
1. Klicken Sie auf **Arbeitsbereich erstellen**.
1. Geben Sie die Details für den neuen Arbeitsbereich an:

    - Geben Sie in das Feld **Name des Arbeitsbereichs** den Namen `Mein Arbeitsbereich` ein.
    - Geben Sie in das Feld **Beschreibung des Arbeitsbereichs** die Beschreibung `Arbeitsbereich für Watson Knowledge Studio-Lernprogramm` ein.
    - Behalten Sie im Feld **Sprache der Dokumente** den Standardwert **English** bei. Für dieses Lernprogramm werden Beispieldateien in englischer Sprache verwendet.

1. Klicken Sie auf **Erstellen**.

### Ergebnisse
{: #wks_tutless2_results}

Der Arbeitsbereich wird erstellt und automatisch geöffnet.

### Nächste Schritte
{: #wks_tutless2_next}

Sie können jetzt mit dem Konfigurieren der Arbeitsbereichsressourcen (z. B. Typsystem) beginnen.

## Lerneinheit 3: Typsystem erstellen
{: #wks_tutless3}

In dieser Lerneinheit erfahren Sie, wie ein Typsystem in {{site.data.keyword.knowledgestudioshort}} hochgeladen und geändert wird. Vor dem Ausführen von Annotationstasks müssen Sie ein Typsystem erstellen oder hochladen.

### Informationen zu diesem Vorgang
{: #wks_tutless3_about}

Weitere Informationen zu Typsystemen finden Sie unter [Typsysteme](/docs/services/watson-knowledge-studio/typesystem.html#wks_typesystem).

### Vorgehensweise
{: #wks_tutless3_procedure}

1. Laden Sie die Datei <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/en-klue2-types.json" download>en-klue2-types.json <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link" class="style-scope doc-content"></a> in Ihren Computer herunter. Diese Datei enthält ein Beispiel für ein KLUE-Typsystem.
1. Klicken Sie auf **Assets** > **Entitätstypen**.
1. Klicken Sie auf der Seite 'Entitätstypen' auf **Hochladen**.
1. Laden Sie die Datei `en-klue2-types.json` auf Ihren Computer herunter. Das hochgeladene Typsystem wird in der Tabelle angezeigt.
1. Durchsuchen Sie das Typsystem, um zu sehen, welche Daten hochgeladen wurden.
1. Bearbeiten Sie einen Entitätstyp:

    1. Lokalisieren Sie den Entitätstyp MONEY.
    1. Doppelklicken Sie auf eine beliebige Tabellenzeile, um den Entitätstyp zu bearbeiten.
    1. Klicken Sie in der Spalte **Rollen** auf das Symbol **Rolle löschen** ![Die "Rolle löschen".](images/wks_delete.jpg "Symbol ") neben der Rolle AWARD.

        ![Dieser Screenshot zeigt das Löschen einer Rolle für einen Entitätstyp.](images/wks_tut_delete_role.jpg "Der Screenshot zeigt, wie sich der Mauszeiger über bewegt: ")

    1. Klicken Sie auf **Speichern**.

### Nächste Schritte
{: #wks_tutless3_next}

Nachdem Sie die Änderungen im Typsystem abgeschlossen haben, können Sie mit dem Hinzufügen von Dokumenten in Ihrem Arbeitsbereich beginnen.

## Lektion 4: Wörterverzeichnis hinzufügen
{: #wks_tutless4}

In dieser Lerneinheit erfahren Sie, wie Sie ein Wörterverzeichnis zu einem Arbeitsbereich in {{site.data.keyword.knowledgestudioshort}} hinzufügen. Wörterverzeichnisse werden beim Erstellen eines Modells für maschinelles Lernen zum Vorannotieren von Text verwendet.

### Informationen zu diesem Vorgang
{: #wks_tutless4_about}

Weitere Informationen zu Wörterverzeichnissen finden Sie unter [Wörterverzeichnisse zu einem Arbeitsbereich hinzufügen](/docs/services/watson-knowledge-studio/dictionaries.html#wks_projdictionaries).

### Vorgehensweise
{: #wks_tutless4_procedure}

1. Laden Sie die Datei <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/dictionary-items-organization.csv" download>`dictionary-items-organization.csv` <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link" class="style-scope doc-content"></a> auf Ihren Computer herunter. Diese Datei enthält Wörterverzeichnisbegriffe im CSV-Format, die in ein {{site.data.keyword.knowledgestudioshort}}-Wörterverzeichnis hochgeladen werden können.
1. Klicken Sie auf **Assets** > **Wörterverzeichnisse**.
1. Klicken Sie auf **Wörterverzeichnis erstellen**, um ein Wörterverzeichnis hinzuzufügen.

    > **Hinweis:** Klicken Sie nicht auf **Wörterverzeichnis hochladen**. Diese Funktion dient zum Hochladen eines Wörterverzeichnisses, das unverändert verwendet werden soll. Für die Zwecke dieses Lernprogramms erstellen Sie ein neues bearbeitbares Wörterverzeichnis und laden anschließend Begriffe in das neue Wörterverzeichnis hoch.

1. Geben Sie in das Feld **Name** den Namen `Testwörterverzeichnis` ein und klicken Sie auf **Speichern**, um das leere Wörterverzeichnis zu erstellen.

    Das neue Wörterverzeichnis wird erstellt und automatisch zum Bearbeiten geöffnet.

1. Klicken Sie im Wörterverzeichnisfenster auf **Hochladen**.
1. Laden Sie die Datei `dictionary-items-organization.csv` auf Ihren Computer herunter. Die Begriffe aus der Datei werden in das Wörterverzeichnis hochgeladen.
1. Klicken Sie auf **Eintrag hinzufügen**, um einen neuen Begriff zu erstellen. Am Anfang der Tabelle wird eine bearbeitbare Zeile hinzugefügt.
1. Geben Sie in der Spalte **Oberflächenformen** die Zeichenfolgen `IBM` und `International Business Machines Corporation` in separaten Zeilen ein. (Wenn Sie mit der Eingabe einer neuen Oberflächenform beginnen, wird darunter Leerraum für eine weitere Oberflächenform eingefügt.) Lassen Sie das Optionsfeld `IBM` ausgewählt. Dadurch wird angegeben, dass `IBM` das Lemma ist.
1. Wählen Sie in der Spalte **Wortart** die Option **Nomen** aus.
1. Klicken Sie auf **Speichern**.

    ![Screenshot der Seite 'Wörterverzeichnisse'. Der Wörterverzeichniseintrag "IBM" ist ausgewählt und die zugehörigen Oberflächenformen und die Wortart sind hervorgehoben.](images/wks_tutdict4.jpg "Screenshot der Seite 'Wörterverzeichnisse'. Der ")

### Nächste Schritte
{: #wks_tutless4_next}

Nachdem Sie ein Wörterverzeichnis erstellt haben, können Sie es verwenden, um durch Vorannotieren der Dokumente die Annotatorbenutzertasks zu beschleunigen.

## Zusammenfassung des Lernprogramms
{: #wks_tutsum}

Beim Kennenlernen von {{site.data.keyword.knowledgestudioshort}} haben Sie einen Arbeitsbereich erstellt und Artefakte zu dem Arbeitsbereich hinzugefügt.

### Eingeübte Lerninhalte
{: #lessons_learned}

Beim Durcharbeiten dieses Lernprogramms haben Sie die folgenden Konzepte kennengelernt:

- Arbeitsbereiche
- Typsysteme
- Wörterverzeichnisse
