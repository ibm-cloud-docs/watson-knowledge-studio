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

Diese Dokumentation bezieht sich auf {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Die Dokumentation für die Vorgängerversion {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace kann über [diesen Link ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/docs/services/knowledge-studio/team.html){: new_window} aufgerufen werden.
{: tip}

# Team zusammenstellen
{: #team}

Für die Erstellung eines Modells sind Eingaben von Fachleuten des jeweiligen Fachgebiets, von Projektleitern und von Benutzern erforderlich, die statistische Modelle verstehen und interpretieren können. Sie müssen in {{site.data.keyword.knowledgestudioshort}} einen Benutzer für jede Person hinzufügen, die sich anmelden soll.
{: shortdesc}

**Hinweis**: Nur Standardpläne und Premium-Pläne können mehr als einen Benutzer haben. Lite-Pläne sind auf einen einzigen Benutzer begrenzt. Diesem einen Benutzer wird die Rolle mit der höchsten Berechtigung (Administratorrolle) zugeordnet.

## Vorbereitungen

- Stellen Sie sicher, dass Sie einen unterstützten Browser verwenden. Siehe [Browseranforderungen](/docs/services/watson-knowledge-studio/system-requirements.html).
- [Erstellen Sie eine Instanz von {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/tutorials-create-project.html#instance).
- Wenn Sie sich für einen Standardplan oder Premium-Plan angemeldet haben, können Sie über die Registerkarte {{site.data.keyword.cloud_notm}} **Verwalten** andere Benutzer in Ihre Organisation einladen, die Sie als Benutzer in {{site.data.keyword.knowledgestudioshort}} hinzufügen möchten. Weitere Informationen zum Einladen von Benutzern finden Sie unter [Benutzer einladen und Benutzern Zugriff zuweisen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/docs/iam/iamuserinv.html){: new_window}.

  **Wichtig**: Stellen Sie sicher, dass eingeladene Benutzer über die Cloud Foundry-Entwicklerrolle verfügen. Siehe [Cloud Foundry-Zugriff ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/docs/iam/cfaccess.html){: new_window}.

## Informationen zu diesem Vorgang

In der Regel fügen Sie Benutzer hinzu, um die Rollen von Annotatorbenutzern und Projektleitern zu füllen. Beschreibungen finden Sie unter [Benutzerrollen in {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/roles.html).

**Hinweis:**

- Wenn Sie für einen Lite-Plan angemeldet sind, können Sie keine weiteren Benutzer in Ihrer {{site.data.keyword.knowledgestudioshort}}-Instanz hinzufügen. Vielmehr werden Sie beim Starten von {{site.data.keyword.knowledgestudioshort}} als Benutzer mit Administratorrolle zu der Instanz hinzugefügt. Als Benutzer mit Administratorrolle können Sie viele Funktionen ausführen, die in der Regel von unterschiedlichen Personen ausgeführt werden, denen verschiedene Rollen zugeordnet sind. Sie können testen, wie Fachleute aus verschiedenen Bereichen eines Fachgebiets zusammenarbeiten können, um ein Modell für maschinelles Lernen oder ein regelbasiertes Modell zu erstellen.
- Dem ersten Benutzer, der {{site.data.keyword.knowledgestudioshort}} startet, wird die Administratorrolle für die {{site.data.keyword.knowledgestudioshort}}-Instanz erteilt. Bei dieser Task wird davon ausgegangen, dass Sie als erste Person {{site.data.keyword.knowledgestudioshort}} starten, nachdem Sie sich für einen Plan angemeldet haben, d. h. Sie verfügen über die Administratorrolle.

## Benutzer in {{site.data.keyword.knowledgestudioshort}} hinzufügen

Fügen Sie Benutzer aus Ihrer {{site.data.keyword.cloud_notm}}-Organisation in {{site.data.keyword.knowledgestudioshort}} hinzu.

So fügen Sie Benutzer zu einer {{site.data.keyword.knowledgestudioshort}}-Instanz hinzu:

1. Melden Sie sich beim [{{site.data.keyword.cloud_notm}}-Dashboard ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net){: new_window} mit Ihrer {{site.data.keyword.ibmid}} an und starten Sie {{site.data.keyword.knowledgestudioshort}}.
1. Klicken Sie auf das Symbol **Einstellungen** und anschließend auf **Servicedetails verwalten**.
1. Geben Sie im Abschnitt **Managerbenutzer** die {{site.data.keyword.ibmid}} des Benutzers ein, den Sie hinzufügen möchten.
1. Wählen Sie die Rolle aus, die Sie dem Benutzer zuweisen möchten. Eine Beschreibung der verfügbaren Rollen finden Sie unter [Benutzerrollen in {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/roles.html).

  **Hinweis**: Zugewiesene Benutzerrollen können später nicht mehr herabgestuft werden. Daher sollten Sie sich bereits vor dem Zuweisen der Rollen 'admin' (Administrator) und 'project' (Projektleiter) darüber im Klaren sein, welche Tasks diese Rollen ausführen können.

1. Klicken Sie auf **Hinzufügen**.

## Benutzerrollen hochstufen

Nach dem Hinzufügen von Benutzern in {{site.data.keyword.knowledgestudioshort}} können Sie Rollen mit geringen Berechtigungen zu Rollen mit höheren Berechtigungen hochstufen. Benutzer müssen über die unten angegebenen Rollen verfügen, damit sie die entsprechenden Tasks ausführen können.

**Hinweis**: Nur Standardpläne und Premium-Pläne können mehr als einen Benutzer haben. Lite-Pläne sind auf einen Benutzer begrenzt, der bereits die höchste Rolle 'admin' hat. 

> **Achtung: Das Herabstufen von einer Rolle mit höherer Berechtigung auf eine Rolle mit geringerer Berechtigung ist nicht zulässig.**

So stufen Sie Rollen für {{site.data.keyword.knowledgestudioshort}}-Benutzer hoch:

1. Melden Sie sich beim [{{site.data.keyword.cloud_notm}}-Dashboard ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net){: new_window} mit Ihrer {{site.data.keyword.ibmid}} an und starten Sie {{site.data.keyword.knowledgestudioshort}}.
1. Klicken Sie im Navigationsmenü in der rechten oberen Ecke auf das Symbol **Einstellungen** ![Symbol 'Einstellungen'](images/settings.png) und anschließend auf **Servicedetails verwalten**. Im Abschnitt **Benutzer verwalten** auf der Seite 'Servicedetails' werden alle Benutzer-IDs aufgelistet, die Benutzer dieser {{site.data.keyword.knowledgestudioshort}}-Instanz sind.
1. Suchen Sie den Namen des Benutzers, der geändert werden soll, und klicken Sie auf den Link **Bearbeiten**.
1. Klicken Sie auf die Rolle des Benutzers und wählen Sie die Rolle mit höheren Berechtigungen aus, auf die Sie den Benutzer hochstufen möchten. Eine Beschreibung der verfügbaren Rollen finden Sie unter [Benutzerrollen in {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/roles.html).

  **Wichtig:** Sie müssen einen Arbeitsbereich erstellen, einem Benutzer eine Dokumentgruppe zuordnen und einem Benutzer eine Annotationstask zuweisen, damit einem Benutzer mit der Rolle 'Annotatorbenutzer' Arbeitsbereiche in der {{site.data.keyword.knowledgestudioshort}}-Anwendung angezeigt werden. Richten Sie den Arbeitsbereich so bald wie möglich ein, nachdem sich Benutzer registriert haben, damit die Benutzer Ihren Arbeitsbereich schon beim ersten Starten der Anwendung sehen können. Es empfiehlt sich, die Benutzer zu benachrichtigen, wenn Sie den Arbeitsbereich eingerichtet haben, damit die Benutzer wissen, dass sie mit dem Annotieren von Dokumenten beginnen können.

1. Optional: Nachdem Sie das Verwalten von Benutzern in {{site.data.keyword.knowledgestudioshort}} abgeschlossen haben, beenden Sie die Sitzung und schließen Sie den Web-Browser. Die Benutzerschnittstelle von {{site.data.keyword.knowledgestudioshort}} enthält keine eigenständige Aktion zum Abmelden.

## Benutzerkonten inaktivieren

Wenn Sie Benutzer entfernen möchten, wiederholen Sie die vorherigen Schritte zum Öffnen der Seite 'Servicedetails'. Suchen Sie in der Liste der Benutzer-IDs den Benutzer, den Sie entfernen möchten, und klicken Sie auf **Inaktivieren**.

> **Achtung**: Wenn den betreffenden Benutzern Dokumente zum Annotieren zugewiesen sind, hat das Entfernen der Benutzerkonten Auswirkungen auf die von ihnen erstellten Annotationen. Alle Annotation der inaktivierten Benutzer, die nicht in die Ground Truth hochgestuft wurden, werden gelöscht.

### Zugehörige Tasks

[Annotationsgruppen erstellen und zuordnen](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projdocsets)
