---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-09"

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

Diese Dokumentation bezieht sich auf {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Die Dokumentation für die Vorgängerversion {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace kann über [diesen Link ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/docs/services/knowledge-studio/release-notes.html){: new_window} aufgerufen werden.
{: tip}

# Releaseinformationen
{: #release-notes}

Die folgenden neuen Features und Änderungen für {{site.data.keyword.knowledgestudiofull}} sind verfügbar.
{: shortdesc}

## August 2018
{: #august2018}

### Neue Features und Änderungen
{: #new-august2018}

- Einführung in eine neue Option für eine automatisierte Migration von Standardplaninstanzen von der veralteten {{site.data.keyword.IBM_notm}} Marketplace-Plattform auf die [{{site.data.keyword.cloud_notm}}-Plattform ![External link icon](../../icons/launch-glyph.svg "Symbol für externen Link") ](https://www.ibm.com/blogs/bluemix/2017/12/watson-knowledge-studio-ibm-cloud/){: new_window}. Wenn Sie über eine Standardinstanz auf der veralteten Plattform verfügen, haben Sie die Möglichkeit der Migration. Siehe [Auf {{site.data.keyword.cloud_notm}} migrieren](/docs/services/watson-knowledge-studio/client-migration.html).

## Juli 2018
{: #july2018}

### Neue Features und Änderungen
{: #new-july2018}

- Die Seite **Bereitgestellte Modelle** wurde aktualisiert, damit Modelle von {{site.data.keyword.knowledgestudioshort}}-Instanzen eingeschlossen werden, die von [IAM*-Ressourcengruppen* verwaltet werden ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/docs/iam/users_roles.html){: new_window}, zusätzlich zu Modellen, die von [Cloud Foundry*-Organisationen* ![External link icon](../../icons/launch-glyph.svg "Symbol für externen Link") verwaltet werden](https://{DomainName}/docs/iam/cfaccess.html){: new_window}.

   Was Sie auf der Seite 'Bereitgestellte Modelle' sehen, hängt von der [-Region ![External link icon](../../icons/launch-glyph.svg "Symbol für externen Link") ](https://{DomainName}/docs/resources/services_region.html){: new_window} ab, in der Ihre {{site.data.keyword.knowledgestudioshort}}-Instanz gehostet wird. Wenn die Region Instanzen unterstützt, die von beiden Zugriffsmanagementmethoden verwaltet wird, wird eine Registerkarte für jede Methode angezeigt. Modelle aus Instanzen, die von IAM verwaltet werden, werden auf der Registerkarte **Ressourcengruppen** aufgelistet. Modelle aus Instanzen, die von Cloud verwaltet werden, werden auf der Registerkarte **Organisationen** aufgelistet. 

  Wenn die Region Instanzen unterstützt, die nur von einer der beiden Zugriffsmanagementmethoden verwaltet wird, wird nur eine Liste mit Modellen angezeigt, da nur eine einzige Zugriffsverwaltungsmethode anwendbar ist.

   Um die Seite **Bereitgestellte Modelle** anzuzeigen, klicken Sie in der Menüleiste rechts oben im Menü **Einstellungen** auf **Bereitgestellte Modelle verwalten**. Informationen zum Aufheben der Bereitstellung von Modellen auf der Seite **Bereitgestellte Modelle** finden Sie unter [Bereitstellung von Modellen für maschinelles Lernen aufheben](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) und [Bereitstellung von regelbasierten Modellen aufheben](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model).

- Die Navigation wurde geändert, um sie besser an den {{site.data.keyword.knowledgestudioshort}}-Workflow auszurichten. Außerdem wurde die folgende Funktionalität neu organisiert:

    - In der vorherigen Version wurde die Verwaltung von Wörterverzeichnissen als Teil der Seite mit den Vorannotatoren einbezogen. Die Verwaltung von Wörterverzeichnissen befindet sich jetzt auf der Seite 'Wörterverzeichnisse' im Abschnitt 'Assets' der Navigation.
    - In der vorherigen Version wurde die Funktionalität der Annotatorbenutzer in den Registerkarten 'Erwähnungen', 'Beziehungen' und 'Koreferenzen' im Abschnitt 'Dokumentannotation' der Navigation verteilt. Nun wird die Funktionalität auf der Seite 'Annotationstasks' im Abschnitt 'Modell für maschinelles Lernen' der Navigation zusammengeführt.
    - Um die Tasks der Annotatorbenutzer zu verwalten, gab es in der Vorgängerversion die Registerkarte 'Tasks' unter der Seite 'Assets' & Tools' > 'Dokumente'. Nun fügen Sie Tasks auf der Seite 'Annotationstasks' im Abschnitt 'Modell für maschinelles Lernen' der Navigation hinzu und verwalten dort Ihre Tasks.
    - In der Vorgängerversion waren die Seiten 'Regeln', 'Regex' und 'Wörterverzeichnisse' separate Seiten im Abschnitt 'Dokumentannotation' der Navigation. Nun wird die Funktionalität auf der Seite 'Regeln' im Abschnitt 'Regelbasiertes Modell' der Navigation zusammengeführt.

    Weitere Details zu den Navigationsänderungen finden Sie in Abbildung 1 und Tabelle 3.

![Screenshots der vorherigen Navigation (links) und der neuen Navigation (rechts).](images/nav3-0718.svg "Screenshots der vorherigen und neuen Navigation. Details zu den Änderungen werden in der Tabelle 3 und im vorhergehenden Text angezeigt.") Abbildung 1. Screenshots der vorherigen Navigation (links) und der neuen Navigation (rechts).

| Feature | Vorherige Position | Aktuelle Position |
|---------|--------------------------|----------------------|
| Annotationstasks | Assets & Tools > Dokumente > Tasks | Modell für maschinelles Lernen > Annotationstasks |
| Registerkarte 'Koreferenzen' | Dokumentannotation | Modell für maschinelles Lernen > Annotationstasks > Task > Annotationsgruppe > Dokument |
| Seite 'Wörterverzeichnisse' (Management) | Assets & Tools > Vorannotatoren > Wörterverzeichnisse verwalten | Assets |
| Registerkarte 'Wörterverzeichnisse' (Zuordnung zu Klassen für regelbasiertes Modell) | Dokumentannotation | Regelbasiertes Modell > Regeln |
| Seite 'Dokumente' | Assets & Tools | Assets |
| Seite 'Entitätstypen' | Assets & Tools | Assets |
| Registerkarte 'Erwähnungen' | Dokumentannotation | Modell für maschinelles Lernen > Annotationstasks > Task > Annotationsgruppe > Dokument |
| Seite 'Leistung' | Modellverwaltung | Modell für maschinelles Lernen |
| Seite 'Vorannotatoren' | Assets & Tools | Modell für maschinelles Lernen > Vorannotation |
| Registerkarte 'Regex' | Dokumentannotation | Regelbasiertes Modell > Regeln |
| Seite 'Beziehungstypen' | Assets & Tools | Assets |
| Registerkarte 'Beziehungen' | Dokumentannotation | Modell für maschinelles Lernen > Annotationstasks > Task > Annotationsgruppe > Dokument |
| Regeisterkarte 'Regeln' | Dokumentannotation | Regelbasiertes Modell |
| Registerkarte 'Tasks' | Assets & Tools > Dokumente | Modell für maschinelles Lernen > Annotationstasks |
| Seite 'Versionen' (Modell für maschinelles Lernen) | Modellverwaltung | Modell für maschinelles Lernen |
| Seite 'Versionen' (regelbasiertes Modell) | Modellverwaltung | Regelbasiertes Modell |
{: caption="Tabelle 3. Navigationsänderungen (Juli 2018)" caption-side="top"}

## Mai 2018
{: #may2018}

### Neue Features und Änderungen
{: #new-may2018}

- Ein Konfigurationsproblem, das dazu führte, dass die Serviceinstanzen in der Region 'Sydney' nicht in den USA (Süden) erscheinen, wurde behoben.
- Im Fenster 'Modell bereitstellen müssen Sie zum Anzeigen der Liste die Zugriffsmanagementmethode auswählen, die von Ihrer Serviceinstanz verwendet wird, wenn die Region, in der Sie die Implementierung ausführen, beide {{site.data.keyword.iamlong}}*Ressourcengruppen* und Cloud Foundry*-Bereiche* unterstützt. Weitere
Informationen zu Cloud Foundry und {{site.data.keyword.iamshort}} finden Sie unter [Ressourcengruppen und Zugriffsmanagement ![External link icon](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/blogs/bluemix/2017/12/resource-groups-access-management/){: new_window}.
- Die Datenerfassungseinstellung wurde auf der Seite 'Servicedetails' hinzugefügt. Weitere Informationen zur Datenerfassung finden Sie unter [Fehlerbehebung, Unterstützung und FAQs](/docs/services/watson-knowledge-studio/troubleshooting.html#content).
- Unterstützung für Chinesisch (traditionell) wurde hinzugefügt.
- Benutzer, die über die Administratorrolle verfügen, können nun die Anzahl der verwendeten Arbeitsbereiche anzeigen. Diese Informationen sind auf der Seite mit den Servicedetails verfügbar.
- {{site.data.keyword.alchemylanguagefull}} steht für die Implementierung von Modellen nicht mehr zur Verfügung. Informationen finden Sie unter [Zurückziehung des Service {{site.data.keyword.alchemyapishort}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/blogs/bluemix/2017/03/bye-bye-alchemyapi/){: new_window}.
- Wenn Sie jetzt einen Arbeitsbereich löschen, werden Sie aufgefordert, Ihre Aktion zu bestätigen. Wir hoffen, dass diese Bestätigung versehentliche Löschvorgänge vermeidet.
- Die Dokumentation enthält einige neue Details zum Datenschutz. Weitere Informationen finden Sie unter [Informationssicherheit](/docs/services/watson-knowledge-studio/information-security.html).

## April 2018
{: #april2018}

### Neue Features und Änderungen
{: #new-april2018}

- Der kostenlose {{site.data.keyword.knowledgestudioshort}}-Plan wurde durch den Lite-Plan ersetzt. Weitere Informationen finden Sie in [Go Lite with Watson {{site.data.keyword.knowledgestudioshort}}![External link icon](../../icons/launch-glyph.svg "Symbol für externen Link") ](https://www.ibm.com/blogs/bluemix/2018/04/go-lite-watson-knowledge-studio/){: new_window}.

## März 2018
{: #march2018}

### Neue Features und Änderungen
{: #new-march2018}

- Eine Seite **Bereitgestellte Modelle** ist verfügbar, auf der alle {{site.data.keyword.knowledgestudioshort}}-Modelle angezeigt werden, die für Services in den Bereichen bereitgestellt wurden, auf die Sie Zugriff haben. Um die Seite **Bereitgestellte Modelle** anzuzeigen, klicken Sie in der Menüleiste rechts oben im Menü **Einstellungen** auf **Bereitgestellte Modelle verwalten**. Informationen zum Aufheben der Bereitstellung und zum Anzeigen von Modellen auf der Seite **Bereitgestellte Modelle** finden Sie unter [Bereitstellung von Modellen für maschinelles Lernen aufheben](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) und [Bereitstellung von regelbasierten Modellen aufheben](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model).
- Eine französische Übersetzung der Benutzeroberfläche von {{site.data.keyword.knowledgestudioshort}} ist jetzt verfügbar.
- {{site.data.keyword.alchemylanguagefull}} ist nicht mehr als Vorannotator verfügbar. Anstelle von {{site.data.keyword.alchemylanguageshort}} können Sie Ihre Dokumente mithilfe von {{site.data.keyword.nlushort}} vorannotieren. Weitere Informationen hierzu finden Sie unter [Annotationsprozess beschleunigen](/docs/services/watson-knowledge-studio/preannotation.html).

## Dezember 2017
{: #december2017}

### Neue Features und Änderungen
{: #new-december2017}

- {{site.data.keyword.knowledgestudioshort}} wird in {{site.data.keyword.cloud_notm}} eingeführt. Informationen zum Zeitplan und zur Vorgehensweise für die Migration finden Sie unter [Migration auf {{site.data.keyword.cloud_notm}}](/docs/services/watson-knowledge-studio/client-migration.html).
- Neu gestaltete Navigation. Details zu den Änderungen bei der Navigation finden Sie in der [Tabelle 2](#september2017) der Releaseinformationen von September 2017.
- {{site.data.keyword.nlufull}} wurde als Vorannotator hinzugefügt.
- Einstellungen für die Benutzer- und Speicherverwaltung wurden auf der Seite 'Servicedetails' hinzugefügt. Informationen zum Hinzufügen von Benutzern finden Sie unter [Team zusammenstellen](/docs/services/watson-knowledge-studio/team.html). Informationen zum Festlegen von Speichergrenzwerten finden Sie unter [Fehlerbehebung > Probleme mit dem Speicherbereich](/docs/services/watson-knowledge-studio/troubleshooting.html#storage).
- Eine Seite 'Leistung' zum Auswerten der Modellqualität und mit Hinweisen zum Verbessern der Qualität des Modells wurde hinzugefügt.

## November 2017
{: #november2017}

### Änderungen
{: #new-november2017}

- Ein Problem mit einigen fehlenden Beziehungsannotationen im heruntergeladenen Korpus wurde behoben.
- Ein Problem beim Aufheben der Bereitstellung eines Modells mit dem Status **Ohne** wurde behoben.
- Ein Problem mit dem Fehlschlagen der Auswertung des Modells für Koreanisch wurde behoben.

## Oktober 2017
{: #october2017}

### Änderungen
{: #new-october2017}

- Das Problem, dass die Schaltfläche **Exportieren** im [experimentellen](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) Release von {{site.data.keyword.Bluemix_notm}} erst nach dem Aktualisieren des Browserfensters aktiviert wurde, wurde behoben.
- Die Schaltflächenbeschriftungen und QuickInfos im [experimentellen](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) Release von {{site.data.keyword.Bluemix_notm}} wurden an die geänderten Begriffe _Hochladen_ und _Herunterladen_ angepasst. Diese Begriffe werden im Zusammenhang mit Typsystemen, Dokumenten und Wörterverzeichnissen anstelle von _Importieren_ und _Exportieren_ verwendet.
- Die Verzögerung beim Aktualisieren der Beschreibungen auf der Seite 'Benutzerkontoverwaltung' für {{site.data.keyword.knowledgestudioshort}} im [experimentellen](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) Release von {{site.data.keyword.Bluemix_notm}} wurde behoben.
- Im Abschnitt für die Vorannotierung in der Benutzeroberfläche wurden Änderungen in der grafischen Benutzerschnittstelle vorgenommen, um die Funktionalität des Modells für maschinelles Lernen, des regelbasierten Modells, des Wörterverzeichnisses und von {{site.data.keyword.alchemylanguagefull}} zu verdeutlichen. Die Schaltflächenbeschriftung wurde von **Ausführen** in **Vorannotieren** geändert, der Fenstertitel wurde von **Annotator ausführen** in **Vorannotierung ausführen** geändert und die Fehlernachricht wurde angepasst, um deutlich zu machen, dass nach dem Hinzufügen von Annotationen durch Annotatorbenutzer keine automatisch erstellten Annotationen mehr hinzugefügt werden können.
- Für Projekte oder Arbeitsbereiche, die wörterverzeichnisbasierte Tokenizer verwenden, wurde das Problem behoben, dass beim Importieren von Dokumenten ohne Ground Truth leere Sätze angezeigt wurden.

## September 2017
{: #september2017}

### Neue Features und Änderungen
{: #new-sept17}

- Eine neue Front-End-Benutzerfunktionalität für {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.Bluemix}} wurde als [experimenteller](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) Service freigegeben. Zu den Änderungen gehören die überarbeitete Navigation und eine neue Seite für die Analyse der Modellleistung. Eine Zusammenfassung der Navigationsänderungen finden Sie in der Tabelle mit den bekannten Problemen.
- Sprachunterstützung für vereinfachtes Chinesisch und Niederländisch wurde hinzugefügt.

### Bekannte Probleme
{: #issues-sept17}

- Nach dem Zuordnen von Klassen und Entitätstypen in einem regelbasierten Modell wird die Schaltfläche **Exportieren** erst nach dem Aktualisieren des Browserfensters aktiviert.
- Im [experimentellen](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) Release von {{site.data.keyword.Bluemix_notm}} stimmt die Terminologie in der Dokumentation nicht vollständig mit der neuen Benutzeroberfläche überein. Die Dokumentation entspricht der Benutzeroberfläche in {{site.data.keyword.IBM_notm}} Marketplace. Im [experimentellen](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) Release wurden die folgenden Begriffe geändert:

| Begriff in {{site.data.keyword.IBM_notm}} Marketplace | Begriff in {{site.data.keyword.Bluemix_notm}} | Hinweise |
|----------|----------|----------|
| _Projekt_ | _Arbeitsbereich_ | Dieser Begriff wurde geändert, weil der Begriff _Projekt_ auch in {{site.data.keyword.Bluemix_notm}} verwendet wird. |
| _importieren_ und _exportieren_ | _hochladen_ und _herunterladen_ | Für die Begriffe _importieren_ und _exportieren_ wird jetzt im Zusammenhang mit Dokumenten und Entitätstypen _hochladen_ und _herunterladen_ verwendet. Der Begriff _exportieren_ wird für das Exportieren eines Modells in Anwendungen wie {{site.data.keyword.watson}} Explorer weiterhin verwendet. |
{: caption="Tabelle 1. Terminologieänderungen für die {{site.data.keyword.Bluemix_notm}}-Version" caption-side="top"}

- Im [experimentellen](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) Release für {{site.data.keyword.Bluemix_notm}} stimmen manche Aufgabenschritte in der Dokumentation nicht mit der neuen Benutzeroberfläche überein. Die Dokumentation entspricht der Benutzeroberfläche in {{site.data.keyword.IBM_notm}} Marketplace. In der folgenden Tabelle sind die Navigationsänderungen für das [experimentelle](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) Release zusammengefasst:

| Feature | Position in {{site.data.keyword.IBM_notm}} Marketplace | Position in {{site.data.keyword.Bluemix_notm}}
|----------|----------|----------|
|Registerkarte 'Annotatorkomponente' | Hauptnavigationsbereich | Nicht mehr vorhanden |
|Tabelle 'Fehlermatrix' (aus der Registerkarte 'Statistik') | Annotatorkomponente > Details | Modellverwaltung > Leistung > Link 'Detaillierte Statistik' |
|Registerkarte 'Wörterverzeichnisse' | Hauptnavigationsbereich | Assets & Tools > Vorannotatoren |
|Seite 'Wörterverzeichniszuordnung' | Annotatorkomponente | Assets & Tools > Vorannotatoren |
|Registerkarte 'Entitätstypen' | Typsystem | Assets & Tools > Entitätstypen |
|Ground Truth-Editor | Annotatorbenutzertasks | Registerkarte 'Dokumentannotation' |
|Registerkarte 'Einstellungen für Ground Truth-Editor' | Annotatorbenutzertasks | Einstellungen > Einstellungen für Dokumentannotation |
|Modelle ausführen und exportieren | Annotatorkomponente | Modellverwaltung > Versionen |
|Regeisterkarte 'Regeln' | Hauptnavigationsbereich | Dokumentannotation > Regeln |
|Registerkarte 'Statistik' | Annotatorkomponente > Details | Modellverwaltung > Leistung |
|Tabelle 'Zusammenfassung' (aus der Registerkarte 'Statistik') | Annotatorkomponente > Details | Modellverwaltung > Leistung > Link 'Detaillierte Statistik' |
|Registerkarte 'Typzuordnung' (für regelbasiertes Modell) | Annotatorkomponente > Details | Modellverwaltung > Versionen > Typzuordnung für regelbasiertes Modell |
{: caption="Tabelle 2. Navigationsänderungen für die {{site.data.keyword.Bluemix_notm}}-Version" caption-side="top"}

## Juli 2017
{: #july2017}

- Behobenes Problem: In einigen Fällen wurde der Header nicht mehr angezeigt
- Sicherheitsupdates für Infrastrukturkomponenten wurden angewendet

## Juni 2017
{: #june2017}

- Die Stabilität der Verarbeitung umfangreicher Daten unter bestimmten Bedingungen wurde verbessert
- Ein Problem im Zusammenhang mit einem Beurteilungsfehler wurde behoben

## Mai 2017
{: #may2017}

- Die Möglichkeit zum Umbenennen verschiedener Objekte wie Projekte, Dokumentgruppen usw. wurde hinzugefügt
- Die Möglichkeit zum Bereitstellen von NLU-Modellen in bestimmten {{site.data.keyword.Bluemix}}-Regionen wurde hinzugefügt
- Die Verarbeitungsleistung beim Anzeigen einer umfangreichen Tabelle für IAA wurde verbessert
- Kleine Fehler wurden behoben
- Sicherheitskorrekturen wurden angewendet

## April 2017
{: #april2017}

- Verbesserte Stabilität für {{site.data.keyword.knowledgestudioshort}} Premium
- Verwendungsanalyse für Geschäftsmetriken wurde hinzugefügt

## Releases vor April 2017

Siehe [{{site.data.keyword.IBM_notm}} Technote #1986001 ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://www.ibm.com/support/docview.wss?uid=swg21986001){: new_window}.
