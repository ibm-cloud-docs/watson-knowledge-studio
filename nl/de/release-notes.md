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

Diese Dokumentation bezieht sich auf {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Die Dokumentation für die Vorgängerversion {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace kann über [diesen Link ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/docs/services/knowledge-studio/release-notes.html){: new_window} aufgerufen werden.
{: tip}

# Releaseinformationen
{: #release-notes}

Die folgenden neuen Features und Änderungen für {{site.data.keyword.knowledgestudiofull}} sind verfügbar.
{: shortdesc}

## März 2018
{: #march2018}

### Neue Features und Änderungen
{: #new-march2018}

- Ein Seite **Bereitgestellte Modelle** ist verfügbar, auf der alle {{site.data.keyword.knowledgestudioshort}}-Modelle angezeigt werden, die für Services in den Bereichen bereitgestellt wurden, auf die Sie Zugriff haben. Um die Seite **Bereitgestellte Modelle** anzuzeigen, klicken Sie in der Menüleiste rechts oben im Menü **Einstellungen** auf **Bereitgestellte Modelle verwalten**. Informationen zum Aufheben der Bereitstellung und zum Anzeigen von Modellen auf der Seite **Bereitgestellte Modelle** finden Sie unter [Bereitstellung von Modellen für maschinelles Lernen aufheben](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) und [Bereitstellung von regelbasierten Modellen aufheben](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model).
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
