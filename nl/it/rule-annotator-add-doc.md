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

Questa documentazione è per {{site.data.keyword.knowledgestudiofull}} su {{site.data.keyword.cloud}}. Per visualizzare la documentazione della versione precedente di {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace, [fai clic su questo link ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/docs/services/knowledge-studio/rule-annotator-add-doc.html){: new_window}.
{: tip}

# Aggiunta di documenti per la definizione delle regole 
{: #wks_rule_anno_add}

Aggiunta di documenti con modelli linguistici che illustrano i tipi di regole che vuoi definire.
{: shortdesc}

I documenti che aggiungi per la definizione delle regole vengono tenuti separati da quelli che aggiungi per l'annotazione. Il loro unico scopo è di essere utilizzati per l'estrazione di esempi dei modelli. Non vengono utilizzati per la preparazione e non vengono mai scaricati.

## Modi con cui puoi aggiungere i documenti all'editor della regola

- **Crea un documento di testo nel formato UTF-8**

    Puoi aggiungere del testo che illustra un modello direttamente nell'editor della regola. Il nome che specifichi per il documento non può essere più lungo di 256 caratteri.

- **Carica un file CSV**

    Carica un file nel formato CSV che contiene il testo del documento.

- **Copia un documento che era stato importato per l'annotazione**

    Se un documento che fa parte di una serie che era stata importata per scopi di annotazione contiene gli esempi dei modelli che vuoi acquisire come regole, puoi copiarlo nell'editor della regola. Tutte le modifiche che apporti al documento non influenzano la versione originale del documento che sta venendo utilizzata per l'annotazione. Consulta [Aggiunta di documenti a uno spazio di lavoro](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projadd) per informazioni sul caricamento dei documenti.

Per i documenti che copi o carichi, scegli quelli che contengono modelli distinti che aiutano a identificare i tipi di entità nei documenti.
