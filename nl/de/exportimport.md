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

Diese Dokumentation bezieht sich auf {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Die Dokumentation für die Vorgängerversion {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace kann über [diesen Link ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/docs/services/knowledge-studio/exportimport.html){: new_window} aufgerufen werden.
{: tip}

# Ressourcen aus einem anderen Arbeitsbereich hochladen
{: #exportimport}

Um die Erstellung eines Modells zu beschleunigen, können Sie Ressourcen wie Dokumente (mit oder ohne Ground Truth-Annotationen), ein Typsystem und Wörterverzeichnisse hochladen, die Sie aus einem anderen Arbeitsbereich heruntergeladen haben.
{: shortdesc}

Die Funktionen zum getrennten Herunter- und Hochladen unterschiedlicher Ressourcen bietet Ihnen mehr Flexibilität beim Entwickeln und Erstellen eines Modells. Sie können beispielsweise einen Arbeitsbereich zum Entwickeln des Typsystems und für die Arbeit der Annotatorbenutzer erstellen und anschließend einen zweiten Arbeitsbereich (möglicherweise in einer separaten {{site.data.keyword.knowledgestudioshort}}-Instanz) für andere Benutzer zum Trainieren des Modells für maschinelles Lernen. Die Funktion zum Hochladen der Ressourcen (einschließlich der von Annotatorbenutzern erstellten Ground Truth) macht dieses Szenario möglich.

Ein Modell für maschinelles Lernen kann nicht heruntergeladen und hochgeladen werden. Stattdessen können Sie alle Artefakte, die zum Erstellen des Modells verwendet wurde, von einem Arbeitsbereich herunterladen und in einen neuen Arbeitsbereich hochladen. In dem neuen Arbeitsbereich können Sie das Training wiederholen, um das Modell erneut zu erstellen. Das neue Modell sollte ähnliche Ergebnisse liefern wie das ursprüngliche Modell, da beide mit derselben Gruppe von Artefakten trainiert wurden.

Die Dateien, die Sie herunterladen, sind vom Betriebssystem unabhängig. Auf den {{site.data.keyword.knowledgestudioshort}}-Instanzen, die Sie zum Herunterladen und zum Hochladen der Dateien verwenden, muss nicht dieselbe Version von Linux ausgeführt werden.

## Typsysteme
{: #wks_exportimport_expimp_type}

Um ein Typsystem herunterzuladen, öffnen Sie die Seite **Assets** > **Entitätstypen** und klicken Sie auf **Typen herunterladen**. Das System erstellt eine Datei mit dem Namen `types-ID.json` und fordert Sie auf, die Datei in Ihr lokales System herunterzuladen. Wenn Sie dieses Typsystem in einem neuen Arbeitsbereich verwenden möchten, öffnen Sie die Seite **Entitätstypen** und laden Sie die `JSON`-Datei hoch, die Sie zuvor heruntergeladen haben.

## Wörterverzeichnisse
{: #wks_exportimport_expimp_dict}

Wenn Sie alle Wörterverzeichnisse herunterladen möchten, wählen Sie die Seite **Assets** > **Wörterverzeichnisse** aus, klicken Sie auf das **Menü**-Symbol neben der Schaltfläche **Wörterverzeichnis erstellen** und wählen Sie **Wörterverzeichnisse herunterladen** aus. Für jedes Wörterverzeichnis, das Sie herunterladen, erstellt das System eine Datei mit dem Namen `wörterverzeichnisname_zeitmarke.csv` , komprimiert die erstellten Dateien zu einer `ZIP`-Datei mit dem Namen `arbeitsverzeichnisname_wörterverzeichnis_zeitmarke.zip` und fordert Sie auf, die Datei in Ihr lokales System herunterzuladen.

Sie können ein einzelnes Wörterverzeichnis herunterladen, indem Sie das Wörterverzeichnis öffnen und auf **Herunterladen** klicken. Schreibgeschützte Wörterverzeichnisse, die Sie als CSV-Datei hochgeladen haben, können nicht heruntergeladen werden.

Bevor Sie ein heruntergeladenes Wörterverzeichnis in einen neuen Arbeitsbereich hochladen, müssen Sie das Typsystem aus dem ursprünglichen Arbeitsbereich herunterladen und in den neuen Arbeitsbereich hochladen. Das Typsystem und die Wörterverzeichnisse müssen aus demselben {{site.data.keyword.knowledgestudioshort}}-Arbeitsbereich stammen und das Typsystem muss in dem neuen Arbeitsbereich vorhanden sein, bevor Sie die Wörterverzeichnisse hochladen.

Um Wörterverzeichnisse hochzuladen, öffnen Sie die Registerkarte **Wörterverzeichnisse** und fügen Sie entweder `CSV`-Datei hinzu, die Sie heruntergeladen haben, oder laden Sie die `ZIP`-Datei hoch.

## Dokumente
{: #wks_exportimport_expimp_doc}

Um Dokumente herunterzuladen, die Sie zum Korpus hinzugefügt haben, öffnen Sie die Registerkarte **Assets** > **Dokumente** > **Dokumentgruppen** und klicken Sie auf **Dokumentgruppen herunterladen**. Das System erstellt eine Datei mit dem Namen `corpus-ID.zip` und fordert Sie auf, die Datei in Ihr lokales System herunterzuladen. Die `ZIP`-Datei enthält alle Dokumente aus dem Korpus. Annotationen, die in Annotationsgruppen hinzugefügt wurden, werden in die ZIP-Datei einbezogen, jedoch erst, nachdem die Annotationsgruppen genehmigt und in die Ground Truth hochgestuft wurden.

> **Einschränkung:** Alle vorannotierten Dokumente werden beim Herunterladen durch ein nicht lesbares Format unkenntlich gemacht. Ereignisannotationen in diesen Dokumenten, die von Annotatorbenutzern hinzugefügt wurden, sind nicht lesbar.

Bevor Sie Dokumente, die Ground Truth enthalten, in einen neuen Arbeitsbereich hochladen, müssen Sie das Typsystem aus dem ursprünglichen Arbeitsbereich herunterladen und in den neuen Arbeitsbereich hochladen. Das Typsystem und die Dokumente müssen aus demselben {{site.data.keyword.knowledgestudioshort}}-Arbeitsbereich stammen und das Typsystem muss in dem neuen Arbeitsbereich vorhanden sein, bevor Sie die Ground Truth-Annotationen hochladen.

Um Dokumente hochzuladen, öffnen Sie die Registerkarte **Dokumentgruppen** im neuen Arbeitsbereich, klicken Sie auf **Dokumentgruppen hochladen** und wählen Sie die `ZIP`-Datei mit dem Korpus aus, die Sie heruntergeladen haben. Geben Sie an, ob die Ground Truth-Annotationen in den hochgeladenen Dokumenten enthalten sein sollen oder nicht, bevor Sie auf **Hochladen** klicken. Es werden nur Annotationen hochgeladen, die vor dem Herunterladen der Dokumente in die Ground Truth hochgestuft wurden.

**Zugehörige Konzepte**:

[Artefakttypen](/docs/services/watson-knowledge-studio/artifacts.html)

[Dokumente zum Annotieren hinzufügen](/docs/services/watson-knowledge-studio/documents-for-annotation.html)

[Dokumente zum Definieren von Regeln hinzufügen](/docs/services/watson-knowledge-studio/rule-annotator-add-doc.html)
