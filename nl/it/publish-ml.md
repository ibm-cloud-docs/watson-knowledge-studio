---

copyright:
  years: 2015, 2018
lastupdated: "2018-04-04"

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

Questa documentazione è per {{site.data.keyword.knowledgestudiofull}} su {{site.data.keyword.cloud}}. Per visualizzare la documentazione della versione precedente di {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace, [fai clic su questo link ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/docs/services/knowledge-studio/publish-ml.html){: new_window}.
{: tip}

# Utilizzo del modello di machine learning
{: #publish-ml}

Utilizza un modello di machine learning che hai preparato con {{site.data.keyword.knowledgestudioshort}} rendendolo disponibile ad altre applicazioni {{site.data.keyword.watson}}.
{: shortdesc}

Puoi distribuire o esportare un modello di machine learning. Può essere utilizzato solo un dizionario o un pre-annotatore {{site.data.keyword.nlushort}} per pre-annotare i documenti in {{site.data.keyword.knowledgestudioshort}}.

Prima che un modello possa essere distribuito per l'utilizzo a un servizio, devi avere una sottoscrizione al servizio. I servizi {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} sono ospitati in {{site.data.keyword.Bluemix_short}}, una piattaforma cloud di {{site.data.keyword.IBM_notm}}. Consulta [What is {{site.data.keyword.Bluemix_notm}}? ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.ng.bluemix.net/docs/overview/whatisbluemix.html){: new_window} per ulteriori informazioni sulla piattaforma. Per sottoscrivere uno dei servizi {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}}, crea un account dal sito web [{{site.data.keyword.Bluemix_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.ng.bluemix.net/){: new_window}.

Per alcuni servizi, devi conoscere i dettagli sull'istanza del servizio a cui pensi di eseguire la distribuzione, come il nome dell'istanza del servizio e dello spazio {{site.data.keyword.Bluemix_notm}}. Le informazioni sul nome dell'istanza del servizio e dello spazio sono disponibili dalla pagina dei servizi {{site.data.keyword.Bluemix_notm}}.

Puoi anche pre-annotare i nuovi documenti con il modello di machine learning. Consulta [Pre-annotazione dei documenti con un modello di machine learning](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotsire) per i dettagli.

## Distribuzione di un modello di machine learning a AlchemyLanguage
{: #wks_mabluemix}

Quando sei soddisfatto delle prestazioni del modello, puoi distribuirne una versione a {{site.data.keyword.IBM_notm}} {{site.data.keyword.alchemylanguageshort}}. Questa funzione, che ti richiede di fornire una chiave di accesso {{site.data.keyword.alchemyapishort}}, abilita le tue applicazioni ad utilizzare il modello di machine learning distribuito per annotare i documenti nel tuo dominio.

### Prima di cominciare

Devi avere un piano avanzato del servizio {{site.data.keyword.alchemylanguageshort}} per poter distribuire ed utilizzare il modello.
>Nota: il servizio {{site.data.keyword.alchemylanguageshort}} è obsoleto. Non puoi distribuire questo modello al servizio se non hai un piano esistente.

### Informazioni su quest'attività

Quando distribuisci il modello di machine learning, seleziona la versione che vuoi distribuire. Per distribuire questo servizio, devi avere una chiave di accesso da {{site.data.keyword.IBM_notm}} {{site.data.keyword.alchemylanguageshort}}.

La chiave deve appartenere a un account che è autorizzato a pubblicare i modelli personalizzati o il modello sarà distribuito, ma non potrai utilizzarlo.

Devi specificare la chiave la prima volta che distribuisci un modello a {{site.data.keyword.alchemylanguageshort}}. Puoi quindi riutilizzare la chiave con più versioni del modello che distribuisci. Ogni chiave ha un numero massimo di modelli che possono essere distribuiti contemporaneamente.

### Procedura

Per distribuire un modello di machine learning a {{site.data.keyword.alchemylanguageshort}} :

1. Accedi come amministratore o gestore del progetto {{site.data.keyword.knowledgestudioshort}} e seleziona il tuo spazio di lavoro.
1. Seleziona la scheda **Model Management** > **Versions** > **Machine learning**.
1. Scegli la versione del modello che vuoi distribuire.

    Se esiste solo una versione funzionante del modello, crea un'istantanea del modello corrente. Queste versioni del modello ti abilitano a distribuire una versione mentre continui a migliorare la versione corrente. L'opzione di distribuzione non viene visualizzata finché non crei almeno una versione.

1. Fai clic su **Deploy** e scegli di distribuirlo al servizio {{site.data.keyword.alchemylanguageshort}} e poi fai clic su **Next**.
1. Immetti la chiave che hai ottenuto da {{site.data.keyword.alchemylanguageshort}} o seleziona una versione distribuita precedente del modello che ha una chiave che vuoi riutilizzare e fai clic su **Deploy**. Se la chiave è valida, viene visualizzata una conferma che contiene l'ID del modello. Questa conferma non significa che il modello è pronto per l'utilizzo da parte delle tue applicazioni.
1. Il processo di distribuzione potrebbe richiedere alcuni minuti. Per controllare lo stato della distribuzione, fai clic su **Status** accanto alla versione che hai distribuito. Se il modello sta ancora venendo distribuito, lo stato indica "publishing". Dopo il completamento della distribuzione, lo stato viene modificato con "available" se è ha avuto esito positivo o con "error" se si sono verificati dei problemi.

    Le informazioni sullo stato includono l'ID del modello, le ultime quattro cifre della chiave {{site.data.keyword.alchemyapishort}} e un log del processo di distribuzione. L'ID del modello (model_id) è come le tue applicazioni denominano il modello di machine learning. Utilizza la chiave {{site.data.keyword.alchemyapishort}} per tenere traccia del numero di distribuzioni per chiave.

### Operazioni successive

Per utilizzare il modello distribuito, devi copiare e incollare l'ID del modello nella chiamata API della tua applicazione. La chiamata deve inoltre specificare il servizio del piano avanzato di {{site.data.keyword.alchemylanguageshort}} che vuoi utilizzare con il modello e la rispettiva chiave di accesso {{site.data.keyword.alchemyapishort}} associata. Sono supportati i seguenti endpoint:

- **&lt;*input-type*&gt;GetRankedNamedEntities**

    Utilizza il modello personalizzato che specifichi nel parametro del modello per estrarre un elenco di citazioni di tutti i tipi di entità conosciuti che trova nell'input che fornisci. I tipi di input supportati includono testo, HTML o un URL pubblico. Consulta [{{site.data.keyword.alchemylanguageshort}}&gt;Entities ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/smarterplanet/us/en/ibmwatson/developercloud/alchemy-language/api/v1/#entities){: new_window} per ulteriori informazioni sull'API e la sintassi da utilizzare.

- **&lt;*input-type*&gt;GetTypedRelations**

    Utilizza il modello personalizzato che specifichi nel parametro del modello per estrarre un elenco di istanze di relazioni note che trova nell'input che fornisci. Consulta [{{site.data.keyword.alchemylanguageshort}}&gt;TypedRelations ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/smarterplanet/us/en/ibmwatson/developercloud/alchemy-language/api/v1/#typed-relations){: new_window} per ulteriori informazioni sull'API e la sintassi da utilizzare.

#### Esempi

- La seguente chiamata API ricerca i tipi di entità noti nella stringa di testo che viene passata nel corpo POST. La richiesta specifica l'ID del modello che è stato creato e una chiave API Alchemy che dispone dei diritti per eseguire i modelli personalizzati.

    ```bash
    curl -d 'text=Mary had a little lamb.'
    "https://gateway-a.watsonplatform.net/calls/text/TextGetRankedNamedEntities?
    showSourceText=1&
    model=44476a63-c55t-451f-ad3r-8b23c0f4628c&
    apikey=s3wee88r25wwe2p6442w99g8t77phll5323kkf3a&
    outputMode=json"
    ```
    {: pre}

    La risposta restituisce `Mary` e `lamb` se queste sono citazioni che vengono riconosciute dal tuo modello di machine learning.

- La seguente chiamata API ricerca le relazioni note nella stringa di testo che viene passata nel corpo POST. La richiesta specifica l'ID del modello che è stato creato e una chiave API Alchemy che dispone dei diritti per eseguire i modelli personalizzati.

    ```bash
    curl -d 'text=Mary had a little lamb.'
    "https://gateway-a.watsonplatform.net/calls/text/TextGetTypedRelations?
    showSourceText=1&
    model=44476a63-c55t-451f-ad3r-8b23c0f4628c&
    apikey=s3wee88r25wwe2p6442w99g8t77phll5323kkf3a&
    outputMode=json"
    ```
    {: pre}

    La risposta restituisce `ownedBy` se tale relazione viene riconosciuta dal tuo modello di machine learning.

> **Nota:** viene incluso il ritorno a capo per formattare in modo migliore gli esempi della schermata. Non includere il ritorno a capo nella sintassi dell'API.

Per ulteriori informazioni, consulta la [documentazione {{site.data.keyword.alchemylanguageshort}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/watson/developercloud/doc/alchemylanguage/customizing.shtml){: new_window}.

#### Informazioni correlate

[Problemi con il modello {{site.data.keyword.alchemylanguageshort}} ](/docs/services/watson-knowledge-studio/troubleshooting.html#wks_ts_deployed_model_deleted)

## Distribuzione di un modello di machine learning a IBM Watson Discovery
{: #wks_madiscovery}

Quando sei soddisfatto delle prestazioni del modello, puoi distribuirne una versione a {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}. Questa funzione abilita le tue applicazioni ad utilizzare il modello di machine learning distribuito per arricchire le informazioni dettagliate che ottieni dai tuoi dati con il riconoscimento dei concetti e delle relazioni che sono rilevanti nel tuo dominio.

### Prima di cominciare

Devi avere l'ascesso amministrativo all'istanza del servizio {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}} e conoscere i nomi dell'istanza e dello spazio {{site.data.keyword.Bluemix_notm}} ad esso associati.

### Informazioni su quest'attività

Quando distribuisci il modello di machine learning, seleziona la versione che vuoi distribuire.

### Procedura

Per distribuire un modello di machine learning a {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}}, completa la seguente procedura:

1. Accedi come amministratore o gestore del progetto {{site.data.keyword.knowledgestudioshort}} e seleziona il tuo spazio di lavoro.
1. Seleziona la scheda **Model Management** > **Versions** > **Machine learning**.
1. Scegli la versione del modello che vuoi distribuire.

    Se esiste solo una versione funzionante del modello, crea un'istantanea del modello corrente. Queste versioni del modello ti abilitano a distribuire una versione mentre continui a migliorare la versione corrente. L'opzione di distribuzione non viene visualizzata finché non crei almeno una versione.

1. Fai clic su **Deploy**, scegli di distribuirlo a {{site.data.keyword.discoveryshort}} e poi fai clic su **Next**.
1. Seleziona l'istanza e lo spazio {{site.data.keyword.Bluemix_notm}}. Se necessario, seleziona una regione differente.
1. Fai clic su **Deploy**.
1. Il processo di distribuzione potrebbe richiedere alcuni minuti. Per controllare lo stato della distribuzione, fai clic su **Status** nella scheda **Versions** accanto alla versione che hai distribuito.

    Se il modello sta ancora venendo distribuito, lo stato indica "publishing". Dopo il completamento della distribuzione, lo stato viene modificato con "available" se è ha avuto esito positivo o con "error" se si sono verificati dei problemi.

    Quando disponibile, prendi nota dell'ID del modello (model_id). Fornirai questo ID al servizio {{site.data.keyword.discoveryshort}} per abilitarlo ad utilizzare il tuo modello personalizzato.

### Operazioni successive

Per utilizzare il modello distribuito, devi fornire l'ID del modello quando viene richiesto durante il processo di configurazione del miglioramento del servizio {{site.data.keyword.discoveryshort}}. Per ulteriori dettagli, consulta la [documentazione del servizio {{site.data.keyword.discoveryshort}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://www.ibm.com/watson/developercloud/doc/discovery/integrate-wks.shtml){: new_window}.

## Distribuzione di un modello di machine learning a IBM Watson Natural Language Understanding
{: #wks_manlu}

Quando sei soddisfatto delle prestazioni del modello, puoi distribuirne una versione a {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.nlushort}}. Questa funzione abilita le tue applicazioni ad utilizzare il modello di machine learning distribuito per analizzare le funzioni semantiche dell'input di testo, incluse le entità e le relazioni.

### Prima di cominciare

Devi avere un servizio {{site.data.keyword.nlushort}} a cui distribuire. E devi conoscere i nomi dell'istanza e dello spazio {{site.data.keyword.Bluemix_notm}} associati al servizio. Se non ricordi i nomi dell'istanza e dello spazio, trovali accedendo a {{site.data.keyword.Bluemix_notm}}. Se non hai un account {{site.data.keyword.Bluemix_notm}}, registrane uno.

### Informazioni su quest'attività

Quando distribuisci il modello di machine learning, seleziona la versione che vuoi distribuire.

### Procedura

Per distribuire un modello di machine learning al servizio  {{site.data.keyword.nlushort}}, completa la seguente procedura:

1. Accedi come amministratore o gestore del progetto {{site.data.keyword.knowledgestudioshort}} e seleziona il tuo spazio di lavoro.
1. Seleziona la scheda **Model Management** > **Versions** > **Machine learning**.
1. Scegli la versione del modello che vuoi distribuire.

    Se esiste solo una versione funzionante del modello, crea un'istantanea del modello corrente. Queste versioni del modello ti abilitano a distribuire una versione mentre continui a migliorare la versione corrente. L'opzione di distribuzione non viene visualizzata finché non crei almeno una versione.

1. Fai clic su **Deploy**, scegli di distribuirlo a {{site.data.keyword.nlushort}} e poi fai clic su **Next**.
1. Seleziona l'istanza e lo spazio {{site.data.keyword.Bluemix_notm}}. Se necessario, seleziona una regione differente.
1. Fai clic su **Deploy**.
1. Il processo di distribuzione potrebbe richiedere alcuni minuti. Per controllare lo stato della distribuzione, fai clic su **Status** nella scheda **Versions** accanto alla versione che hai distribuito. Se il modello sta ancora venendo distribuito, lo stato indica "publishing". Dopo il completamento della distribuzione, lo stato viene modificato con "available" se è ha avuto esito positivo o con "error" se si sono verificati dei problemi.

    Quando disponibile, prendi nota dell'ID del modello (model_id). Fornirai questo ID al servizio {{site.data.keyword.nlushort}} per abilitarlo ad utilizzare il tuo modello personalizzato.

### Operazioni successive

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

Consulta la [documentazione {{site.data.keyword.nlushort}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/watson/developercloud/doc/natural-language-understanding/index.html){: new_window} per ulteriori dettagli.

## Annullamento della distribuzione dei modelli
{: #undeploy-view-model}

Se vuoi annullare la distribuzione di un modello o trovare un ID del modello, consulta la pagina **Deployed Models**. La pagina **Deployed Models** mostra tutti i modelli {{site.data.keyword.knowledgestudioshort}} distribuiti ai servizi negli spazi a cui hai accesso.

Per annullare la distribuzione dei modelli o trovare gli ID del modello:

1. Accedi come amministratore o gestore del progetto {{site.data.keyword.knowledgestudioshort}} e seleziona il tuo spazio di lavoro.
1. Dal menu **Settings** nella barra del menu in alto a destra, seleziona **Manage deployed models**.
1. Dall'elenco di modelli distribuiti, trova il modello che vuoi visualizzare o di cui vuoi annullare la distribuzione.
1. Per annullare la distribuzione di un modello, dall'ultima colonna di tale riga, fai clic su **Undeploy model**.
1. Per trovare l'ID del modello, consulta la colonna **Model ID**.

## Utilizzo di un modello di machine learning in IBM Watson Explorer
{: #wks_maexport}

Esporta il modello di machine learning preparato in modo che possa essere utilizzato in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.

### Prima di cominciare

Se scegli di identificare i tipi di relazione e annotarli, devi definire almeno due tipi di relazione e annotare le istanze delle relazioni nel ground truth prima di esportare il modello. Definire e annotare un solo tipo di relazione può causare problemi successivi in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, release 11.0.1.0.

### Informazioni su quest'attività

Ora che il modello di machine learning è preparato per riconoscere le entità e le relazioni di un determinato dominio, puoi utilizzarlo in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.

Fai clic su [questo link ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.youtube.com/watch?v=1VoS-xczBow&amp;feature=youtu.be){: new_window} per guardare un video di meno di 2 minuti che illustra come esportare un modello e utilizzarlo in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.

### Procedura

Per utilizzare un modello di machine learning in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, completa la seguente procedura.

1. Accedi come amministratore o gestore del progetto {{site.data.keyword.knowledgestudioshort}} e seleziona il tuo spazio di lavoro.
1. Seleziona la scheda **Model Management** > **Versions** > **Machine learning**.
1. Fai clic su **Export current model**.

    Se hai una sottoscrizione di piano gratuito, l'opzione di esportazione non è disponibile. 

    Il modello viene salvato come un file ZIP e ti viene richiesto di scaricarlo.

1. Scarica il file nel tuo sistema locale.
1. Dall'applicazione {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, importa il modello.

    Puoi quindi associare il modello a un modello di machine learning in {{site.data.keyword.watson}} Explorer Content Analytics. Dopo aver eseguito il passo di associazione, quando effettui una ricerca per indicizzazione dei documenti, il modello trova le istanze delle entità e delle relazioni comprese dal tuo modello. Per imparare come importare e configurare in modello in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer, consulta la documentazione tecnica che descrive l'integrazione: [http://www.ibm.com/support/docview.wss?uid=swg27048147 ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://www.ibm.com/support/docview.wss?uid=swg27048147){: new_window}.

#### Attività correlate

[Esportazione dei documenti analizzati da {{site.data.keyword.watson}} Explorer Content Analytics](/docs/services/watson-knowledge-studio/preannotation.html#wks_uimawexca)
