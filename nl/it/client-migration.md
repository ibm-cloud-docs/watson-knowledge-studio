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

Questa documentazione è per {{site.data.keyword.knowledgestudiofull}} su {{site.data.keyword.cloud}}. Per visualizzare la documentazione della versione precedente di {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace, [fai clic su questo link ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/docs/services/knowledge-studio/client-migration.html){: new_window}.
{: tip}

# Migrazione a IBM Cloud
{: #migrate}

Il 18 dicembre 2017, IBM ha lanciato {{site.data.keyword.knowledgestudiofull}} su {{site.data.keyword.cloud_notm}}, che segna l'inizio del processo di migrazione di tutte le istanze {{site.data.keyword.knowledgestudioshort}} dall'{{site.data.keyword.IBM_notm}} Marketplace alla piattaforma [{{site.data.keyword.cloud_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/blogs/bluemix/2017/12/watson-knowledge-studio-ibm-cloud/){: new_window}.
{: shortdesc}

**Nota**: {{site.data.keyword.knowledgestudioshort}} su {{site.data.keyword.cloud_notm}} utilizza il termine _spazio di lavoro_, mentre {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace utilizza _progetto_. La funzionalità è la stessa. È diversa soltanto la terminologia.

**Attenzione**: se devi essere conforme con il GDPR, devi eseguire la migrazione alla piattaforma {{site.data.keyword.cloud_notm}}. {{site.data.keyword.knowledgestudioshort}} sull'{{site.data.keyword.IBM_notm}} Marketplace è stato ritirato e non è adatto ai clienti che richiedono la conformità con il Regolamento generale sulla protezione dei dati dell'Unione Europea (GDPR) (EU) 2016/679.

## Processo 
{: #process}

Il processo di migrazione dei tuoi progetti {{site.data.keyword.knowledgestudioshort}} dipende dalla tua sottoscrizione all'{{site.data.keyword.IBM_notm}} Marketplace, come illustrato nella seguente tabella.

| Sottoscrizione | Processo di migrazione | Dettagli |
|------|-------------------|--------------------|
| Piano standard con una sottoscrizione self-service  | Il cliente migra l'istanza e i dati | Migrare il prima possibile per ottenere l'accesso alla versione più aggiornata di {{site.data.keyword.knowledgestudioshort}} su {{site.data.keyword.cloud_notm}}.
| Piano standard con un contratto di sottoscrizione | {{site.data.keyword.IBM_notm}} migra il contratto di sottoscrizione. Il cliente migra l'istanza e i dati. | Contatta il tuo rappresentante dell'account designato {{site.data.keyword.IBM_notm}} o i [rappresentanti delle vendite {{site.data.keyword.cloud_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). |
| Piano premium con contratto di sottoscrizione | {{site.data.keyword.IBM_notm}} migra il contratto di sottoscrizione. {{site.data.keyword.IBM_notm}} migra l'istanza e i dati. | Contatta il tuo rappresentante dell'account designato {{site.data.keyword.IBM_notm}} o i [rappresentanti delle vendite {{site.data.keyword.cloud_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). |
{: caption="Tabella 1. Processo e pianificazione per migrare {{site.data.keyword.knowledgestudioshort}} dal {{site.data.keyword.IBM_notm}} Marketplace a {{site.data.keyword.cloud_notm}}" caption-side="top"}

## Migrazione automatica delle istanze del piano standard
{: migratestandard}

Se disponi di un piano standard, completa la seguente procedura per migrare le tue istanze dall'{{site.data.keyword.IBM_notm}} Marketplace a {{site.data.keyword.cloud_notm}}:

1. Se non hai un account {{site.data.keyword.cloud_notm}}, registrati su [{{site.data.keyword.cloud_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/registration/){: new_window} utilizzando il tuo {{site.data.keyword.ibmid}} dal {{site.data.keyword.IBM_notm}} Marketplace.

   Il tuo {{site.data.keyword.ibmid}} è l'ID che utilizzi per accedere a {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace.

2. Accedi a [{{site.data.keyword.cloud_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net){: new_window}.
3. Se il tuo account {{site.data.keyword.cloud_notm}} è un account Lite, esegui l'upgrade a un piano a pagamento. Per ulteriori informazioni sui tipi di account a pagamento, consulta [Account types ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/docs/account/index.html){: new_window}.
4. Dalla console [{{site.data.keyword.cloud_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/catalog/services/knowledge-studio){: new_window}, crea un piano standard di {{site.data.keyword.knowledgestudioshort}}.
5. Segui le istruzioni nella schermata, che indicano che desideri migrare un'istanza dall'{{site.data.keyword.IBM_notm}} Marketplace a {{site.data.keyword.cloud_notm}}.
6. Se devi migrare più di una istanza, ripeti il processo.

## Migrazione delle istanze del piano premium
{: migratesubscription}

Se hai un piano premium {{site.data.keyword.knowledgestudioshort}}, contatta il tuo rappresentante dell'account designato {{site.data.keyword.IBM_notm}} o i [rappresentanti delle vendite {{site.data.keyword.cloud_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). Dopo che la sottoscrizione è stata migrata a {{site.data.keyword.cloud_notm}}, i tuoi dati saranno migrati da IBM in base a una pianificazione che è stata negoziata tra te e {{site.data.keyword.IBM_notm}}.
