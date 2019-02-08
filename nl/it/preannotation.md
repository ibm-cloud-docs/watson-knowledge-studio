---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-13"

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

Questa documentazione è per {{site.data.keyword.knowledgestudiofull}} su {{site.data.keyword.cloud}}. Per visualizzare la documentazione della versione precedente di {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace, [fai clic su questo link ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/docs/services/knowledge-studio/preannotation.html){: new_window}.
{: tip}

# Inizio dell'annotazione
{: #preannotation}

Semplifica il lavoro dell'annotatore umano pre-annotando i documenti in uno spazio di lavoro. Un pre-annotatore è un dizionario {{site.data.keyword.knowledgestudioshort}}, un modello basato sulla regola o un modello di machine learning che esegui per trovare e annotare le citazioni automaticamente.
{: shortdesc}

La pre-annotazione rende il lavoro degli annotatori umani più semplice perché copre le annotazioni più semplici e inizia il lavoro di annotazione dei documenti.

Il metodo che utilizzi per pre-annotare i documenti non limita in alcun modo i modi in cui puoi utilizzare il modello risultante. Ad esempio, solo perché utilizzi il servizio {{site.data.keyword.nlushort}} per pre-annotare i documenti non significa che devi distribuire il modello di machine learning finale che crei per il servizio {{site.data.keyword.nlushort}}. La pre-annotazione è pensata solo per iniziare il processo di annotazione umana.

## Note importanti
{: #preannotation_notes}

- Non eseguire mai un pre-annotatore sui documenti che gli annotatori umani hanno annotato perché le annotazioni da loro aggiunte saranno rimosse.
- Puoi eseguire solo un pre-annotatore sui documenti. Se esegui un pre-annotatore e poi un altro, il secondo rimuoverà le annotazioni che sono state aggiunte dal primo. Scegli il metodo di pre-annotazione che si adatta meglio al tuo caso e utilizza solo un pre-annotatore.

## Metodi di pre-annotazione
{: #preannotation_methods}

Sono disponibili i seguenti pre-annotatori:

- **{{site.data.keyword.nlushort}}**

    Un pre-annotatore che puoi utilizzare per trovare le citazioni di entità nei tuoi documenti automaticamente. Se i tuoi documenti di origine hanno una conoscenza sulla materia generale, questo pre-annotatore è una buona scelta. Se stai lavorando con documenti altamente specializzati che si concentrano su un campo specifico, come la ricerca di brevetti, ad esempio, il dizionario pre-annotatore o il modello basato sulla regola potrebbe essere una scelta migliore.

- **Dizionario**

    Utilizza un dizionario dei termini che fornisci e associ a un tipo di entità per trovare le citazioni di tale tipo di entità nei documenti. Questa scelta è la migliore per i campi con terminologia specializzata o unica perché questo pre-annotatore non analizza il contesto in cui viene utilizzato il termine nel modo fatto dal pre-annotatore di machine learning; invece si basa sul termine che viene distinto sufficientemente da avere un significato decifrabile indipendentemente dal contesto in cui viene utilizzato. Ad esempio, è facile riconoscere *asbestos* come un tipo di entità di un minerale, rispetto a determinare il tipo di entità di *squash*, che fa riferimento a uno sport o a un verbo con il significato di schiacciare qualcosa.

- **Machine learning**

    Utilizza un modello di machine learning per annotare automaticamente i documenti. Questa opzione è disponibile solo se hai già creato un modello di machine learning con {{site.data.keyword.knowledgestudioshort}}. Se aggiungi una nuova serie di documenti, puoi eseguire l'annotatore di machine learning che hai creato precedentemente per pre-annotare i nuovi documenti. Se la nuova serie di documenti è simile ai documenti che sono stati utilizzati per preparare l'annotatore di machine learning originariamente, questa è probabilmente la tua migliore scelta per la pre-annotazione.

- **Regola**

    Utilizza un modello basato sulla regola per annotare automaticamente i documenti. Questa opzione è disponibile solo se hai già creato un modello basato sulla regola con {{site.data.keyword.knowledgestudioshort}}. Se i tuoi documenti contengono modelli comuni di token da cui derivare il significato, questo modello potrebbe essere una buona scelta. Può incorporare alcune funzioni del pre-annotatore del dizionario se lo abiliti, identificando inoltre i tipi di classe dei termini del dizionario che trova nei documenti.

In alternativa, puoi caricare documenti già annotati e utilizzarli per iniziare la preparazione del modello di machine learning. Non puoi eseguire un pre-annotatore sui documenti annottati che carichi o le annotazioni esistenti saranno eliminate dai documenti e sostituite soltanto con le annotazioni prodotte dal pre-annotatore.

> **Nota:** *puoi* eseguire un pre-annotatore sui documenti che sono stati aggiunti al ground truth come parte dello spazio di lavoro corrente. Le annotazioni che sono state aggiunte ai documenti, revisionate, accettate e promosse a ground truth all'interno dello spazio di lavoro non vengono eliminate.

## Pre-annotazione dei documenti con {{site.data.keyword.nlushort}}
{: #wks_preannotnlu}

Puoi utilizzare il servizio {{site.data.keyword.nlushort}} per pre-annotare i documenti che aggiungi al tuo corpus.

### Prima di cominciare
{: #wks_preannotnlu_prereqs}

Determina se il pre-annotatore {{site.data.keyword.nlushort}} è presumibile che aggiunga valore al tuo caso di utilizzo. Controlla l'elenco di sottotipi e tipi di entità [{{site.data.keyword.nlushort}} supportati ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/docs/services/natural-language-understanding/entity-types.html){: new_window} per determinare se è presente una sovrapposizione naturale tra loro e i tipi nel tuo sistema tipo. Se è così, continua con questa procedura. Se non lo è, scegli un pre-annotatore diverso da utilizzare.

### Informazioni su quest'attività
{: #wks_preannotnlu_about}

{{site.data.keyword.nlushort}} è un servizio che offre l'analisi del testo tramite l'elaborazione del linguaggio naturale. Quando utilizzi il pre-annotatore {{site.data.keyword.nlushort}}, richiama il servizio {{site.data.keyword.nlushort}} per trovare e annotare automaticamente le entità nei tuoi documenti.

Devi specificare i tipi di entità che desideri il servizio ricerchi associando i tipi di entità {{site.data.keyword.nlushort}} ai corrispondenti tipi di entità {{site.data.keyword.knowledgestudioshort}} che hai aggiunto al sistema tipo {{site.data.keyword.knowledgestudioshort}}. Solo le citazioni dei tipi di entità che associ saranno trovate e annotate.

### Procedura
{: #wks_preannotnlu_procedure}

Per utilizzare il servizio {{site.data.keyword.nlushort}} per pre-annotare i documenti, completa la seguente procedura:

1. Accedi come amministratore {{site.data.keyword.knowledgestudioshort}} e seleziona il tuo spazio di lavoro.
1. Seleziona la scheda **Machine Learning Model** > **Pre-annotation** > **Natural Language Understanding**.
1. Fai clic su **Edit** per associare ogni tipo di entità che viene definito nella pagina **Entity Types** ai tipi di entità corrispondenti {{site.data.keyword.nlushort}}.

    - L'elenco a discesa dei tipi di entità {{site.data.keyword.nlushort}} è pre-popolato con i tipi di entità che sono stati riconosciuti dal servizio {{site.data.keyword.nlushort}}.
    - Devi associare almeno un tipo di entità.
    - Non puoi associare un tipo di entità {{site.data.keyword.nlushort}} a un ruolo entità {{site.data.keyword.knowledgestudioshort}}, solo ai tipi di entità {{site.data.keyword.knowledgestudioshort}}.
    - Puoi associare più di un tipo di entità {{site.data.keyword.nlushort}} a un solo tipo di entità {{site.data.keyword.knowledgestudioshort}} o il contrario. Ad esempio, le seguenti associazioni sono consentite:

    <table summary="Associazione di esempio dei tipi di entità">
    <caption>Tabella 1. Associazione di esempio dei tipi di entità</caption>
      <tr>
        <th style="vertical-align:bottom; text-align"left" id="d20428e292">Watson Knowledge Studio Entity Type</th>
        <th style="vertical-align:bottom; text-align"left" id="d20428e298">Tipo di entità {{site.data.keyword.nlushort}}</th>
      </tr>
      <tr>
        <td headers="d20428e292">
          ENGINEER<br/>
          SCIENTIST
        </td>
        <td headers="d20428e298">
          Person
        </td>
      </tr>
      <tr>
        <td headers="d20428e292">
          LOCATION
        </td>
        <td headers="d20428e298">
          CityTown<br/>
          Country
        </td>
      </tr>
    </table>
    {: #wks_preannotnlu__datasimpletable_cm1_y3g_fx}

1. Dopo aver associato tutti i tipi di entità che desideri applicare, fai clic su **Apply This Pre-annotator**.

    Il pulsante **Apply This Pre-annotator** non è disponibile finché non associ almeno un tipo di entità.

1. Seleziona la casella di spunta di ogni serie di documenti che vuoi pre-annotare.

    Se stai eseguendo questo pre-annotatore per la prima volta, controlla prima che il pre-annotatore possa trovare le citazioni delle entità associate come previsto. Crea una serie di documenti che contiene uno o più documenti rappresentativi da ogni origine dati distinta.
    {: tip}

1. Fai clic su **Run**.

    Se stai eseguendo un controllo di convalida del pre-annotatore, apri i documenti annotati e controlla le annotazioni che sono state aggiunte. Assicurati che sia stato creato un numero sufficiente di annotazioni accurate. Se le annotazioni sono accurate, puoi eseguire nuovamente l'annotatore su serie di documenti più grandi. Se le annotazioni non sono accurate, considera l'associazione di tipi di entità {{site.data.keyword.nlushort}} differenti rispetto ai tuoi tipi. Se i tipi non si sovrappongono naturalmente, il pre-annotatore {{site.data.keyword.nlushort}} non è quello migliore per il tuo utilizzo.

    La pre-annotazione viene applicata ai singoli documenti senza tenere conto delle varie serie di documenti a cui potrebbe appartenere un documento. Un documento che si sovrappone tra una serie di documenti selezionata e una non selezionata sarà pre-annotato in entrambe.

1. Dopo aver eseguito il pre-annotatore una volta, puoi fare clic su **Apply This Pre-annotator** ogni volta che vuoi utilizzarlo per pre-annotare le ulteriori serie di documenti che aggiungi al corpus.

    > **Limitazione:** se modifichi la definizione dell'associazione del tipo del pre-annotatore {{site.data.keyword.nlushort}}, devi ricreare le attività di annotazione che includono le serie di documenti pre-annotate. La pre-annotazione basata sulle modifiche che effettui alla definizione di associazione del pre-annotatore non può essere applicata alle serie di documenti che sono già assegnate a un'attività di annotazione.

### Risultati
{: #wks_preannotnlu__export-warning}

Il ground truth che viene prodotto dai documenti che sono stati pre-annotati dal servizio {{site.data.keyword.nlushort}} non può essere utilizzato direttamente al di fuori di {{site.data.keyword.knowledgestudioshort}}. Puoi scaricare il ground truth (in un formato non leggibile) per spostarlo da uno spazio di lavoro {{site.data.keyword.knowledgestudioshort}} a un altro. E puoi continuare a sviluppare il ground truth e utilizzarlo per creare un modello di machine learning o basato sulla regola che può essere distribuito per l'utilizzo nei servizi al di fuori di {{site.data.keyword.knowledgestudioshort}}.

> **Limitazione:** i documenti che sono stati pre-annotati con {{site.data.keyword.nlushort}} sono oscurati in un formato non leggibile quando vengono scaricati. Ma sono state oscurate tutte le annotazioni in questi documenti, incluse quelle che sono state aggiunte dagli annotatori umani.

**Informazioni correlate**:

[{{site.data.keyword.nlushort}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/watson/services/natural-language-understanding/){: new_window}

## Pre-annotazione dei documenti con un dizionario
{: #wks_preannot}

Per aiutare gli annotatori umani ad iniziare le loro attività di annotazione, puoi creare un dizionario e utilizzarlo per pre-annotare i documenti che aggiungi al corpus.

### Informazioni su quest'attività
{: #wks_preannot_about}

Quando un annotatore umano inizia a lavorare sui documenti che sono stati pre-annotati, è probabile che molte citazioni siano state già contrassegnate dai tipi di entità in base alle voci del dizionario. L'annotatore umano può modificare o rimuovere i tipi di entità pre-annotati e assegnarne alle citazioni non annotate. La pre-annotazione di un dizionario non annota le relazioni e le coreferenze. Le relazioni e le coreferenze devono essere annotate dagli annotatori umani.

**Nota**: questa attività mostra come creare un dizionario modificabile. Se vuoi caricare e pre-annotare i tuoi documenti con un dizionario in sola lettura, fai clic sull'icona **Menu** accanto al pulsante **Create Dictionary**. Seleziona **Upload Dictionary**.

### Procedura
{: #wks_preannot_procedure}

Per creare un dizionario modificabile e pre-annotare i documenti:

1. Accedi come amministratore {{site.data.keyword.knowledgestudioshort}} e seleziona il tuo spazio di lavoro.
1. Seleziona la pagina **Assets** > **Dictionaries**.
1. Fai clic su **Create Dictionary**, immetti un nome e poi fai clic su **Save**.
1. Dall'elenco **Entity type**, seleziona un tipo di entità da associare al dizionario.
3. Aggiungi le voci al dizionario o carica un file che contiene i termini del dizionario.
4. Fai clic su **Machine Learning Model** > **Pre-annotation**.
5. Nella scheda **Dictionaries**, fai clic su **Apply This Pre-annotator**.
6. Seleziona la casella di spunta di ogni serie di documenti che vuoi pre-annotare e fai clic su **Run**.

    La pre-annotazione viene applicata ai singoli documenti senza tenere conto delle varie serie di documenti o annotazioni a cui potrebbe appartenere un documento. Un documento che si sovrappone tra una serie di documenti selezionata e una non selezionata sarà pre-annotato in entrambe.

7. Dopo avere creato il dizionario, fai clic su **Run** ogni volta che vuoi utilizzarlo per pre-annotare ulteriori serie di documenti che aggiungi al corpus.

    > **Limitazione:** se modifichi il dizionario per aggiungere o rimuovere le voci, devi ricreare le attività di annotazione che includono le serie di documenti pre-annotati. La pre-annotazione basata sulle modifiche che effettui all'annotatore del dizionario non possono essere applicate alle serie di annotazioni che sono già state assegnate a un'attività di annotazione.

**Informazioni correlate**:

[Creazione dei dizionari](/docs/services/watson-knowledge-studio/dictionaries.html)

[Introduzione > Aggiunta di un dizionario](/docs/services/watson-knowledge-studio/tutorials-create-project.html#wks_tutless4)

## Pre-annotazione dei documenti con il modello di machine learning
{: #wks_preannotsire}

Puoi utilizzare un modello di machine learning esistente per pre-annotare i documenti che aggiungi al tuo corpus.

### Informazioni su quest'attività
{: #wks_preannotsire_about}

Dopo aver annotato tra i 10 e i 30 documenti, un modello di machine learning può essere preparato con i dati. Un modello poco preparato non dovrebbe essere utilizzato nella produzione, ma può essere utilizzato per pre-annotare i documenti per velocizzare l'annotazione umana dei successivi documenti. Ad esempio, se aggiungi i documenti al corpus dopo aver preparato un modello di machine learning, puoi utilizzarlo per pre-annotare le nuove serie di documenti. Non eseguire mai un pre-annotatore sugli stessi documenti che sono stati annotati da una persona. I pre-annotatori rimuovono l'annotazione umana.

### Procedura
{: #wks_preannotsire_procedure}

Per utilizzare un modello di machine learning esistente per pre-annotare i documenti:

1. Accedi come amministratore {{site.data.keyword.knowledgestudioshort}} e seleziona il tuo spazio di lavoro.
2. Seleziona **Machine Learning Model** > **Versions**.
3. Per pre-annotare nuovi documenti, fai clic su **Run this model**.
4. Seleziona la casella di spunta di ogni serie di documenti che vuoi pre-annotare e fai clic su **Run**.

    La pre-annotazione viene applicata ai singoli documenti senza tenere conto delle varie serie di documenti o annotazioni a cui potrebbe appartenere un documento. Un documento che si sovrappone tra una serie di documenti selezionata e una non selezionata sarà pre-annotato in entrambe.

5. Puoi fare clic su **Run this model** ogni volta che vuoi utilizzare il modello di machine learning per pre-annotare le ulteriori serie di documenti che aggiungi al corpus.

## Pre-annotazione dei documenti con il modello basato sulla regola
{: #wks_preannotrule}

Puoi utilizzare un modello basato sulla regola esistente per pre-annotare i documenti che aggiungi al tuo corpus.

### Procedura
{: #wks_preannotrule_procedure}

Per utilizzare il modello basato sulla regola per pre-annotare i documenti, completa la seguente procedura:

1. Accedi come amministratore {{site.data.keyword.knowledgestudioshort}} e seleziona il tuo spazio di lavoro.
1. Seleziona la scheda **Rule-based Model** > **Versions** > **Rule-based Model**.
1. Se non ancora completato, fai clic su **Map entity types and classes** per associare i tipi di entità che hai definito nel sistema tipo {{site.data.keyword.knowledgestudioshort}} a una o più classi del modello basato sulla regola.
2. Fai clic su **Edit** per ogni tipo di entità che vuoi associare.

    - L'elenco a discesa della colonna **Class Name** viene pre-popolato con le classi associate al modello basato sulla regola.
    - Devi associare almeno un tipo di entità a una classe.

3. Nella scheda **Rule-based Model**, fa clic su **Run this model**.

    Il pulsante **Run this model** non è disponibile finché non associ almeno un tipo di entità a una classe.

4. Seleziona le serie di documenti o di annotazioni che vuoi pre-annotare. Assicurati che le serie che selezioni non contengano documenti che hanno annotazioni umane. I pre-annotatori rimuovono l'annotazione umana.
5. Fai clic su **Run**.

    La pre-annotazione viene applicata ai singoli documenti senza tenere conto delle varie serie di documenti a cui potrebbe appartenere un documento. Un documento che si sovrappone tra una serie di documenti selezionata e una non selezionata sarà pre-annotato in entrambe

6. Puoi fare clic su **Run this model** ogni volta che vuoi utilizzare il modello basato sulla regola per pre-annotare le ulteriori serie di documenti che aggiungi al corpus.

    > **Limitazione:** se modifichi l'associazione tipo di entità a classe del modello basato sulla regola, devi ricreare le attività di annotazione che includono le serie di documenti pre-annotati. La pre-annotazione basata sulle modifiche che effettui alla definizione di associazione del pre-annotatore non può essere applicata alle serie di documenti che sono già assegnate a un'attività di annotazione.

## Caricamento dei documenti pre-annotati
{: #wks_uima}

Puoi avviare la preparazione del tuo modello caricando i documenti che sono stati pre-annotati tramite un motore di analisi Unstructured Information Management Architecture (UIMA).

I documenti pre-annotati devono essere nel formato di serializzazione XMI di UIMA Common Analysis Structure (UIMA CAS XMI). Il file ZIP che carichi deve includere il file descrittore UIMA TypeSystem e un file che associa i tipi UIMA ai tipi di entità nel tuo sistema tipo {{site.data.keyword.knowledgestudioshort}}.

UIMA CAS XMI è un formato standard di Apache UIMA. Vengono fornite le linee guida su come creare i file nel formato corretto dalle raccolte analizzate in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer. Se utilizzi un'altra implementazione Apache UIMA, adatta queste linee guida ai tuoi scopi. Indipendentemente da come crei i file XMI, i requisiti per la creazione del file di associazione del sistema tipo e del file ZIP sono le stesse per tutti.

Se assegni i documenti importati agli annotatori umani, i documenti vengono visualizzati come pre-annotati nell'editor ground truth e potrebbero essere stare già annotate alcune citazioni. L'annotatore umano quindi ha più tempo per concentrarsi sull'applicazione delle linee guida di annotazione per le citazioni non contrassegnate. In alternativa, puoi ignorare il passo si annotazione umana e utilizzare i documenti pre-annotati per iniziare immediatamente la preparazione e la valutazione del modello di machine learning.

### Esportazione dei documenti analizzati da Watson Explorer Content Analytics
{: #wks_uimawexca}

Puoi esportare i documenti che sono stati creati e analizzati in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer Content Analytics e caricare i documenti analizzati come file XMI in uno spazio di lavoro {{site.data.keyword.knowledgestudioshort}}.

#### Procedura
{: #wks_uima_procedure}

Per prendere i documenti analizzati da una raccolta {{site.data.keyword.watson}} Explorer Content Analytics:

1. Apri la console di gestione di Content Analytics in un browser web.
1. Nella vista Collections, espandi la raccolta da cui vuoi esportare i documenti. Nel pannello Parse and Index, assicurati che il processo di analisi e indicizzazione sia in esecuzione e poi fai clic sull'icona a forma di freccia per **Export analyzed document content and metadata**.
1. Nell'area **Analyzed document export options**, seleziona **Export documents as XML files**, seleziona la casella di spunta **Enable CAS as XMI format export**, specifica il percorso di output di dove scrivere i dati esportati e fai clic su **OK**.
1. Arresta e riavvia il servizio di analisi e indicizzazione della raccolta e poi esegui uno dei seguenti passi:

    - Se una raccolta già contiene i documenti indicizzati che vuoi utilizzare per la preparazione del modello di machine learning nella cache del documento, riavvia una creazione dell'indice completa.
    - Se una raccolta non contiene i documenti indicizzati che vuoi utilizzare per la preparazione del modello di machine learning, carica i documenti, configura almeno un crawler per creare i documenti e avvialo.

1. Nell'area **Export**, controlla lo stato della richiesta di esportazione. L'avanzamento indica quanti documenti sono stati esportati.
1. Vai alla cartella dell'output che hai specificato quando hai configurato le opzioni di esportazione. Una volta che i documenti sono stati esportati come file XML, il nome della cartella di output si basa sulla data/ora di quando si è verificata l'esportazione. La cartella di output contiene i file XMI (`*.xmi`) e il file descrittore UIMA TypeSystem (`exported_typesystem.xml`).

#### Operazioni successive
{: #wks_uimawexca__preUIMAimport}

Devi definire un'associazione tra i tipi UIMA  e i tipi di entità {{site.data.keyword.knowledgestudioshort}}. Devi anche creare un file ZIP che contiene tutti i file che sono necessari per caricare i dati analizzati nello spazio di lavoro {{site.data.keyword.knowledgestudioshort}}.

**Informazioni correlate**:

[Exporting crawled or analyzed documents ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ad.doc/iiysatexportca.htm){: new_window}

[Output paths for exported documents ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ad.doc/iiysaexportoutput.htm){: new_window}

### Esportazione di una raccolta analizzata da Content Analytics Studio
{: #wks_uimawexstudio}

Puoi esportare una raccolta di documenti analizzati da {{site.data.keyword.watson}} Explorer Content Analytics Studio e caricare i documenti analizzati come file XMI in un progetto {{site.data.keyword.knowledgestudioshort}}.

#### Procedura
{: #wks_uimawexstudio_procedure}

Per prendere i documenti analizzati da una raccolta Content Analytics Studio:

1. Avvia Content Analytics Studio e apri il progetto Studio.
1. Fai clic con il tasto destro su una cartella che contiene i documenti che vuoi utilizzare per preparare un modello di machine learning e seleziona **Analyze Collection**.
1. Seleziona un file di configurazione della pipeline UIMA.
1. Passa alla vista Collection Analysis e fai clic sull'icona **Save** nella vista Collection Analysis. Specifica la cartella in cui devono essere scritti i risultati salvati e specifica il nome del file.
1. Apri la cartella che hai specificato. L'estensione file del file salvato è `.annotations`.
1. Copia il file `.annotations` nel tuo file system locale e ridenomina l'estensione file da `.annotations` a `.zip`.
1. Estrai tutti i file dal file ZIP. I contenuti estratti includono i file XMI (`*.xmi`), il file descrittore UIMA TypeSystem (`TypeSystem.xml`) e altri file.

#### Operazioni successive
{: #wks_uimawexstudio_next}

Devi definire un'associazione tra i tipi UIMA  e i tipi di entità {{site.data.keyword.knowledgestudioshort}}. Devi anche creare un file ZIP che contiene tutti i file che sono necessari per caricare i dati analizzati nello spazio di lavoro {{site.data.keyword.knowledgestudioshort}}.

### Associazione dei tipi UIMA ai tipi di entità
{: #wks_uimawexmap}

Prima di caricare i file XMI in uno spazio di lavoro {{site.data.keyword.knowledgestudioshort}}, devi definire l'associazione tra i tipi UIMA  i tipi di entità {{site.data.keyword.knowledgestudioshort}}.

#### Prima di cominciare
{: #wks_uimawexmap_prereqs}

Il sistema tipo nel tuo spazio di lavoro {{site.data.keyword.knowledgestudioshort}} deve includere i tipi di entità a cui vuoi associare i tipi UIMA.

#### Procedura
{: #wks_uimawexmap_procedure}

Per associare i tipi UIMA ai tipi di entità {{site.data.keyword.knowledgestudioshort}}:

1. Crea un file denominato `cas2di.tsv` nella cartella che contiene il file descrittore UIMA TypeSystem, come ad esempio `exported_typesystem.xml` o `TypeSystem.xml`.
1. Apri il file `cas2di.tsv` con un editor di testo. Ogni riga nel file specifica una sola associazione. Il formato della associazione dipende da quali annotazioni dell'annotatore vuoi associare:

    - Puoi creare le associazioni utilizzando il formato di base:

        `UIMA_Type_Name[TAB]WKS_Entity_Type`

        Il seguente esempio definisce le associazioni tra i tipi UIMA prodotte dall'annotatore Named Entity Recognition in {{site.data.keyword.watson}} Explorer Content Analytics e i tipi di entità definiti in un sistema tipo {{site.data.keyword.knowledgestudioshort}}:

        ```
        com.ibm.langware.Organization  ORGANIZATION
        com.ibm.langware.Person  PERSON
        com.ibm.langware.Location  LOCATION
        ```
        {: screen}

        Un altro esempio definisce un'associazione tra i tipi UIMA prodotti dall'annotatore personalizzato che è stato creato in {{site.data.keyword.watson}} Explorer Content Analytics Studio e i tipi di entità {{site.data.keyword.knowledgestudioshort}}:

        ```
        com.ibm.Person  PERSON
        com.ibm.Date  DATE
        ```
        {: screen}

    - Puoi creare le associazioni in base ai facet utilizzati nell'annotatore Pattern Matcher o Dictionary Lookup in {{site.data.keyword.watson}} Explorer Content Analytics. Nei file della regola di analisi del testo (`*.pat`), il facet viene rappresentato come un attributo di categoria. Per definire un'associazione, utilizza la seguente sintassi:

        ```
        com.ibm.takmi.nlp.annotation_type.ContiguousContext:category={FACET_PATH}[TAB]{WKS_ENTITY_TYPE}
        ```
        {: screen}

        Il seguente esempio, che si applica agli annotatori Pattern Matcher e Dictionary Lookup, definisce un'associazione tra la categoria $.mykeyword.product e il tipo di entità {{site.data.keyword.knowledgestudioshort}} PRODUCT:

        ```
        com.ibm.takmi.nlp.annotation_type.ContiguousContext:category=$.mykeyword.product PRODUCT
        ```
        {: screen}

#### Operazioni successive
{: #wks_uimawexmap_next}

Devi creare un file ZIP che contiene tutti i file che sono necessari per caricare i dati analizzati nello spazio di lavoro {{site.data.keyword.knowledgestudioshort}}.

**Informazioni correlate**:

[Pattern Matcher annotator ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ta.doc/iiystapattmatch.htm){: new_window}

[Dictionary Lookup annotator ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ta.doc/iiystadictlookup.htm){: new_window}

[Named Entity Recognition annotator ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ta.doc/iiystasystemt.htm){: new_window}

### Caricamento dei file UIMA CAS XMI in uno spazio di lavoro
{: #wks_uimaweximport}

Per utilizzare i documenti pre-annotati che hai scaricato per preparare il modello, dvi creare un file ZIP che contiene tutti i file necessari per caricare i file XMI e poi caricare il file ZIP in uno spazio di lavoro {{site.data.keyword.knowledgestudioshort}}.

#### Prima di cominciare
{: #wks_uimaweximport_prereqs}

Prima di caricare il file ZIP, assicurati che il sistema tipo nel tuo spazio di lavoro {{site.data.keyword.knowledgestudioshort}} includa i tipi di entità a cui hai associato i tipi UIMA.

> **Avvertenza:** i motori di analisi UIMA consentono alle annotazioni di suddividere le frasi. In {{site.data.keyword.knowledgestudioshort}}, le annotazioni devono esistere nei limiti di una singola frase. Se i file XMI che carichi includono annotazioni che suddividono le frasi, tali annotazioni non vengono visualizzate nell'editor ground truth.

#### Procedura
{: #wks_uimaweximport_procedure}

Per caricare i documenti pre-annotati in uno spazio di lavoro {{site.data.keyword.knowledgestudioshort}}:

1. Crea un file ZIP che contiene tutti i file che sono necessari a {{site.data.keyword.knowledgestudioshort}}.

    1. Seleziona la cartella che contiene i file XMI, il descrittore file del sistema tipo UIMA e il file `cas2di.tsv` o seleziona tutti i file nella cartella.
    1. Crea un file ZIP che include tutti i file. Assicurati che `cas2di.tsv` e i file descrittori del sistema tipo UIMA siano archiviati nella directory root del file ZIP. Questi file non possono essere archiviati in una cartella secondaria nel file ZIP o {{site.data.keyword.knowledgestudioshort}} potrà leggerli e non sarà importato nulla.

        In Windows, puoi fare clic con il tasto destro e selezionare **Send to** > **Compressed (zipped) folder** .

1. Carica il file ZIP in uno spazio di lavoro {{site.data.keyword.knowledgestudioshort}}.

    1. Accedi come amministratore o gestore del progetto {{site.data.keyword.knowledgestudioshort}}, apri lo spazio di lavoro a cui vuoi aggiungere i documenti e apri la pagina **Assets**> **Documents**.
    1. Fai clic su **Upload Document Sets**.
    1. Trascina il file ZIP che hai creato o fai clic per individuare e selezionare il file.
    1. Seleziona la casella di spunta per indicare che il file ZIP contiene i file UIMA CAS XMI.
    1. Fai clic su **Upload**.
