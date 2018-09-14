---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-14"

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

Questa documentazione è per {{site.data.keyword.knowledgestudiofull}} su {{site.data.keyword.cloud}}. Per visualizzare la documentazione della versione precedente di {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace, [fai clic su questo link ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/docs/services/knowledge-studio/rule-annotator-model-use.html){: new_window}.
{: tip}

# Utilizzo del modello basato sulla regola
{: #wks_rule_publish}

Utilizzo di un modello basato sulla regola che hai creato con {{site.data.keyword.knowledgestudioshort}} rendendolo disponibile ad altre applicazioni {{site.data.keyword.watson}}.
{: shortdesc}

**Attenzione:**: puoi distribuire un modello basato sulla regola rendendolo disponibile per l'utilizzo in questi servizi come una funzione [sperimentale](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental).

Prima che un modello possa essere distribuito per l'utilizzo a un servizio, devi avere una sottoscrizione al servizio. I servizi {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} sono ospitati in {{site.data.keyword.Bluemix_notm}}, una piattaforma cloud di {{site.data.keyword.IBM_notm}}. Consulta [What is {{site.data.keyword.Bluemix_notm}}? ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.ng.bluemix.net/docs/overview/whatisbluemix.html){: new_window} per ulteriori informazioni sulla piattaforma. Per sottoscrivere uno dei servizi {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}}, crea un account dal sito web [{{site.data.keyword.Bluemix_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.ng.bluemix.net/){: new_window}.

Per alcuni servizi, devi conoscere i dettagli sull'istanza del servizio a cui pensi di eseguire la distribuzione, come il nome dell'istanza del servizio e dello spazio {{site.data.keyword.Bluemix_notm}}. Le informazioni sul nome dell'istanza del servizio e dello spazio sono disponibili dalla pagina dei servizi {{site.data.keyword.Bluemix_notm}}.

Puoi anche pre-annotare i nuovi documenti con il modello basato sulla regola. Consulta [Pre-annotazione dei documenti con il modello basato sulla regola](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotrule) per i dettagli.

## Distribuzione di un modello basato sulla regola a IBM Watson Discovery
{: #wks_rule_discovery}

Distribuisci il modello per abilitare un'applicazione che utilizza il servizio {{site.data.keyword.discoveryshort}} ad utilizzare il modello basato sulla regola per trovare le entità estratte durante il miglioramento del documento.

**Attenzione**: questa è al momento una funzione del servizio [sperimentale](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental).

### Prima di cominciare
{: #wks_rule_discovery_prereqs}

Devi avere l'ascesso amministrativo all'istanza del servizio {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}} e conoscere i nomi dell'istanza e dello spazio {{site.data.keyword.Bluemix_notm}} ad esso associati.

### Procedura
{: #wks_rule_discovery_procedure}

Per distribuire un modello basato sulla regola a {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}, completa la seguente procedura:

1. Accedi come amministratore o gestore del progetto {{site.data.keyword.knowledgestudioshort}} e seleziona il tuo spazio di lavoro.
1. Seleziona la scheda **Rule-based Model** > **Versions** > **Rule-based Model**.
1. Scegli la versione del modello che vuoi distribuire.

    Se esiste solo una versione funzionante del modello, salva il modello corrente per la distribuzione e fai clic su **Save for Deployment**. Queste versioni del modello ti abilitano a distribuire una versione mentre continui a migliorare la versione corrente. Il salvataggio della versione può richiedere alcuni minuti. L'opzione di distribuzione non viene visualizzata finché non viene creata la versione.

    **Nota**: ogni versione può essere distribuita ad una sola istanza del servizio. Se vuoi distribuire lo stesso modello a più di un'istanza, crea una versione per ciascuna istanza.

1. Fai clic su **Deploy**, scegli di distribuirlo a {{site.data.keyword.discoveryshort}} e poi fai clic su **Next**.
1. Fornisci l'istanza e lo spazio {{site.data.keyword.Bluemix_notm}}. Se necessario, seleziona una regione differente.
1. Fai clic su **Deploy**.
1. Il processo di distribuzione potrebbe richiedere alcuni minuti. Per controllare lo stato della distribuzione, fai clic su **Status** nella scheda **Versions** accanto alla versione che hai distribuito.

    Se il modello sta ancora venendo distribuito, lo stato indica "publishing". Dopo il completamento della distribuzione, lo stato viene modificato con "available" se è ha avuto esito positivo o con "error" se si sono verificati dei problemi.

    Quando disponibile, prendi nota dell'ID del modello (model_id). Fornirai questo ID al servizio {{site.data.keyword.discoveryshort}} per abilitarlo ad utilizzare il tuo modello personalizzato.

### Operazioni successive
{: #wks_rule_discovery_next}

Per utilizzare il modello distribuito, devi fornire l'ID del modello quando viene richiesto durante il processo di configurazione del miglioramento del servizio {{site.data.keyword.discoveryshort}}.

## Distribuzione di un modello basato sulla regola a IBM Watson Natural Language Understanding
{: #wks_rule_nlu}

Distribuisci il modello basato sulla regola per abilitare un'applicazione che utilizza il servizio {{site.data.keyword.nlushort}} ad utilizzare il modello per trovare le entità estratte rilevanti per il tuo dominio.

**Attenzione**: questa è al momento una funzione del servizio [sperimentale](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental).

### Prima di cominciare
{: #wks_rule_prereqs}

Devi avere l'ascesso amministrativo all'istanza del servizio {{site.data.keyword.nlushort}} e conoscere i nomi dell'istanza e dello spazio {{site.data.keyword.Bluemix_notm}} ad esso associati.

### Procedura
{: #wks_rule_procedure}

Per distribuire un modello basato sulla regola a {{site.data.keyword.nlushort}}, completa la seguente procedura:

1. Accedi come amministratore o gestore del progetto {{site.data.keyword.knowledgestudioshort}} e seleziona il tuo spazio di lavoro.
1. Seleziona la scheda **Rule-based Model** > **Versions** > **Rule-based Model**.
1. Scegli la versione del modello che vuoi distribuire.

    Se esiste solo una versione funzionante del modello, salva il modello corrente per la distribuzione e fai clic su **Save for Deployment**. Queste versioni del modello ti abilitano a distribuire una versione mentre continui a migliorare la versione corrente. Il salvataggio della versione può richiedere alcuni minuti. L'opzione di distribuzione non viene visualizzata finché non viene creata la versione.

    **Nota**: ogni versione può essere distribuita ad una sola istanza del servizio. Se vuoi distribuire lo stesso modello a più di un'istanza, crea una versione per ciascuna istanza.

1. Fai clic su **Deploy**, scegli di distribuirlo a {{site.data.keyword.nlushort}} e poi fai clic su **Next**.
1. Fornisci l'istanza e lo spazio {{site.data.keyword.Bluemix_notm}}. Se necessario, seleziona una regione differente.
1. Fai clic su **Deploy**.
1. Il processo di distribuzione potrebbe richiedere alcuni minuti. Per controllare lo stato della distribuzione, fai clic su **Status** nella scheda **Versions** accanto alla versione che hai distribuito.

    Se il modello sta ancora venendo distribuito, lo stato indica "publishing". Dopo il completamento della distribuzione, lo stato viene modificato con "available" se è ha avuto esito positivo o con "error" se si sono verificati dei problemi.

    Quando disponibile, prendi nota dell'ID del modello (model_id). Fornirai questo ID al servizio {{site.data.keyword.nlushort}} per abilitarlo ad utilizzare il tuo modello personalizzato.

### Operazioni successive
{: #wks_rule_next}

Per utilizzare il modello distribuito, devi specificare l'ID del modello del tuo modello personalizzato nel parametro `entities.model`.

Puoi utilizzare il modello con la richiesta {{site.data.keyword.nlushort}} `GET /analyze` per estrarre le entità.

Consulta la [documentazione {{site.data.keyword.nlushort}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/docs/services/natural-language-understanding/index.html){: new_window} per ulteriori dettagli.

## Annullamento della distribuzione dei modelli
{: #undeploy-view-model}

Se vuoi annullare la distribuzione di un modello o trovare un ID del modello, consulta la pagina **Deployed Models**.

### Informazioni su quest'attività
{: #wks_undeploy_about}

Ciò che viene visualizzato nella pagina Deployed Models dipende dalla [regione ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/docs/resources/services_region.html){: new_window} che ospita la tua istanza {{site.data.keyword.knowledgestudioshort}}. Se la regione supporta le istanze gestite dai metodi di gestione dell'accesso [IAM ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/docs/iam/users_roles.html){: new_window} e [Cloud Foundry ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/docs/iam/cfaccess.html){: new_window}, visualizzi una scheda per ogni metodo. I modelli dalle istanze gestite da IAM sono elencate nella scheda **Resource Groups**. I modelli dalle istanze gestite da Cloud Foundry sono elencate nella scheda **Organizations**.

Se la regione supporta le istanze gestite da solo uno dei metodi di gestione dell'accesso, visualizzi solo un elenco di modelli, perché viene applicato solo un metodo di gestione dell'accesso.

### Procedura
{: #wks_deploy_procedure}

Per annullare la distribuzione dei modelli o trovare gli ID del modello:

1. Avvia {{site.data.keyword.knowledgestudioshort}}.
1. Dal menu **Settings** nella barra del menu in alto a destra, seleziona **Manage deployed models**.
1. Dall'elenco di modelli distribuiti, trova il modello che vuoi visualizzare o di cui vuoi annullare la distribuzione.
1. Per annullare la distribuzione di un modello, dall'ultima colonna di tale riga, fai clic su **Undeploy model**.
1. Per trovare l'ID del modello, consulta la colonna **Model ID**.

In alternativa, puoi annullare la distribuzione dei modelli dalle pagine Versions dei modelli basati sulla regola e di machine learning.

## Utilizzo di un modello basato sulla regola in IBM Watson Explorer
{: #wks_rule_export}

Esporta il file PEAR prodotto quando viene creato il modello basato sulla regola in modo che possa essere utilizzato in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.

### Procedura
{: #wks_rule_export_procedure}

Per utilizzare un modello basato sulla regola in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, completa la seguente procedura.

1. Accedi come amministratore o gestore del progetto {{site.data.keyword.knowledgestudioshort}} e seleziona il tuo spazio di lavoro.
1. Seleziona la scheda **Rule-based Model** > **Versions** > **Rule-based Model**.
1. Fai clic su **Export current model**.

    Se hai una sottoscrizione di piano Lite, l'opzione di esportazione non è disponibile.

    Il modello viene salvato come un file PEAR e ti viene richiesto di scaricarlo. Un file PEAR (Processing Engine ARchive) è il formato di impacchettamento standard UIMA per i componenti UIMA. Il modello viene salvato nel formato PEAR in modo che possa venire distribuito e riutilizzato nelle applicazioni UIMA.

1. Scarica il file nel tuo sistema locale.
1. Dall'applicazione {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, importa il file PEAR.
