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

Questa documentazione è per {{site.data.keyword.knowledgestudiofull}} su {{site.data.keyword.cloud}}. Per visualizzare la documentazione della versione precedente di {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace, [fai clic su questo link ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/docs/services/knowledge-studio/tutorials-bootstrap-annotation.html){: new_window}.
{: tip}

# Pre-annotazione dei documenti
{: #wks_tutboot_intro}

Questa esercitazione ti aiuta a comprendere come pre-annotare i documenti, per far progredire il processo di annotazione dell'annotazione umana.
{: shortdesc}

## Obiettivi di apprendimento
{: #objectives}

Dopo aver completato questa esercitazione, conoscerai come pre-annotare i documenti con un modello di machine learning.

Questa esercitazione dovrebbe richiedere 5 minuti circa per essere completata. Potrebbe essere necessario più tempo se si approfondiscono altri concetti correlati a quest'esercitazione.

## Prima di cominciare
{: #prereqs}

- Assicurati di stare utilizzando un browser supportato. Per informazioni, consulta [Requisiti del browser](/docs/services/watson-knowledge-studio/system-requirements.html).
- Hai correttamente completato l'[Introduzione a {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/tutorials-create-project.html), che copre la creazione di uno spazio di lavoro, la creazione di un sistema tipo e l'aggiunta di un dizionario.
- Hai correttamente completato la [Creazione di un modello di machine learning](/docs/services/watson-knowledge-studio/tutorials-create-ml-model.html).
- Devi avere almeno un ID utente nel ruolo di gestore del progetto o di amministratore. Per informazioni sui ruoli utente, consulta [Ruoli utente in {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/roles.html).

## Risultati
{: #results}

Dopo aver completato questa esercitazione, avrai una serie di documenti parzialmente annotati. In seguito, puoi assegnare i documenti agli annotatori umani per finire il lavoro di annotazione.

## Lezione 1: Pre-annotazione di nuovi documenti con un modello di machine learning
{: #wks_tutboot_ml}

In questa lezione, apprenderai come utilizzare un modello di machine learning per pre-annotare i documenti in {{site.data.keyword.knowledgestudioshort}}.

### Informazioni su quest'attività
{: #wks_tutboot_ml_about}

Dopo aver preparato un modello di machine learning, puoi utilizzarlo per pre-annotare i nuovi documenti che aggiungi al corpus.

> **Attenzione:** non eseguire un pre-annotatore sui documenti che sono stati annotati dagli umani ma non ancora aggiunti al ground truth. Se lo fai, tutte le annotazioni correnti saranno rimosse dai documenti.

In questa esercitazione, puoi aggiungere una seconda serie di documenti utilizzando il file `documents-ml.csv`. Non riaggiungere il file `documents-new.csv`, poiché creerà documenti duplicati nel ground truth. La duplicazione causa i seguenti problemi:

- Se le annotazioni su ogni documento non corrispondono, abbasseranno la qualità del modello di machine learning.
- Se le annotazioni su ogni documento corrispondono, sovrappreparano il modello di machine learning per i file duplicati.

Per ulteriori informazioni sulla pre-annotazione dei documenti, consulta [Inizio dell'annotazione](/docs/services/watson-knowledge-studio/preannotation.html), che copre i metodi aggiuntivi di pre-annotazione.

### Procedura
{: #wks_tutboot_ml_procedure}

1. Accedi a {{site.data.keyword.knowledgestudioshort}} come amministratore.
1. Carica ulteriori documenti nello spazio di lavoro. Puoi utilizzare il file <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/documents-ml.csv" download>`documents-ml.csv` <img src="../../icons/launch-glyph.svg" alt="Icona link esterno" title="Icona link esterno" class="style-scope doc-content"></a>.

    Per ulteriori informazioni sull'aggiunta dei documenti a uno spazio di lavoro, vedi [Aggiunta di documenti per l'annotazione](/docs/services/watson-knowledge-studio/documents-for-annotation.html).

1. Crea una serie di annotazioni che utilizza il file `documents-ml.csv` come serie di base ed assegnati ad essa come amministratore.

    Dopo aver completato le seguenti istruzioni per pre-annotare i nuovi documenti, puoi visualizzare la serie di annotazioni per vedere come il modello di machine learning ha annotato i documenti. Generalmente, assegni le serie di annotazioni a uno o più annotatori umani. Per ulteriori informazioni sulla creazione e l'assegnazione delle serie di annotazioni, consulta [Aggiunta di documenti per l'annotazione](/docs/services/watson-knowledge-studio/documents-for-annotation.html).

1. Per pre-annotare i nuovi documenti, fai clic su **Machine Learning Model** > **Versions** e poi su **Run this model**.
1. Seleziona la serie di documenti che hai aggiunto al corpus, `documents-ml.csv` e fai clic su **Run**.
1. Dopo il completamento della pre-annotazione, crea un'attività di pre-annotazione umana che include la serie di annotazioni che hai creato. 

    Per ulteriori informazioni sulla creazione di un'attività di annotazione, consulta [Configurazione dell'annotazione](/docs/services/watson-knowledge-studio/annotate-documents.html).

1. Per visualizzare le annotazioni che sono state applicate dal modello di machine learning ai nuovi documenti, apri l'attività di annotazione.

    Poiché i nuovi documenti sono stati pre-annotati con il modello di machine learning, l'annotazione umana richiede meno tempo. Per ulteriori informazioni sull'aggiunta di annotazioni da parte di annotatori umani, consulta [Annotazione dei documenti](/docs/services/watson-knowledge-studio/user-guide.html).

### Risultati
{: #wks_tutboot_ml_results}

Utilizzando il tuo modello di machine learning per pre-annotare le nuove serie di documenti, puoi velocizzare le attività di annotazione umana per quei documenti.
