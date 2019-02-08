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

Diese Dokumentation bezieht sich auf {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Die Dokumentation für die Vorgängerversion {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace kann über [diesen Link ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/docs/services/knowledge-studio/client-migration.html){: new_window} aufgerufen werden.
{: tip}

# Migration auf IBM Cloud
{: #migrate}

Am 18. Dezember 2017 wurde von IBM {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud_notm}} eingeführt. Ab diesem Datum beginnt der Prozess für die Migration aller {{site.data.keyword.knowledgestudioshort}}-Instanzen von {{site.data.keyword.IBM_notm}} Marketplace auf die [{{site.data.keyword.cloud_notm}}-Plattform ![External link icon](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/blogs/bluemix/2017/12/watson-knowledge-studio-ibm-cloud/){: new_window}.
{: shortdesc}

**Hinweis**: In {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud_notm}} wird der Begriff _Arbeitsbereich_ verwendet, während in {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace der Begriff _Projekt_ verwendet wird. Beide Begriffe bezeichnen die gleiche Funktionalität. Der einzige Unterschied liegt in der verwendeten Terminologie.

**Achtung**: Wenn Sie die DSGVO einhalten müssen, müssen Sie eine Migration auf die {{site.data.keyword.cloud_notm}}-Plattform durchführen. {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace wurde zurückgezogen und ist nicht geeignet für Kunden, die die Datenschutz-Grundverordnung (DSGVO) 2016/679 der Europäischen Union (EU) einhalten müssen.

## Prozess
{: #process}

Der Migrationsprozess für Ihre {{site.data.keyword.knowledgestudioshort}}-Projekte hängt von Ihrem aktuellen {{site.data.keyword.IBM_notm}} Marketplace-Abonnement ab, wie in der folgenden Tabelle dargestellt.

| Abonnement | Migrationsprozess | Details |
|------|-------------------|--------------------|
| Standardplan mit Self-Service-Abonnement | Instanz und Daten werden vom Kunden migriert. | Migrieren Sie so schnell wie möglich, um Zugriff auf die aktuelle Version von {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud_notm}} zu erhalten. | Standardplan mit Abonnementvertrag | {{site.data.keyword.IBM_notm}} migriert den Abonnementvertrag. Der Kunde migriert die Instanz und die Daten. | Wenden Sie sich an Ihren zuständigen {{site.data.keyword.IBM_notm}} Kundenbeauftragten oder an [{{site.data.keyword.cloud_notm}} Sales ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). |
| Premium-Plan mit Abonnementvertrag | {{site.data.keyword.IBM_notm}} migriert den Abonnementvertrag. {{site.data.keyword.IBM_notm}} migriert die Instanz und die Daten. | Wenden Sie sich an Ihren zuständigen {{site.data.keyword.IBM_notm}} Kundenbeauftragten oder an [{{site.data.keyword.cloud_notm}} Sales ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). |
{: caption="Tabelle 1. Prozess und Zeitplan für die {{site.data.keyword.knowledgestudioshort}}-Migration von {{site.data.keyword.IBM_notm}} Marketplace auf {{site.data.keyword.cloud_notm}}" caption-side="top"}

## Self-Migration von Standardplaninstanzen
{: migratestandard}

Wenn Sie über einen Standardplan verfügen, führen Sie die folgenden Schritte aus, um Ihre Instanz von {{site.data.keyword.IBM_notm}} Marketplace auf {{site.data.keyword.cloud_notm}} zu migrieren:

1. Wenn Sie noch nicht über ein {{site.data.keyword.cloud_notm}}-Konto verfügen, registrieren Sie sich unter [{{site.data.keyword.cloud_notm}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/registration/){: new_window} mithilfe Ihrer {{site.data.keyword.ibmid}} in {{site.data.keyword.IBM_notm}} Marketplace.

   Ihre {{site.data.keyword.ibmid}} ist die ID, die Sie für die Anmeldung bei {{site.data.keyword.knowledgestudioshort}} in {{site.data.keyword.IBM_notm}} Marketplace verwenden.

2. Melden Sie sich bei [{{site.data.keyword.cloud_notm}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}){: new_window} an.
3. Wenn Ihr {{site.data.keyword.cloud_notm}}-Konto ein Lite-Konto ist, führen Sie ein Upgrade auf ein gebührenpflichtiges Konto durch. Weitere Informationen zu den Typen von gebührenpflichtigen Konten finden Sie unter [Kontotypen ![External link icon](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/docs/account/index.html){: new_window}.
4. Erstellen Sie in der [{{site.data.keyword.cloud_notm}}-Konsole ![External link icon](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/catalog/services/knowledge-studio){: new_window} einen {{site.data.keyword.knowledgestudioshort}}-Standardplan.
5. Folgen Sie den Anweisungen in der Anzeige, um anzugeben, dass Sie eine Instanz von {{site.data.keyword.IBM_notm}} Marketplace auf {{site.data.keyword.cloud_notm}} migrieren möchten.
6. Wenn Sie mehr als eine Instanz migrieren möchten, wiederholen Sie den Prozess.

## Migration von Premium-Planinstanzen
{: migratesubscription}

Wenn Sie über einen {{site.data.keyword.knowledgestudioshort}}-Premium-Plan verfügen, wenden Sie sich an Ihren zuständigen {{site.data.keyword.IBM_notm}} Kundenbeauftragten oder an [{{site.data.keyword.cloud_notm}} Sales ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). Sobald das Abonnement auf {{site.data.keyword.cloud_notm}} migriert ist, werden Ihre Daten von IBM entsprechend dem zwischen Ihnen und {{site.data.keyword.IBM_notm}} vereinbarten Zeitplan migriert.
