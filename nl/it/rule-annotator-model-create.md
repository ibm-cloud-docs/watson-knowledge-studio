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

Questa documentazione è per {{site.data.keyword.knowledgestudiofull}} su {{site.data.keyword.cloud}}. Per visualizzare la documentazione della versione precedente di {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace, [fai clic su questo link ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/docs/services/knowledge-studio/rule-annotator-model-create.html){: new_window}.
{: tip}

# Creazione del modello basato sulla regola
{: #wks_rule_train}

Dopo aver definito le regole, puoi creare un modello basato sulla regola.
{: shortdesc}

## Procedura
{: #wks_rule_train_procedure}

Per creare un modello basato sulla regola, completa la seguente procedura:

1. Accedi come amministratore o gestore del progetto {{site.data.keyword.knowledgestudioshort}} e seleziona il tuo spazio di lavoro.
1. Seleziona la scheda **Rule-based Model** > **Versions** > **Rule-based Model**.
2. Fai clic su **Map entity types and classes**.
3. Associa i tipi di entità dal tuo sistema tipo a una o più classi che hai utilizzato per definire le regole.

  Dopo aver associato i tipi di entità, puoi [distribuire il modello basato sulla regola](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html) o utilizzarlo per [pre-annore i documenti](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannotrule) nel processo di creazione di un modello di machine learning.

## Eliminazione di un modello basato sulla regola
{: #wks_rule_delete_model}

Non puoi eliminare un modello basato sulla regola.

Puoi eliminare lo spazio di lavoro che è stato utilizzato per sviluppare il modello basato sulla regola ma non il modello stesso. L'eliminazione di un modello non è l'approccio migliore. Invece, ricrea le regole che sono state definite per esso. Modificando le regole si modifica direttamente il comportamento del modello basato sulla regola.
