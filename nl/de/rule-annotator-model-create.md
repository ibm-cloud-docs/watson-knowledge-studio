---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-19"

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

Diese Dokumentation bezieht sich auf {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Die Dokumentation für die Vorgängerversion {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace kann über [diesen Link ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/docs/services/knowledge-studio/rule-annotator-model-create.html){: new_window} aufgerufen werden.
{: tip}

# Regelbasiertes Modell erstellen
{: #wks_rule_train}

Nachdem Sie Regeln definiert haben, können Sie ein regelbasiertes Modell erstellen.
{: shortdesc}

## Vorgehensweise
{: #wks_rule_train_procedure}

Führen Sie die folgenden Schritte aus, um ein regelbasiertes Modell zu erstellen:

1. Melden Sie sich als {{site.data.keyword.knowledgestudioshort}}-Administrator oder -Projektleiter an und wählen Sie Ihren Arbeitsbereich aus.
1. Wählen Sie die Registerkarte **Regelbasiertes Modell** > **Versionen** > **Regelbasiertes Modell** aus.
2. Klicken Sie auf **Entitätstypen und -klassen zuordnen**.
3. Ordnen Sie die Entitätstypen aus Ihrem Typsystem mindestens einer Klasse zu, die Sie zum Definieren von Regeln verwendet haben.

  Nach dem Zuordnen der Entitätstypen können Sie das [regelbasierte Modell bereitstellen](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html) oder beim Erstellen eines Modells für maschinelles Lernen zum [Vorannotieren von Dokumenten](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotrule) verwenden.

## Regelbasiertes Modell löschen
{: #wks_rule_delete_model}

Ein regelbasiertes Modell kann nicht gelöscht werden.

Sie können den Arbeitsbereich löschen, der zum Entwickeln des regelbasierten Modells verwendet wurde, aber Sie können das Modell an sich nicht löschen. Das Löschen eines Modells ist keine empfehlenswerte Vorgehensweise. Erstellen Sie stattdessen die Regeln neu, die für das Modell definiert wurden. Durch direktes Bearbeiten der Regeln kann das Verhalten des regelbasierten Modells geändert werden.
