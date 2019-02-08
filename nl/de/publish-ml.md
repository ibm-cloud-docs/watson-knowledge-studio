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

Diese Dokumentation bezieht sich auf {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Die Dokumentation für die Vorgängerversion {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace kann über [diesen Link ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/docs/services/knowledge-studio/publish-ml.html){: new_window} aufgerufen werden.
{: tip}

# Modell für maschinelles Lernen verwenden
{: #publish-ml}

Nutzen Sie ein Modell für maschinelles Lernen, das Sie mit {{site.data.keyword.knowledgestudioshort}} trainiert haben, wiederholt, indem Sie es für andere {{site.data.keyword.watson}}-Anwendungen verfügbar machen.
{: shortdesc}

Ein Modell für maschinelles Lernen kann bereitgestellt oder exportiert werden. Ein wörterverzeichnisbasierter Vorannotator oder {{site.data.keyword.nlushort}}-Vorannotator kann nur zum Vorannotieren von Dokumenten in {{site.data.keyword.knowledgestudioshort}} verwendet werden.

Damit ein Modell für die Verwendung durch einen Service bereitgestellt werden kann, müssen Sie über ein Abonnement für den betreffenden Service verfügen. {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}}-Services werden in {{site.data.keyword.Bluemix_short}}, der Cloudplattform für {{site.data.keyword.IBM_notm}}, gehostet. Weitere Informationen zur Plattform finden Sie unter [Was ist {{site.data.keyword.Bluemix_notm}}? ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.ng.bluemix.net/docs/overview/whatisbluemix.html){: new_window}. Um einen der {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}}-Services zu abonnieren, erstellen Sie ein Konto über die [{{site.data.keyword.Bluemix_notm}}-Website ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.ng.bluemix.net/){: new_window}.

Für einige der Services müssen Sie Details  zu der Serviceinstanz kennen, in der die Bereitstellung erfolgen soll (z. B. den Namen des {{site.data.keyword.Bluemix_notm}}-Bereichs und den Namen der Serviceinstanz). Der Bereichsname und der Instanzname sind auf der Seite für {{site.data.keyword.Bluemix_notm}}-Services verfügbar.

Sie können das Modell für maschinelles Lernen auch zum Vorannotieren neuer Dokumente verwenden. Details hierzu finden Sie unter [Dokumente mit einem Modell für maschinelles Lernen vorannotieren](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotsire).

## Modell für maschinelles Lernen in IBM Watson Discovery bereitstellen
{: #wks_madiscovery}

Wenn die Leistung des Modells Ihren Erwartungen entspricht, können Sie eine Version des Modells in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}} bereitstellen. Diese Funktion ermöglicht Ihren Anwendungen, das bereitgestellte Modell für maschinelles Lernen zu verwenden, um die aus Ihren Daten gewonnenen Erkenntnissen um die Erkennung der relevanten Konzepte und Beziehungen für Ihr Fachgebiet zu erweitern.

### Vorbereitungen
{: #wks_madiscovery_prereqs}

Sie benötigen Administratorzugriff auf eine Instanz des {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}-Service sowie die Namen des zugeordneten {{site.data.keyword.Bluemix_notm}}-Bereichs und der Instanz.

### Informationen zu diesem Vorgang
{: #wks_madiscovery_about}

Beim Bereitstellen des Modells für maschinelles Lernen wählen Sie die Modellversion aus, die Sie bereitstellen möchten.

### Vorgehensweise
{: #wks_madiscovery_procedure}

Führen Sie die folgenden Schritte aus, um das Modell für maschinelles Lernen in {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}} bereitzustellen:

1. Melden Sie sich als {{site.data.keyword.knowledgestudioshort}}-Administrator oder -Projektleiter an und wählen Sie Ihren Arbeitsbereich aus.
1. Wählen Sie **Modell für maschinelles Lernen** > **Versionen** aus.
1. Wählen Sie die Version des Modells aus, das Sie bereitstellen möchten.

    Wenn nur eine einzige funktionsfähige Version des Modells vorhanden ist, erstellen Sie einen Snapshot des aktuellen Modells. Dadurch wird das Modell versioniert, d. h. Sie können eine Modellversion bereitstellen und trotzdem fortfahren, die aktuelle Version zu verbessern. Die Option zum Bereitstellen wird erst angezeigt, wenn Sie mindestens eine Version erstellt haben.

    **Hinweis**: Jede Version kann nur für eine Serviceinstanz implementiert werden. Wenn Sie dasselbe Modell in mehreren Instanzen implementieren möchten, müssen Sie für jede Instanz eine Version erstellen.

1. Klicken Sie auf **Bereitstellen**, wählen Sie {{site.data.keyword.discoveryshort}} als Ziel für die Bereitstellung aus und klicken Sie anschließend auf **Weiter**.
1. Wählen Sie den {{site.data.keyword.Bluemix_notm}}-Bereich und die Instanz aus. Wählen Sie eine andere Region aus, falls nötig.
1. Klicken Sie auf **Bereitstellen**.
1. Der Bereitstellungsprozess kann mehrere Minuten dauern. Um den Status der Bereitstellung zu prüfen, klicken Sie auf **Status** in der Registerkarte **Versionen** neben der von Ihnen bereitgestellten Version.

    Wenn die Bereitstellung des Modells noch nicht abgeschlossen ist, wird der Status 'Publizieren läuft' angezeigt. Wenn die Bereitstellung erfolgreich abgeschlossen ist, wird der Status in 'Verfügbar' geändert. Wenn Probleme aufgetreten sind, wird der Status 'Fehler' angezeigt.

    Notieren Sie die Modell-ID (model_id), sobald sie angezeigt wird. Sie geben diese ID später im {{site.data.keyword.discoveryshort}}-Service an, damit der Service Ihr angepasstes Modell verwenden kann.

### Nächste Schritte
{: #wks_madiscovery_next}

Damit das bereitgestellte Modell verwendet werden kann, müssen Sie die Modell-ID nach entsprechender Aufforderung beim Konfigurationsprozess für die Aufbereitung des {{site.data.keyword.discoveryshort}}-Service, angeben. Details hierzu finden Sie in der [{{site.data.keyword.discoveryshort}}-Service-Dokumentation ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/docs/services/discovery/integrate-wks.html){: new_window}.

## Modell für maschinelles Lernen in IBM Watson Natural Language Understanding bereitstellen
{: #wks_manlu}

Wenn die Leistung des Modells Ihren Erwartungen entspricht, können Sie eine Version des Modells in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.nlushort}} bereitstellen. Mit dieser Funktion können Ihre Anwendungen das bereitgestellte Modell für maschinelles Lernen verwenden, um semantische Elemente der Texteingabe (einschließlich Entitäten und Beziehungen) zu analysieren.

### Vorbereitungen
{: #wks_manlu_prereqs}

Sie müssen über einen Service {{site.data.keyword.nlushort}} verfügen, der als Bereitstellungsziel verwendet werden kann. Außerdem müssen Sie die Namen des {{site.data.keyword.Bluemix_notm}}-Bereichs und der Instanz kennen, die dem Service zugeordnet sind. Die Namen des Bereichs und der Instanz können Sie abrufen, indem Sie sich bei {{site.data.keyword.Bluemix_notm}} anmelden. Wenn Sie nicht über ein {{site.data.keyword.Bluemix_notm}}-Konto verfügen, erstellen Sie ein Konto.

### Informationen zu diesem Vorgang
{: #wks_manlu_about}

Beim Bereitstellen des Modells für maschinelles Lernen wählen Sie die Modellversion aus, die Sie bereitstellen möchten.

### Vorgehensweise
{: #wks_manlu_procedure}

Führen Sie die folgenden Schritte aus, um ein Modell für maschinelles Lernen im Service {{site.data.keyword.nlushort}} bereitzustellen:

1. Melden Sie sich als {{site.data.keyword.knowledgestudioshort}}-Administrator oder -Projektleiter an und wählen Sie Ihren Arbeitsbereich aus.
1. Wählen Sie **Modell für maschinelles Lernen** > **Versionen** aus.
1. Wählen Sie die Version des Modells aus, das Sie bereitstellen möchten.

    Wenn nur eine einzige funktionsfähige Version des Modells vorhanden ist, erstellen Sie einen Snapshot des aktuellen Modells. Dadurch wird das Modell versioniert, d. h. Sie können eine Modellversion bereitstellen und trotzdem fortfahren, die aktuelle Version zu verbessern. Die Option zum Bereitstellen wird erst angezeigt, wenn Sie mindestens eine Version erstellt haben.

    **Hinweis**: Jede Version kann nur für eine Serviceinstanz implementiert werden. Wenn Sie dasselbe Modell in mehreren Instanzen implementieren möchten, müssen Sie für jede Instanz eine Version erstellen.

1. Klicken Sie auf **Bereitstellen**, wählen Sie {{site.data.keyword.nlushort}} als Ziel für die Bereitstellung aus und klicken Sie anschließend auf **Weiter**.
1. Wählen Sie den {{site.data.keyword.Bluemix_notm}}-Bereich und die Instanz aus. Wählen Sie eine andere Region aus, falls nötig.
1. Klicken Sie auf **Bereitstellen**.
1. Der Bereitstellungsprozess kann mehrere Minuten dauern. Um den Status der Bereitstellung zu prüfen, klicken Sie auf **Status** in der Registerkarte **Versionen** neben der von Ihnen bereitgestellten Version. Wenn die Bereitstellung des Modells noch nicht abgeschlossen ist, wird der Status 'Publizieren läuft' angezeigt. Wenn die Bereitstellung erfolgreich abgeschlossen ist, wird der Status in 'Verfügbar' geändert. Wenn Probleme aufgetreten sind, wird der Status 'Fehler' angezeigt.

    Notieren Sie die Modell-ID (model_id), sobald sie angezeigt wird. Sie geben diese ID später im {{site.data.keyword.nlushort}}-Service an, damit der Service Ihr angepasstes Modell verwenden kann.

### Nächste Schritte
{: #wks_manlu_next}

Damit das bereitgestellte Modell verwendet wird, müssen Sie die Modell-ID Ihres angepassten Modells im Parameter `entities.model` angeben.

Sie können das Modell mit der Anforderung {{site.data.keyword.nlushort}} `GET /analyze` verwenden, um die folgenden Elemente zu extrahieren:

- **Entitäten**

    Der folgende Befehl findet die vorhandenen Entitäten in dem Satz, der im Parameter 'text' übergeben wird:

    ```bash
    curl -G -u "3330af09-4b22-4f2d-a54c-1cb099df1fa8":"338rTJSvPVqeG"
    -d "version=2016-05-17"
    -d "text=Vehicle%201%2C%20a%201995%20Honda%20Civic%20was%20traveling%20north
    %20on%20a%20two%20lane%20undivided%20roadway%2C%20negotiating%20a%20curve%20to
    %20the%20left%20on%20an%20upgrade."
    -d "features=entities"
    -d "entities.model=10:7abc4c2f-5846-3334-b8f7-af5a6fad3398"
    "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze" -k
    ```
    {: pre}

    Der Service gibt ein JSON-Objekt mit den gefundenen Instanzen der Entitätstypen zurück, die in dem angepassten Modell definiert sind:

    ```javascript
    {
      "language": "en",
      "entities": [
        {
          "type": "MANUFACTURER",
          "text": "Honda",
          "count": 1
        },
        {
          "type": "MODEL",
          "text": "Civic",
          "count": 1
        },
        {
          "type": "VEHICLE",
          "text": "Vehicle 1",
          "count": 1
        },
        {
          "type": "STRUCTURE",
          "text": "two lane undivided roadway",
          "count": 1
        },
        {
          "type": "STRUCTURE",
          "text": "curve",
          "count": 1
        },
        {
          "type": "MODEL_YEAR",
          "text": "1995",
          "count": 1
        },
        {
          "type": "CONDITION",
          "text": "negotiating",
          "count": 1
        }
      ],
      "language": "en"
    }
    ```
    {: codeblock}

- **Beziehungen**

    Der folgende Befehl findet die vorhandenen Beziehungen in dem Satz, der im Parameter 'text' übergeben wird:

    ```bash
    curl -G -u "3330af09-4b22-4f2d-a54c-1cb099df1fa8":"338rTJSvPVqeG"
    -d "version=2016-05-17"
    -d "text=Vehicle%201%2C%20a%201995%20Honda%20Civic%20was%20traveling%20north
    %20on%20a%20two%20lane%20undivided%20roadway%2C%20negotiating%20a%20curve%20to
    %20the%20left%20on%20an%20upgrade."
    -d "features=relations"
    -d "entities.model=10:7abc4c2f-5846-3334-b8f7-af5a6fad3398"
    "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze" -k
    ```
    {: pre}

    Der Service gibt ein JSON-Objekt mit den gefundenen Instanzen der Beziehungstypen zurück, die in dem angepassten Modell definiert sind:

    ```javascript
    {
      "relations": [
        {
          "type": "timeOf",
          "sentence": "Vehicle 1, a 1995 Honda Civic was traveling north
           on a two lane undivided roadway, negotiating a curve to
           the left on an upgrade.",
          "score": 0.954254,
          "arguments": [
            {
              "text": "1995",
              "entities": [
                {
                  "type": "Date",
                  "text": "1995"
                }
              ]
            },
            {
              "text": "Honda Civic",
              "entities": [
                {
                  "type": "SportingEvent",
                  "text": "Honda Civic"
                }
              ]
            }
          ]
        },
        {
          "type": "locatedAt",
          "sentence": "Vehicle 1, a 1995 Honda Civic was traveling north
           on a two lane undivided roadway, negotiating a curve to
           the left on an upgrade.",
          "score": 0.40592,
          "arguments": [
            {
              "text": "negotiating",
              "entities": [
                {
                  "type": "EventMeeting",
                  "text": "negotiating"
                }
              ]
            },
            {
              "text": "roadway",
              "entities": [
                {
                  "type": "Facility",
                  "text": "roadway"
                }
              ]
            }
          ]
        }
      ],
      "language": "en"
    }
    ```
    {: codeblock}

Details hierzu finden Sie in der [Dokumentation für {{site.data.keyword.nlushort}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/docs/services/natural-language-understanding/index.html){: new_window}.

## Bereitstellung von Modellen aufheben
{: #undeploy-view-model}

Wenn Sie die Bereitstellung eines Modells aufheben oder ein Modell-ID abrufen möchten, öffnen Sie die Seite **Bereitgestellte Modelle**.

### Informationen zu diesem Vorgang
{: #wks_undeploy_about}

Was Sie auf der Seite 'Bereitgestellte Modelle' sehen, hängt von der [-Region ![External link icon](../../icons/launch-glyph.svg "Symbol für externen Link") ](https://{DomainName}/docs/resources/services_region.html){: new_window} ab, in der Ihre {{site.data.keyword.knowledgestudioshort}}-Instanz gehostet wird. Wenn
die Region Instanzen unterstützt, die von [IAM ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/docs/iam/users_roles.html){: new_window}- und [Cloud Foundry ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/docs/iam/cfaccess.html){: new_window}-Zugriffsmanagementmethoden unterstützt werden, werden für jede Methode eine Registerkarte angezeigt. Modelle aus Instanzen, die von IAM verwaltet werden, werden auf der Registerkarte **Ressourcengruppen** aufgelistet. Modelle aus Instanzen, die von Cloud verwaltet werden, werden auf der Registerkarte **Organisationen** aufgelistet. 

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

## Modell für maschinelles Lernen in IBM Watson Explorer wiederverwenden
{: #wks_maexport}

Exportieren Sie das trainierte Modell für maschinelles Lernen für die Verwendung in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.

### Vorbereitungen
{: #wks_maexport_prereqs}

Wenn Sie Beziehungstypen identifizieren und annotieren möchten, müssen Sie mindestens zwei Beziehungstypen definieren und Instanzen der Beziehung in der Ground Truth annotieren, bevor Sie das Modell exportieren. Wenn nur ein Beziehungstyp definiert und annotiert wird, kann dies zu Problemen in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer Version 11.0.1.0 führen.

### Informationen zu diesem Vorgang
{: #wks_maexport_about}

Nachdem das Modell für maschinelles Lernen zum Erkennen von Entitäten und Beziehungen für ein bestimmtes Fachgebiet trainiert wurde, können Sie es in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer wiederverwenden.

Klicken Sie auf [diesen Link ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.youtube.com/watch?v=1VoS-xczBow&amp;feature=youtu.be){: new_window} um ein Video über das Exportieren und Verwenden eines Modells in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer abzuspielen, das kürzer als zwei Minuten ist.

### Vorgehensweise
{: #wks_maexport_procedure}

Führen Sie die folgenden Schritte aus, um ein Modell für maschinelles Lernen in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer wiederzuverwenden.

1. Melden Sie sich als {{site.data.keyword.knowledgestudioshort}}-Administrator oder -Projektleiter an und wählen Sie Ihren Arbeitsbereich aus.
1. Wählen Sie **Modell für maschinelles Lernen** > **Versionen** aus.
1. Klicken Sie auf **Aktuelles Modell exportieren**.

    Wenn Sie einen Lite-Plan abonniert haben, ist keine Exportoption verfügbar.

    Das Modell wird als ZIP-Datei gespeichert und Sie werden aufgefordert, die Datei herunterzuladen.

1. Laden Sie die Datei in Ihr lokales System herunter.
1. Importieren Sie das Modell mit der {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer-Anwendung.

    Anschließend können Sie das Modell einem Modell für maschinelles Lernen in {{site.data.keyword.watson}} Explorer Content Analytics zuordnen. Nachdem Sie den Zuordnungsschritt ausgeführt haben, findet das Modell beim Durchsuchen von Dokumenten Instanzen der Entitäten und Beziehungen, die in dem Modell definiert sind. Informationen zum Importieren und Konfigurieren des Modells in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer finden Sie in der technischen Dokumentation zur Integration: [http://www.ibm.com/support/docview.wss?uid=swg27048147 ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://www.ibm.com/support/docview.wss?uid=swg27048147){: new_window}.

#### Zugehörige Tasks
{: #wks_maexport_related}

[Analysierte Dokumente aus {{site.data.keyword.watson}} Explorer Content Analytics exportieren](/docs/services/watson-knowledge-studio/preannotation.html#wks_uimawexca)
