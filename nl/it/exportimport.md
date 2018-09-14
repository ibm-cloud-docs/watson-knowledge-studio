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

Questa documentazione è per {{site.data.keyword.knowledgestudiofull}} su {{site.data.keyword.cloud}}. Per visualizzare la documentazione della versione precedente di {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace, [fai clic su questo link ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/docs/services/knowledge-studio/exportimport.html){: new_window}.
{: tip}

# Caricamento delle risorse da un altro spazio di lavoro
{: #exportimport}

Per accelerare la creazione di un modello, puoi caricare le risorse come i documenti (con o senza le annotazioni ground truth), un sistema tipo e i dizionari che hai scaricato da un altro spazio di lavoro.
{: shortdesc}

La capacità di scaricare e caricare separatamente diverse risorse ti fornisce la flessibilità quando progetti e crei un modello. Ad esempio, potresti creare uno spazio di lavoro per progettare il sistema tipo ed eseguire l'annotazione umana e poi creare uno spazio di lavoro separato, forse in un'istanza separata di {{site.data.keyword.knowledgestudioshort}} con utenti differenti, per preparare il modello di machine learning. L'essere in grado di caricare le risorse, incluso il ground truth creato dagli annotatori umani, rende possibile questo scenario.

Non puoi scaricare e caricare un modello di machine learning. Invece, puoi scaricare tutte le risorse che sono state utilizzate per creare il modello da uno spazio di lavoro e caricarle in un nuovo spazio. Dal nuovo spazio di lavoro, puoi eseguire nuovamente la preparazione per ricreare il modello. Il nuovo modello dovrebbe produrre risultati simili al modello originale perché sono entrambi stati preparati con la stessa serie di risorse.

I file che scarichi sono indipendenti dal sistema operativo. Le istanze di {{site.data.keyword.knowledgestudioshort}} dove scarichi o carichi i file non devono essere eseguite nella stessa versione di Linux.

## Sistemi tipo
{: #wks_exportimport_expimp_type}

Per scaricare un sistema tipo, apri la pagina **Assets**> **Entity Types** e fai clic su **Download Types**. Il sistema crea un file denominato `types-ID.json` e ti richiede di scaricarlo nel tuo sistema locale. Per utilizzare questo sistema tipo in un nuovo spazio di lavoro, apri la pagina **Entity Types** e carica il file `JSON` che hai scaricato.

## Dizionari
{: #wks_exportimport_expimp_dict}

Per scaricare tutti i dizionari, seleziona la pagina **Assets** > **Dictionaries** e fai clic sull'icona **Menu** accanto al pulsante **Create Dictionary** e seleziona **Download Dictionaries**. Per ogni dizionario che scarichi, il sistema crea un file denominato `dictionary name_timestamp.csv`, combina i file in un file `ZIP` denominato `workspace name_dictionary_timestamp.zip` e ti richiede di scaricarlo nel tuo sistema locale.

Puoi scaricare un solo dizionario aprendolo e facendo clic su **Download**. I dizionari di sola anteprima che hai caricato come file CSV del dizionario non possono essere scaricati.

Prima di caricare un dizionario scaricato in un nuovo spazio di lavoro, devi scaricare il sistema tipo dal vecchio spazio di lavoro e caricarlo nel nuovo. Il sistema tipo e i dizionari devono essere originati dallo stesso spazio di lavoro {{site.data.keyword.knowledgestudioshort}} e deve essere presente il sistema tipo nel nuovo spazio di lavoro prima di caricare i dizionari.

Per caricare i dizionari, apri la scheda **Dictionaries** e aggiungi un file `CSV` che hai scaricato o carica il file `ZIP`.

## Documenti
{: #wks_exportimport_expimp_doc}

Per scaricare i documenti che hai aggiunto al corpus, apri la scheda **Assets**> **Documents** > **Document Sets** e fai clic su **Download Document Sets**. Il sistema crea un file denominato `corpus-ID.zip` e ti richiede di scaricarlo nel tuo sistema locale. Il file `ZIP` contiene tutti i documenti nel corpus. Le annotazioni che sono state aggiunte alle serie di annotazioni sono incluse nel file ZIP, ma solo dopo che le serie di annotazioni sono state approvate e promosse a ground truth.

> **Limitazione:** tutti i documenti che sono stati pre-annotati saranno oscurati in un formato non leggibile quando vengono scaricati. Anche le annotazioni in questi documenti che sono state aggiunte dall'annotazione umana non sono leggibili.

Prima di caricare i documenti che includono il ground truth in un nuovo spazio di lavoro, devi scaricare il sistema tipo dal vecchio spazio di lavoro e caricarlo nel nuovo. Il sistema tipo e i documenti devono essere originati dallo stesso spazio di lavoro {{site.data.keyword.knowledgestudioshort}} e deve essere presente il sistema tipo nel nuovo spazio di lavoro prima di caricare le annotazioni ground truth.

Per caricare i documenti, apri la scheda **Document Sets** nel nuovo spazio di lavoro, fai clic su **Upload Document Sets** e seleziona il file `ZIP` del corpus che hai scaricato. Specifica se vuoi che i documenti scaricati includano o escludano le annotazioni ground truth prima di far clic su **Upload**. Saranno caricate solo le annotazioni che sono state promosse a ground truth prima che sono stati scaricati i documenti.

**Concetti correlati**:

[Tipi di risorse ](/docs/services/watson-knowledge-studio/artifacts.html)

[Aggiunta di documenti per l'annotazione ](/docs/services/watson-knowledge-studio/documents-for-annotation.html)

[Aggiunta di documenti per la definizione delle regole ](/docs/services/watson-knowledge-studio/rule-annotator-add-doc.html)
