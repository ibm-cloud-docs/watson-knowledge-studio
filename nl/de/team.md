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

Diese Dokumentation bezieht sich auf {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Die Dokumentation für die Vorgängerversion {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace kann über [diesen Link ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/docs/services/knowledge-studio/team.html){: new_window} aufgerufen werden.
{: tip}

# Team zusammenstellen
{: #team}

Für die Erstellung eines Modells sind Eingaben von Fachleuten des jeweiligen Fachgebiets, von Projektleitern und von Benutzern erforderlich, die statistische Modelle verstehen und interpretieren können. Sie müssen in {{site.data.keyword.knowledgestudioshort}} einen Benutzer für jede Person hinzufügen, die sich anmelden soll.
{: shortdesc}

**Hinweise**: Nur unter Standardplänen und Premium-Plänen können Benutzer hinzugefügt werden. Kostenlose Pläne sind auf einen einzigen Benutzer begrenzt. Diesem einen Benutzer wird die Rolle mit der höchsten Berechtigung (Administratorrolle) zugeordnet.

## Vorbereitungen

- Stellen Sie sicher, dass Sie einen unterstützten Browser verwenden. Weitere Informationen finden Sie unter [Browseranforderungen](/docs/services/watson-knowledge-studio/system-requirements.html).
- [Erstellen Sie eine Instanz von {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/tutorials-create-project.html#instance).
- Wenn Sie sich für einen Standardplan oder Premium-Plan angemeldet haben, können Sie über die Registerkarte {{site.data.keyword.cloud_notm}} **Verwalten** andere Benutzer in Ihre Organisation einladen, die Sie als Benutzer in {{site.data.keyword.knowledgestudioshort}} hinzufügen möchten. Weitere Informationen zum Einladen von Benutzern finden Sie unter [Benutzer einladen und Benutzern Zugriff zuweisen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/docs/iam/iamuserinv.html){: new_window}.

  **Wichtig**:

  - Stellen Sie sicher, dass eingeladene Benutzer über die Cloud Foundry-Rolle **Entwickler** verfügen. Weitere Informationen finden Sie unter [Cloud Foundry-Zugriff ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/docs/iam/cfaccess.html){: new_window}.
  - Dem ersten Benutzer, der {{site.data.keyword.knowledgestudioshort}} startet, wird die Administratorrolle für die {{site.data.keyword.knowledgestudioshort}}-Instanz erteilt. Bei dieser Task wird davon ausgegangen, dass Sie als erste Person {{site.data.keyword.knowledgestudioshort}} starten, nachdem Sie sich für einen Plan angemeldet haben, d. h. Sie verfügen über die Administratorrolle.

## Informationen zu diesem Vorgang

Normalerweise fügen Sie Benutzer für die folgenden Rollen hinzu.

**Hinweis:** Wenn Sie für einen kostenlosen Plan angemeldet sind, können Sie keine weiteren Benutzer in Ihrer {{site.data.keyword.knowledgestudioshort}}-Instanz hinzufügen. Vielmehr werden Sie beim Starten von {{site.data.keyword.knowledgestudioshort}} als Benutzer mit Administratorrolle zu der Instanz hinzugefügt. Als Benutzer mit Administratorrolle können Sie viele Funktionen ausführen, die in der Regel von unterschiedlichen Personen ausgeführt werden, denen verschiedene Rollen zugeordnet sind. Sie können testen, wie Fachleute aus verschiedenen Bereichen eines Fachgebiets zusammenarbeiten können, um ein Modell für maschinelles Lernen oder ein regelbasiertes Modell zu erstellen.

- **HumanAnnotator** (Annotatorbenutzer)

    Annotatorbenutzer sind in der Regel Fachleute, die Dokumente aus einem bestimmten Fachgebiets prüfen, um Entitäten und Beziehungen zu identifizieren, die für das Fachgebiet von Interesse sind. Diese Benutzer können in begrenztem Umfang mit der Anwendung interagieren. Sie arbeiten mit dem Ground Truth-Editor und annotieren eine Dokumentgruppe, die ihnen zugeordnet wurde.

- **ProjectManager** (Projektleiter)

    Projektleiter unterstützen die Erstellung von Modellen, indem Sie Tasks wie das Erstellen von Arbeitsbereichsartefakten sowie das Trainieren, Erstellen und Bereitstellen von Modellen ausführen. In Arbeitsbereichen, die zum Erstellen von Annotatoren für maschinelles Lernen verwendet werden, verwalten Projektleiter außerdem den Prozess zum Annotieren von Dokumenten, indem Sie Dokumentüberprüfungstasks bestimmten Annotatorbenutzern zuweisen, Annotationskonflikte beurteilen und genehmigen, welche Dokumente zur Ground Truth hinzugefügt werden dürfen.

## Benutzer in {{site.data.keyword.knowledgestudioshort}} hinzufügen

Fügen Sie Benutzer aus Ihrer {{site.data.keyword.cloud_notm}}-Organisation in {{site.data.keyword.knowledgestudioshort}} hinzu.

**Hinweise**: Nur unter Standardplänen und Premium-Plänen können Benutzer hinzugefügt werden. Kostenlose Pläne sind auf einen einzigen Benutzer begrenzt. 

So fügen Sie Benutzer zu einer {{site.data.keyword.knowledgestudioshort}}-Instanz hinzu:

1. Melden Sie sich beim [{{site.data.keyword.cloud_notm}}-Dashboard ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/dashboard/apps/){: new_window} mit Ihrer {{site.data.keyword.ibmid}} an und starten Sie {{site.data.keyword.knowledgestudioshort}}.
1. Klicken Sie auf das Symbol **Einstellungen** und anschließend auf **Servicedetails anzeigen/ändern**.
1. Geben Sie im Abschnitt **Managerbenutzer** die {{site.data.keyword.ibmid}} des Benutzers ein, den Sie hinzufügen möchten.
1. Wählen Sie die Rolle aus, die Sie dem Benutzer zuweisen möchten.

   Hinweis: Zugewiesene Benutzerrollen können später nicht mehr herabgestuft werden. Daher sollten Sie sich bereits vor dem Zuweisen der Rollen 'Admin' (Administrator) und 'ProjectManager' (Projektleiter) darüber im Klaren sein, welche Tasks diese Rollen ausführen können.

1. Klicken Sie auf **Hinzufügen**.

## Benutzerrollen hochstufen

Nach dem Hinzufügen von Benutzern in {{site.data.keyword.knowledgestudioshort}} können Sie Rollen mit geringen Berechtigungen zu Rollen mit höheren Berechtigungen hochstufen. Benutzer müssen über die unten angegebenen Rollen verfügen, damit sie die entsprechenden Tasks ausführen können.

**Hinweis**: Nur unter Standardplänen und Premium-Plänen können Benutzerrollen hochgestuft werden. Kostenlose Pläne sind auf einen einzigen Benutzer begrenzt, der die höchste Rolle 'Admin' (Administrator) hat.

> **Achtung: Das Herabstufen von einer Rolle mit höherer Berechtigung auf eine Rolle mit geringerer Berechtigung ist nicht zulässig.**

So stufen Sie Rollen für {{site.data.keyword.knowledgestudioshort}}-Benutzer hoch:

1. Melden Sie sich beim [{{site.data.keyword.cloud_notm}}-Dashboard ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/dashboard/apps/){: new_window} mit Ihrer {{site.data.keyword.ibmid}} an und starten Sie {{site.data.keyword.knowledgestudioshort}}.
1. Klicken Sie im Navigationsmenü in der rechten oberen Ecke auf das Symbol **Einstellungen** ![Symbol 'Einstellungen'](images/settings.png) und anschließend auf **Servicedetails anzeigen/ändern**. Im Abschnitt **Benutzer verwalten** auf der Seite 'Servicedetails' werden alle Benutzer-IDs aufgelistet, die Benutzer dieser {{site.data.keyword.knowledgestudioshort}}-Instanz sind.
1. Suchen Sie den Namen des Benutzers, der geändert werden soll, und klicken Sie auf den Link **Bearbeiten**.

    In {{site.data.keyword.knowledgestudioshort}} sind die folgenden Rollen definiert (aufgelistet von der höchsten bis zur niedrigsten Berechtigungsstufe):
    - **Admin** (Administrator)

      Benutzer mit dieser Rolle können die folgenden Tasks ausführen:

        - Ein Abonnement verwalten (z. B. Feature, Speicher und weitere Benutzer hinzufügen)
        - Benutzern über die Seite 'Servicedetails' Zugriff auf ein Abonnement erteilen
        - Alle Arbeitsbereiche in ihrem Abonnement verwalten
        - Benutzern die Rollen von Projektleitern und Annotatorbenutzern für alle Arbeitsbereiche zuweisen

    - **ProjectManager** (Projektleiter)

      Benutzer mit dieser Rolle können die folgenden Tasks ausführen:

      - Arbeitsbereiche verwalten, in denen sie hinzugefügt wurden
      - Annotatorbenutzer für einen Arbeitsbereich zuordnen

      Benutzer mit dieser Rolle können die folgenden Tasks nicht ausführen:

      - Arbeitsbereiche erstellen
      - Benutzerzugriff und Rollen über die Seite 'Servicedetails' verwalten

    - **HumanAnnotator** (Annotatorbenutzer)

      Benutzer mit dieser Rolle können Dokumente annotieren, die sich in Arbeitsbereichen befinden, für die ihnen die Rolle des Annotatorbenutzers zugewiesen wurde, sowie in einer Dokumentgruppe mit Annotationstasks, die ihnen zugeordnet sind.

      **Wichtig:** Sie müssen einen Arbeitsbereich erstellen, einem Benutzer eine Dokumentgruppe zuordnen und einem Benutzer eine Annotationstask zuweisen, damit einem Benutzer mit der Rolle **HumanAnnotator** Arbeitsbereiche in der {{site.data.keyword.knowledgestudioshort}}-Anwendung angezeigt werden. Richten Sie den Arbeitsbereich so bald wie möglich ein, nachdem sich Benutzer registriert haben, damit die Benutzer Ihren Arbeitsbereich schon beim ersten Starten der Anwendung sehen können. Es empfiehlt sich, die Benutzer zu benachrichtigen, wenn Sie den Arbeitsbereich eingerichtet haben, damit die Benutzer wissen, dass sie mit dem Annotieren von Dokumenten beginnen können.

1. Klicken Sie auf die Rolle des Benutzers und wählen Sie die Rolle mit höheren Berechtigungen aus, auf die Sie den Benutzer hochstufen möchten.
1. Optional: Nachdem Sie das Verwalten von Benutzern in {{site.data.keyword.knowledgestudioshort}} abgeschlossen haben, beenden Sie die Sitzung und schließen Sie den Web-Browser. Die Benutzerschnittstelle von {{site.data.keyword.knowledgestudioshort}} enthält keine eigenständige Aktion zum Abmelden.

## Benutzerkonten inaktivieren

Wenn Sie später Benutzer entfernen möchten, wiederholen Sie die vorherigen Schritte zum Öffnen der Seite 'Servicedetails'. Suchen Sie in der Liste der Benutzer-IDs den Benutzer, den Sie entfernen möchten, und klicken Sie auf **Inaktivieren**.

> **Achtung**: Wenn den betreffenden Benutzern Dokumente zum Annotieren zugewiesen sind, hat das Entfernen der Benutzerkonten Auswirkungen auf die von ihnen erstellten Annotationen. Alle Annotation der inaktivierten Benutzer, die nicht in die Ground Truth hochgestuft wurden, werden gelöscht.

### Zugehörige Tasks

[Annotationsgruppen erstellen und zuordnen](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projdocsets)
