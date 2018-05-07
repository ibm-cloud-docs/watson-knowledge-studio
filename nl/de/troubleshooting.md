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

Bei der Beschreibung eines Problems lautet die offensichtlichste Frage "Was ist das Problem?" Diese Frage erscheint zunächst einfach. Sie können sie jedoch in mehrere fokussiertere Fragen unterteilen, die ein weitaus genaueres Bild des Problems liefern. Hierzu können die beispielsweise die folgenden Fragen gehören:

- Wer oder was meldet das Problem?
- Wie lauten die Fehlercodes und -nachrichten?
- Wie schlägt das System fehl? Handelt es sich beispielsweise um eine Schleife, eine Blockierung, einen Absturz, eine Leistungsverschlechterung oder ein fehlerhaftes Ergebnis?

### Wo tritt das Problem auf?

Den Ursprung des Problems festzustellen, ist nicht immer einfach. Dieser Schritt ist jedoch einer der wichtigsten bei der Behebung eines Problems. Zahlreiche Technologieebenen können sich zwischen der Komponente, die den Fehler meldet, und der Komponente, bei der der Fehler auftritt, befinden. Netze, Platten und Treiber sind nur einige der Komponenten, die bei der Untersuchung von Problemen zu berücksichtigen sind.

Mithilfe der folgenden Fragen können Sie den Ursprung des Problems eingrenzen, um so die Ebene zu isolieren, auf der der Fehler auftritt:

- Ist das Problem für eine Plattform oder ein Betriebssystem spezifisch oder tritt es plattform- bzw. betriebssystemunabhängig auf?
- Werden die aktuelle Umgebung und Konfiguration unterstützt?
- Tritt das Problem bei allen Benutzern auf?
- (Bei Installationen an mehreren Standorten.) Tritt das Problem an allen Standorten auf?

Wenn eine Ebene das Problem meldet, befindet sich der Ursprung des Problems nicht notwendigerweise auf dieser Ebene. Bei der Identifizierung des Problemursprungs spielen genaue Kenntnisse der betreffenden Umgebung eine wichtige Rolle. Nehmen Sie sich Zeit, um die Umgebung, in der das Problem auftritt, umfassend zu beschreiben. Zu den relevanten Informationen gehören z. B. das Betriebssystem und die Betriebssystemversion, die gesamte verwendete Software einschließlich der Versionsinformationen sowie Details zur Hardware. Vergewissern Sie sich, dass eine Umgebung verwendet wird, bei der es sich um eine unterstützte Konfiguration handelt. Zahlreiche Probleme sind auf nicht kompatible Softwareversionen zurückzuführen, die nicht zusammen ausgeführt werden dürfen oder die noch nicht abschließend auf Kompatibilität getestet wurden.

### Wann tritt das Problem auf?

Erstellen Sie eine detaillierte Zeitachse der Ereignisse, die im Vorfeld eines Fehlers auftreten, vor allem bei Problemen, die nur ein einziges Mal vorkommen. Am einfachsten lässt sich eine Zeitachse rückwärts erstellen: Beginnen Sie mit dem Zeitpunkt, zu dem ein Fehler gemeldet wurde (so genau wie möglich, gegebenenfalls bis auf die Millisekunde genau), und arbeiten Sie die verfügbaren Protokolle und Informationen zeitlich rückwärts durch. Normalerweise müssen Sie nur bis zum ersten verdächtigen Ereignis zurück gehen, das Sie in einem Diagnoseprotokoll finden.

Beantworten Sie die folgenden Fragen, um eine detaillierte Zeitachse der Ereignisse zu erstellen:

- Tritt das Problem ausschließlich zu einer bestimmten Uhrzeit auf?
- Wie häufig tritt das Problem auf?
- Welche Abfolge von Ereignissen tritt bis zu dem Zeitpunkt auf, an dem das Problem gemeldet wird?
- Tritt das Problem nach einer Umgebungsänderung auf, wie z. B. nach einem Upgrade oder der Installation von Software oder Hardware?

Die Antworten auf diese Art von Fragen können Ihnen ein Bezugssystem liefern, in dem Sie das Problem untersuchen können.

### Unter welchen Bedingungen tritt das Problem auf?

Ein wichtiger Teil der Fehlerbehebung besteht darin, festzustellen, welche Systeme und Anwendungen zum Zeitpunkt des Auftretens eines Problems aktiv sind. Diese Fragen zur verwendeten Umgebung können Sie bei der Ermittlung der zugrunde liegenden Fehlerursache unterstützen:

- Tritt das Problem immer bei der Ausführung derselben Task auf?
- Muss eine bestimmte Abfolge von Ereignissen stattfinden, damit das Problem auftritt?
- Treten bei anderen Anwendungen zum selben Zeitpunkt Fehler auf?

Die Antworten auf diese Art von Fragen unterstützen Sie bei der Beschreibung der Umgebung, in der das Problem auftritt, und bei der Korrelation möglicher Abhängigkeiten. Beachten Sie dabei, dass mehrere Probleme, die zu ungefähr demselben Zeitpunkt aufgetreten sind, nicht unbedingt zusammenhängen müssen.

### Kann das Problem reproduziert werden?

Aus Sicht der Fehlerbehebung ist das ideale Problem ein reproduzierbares Problem. Normalerweise stehen bei einem reproduzierbaren Problem zusätzliche Tools und Prozeduren für die Untersuchung zur Verfügung. Daher sind das Debugging und die Fehlerbehebung bei reproduzierbare Probleme häufig einfacher.

Reproduzierbare Probleme können jedoch auch einen Nachteil haben: Wenn das Problem einen signifikanten Einfluss auf die Geschäftsabläufe hat, soll es natürlich nicht erneut auftreten. Reproduzieren Sie das Problem in einer Test- oder Entwicklungsumgebung, falls möglich. Dies bietet Ihnen größere Flexibilität und Kontrolle bei der Untersuchung.

- Kann das Problem auf einem Testsystem reproduziert werden?
- Tritt derselbe Problemtyp bei mehreren Benutzern oder Anwendungen auf?
- Kann das Problem durch die Ausführung eines einzelnen Befehls, einer Befehlsgruppe oder einer bestimmten Anwendung reproduziert werden?

## Probleme mit AlchemyLanguage-Modellen
{: #wks_ts_deployed_model_deleted}

### Problem

Ein AlchemyLanguage-Modell kann nicht bereitgestellt werden oder die Bereitstellung war erfolgreich, aber das Modell kann nicht verwendet werden.

### Symptome

- Der Status des bereitgestellten Modells zeigt, dass ein Fehler aufgetreten ist.
- Der Status des bereitgestellten Modells zeigt, dass das Modell verfügbar ist, aber Sie können es nicht verwenden.
- Das Modell wurde erfolgreich bereitgestellt und konnte verwendet werden, aber jetzt funktioniert es nicht mehr.

### Ursachen

Die folgenden Ereignisse können zu Problemen mit bereitgestellten Modellen führen:

- Wenn der {{site.data.keyword.alchemyapishort}}-Schlüssel beim Hinzufügen des Schlüssels im Parameter `apikey` des REST-API-Aufrufs nicht korrekt eingegeben wird, schlägt der Aufruf fehl. Dies gilt auch für die Modell-ID. Es wird empfohlen, die Modell-ID und den API-Schlüssel durch Kopieren und Einfügen anzugeben, um Eingabefehler zu vermeiden.
- Wenn Sie einen {{site.data.keyword.alchemyapishort}}-Schlüssel angeben, der ungültig oder nicht zum Bereitstellen eines angepassten Modells berechtigt ist, gibt der Bereitstellungsprozess zwar an, dass das Modell erfolgreich bereitgestellt wurde, aber Sie können das Modell nicht verwenden.
- Wenn Sie beim Arbeiten mit {{site.data.keyword.alchemylanguageshort}} in {{site.data.keyword.Bluemix}} alle Serviceinstanzen löschen, die einem {{site.data.keyword.alchemyapishort}}-Schlüssel in {{site.data.keyword.Bluemix_notm}} zugeordnet sind, werden alle bereitgestellten Modelle, die auf diesen Schlüssel verweisen, aus dem Service entfernt. {{site.data.keyword.Bluemix_notm}} überprüft in regelmäßigen Abständen, ob die registrierten Modelle einem gültigen Schlüssel zugeordnet sind. Modelle, die keinem gültigen Schlüssel zugeordnet sind, werden gelöscht. Wenn Ihr Modell unter einem Schlüssel bereitgestellt wurde, der später gelöscht wurde, wird der Status des Modells in `Fehler` geändert.

### Problem beheben

1. Überprüfen Sie den Status der Bereitstellung.

    Melden Sie sich bei {{site.data.keyword.knowledgestudioshort}} als Administrator an. Überprüfen Sie auf der Seite **Modellverwaltung** > **Versionen** in der Spalte **Status** den Status des Modells, das Sie bereitgestellt haben.

1. Wenn das Modell den Bereitstellungsstatus `Fehler` aufweist oder wenn der Status `Verfügbar` angezeigt wird, aber das Modell nicht verwendet werden kann, heben Sie die Bereitstellung des Modells auf, indem Sie auf **Bereitstellung aufheben** klicken.
1. Stellen Sie das Modell erneut bereit.

    Verwenden Sie nur einen gültigen {{site.data.keyword.alchemyapishort}}-Schlüssel, der zum Bereitstellen von Modellen berechtigt ist, und geben Sie die Modell-ID und den API-Schlüssel durch Kopieren und Einfügen als Parameter im API-Aufruf an.

**Zugehörige Tasks**:

[Modell für maschinelles Lernen in {{site.data.keyword.IBM_notm}} {{site.data.keyword.alchemylanguageshort}}](/docs/services/watson-knowledge-studio/publish-ml.html#wks_mabluemix) bereitstellen

## Ein kostenloses Konto kann nicht erstellt werden
{: #wks_ts_free}

### Problem

Beim Erstellen eines kostenlosen Kontos wird die folgende Fehlernachricht angezeigt: `Error 331: We are unable to process your request. Please try again later or contact the {{site.data.keyword.IBM_notm}} Helpdesk.`

### Ursachen

Für {{site.data.keyword.knowledgestudioshort}} ist nur ein kostenloses Konto pro Organisation zulässig.

### Problem beheben

Erstellen Sie ein Konto, das nicht der Organisation zugeordnet ist.

Wenn Sie für den kostenlosen Test Ihr aktuelles Konto verwenden müssen, aber Ihre Benutzer-ID ist einem gebührenpflichtigen Konto zugeordnet, können Sie ein Support-Ticket einreichen. Weitere Informationen hierzu finden Sie unter [Kontaktaufnahme mit {{site.data.keyword.IBM_notm}} Support](/docs/services/watson-knowledge-studio/troubleshooting.html#ts_contactingibmsupport).

Wenn Sie für den kostenlosen Test Ihr aktuelles Konto verwenden müssen und Ihr Benutzerkonto keinem gebührenpflichtigen Konto zugeordnet ist, senden Sie Ihr Problem an [{{site.data.keyword.IBM_notm}} developerWorks Answers](https://developer.ibm.com/answers/topics/wks/) und versehen Sie die Frage mit dem Tag **WKS**.

## Anwendung kann nicht aufgerufen werden
{: #wks_ts_access}

Informieren Sie sich darüber, wie Sie Benutzern Zugriff auf {{site.data.keyword.knowledgestudioshort}} gewähren und allgemeine Zugriffsprobleme beheben können.

Sie benötigen eine {{site.data.keyword.IBM_notm}} Benutzerregistrierung mit entsprechenden Berechtigungen, um eine {{site.data.keyword.IBM_notm}} {{site.data.keyword.knowledgestudioshort}}-Instanz anzufordern.

### Administrator

Jeder {{site.data.keyword.knowledgestudioshort}}-Instanz ist eine Administratorrolle zugeordnet. Der Person, die sich zuerst für die Nutzung der Anwendung registriert, wird automatisch die Administratorrolle zugeordnet. Der Administrator kann weitere Benutzer einladen.

Informationen zum Einladen von Benutzern für die Verwendung Ihrer Instanz der Anwendung finden Sie unter [Team zusammenstellen](/docs/services/watson-knowledge-studio/team.html).

### Annotatorbenutzer

Falls Sie von einem anderen Benutzer eingeladen wurden, an dessen {{site.data.keyword.knowledgestudioshort}}-Instanz als Annotatorbenutzer mitzuwirken, haben Sie wahrscheinlich eine E-Mail-Einladung erhalten. Zuerst müssen Sie sich bei {{site.data.keyword.IBM_notm}} registrieren, falls Sie noch nicht über {{site.data.keyword.IBM_notm}} Berechtigungsnachweise verfügen. Wenn Sie bei {{site.data.keyword.IBM_notm}} registriert sind die Einladung akzeptiert haben, erhalten Sie Zugriff auf die Instanz. Nachdem Sie Zugriff erhalten haben und bevor Sie mit dem Annotieren von Dokumenten beginnen können, muss der Administrator oder ein Projektleiter der Instanz Sie zum Arbeitsbereich hinzufügen und Ihnen eine Annotationstask zuordnen. Erst nachdem Ihnen eine Task zugeordnet wurde, können Sie Aktionen in der {{site.data.keyword.knowledgestudioshort}}-Instanz ausführen. Verwenden Sie den Ground Truth-Editor, um Dokumente zu annotieren. Die beste Leistung erzielen Sie mit einem Google Chrome-Browser.

Hilfreiche Informationen zum Arbeiten mit dem Ground Truth-Editor finden Sie unter [Dokumente annotieren](/docs/services/watson-knowledge-studio/user-guide.html).

## Experimentelle Services: Was bedeutet *experimentell*?
{: #experimental}

Informationen zu experimentellen Services finden Sie in der [{{site.data.keyword.Bluemix_notm}}-Dokumentation](/docs/services/index.html#experimental_services). Vollständige Details zu experimentellen Services enthält die aktuelle Version der [{{site.data.keyword.Bluemix_notm}} Service Description ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://www.ibm.com/software/sla/sladb.nsf/searchsaas/?searchview&searchorder=4&searchmax=0&query=IBM+Bluemix+Service+Description){: new_window}.

## Probleme mit dem Speicherbereich
{: #storage}

Wenn der Speichergrenzwert für Ihren Abonnementplan erreicht ist, können Sie angefangene Tasks möglicherweise nicht abschließen.

### Symptome

Beim Ausführen einer der folgenden Tasks weist gegebenenfalls eine Nachricht darauf hin, dass der zulässige Speicherbereich ausgeschöpft ist:

- Dokumente oder Wörterverzeichnisse hochladen
- Modell oder Modellversion bereitstellen
- Vorannotator auf Dokumente anwenden

### Ursachen

Der Speichergrenzwert ist erreicht oder würde beim Ausführen der Aktion überschritten.

### Problem beheben

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

### Vorbereitungen

Prüfen Sie zunächst. ob bereits eine Lösung für Ihr Problem dokumentiert ist. Suchen Sie im [{{site.data.keyword.IBM_notm}} Support Portal ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/home/entry/portal){: new_window} nach {{site.data.keyword.knowledgestudioshort}}. Klicken Sie auf der Seite mit den Suchergebnissen auf die Registerkarte **Support**, um die Ergebnisse aus den Technotes, {{site.data.keyword.IBM_notm}} Redbooks und der Dokumentation anzuzeigen. Klicken Sie auf die Registerkarte **For Developers**, um die Suchergebnisse aus der {{site.data.keyword.IBM_notm}} developerWorks-Community wie Blogs und im Forum gestellte Fragen anzuzeigen.

Nachdem Sie versucht haben, eine Antwort oder Lösung im [{{site.data.keyword.IBM_notm}} Support Portal ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/home/entry/portal){: new_window} zu finden, können Sie sich an den {{site.data.keyword.IBM_notm}} Support wenden. Welche Unterstützung für Sie verfügbar ist, hängt von Ihrem Servicetyp ab.

- **Benutzer des kostenlosen Plans**

    Fragen Sie die Mitglieder der Community für Entwickler nach Antworten auf Ihre Fragen. Links zu Communitys für Entwickler enthält der Abschnitt **Developer community** im Inhaltsverzeichnis.

- **Benutzer eines gebührenpflichtigen Plans**

    Als Benutzer eines gebührenpflichtigen Plans können Sie ebenfalls Fragen an andere Benutzer stellen und aus ihren Fragen lernen. Die Foren sind frei zugänglich und bieten einen guten Ausgangspunkt zum Klären von Fragen. Entsprechende Links enthält der Abschnitt **Developer community** im Inhaltsverzeichnis.

    Öffnen Sie ein Problemticket im [{{site.data.keyword.IBM_notm}} Cloud Service Portal ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://watson.service-now.com/wcp){: new_window}.

    > **Hinweis:** Nur als berechtigter Benutzer können Sie Probleme bei {{site.data.keyword.IBM_notm}} einreichen.

### Vorgehensweise

Gehen Sie wie folgt vor, um ein Problem beim {{site.data.keyword.IBM_notm}} Support einzureichen:

1. Grenzen Sie das Problem ein, sammeln Sie Hintergrundinformationen und legen Sie die Dringlichkeit des Problems fest.
1. Sammeln Sie Diagnoseinformationen, falls möglich.
1. Reichen Sie das Problem beim {{site.data.keyword.IBM_notm}} Support ein. Kontaktinformationen finden Sie in der Veröffentlichung [Software as a Service support guide ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www-01.ibm.com/software/support/acceleratedvalue/SaaS_Handbook_V18.pdf){: new_window}.
