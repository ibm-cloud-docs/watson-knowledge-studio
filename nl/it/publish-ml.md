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

Questa documentazione è per {{site.data.keyword.knowledgestudiofull}} su {{site.data.keyword.cloud}}. Per visualizzare la documentazione della versione precedente di {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace, [fai clic su questo link ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/docs/services/knowledge-studio/publish-ml.html){: new_window}.
{: tip}

# Utilizzo del modello di machine learning
{: #publish-ml}

Utilizza un modello di machine learning che hai preparato con {{site.data.keyword.knowledgestudioshort}} rendendolo disponibile ad altre applicazioni {{site.data.keyword.watson}}.
{: shortdesc}

Puoi distribuire o esportare un modello di machine learning. Può essere utilizzato solo un dizionario o un pre-annotatore {{site.data.keyword.nlushort}} per pre-annotare i documenti in {{site.data.keyword.knowledgestudioshort}}.

Prima che un modello possa essere distribuito per l'utilizzo a un servizio, devi avere una sottoscrizione al servizio. I servizi {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} sono ospitati in {{site.data.keyword.Bluemix_short}}, una piattaforma cloud di {{site.data.keyword.IBM_notm}}. Consulta [What is {{site.data.keyword.Bluemix_notm}}? ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.ng.bluemix.net/docs/overview/whatisbluemix.html){: new_window} per ulteriori informazioni sulla piattaforma. Per sottoscrivere uno dei servizi {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}}, crea un account dal sito web [{{site.data.keyword.Bluemix_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.ng.bluemix.net/){: new_window}.

Per alcuni servizi, devi conoscere i dettagli sull'istanza del servizio a cui pensi di eseguire la distribuzione, come il nome dell'istanza del servizio e dello spazio {{site.data.keyword.Bluemix_notm}}. Le informazioni sul nome dell'istanza del servizio e dello spazio sono disponibili dalla pagina dei servizi {{site.data.keyword.Bluemix_notm}}.

Puoi anche pre-annotare i nuovi documenti con il modello di machine learning. Consulta [Pre-annotazione dei documenti con il modello di machine learning](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotsire) per i dettagli.

## Distribuzione di un modello di machine learning a IBM Watson Discovery
{: #wks_madiscovery}

Quando sei soddisfatto delle prestazioni del modello, puoi distribuirne una versione a {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}. Questa funzione abilita le tue applicazioni ad utilizzare il modello di machine learning distribuito per arricchire le informazioni dettagliate che ottieni dai tuoi dati con il riconoscimento dei concetti e delle relazioni che sono rilevanti nel tuo dominio.

### Prima di cominciare
{: #wks_madiscovery_prereqs}

Devi avere l'ascesso amministrativo all'istanza del servizio {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}} e conoscere i nomi dell'istanza e dello spazio {{site.data.keyword.Bluemix_notm}} ad esso associati.

### Informazioni su quest'attività
{: #wks_madiscovery_about}

Quando distribuisci il modello di machine learning, seleziona la versione che vuoi distribuire.

### Procedura
{: #wks_madiscovery_procedure}

Per distribuire un modello di machine learning a {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}, completa la seguente procedura:

1. Accedi come amministratore o gestore del progetto {{site.data.keyword.knowledgestudioshort}} e seleziona il tuo spazio di lavoro.
1. Seleziona **Machine Learning Model** > **Versions**.
1. Scegli la versione del modello che vuoi distribuire.

    Se esiste solo una versione funzionante del modello, crea un'istantanea del modello corrente. Queste versioni del modello ti abilitano a distribuire una versione mentre continui a migliorare la versione corrente. L'opzione di distribuzione non viene visualizzata finché non crei almeno una versione.

    **Nota**: ogni versione può essere distribuita ad una sola istanza del servizio. Se vuoi distribuire lo stesso modello a più di un'istanza, crea una versione per ciascuna istanza.

1. Fai clic su **Deploy**, scegli di distribuirlo a {{site.data.keyword.discoveryshort}} e poi fai clic su **Next**.
1. Seleziona l'istanza e lo spazio {{site.data.keyword.Bluemix_notm}}. Se necessario, seleziona una regione differente.
1. Fai clic su **Deploy**.
1. Il processo di distribuzione potrebbe richiedere alcuni minuti. Per controllare lo stato della distribuzione, fai clic su **Status** nella scheda **Versions** accanto alla versione che hai distribuito.

    Se il modello sta ancora venendo distribuito, lo stato indica "publishing". Dopo il completamento della distribuzione, lo stato viene modificato con "available" se è ha avuto esito positivo o con "error" se si sono verificati dei problemi.

    Quando disponibile, prendi nota dell'ID del modello (model_id). Fornirai questo ID al servizio {{site.data.keyword.discoveryshort}} per abilitarlo ad utilizzare il tuo modello personalizzato.

### Operazioni successive
{: #wks_madiscovery_next}

Per utilizzare il modello distribuito, devi fornire l'ID del modello quando viene richiesto durante il processo di configurazione del miglioramento del servizio {{site.data.keyword.discoveryshort}}. Per ulteriori dettagli, consulta la [documentazione del servizio {{site.data.keyword.discoveryshort}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/docs/services/discovery/integrate-wks.html){: new_window}.

## Distribuzione di un modello di machine learning a IBM Watson Natural Language Understanding
{: #wks_manlu}

Quando sei soddisfatto delle prestazioni del modello, puoi distribuirne una versione a {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.nlushort}}. Questa funzione abilita le tue applicazioni ad utilizzare il modello di machine learning distribuito per analizzare le funzioni semantiche dell'input di testo, incluse le entità e le relazioni.

### Prima di cominciare
{: #wks_manlu_prereqs}

Devi avere un servizio {{site.data.keyword.nlushort}} a cui distribuire. E devi conoscere i nomi dell'istanza e dello spazio {{site.data.keyword.Bluemix_notm}} associati al servizio. Se non ricordi i nomi dell'istanza e dello spazio, trovali accedendo a {{site.data.keyword.Bluemix_notm}}. Se non hai un account {{site.data.keyword.Bluemix_notm}}, registrane uno.

### Informazioni su quest'attività
{: #wks_manlu_about}

Quando distribuisci il modello di machine learning, seleziona la versione che vuoi distribuire.

### Procedura
{: #wks_manlu_procedure}

Per distribuire un modello di machine learning al servizio  {{site.data.keyword.nlushort}}, completa la seguente procedura:

1. Accedi come amministratore o gestore del progetto {{site.data.keyword.knowledgestudioshort}} e seleziona il tuo spazio di lavoro.
1. Seleziona **Machine Learning Model** > **Versions**.
1. Scegli la versione del modello che vuoi distribuire.

    Se esiste solo una versione funzionante del modello, crea un'istantanea del modello corrente. Queste versioni del modello ti abilitano a distribuire una versione mentre continui a migliorare la versione corrente. L'opzione di distribuzione non viene visualizzata finché non crei almeno una versione.

    **Nota**: ogni versione può essere distribuita ad una sola istanza del servizio. Se vuoi distribuire lo stesso modello a più di un'istanza, crea una versione per ciascuna istanza.

1. Fai clic su **Deploy**, scegli di distribuirlo a {{site.data.keyword.nlushort}} e poi fai clic su **Next**.
1. Seleziona l'istanza e lo spazio {{site.data.keyword.Bluemix_notm}}. Se necessario, seleziona una regione differente.
1. Fai clic su **Deploy**.
1. Il processo di distribuzione potrebbe richiedere alcuni minuti. Per controllare lo stato della distribuzione, fai clic su **Status** nella scheda **Versions** accanto alla versione che hai distribuito. Se il modello sta ancora venendo distribuito, lo stato indica "publishing". Dopo il completamento della distribuzione, lo stato viene modificato con "available" se è ha avuto esito positivo o con "error" se si sono verificati dei problemi.

    Quando disponibile, prendi nota dell'ID del modello (model_id). Fornirai questo ID al servizio {{site.data.keyword.nlushort}} per abilitarlo ad utilizzare il tuo modello personalizzato.

### Operazioni successive
{: #wks_manlu_next}

Per utilizzare il modello distribuito, devi specificare l'ID del modello del tuo modello personalizzato nel parametro `entities.model`.

Puoi utilizzare il modello con la richiesta {{site.data.keyword.nlushort}} `GET /analyze` per estrarre le seguenti funzioni:

- **entità**

    Il seguente comando trova le entità presenti nella frase che viene passata utilizzando il parametro di testo:

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

    Il servizio restituisce un oggetto JSON delle istanze che trova dei tipi di entità che sono stati definiti nel modello personalizzato:

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

- **relazioni**

    Il seguente comando trova le relazioni presenti nella frase che viene passata utilizzando il parametro di testo:

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

    Il servizio restituisce un oggetto JSON delle istanze che trova dei tipi di relazione che sono stati definiti nel modello personalizzato:

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

Consulta la [documentazione {{site.data.keyword.nlushort}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/docs/services/natural-language-understanding/index.html){: new_window} per ulteriori dettagli.

## Annullamento della distribuzione dei modelli
{: #undeploy-view-model}

Se vuoi annullare la distribuzione di un modello o trovare un ID del modello, consulta la pagina **Deployed Models**.

### Informazioni su quest'attività
{: #wks_undeploy_about}

Ciò che viene visualizzato nella pagina Deployed Models dipende dalla [regione ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/docs/resources/services_region.html){: new_window} che ospita la tua istanza {{site.data.keyword.knowledgestudioshort}}. Se la regione supporta le istanze gestite dai metodi di gestione dell'accesso [IAM ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/docs/iam/users_roles.html){: new_window} e [Cloud Foundry ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/docs/iam/cfaccess.html){: new_window}, visualizzi una scheda per ogni metodo. I modelli dalle istanze gestite da IAM sono elencate nella scheda **Resource Groups**. I modelli dalle istanze gestite da Cloud Foundry sono elencate nella scheda **Organizations**.

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

## Utilizzo di un modello di machine learning in IBM Watson Explorer
{: #wks_maexport}

Esporta il modello di machine learning preparato in modo che possa essere utilizzato in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.

### Prima di cominciare
{: #wks_maexport_prereqs}

Se scegli di identificare i tipi di relazione e annotarli, devi definire almeno due tipi di relazione e annotare le istanze delle relazioni nel ground truth prima di esportare il modello. Definire e annotare un solo tipo di relazione può causare problemi successivi in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, release 11.0.1.0.

### Informazioni su quest'attività
{: #wks_maexport_about}

Ora che il modello di machine learning è preparato per riconoscere le entità e le relazioni di un determinato dominio, puoi utilizzarlo in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.

Fai clic su [questo link ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.youtube.com/watch?v=1VoS-xczBow&amp;feature=youtu.be){: new_window} per guardare un video di meno di 2 minuti che illustra come esportare un modello e utilizzarlo in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.

### Procedura
{: #wks_maexport_procedure}

Per utilizzare un modello di machine learning in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, completa la seguente procedura.

1. Accedi come amministratore o gestore del progetto {{site.data.keyword.knowledgestudioshort}} e seleziona il tuo spazio di lavoro.
1. Seleziona **Machine Learning Model** > **Versions**.
1. Fai clic su **Export current model**.

    Se hai una sottoscrizione di piano Lite, l'opzione di esportazione non è disponibile. 

    Il modello viene salvato come un file ZIP e ti viene richiesto di scaricarlo.

1. Scarica il file nel tuo sistema locale.
1. Dall'applicazione {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, importa il modello.

    Puoi quindi associare il modello a un modello di machine learning in {{site.data.keyword.watson}} Explorer Content Analytics. Dopo aver eseguito il passo di associazione, quando effettui una ricerca per indicizzazione dei documenti, il modello trova le istanze delle entità e delle relazioni comprese dal tuo modello. Per imparare come importare e configurare in modello in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, consulta la documentazione tecnica che descrive l'integrazione: [http://www.ibm.com/support/docview.wss?uid=swg27048147 ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://www.ibm.com/support/docview.wss?uid=swg27048147){: new_window}.

#### Attività correlate
{: #wks_maexport_related}

[Esportazione dei documenti analizzati da {{site.data.keyword.watson}} Explorer Content Analytics](/docs/services/watson-knowledge-studio/preannotation.html#wks_uimawexca)
