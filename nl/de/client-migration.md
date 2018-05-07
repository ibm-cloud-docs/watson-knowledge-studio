---

copyright:
  years: 2015, 2018
lastupdated: "2018-03-14"

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

Diese Dokumentation bezieht sich auf {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Die Dokumentation für die Vorgängerversion {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace kann über [diesen Link ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/docs/services/knowledge-studio/client-migration.html){: new_window} aufgerufen werden.
{: tip}

# Migration auf IBM Cloud
{: #migrate}

Am 18. Dezember 2017 wurde von IBM {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud_notm}} eingeführt. Ab diesem Datum beginnt der Prozess für die Migration aller {{site.data.keyword.knowledgestudioshort}}-Instanzen von {{site.data.keyword.IBM_notm}} Marketplace auf {{site.data.keyword.cloud_notm}}.
{: shortdesc}

**Hinweis**: In {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud_notm}} wird der Begriff _Arbeitsbereich_ verwendet, während in {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace der Begriff _Projekt_ verwendet wird. Beide Begriffe bezeichnen die gleiche Funktionalität. Der einzige Unterschied liegt in der verwendeten Terminologie.

## Prozess und Zeitplan
{: #process}

Der Migrationsprozess und -zeitplan für Ihre {{site.data.keyword.knowledgestudioshort}}-Projekte hängt von Ihrem aktuellen [-Preistarif für {{site.data.keyword.IBM_notm}} Marketplace ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/us-en/marketplace/supervised-machine-learning/purchase#product-header-top){: new_window} und dem Kontotyp ab, wie in der folgenden Tabelle gezeigt:

| Tarif und Konto | Migrationsprozess | Migrationszeitplan |
|------|-------------------|--------------------|
| Kostenloser Plan | Instanz und Daten werden vom Kunden migriert. | Migrationen müssen bis zum 1. Februar 2018 abgeschlossen sein. Am 2. Februar 2018 werden alle kostenlosen Pläne in {{site.data.keyword.IBM_notm}} Marketplace bereinigt, einschließlich der zugehörigen Projektdaten. |
| Standardplan mit nutzungsabhängigem Konto | Instanz und Daten werden vom Kunden migriert. | Migrationen müssen spätestens am 29. Juni 2018 abgeschlossen sein. Am 30. Juni 2018 werden alle Standardpläne mit nutzungsabhängigen Konten in {{site.data.keyword.IBM_notm}} Marketplace bereinigt, einschließlich der zugehörigen Projektdaten.
| Standardplan mit Vertrag | Instanz und Daten werden vom Kunden migriert. {{site.data.keyword.IBM_notm}} verlängert den Vertrag. | Migrationen müssen spätestens am 29. Juni 2018 abgeschlossen sein. Wenden Sie sich an Ihren zuständigen {{site.data.keyword.IBM_notm}} Kundenbeauftragten oder an [{{site.data.keyword.cloud_notm}} Sales ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). |
| Premium-Plan mit Vertrag | Instanz und Daten werden von {{site.data.keyword.IBM_notm}} migriert. {{site.data.keyword.IBM_notm}} verlängert den Vertrag. | Migrationen müssen spätestens am 29. Juni 2018 abgeschlossen sein. Wenden Sie sich an Ihren zuständigen {{site.data.keyword.IBM_notm}} Kundenbeauftragten oder an [{{site.data.keyword.cloud_notm}} Sales ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). |
{: caption="Tabelle 1. Prozess und Zeitplan für die {{site.data.keyword.knowledgestudioshort}}-Migration von {{site.data.keyword.IBM_notm}} Marketplace auf {{site.data.keyword.cloud_notm}}" caption-side="top"}

## Kostenlose Pläne migrieren
{: migratefree}

Wenn Sie über einen kostenlosen Plan für {{site.data.keyword.knowledgestudioshort}} verfügen, führen Sie die folgenden Schritte aus, um Ihre Instanz und Ihre Projekte von {{site.data.keyword.IBM_notm}} Marketplace auf {{site.data.keyword.cloud_notm}} zu migrieren:

1. Wenn Sie noch nicht über ein {{site.data.keyword.cloud_notm}}-Konto verfügen, registrieren Sie sich unter [{{site.data.keyword.cloud_notm}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://ibm.biz/wks_cloud){: new_window} mithilfe Ihrer {{site.data.keyword.ibmid}} in {{site.data.keyword.IBM_notm}} Marketplace.

   Ihre {{site.data.keyword.ibmid}} ist die ID, die Sie für die Anmeldung bei {{site.data.keyword.knowledgestudioshort}} in {{site.data.keyword.IBM_notm}} Marketplace verwenden.

1. Melden Sie sich bei [{{site.data.keyword.cloud_notm}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/dashboard/apps/){: new_window} an.
1. Wenn Sie noch nicht über eine {{site.data.keyword.knowledgestudioshort}}-Instanz in {{site.data.keyword.cloud_notm}} verfügen, erstellen Sie eine Instanz im [{{site.data.keyword.cloud_notm}}-Katalog auf der Seite {{site.data.keyword.knowledgestudioshort}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/catalog/services/knowledge-studio){: new_window}.
1. Führen Sie den Prozess [Sicherung und Wiederherstellung](/docs/services/watson-knowledge-studio/backup-restore.html) aus, um Ihre Projekte manuell von der {{site.data.keyword.IBM_notm}} Marketplace-Instanz auf Ihre Instanz in {{site.data.keyword.cloud_notm}} zu migrieren.

  **Hinweis**: Wenn Sie bereits über ein bereitgestelltes Modell verfügen und den Arbeitsbereich nach dem Sichern löschen möchten, ziehen Sie das Modell aus der Bereitstellung zurück. Sie können das Modell erneut erstellen und implementieren, nachdem Sie den Arbeitsbereich aus der Sicherung wiederhergestellt haben. Informationen zum Aufheben der Bereitstellung von Modellen finden Sie unter [Bereitstellung von Modellen für maschinelles Lernen aufheben](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) und [Bereitstellung regelbasierter Modelle aufheben](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model).

## Migration von Standardplänen für nutzungsabhängige Konten
{: migratepaygo}

Wenn Sie über einen Standardplan und ein [nutzungsabhängiges Konto ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/docs/pricing/billable.html){: new_window} verfügen, führen Sie die folgenden Schritte aus, um Ihre Instanzen und Projekte von {{site.data.keyword.IBM_notm}} Marketplace auf {{site.data.keyword.cloud_notm}} zu migrieren:

1. Wenn Sie noch nicht über ein {{site.data.keyword.cloud_notm}}-Konto verfügen, registrieren Sie sich unter [{{site.data.keyword.cloud_notm}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/cloud/){: new_window} mithilfe Ihrer {{site.data.keyword.ibmid}} in {{site.data.keyword.IBM_notm}} Marketplace.

   Ihre {{site.data.keyword.ibmid}} ist die ID, die Sie für die Anmeldung bei {{site.data.keyword.knowledgestudioshort}} in {{site.data.keyword.IBM_notm}} Marketplace verwenden.

1. Melden Sie sich bei [{{site.data.keyword.cloud_notm}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/dashboard/apps/){: new_window} an.
1. Wenn Sie noch nicht über eine {{site.data.keyword.knowledgestudioshort}}-Instanz in {{site.data.keyword.cloud_notm}} verfügen, erstellen Sie eine Instanz im [{{site.data.keyword.cloud_notm}}-Katalog auf der Seite {{site.data.keyword.knowledgestudioshort}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/catalog/services/knowledge-studio){: new_window}.
1. Führen Sie den Prozess [Sicherung und Wiederherstellung](/docs/services/watson-knowledge-studio/backup-restore.html) aus, um Ihre Projekte manuell von der {{site.data.keyword.IBM_notm}} Marketplace-Instanz auf Ihre Instanz in {{site.data.keyword.cloud_notm}} zu migrieren.

  **Hinweis**: Wenn Sie bereits über ein bereitgestelltes Modell verfügen und den Arbeitsbereich nach dem Sichern löschen möchten, ziehen Sie das Modell aus der Bereitstellung zurück. Sie können das Modell erneut erstellen und implementieren, nachdem Sie den Arbeitsbereich aus der Sicherung wiederhergestellt haben. Informationen zum Aufheben der Bereitstellung von Modellen finden Sie unter [Bereitstellung von Modellen für maschinelles Lernen aufheben](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) und [Bereitstellung regelbasierter Modelle aufheben](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model).

## Migration von Standardplänen für Vertragskonten
{: migratecontract}

Wenn Sie über einen {{site.data.keyword.knowledgestudioshort}}-Standardplan mit Vertrag verfügen, führen Sie die folgenden Schritte aus, um Ihren Vertrag zu verlängern und Ihre Instanz und Projekte von {{site.data.keyword.IBM_notm}} Marketplace auf {{site.data.keyword.cloud_notm}} zu migrieren:

1. Um den Vertrag zu verlängern, wenden Sie sich an Ihren zuständigen {{site.data.keyword.IBM_notm}} Kundenbeauftragten oder an [{{site.data.keyword.cloud_notm}} Sales ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration).
1. Melden Sie sich nach dem Verlängern des Vertrags für {{site.data.keyword.cloud_notm}} bei [{{site.data.keyword.cloud_notm}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/dashboard/apps/){: new_window} an.
1. Wenn Sie noch nicht über eine {{site.data.keyword.knowledgestudioshort}}-Instanz in {{site.data.keyword.cloud_notm}} verfügen, erstellen Sie eine Instanz im [{{site.data.keyword.cloud_notm}}-Katalog auf der Seite {{site.data.keyword.knowledgestudioshort}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/catalog/services/knowledge-studio){: new_window}.
1. Führen Sie den Prozess [Sicherung und Wiederherstellung](/docs/services/watson-knowledge-studio/backup-restore.html) aus, um Ihre Projekte manuell von der {{site.data.keyword.IBM_notm}} Marketplace-Instanz auf Ihre Instanz in {{site.data.keyword.cloud_notm}} zu migrieren.

  **Hinweis**: Wenn Sie bereits über ein bereitgestelltes Modell verfügen und den Arbeitsbereich nach dem Sichern löschen möchten, ziehen Sie das Modell aus der Bereitstellung zurück. Sie können das Modell erneut erstellen und implementieren, nachdem Sie den Arbeitsbereich aus der Sicherung wiederhergestellt haben. Informationen zum Aufheben der Bereitstellung von Modellen finden Sie unter [Bereitstellung von Modellen für maschinelles Lernen aufheben](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) und [Bereitstellung regelbasierter Modelle aufheben](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model).

## Migration von Premium-Plänen für Vertragskonten
{: migratecontract}

Wenn Sie über einen {{site.data.keyword.knowledgestudioshort}}-Premium-Plan mit Vertrag verfügen, wenden Sie sich an Ihren zuständigen {{site.data.keyword.IBM_notm}} Kundenbeauftragten oder an [{{site.data.keyword.cloud_notm}} Sales ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). Sobald der Vertrag in {{site.data.keyword.cloud_notm}} verlängert ist, werden Ihre Daten von IBM entsprechend dem zwischen Ihnen und {{site.data.keyword.cloud_notm}} vereinbarten Zeitplan migriert.
