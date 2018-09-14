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

Diese Dokumentation bezieht sich auf {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Die Dokumentation für die Vorgängerversion {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace kann über [diesen Link ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/docs/services/knowledge-studio/troubleshooting.html){: new_window} aufgerufen werden.
{: tip}

# Fehlerbehebung, Unterstützung und häufige Fragen
{: #troubleshooting}

Zum Isolieren und Beheben von Problemen mit Ihren {{site.data.keyword.IBM_notm}}-Produkten können Sie die Fehlerbehebungs- und Unterstützungsinformationen verwenden. Diese Informationen enthalten Anleitungen zur Verwendung der Ressourcen für die Problembestimmung, die mit Ihren {{site.data.keyword.IBM_notm}} Produkten bereitgestellt werden (einschließlich {{site.data.keyword.knowledgestudiofull}}).
{: shortdesc}

## Verfahren zur Fehlerbehebung
{: #ts_overview}

Die *Fehlerbehebung* ist eine systematische Methode zur Behebung eines Problems. Das Ziel der Fehlerbehebung ist es, festzustellen, warum etwas nicht wie erwartet funktioniert und wie das Problem behoben werden kann. Bestimmte einheitliche Verfahren können bei der Fehlerbehebung nützlich sein.

Der erste Schritt im Fehlerbehebungsprozess ist die vollständige Beschreibung des Problems. Problembeschreibungen unterstützen Sie und die Mitarbeiter des {{site.data.keyword.IBM_notm}} Technical Support bei der Suche nach der Problemursache. Dieser Schritt umfasst die folgenden grundlegenden Fragen:

- Welche Symptome weist das Problem auf?
- Wo tritt das Problem auf?
- Wann tritt das Problem auf?
- Unter welchen Bedingungen tritt das Problem auf?
- Kann das Problem reproduziert werden?

Die Antworten auf diese Fragen liefern in der Regel eine gute Beschreibung des Problems, die zu einer Problemlösung beitragen kann.

### Welche Symptome weist das Problem auf?
{: #ts_overview_symptoms}

Bei der Beschreibung eines Problems lautet die offensichtlichste Frage "Was ist das Problem?" Diese Frage erscheint zunächst einfach. Sie können sie jedoch in mehrere fokussiertere Fragen unterteilen, die ein weitaus genaueres Bild des Problems liefern. Hierzu können die beispielsweise die folgenden Fragen gehören:

- Wer oder was meldet das Problem?
- Wie lauten die Fehlercodes und -nachrichten?
- Wie schlägt das System fehl? Handelt es sich beispielsweise um eine Schleife, eine Blockierung, einen Absturz, eine Leistungsverschlechterung oder ein fehlerhaftes Ergebnis?

### Wo tritt das Problem auf?
{: #ts_overview_where}

Den Ursprung des Problems festzustellen, ist nicht immer einfach. Dieser Schritt ist jedoch einer der wichtigsten bei der Behebung eines Problems. Zahlreiche Technologieebenen können sich zwischen der Komponente, die den Fehler meldet, und der Komponente, bei der der Fehler auftritt, befinden. Netze, Platten und Treiber sind nur einige der Komponenten, die bei der Untersuchung von Problemen zu berücksichtigen sind.

Mithilfe der folgenden Fragen können Sie den Ursprung des Problems eingrenzen, um so die Ebene zu isolieren, auf der der Fehler auftritt:

- Ist das Problem für eine Plattform oder ein Betriebssystem spezifisch oder tritt es plattform- bzw. betriebssystemunabhängig auf?
- Werden die aktuelle Umgebung und Konfiguration unterstützt?
- Tritt das Problem bei allen Benutzern auf?
- (Bei Installationen an mehreren Standorten.) Tritt das Problem an allen Standorten auf?

Wenn eine Ebene das Problem meldet, befindet sich der Ursprung des Problems nicht notwendigerweise auf dieser Ebene. Bei der Identifizierung des Problemursprungs spielen genaue Kenntnisse der betreffenden Umgebung eine wichtige Rolle. Nehmen Sie sich Zeit, um die Umgebung, in der das Problem auftritt, umfassend zu beschreiben. Zu den relevanten Informationen gehören z. B. das Betriebssystem und die Betriebssystemversion, die gesamte verwendete Software einschließlich der Versionsinformationen sowie Details zur Hardware. Vergewissern Sie sich, dass eine Umgebung verwendet wird, bei der es sich um eine unterstützte Konfiguration handelt. Zahlreiche Probleme sind auf nicht kompatible Softwareversionen zurückzuführen, die nicht zusammen ausgeführt werden dürfen oder die noch nicht abschließend auf Kompatibilität getestet wurden.

### Wann tritt das Problem auf?
{: #ts_overview_when}

Erstellen Sie eine detaillierte Zeitachse der Ereignisse, die im Vorfeld eines Fehlers auftreten, vor allem bei Problemen, die nur ein einziges Mal vorkommen. Am einfachsten lässt sich eine Zeitachse rückwärts erstellen: Beginnen Sie mit dem Zeitpunkt, zu dem ein Fehler gemeldet wurde (so genau wie möglich, gegebenenfalls bis auf die Millisekunde genau), und arbeiten Sie die verfügbaren Protokolle und Informationen zeitlich rückwärts durch. Normalerweise müssen Sie nur bis zum ersten verdächtigen Ereignis zurück gehen, das Sie in einem Diagnoseprotokoll finden.

Beantworten Sie die folgenden Fragen, um eine detaillierte Zeitachse der Ereignisse zu erstellen:

- Tritt das Problem ausschließlich zu einer bestimmten Uhrzeit auf?
- Wie häufig tritt das Problem auf?
- Welche Abfolge von Ereignissen tritt bis zu dem Zeitpunkt auf, an dem das Problem gemeldet wird?
- Tritt das Problem nach einer Umgebungsänderung auf, wie z. B. nach einem Upgrade oder der Installation von Software oder Hardware?

Die Antworten auf diese Art von Fragen können Ihnen ein Bezugssystem liefern, in dem Sie das Problem untersuchen können.

### Unter welchen Bedingungen tritt das Problem auf?
{: #ts_overview_conditions}

Ein wichtiger Teil der Fehlerbehebung besteht darin, festzustellen, welche Systeme und Anwendungen zum Zeitpunkt des Auftretens eines Problems aktiv sind. Diese Fragen zur verwendeten Umgebung können Sie bei der Ermittlung der zugrunde liegenden Fehlerursache unterstützen:

- Tritt das Problem immer bei der Ausführung derselben Task auf?
- Muss eine bestimmte Abfolge von Ereignissen stattfinden, damit das Problem auftritt?
- Treten bei anderen Anwendungen zum selben Zeitpunkt Fehler auf?

Die Antworten auf diese Art von Fragen unterstützen Sie bei der Beschreibung der Umgebung, in der das Problem auftritt, und bei der Korrelation möglicher Abhängigkeiten. Beachten Sie dabei, dass mehrere Probleme, die zu ungefähr demselben Zeitpunkt aufgetreten sind, nicht unbedingt zusammenhängen müssen.

### Kann das Problem reproduziert werden?
{: #ts_overview_reproduce}

Aus Sicht der Fehlerbehebung ist das ideale Problem ein reproduzierbares Problem. Normalerweise stehen bei einem reproduzierbaren Problem zusätzliche Tools und Prozeduren für die Untersuchung zur Verfügung. Daher sind das Debugging und die Fehlerbehebung bei reproduzierbare Probleme häufig einfacher.

Reproduzierbare Probleme können jedoch auch einen Nachteil haben: Wenn das Problem einen signifikanten Einfluss auf die Geschäftsabläufe hat, soll es natürlich nicht erneut auftreten. Reproduzieren Sie das Problem in einer Test- oder Entwicklungsumgebung, falls möglich. Dies bietet Ihnen größere Flexibilität und Kontrolle bei der Untersuchung.

- Kann das Problem auf einem Testsystem reproduziert werden?
- Tritt derselbe Problemtyp bei mehreren Benutzern oder Anwendungen auf?
- Kann das Problem durch die Ausführung eines einzelnen Befehls, einer Befehlsgruppe oder einer bestimmten Anwendung reproduziert werden?

## Es kann keine Instanz unter dem Lite-Plan erstellt werden
{: #wks_ts_lite}

### Problem
{: #wks_ts_lite_problem}

Beim Erstellen einer {{site.data.keyword.knowledgestudioshort}}-Instanz unter dem Lite-Plan wird die folgende Fehlernachricht angezeigt: `Error 331: We are unable to process your request. Please try again later or contact the {{site.data.keyword.IBM_notm}} Helpdesk.`

### Ursachen
{: #wks_ts_lite_causes}

Für {{site.data.keyword.knowledgestudioshort}} ist nur ein Lite-Plan pro Organisation zulässig.

### Problem beheben
{: #wks_ts_lite_resolve}

Erstellen Sie ein Konto, das nicht der Organisation zugeordnet ist.

Wenn Sie Ihr aktuelles Konto für eine {{site.data.keyword.knowledgestudioshort}}-Instanz auf einem Lite-Plan verwenden müssen und Ihr Benutzerkonto einem kostenpflichtigen Konto zugeordnet ist, können Sie einen Fall erstellen. Weitere Informationen hierzu finden Sie unter [Kontaktaufnahme mit {{site.data.keyword.IBM_notm}} Support](/docs/services/watson-knowledge-studio/troubleshooting.html#ts_contactingibmsupport).

Wenn Sie Ihr aktuelles Konto für eine {{site.data.keyword.knowledgestudioshort}}-Instanz auf einem Lite-Plan verwenden müssen und Ihr Benutzerkonto keinem bezahlten Konto zugeordnet ist, senden Sie Ihr Problem an [ {{site.data.keyword.IBM_notm}} developerWorks Answers ![External link icon](../../icons/launch-glyph.svg "Symbol für externen Link")](https://developer.ibm.com/answers/topics/watson-knowledge-studio/){: new_window}. Versehen Sie Ihre Frage mit einem Tag: **WATSON-KNOWLEDGE-STUDIO**.

## Anwendung kann nicht aufgerufen werden
{: #wks_ts_access}

Informieren Sie sich darüber, wie Sie Benutzern Zugriff auf {{site.data.keyword.knowledgestudioshort}} gewähren und allgemeine Zugriffsprobleme beheben können.

Sie benötigen eine {{site.data.keyword.IBM_notm}} Benutzerregistrierung mit entsprechenden Berechtigungen, um eine {{site.data.keyword.IBM_notm}} {{site.data.keyword.knowledgestudioshort}}-Instanz anzufordern.

### Administrator
{: #wks_ts_access_administrator}

Jeder {{site.data.keyword.knowledgestudioshort}}-Instanz ist eine Administratorrolle zugeordnet. Der Person, die sich zuerst für die Nutzung der Anwendung registriert, wird automatisch die Administratorrolle zugeordnet. Der Administrator kann weitere Benutzer einladen.

Informationen zum Einladen von Benutzern für die Verwendung Ihrer Instanz der Anwendung finden Sie unter [Team zusammenstellen](/docs/services/watson-knowledge-studio/team.html).

### Annotatorbenutzer
{: #wks_ts_access_annotator}

Falls Sie von einem anderen Benutzer eingeladen wurden, an dessen {{site.data.keyword.knowledgestudioshort}}-Instanz als Annotatorbenutzer mitzuwirken, haben Sie wahrscheinlich eine E-Mail-Einladung erhalten. Zuerst müssen Sie sich bei {{site.data.keyword.IBM_notm}} registrieren, falls Sie noch nicht über {{site.data.keyword.IBM_notm}} Berechtigungsnachweise verfügen. Wenn Sie bei {{site.data.keyword.IBM_notm}} registriert sind die Einladung akzeptiert haben, erhalten Sie Zugriff auf die Instanz. Nachdem Sie Zugriff erhalten haben und bevor Sie mit dem Annotieren von Dokumenten beginnen können, muss der Administrator oder ein Projektleiter der Instanz Sie zum Arbeitsbereich hinzufügen und Ihnen eine Annotationstask zuordnen. Erst nachdem Ihnen eine Task zugeordnet wurde, können Sie Aktionen in der {{site.data.keyword.knowledgestudioshort}}-Instanz ausführen. Verwenden Sie den Ground Truth-Editor, um Dokumente zu annotieren. Die beste Leistung erzielen Sie mit einem Google Chrome-Browser.

Hilfreiche Informationen zum Arbeiten mit dem Ground Truth-Editor finden Sie unter [Dokumente annotieren](/docs/services/watson-knowledge-studio/user-guide.html).

## Datenerfassung
{: #content}

Für Standardpläne (Lite, Standard, Pro) verwendet {{site.data.keyword.knowledgestudioshort}} standardmäßig Clientdaten, um den Service zu verbessern. Diese Daten werden nur zusammengefasst verwendet. Die Clientdaten werden weder freigegeben noch öffentlich gemacht.


Wenn Sie über die Administratorrolle verfügen, können Sie dieses Standardverhalten ändern, indem Sie die Datenerfassungseinstellung auf der Seite 'Servicedetails' auswählen.

Bei Premium-Plänen und Dedicated-Konten verwendet {{site.data.keyword.knowledgestudioshort}} keine Clientdaten, um den Service zu verbessern.

Details hierzu finden Sie in der aktuellen [{{site.data.keyword.knowledgestudioshort}}-Servicebeschreibung ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/software/sla/sladb.nsf/searchsaas/?searchview&searchorder=4&searchmax=0&query=Knowledge+Studio){: new_window}.

## Experimentelle Services und Features: Was bedeutet *experimentell*?
{: #experimental}

{{site.data.keyword.IBM_notm}} veröffentlicht experimentelle Services und Features, die Sie testen können. Diese Services sind möglicherweise instabil, ändern sich häufig, sodass sie nicht mit früheren Versionen kompatibel sind, und können kurzfristig eingestellt werden. Diese Services und Features werden nicht für die Verwendung in Produktionsumgebungen empfohlen.

Weitere Informationen zu experimentellen Services finden Sie in der [{{site.data.keyword.cloud_notm}}-Dokumentation ![External link icon](../../icons/launch-glyph.svg "Symbol für externen Link") ](https://console.bluemix.net/docs/get-support/servicessupport.html#s-services-exporcont){: new_window}. Vollständige Details zu experimentellen Services enthält die aktuelle Version der [{{site.data.keyword.cloud_notm}} Service Description ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/software/sla/sladb.nsf/sla/bm?OpenDocument){: new_window}.

## Probleme mit dem Speicherbereich
{: #storage}

Wenn der Speichergrenzwert für Ihren Abonnementplan erreicht ist, können Sie angefangene Tasks möglicherweise nicht abschließen.

### Symptome
{: #storage_symptoms}

Beim Ausführen einer der folgenden Tasks weist gegebenenfalls eine Nachricht darauf hin, dass der zulässige Speicherbereich ausgeschöpft ist:

- Dokumente oder Wörterverzeichnisse hochladen
- Modell oder Modellversion bereitstellen
- Vorannotator auf Dokumente anwenden

### Ursachen
{: #storage_causes}

Der Speichergrenzwert ist erreicht oder würde beim Ausführen der Aktion überschritten.

### Problem beheben
{: #storage_resolve}

Die größten Verbraucher von Speicherbereich sind Modelle für maschinelles Lernen und regelbasierte Modelle. Mit den folgenden Maßnahmen können Sie Speicherbereich freigeben:

- Löschen Sie Snapshot-Versionen der Modelle, auf die Sie wahrscheinlich nicht mehr zurückgreifen werden.
- Löschen Sie alle Modelle, die Sie nicht benötigen.
- Wenn Ihre Modelle nicht gelöscht werden dürfen, sollten Sie ein Upgrade auf einen Plan mit einem größeren Speicherkontingent in Erwägung ziehen.

Warten Sie nach dem Entfernen von Modellen oder Modellversionen eine Stunde, bevor Sie die Aktion wiederholen, die der Auslöser für die Fehlernachricht war. Es kann bis zu einer Stunde dauern, bis der von Ihnen freigegebene Speicherbereich wieder verwendet werden kann.

Um die monatliche Rechnung in Grenzen zu halten, können Sie (sofern Sie über die Administratorrolle und ein Premium- oder Standardkonto verfügen) auf der Seite 'Servicedetails' in {{site.data.keyword.knowledgestudioshort}} einen Speichergrenzwert festlegen. Um die Seite 'Servicedetails' zu öffnen und einen Speichergrenzwert festzulegen, klicken Sie in der oberen Navigationsleiste in {{site.data.keyword.knowledgestudioshort}} auf das Symbol **Einstellungen**, klicken Sie auf **Servicedetails anzeigen/ändern** und klicken Sie anschließend auf den Link **Speichergrenzwert festlegen**.
{: tip}

## Kontaktaufnahme mit IBM Support
{: #ts_contactingibmsupport}

Der {{site.data.keyword.IBM_notm}} Support bietet Unterstützung bei Produktfehlern, beantwortet häufig gestellte Fragen und unterstützt die Benutzer beim Beheben von Problemen im Zusammenhang mit dem Produkt.

- **Lite-Plan-Kunden, die keinem gebührenpflichtigen Konto zugeordnet sind**

    Fragen Sie die Mitglieder der Community für Entwickler nach Antworten auf Ihre Fragen. Links finden Sie im Abschnitt "Entwickler-Community" unter dem Inhaltsverzeichnis.

- **Kunden, die einem gebührenpflichtigen Konto zugeordnet sind**

    Als Kunde, der einem gebührenpflichtigen Konto zugeordnet ist, können Sie ebenfalls Fragen an andere Benutzer stellen und aus ihren Fragen lernen. Die Entwickler-Communitys sind frei zugänglich und bieten einen guten Ausgangspunkt zum Klären von Fragen. Links finden Sie im Abschnitt "Entwickler-Community" unter dem Inhaltsverzeichnis.

    **Wenden Sie sich an den {{site.data.keyword.IBM_notm}} Support:**

    Sie müssen die Berechtigung haben, Support-Fälle im {{site.data.keyword.cloud_notm}}-Service-Portal zu erstellen.

    1. Grenzen Sie das Problem ein, sammeln Sie Hintergrundinformationen und legen Sie die Dringlichkeit des Problems fest.
    1. Sammeln Sie Diagnoseinformationen, falls möglich.
    1. Erstellen Sie einen Fall in [{{site.data.keyword.cloud_notm}} Service Portal ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link") ](https://watson.service-now.com/wcp){: new_window}.
