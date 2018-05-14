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

Questa documentazione è per {{site.data.keyword.knowledgestudiofull}} su {{site.data.keyword.cloud}}. Per visualizzare la documentazione della versione precedente di {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace, [fai clic su questo link ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/docs/services/knowledge-studio/client-migration.html){: new_window}.
{: tip}

# Migrazione a IBM Cloud
{: #migrate}

Il 18 dicembre 2017, IBM ha lanciato {{site.data.keyword.knowledgestudiofull}} su {{site.data.keyword.cloud_notm}}, che segna l'inizio del processo di migrazione di tutte le istanze {{site.data.keyword.knowledgestudioshort}} dal {{site.data.keyword.IBM_notm}} Marketplace a {{site.data.keyword.cloud_notm}}.
{: shortdesc}

**Nota**: {{site.data.keyword.knowledgestudioshort}} su {{site.data.keyword.cloud_notm}} utilizza il termine _spazio di lavoro_, mentre {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace utilizza _progetto_. La funzionalità è la stessa. È diversa soltanto la terminologia.

## Processo e pianificazione
{: #process}

La pianificazione e il processo di migrazione dei tuoi progetti {{site.data.keyword.knowledgestudioshort}} dipende dal tuo piano dei prezzi [ corrente sul {{site.data.keyword.IBM_notm}} Marketplace ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/us-en/marketplace/supervised-machine-learning/purchase#product-header-top){: new_window} e sul tipo di account, come illustrato nella seguente tabella:

| Piano e account | Processo di migrazione | Pianificazione della migrazione |
|------|-------------------|--------------------|
| Piano gratuito | Il cliente migra l'istanza e i dati | Le migrazioni devono essere completate entro il 1 febbraio 2018. Il 2 febbraio 2018, tutti i piani gratuiti nel {{site.data.keyword.IBM_notm}} Marketplace saranno eliminati, inclusi i dati del progetto associati. |
| Piano standard con account Pagamento a consumo | Il cliente migra l'istanza e i dati | Le migrazioni devono essere completate entro il 29 giugno 2018. Il 30 giugno 2018, tutti i piani standard con account Pagamento a consumo nel {{site.data.keyword.IBM_notm}} Marketplace saranno eliminati, inclusi i dati del progetto associati.
| Piano standard con contratto | Il cliente migra l'istanza e i dati. {{site.data.keyword.IBM_notm}} rinnova il contratto. | Le migrazioni devono essere completate entro il 29 giugno 2018. Contatta il tuo rappresentante dell'account designato {{site.data.keyword.IBM_notm}} o i [rappresentanti delle vendite {{site.data.keyword.cloud_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). |
| Piano premium con contratto | {{site.data.keyword.IBM_notm}} migra l'istanza e i dati. {{site.data.keyword.IBM_notm}} rinnova il contratto. | Le migrazioni devono essere completate entro il 29 giugno 2018. Contatta il tuo rappresentante dell'account designato {{site.data.keyword.IBM_notm}} o i [rappresentanti delle vendite {{site.data.keyword.cloud_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). |
{: caption="Tabella 1. Processo e pianificazione per migrare {{site.data.keyword.knowledgestudioshort}} dal {{site.data.keyword.IBM_notm}} Marketplace a {{site.data.keyword.cloud_notm}}" caption-side="top"}

## Migrazione di piani gratuiti
{: migratefree}

Se hai un piano gratuito {{site.data.keyword.knowledgestudioshort}}, completa la seguente procedura per migrare i tuoi progetti e istanza dal {{site.data.keyword.IBM_notm}} Marketplace a {{site.data.keyword.cloud_notm}}:

1. Se non hai un account {{site.data.keyword.cloud_notm}}, registrati su [{{site.data.keyword.cloud_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://ibm.biz/wks_cloud){: new_window} utilizzando il tuo {{site.data.keyword.ibmid}} dal {{site.data.keyword.IBM_notm}} Marketplace.

   Il tuo {{site.data.keyword.ibmid}} è l'ID che utilizzi per accedere a {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace.

1. Accedi a [{{site.data.keyword.cloud_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/dashboard/apps/){: new_window}.
1. Se non hai un'istanza {{site.data.keyword.knowledgestudioshort}} in {{site.data.keyword.cloud_notm}}, creane una nella pagina del catalogo [{{site.data.keyword.cloud_notm}} {{site.data.keyword.knowledgestudioshort}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/catalog/services/knowledge-studio){: new_window}.
1. Segui il processo di [backup e ripristino](/docs/services/watson-knowledge-studio/backup-restore.html) per migrare manualmente i tuoi progetti dall'istanza del {{site.data.keyword.IBM_notm}} Marketplace a quella in {{site.data.keyword.cloud_notm}}.

  **Nota**: se hai un modello che è già stato distribuito e pensi di eliminare lo spazio di lavoro dopo il backup, ritira il modello dalla distribuzione. Puoi ricreare e ridistribuire il modello dopo il ripristino dello spazio di lavoro dal backup. Per informazioni sui modelli di distribuzione, consulta [Annullamento della distribuzione dei modelli di machine learning](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) e [Annullamento della distribuzione dei modelli basati sulla regola](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model).

## Migrazione dei piani standard per gli account Pagamento a consumo
{: migratepaygo}

Se hai un piano standard e un account [Pagamento a consumo ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/docs/pricing/billable.html){: new_window}, completa la seguente procedura per migrare i tuoi progetti e istanza dal {{site.data.keyword.IBM_notm}} Marketplace a {{site.data.keyword.cloud_notm}}:

1. Se non hai un account {{site.data.keyword.cloud_notm}}, registrati su [{{site.data.keyword.cloud_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/){: new_window} utilizzando il tuo {{site.data.keyword.ibmid}} dal {{site.data.keyword.IBM_notm}} Marketplace.

   Il tuo {{site.data.keyword.ibmid}} è l'ID che utilizzi per accedere a {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace.

1. Accedi a [{{site.data.keyword.cloud_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/dashboard/apps/){: new_window}.
1. Se non hai un'istanza {{site.data.keyword.knowledgestudioshort}} in {{site.data.keyword.cloud_notm}}, creane una nella pagina del catalogo [{{site.data.keyword.cloud_notm}} {{site.data.keyword.knowledgestudioshort}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/catalog/services/knowledge-studio){: new_window}.
1. Segui il processo di [backup e ripristino](/docs/services/watson-knowledge-studio/backup-restore.html) per migrare manualmente i tuoi progetti dall'istanza del {{site.data.keyword.IBM_notm}} Marketplace a quella in {{site.data.keyword.cloud_notm}}.

  **Nota**: se hai un modello che è già stato distribuito e pensi di eliminare lo spazio di lavoro dopo il backup, ritira il modello dalla distribuzione. Puoi ricreare e ridistribuire il modello dopo il ripristino dello spazio di lavoro dal backup. Per informazioni sui modelli di distribuzione, consulta [Annullamento della distribuzione dei modelli di machine learning](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) e [Annullamento della distribuzione dei modelli basati sulla regola](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model).

## Migrazione dei piani standard per gli account con contratto 
{: migratecontract}

Se hai un piano standard {{site.data.keyword.knowledgestudioshort}} con contratto, completa la seguente procedura per rinnovare il tuo contratto e migrare i tuoi progetti e istanza dal {{site.data.keyword.IBM_notm}} Marketplace a {{site.data.keyword.cloud_notm}}:

1. Per rinnovare il tuo contratto, contatta il tuo rappresentante dell'account designato {{site.data.keyword.IBM_notm}} o i [rappresentanti delle vendite {{site.data.keyword.cloud_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration).
1. Dopo aver rinnovato il tuo contratto per {{site.data.keyword.cloud_notm}}, accedi a [{{site.data.keyword.cloud_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/dashboard/apps/){: new_window}.
1. Se non hai un'istanza {{site.data.keyword.knowledgestudioshort}} in {{site.data.keyword.cloud_notm}}, creane una nella pagina del catalogo [{{site.data.keyword.cloud_notm}} {{site.data.keyword.knowledgestudioshort}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/catalog/services/knowledge-studio){: new_window}.
1. Segui il processo di [backup e ripristino](/docs/services/watson-knowledge-studio/backup-restore.html) per migrare manualmente i tuoi progetti dall'istanza del {{site.data.keyword.IBM_notm}} Marketplace a quella in {{site.data.keyword.cloud_notm}}.

  **Nota**: se hai un modello che è già stato distribuito e pensi di eliminare lo spazio di lavoro dopo il backup, ritira il modello dalla distribuzione. Puoi ricreare e ridistribuire il modello dopo il ripristino dello spazio di lavoro dal backup. Per informazioni sui modelli di distribuzione, consulta [Annullamento della distribuzione dei modelli di machine learning](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) e [Annullamento della distribuzione dei modelli basati sulla regola](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model).

## Migrazione dei piani premium per gli account con contratto 
{: migratecontract}

Se hai un piano premium {{site.data.keyword.knowledgestudioshort}} con contratto, contatta il tuo rappresentante dell'account designato {{site.data.keyword.IBM_notm}} o i [rappresentanti delle vendite {{site.data.keyword.cloud_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). Una volta che è stato rinnovato il contratto con {{site.data.keyword.cloud_notm}}, i tuoi dati saranno migrati da IBM in base a una pianificazione che è stata negoziata tra te e {{site.data.keyword.cloud_notm}}.
