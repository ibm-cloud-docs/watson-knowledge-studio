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

Questa documentazione è per {{site.data.keyword.knowledgestudiofull}} su {{site.data.keyword.cloud}}. Per visualizzare la documentazione della versione precedente di {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace, [fai clic su questo link ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/docs/services/knowledge-studio/index.html){: new_window}.
{: tip}

# Informazioni
{: #wks_overview_full}

Utilizza {{site.data.keyword.knowledgestudiofull}} per creare un modello di machine learning che comprende le sfumature linguistiche, il significato e le relazioni specifiche del tuo settore o per creare un modello basato sulla regola che trova le entità nei documenti basati sulle regole che definisci.
{: shortdesc}

Per diventare un esperto in materia per un determinato dominio o un settore, {{site.data.keyword.watson}} deve essere preparato. Puoi facilitare l'attività di preparazione di {{site.data.keyword.watson}} con {{site.data.keyword.knowledgestudioshort}}.

## Crea un modello di machine learning

{{site.data.keyword.knowledgestudioshort}} fornisce strumenti di facile utilizzo per l'annotazione della letteratura del dominio non strutturata e utilizza queste annotazioni per creare un modello di machine learning personalizzato che comprende la lingua del dominio. L'accuratezza del modello migliora attraverso la verifica iterativa, infine determinando un algoritmo che può imparare dai modelli e che li visualizza e riconosce in raccolte molto grandi di nuovi documenti. Puoi distribuire il modello di machine learning finito ad altre soluzioni cognitive e offerte basate sul cloud di {{site.data.keyword.watson}} e estrarre le citazioni di relazioni e entità, incluse le coreferenze dell'entità.

![Panoramica del processo per creare un modello di machine learning](images/wks-ovw-anno.svg "Mostra il processo di creazione di un modello di machine learning che può trovare le entità e le relazioni nei nuovi documenti.") Figura 1. Panoramica del processo per creare un modello di machine learning

1. In base a un serie di documenti di origine specifici del dominio, il team crea un sistema tipo che definisce i tipi di entità e di relazione per le informazioni di interesse dell'applicazione che utilizzerà il modello.
1. Un gruppo di due o più annotatori umani annota una piccola serie di documenti di origine per etichettare le parole che rappresentano i tipi di entità, per identificare i tipi di relazione dove il testo identifica le relazioni tra le citazioni dell'entità e per definire le coreferenze, che identificano le citazioni differenti che fanno riferimento alla stessa cosa, ovvero, la stessa entità. Tutte le incongruenze nell'annotazione vengono risolte e viene creata una serie ottimale di documenti annotati, che forma il ground truth.
1. {{site.data.keyword.knowledgestudioshort}} utilizza il ground truth per preparare un modello.
1. Il modello preparato viene utilizzato per trovare le entità, le relazioni e le coreferenze nei nuovi e mai visti prima documenti.

Consulta [Creazione di un modello di machine learning](/docs/services/watson-knowledge-studio/ml-annotator.html) per ulteriori dettagli.

## Crea un modello basato sulla regola

{{site.data.keyword.knowledgestudioshort}} fornisce un editor delle regole che semplifica il processo per trovare e acquisire i modelli comuni nei tuoi documenti come regole. Puoi quindi creare un modello che riconosce i modelli di regole e lo distribuisce per l'utilizzo con altri servizi.

Consulta [Creazione di un modello basato sulla regola](/docs/services/watson-knowledge-studio/rule-annotator.html) per ulteriori dettagli.

## Integrazione dei servizi Watson
{: #wks_watsoninteg}

Condividi i modelli e le risorse del dominio tra {{site.data.keyword.knowledgestudiofull}} a altri servizi {{site.data.keyword.watson}}.

Utilizza {{site.data.keyword.knowledgestudioshort}} per eseguire le seguenti attività:

- Iniziare l'annotazione utilizzando il servizio {{site.data.keyword.nlushort}} per trovare e annotare automaticamente le entità nei tuoi documenti. Quando gli annotatori umani iniziano ad annotare i documenti, possono visualizzare le annotazioni che sono già state fatte dal servizio e revisionarle e aggiungerle. Consulta [Pre-annotazione dei documenti con {{site.data.keyword.nlushort}}](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotnlu) per i dettagli.
- Caricare i documenti analizzati che sono nel [formato UIMA CAS XMI](/docs/services/watson-knowledge-studio/preannotation.html#wks_uimaweximport). Ad esempio, puoi caricare i file UIMA CAS XMI che sono stati esportati dalle raccolte di analisi del contenuto {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer o da [{{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer Content Analytics Studio](/docs/services/watson-knowledge-studio/preannotation.html#wks_uimawexstudio).
- Distribuire un modello [machine learning](/docs/services/watson-knowledge-studio/publish-ml.html#wks_madiscovery) o [basato sulla regola](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#wks_rule_discovery) da utilizzare con il servizio {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}.
- Distribuire un modello [machine learning](/docs/services/watson-knowledge-studio/publish-ml.html#wks_manlu) o [basato sulla regola](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#wks_rule_nlu) da utilizzare con il servizio {{site.data.keyword.nlushort}}.
- [Esportare un modello di machine learning](/docs/services/watson-knowledge-studio/publish-ml.html#wks_maexport) da utilizzare in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.
- [Esportare un file PEAR del modello basato sulla regola](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#wks_rule_export) da utilizzare in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.
