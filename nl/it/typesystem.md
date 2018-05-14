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

Questa documentazione è per {{site.data.keyword.knowledgestudiofull}} su {{site.data.keyword.cloud}}. Per visualizzare la documentazione della versione precedente di {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace, [fai clic su questo link ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/docs/services/knowledge-studio/typesystem.html){: new_window}.
{: tip}

# Stabilire un sistema tipo 
{: #typesystem}

Il sistema tipo controlla come può essere annotato il contenuto.
{: shortdesc}

## Sistemi tipo
{: #wks_typesystem}

Un sistema tipo definisce le cose interessanti nel tuo contenuto del dominio che vuoi vengano etichettate con un'annotazione. Il sistema tipo controlla come può essere annotato il contenuto definendo i tipi di entità che possono essere etichettati e come le relazioni tra diverse entità possono essere etichettate. Il gestore del processo del modello normalmente collabora con gli
esperti in materia del tuo dominio per definire il sistema tipo.

In {{site.data.keyword.knowledgestudioshort}}, puoi creare un sistema tipo da zero oppure caricarne uno esistente. Per avviare velocemente uno spazio di lavoro, potresti voler caricare un sistema tipo che è stato creato per un dominio simile. Puoi quindi modificare il sistema tipo per aggiungere o rimuovere i tipi di entità o ridefinire i tipi di relazione.

Ti viene fornito un sistema tipo di esempio basato sul sistema tipo KLUE da utilizzare con le esercitazioni di {{site.data.keyword.knowledgestudioshort}}. KLUE sta per Knowledge from Language Understanding and Extraction ed è conseguente alla ricerca di {{site.data.keyword.IBM_notm}} basata sulle analisi delle raccolte di nuovi articoli. Puoi scaricare un sistema tipo KLUE di esempio da <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/en-klue2-types.json" download>qui<img src="../../icons/launch-glyph.svg" alt="Icona link esterno" title="Icona link esterno" class="style-scope doc-content"></a>.

Molte industrie, come in settori come metallurgia, geologia, market intelligence, scienze naturali, cartelle cliniche elettroniche e oncologia pubblicano dizionari o ontologie di terminologia specifica del settore. Considera questi tipi di riferimenti per farti un'idea dei tipi di entità che potresti voler definire in tuo sistema tipo.

### Citazioni 
{: #wks_typesystem__wks_typesystemS2}

Una citazione è una qualsiasi parte di testo che consideri rilevante nei tuoi dati del dominio. Ad esempio, in un sistema tipo di veicoli automobilistici, le ricorrenze dei termini *airbag*, *Ford Explorer* e *child restraint system* potrebbero essere citazioni importanti.

### Tipi di entità 
{: #wks_typesystem__wks_typesystemS3}

Un tipo di entità è come categorizzi una cosa reale. Una citazione dell'entità è un esempio di una cosa di quel tipo. Ad esempio, la citazione "President Obama" può essere annotata come un tipo di entità PERSON. La citazione "{{site.data.keyword.IBM_notm}}" può essere annotata come un tipo di entità ORGANIZATION. Le entità sono spesso nomi ma possono essere anche verbi, purché il verbo sia importante da acquisire ai fini dell'applicazione che utilizzerà il sistema tipo. Ad esempio, EVENT_CRASH potrebbe essere un tipo di entità valido per un sistema tipo sui veicoli automobilistici, per cui la parola *hit* nella frase, "The car hit the barrier." può essere annotata.

L'obiettivo del tuo spazio di lavoro di annotazione è di annotare tutte le citazioni in un documento con il tipo di cosa che rappresenta. Dopo che una citazione viene classificata dal tipo di entità, alla parte del discorso etichettata viene fatto riferimento come a un'entità.

Un sistema tipo che crei con {{site.data.keyword.knowledgestudioshort}} può includere i seguenti attributi del tipo di entità. Gli attributi aiutano a qualificare le citazioni nel testo ma non sono contrassegnati come entità da un modello di machine learning. Ad esempio, se il tipo di entità ORGANIZATION ha un sottotipo di entità denominato COMMERCIAL, COMMERCIAL non viene contrassegnato come un tipo di entità a sua volta.

- **Ruolo**

    Qualifica la citazione dal contesto in cui si verifica. Ad esempio, la citazione "France" nell'affermazione, "the students went to France", viene contrassegnata con il tipo di entità GPE perché France è un'entità geo-politica. Ma poiché France in questo contesto è anche una destinazione degli studenti in viaggio, il tipo di entità viene qualificato aggiungendo un attributo, in questo caso il ruolo LOCATION. Per un altro esempio, la citazione "Lawyers" potrebbe essere contrassegnata con il tipo di entità PEOPLE ma anche con il ruolo OCCUPATION.

- **Sottotipi di entità**

    Classifica ulteriormente il tipo di entità. Ad esempio, il tipo di entità ORGANIZATION potrebbe includere i sottotipi COMMERCIAL, GOVERNMENT, MILITARY e EDUCATION.

- **Tipo di citazione**

    Qualifica la citazione da alcune parti del discorso:
    - NAM: la citazione è un nome proprio, come il nome di una persona o di un'organizzazione.
    - NOM: la citazione è nominale (un nome comune), come un'azienda o un presidente.
    - PRO: la citazione è un pronome, come lui, noi o esso.
    - NONE: nessuno degli altri tre tipi di citazione sono applicabili.

- **Classe della citazione**

    Qualifica la citazione indicando se è specifica, generica o negativa:
    - SPC: la citazione è specifica, spesso include la parola "the" in inglese, come "the book" o "the hurricane occurred in September". In questi esempi, le citazioni "book" e "hurricane" dovrebbero essere annotate con l'attributo SPC.
    - GEN: la citazione è generica, come "a book" o "hurricanes usually occur in the fall". In questi esempi, le citazioni "book" e "hurricanes" dovrebbero essere annotate con l'attributo GEN.
    - NEG: la citazione è negativa, come i riferimenti a "no book". Quando prepari un modello, l'algoritmo può imparare sia dagli esempi positivi che negativi, quindi è importante contrassegnare le citazioni di entrambi i tipi.

### Tipi di relazione 
{: #wks_typesystem__wks_typesystemS4}

Un tipo di relazione definisce un binario, la relazione ordinata tra due entità. Perché sia presente una citazione di relazione, il testo deve definire esplicitamente la relazione e associare le citazioni delle due entità tra loro e deve farlo all'interno di una frase. Ad esempio, la frase *Mary works for {{site.data.keyword.IBM_notm}}* è una prova testuale del tipo di relazione **employedBy**.

Per alcuni tipi di relazione, l'ordine delle citazioni di entità è importante. Ad esempio, il tipo di relazione employedBy consente il tipo di entità PERSON o PEOPLE come prima citazione nella relazione e ORGANIZATION o GPE come secondo, ma non viceversa. Mary employedBy {{site.data.keyword.IBM_notm}} è una relazione valida; {{site.data.keyword.IBM_notm}} employedBy Mary non lo è. Per alcuni tipi di relazione, come spouseOf, colleague o sibling, l'ordine non è importante. Quando definisci un tipo di relazione in cui l'ordine non è importante, una procedura consigliata è di aggiungere le informazioni alle linee guida di annotazione per regolarizzare come viene utilizzato il tipo di relazione. Una convenzione per rilevare queste relazioni simmetriche è di dire che la citazione di entità che si verifica per prima nel testo dovrebbe essere la prima nella relazione.

**Concetti correlati**:

[Caricamento delle risorse da un altro spazio di lavoro](/docs/services/watson-knowledge-studio/exportimport.html)

## Aggiunta di un sistema tipo a uno spazio di lavoro
{: #wks_projtypesys}

Devi creare o caricare un sistema tipo prima di iniziare qualsiasi attività di annotazione.

### Informazioni su quest'attività

Le seguenti regole di denominazione vengono applicate alle voci del sistema tipo:

- I nomi non possono contenere spazi.
- Utilizza solo i seguenti caratteri ASCII alfanumerici e il carattere di sottolineatura nei valori che aggiungi al sistema tipo: da A a Z, da a a z, da 0 a 9. 
- Il primo carattere in un nome del tipo di entità o di relazione deve essere alfabetico. 
- I nomi dei tipi di entità non possono essere più lunghi di 64 caratteri. 
- I nomi dei tipi di relazione non possono essere più lunghi di 128 caratteri. 

Per convenzione, i nomi dei tipi di entità vengono specificati con caratteri maiuscoli (ORGANIZATION) e i nomi dei tipi di relazione sono specificati con il CamelCase (employedBy). Ma questa convenzione è facoltativa.

### Procedura

1. Accedi come amministratore o gestore del progetto {{site.data.keyword.knowledgestudioshort}} e apri la pagina **Assets & Tools** > **Entity Types**.
1. Scegli uno dei seguenti metodi per la creazione del sistema tipo:

    - Per caricare un sistema tipo esistente:

        1. Fai clic su **Upload** per caricare un sistema tipo esistente.

            Se hai precedentemente scaricato un sistema tipo dallo spazio di lavoro {{site.data.keyword.knowledgestudioshort}}, viene scaricato nel formato `JSON`. Puoi caricare questo sistema tipo per iniziare velocemente la creazione di un nuovo spazio di lavoro. Per i dettagli, vedi [Caricamento delle risorse da un altro spazio di lavoro](/docs/services/watson-knowledge-studio/exportimport.html).

            > **Nota:** indipendentemente dall'origine del sistema tipo, le voci in esso devono soddisfare le regole di denominazione elencate precedentemente.

        1. Aggiungi, modifica ed elimina i tipi di entità e di relazione nello stesso modo di quando crei un sistema tipo da zero.

    - Per creare un sistema tipo da zero: 

        1. Fai clic su **Add Entity Type**.
        1. Specifica un nome del tipo di entità descrittivo, tenendo presente che è un'etichetta per l'annotazione di parti del discorso importanti (citazioni) nel tuo contenuto del dominio. Mantieni il nome breve e rappresentativo, in modo che gli annotatori umani possano ricordarlo facilmente.

            Puoi anche facoltativamente definire i ruoli e i sottotipi del tipo di entità:
            - Un ruolo aiuta a qualificare il tipo di entità nel contesto in cui si verifica la citazione. Ad esempio, la citazione Software Engineer potrebbe essere etichettata con il tipo di entità PEOPLE e, in questo contesto, dal ruolo OCCUPATION. Consulta [Quando definire i ruoli](/docs/services/watson-knowledge-studio/typesystem.html#wks_typesystem_roles) per ulteriori informazioni.
            - Un sottotipo aiuta a classificare ulteriormente il tipo di entità. Ad esempio, il tipo di entità GOVERNMENT potrebbe avere i sottotipi MILITARY e CIVILIAN.

            > **Nota:** definendo un ruolo o un sottotipo di un'entità, stai fornendo ulteriori opzioni alla persona che assocerà le informazioni del tipo alle citazioni al momento dell'annotazione. L'annotatore umano può applicare un'annotazione che specifica solo il tipo di entità o il tipo di entità più il ruolo o il sottotipo che stai definendo ora.

            Prova a definire abbastanza tipi di entità per acquisire i concetti chiave che vuoi annotare, ma non così tanti da rendere difficile agli annotatori umani di applicare le etichette in modo accurato.

        1. Fai clic su **Mention Classes** e **Mention Types** per visualizzare le classi della citazione e i tipi di citazione (non puoi modificare questi valori).

            Lo scopo di un attributo è di aiutare ad etichettare ogni citazione con il tipo della cosa che rappresenta. Un tipo di citazione indica se è un nome, nominale o un pronome e una classe della citazione indica se è specifica, generica o negativa.

        1. Apri la pagina **Assets & Tools** > **Relation Types** e specifica come due citazioni possono essere collegate tra loro.

            L'ordine tra la prima e la seconda entità in un tipo di relazione è generalmente importante. Ad esempio, un'entità PERSON può essere un impiegato di un'entità ORGANIZATION o di un'entità geo-politica (GPE), come ad esempio Mary employedBy {{site.data.keyword.IBM_notm}}, ma le entità delle organizzazione e geo-politiche non possono essere degli impiegati di una persona. Quando un annotatore umano fa clic su un'entità nell'editor ground truth, l'elenco dei tipi di relazione disponibili viene controllato da ciò che viene definito nel sistema tipo.

            Non definire gli attributi della relazione. Non vengono utilizzati dal modello di machine learning. Il modello utilizza solo l'ordine o il tipo di relazione e ignora gli attributi della relazione.

        1. Utilizza le icone **Edit** e **Delete** per modificare i tipi di entità e i loro tipi di relazione associati o per eliminare un tipo di entità o di relazione dal sistema tipo.

            Se elimini un'entità che viene utilizzata in una definizione del tipo di relazione, viene eliminata la definizione.

**Attività correlate**:

[Modifica di un sistema tipo senza perdere le annotazioni umane](/docs/services/watson-knowledge-studio/improve-ml.html#wks_projtypesysmod)

## Linee guida sulla creazione del sistema tipo
{: #wks_typesys_guidelines}

Lo scopo di qualsiasi sistema tipo in {{site.data.keyword.knowledgestudioshort}} è di definire come le parti del discorso possono essere annotate. Se scegli di creare un sistema tipo da zero, segui queste linee guida.

Concentrati sulla creazione di un inventario di tipi di entità e di relazione che copre le informazioni di cui ha bisogno l'applicazione in cui sarà utilizzato il sistema tipo. Non coprire cose non necessarie. Non suddividere i tipi o fare distinzioni che non sono necessarie all'applicazione. Ad esempio, se il documento di origine contiene la frase *Murder on the Orient Express made headlines*, come definisci i tipi di entità per acquisire le informazioni chiave nella frase è diverso a seconda del tipo di applicazione che utilizzerà il modello che crei con il sistema tipo.

- Per un'applicazione letteraria, potresti creare i tipi che acquisiscono queste informazioni:

    ```
               [NOVEL]           [CRITICAL_RECEPTION]
    ```
    {: screen}

    ```
    [Murder on the Orient Express] [made headlines]
    ```
    {: screen}

- Per un'applicazione di sicurezza pubblica, potresti creare questi tipi: 

    ```
    [EVENT_CRIME]      [LOCATION]
    ```
    {: screen}

    ```
      [Murder] on the [Orient Express] made headlines
    ```
    {: screen}

La struttura è spesso guidata dalle caratteristiche dei documenti da cui saranno estratte le informazioni ma dovrebbe sempre essere mitigata da quali informazioni l'applicazione sta al momento utilizzando da questi documenti. Ad esempio, potresti stare creando un'applicazione che ottiene le informazioni approfondite dalle cartelle cliniche. Per creare il sistema tipo, inizia a guardare le cartelle cliniche per vedere quali tipi di informazioni devono essere acquisiti. Le cartelle cliniche potrebbero tutte contenere un campo che descrive cosa il paziente ha mangiato per pranzo. Tuttavia, se l'applicazione non utilizzerà tali informazioni, non aggiungerle al sistema tipo. E nel prendere la decisione di fare questa omissione, riconosci che questo significa che queste sezioni dei tuoi documenti della cartella clinica saranno lasciati non annotati. Questo è corretto e anche previsto.

Le citazioni annotano una parte del discorso; non sostituiscono il testo. Un sistema tipo non è un'ontologia di un dominio. Aspettati di avere tipi di entità generali come MEDICATION_NAME invece di un tipo di entità per ogni tipo di medicina. Il testo del documento continuerà a contenere il nome della medicina specifico. Sarà semplicemente migliorato con un'annotazione che ne identifica il tipo, che rende queste informazioni più facili da trovare ed estrarre in modo programmatico.

Per iniziare, definisci da 10 a 40 tipi di entità e di relazione. Rimani nell'estremità inferiore dell'intervallo se gli annotatori umani che lavoreranno nello spazio di lavoro sono altamente specializzati in quel campo. Non definirne più di 50.

Pensa di passare una buona quantità di tempo nella definizione del sistema tipo prima che il team inizi una qualsiasi attività di annotazione umana. Quando il team inizia ad annotare i documenti, inizia con una piccola serie, forse non più di 50. Inizialmente annota solo le citazioni, esamina i risultati e rifinisci le tue linee guida di annotazione e il sistema tipo se necessario. Quando sei soddisfatto dei risultati dell'annotazione della citazione, passa ad annotare le relazioni e le coreferenze.

Mentre è in corso il lavoro fondamentale di definire una serie di tipi di entità e di linee guida di annotazione della citazione, evita di mettere molto impegno nell'annotazione delle citazioni di relazione. Le modifiche alla citazione annulleranno il lavoro di annotazione della relazione. Prenditi del tempo per definire una serie di tipi di relazione e le loro coppie di tipo di entità consentiti in modo che tale tipo di relazione venga preso in considerazione prima che venga finalizzato l'inventario del tipo di entità.

Aspettati che il sistema tipo si evolva con l'esperienza delle persone che stanno tentando di annotarlo. Se revisioni il sistema tipo dopo aver creato le attività di annotazione umana, devi decidere se applicare le modifiche ad ogni attività. Se applichi le modifiche, gli annotatori umani dovranno rivedere i documenti che hanno annotato precedentemente.

Quando verifichi il modello, puoi controllare le statistiche che mostrano quanto frequentemente i tipi di entità e di relazione si verificano nei tuoi documenti di esempio. Assicurati di controllare queste statistiche. Per assicurarti che la tua applicazione riceva abbastanza contesto per annotare accuratamente grandi raccolte di documenti, i tuoi dati di test dovrebbero includere un grande campione dei tipi di entità e di relazione più importanti.

> **Importante:** dopo aver preparato il primo modello, avrai probabilmente bisogno di effettuare modifiche in base alle statistiche delle prestazioni. Tuttavia, per creare un modello statistico affidabile, vuoi che il sistema tipo sia il più vicino possibile a quello finale prima di iniziare attività di annotazione su larga scala.

## Quando definire i ruoli
{: #wks_typesystem_roles}

Utilizzando i ruoli puoi definire i tipi di entità in modo più preciso.

Ogni entità che aggiungi ha un ruolo. A meno che lo modifichi, il nome del ruolo è lo stesso del nome dell'entità. Puoi scegliere di definire un ruolo differente di un'entità per acquisire un utilizzo con più sfumature della citazione. La parola o la frase a cui viene applicato il ruolo è letteralmente un esempio di un tipo di entità ma nella frase copre il ruolo di un altro tipo di entità. Ad esempio, nella frase, *the White House vetoed the bill*, possiamo acquisire in modo più preciso il significato di *White House* se annotiamo sia il tipo di entità FACILITY che un ruolo di ORGANIZATION o PERSON. White House è una costruzione (FACILITY), ma rappresenta il governo (ORGANIZATION) o il presidente degli Stati Uniti (PERSON) in questa costruzione. Il tipo di entità + l'etichetta del ruolo crea una classificazione più precisa della citazione nel testo.

I ruoli possono anche fornirti un modo per acquisire le informazioni di relazione senza affidarsi all'utilizzo delle citazioni di sovrapposizione. Ad esempio, potresti voler annotare il testo *31-year-old male* che da l'idea di essere un riferimento a un persona con l'attributo età di 31 anni e con l'attributo di genere maschile. Esaminando il testo, determiniamo che *31-year-old* è un'età, *male* è un genere e insieme significano una persona. Ti stai affidando a 3 tipi di entità, sostanzialmente: AGE, GENDER e PERSON. Un approccio a questa rappresentazione potrebbe essere di annotare *31-year-old* come AGE, *male* come GENDER e poiché la citazione distinta di PERSON è mancante ma *male* rappresenta una persona, la parola *male* può avere un ruolo di PERSON. Puoi quindi acquisire le relazioni tra il ruolo PERSON e tutti gli attributi di una persona che vuoi acquisire. Ad esempio, puoi definire una relazione hasAttribute tra il ruolo PERSON e la citazione AGE. Poiché hai applicato sia un tipo di entità GENDER che un'etichetta del ruolo PERSON alla stessa parola *male*, non puoi definire una relazione hasAttribute tra i due. Tuttavia, il fatto che le due etichette siano applicate alla stessa citazione le associa tra loro. Questa associazione viene presa in considerazione dal modello di machine learning senza dover definire un tipo di relazione hasAttribute che richiama esplicitamente la relazione.

Un esempio simile è quando la frase *2008 Ford F-150* viene utilizzata come abbreviazione di *2008 Ford F-150 truck*. Qui, *2008* viene annotato come un tipo di entità MODEL_YEAR, *Ford* come MANUFACTURER e a *F-150* viene assegnato un tipo di entità MODEL. Ma con la parola "truck" mancante, *F-150* rappresenta anche un veicolo. Dire *the F-150* è come dire *the truck*. Puoi acquisire tale utilizzo aggiungendo un ruolo VEHICLE alla citazione in aggiunta al suo tipo di entità MODEL. Puoi quindi definire le relazioni hasAttribute tra il ruolo VEHICLE e le citazioni dell'entità MANUFACTURER e MODEL_YEAR.

### Come sono diversi i ruoli rispetto ai sottotipi?

I sottotipi dell'entità sono per la stratificazione di un inventario di tipi di entità in una gerarchia. Ad esempio, se vuoi distinguere 40 cose, ma vengono raggruppate in modo logico in serie di 10 da 4 (VITALSIGN_BLOODpreSSURE, VITALSIGN_HEARTRATE, MEDICATION_DOSAGE, MEDICATION_FREQUENCY), potresti strutturarle in tipi e sottotipi, che forniscono menu più compatti ma aggiungono un livello di profondità e rendimento al processo di etichettatura. Per gli scopi di estrazione delle informazioni, una combinazione di tipi e sottotipi è interscambiabile come molti e molti tipi senza sottotipi. Al contrario, la parola o la frase a cui applichi un ruolo è un esempio di un tipo di entità ma copre il ruolo di un altro tipo di entità e uno non è il sottotipo dell'altro.

### Come vengono trattati i ruoli?

Il modello di machine learning {{site.data.keyword.knowledgestudioshort}} definisce le etichette di classificazione di ogni citazione di un'entità che trova nei documenti di origine concatenando i valori tipo di entità + ruolo. Quando fornisci i valori del ruolo, crei etichette più precise. Ogni gruppo di istanze di un tipo di etichetta che viene trovato nei dati di preparazione forma una serie di citazioni più uniforme. La sfida è che scegliendo di essere più preciso, devi anche acconsentire a fornire più dati di preparazione per assicurarti che il modello funzioni bene. Ma, più dati di preparazione fornisci, meglio diventa il modello. Quindi, se non vuoi effettuare ulteriori annotazioni, l'utilizzo dei ruoli può darti risultati migliori.

Ad esempio, assumiamo che le seguenti frasi si verificano in un documento di origine e che vogliamo acquisire "Acme" (dove Acme è un produttore di autocarri ben conosciuto), "sedan" e "truck" come entità simili perché fanno tutte riferimento a un veicolo fisico:

- a) The Acme crashed into the concrete barrier.
- b) The sedan crashed into the concrete barrier.
- c) The Acme A-160 truck crashed into the concrete barrier.

Puoi gestire la progettazione del sistema tipo in due modi:

1. Definisci due tipi di entità: **MANUFACTURER** e **VEHICLE**. Per l'entità **MANUFACTURER**, definisci un ruolo **VEHICLE** che può essere utilizzato in aggiunta al ruolo **MANUFACTURER** predefinito.

    Utilizzando questo sistema, le frasi vengono annotate nel seguente modo:
    - a) "Acme" viene annotato come un'entità **MANUFACTURER** ma con un ruolo di **VEHICLE**, poiché fa riferimento a un veicolo reale. Quindi, la sua etichetta interna è **MANUFACTURER-VEHICLE**.
    - b) "sedan" viene annotato come tipo di entità **VEHICLE**. Gli viene automaticamente assegnato il ruolo **VEHICLE**, poiché nessun altro ruolo è definito.
    - c) "Acme" viene annotato come tipo di entità **MANUFACTURER** e "truck" come **VEHICLE**. Nessun ruolo è stato assegnato, per cui vengono utilizzati i ruoli predefiniti.

1. Definisci solo due tipi di entità senza ruoli: **MANUFACTURER** e **VEHICLE**.

    Utilizzando questo sistema, le frasi vengono annotate nel seguente modo:
    - a) "Acme" viene annotato come tipo di entità **VEHICLE**. 
    - b) "sedan" viene annotato come tipo di entità **VEHICLE**. 
    - c) "Acme" viene annotato come tipo di entità **MANUFACTURER** e "truck" come **VEHICLE**. 

Come funzionano due sistemi tipo differenti? Assumiamo che è stata annotata una serie di documenti dagli annotatori umani. Dopo la fase di annotazione, i seguenti eventi di preparazione, che sono entità etichettate manualmente, sono identificati nel corpus di preparazione:

- **Sistema tipo 1**

    ```
    MANUFACTURER-MANUFACTURER 800 events
    MANUFACTURER-VEHICLE 200 events
    VEHICLE-VEHICLE 400 events
    ```
    {: screen}

- **Sistema tipo 2**

    ```
    MANUFACTURER 800 events
    VEHICLE 200 + 400 = 600 events
    ```
    {: screen}

Quando il modello elabora i nuovi documenti, è probabile che "Acme" sarà etichettato come MANUFACTURER la maggior parte delle volte perché l'ortografia di una parola è una funzione importante e la parola "Acme" sarà probabilmente definita nel dizionario MANUFACTURER. Servirà molto contesto per etichettarla diversamente. Se utilizziamo il sistema tipo 1, ci sono solo 200 eventi di preparazione MANUFACTURER-VEHICLE, che è uno svantaggio quando confrontati ai 600 eventi di VEHICLE nel sistema tipo 2. Tuttavia, i cluster dell'evento di preparazione nel sistema tipo 1 sono piuttosto uniformi, che porta a prestazioni migliori. Per il sistema tipo 2, la serie di 600 eventi di preparazione di VEHICLE è al momento composta da due cluster piuttosto disgiunti: uno che contiene i nomi del produttore che fanno riferimento a veicoli reali come "Acme" e "Ford" e l'altra che contiene i tipi di veicolo, come "sedan", "SUV" e "truck". In modo intuitivo, ognuno di questi due cluster per se stesso è uniforme, ma unendoli insieme, si diluisce il cluster di preparazione che presenta un problema difficile da risolvere. Se continui ad annotare e ad aggiungere ulteriori eventi di preparazione, le prestazioni nel sistema tipo 1 continuano a migliorare, mentre, il problema di risoluzione dei due cluster disgiunti che hai con il sistema tipo 2 non migliora con ulteriore preparazione.
