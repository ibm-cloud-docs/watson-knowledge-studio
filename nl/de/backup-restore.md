---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-20"

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

Diese Dokumentation bezieht sich auf {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Die Dokumentation für die Vorgängerversion {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace kann über [diesen Link ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/docs/services/knowledge-studio/backup-restore.html){: new_window} aufgerufen werden.
{: tip}

# Daten sichern und wiederherstellen
{: #backup-restore}

Wenn Sie einen Arbeitsbereich für {{site.data.keyword.knowledgestudioshort}} sichern und wiederherstellen möchten, führen Sie die folgenden Tasks aus. Führen Sie diese Tasks auch aus, wenn Sie eine manuelle Datenmigration von einer {{site.data.keyword.knowledgestudioshort}}-Instanz auf eine andere vornehmen möchten (z. B. bei der Migration von einer Instanz in {{site.data.keyword.IBM_notm}} Marketplace auf eine Instanz in {{site.data.keyword.cloud_notm}}).
{: shortdesc}

Bei der _manuellen Datenmigration_ werden Ihre Daten aus einer Instanz gesichert und in einer anderen Instanz wiederhergestellt.

**Hinweis**: In {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud_notm}} wird der Begriff _Arbeitsbereich_ verwendet, während in {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace der Begriff _Projekt_ verwendet wird. Beide Begriffe bezeichnen die gleiche Funktionalität. Der einzige Unterschied liegt in der verwendeten Terminologie.

Führen Sie die folgenden Schritte aus, um Ihre Daten zu sichern und wiederherzustellen:

1. [In Erfahrung bringen, welche Daten gesichert werden können](#data)
1. [Sicherung vorbereiten](#prepare)
1. [Artefakte aus der aktuellen Instanz herunterladen](#export)
1. [Arbeitsbereiche in der neuen Instanz erneut erstellen](#recreateproj)
1. [Arbeitsbereichsdaten wiederherstellen](#restoredata)
1. [Modelle wiederherstellen](#restoremodels)
1. [Unvollständige Annotationstasks wiederherstellen](#restoretasks)

## Diese Daten können gesichert werden
{: #data}

Die folgenden Artefakte können manuell gesichert und migriert werden:

- Bearbeitbare Wörterverzeichnisse
- Typsystem
- Genehmigte Ground Truth-Dokumentgruppen

Die folgenden Artefakttypen können nicht manuell gesichert und migriert werden:

- In Bearbeitung befindliche Dokumente der Annotationsbenutzer
- Annotationstasks
- Modelle und Snapshots
- Schreibgeschützte Wörterverzeichnisse

## Sicherung vorbereiten
{: #prepare}

Führen Sie die folgenden Schritte aus, um die Sicherung und Wiederherstellung Ihrer Daten vorzubereiten:

1. Beenden Sie alle in Bearbeitung befindlichen Tasks in Ihrem Arbeitsbereich.

    - >**Wichtig:** Beenden Sie alle in Bearbeitung befindlichen Annotationstasks. Nur Dokumente, die annotiert, beurteilt, genehmigt und in die Ground Truth hochgestuft wurden, können gesichert werden. Wenn Sie die Annotationstasks nicht beenden, gehen alle Ergebnisse der aktiven und nicht abgeschlossenen Annotationstasks verloren.

    - Wenn Sie Annotationstasks erstellt haben, um auszuführende Arbeiten zu überwachen, die erst nach der Wiederherstellung des Arbeitsbereichs begonnen bzw. ausgeführt werden, erstellen Sie eine Liste der ausstehenden Annotationstasks. Notieren Sie unbedingt die von Ihnen importierten Dokumentgruppen, die noch nicht zur Ground Truth hinzugefügt wurden. Notieren Sie außerdem welche Personen Sie als Annotatorbenutzer für die einzelnen Dokumentgruppen zugeordnet haben. Nach der Wiederherstellung des Arbeitsbereichs müssen Sie diese Dokumentgruppen erneut hochladen und die Annotationstasks erneut erstellen.

1. Tokenizer-Verwendung verstehen

    In Arbeitsbereichen für Modelle für maschinelles Lernen wird standardmäßig der Tokenizer für maschinelles Lernen verwendet. Wenn Sie einen wörterverzeichnisbasierten Tokenizer verwenden und aufgrund Ihrer speziellen Anforderungen beibehalten müssen, können Sie den Arbeitsbereich so konfigurieren, dass nach der Wiederherstellung der wörterverzeichnisbasierte Tokenizer verwendet wird. Weitere Informationen hierzu finden Sie unter [Tokenizer](/docs/services/watson-knowledge-studio/create-project.html#wks_tokenizer).

1. Modellressourcen verwalten

    Ihr Modell sowie die zugehörigen Versionen und Snapshot-Daten können nicht migriert werden. Die Ressourcen, die Sie zum Trainieren dieser Artefakte verwendet haben, können migriert werden (ausgenommen schreibgeschützte Wörterverzeichnisse). Daher können Sie das Modell nach der Migration erneut erstellen. Die Funktionsweise des resultierenden Modells entspricht den Modellen, die Sie vor der Migration generiert haben, da dieselben Trainingsressourcen verwendet werden.

    **ACHTUNG**: Wenn Sie bereits über ein bereitgestelltes Modell verfügen und den Arbeitsbereich nach dem Sichern löschen möchten, heben Sie die Bereitstellung des Modells auf. Sie können das Modell erneut erstellen und implementieren, nachdem Sie den Arbeitsbereich aus der Sicherung wiederhergestellt haben. Informationen zum Aufheben der Bereitstellung von Modellen finden Sie unter [Bereitstellung von Modellen für maschinelles Lernen aufheben](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) und [Bereitstellung regelbasierter Modelle aufheben](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model).

    **Wenn die Bereitstellung des Modells nicht aufgehoben wird, ist das Ergebnis ein _verwaistes_ bereitgestelltes Modell. Für verwaiste bereitgestellte Modelle fallen weiter Gebühren in Ihren Monatsrechnungen an.**

1. Informationen für schreibgeschützte Wörterverzeichnisse verwalten

    Schreibgeschützte Wörterverzeichnisse können nicht migriert werden. Stellen Sie fest, aus welcher Quelle das schreibgeschützte Wörterverzeichnis importiert wurde, damit es nach der Migration erneut in Ihren Arbeitsbereich hochgeladen werden kann.

1. Erstellen Sie eine Liste der aktuellen Benutzerrollen.

    **Hinweis**: Dieser Schritt ist optional. Er wird normalerweise ausgeführt, wenn ein Arbeitsbereich über mehrere Instanzen migriert wird und der neue Arbeitsbereich mit dem ursprünglichen Arbeitsbereich identisch sein muss. Wenn Sie nur die Arbeitsbereichsdaten in einen neuen Arbeitsbereich migrieren möchten, können Sie diesen Schritt überspringen.

    Wenn Sie Arbeitsbereiche über mehrere Instanzen migrieren, sollten Sie in Betracht ziehen, eine Liste der Benutzer und ihrer Rollen für die Instanz zu erstellen, die Sie sichern möchten. Ein Benutzer mit der Rolle 'Administrator' kann die Liste von der Seite 'Benutzerkontoverwaltung' aus drucken. Nachdem die Arbeitsbereiche in der neuen Instanz erneut erstellt wurden, muss ein Benutzer mit der Rolle 'Administrator' die Benutzer hinzufügen und ihnen Rollen zuordnen.

    Weitere Informationen zu Rollen finden Sie in [Benutzerrollen in {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/roles.html).

1. Arbeitsbereichsinformationen notieren

    Solange Sie noch Zugriff auf die aktuelle Instanz haben, notieren Sie die folgenden Informationen für jeden Arbeitsbereich, den Sie migrieren möchten:
    - Name des Arbeitsbereichs
    - Beschreibung des Arbeitsbereichs
    - Eigentümer des Arbeitsbereichs
    - Sprache
    - Falls nicht abgeschlossene Annotationstasks vorhanden sind (sie können nicht gesichert oder migriert werden), notieren Sie die Annotationsbenutzer, denen diese Tasks im Arbeitsbereich zugeordnet sind. Notieren Sie auch die Details der Annotationstasks (z. B. den Tasknamen, das Fälligkeitsdatum und welche Dokumentgruppen welchen Benutzern zugeordnet sind).

## Artefakte herunterladen
{: #export}

Laden Sie für jeden Arbeitsbereich, den Sie migrieren möchten, die folgenden Artefakte herunter. Speichern Sie diese Artefakte an einer sicheren Position, aus der sie später in die neue Instanz hochgeladen werden können.

- Typsystem
- Wörterverzeichnisse

  **Hinweis**:
    - Nur bearbeitbare Wörterverzeichnisse werden heruntergeladen. Sie können keine schreibgeschützten Wörterverzeichnisse herunterladen.
    - Bei Wörterverzeichnissen werden Entitätstypzuordnungen nicht migriert. Nachdem Sie diese Artefakte wiederhergestellt haben, müssen Sie die Wörterverzeichnisse möglicherweise den Entitätstypen zuordnen. 

- Dokumente

  Informationen zum Herunterladen dieser Artefakte, damit sie in einen neuen Arbeitsbereich importiert werden können, finden Sie unter [Ressourcen aus einem anderen Arbeitsbereich hochladen](/docs/services/watson-knowledge-studio/exportimport.html).

## Arbeitsbereiche erneut erstellen
{: #recreateproj}

**Hinweis**: In diesem Schritt muss lediglich die Sprache mit der Einstellung des ursprünglichen (heruntergeladenen) Arbeitsbereichs übereinstimmen. Die übrigen Einstellungen können von den Einstellungen des ursprünglichen Arbeitsbereichs abweichen.

Sie können jeden Arbeitsbereich erneut erstellen, indem Sie die folgenden Informationen aus der vorherigen Instanz in die neue Instanz kopieren:

- Name des Arbeitsbereichs
- Beschreibung des Arbeitsbereichs
- Sprache der Dokumente (diese Einstellung muss mit der Einstellung im ursprünglichen Arbeitsbereich übereinstimmen)
- Wenn Sie zuvor einen wörterverzeichnisbasierten Tokenizer im Arbeitsbereich verwendet haben und diesen aus gegebenem Anlass weiterhin verwenden möchten, müssen Sie bei der Erstellung des Arbeitsbereichs angeben, dass nicht der Standard-Tokenizer sondern der wörterverzeichnisbasierte Tokenizer verwendet werden soll. Weitere Informationen hierzu finden Sie unter [Tokenizer](/docs/services/watson-knowledge-studio/create-project.html#wks_tokenizer).

  Um einen wörterverzeichnisbasierten Tokenizer zu verwenden, erweitern Sie den Abschnitt 'Erweiterte Optionen' im Fenster 'Arbeitsbereich erstellen' (in {{site.data.keyword.IBM_notm}} Marketplace das Fenster 'Arbeitsbereich erstellen') und ändern Sie die Einstellung für Tokenizer.

## Arbeitsbereichsdaten wiederherstellen
{: #restoredata}

Laden Sie nach dem erneuten Erstellen der Arbeitsbereiche die Artefakte hoch, die zuvor heruntergeladen wurden.

1. Laden Sie das Typsystem aus der zuvor erstellten Typsystemsicherung hoch.
   Details hierzu finden Sie unter [Ressourcen aus einem anderen Arbeitsbereich hochladen](/docs/services/watson-knowledge-studio/exportimport.html).

  **Hinweis**: Erst nach dem Hochladen des Typsystems können Sie andere Artefakte hochladen, die Sie aus der Sicherung des Arbeitsbereichs übernehmen möchten.

1. Laden Sie die Wörterverzeichnisse aus der zuvor erstellten Sicherung der Wörterverzeichnisse hoch.
   Details hierzu finden Sie unter [Ressourcen aus einem anderen Arbeitsbereich hochladen](/docs/services/watson-knowledge-studio/exportimport.html).

  Wenn in der vorherigen Version des Arbeitsbereichs schreibgeschützte Wörterverzeichnisse verwendet wurden, laden Sie sie aus der ursprünglichen Quelle erneut in diesen Arbeitsbereich hoch.

1. Für Wörterverzeichnisvorannotatoren ordnen Sie die Wörterverzeichnisse einem Entitätstyp zu. Wörterverzeichnisse, für die keine Zuordnungen für Entitätstypen vorhanden sind, wenden keine Annotationen an, wenn Sie Dokumente vorab mit Annotationen versehen.

1. Laden Sie die Dokumente, die Sie aus der vorherigen Version des Arbeitsbereichs heruntergeladen haben, in diese Version des Arbeitsbereichs hoch.
   Details hierzu finden Sie unter [Ressourcen aus einem anderen Arbeitsbereich hochladen](/docs/services/watson-knowledge-studio/exportimport.html).

## Modelle wiederherstellen
{: #restoremodels}

Jetzt sind alle Artefakte, die zum Trainieren des Modells in der vorherigen (gesicherten) Version des Arbeitsbereichs verwendet wurden, in der neuen Instanz verfügbar.

Führen Sie die folgenden Schritte aus, um ein Modell für maschinelles Lernen, das Sie in der vorherigen Instanz bereitgestellt hatten, erneut bereitzustellen:

1. [Trainieren Sie das Modell für maschinelles Lernen](/docs/services/watson-knowledge-studio/train-ml.html).

  **Hinweise**: Wenden Sie keine Vorannotationen auf die annotierten Dokumente an, die Sie in diesen Arbeitsbereich migriert haben. Andernfalls gehen alle Annotationen in den betreffenden Dokumenten verloren, die von Annotatorbenutzern hinzugefügt wurden.

1. Stellen Sie das Modell erneut bereit, nachdem Sie es erstellt haben. Details hierzu finden Sie unter [Modell für maschinelles Lernen verwenden](/docs/services/watson-knowledge-studio/publish-ml.html).

Führen Sie die folgenden Schritte aus, um ein regelbasiertes Modell erneut bereitzustellen, das Sie in der vorherigen Instanz bereitgestellt hatten:

1. [Regelbasiertes Modell erstellen](/docs/services/watson-knowledge-studio/rule-annotator-model-create.html).
1. [Regelbasiertes Modell bereitstellen](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html).

## Unvollständige Annotationstasks wiederherstellen
{: #restoretasks}

Wenn Sie im vorherigen Arbeitsbereich Annotationstasks erstellt hatten, die noch nicht abgeschlossen waren, führen Sie die folgenden Schritte aus, um die betreffenden Annotationstasks erneut zu erstellen:

1. [Laden Sie alle noch nicht annotierten Dokumente hoch](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projadd), die Sie jedoch zur Ground Truth hinzufügen möchten, um das Modell zu verbessern.
1. Erstellen Sie aus den neu importierten und nicht annotierten Dokumenten [Annotationsgruppen](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projdocsets).
1. [Erstellen Sie die Annotationstasks erneut](/docs/services/watson-knowledge-studio/annotate-documents.html#wks_hatask). Weisen Sie den Tasks denselben Namen sowie ein geeignetes Fälligkeitsdatum zu und ordnen Sie Annotationsgruppen den gewünschten Annotatorbenutzern zu.
