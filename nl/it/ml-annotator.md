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

Questa documentazione è per {{site.data.keyword.knowledgestudiofull}} su {{site.data.keyword.cloud}}. Per visualizzare la documentazione della versione precedente di {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace, [fai clic su questo link ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/docs/services/knowledge-studio/ml-annotator.html){: new_window}.
{: tip}

# Flusso di lavoro di creazione del modello di machine learning
{: #ml_annotator}

Crea un modello di machine learning che tratta un modello che puoi utilizzare per identificare le voci, le coreferenze e le relazioni di interesse nei nuovi documenti.
{: shortdesc}

Comprendi il flusso di lavoro tipico per la creazione di un modello di machine learning in {{site.data.keyword.knowledgestudioshort}}.

Tutti i passi vengono eseguiti dal gestore del progetto, tranne il passo *Annota i documenti*, che viene eseguito da un annotatore umano. Poiché gli annotatori umani sono spesso esperti in materia, potrebbero essere consultati durante la creazione delle risorse dello spazio di lavoro, come il sistema tipo e altro.

![Il flusso di lavoro per lo sviluppo di un modello di machine learning](images/wks-checklist.svg "Mostra i passi chiave che devi eseguire per creare un modello") Figura 1. Il flusso di lavoro per lo sviluppo di un modello di machine learning

<table summary="Creazione e rifinitura di un modello">
  <caption>Tabella 1. Creazione e rifinitura di un flusso di lavoro</caption>
  <tr>
    <th style="vertical-align:bottom; text-align:left" id="d14771e70">Passo</th>
    <th style="vertical-align:bottom; text-align:left" id="d14771e72">Descrizione</th>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d14771e70">
      <p>Crea uno spazio di lavoro.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d14771e72">
      <p>Consulta [Creazione di uno spazio di lavoro](/docs/services/watson-knowledge-studio/create-project.html). Uno spazio di lavoro contiene le risorse
che vengono utilizzate per creare il modello, inclusi:</p>
      <dl>
        <dt>Sistema tipo</dt>
        <dd>
          <p>Carica o crea il sistema tipo e definisci i tipi di entità e di relazione che gli annotatori umani
possono applicare quando annotano il testo. Il gestore del processo del modello normalmente collabora con gli
esperti in materia del tuo dominio per definire il sistema tipo. Consulta [Stabilire un sistema tipo](/docs/services/watson-knowledge-studio/typesystem.html)</p>
        </dd>
        <dt>Documenti di origine</dt>
        <dd>
          <p>Crea un corpus caricando i documenti di esempio che rappresentano il tuo contenuto del dominio
nello spazio di lavoro. Consulta [Aggiunta di documenti per l'annotazione](/docs/services/watson-knowledge-studio/documents-for-annotation.html). Suddividi il corpus in serie di documenti,
specifica la percentuale di documenti che sono condivisi tra tutte le serie di documenti e assegna le serie di documenti
agli annotatori umani. Consulta [Creazione e assegnazione delle serie di annotazioni](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projdocsets).</p>
        </dd>
        <dt>Dizionari</dt>
        <dd>
          <p>Carica o crea i dizionari per l'annotazione del testo. Puoi scegliere di aggiungere manualmente le voci del dizionario
o di caricarle da un file e poi modificarle. Consulta [Creazione dei dizionari](/docs/services/watson-knowledge-studio/dictionaries.html).</p>
        </dd>
      </dl>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d14771e70">
      <p><strong>Facoltativo</strong>: pre-annota i documenti</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d14771e72">
      <p>Pre-annota i documenti in base ai termini nei dizionari dello spazio di lavoro, alle citazioni dei tipi {{site.data.keyword.nlushort}}
o in base alle regole che definisci. Consulta [Inizio dell'annotazione](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotate).</p>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d14771e70">
      <p>Annota i documenti</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d14771e72">
      <ol>
        <li>
          <p>Il gestore del progetto assegna le attività di annotazione agli annotatori umani, configura la soglia dell'accordo
tra annotatori e fornisce le linee guida di annotazione che devono seguire gli annotatori umani. Consulta
[Creazione di un'attività di annotazione](/docs/services/watson-knowledge-studio/annotate-documents.html#wks_hatask).</p>
        </li>
        <li>
          <p>Gli annotatori umani utilizzano l'editor ground truth
per annotare manualmente i documenti. Un annotatore umano identifica le citazioni di interesse nel tuo contenuto del dominio
e le etichetta con i tipi di entità. L'annotatore umano inoltre identifica le relazioni tra le citazioni
(ad esempio, Mary è un'impiegata di IBM) e come le citazioni fanno coreferimento alla stessa entità
(come una ricorrenza di "she" che fa riferimento a Mary). Fai riferimento a [Annotazione dei documenti](/docs/services/watson-knowledge-studio/user-guide.html).</p>
        </li>
      </ol>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d14771e70">
      <p>Giudica e promuovi i documenti</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d14771e72">
      <p>Accetta o rifiuta il ground truth che è stato generato dagli annotatori umani e giudica tutte
le differenze di annotazione per risolvere i conflitti. La valutazione dell'accuratezza e della congruenza del lavoro di annotazione umana
potrebbe essere di responsabilità di un annotatore umano esperto o di un utente
con maggiore esperienza in materia rispetto al gestore del progetto. Consulta [Giudizio](/docs/services/watson-knowledge-studio/build-groundtruth.html#wks_haperform).</p>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d14771e70">
      <p>Prepara il modello</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d14771e72">
      <p>Crea il modello di machine learning. Consulta [Creazione di un modello di machine learning](/docs/services/watson-knowledge-studio/train-ml.html#wks_madocsets).</p>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d14771e70">
      <p>Valuta il modello.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d14771e72">
      <p>Valuta l'accuratezza del modello. Consulta [Valutazione delle annotazioni aggiunte dal modello](/docs/services/watson-knowledge-studio/train-ml.html#wks_matest). A seconda dell'accuratezza del modello, questo passo potrebbe creare
il bisogno di ripetere nuovamente dei passi precedenti finché non viene raggiunta l'accuratezza ottimale. Consulta [Analisi delle prestazioni del modello di machine learning](/docs/services/watson-knowledge-studio/evaluate-ml.html) per idee su cosa aggiornare in base
ai problemi di prestazioni comuni.</p>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d14771e70">
      <p>Pubblica il modello.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d14771e72">
      <p>Esporta o distribuisci il modello. Consulta [Utilizzo del modello di machine learning](/docs/services/watson-knowledge-studio/publish-ml.html).</p>
    </td>
  </tr>
</table>
