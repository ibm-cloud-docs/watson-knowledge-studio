---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-16"

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

Questa documentazione è per {{site.data.keyword.knowledgestudiofull}} su {{site.data.keyword.cloud}}. Per visualizzare la documentazione della versione precedente di {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace, [fai clic su questo link ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/docs/services/knowledge-studio/tutorials-create-project.html){: new_window}.
{: tip}

# Introduzione a {{site.data.keyword.knowledgestudioshort}}
{: #wks_tutintro}

Questa esercitazione di {{site.data.keyword.knowledgestudiofull}} ti aiuta ad eseguire le attività prerequisite che devono essere completate prima di poter iniziare qualsiasi altra esercitazione.
{: shortdesc}

## Prima di cominciare
{: #prereq}

- Conferma di stare utilizzando un browser supportato. Per informazioni, consulta [Requisiti del browser](/docs/services/watson-knowledge-studio/system-requirements.html).
-  Per completare questa esercitazione, devi avere almeno un ID utente che puoi utilizzare in {{site.data.keyword.knowledgestudioshort}}. Questo ID utente deve avere il ruolo di amministratore. Se sei registrato a un piano Lite, come unico utente, avrai il ruolo di amministratore. Per informazioni sui ruoli utente, vedi [Assemblaggio di team](/docs/services/watson-knowledge-studio/team.html).

## Creazione di un'istanza del servizio
{: #instance}

1. Se non lo sei già, [registrati in {{site.data.keyword.ibmid}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}){: new_window} e accedi a {{site.data.keyword.cloud_notm}}.
1. Dalla pagina dei servizi {{site.data.keyword.cloud_notm}} {{site.data.keyword.watson}} [ ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/developer/watson/services){: new_window} fai clic sul tile {{site.data.keyword.knowledgestudioshort}} e registrati per un piano.
1. Dopo che ti sei registrato a un piano, dall'elenco dei servizi esistenti, avvia {{site.data.keyword.knowledgestudioshort}}.

## Lezione 1: Assegnazione dei ruoli utente
{: #wks_tutless1}

In questa lezione, apprenderai quali sono i ruoli differenti che puoi assegnare agli utenti in {{site.data.keyword.knowledgestudioshort}}.

### Informazioni su quest'attività
{: #wks_tutless1_about}

La creazione di un modello di machine learning richiede l'input dagli esperti in materia, dai gestori del progetto e dagli utenti che possono comprendere ed interpretare i modelli statistici. Gli amministratori assegnano i ruoli ad ogni utente, in modo che abbiano l'autorità appropriata per loro attività. Per ulteriori informazioni sui ruoli utente, vedi [Assemblaggio di team](/docs/services/watson-knowledge-studio/team.html).

### Procedura
{: #wks_tutless1_procedure}

1. Accedi a {{site.data.keyword.knowledgestudioshort}} con il tuo ID amministratore. Se già hai un'istanza di {{site.data.keyword.knowledgestudioshort}} esistente, puoi trovarla nella pagina dei servizi {{site.data.keyword.cloud_notm}} {{site.data.keyword.watson}} [ ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/developer/watson/services){: new_window}.
1. Fai clic sull'icona delle impostazioni per aprire la pagina Service Details. La pagina elenca tutti gli ID utente che sono registrati come utenti {{site.data.keyword.knowledgestudioshort}}. Ogni ID utente ha uno dei seguenti ruoli (in ordine decrescente di autorizzazioni incluse):

    - Amministratore
    - Gestore progetto
    - Annotatore umano

    Per informazioni sui ruoli utente, consulta [Ruoli utente in {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio/roles.html).

1. Verifica che ci sia almeno un utente con il ruolo di amministratore. Un ID utente con questo ruolo può creare gli spazi di lavoro e agire come un gestore del progetto o un annotatore umano.
1. Se hai accesso a ulteriori ID utente, verifica che ci siano almeno due utenti con il ruolo di annotatore umano.

    > **Nota:** la creazione di un modello reale normalmente implica più annotatori umani in aggiunta a un amministratore o a un gestore del progetto. Tuttavia, per gli scopi dell'esercitazione, puoi continuare con un solo ID utente.

1. Facoltativo: modifica il ruolo assegnato a un ID utente. Dalla colonna **Action** della tabella, fai clic sul link **Edit** e poi modifica il ruolo utente assegnato.

    > **Nota:** puoi eseguire l'upgrade di un ID utente a un ruolo con autorizzazioni maggiori ma non puoi eseguire il downgrade di un utente con ruolo di amministratore o di gestore del progetto a un ruolo di annotatore umano.

## Lezione 2: Creazione di uno spazio di lavoro
{: #wks_tutless2}

In questa lezione, apprenderai come creare uno spazio di lavoro all'interno di {{site.data.keyword.knowledgestudioshort}}.

### Informazioni su quest'attività
{: #wks_tutless2_about}

Uno spazio di lavoro definisce tutte le risorse necessarie per creare un modello di machine learning, inclusi i documenti preparati, il sistema tipo, i dizionari e le annotazioni che sono state aggiunte dagli annotatori umani. Per ulteriori informazioni sulla creazione di uno spazio di lavoro, vedi [Creazione di uno spazio di lavoro](/docs/services/watson-knowledge-studio/create-project.html).

### Procedura
{: #wks_tutless2_procedure}

1. Come amministratore di {{site.data.keyword.knowledgestudioshort}}, dal tuo {{site.data.keyword.cloud_notm}}dashboard [ ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}){:new_window}, avvia il servizio {{site.data.keyword.knowledgestudioshort}}.
1. Fai clic su **Create Worskpace**.
1. Specifica i dettagli del nuovo spazio di lavoro:

    - Nel campo **Workspace name**, immetti `My workspace`.
    - Nel campo **Workspace description**, immetti `Watson Knowledge Studio tutorial workspace`.
    - Nel campo **Language of documents**, utilizza il valore predefinito **English**. I file di esempio che utilizzerai per questa esercitazione sono in inglese.

1. Fai clic su **Create**.

### Risultati
{: #wks_tutless2_results}

Lo spazio di lavoro viene creato e si apre automaticamente.

### Operazioni successive
{: #wks_tutless2_next}

Puoi ora iniziare a configurare le risorse dello spazio di lavoro, come il sistema tipo.

## Lezione 3: Creazione di un sistema tipo
{: #wks_tutless3}

In questa lezione, apprenderai come caricare e modificare un sistema tipo in {{site.data.keyword.knowledgestudioshort}}. Devi creare o caricare un sistema tipo prima di iniziare qualsiasi attività di annotazione.

### Informazioni su quest'attività
{: #wks_tutless3_about}

Per ulteriori informazioni sui sistemi tipo, vedi [Sistemi tipo](/docs/services/watson-knowledge-studio/typesystem.html#wks_typesystem).

### Procedura
{: #wks_tutless3_procedure}

1. Scarica il file <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/en-klue2-types.json" download>en-klue2-types.json<img src="../../icons/launch-glyph.svg" alt="Icona link esterno" title="Icona link esterno" class="style-scope doc-content"></a> sul tuo computer. Questo file contiene un sistema tipo KLUE di esempio.
1. Fai clic su **Assets**> **Entity Types**.
1. Nella pagina Entity Types, fai clic su **Upload**.
1. Carica il file `en-klue2-types.json` dal tuo computer. Il sistema tipo caricato viene visualizzato nella tabella.
1. Sfoglia il sistema tipo così puoi visualizzare i dati che sono stati caricati.
1. Modifica un tipo di entità:

    1. Individua il tipo di entità MONEY.
    1. Fai doppio clic in un qualsiasi punto nella riga della tabella per modificare il tipo di entità.
    1. Nella colonna **Roles**, fai clic sull'icona **Delete a role** ![L'icona "Delete a role".](images/wks_delete.jpg "L'icona") accanto al ruolo AWARD.

        ![Un'acquisizione schermo che mostra il cursore che passa sul un tipo di entità.](images/wks_tut_delete_role.jpg "Un'acquisizione schermo che mostra il cursore che passa su ")

    1. Fai clic su **Save**.

### Operazioni successive
{: #wks_tutless3_next}

Dopo aver finito di apportare le modifiche al sistema tipo, puoi iniziare ad aggiungere i documenti al tuo spazio di lavoro.

## Lezione 4: Aggiunta di un dizionario
{: #wks_tutless4}

In questa lezione, apprenderai come aggiungere un dizionario a uno spazio di lavoro in {{site.data.keyword.knowledgestudioshort}}. I dizionari sono utilizzati per la pre-annotazione del testo quando crei un modello di machine learning.

### Informazioni su quest'attività
{: #wks_tutless4_about}

Per ulteriori informazioni sui dizionari, consulta [Aggiunta di dizionari a uno spazio di lavoro](/docs/services/watson-knowledge-studio/dictionaries.html#wks_projdictionaries).

### Procedura
{: #wks_tutless4_procedure}

1. Scarica il file <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/dictionary-items-organization.csv" download>`dictionary-items-organization.csv` <img src="../../icons/launch-glyph.svg" alt="Icona link esterno" title="Icona link esterno" class="style-scope doc-content"></a> sul tuo computer. Questo file contiene i termini nel formato CSV, adatto per il caricamento in un dizionario {{site.data.keyword.knowledgestudioshort}}.
1. Fai clic su **Assets** > **Dictionaries**.
1. Fai clic su **Create Dictionary** per aggiungere un dizionario.

    > **Nota:** non fare clic su **Upload dictionary**, che viene utilizzato per caricare un dizionario che vuoi utilizzare così come è. Per l'esercitazione, creerai un nuovo dizionario modificabile e poi caricherai i termini in esso.

1. Nel campo **Name**, immetti `Test dictionary` e fai clic su **Save** per creare il dizionario (vuoto).

    Il nuovo dizionario viene creato e automaticamente aperto per la modifica.

1. Nel pannello del dizionario, fai clic su **Upload**.
1. Carica il file `dictionary-items-organization.csv` dal tuo computer. I termini nel file vengono caricati nel dizionario.
1. Fai clic su **Add Entry** per creare un nuovo termine. Viene aggiunta una riga modificabile all'inizio della tabella.
1. Nella colonna **Surface Forms**, immetti `IBM` e `International Business Machines Corporation` in righe separate. (Quando inizi a immettere un nuovo formato di superficie, viene aggiunto uno spazio sottostante per un ulteriore formato di superficie.) Lascia il pulsante di opzione accanto a `IBM` selezionato, che indica che `IBM` è il lemma.
1. Nella colonna **Part of Speech**, seleziona **Noun**.
1. Fai clic su **Save**.

    ![Una schermata di una pagina Dictionaries. Viene selezionata una voce del dizionario "IBM" e i relativi formati di superficie e parte del discorso vengono evidenziati.](images/wks_tutdict4.jpg "Una schermata di una pagina Dictionaries. ")

### Operazioni successive
{: #wks_tutless4_next}

Dopo aver creato un dizionario, puoi utilizzarlo per velocizzare le attività di annotazione umana pre-annotando i documenti.

## Riepilogo esercitazione
{: #wks_tutsum}

Mentre imparavi ad utilizzare {{site.data.keyword.knowledgestudioshort}}, hai creato uno spazio di lavoro e aggiunto le risorse ad esso.

### Lezione imparate
{: #lessons_learned}

Completando questa esercitazione, hai imparato i seguenti concetti:

- Spazi di lavoro
- Sistemi tipo
- Dizionari
