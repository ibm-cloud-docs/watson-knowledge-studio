---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-29"

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

Questa documentazione è per {{site.data.keyword.knowledgestudiofull}} su {{site.data.keyword.cloud}}. Per visualizzare la documentazione della versione precedente di {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace, [fai clic su questo link ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/docs/services/knowledge-studio/train-ml.html){: new_window}.
{: tip}

# Preparazione del modello di machine learning
{: #train-ml}

In {{site.data.keyword.knowledgestudiofull}}, la creazione del modello di machine learning implica la sua preparazione e la valutazione di quanto buona è stata l'esecuzione dell'annotazione dei dati di test e senza indicazioni.
{: shortdesc}

## Creazione di un modello di machine learning
{: #wks_madocsets}

Quando crei un modello di machine learning, selezioni le serie di documenti che vuoi utilizzare per preparare il modello e specifichi la percentuale di documenti che vengono utilizzati come dati di preparazione, di test e senza indicazioni.

### Informazioni su quest'attività
{: #wks_madocsets_about}

Esplorando le metriche delle prestazioni, puoi identificare i modi per migliorare l'accuratezza del modello.

> **Limitazione:** possono essere preparati contemporaneamente solo tre modelli di machine learning per istanza di {{site.data.keyword.knowledgestudioshort}}. Se la tua istanza contiene più spazi di lavoro e il numero di modelli di machine learning che sta venendo preparato negli altri spazi di lavoro è già 3, la richiesta di preparazione del modello di machine learning nel tuo spazio di lavoro sarà accodata finché non finiscono gli altri processi di preparazione.

### Procedura
{: #wks_madocsets_procedure}

Per creare un modello di machine learning:

1. Accedi come amministratore {{site.data.keyword.knowledgestudioshort}} e seleziona il tuo spazio di lavoro.
1. Seleziona **Machine Learning Model** > **Performance**.
1. Verifica che tutte le serie di documenti siano state approvate e che tutti conflitti di annotazione siano stati risolti tramite il giudizio. Solo i documenti che sono diventati ground truth tramite il giudizio o l'approvazione possono essere utilizzati per preparare il modello.
1. Fai clic su **Train and evaluate**.
1. Facoltativo: per specificare come vuoi assegnare i documenti dalle tue serie di documenti da utilizzare per le serie di preparazione, test e senza indicazioni al livello del sistema, fai clic su **Edit settings**.

    Consulta [Gestione della serie di documenti](/docs/services/watson-knowledge-studio/improve-ml.html#wks_mamanagedata) per determinare quali rapporti applicare.

1. Facoltativo: associa tutti i dizionari, che vuoi che il modello di machine learning utilizzi durante la preparazione, al tipo di entità delle voci del dizionario.

    Se hai creato un pre-annotatore del dizionario, hai già eseguito questo passo. Fai clic su **Reuse mapping that is defined for dictionary pre-annotator** per riutilizzare o definire una nuova associazione.

    Il modello utilizza le informazioni sul tipo di termini del dizionario come una funzione tra le molte funzioni di analisi linguistica che prende in considerazione durante la preparazione.

1. Fai clic su **Train** per preparare il modello o su **Train & Evaluate** per preparalo, valutare le annotazioni aggiunte dal modello di machine learning e analizzare le statistiche delle prestazioni.

    > **Importante:** la preparazione di un modello di machine learning può durare molti minuti o molte ore, a seconda del numero di annotazioni umane presenti e dal numero totale di parole di tutti i documenti.

1. Seleziona le serie di documenti che vuoi utilizzare per la preparazione del modello.

    > **Nota:** le serie di documenti devono contenere almeno 10 documenti annotati.

1. Dopo aver creato il modello, seleziona una delle seguenti azioni:

    <table summary="Ogni riga in questa tabella descrive una opzione per una scelta.">
      <caption>Tabella 1. Opzioni del documento</caption>
      <tr>
        <th style="vertical-align:bottom; text-align"left" id="d33883e137-option">Option</th>
        <th style="vertical-align:bottom; text-align"left" id="d33883e137-desc">Descrizione</th>
      </tr>
      <tr>
        <td style="vertical-align:top; text-align"left" headers="d33883e137-option" id="d33883e139">
          <p><strong>Log</strong></p>
        </td>
        <td style="vertical-align:top; text-align"left" headers="d33883e137-desc d33883e139">
          <p>Visualizza il file di log per vedere se si sono verificati dei problemi.</p>
        </td>
      </tr>
      <tr>
        <td style="vertical-align:top; text-align"left" headers="d33883e137-option" id="d33883e144">
          <p><strong>Details</strong></p>
        </td>
        <td style="vertical-align:top; text-align"left" headers="d33883e137-desc d33883e144">
          <p>Visualizza le statistiche delle prestazioni di annotazione, modifica le serie di documenti che vuoi utilizzare
              per la preparazione e il test del modello e crea l'istantanea delle versioni delle risorse
              del modello.</p>
        </td>
      </tr>
      <tr>
        <td style="vertical-align:top; text-align"left" headers="d33883e137-option" id="d33883e149">
          <p><strong>Export</strong></p>
        </td>
        <td style="vertical-align:top; text-align"left" headers="d33883e137-desc d33883e149">
          <p>Se hai un piano standard o premium, puoi esportare un file <code>ZIP</code> nel tuo sistema locale che contiene i componenti necessari al modello per eseguire un ambiente di runtime di machine learning, come ad esempio {{site.data.keyword.watson}} Explorer. </p>
        </td>
      </tr>
    </table>

## Valutazione delle annotazioni aggiunte dal modello
{: #wks_matest}

Puoi confrontare la vista del ground truth delle annotazioni aggiunte dagli annotatori umani rispetto a quelle aggiunte dal modello.

### Procedura
{: #wks_matest_procedure}

Per valutare le annotazioni aggiunte dal modello:

1. Seleziona **Machine Learning Model** > **Performance** > **Train and evaluate**. Viene visualizzata la pagina Training/Test/Blind Sets.
1. Fai clic su **View Ground Truth** della serie di preparazione o di test per visualizzare le annotazioni che sono state aggiunte tramite la pre-annotazione o dagli annotatori umani. Si apre l'editor ground truth. Fai clic per aprire i documenti individuali e vedere come citazioni, relazioni e citazioni di coreferenza sono state annotate.
1. Nella pagina **Performance**, fai clic su **View Decoding Results** per visualizzare le annotazioni che il modello di machine learning ha aggiunto ai documenti nella serie di test. Questo pulsante è disponibile solo dopo che valuti il modello. Visualizzando i risultati, puoi vedere quanto bene il modello di machine learning ha etichettato le citazioni, le relazioni e le citazioni di coreferenza nei dati di test.
1. Se vuoi modificare come i documenti sono stati suddivisi tra le serie di preparazione, test e senza indicazioni, fai clic su **Performance** > **Train and evaluate** > **Edit Settings**. Ad esempio, se i risultati iniziali sembrano accettabili, potresti voler aumentare il numero di documenti nella serie di test per verificare ulteriormente i risultati del modello di machine learning. Puoi modificare il rapporto di quanti documenti sono automaticamente suddivisi per scopi diversi o puoi selezionare le serie di documenti specifiche da utilizzare come dati di preparazione, test e senza indicazioni.
1. Se apporti delle modifiche, fai clic su **Train & Evaluate** per riaggiornare il modello e rivalutare le annotazioni.

## Eliminazione di un modello di machine learning
{: #wks_madelete}

Non puoi eliminare un modello di machine learning.

Puoi eliminare lo spazio di lavoro che è stato utilizzato per sviluppare il modello ma non il modello stesso. L'eliminazione di un modello non è l'approccio migliore. Invece, aggiorna o sostituisci le risorse che sono state utilizzate per preparare il modello. Anche se il modello non sta producendo i risultati previsti, puoi continuare a rifinirlo. Ogni volta che crei una nuova versione, il modello viene creato nuovamente. Puoi modificare le risorse come i dizionari e i tipi di sistema e scegliere di utilizzare serie di annotazioni differenti quando prepari la versione successiva.
