---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-14"

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

Diese Dokumentation bezieht sich auf {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Die Dokumentation für die Vorgängerversion {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace kann über [diesen Link ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/docs/services/knowledge-studio/rule-annotator-model-use.html){: new_window} aufgerufen werden.
{: tip}

# Regelbasiertes Modell verwenden
{: #wks_rule_publish}

Nutzen Sie ein regelbasiertes Modell, das Sie mit {{site.data.keyword.knowledgestudioshort}} erstellt haben, wiederholt, indem Sie es für andere {{site.data.keyword.watson}}-Anwendungen verfügbar machen.
{: shortdesc}

**Achtung**: Das Bereitstellen eines regelbasierten Modells für die Verwendung in diesen Services ist eine [experimentelle](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) Funktion.

Damit ein Modell für die Verwendung durch einen Service bereitgestellt werden kann, müssen Sie über ein Abonnement für den betreffenden Service verfügen. {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}}-Services werden in {{site.data.keyword.Bluemix_notm}}, der Cloudplattform für {{site.data.keyword.IBM_notm}}, gehostet. Weitere Informationen zur Plattform finden Sie unter [Was ist {{site.data.keyword.Bluemix_notm}}? ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.ng.bluemix.net/docs/overview/whatisbluemix.html){: new_window}. Um einen der {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}}-Services zu abonnieren, erstellen Sie ein Konto über die [{{site.data.keyword.Bluemix_notm}}-Website ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.ng.bluemix.net/){: new_window}.

Für einige der Services müssen Sie Details der Serviceinstanz kennen, in der die Bereitstellung erfolgen soll (z. B. den Namen des {{site.data.keyword.Bluemix_notm}}-Bereichs und den Namen der Serviceinstanz). Der Bereichsname und der Instanzname sind auf der Seite für {{site.data.keyword.Bluemix_notm}}-Services verfügbar.

Sie können mit dem regelbasierten Modell auch neue Dokumente vorannotieren. Details hierzu finden Sie unter [Dokumente mit dem regelbasierten Model vorannotieren](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotrule).

## Regelbasiertes Modell in IBM Watson Discovery bereitstellen
{: #wks_rule_discovery}

Stellen Sie ein Modell bereit, damit eine Anwendung, die den {{site.data.keyword.discoveryshort}}-Service verwendet, das regelbasierte Modell verwenden kann, um während der Dokumentaufbereitung Entitäten zu finden und zu extrahieren.

**Achtung**: Dies ist gegenwärtig eine [experimentelle](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) Funktion des Service.

### Vorbereitungen
{: #wks_rule_discovery_prereqs}

Sie benötigen Administratorzugriff auf eine Instanz des {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}-Service sowie die Namen des zugeordneten {{site.data.keyword.Bluemix_notm}}-Bereichs und der Instanz.

### Vorgehensweise
{: #wks_rule_discovery_procedure}

Führen Sie die folgenden Schritte aus, um ein regelbasiertes Modell in {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}} bereitzustellen:

1. Melden Sie sich als {{site.data.keyword.knowledgestudioshort}}-Administrator oder -Projektleiter an und wählen Sie Ihren Arbeitsbereich aus.
1. Wählen Sie die Registerkarte **Regelbasiertes Modell** > **Versionen** > **Regelbasiertes Modell** aus.
1. Wählen Sie die Version des Modells aus, das Sie bereitstellen möchten.

    Wenn nur eine einzige funktionsfähige Version des Modells vorhanden ist, speichern Sie das aktuelle Modell für die Bereitstellung, indem Sie auf **Zum Bereitstellen speichern** klicken. Dadurch wird das Modell versioniert, d. h. Sie können eine Modellversion bereitstellen und trotzdem fortfahren, die aktuelle Version zu verbessern. Das Speichern der Version kann mehrere Minuten dauern. Die Option zum Bereitstellen wird erst angezeigt, nachdem die Version erstellt wurde.

    **Hinweis**: Jede Version kann nur für eine Serviceinstanz implementiert werden. Wenn Sie dasselbe Modell in mehreren Instanzen implementieren möchten, müssen Sie für jede Instanz eine Version erstellen.

1. Klicken Sie auf **Bereitstellen**, wählen Sie {{site.data.keyword.discoveryshort}} als Ziel für die Bereitstellung aus und klicken Sie anschließend auf **Weiter**.
1. Geben Sie den {{site.data.keyword.Bluemix_notm}}-Bereich und die Instanz an. Wählen Sie eine andere Region aus, falls nötig.
1. Klicken Sie auf **Bereitstellen**.
1. Der Bereitstellungsprozess kann mehrere Minuten dauern. Um den Status der Bereitstellung zu prüfen, klicken Sie auf **Status** in der Registerkarte **Versionen** neben der von Ihnen bereitgestellten Version.

    Wenn die Bereitstellung des Modells noch nicht abgeschlossen ist, wird der Status 'Publizieren läuft' angezeigt. Wenn die Bereitstellung erfolgreich abgeschlossen ist, wird der Status in 'Verfügbar' geändert. Wenn Probleme aufgetreten sind, wird der Status 'Fehler' angezeigt.

    Notieren Sie die Modell-ID (model_id), sobald sie angezeigt wird. Sie geben diese ID später im {{site.data.keyword.discoveryshort}}-Service an, damit der Service Ihr angepasstes Modell verwenden kann.

### Nächste Schritte
{: #wks_rule_discovery_next}

Damit das bereitgestellte Modell verwendet werden kann, müssen Sie die Modell-ID nach entsprechender Aufforderung beim Konfigurationsprozess für die Aufbereitung des {{site.data.keyword.discoveryshort}}-Service angeben.

## Regelbasiertes Modell in IBM Watson Natural Language Understanding bereitstellen
{: #wks_rule_nlu}

Stellen Sie das regelbasierte Modell bereit, damit eine Anwendung, die den {{site.data.keyword.nlushort}}-Service verwendet, das Modell verwenden kann, um Entitäten zu finden und zu extrahieren, die für Ihr Fachgebiet relevant sind.

**Achtung**: Dies ist gegenwärtig eine [experimentelle](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) Funktion des Service.

### Vorbereitungen
{: #wks_rule_prereqs}

Sie benötigen Administratorzugriff auf eine Instanz des {{site.data.keyword.nlushort}}-Service sowie die Namen des zugeordneten {{site.data.keyword.Bluemix_notm}}-Bereichs und der Instanz.

### Vorgehensweise
{: #wks_rule_procedure}

Führen Sie die folgenden Schritte aus, um ein regelbasiertes Modell in {{site.data.keyword.nlushort}} bereitzustellen:

1. Melden Sie sich als {{site.data.keyword.knowledgestudioshort}}-Administrator oder -Projektleiter an und wählen Sie Ihren Arbeitsbereich aus.
1. Wählen Sie die Registerkarte **Regelbasiertes Modell** > **Versionen** > **Regelbasiertes Modell** aus.
1. Wählen Sie die Version des Modells aus, das Sie bereitstellen möchten.

    Wenn nur eine einzige funktionsfähige Version des Modells vorhanden ist, speichern Sie das aktuelle Modell für die Bereitstellung, indem Sie auf **Zum Bereitstellen speichern** klicken. Dadurch wird das Modell versioniert, d. h. Sie können eine Modellversion bereitstellen und trotzdem fortfahren, die aktuelle Version zu verbessern. Das Speichern der Version kann mehrere Minuten dauern. Die Option zum Bereitstellen wird erst angezeigt, nachdem die Version erstellt wurde.

    **Hinweis**: Jede Version kann nur für eine Serviceinstanz implementiert werden. Wenn Sie dasselbe Modell in mehreren Instanzen implementieren möchten, müssen Sie für jede Instanz eine Version erstellen.

1. Klicken Sie auf **Bereitstellen**, wählen Sie {{site.data.keyword.nlushort}} als Ziel für die Bereitstellung aus und klicken Sie anschließend auf **Weiter**.
1. Geben Sie den {{site.data.keyword.Bluemix_notm}}-Bereich und die Instanz an. Wählen Sie eine andere Region aus, falls nötig.
1. Klicken Sie auf **Bereitstellen**.
1. Der Bereitstellungsprozess kann mehrere Minuten dauern. Um den Status der Bereitstellung zu prüfen, klicken Sie auf **Status** in der Registerkarte **Versionen** neben der von Ihnen bereitgestellten Version.

    Wenn die Bereitstellung des Modells noch nicht abgeschlossen ist, wird der Status 'Publizieren läuft' angezeigt. Wenn die Bereitstellung erfolgreich abgeschlossen ist, wird der Status in 'Verfügbar' geändert. Wenn Probleme aufgetreten sind, wird der Status 'Fehler' angezeigt.

    Notieren Sie die Modell-ID (model_id), sobald sie angezeigt wird. Sie geben diese ID später im {{site.data.keyword.nlushort}}-Service an, damit der Service Ihr angepasstes Modell verwenden kann.

### Nächste Schritte
{: #wks_rule_next}

Damit das bereitgestellte Modell verwendet wird, müssen Sie die Modell-ID Ihres angepassten Modells im Parameter `entities.model` angeben.

Sie können das Modell mit der Anforderung {{site.data.keyword.nlushort}} `GET /analyze` verwenden, um Entitäten zu extrahieren.

Details hierzu finden Sie in der [Dokumentation für {{site.data.keyword.nlushort}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/docs/services/natural-language-understanding/index.html){: new_window}.

## Bereitstellung von Modellen aufheben
{: #undeploy-view-model}

Wenn Sie die Bereitstellung eines Modells aufheben oder ein Modell-ID abrufen möchten, öffnen Sie die Seite **Bereitgestellte Modelle**.

### Informationen zu diesem Vorgang
{: #wks_undeploy_about}

Was Sie auf der Seite 'Bereitgestellte Modelle' sehen, hängt von der [-Region ![External link icon](../../icons/launch-glyph.svg "Symbol für externen Link") ](https://console.bluemix.net/docs/resources/services_region.html){: new_window} ab, in der Ihre {{site.data.keyword.knowledgestudioshort}}-Instanz gehostet wird. Wenn die Region Instanzen unterstützt, die von [IAM ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/docs/iam/users_roles.html){: new_window}- und [Cloud Foundry ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/docs/iam/cfaccess.html){: new_window}-Zugriffsmanagementmethoden unterstützt werden, werden für jede Methode eine Registerkarte angezeigt. Modelle aus Instanzen, die von IAM verwaltet werden, werden auf der Registerkarte **Ressourcengruppen** aufgelistet. Modelle aus Instanzen, die von Cloud verwaltet werden, werden auf der Registerkarte **Organisationen** aufgelistet. 

Wenn die Region Instanzen unterstützt, die nur von einer der beiden Zugriffsmanagementmethoden verwaltet wird, wird nur eine Liste mit Modellen angezeigt, da nur eine einzige Zugriffsverwaltungsmethode anwendbar ist.

### Vorgehensweise
{: #wks_deploy_procedure}

So können Sie die Bereitstellung eines Modells aufheben oder Modell-IDs finden:

1. Starten Sie {{site.data.keyword.knowledgestudioshort}}.
1. Wählen Sie im Menü **Einstellungen** in der rechten oberen Menüleiste die Option **Bereitgestellte Modelle verwalten** aus.
1. Suchen Sie in der Liste der bereitgestellten Modelle das Modell, das Sie anzeigen oder dessen Bereitstellung Sie aufheben möchten.
1. Um die Bereitstellung des Modells aufzuheben, klicken Sie in der letzten Spalte der betreffenden Zeile auf **Modellbereitstellung aufheben**.
1. Die Modell-ID finden Sie in der Spalte **Modell-ID**.

Alternativ können Sie die Bereitstellung der Modelle aus der Seite 'Versionen' für regelbasierte Modelle und Modelle für maschinelles Lernen zurücknehmen.

## Regelbasiertes Modell in IBM Watson Explorer wiederverwenden
{: #wks_rule_export}

Exportieren Sie die PEAR-Datei, die beim Erstellen des regelbasierten Modells generiert wird, damit sie in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer verwendet werden kann.

### Vorgehensweise
{: #wks_rule_export_procedure}

Führen Sie die folgenden Schritte aus, um ein regelbasiertes Modell in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer wiederzuverwenden:

1. Melden Sie sich als {{site.data.keyword.knowledgestudioshort}}-Administrator oder -Projektleiter an und wählen Sie Ihren Arbeitsbereich aus.
1. Wählen Sie die Registerkarte **Regelbasiertes Modell** > **Versionen** > **Regelbasiertes Modell** aus.
1. Klicken Sie auf **Aktuelles Modell exportieren**.

    Wenn Sie einen Lite-Plan abonniert haben, ist keine Exportoption verfügbar.

    Das Modell wird als PEAR-Datei gespeichert und Sie werden aufgefordert, die Datei herunterzuladen. Eine PEAR-Datei (Processing Engine ARchive) ist das UIMA-Standardpaketformat für UIMA-Komponenten. Das Modell wird im PEAR-Format gespeichert, damit es in UIMA-Anwendungen verteilt und wiederverwendet werden kann.

1. Laden Sie die Datei in Ihr lokales System herunter.
1. Importieren Sie die PEAR-Datei mit der {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer-Anwendung.
