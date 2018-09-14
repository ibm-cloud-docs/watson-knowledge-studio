---

copyright:
  years: 2018
lastupdated: "2018-07-02"

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

# Benutzerrollen in {{site.data.keyword.knowledgestudioshort}}
{: #roles}

{{site.data.keyword.knowledgestudiofull}}-Rollen werden verwendet, um ein Team von Personen zu organisieren, die maschinelles Lernen oder regelbasierte Modelle erstellen.
{: shortdesc}

## Anmerkungen zu den Rollen in {{site.data.keyword.knowledgestudioshort}}
{: #notes}

- Benutzerrollen in {{site.data.keyword.knowledgestudioshort}} werden auf den folgenden Ebenen verwaltet:
  - {{site.data.keyword.cloud}}-Rollen steuern den Zugriff auf {{site.data.keyword.cloud_notm}}-Services. {{site.data.keyword.knowledgestudioshort}} verwendet Cloud Foundry für die Zugriffssteuerung, für die die {{site.data.keyword.knowledgestudioshort}}-Benutzer die Entwicklerrolle haben müssen. Siehe [Cloud Foundry-Zugriff ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/docs/iam/cfaccess.html){: new_window}.
  - {{site.data.keyword.knowledgestudioshort}}-Rollen steuern den Zugriff auf die {{site.data.keyword.knowledgestudioshort}}-Funktionalität, wie auf dieser Seite beschrieben.
- Eine {{site.data.keyword.knowledgestudioshort}}-Rolle ist nicht erforderlich, um eine Instanz von {{site.data.keyword.knowledgestudioshort}} zu erstellen. Wenn jedoch eine Person eine Instanz von {{site.data.keyword.knowledgestudioshort}} erstellt, wird dem ersten Benutzer, der {{site.data.keyword.knowledgestudioshort}} startet, die {{site.data.keyword.knowledgestudioshort}}-Administratorrolle zugewiesen.
- Um einen Arbeitsbereich zu verwalten, müssen Projektleiter diesem Arbeitsbereich von einem Administrator zugeordnet werden.
- Administratoren und Projektleiter können die Rolle 'Annotatorbenutzer' übernehmen, ihnen müssen jedoch Annotationsgruppen auf die gleiche Weise wie Annotationsgruppen den Annotatorbenutzern zugeordnet werden.
- Nach der Zuordnung können Benutzerrollen nicht von einer höheren Ebene herabgestuft werden, um die Berechtigungen zu verringern. Administratoren können nicht zu Projektleitern oder Annotatorbenutzern herabgestuft werden, und Projektleiter können nicht auf Annotatorbenutzern herabgestuft werden. Informationen zum Hinzufügen von Benutzern, zum Aktualisieren von Rollen und zum Inaktivieren von Benutzerkonten finden Sie unter [Team zusammenstellen](/docs/services/watson-knowledge-studio/team.html). 

## Rollenbeschreibungen
{: #descriptions}
{{site.data.keyword.knowledgestudioshort}}-Rollen werden in der folgenden Tabelle beschrieben. Die Rollen werden in der Reihenfolge von der höchsten bis zur niedrigsten Berechtigungsstufe aufgelistet.

| Rolle | Beschreibung |
|------|-------------|
| Admin (Administrator) | Verantwortlich für Verwaltungsaufgaben, z. B. für die Verwaltung von Benutzern, den Ressourcenverbrauch und die monatlichen Gebühren. In großen Teameinstellungen nehmen Admins selten am Modellentwicklungsprozess teil. | Projektleiter | Verantwortlich für die allgemeine Organisation des Arbeitsbereichs, dem sie oder er zugeordnet ist. Zu den Tasks gehören das Erstellen des Typensystems, das Verwalten von Assets, die Verwaltung von Annotationstasks, das Auswerten des Modells für maschinelles Lernen und die Implementierung von Modellen. Benutzer in dieser Rolle benötigen Branchenwissen, weil sie das Typsystem erstellen, den Annotatorbenutzern zeigen, wie das Typsystem korrekt angewendet wird, und die Modellqualität bewerten. |
| Annotatorbenutzer | Führt die Beschriftung der Entitätserwähnungen und Beziehungserwähnungen in den Trainingsdokumenten aus, denen er oder sie zugeordnet ist. Die Arbeit ist den Annotatorbenutzern zugeordnet und wird vom Projektleiter überwacht. Annotatorbenutzer benötigen möglicherweise Fachwissen, solange sie vom Projektleiter gezeigt bekommen, wie das Typsystem korrekt angewendet wird. |
{:caption="Tabelle 1. Rollenbeschreibungen" caption-side="top"}

## Rollenberechtigungen
{: #permissions}

Informationen zum Vergleichen der Berechtigungen für die einzelnen Rollen finden Sie in der folgenden Tabelle. In jeder Zeile wird jeweils eine Berechtigung aufgelistet. Wenn eine Rolle über diese Berechtigung verfügt, wird die Rollenspalte mit einem Häkchen markiert (&checkmark;).

| Berechtigung | Admin (Administrator) | Projektleiter | Annotatorbenutzer |
|------------|-------|-----------------|-----------------|
| Benutzerzugriff und Rollen verwalten | &checkmark; |  |  |
| Arbeitsbereiche verwalten | &checkmark; |  |  |
| Richtlinien für Typsystem und Annotationen erstellen | &checkmark; | &checkmark; |  |
| Trainingsdokument hochladen | &checkmark; | &checkmark; |  |
| Regeln verwalten | &checkmark; | &checkmark; |  |
| Dokumente vorannotieren | &checkmark; | &checkmark; |  |
| Annotationstasks verwalten | &checkmark; | &checkmark; |  |
| Annotationskonflikte mit Benutzerannotationen auflösen (*Beurteilung*) | &checkmark; | &checkmark; |  |
| Modelle für maschinelles Lernen trainieren und bewerten | &checkmark; | &checkmark; |  |
| Modelle für Laufzeitservices bereitstellen und Bereitstellung zurücknehmen | &checkmark; | &checkmark; |  |
| Dokumentannotationen ausführen | &checkmark; | &checkmark; | &checkmark; |
{:caption="Tabelle 2. Rollenberechtigungen" caption-side="top"}
