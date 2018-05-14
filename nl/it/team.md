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

Questa documentazione è per {{site.data.keyword.knowledgestudiofull}} su {{site.data.keyword.cloud}}. Per visualizzare la documentazione della versione precedente di {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace, [fai clic su questo link ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/docs/services/knowledge-studio/team.html){: new_window}.
{: tip}

# Assemblaggio di un team 
{: #team}

La creazione di un modello richiede l'input dagli esperti in materia, dai gestori del progetto e dagli utenti che possono comprendere ed interpretare i modelli statistici. Devi aggiungere un utente in {{site.data.keyword.knowledgestudioshort}} per ogni persona che ha bisogno di accedere.
{: shortdesc}

**Nota**: solo i piani standard e premium possono aggiungere gli utenti. I piani gratuiti sono limitati a un utente. Per via del solo utente, a tale persona viene assegnato il ruolo con l'autorizzazione più alta, ovvero il ruolo di amministratore.

## Prima di cominciare

- Assicurati di stare utilizzando un browser supportato. Per informazioni, consulta [Requisiti del browser](/docs/services/watson-knowledge-studio/system-requirements.html).
- [Crea un'istanza di {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/tutorials-create-project.html#instance).
- Se sei registrato per un piano standard o premium, dalla scheda {{site.data.keyword.cloud_notm}} **Manage**, invita altri utenti alla tua organizzazione che vuoi aggiungere come utenti in {{site.data.keyword.knowledgestudioshort}}. Per ulteriori informazioni sull'invito degli utenti, consulta [Invito di utenti e assegnazione dell'accesso ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/docs/iam/iamuserinv.html){: new_window}.

  **Importante**: 

  - Assicurati che gli utenti invitati abbiano il ruolo Cloud Foundry di **Sviluppatore**. Per ulteriori informazioni, vedi [Accesso Cloud Foundry ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/docs/iam/cfaccess.html){: new_window}.
  - Al primo utente che avvia {{site.data.keyword.knowledgestudioshort}} viene concesso il ruolo di amministratore dell'istanza {{site.data.keyword.knowledgestudioshort}}. Questa attività presuppone che tu sei la prima persona ad avviare {{site.data.keyword.knowledgestudioshort}} dopo esserti registrato a un piano, il che significa che hai ruolo di amministratore.

## Informazioni su quest'attività

Generalmente, aggiungi gli utenti per coprire i seguenti ruoli.

**Nota:** se sei registrato a un piano gratuito, non puoi aggiungere altri utenti alla tua istanza di {{site.data.keyword.knowledgestudioshort}}. Invece, quando avvii {{site.data.keyword.knowledgestudioshort}}, sei aggiunto all'istanza con il ruolo di amministratore. Con il ruolo di amministratore, puoi eseguire molte funzioni che generalmente vengono eseguite da altre persone che hanno assegnati ruoli diversi. Puoi verificare quanti esperti da aree diverse di un dominio possono lavorare insieme per creare un modello di machine learning o basato sulla regola.

- **Annotatore umano**

    Gli annotatori umani sono generalmente esperti in materia che controllano i documenti di un dominio specifico per identificare le entità e le relazioni di interesse del dominio. Questi utenti interagiscono con l'applicazione in un modo limitato. Utilizzano l'editor ground truth per annotare una serie di documenti che sono stati assegnati loro.

- **Gestore del progetto**

    I gestori del progetto sono persone che facilitano la creazione dei modelli eseguendo attività come la creazione delle risorse dello spazio di lavoro e la preparazione, creazione e distribuzione dei modelli. Per gli spazi di lavoro che sono utilizzati per creare gli annotatori di machine learning, i gestori del progetto gestiscono inoltre il processo di annotazione del documento assegnando le attività di controllo del documento agli annotatori umani, giudicando i conflitti di annotazione e approvando i documenti da aggiungere al ground truth.

## Aggiunta di utenti in {{site.data.keyword.knowledgestudioshort}}

Aggiungi gli utenti dalla tua organizzazione {{site.data.keyword.cloud_notm}} a {{site.data.keyword.knowledgestudioshort}}.

**Nota**: solo i piani standard e premium possono aggiungere gli utenti. I piani gratuiti sono limitati a un utente. 

Per aggiungere gli utenti a un'istanza di {{site.data.keyword.knowledgestudioshort}}:

1. Accedi al dashboard [{{site.data.keyword.cloud_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/dashboard/apps/){: new_window} con il tuo {{site.data.keyword.ibmid}} e avvia {{site.data.keyword.knowledgestudioshort}}.
1. Fai clic sull'icona **Settings** e poi su **View/modify service details**.
1. Nella sezione **Manager users**, immetti l'{{site.data.keyword.ibmid}} dell'utente che vuoi aggiungere.
1. Seleziona il ruolo che vuoi dare all'utente.

   Nota: non puoi eseguire il downgrade dei ruoli utente dopo che li hai assegnati, per cui assicurati di comprendere le attività che ogni ruolo può eseguire quando assegni il ruolo di amministratore e di gestore del progetto.

1. Fai clic su **Add**.

## Upgrade dei ruoli utente

Dopo che hai aggiunto gli utenti a {{site.data.keyword.knowledgestudioshort}}, puoi eseguire l'upgrade dei ruoli inferiori a quelli superiori. Gli utenti devono essere assegnati ai ruoli descritti di seguito per poter eseguire le rispettive attività.

**Nota**: solo i piani standard e premium possono eseguire l'upgrade degli utenti. I piani gratuiti sono limitati a un utente che già dispone del ruolo più elevato, amministratore. 

> **Attenzione: il downgrade da un ruolo superiore a uno inferiore non è consentito.**

Per eseguire l'upgrade dei ruoli per gli utenti di {{site.data.keyword.knowledgestudioshort}}:

1. Accedi al dashboard [{{site.data.keyword.cloud_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/dashboard/apps/){: new_window} con il tuo {{site.data.keyword.ibmid}} e avvia {{site.data.keyword.knowledgestudioshort}}.
1. Dal menu di navigazione in alto a destra, fai clic sull'icona **Settings** ![the Settings icon](images/settings.png) e poi su **View/modify service details**. La sezione **Manage users** della pagina Service Details elenca tutti gli ID utente che sono utenti di questa istanza di {{site.data.keyword.knowledgestudioshort}}.
1. Trova il nome dell'utente che vuoi modificare e fai clic sul link **Edit**.

    {{site.data.keyword.knowledgestudioshort}} ha i seguenti ruoli, che sono elencati dal livello di privilegi più alto al più basso:
    - **Amministratore**

      Gli utenti appartenenti a questo ruolo possono eseguire le seguenti attività:

        - Gestire una sottoscrizione, come aggiungere le funzioni, l'archiviazione e ulteriori utenti.
        - Fornire agli utenti l'accesso a una sottoscrizione dalla pagina Service Details
        - Creare e gestire tutti gli spazi di lavoro nelle loro sottoscrizioni
        - Assegnare alle persone i ruoli di gestore del progetto e di annotatore umano di tutti gli spazi di lavoro.

    - **Gestore del progetto**

      Gli utenti con questo ruolo possono effettuare le seguenti attività:

      - Gestire gli spazi lavoro a cui sono stati aggiunti
      - Assegnare gli annotatori umani a uno spazio di lavoro

      Gli utenti con questo ruolo non possono effettuare le seguenti attività: 

      - Creare gli spazi di lavoro
      - Gestire i ruoli e l'accesso dell'utente dalla pagina Service Details

    - **Annotatore umano**

      Gli utenti con questo ruolo possono annotare i documenti presenti negli spazi di lavoro a cui sono assegnati e in una serie di documenti associata alle attività di annotazione a cui sono assegnati.

      **Importante:** devi creare uno spazio di lavoro, associare un utente a una serie di documenti e assegnare un'attività di annotazione a un utente prima che un utente con il ruolo **Annotatore umano** possa visualizzare gli spazi di lavoro elencati nell'applicazione {{site.data.keyword.knowledgestudioshort}}. Configura lo spazio di lavoro il prima possibile dopo la registrazione degli utenti in modo che possano visualizzare il tuo spazio di lavoro al loro primo accesso all'applicazione. Potresti voler avvertire gli utenti dopo aver configurato lo spazio di lavoro per fargli sapere che possono iniziare ad annotare i documenti.

1. Fai clic sul ruolo dell'utente e scegli il ruolo a cui vuoi eseguire l'upgrade per tale utente.
1. Facoltativo: quando finisci di gestire gli utenti in {{site.data.keyword.knowledgestudioshort}}, esci dalla sessione chiudendo il browser web. L'interfaccia utente {{site.data.keyword.knowledgestudioshort}} non fornisce un'azione per scollegarsi in modo esplicito.

## Disattivazione degli account dell'utente

Successivamente, se vuoi rimuovere gli utenti, segui i passi precedenti per riaprire la pagina Service Details. Dall'elenco degli ID utente, trova l'utente che vuoi rimuovere e fai clic su **Deactivate**.

> **Attenzione**: se gli utenti sono assegnati a dei documenti per l'annotazione e disattivi i loro account, ne saranno influenzate le loro annotazioni. Se le annotazioni effettuate dagli utenti disattivati non sono state promosse al ground truth, vengono eliminate.

### Attività correlate

[Creazione e assegnazione delle serie di annotazioni](/docs/services/watson-knowledge-studio/documents-for-annotation.html#wks_projdocsets)
