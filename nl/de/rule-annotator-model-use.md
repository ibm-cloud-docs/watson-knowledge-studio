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

## Regelbasiertes Modell in AlchemyLanguage bereitstellen
{: #wks_rule_bluemix}

Mit dieser Funktion können Ihre Anwendungen das bereitgestellte regelbasierte Modell verwenden, um Entitäten in Dokumenten in Ihrem Fachgebiet zu suchen und zu extrahieren.

**Achtung**: Dies ist gegenwärtig eine [experimentelle](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) Funktion des Service.

### Vorbereitungen

Für die Verwendung dieses angepassten Modells müssen Sie über den erweiterten Plan für den Service {{site.data.keyword.alchemylanguageshort}} verfügen.

### Informationen zu diesem Vorgang

Für die Bereitstellung in diesem Service benötigen Sie einen Zugriffsschlüssel von {{site.data.keyword.IBM_notm}} {{site.data.keyword.alchemylanguageshort}}.

Der Schlüssel muss mit einem Konto verknüpft sein, das zum Publizieren angepasster Modelle berechtigt ist. Andernfalls wird das Modell zwar erfolgreich bereitgestellt, aber Sie können es nicht verwenden.

Beim Bereitstellen des regelbasierten Modells wählen Sie aus, welche Version des Modells bereitgestellt werden soll. Den Schlüssel müssen Sie angeben, wenn Sie zum ersten Mal ein Modell in {{site.data.keyword.alchemylanguageshort}} bereitstellen. Anschließend können Sie den Schlüssel für mehrere Versionen des Modells wiederverwenden, die Sie bereitstellen. Für jeden Schlüssel gilt eine Obergrenze für die Anzahl der Modelle, die gleichzeitig bereitgestellt werden können.

### Vorgehensweise

So stellen Sie ein regelbasiertes Modell in {{site.data.keyword.alchemylanguageshort}} bereit:

1. Melden Sie sich als {{site.data.keyword.knowledgestudioshort}}-Administrator oder -Projektleiter an und wählen Sie Ihren Arbeitsbereich aus.
1. Wählen Sie die Registerkarte **Modellverwaltung** > **Versionen** > **Regelbasiert** aus.
1. Wählen Sie die Version des Modells aus, das Sie bereitstellen möchten.

    Wenn nur eine funktionsfähige Version des Modells vorhanden ist, speichern Sie das aktuelle Modell für die Bereitstellung, indem Sie auf **Zum Bereitstellen speichern** klicken. Nach dem Klicken auf **Zum Bereitstellen speichern** wird eine Version des Modells erstellt, d. h. Sie können eine Modellversion bereitstellen, und trotzdem fortfahren, die aktuelle Version zu verbessern. Das Speichern der Version kann mehrere Minuten dauern. Die Option zum Bereitstellen wird erst angezeigt, nachdem die Version erstellt wurde.

1. Klicken Sie auf **Bereitstellen**, wählen Sie {{site.data.keyword.alchemylanguageshort}} als Ziel für die Bereitstellung aus und klicken Sie anschließend auf **Weiter**.
1. Geben Sie entweder den Schlüssel ein, den Sie von {{site.data.keyword.alchemylanguageshort}} erhalten haben, oder wählen Sie eine zuvor bereitgestellte Version des Modells aus, deren Schlüssel Sie wiederverwenden möchten, und klicken Sie auf **Bereitstellen**. Wenn der Schlüssel gültig ist, wird eine Bestätigung angezeigt, in der die Modell-ID enthalten ist. Diese Bestätigung bedeutet nicht, dass das Modell für die Verwendung durch Ihre Anwendungen bereit ist.
1. Der Bereitstellungsprozess kann mehrere Minuten dauern. Um den Status der Bereitstellung zu prüfen, klicken Sie auf **Status** neben der Version, die Sie implementiert haben. Wenn die Bereitstellung des Modells noch nicht abgeschlossen ist, wird der Status 'Publizieren läuft' angezeigt. Wenn die Bereitstellung erfolgreich abgeschlossen ist, wird der Status in 'Verfügbar' geändert. Wenn Probleme aufgetreten sind, wird der Status 'Fehler' angezeigt.

    Die Statusinformationen beinhalten die Modell-ID, die letzten vier Stellen des {{site.data.keyword.alchemyapishort}}-Schlüssels und ein Protokoll für den Bereitstellungsprozess. Über die Modell-ID (model_id) rufen Ihre Anwendungen das Modell für maschinelles Lernen auf. Notieren Sie diese Modell-ID, da es im Programm keine weitere Möglichkeit gibt, diese ID aufzurufen. Anhand des {{site.data.keyword.alchemyapishort}}-Schlüssels können Sie die Anzahl der Bereitstellungen pro Schlüssel überwachen.

### Nächste Schritte

Um das bereitgestellte Modell zu verwenden, müssen Sie die Modell-ID kopieren und in den API-Aufruf Ihrer Anwendung einfügen.

> **Achtung:** Der Aufruf `GET /info/models` der {{site.data.keyword.alchemylanguageshort}}-API kann nicht verwendet werden, um die Modell-IDs von regelbasierten Modellen im Programmcode abzurufen. Mit diesem API-Aufruf können Sie die Modell-IDs von Modellen für maschinelles Lernen abrufen, jedoch nicht die Modell-IDs von regelbasierten Modellen.

In dem Aufruf muss außerdem der {{site.data.keyword.alchemylanguageshort}}-Service angegeben werden, den Sie mit dem Modell verwenden möchten, und Ihr Zugriffsschlüssel für {{site.data.keyword.alchemyapishort}}.

Der folgende Endpunkt wird unterstützt:

- **&lt;*input-type*&gt;GetRankedNamedEntities**

    Verwendet das angepasste Modell, das Sie im Modellparameter angeben, um eine Liste der Erwähnungen aller bekannten Entitätstypen zu extrahieren, die in den von Ihnen bereitgestellten Eingabedaten gefunden werden. Zu den unterstützten Eingabetypen gehören Text, HTML oder eine öffentliche URL. Weitere Informationen zu der API und der zu verwendenden Syntax finden Sie unter [{{site.data.keyword.alchemylanguageshort}}&gt;Entitäten ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/smarterplanet/us/en/ibmwatson/developercloud/alchemy-language/api/v1/#entities){: new_window}.

## Regelbasiertes Modell in IBM Watson Discovery bereitstellen
{: #wks_rule_discovery}

Stellen Sie ein Modell bereit, damit eine Anwendung, die den {{site.data.keyword.discoveryshort}}-Service verwendet, das regelbasierte Modell verwenden kann, um während der Dokumentaufbereitung Entitäten zu finden und zu extrahieren.

**Achtung**: Dies ist gegenwärtig eine [experimentelle](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) Funktion des Service.

### Vorbereitungen

Sie benötigen Administratorzugriff auf eine Instanz des {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}-Service sowie die Namen des zugeordneten {{site.data.keyword.Bluemix_notm}}-Bereichs und der Instanz.

### Vorgehensweise

Führen Sie die folgenden Schritte aus, um ein regelbasiertes Modell in {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}} bereitzustellen:

1. Melden Sie sich als {{site.data.keyword.knowledgestudioshort}}-Administrator oder -Projektleiter an und wählen Sie Ihren Arbeitsbereich aus.
1. Wählen Sie die Registerkarte **Modellverwaltung** > **Versionen** > **Regelbasiert** aus.
1. Wählen Sie die Version des Modells aus, das Sie bereitstellen möchten.

    Wenn nur eine einzige funktionsfähige Version des Modells vorhanden ist, speichern Sie das aktuelle Modell für die Bereitstellung, indem Sie auf **Zum Bereitstellen speichern** klicken. Dadurch wird das Modell versioniert, d. h. Sie können eine Modellversion bereitstellen und trotzdem fortfahren, die aktuelle Version zu verbessern. Das Speichern der Version kann mehrere Minuten dauern. Die Option zum Bereitstellen wird erst angezeigt, nachdem die Version erstellt wurde.

1. Klicken Sie auf **Bereitstellen**, wählen Sie {{site.data.keyword.discoveryshort}} als Ziel für die Bereitstellung aus und klicken Sie anschließend auf **Weiter**.
1. Geben Sie den {{site.data.keyword.Bluemix_notm}}-Bereich und die Instanz an. Wählen Sie eine andere Region aus, falls nötig.
1. Klicken Sie auf **Bereitstellen**.
1. Der Bereitstellungsprozess kann mehrere Minuten dauern. Um den Status der Bereitstellung zu prüfen, klicken Sie auf **Status** in der Registerkarte **Versionen** neben der von Ihnen bereitgestellten Version.

    Wenn die Bereitstellung des Modells noch nicht abgeschlossen ist, wird der Status 'Publizieren läuft' angezeigt. Wenn die Bereitstellung erfolgreich abgeschlossen ist, wird der Status in 'Verfügbar' geändert. Wenn Probleme aufgetreten sind, wird der Status 'Fehler' angezeigt.

    Notieren Sie die Modell-ID (model_id), sobald sie angezeigt wird. Sie geben diese ID später im {{site.data.keyword.discoveryshort}}-Service an, damit der Service Ihr angepasstes Modell verwenden kann.

### Nächste Schritte

Damit das bereitgestellte Modell verwendet werden kann, müssen Sie die Modell-ID nach entsprechender Aufforderung beim Konfigurationsprozess für die Aufbereitung des {{site.data.keyword.discoveryshort}}-Service angeben.

## Regelbasiertes Modell in IBM Watson Natural Language Understanding bereitstellen
{: #wks_rule_nlu}

Stellen Sie das regelbasierte Modell bereit, damit eine Anwendung, die den {{site.data.keyword.nlushort}}-Service verwendet, das Modell verwenden kann, um Entitäten zu finden und zu extrahieren, die für Ihr Fachgebiet relevant sind.

**Achtung**: Dies ist gegenwärtig eine [experimentelle](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) Funktion des Service.

### Vorbereitungen

Sie benötigen Verwaltungszugriff auf eine Instanz des {{site.data.keyword.nlushort}}-Service sowie die Namen des zugeordneten {{site.data.keyword.Bluemix_notm}}-Bereichs und der Instanz.

### Vorgehensweise

Führen Sie die folgenden Schritte aus, um ein regelbasiertes Modell in {{site.data.keyword.nlushort}} bereitzustellen:

1. Melden Sie sich als {{site.data.keyword.knowledgestudioshort}}-Administrator oder -Projektleiter an und wählen Sie Ihren Arbeitsbereich aus.
1. Wählen Sie die Registerkarte **Modellverwaltung** > **Versionen** > **Regelbasiert** aus.
1. Wählen Sie die Version des Modells aus, das Sie bereitstellen möchten.

    Wenn nur eine einzige funktionsfähige Version des Modells vorhanden ist, speichern Sie das aktuelle Modell für die Bereitstellung, indem Sie auf **Zum Bereitstellen speichern** klicken. Dadurch wird das Modell versioniert, d. h. Sie können eine Modellversion bereitstellen und trotzdem fortfahren, die aktuelle Version zu verbessern. Das Speichern der Version kann mehrere Minuten dauern. Die Option zum Bereitstellen wird erst angezeigt, nachdem die Version erstellt wurde.

1. Klicken Sie auf **Bereitstellen**, wählen Sie {{site.data.keyword.nlushort}} als Ziel für die Bereitstellung aus und klicken Sie anschließend auf **Weiter**.
1. Geben Sie den {{site.data.keyword.Bluemix_notm}}-Bereich und die Instanz an. Wählen Sie eine andere Region aus, falls nötig.
1. Klicken Sie auf **Bereitstellen**.
1. Der Bereitstellungsprozess kann mehrere Minuten dauern. Um den Status der Bereitstellung zu prüfen, klicken Sie auf **Status** in der Registerkarte **Versionen** neben der von Ihnen bereitgestellten Version.

    Wenn die Bereitstellung des Modells noch nicht abgeschlossen ist, wird der Status 'Publizieren läuft' angezeigt. Wenn die Bereitstellung erfolgreich abgeschlossen ist, wird der Status in 'Verfügbar' geändert. Wenn Probleme aufgetreten sind, wird der Status 'Fehler' angezeigt.

    Notieren Sie die Modell-ID (model_id), sobald sie angezeigt wird. Sie geben diese ID später im {{site.data.keyword.nlushort}}-Service an, damit der Service Ihr angepasstes Modell verwenden kann.

### Nächste Schritte

Damit das bereitgestellte Modell verwendet wird, müssen Sie die Modell-ID Ihres angepassten Modells im Parameter `entities.model` angeben.

Sie können das Modell mit der Anforderung {{site.data.keyword.nlushort}} `GET /analyze` verwenden, um Entitäten zu extrahieren.

Details hierzu finden Sie in der [Dokumentation für {{site.data.keyword.nlushort}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/watson/developercloud/doc/natural-language-understanding/index.html){: new_window}.

## Bereitstellung von Modellen aufheben
{: #undeploy-view-model}

Wenn Sie die Bereitstellung eines Modells aufheben oder ein Modell-ID abrufen möchten, öffnen Sie die Seite **Bereitgestellte Modelle**. Auf der Seite **Bereitgestellte Modelle** werden alle {{site.data.keyword.knowledgestudioshort}}-Modelle aufgelistet, die für Services in den Bereichen bereitgestellt wurden, auf die Sie Zugriff haben.

So können Sie die Bereitstellung eines Modells aufheben oder Modell-IDs finden:

1. Melden Sie sich als {{site.data.keyword.knowledgestudioshort}}-Administrator oder -Projektleiter an und wählen Sie Ihren Arbeitsbereich aus.
1. Wählen Sie im Menü **Einstellungen** in der rechten oberen Menüleiste die Option **Bereitgestellte Modelle verwalten** aus.
1. Suchen Sie in der Liste der bereitgestellten Modelle das Modell, das Sie anzeigen oder dessen Bereitstellung Sie aufheben möchten.
1. Um die Bereitstellung des Modells aufzuheben, klicken Sie in der letzten Spalte der betreffenden Zeile auf **Modellbereitstellung aufheben**.
1. Die Modell-ID finden Sie in der Spalte **Modell-ID**.

## Regelbasiertes Modell in IBM Watson Explorer wiederverwenden
{: #wks_rule_export}

Exportieren Sie die PEAR-Datei, die beim Erstellen des regelbasierten Modells generiert wird, damit sie in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer verwendet werden kann.

### Vorgehensweise

Führen Sie die folgenden Schritte aus, um ein regelbasiertes Modell in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer wiederzuverwenden:

1. Melden Sie sich als {{site.data.keyword.knowledgestudioshort}}-Administrator oder -Projektleiter an und wählen Sie Ihren Arbeitsbereich aus.
1. Wählen Sie die Registerkarte **Modellverwaltung** > **Versionen** > **Regelbasiert** aus.
1. Klicken Sie auf **Aktuelles Modell exportieren**.

    Wenn Sie einen kostenfreien Plan abonniert haben, ist keine Exportoption verfügbar.

    Das Modell wird als PEAR-Datei gespeichert und Sie werden aufgefordert, die Datei herunterzuladen. Eine PEAR-Datei (Processing Engine ARchive) ist das UIMA-Standardpaketformat für UIMA-Komponenten. Das Modell wird im PEAR-Format gespeichert, damit es in UIMA-Anwendungen verteilt und wiederverwendet werden kann.

1. Laden Sie die Datei in Ihr lokales System herunter.
1. Importieren Sie die PEAR-Datei mit der {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer-Anwendung.
