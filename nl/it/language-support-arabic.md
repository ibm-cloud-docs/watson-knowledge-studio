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

Questa documentazione è per {{site.data.keyword.knowledgestudiofull}} su {{site.data.keyword.cloud}}. Per visualizzare la documentazione della versione precedente di {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace, [fai clic su questo link ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/docs/services/knowledge-studio/language-support-arabic.html){: new_window}.
{: tip}

# Configurazione del supporto per l'arabo
{: #wks_langsupp_ar}

Leggi queste linee guida per comprendere come {{site.data.keyword.knowledgestudioshort}} gestisce la forma dei caratteri e dei numeri arabi nei documenti in arabo.

## Informazioni su quest'attività

Con il rispetto della forma del carattere, l'alfabeto arabo non ha lettere maiuscole ma le lettere possono modificare la forma a seconda della loro posizione nella stringa di testo e delle lettere circostanti. Sistemi operativi differenti e programmi di conversione della pagina di codice gestiscono la forma della lettera in modi diversi. La memorizzazione senza forma è uno standard per i sistemi Windows e {{site.data.keyword.knowledgestudioshort}} presume che il testo arabo sia memorizzato senza forma. Se vuoi caricare il testo con forma in {{site.data.keyword.knowledgestudioshort}}, devi prima convertirlo dal formato senza forma utilizzando strumenti standard, come l'API International Components for Unicode (ICU) (consulta ArabicShaping Class all'indirizzo [http://icu-project.org/apiref/icu4j/com/ibm/icu/text/ArabicShaping.html ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://icu-project.org/apiref/icu4j/com/ibm/icu/text/ArabicShaping.html){: new_window}).

> **Importante:** in alcuni casi, la mancanza della formazione adeguata del carattere arabo potrebbe causare che il contenuto venga visualizzato in modo non corretto nell'editor ground truth.

Con il rispetto della forma del numero, {{site.data.keyword.knowledgestudioshort}} considera la forma numerica come una proprietà al livello di memorizzazione, simile a come il contenuto in arabo viene gestito nella piattaforma iOS. Poiché viene creato molto contenuto arabo sulle piattaforme come Windows, che tratta la forma numerica come una proprietà al livello di visualizzazione, devi convertire il contenuto per rendere la forma numerica una proprietà al livello di memorizzazione o utilizza un browser Firefox quando utilizzi {{site.data.keyword.knowledgestudioshort}}. Firefox supporta la capacità di impostare le preferenze della forma numerica esplicitamente al livello del browser e applica la visualizzazione appropriata a tutto il contenuto visualizzato nel browser.

## Procedura

Per configurare la forma numerica nel browser Firefox:

1. Nel campo URL del browser, immetti **about:config**. Se ti viene mostrata un'avvertenza da Firefox, fai clic sull'azione per ignorarla e continua. Per informazioni sulla modifica delle proprietà **about:config**, consulta [http://kb.mozillazine.org/About:config_entries ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://kb.mozillazine.org/About:config_entries){: new_window}.
1. Immetti `bidi` nel campo del filtro di ricerca.
1. Seleziona la proprietà **bidi.numeral**, che controlla come i numeri sono visualizzati e premi Invio.
1. Modifica il valore di questa proprietà come necessario. Ad esempio, immetti `3` e poi fai clic su **OK**.

    - **0**: numeri nominali (il valore predefinito)
    - **1**: numeri di contesto regolari
    - **2**: numeri di contesto hindi
    - **3**: numeri arabi
    - **4**: numeri hindi

    > **Importante:** quando viene utilizzata la proprietà **bidi.numeral**, Firefox ignora completamente il punto di codice dei caratteri numerici specifici nel contenuto di una pagina web.

### Riferimenti correlati

[Supporto per la lingua](/docs/services/watson-knowledge-studio/language-support.html)
