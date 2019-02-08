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

Questa documentazione è per {{site.data.keyword.knowledgestudiofull}} su {{site.data.keyword.cloud}}. Per visualizzare la documentazione della versione precedente di {{site.data.keyword.knowledgestudioshort}} nel {{site.data.keyword.IBM_notm}} Marketplace, [fai clic su questo link ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/docs/services/knowledge-studio/user-guide.html){: new_window}.
{: tip}

# Annotazione dei documenti
{: #user-guide}

Le informazioni in questa sezione aiutano gli esperti in materia a cui è stato chiesto di annotare documenti di settore ad utilizzare l'editor ground truth per completare l'attività.
{: shortdesc}

## Accesso allo spazio di lavoro
{: #wks_access_for_annotator}

Non puoi visualizzare alcun spazio di lavoro finché qualcun altro non crea uno spazio di lavoro e te ne fornisce l'accesso.

Quando un amministratore ti aggiunge a un'istanza di {{site.data.keyword.knowledgestudioshort}}, vieni aggiunto nel ruolo di annotatore umano. Con questo ruolo, non puoi creare uno spazio di lavoro. Per ottenere l'accesso a uno spazio di lavoro, l'amministratore deve creare uno spazio di lavoro. Successivamente l'amministratore o un gestore del progetto che l'amministratore associa allo spazio di lavoro, deve eseguire i seguenti passi:

1. Creare una serie di annotazioni e associarti ad essa.
1. Creare un'attività che ti assegna per annotare i documenti nella serie.

Finché non ti viene assegnata un'attività di annotazione non puoi visualizzare lo spazio di lavoro.

Se sei stato invitato a partecipare allo spazio di lavoro {{site.data.keyword.knowledgestudioshort}} ma non ne vedi alcuno nella pagina Workspaces, contatta la persona che ti ha invitato e chiedile di eseguire le operazioni necessarie.

## Procedure consigliate per l'annotazione
{: #wks_anno_bp}

Queste procedure consigliate di annotazione fornisco alcune linee guida ed esempi per iniziare ad annotare i documenti.

- Annota tutti i documenti completamente.

    Il machine learning impara dagli esempi negativi -- quello che non è annotato -- non solo da cosa è annotato. Per cui, devi essere giudizioso su cosa annoti ma fai un lavoro completo. Se annoti attentamente solo i primi 5 di 10 documenti in una serie, le annotazioni che non prendi negli ultimi 5 documenti istruiranno il modello ad ignorare tutte le citazioni di relazione o entità che mancano in questi documenti. Potresti terminare invertendo tutti i vantaggi acquisiti effettuando un lavoro approfondito con i primi 5 documenti.

- L'annotazione coerente è importante almeno quanto l'annotazione corretta.

    Alcune decisioni che riguardano le linee guida di annotazione sono arbitrarie, come se un'automobile e le lettere appuntate dovrebbero far parte dei nomi del modello, ad esempio *Camry* o *Camry LX*. Quale delle politiche viene scelta è molto meno importante rispetto a che il team del progetto sia d'accordo su una o l'altra e la annoti in accordo in modo coerente.

- Etichetta le citazioni dell'entità sui limiti del token-parola soltanto, perché la ricerca rilevamento-citazione funziona al livello di granularità del token-parola.
- Etichetta le citazioni dell'entità che sono limitate a una o due parole adiacenti quando possibile.

    Fare in questo modo non è sempre possibile o facile. Considera questi esempi:
    - Il documento di origine contiene una frase da cui, per gli scopi dell'applicazione che utilizzerà il sistema tipo, vogliamo annotare il problema e le sue cause.

        ```
        The electronic module was burnt because the wrong voltage was applied.
        ```
        {: screen}

        Qualcuno potrebbe essere tentato di annotare il problema e la causa così:

        ```
                    [PROBLEM][CAUSE]
        ```
        {: screen}

        ```
        [The electronic module was burnt][because the wrong voltage was applied].
        ```
        {: screen}

        Tuttavia, non è una buona pratica annotare frasi così lunghe come tipi di entità. Invece, trova le entità importanti e identifica come sono associate ad un'altra definendo una citazione di relazione.

        ```
               [LOCATION][SYMPTOM]                [CAUSE]
        ```
        {: screen}

        ```
        The [electronic module] was [burnt] because the [wrong voltage] was applied.
        ```
        {: screen}

        ```
                      ^---isStatusOf--| |------causedBy-------^
        ```
        {: screen}

    - Il documento di origine contiene un verbo separato che vuoi annotare. Come annoti il testo non contiguo come un solo tipo di entità? Puoi annotare ogni citazione dell'entità e identificarle correlate tra loro utilizzando una citazione della relazione.

        ```
                  [EVENT_ANSWER][EVENT_ANSWER]
        ```
        {: screen}

        ```
        All of the phones were ringing, but he knew he should [pick] the red phone [up] first.
        ```
        {: screen}

        ```
                            ^----splitType-----^
        ```
        {: screen}

- Evita la sovrapposizione delle citazioni, che sono due diversi etichette del tipo di entità applicate a una sola frase in un documento. Ad esempio, con la frase, *She donated her father's journals to the JFK Library.*, sovrapporrai le citazioni se annoti `JFK`=`PERSON` e `JFK Library`=`LOCATION` per la sola frase *JFK Library*. L'utilizzo del termine è più indicato alla libreria che alla persona in questa frase, per cui solo l'ultima annotazione dovrebbe essere applicata.

    Decodifica quelle strutture che richiedono più richiami paralleli di un modello di machine learning poiché il rilevamento della citazione ricerca solo un'etichetta o nessuna etichetta su ogni token della parola.

- Determina come il team gestirà gli elenchi e i plurali nel testo in esecuzione. Ad esempio, il sistema tipo KLUE ha i tipi di entità `PERSON` e `PEOPLE` che distinguono il singolare dal plurale. Puoi scegliere di annotare l'elenco *Barack, Michelle, Malia, and Sasha Obama*, in uno dei seguenti modi:

    - Annota ogni elemento nell'elenco come una citazione dell'entità singolare (*Barack*, *Michelle*, *Malia* e *Sasha Obama* sono ognuna una citazione `PERSON`)
    - Annota l'intera frase come una citazione dell'entità plurale (*Barack, Michelle, Malia, and Sasha Obama* è una citazione `PEOPLE` singola).

    Nessun approccio è necessariamente migliore dell'altro. Assicurati semplicemente che il tuo team scelga uno dei due e lo applichi coerentemente a tutti gli elenchi che si verificano nei documenti. 

- Viene utilizzata una coreferenza quando le citazioni fanno riferimento alla stessa entità reale. Le relazioni sono utilizzate tra entità distinte. Per cui, non dovrebbero essere collegate due citazioni tramite coreferenza e relazione.

## Annotazione con l'editor ground truth
{: #wks_hagte}

Quando un annotatore umano annota un documento, il documento viene aperto nell'*editor ground truth*. L'editor ground truth è uno strumento grafico che gli annotatori umani utilizzano per applicare le etichette al testo.

L'obiettivo dell'annotazione umana è di etichettare le citazioni, le relazioni e le citazioni di coreferenza in modo che il modello di machine learning possa essere preparato per individuare questi modelli nel testo non visto. Come minimo, utilizza lo strumento per annotare le citazioni dell'entità. Se l'applicazione che utilizzerà il modello risultante non deve trovare ed estrarre le citazioni di relazione e coreferenza, non hai bisogno di annotarle.

La concordanza è uno strumento facoltativo che può essere utilizzato dagli annotatori umani per velocizzare l'annotazione di citazioni ripetute.

Scegli una modalità di utilizzo quando annoti i documenti manualmente:

- Modalità **Citazione** 

    In questa modalità, l'annotatore umano associa i tipi di entità, come definito nel sistema tipo, con le parole o le frasi significative nel testo. Ad esempio, tutte le citazioni dei nomi delle persone potrebbero essere associate a un tipo di entità denominato PERSON. L'annotazione delle citazioni è obbligatoria e deve essere eseguita prima di annotare i tipi di relazione e le citazioni come coreferenze.

    L'annotatore umano può facoltativamente utilizzare lo strumento di concordanza per assicurarsi che lo stesso testo sia annotato con lo stesso tipo di entità in un documento e tra le serie di annotazioni.

- Modalità **Relazione**

    In questa modalità, l'annotatore umano collega le citazioni associando un tipo di relazione, come definito nel sistema tipo. Ad esempio, la citazione `John Smith` potrebbe essere collegata alla citazione `{{site.data.keyword.IBM_notm}}` dal tipo di relazione `employedBy`. L'annotazione dei tipi di relazione è facoltativa e può essere eseguita prima o dopo l'annotazione delle citazioni come coreferenze.

- Modalità **Coreferenza**

    In questa modalità, l'annotatore umano identifica le citazioni che significano le stesse cose, aiutando quindi a garantire la coerenza nelle annotazioni quando le parole non sono identiche. Ad esempio, la citazione di `{{site.data.keyword.IBM_notm}}` nella prima frase, la citazione di `International Business Machines` e di `{{site.data.keyword.IBM_notm}}` in una frase successiva fanno riferimento alla stessa cosa e dovrebbero essere tutte etichettate dallo stesso tipo di entità, come ad esempio `ORGANIZATION`. L'annotazione delle citazioni come coreferenze è facoltativa e può essere eseguita prima o dopo l'annotazione dei tipi di entità.

### Suggerimenti per l'utilizzo dell'editor
{: #wks_hagte_tips}

- Salva il tuo lavoro come hai fatto.
- Se commetti un errore, puoi premere Ctrl+Z per annullare l'azione precedente. Per ripetere l'azione dopo averla annullata, premi Ctrl+Y. Puoi annullare le precedenti 10 azioni che hai eseguito mentre modificavi il documento corrente. Le azioni andranno perse appena chiudi il documento. Le azioni devono essere annullate in ordine inverso e devi passare alla modalità in cui eri quando hai seguito l'azione per annullarla. Non puoi annullare e ripetere le azioni dello strumento di concordanza.

## Annotazione delle citazioni dell'entità
{: #wks_haentity}

Per annotare le citazioni dell'entità, un annotatore umano seleziona una stringa di testo in un documento e poi applica un'etichetta che meglio descrive cosa rappresenta. Le etichette che possono essere applicate sono i tipi di entità definiti nel sistema tipo dello spazio di lavoro.

### Informazioni su quest'attività
{: #wks_haentity_about}

Prima di iniziare ad annotare le citazioni dell'entità in un documento, è buona prassi leggere il documento completo. In questo modo tieni a mente l'intero contesto mentre annoti e puoi fornire informazioni dettagliate su come le citazioni dell'entità possono essere collegate tra loro e per quali citazioni sono presenti delle coreferenze da effettuare nei successivi passi attraverso il documento.

Quando apri un documento per annotarlo, potresti voler utilizzare lo strumento di concordanza per annotare prima le citazioni dell'entità ripetute e successivamente le individuali. Puoi quindi annotare le citazioni della relazione e le coreferenze in qualsiasi ordine tu voglia o non farlo affatto. L'annotazione della citazione dell'entità è obbligatoria. Se annotare anche le citazioni della relazione e le coreferenze dipende dallo scopo del tuo modello e dai bisogni del tuo dominio. Tuttavia, finché e a meno che non identifichi le coreferenze, ogni citazione dell'entità viene considerata come rappresentante di un'entità distinta.

#### Suggerimenti
{: #wks_haentity_tips}

- Tieni presente che citazioni più brevi sono migliori per la preparazione perché è più facile per il modello di machine learning riconoscere i modelli più corti e aggiungere i token di annotazione corretti.
- Se scegli di utilizzare un tokenizer basato sul dizionario con lo spazio di lavoro e vuoi gestire la punteggiatura e i termini composti nei tuoi dati di preparazione, puoi aggiungere i termini a un dizionario e creare un annotatore del dizionario per pre-annotare le ricorrenze. Ad esempio, per evitare le interruzioni dei limiti della frase dei termini che includono la punteggiatura, aggiungi termini come Yahoo! e Dr. a un dizionario. Altrimenti, se i tuoi dati di preparazione includono parole unite da trattini o acronimi alfanumerici, come `Hi-C` o `MS-60-70`, aggiungi questi termini al dizionario. Per annotare le ricorrenze indipendentemente dal caso, aggiungi i termini in caratteri minuscoli (come `hi-c`). Per annotare le variazioni, aggiungile come formati di superficie (`MS-60-70` e `MS 60 70`). 

   **Importante**: non utilizzare questo approccio se stai utilizzando il tokenizer predefinito.

### Procedura
{: #wks_haentity_procedure}

Per annotare le citazioni dell'entità in un documento:

1. Accedi come un annotatore umano (o come un amministratore che era stato assegnato ai documenti da annotare). Vengono visualizzati gli spazi di lavoro che contengono le attività che ti sono state assegnate.
1. Apri un spazio di lavoro e poi fai clic su **Machine Learning Model** > **Annotation Tasks**. Vengono visualizzate le attività di annotazioni che ti sono state assegnate.
1. Apri l'attività di annotazione su cui vuoi lavorare. Vengono visualizzate le serie di annotazioni che ti sono state assegnate.
1. Fai clic su **Annotate** per aprire la serie di annotazioni su cui vuoi lavorare. Vengono visualizzati i documenti nella serie di annotazioni.
1. Apri il documento che vuoi annotare. Per impostazione predefinita, il documento viene aperto nella modalità **Citazione**, che è la modalità che utilizzi per annotare le citazioni dell'entità.
1. Inizia ad annotare le citazioni dell'entità.

    1. Fai clic su una parola nel testo che riconosci come una citazione di un tipo di entità particolare dal sistema tipo. Per le citazioni dell'entità formate da più di una parola, fai clic sull'altra parola e trascina i bordi della casella di selezione per selezionare più parole o parole composte.
    1. Seleziona il tipo di entità che vuoi applicare dal pannello sulla destra o immetti il tasto di scelta rapida del tipo di entità.

        Se le linee guida di annotazione sono state precedentemente collegate allo spazio di lavoro e vuoi avere aiuto nella scelta dell'annotazione corretta da applicare, fai clic su **View Guidelines**. A seconda delle autorizzazioni di accesso configurate nel sito in cui sono ospitate le linee guida, potresti doverle aggiornare dopo averle aperte, ad esempio, per aggiungere chiarimenti ed esempi.
        {: tip}

    1. Evita di creare citazioni di sovrapposizione. Ma, se è necessaria un citazione di sovrapposizione valida, fai clic su **Replace** per aggiungerla più facilmente. Una sovrapposizione si verifica quando applichi più di un'etichetta a una citazione dell'entità. Controlla questi suggerimenti:

        - Annota *Sub-Saharan* come citazione singola, non solo *Saharan* o *Sub*.
        - Non creare un'annotazione `PERSON` di sovrapposizione per il riferimento *JFK* in *JFK International Airport*. La citazione completa *JFK International Airport* dovrebbe essere etichettata solo come `FACILITY`.
        - Per il testo *CEOs*, non creare un'annotazione `PERSON` per *CEO* e una `PEOPLE` per *CEOs*. Annota *CEOs* solo come un tipo di entità `PEOPLE`.

        Generalmente, l'esistenza di troppe citazioni di sovrapposizione significa che le linee guida di annotazione sono ambigue e devono essere migliorate per fornire esempi migliori su come gestire le parole composte nei tuoi dati di origine.

    1. Per rimuovere un'annotazione che hai appena aggiunto, premi Ctrl+Z per annullare l'azione. Per rimuovere un citazione dell'entità in un secondo momento, puoi fare clic con il tasto sinistro su una citazione e premere il tasto Delete o fare clic su **View Details** e poi sulla **X** accanto al tipo di entità assegnato alla citazione.

1. A seconda del sistema tipo, potresti essere in grado di configurare gli attributi di una citazione dell'entità, come l'assegnazione di un sottotipo o un ruolo dell'entità o un tipo o una classe della citazione. Se è così, seleziona una citazione e fai clic su **Attribute View**.

1. Fai clic su **Save** in qualsiasi momento per salvare il tuo lavoro.

### Operazioni successive
{: #wks_haentity_next}

Dopo aver finito di annotare tutte le citazioni dell'entità, di relazione e le coreferenze nel documento, quando applicabile, modifica lo stato del documento da **In Progress** a **Completed**, fai clic su **Save** e poi chiudi il documento.

Dopo aver finito di annotare tutti i documenti e di averli contrassegnati con **Completed**, lo stato della serie di annotazioni viene modificato con **Submitted**. Questo è il modo in cui i gestori del progetto sanno che possono iniziare a valutare i documenti per l'accordo tra annotatori, rifiutarli o accettarli e promuoverli a ground truth.

## Annotazione delle citazioni ripetute
{: #wks_haconcordance}

Puoi facoltativamente utilizzare lo strumento di concordanza per etichettare più ricorrenze di una citazione contemporaneamente. Lo strumento ti consente di annotare lo stesso testo con lo stesso tipo di entità in un documento e tra le serie di annotazioni. L'utilizzo dello strumento garantisce la coerenza nell'annotazione tra più documenti. Ad esempio, puoi etichettare ogni ricorrenza *encryption* individualmente nella modalità di citazione o puoi etichettare tutte le ricorrenze di *encryption* utilizzando lo strumento di concordanza. In entrambi i casi, il modello impara dal tipo di entità che applichi alla citazione.

### Informazioni su quest'attività
{: #wks_haconcordance_about}

Sebbene lo strumento di concordanza sia facoltativo, una procedura consigliata è di utilizzarlo per annotare le citazioni in un documento o tra i documenti prima di iniziare ad annotare le citazioni nei documenti individuali. Quando applichi un tipo di entità a una citazione con lo strumento di concordanza, il sistema applica il tipo di entità a tutte le citazioni corrispondenti, sovrascrivendo tutti i tipi di entità assegnati a una citazione corrispondente. Per evitare conflitti, gli attributi (come i ruoli o i sottotipi) vengono rimossi dai tipi di entità esistenti quando viene applicata una nuova voce dallo strumento di concordanza.

### Procedura
{: #wks_haconcordance_procedure}

Per annotare le citazioni ripetute:

1. Accedi come un annotatore umano (o come un amministratore o un gestore del progetto che era stato assegnato ai documenti da annotare). Vengono visualizzati gli spazi di lavoro che contengono le attività che ti sono state assegnate.
1. Apri un spazio di lavoro e poi fai clic su **Machine Learning Model** > **Annotation Tasks**. Vengono visualizzate le attività di annotazioni che ti sono state assegnate.
1. Apri l'attività di annotazione su cui vuoi lavorare. Vengono visualizzate le serie di annotazioni che ti sono state assegnate.
1. Fai clic su **Annotate** per aprire la serie di annotazioni su cui vuoi lavorare. Vengono visualizzati i documenti nella serie di annotazioni.
1. Apri il documento che vuoi annotare. Per impostazione predefinita, il documento viene aperto nella modalità **Citazione**, che è la modalità che utilizzi per annotare le citazioni dell'entità.
1. Se non hai ancora aggiunto alcuna annotazione, aggiungine almeno una. Seleziona una parola o una frase che rappresenta una citazione di un tipo di entità dal tuo sistema tipo e assegna ad essa il tipo appropriato. Fai clic su **Save** per salvare la tua annotazione.
1. Seleziona una sola ricorrenza del testo ripetuto che vuoi annotare e poi fai clic su **Concordance**.
1. Seleziona i documenti a cui vuoi applicare il tipo di entità selezionato. Puoi creare le annotazioni in tutti i documenti a cui sei stato assegnato per l'annotazione, tutti i documenti che hai iniziato ad annotare o tutti i documenti che non hai ancora iniziato ad annotare.
1. Fai clic su **Preview** per visualizzare le annotazioni che saranno aggiunte.

  Se vuoi controllare le annotazioni in un contesto più grande, fai clic sulle icone per visualizzare un'anteprima del contenuto del documento o aprirlo in una nuova finestra.

1. Fai clic su **Apply & Review** per applicare i tipi di entità selezionati alle citazioni nei documenti selezionati. Hai ancora una possibilità per rivedere le citazioni che saranno aggiunte. Se un'annotazione non è accurata in un contesto particolare, puoi rimuovere tale ricorrenza facendo clic sull'icona Edit e poi rimuovere l'assegnazione del tipo di entità della citazione.
1. Quando sei soddisfatto dell'elenco di annotazioni, fai clic su **Go Back to Ground Truth Editor** .

### Risultati
{: #wks_haconcordance_results}

Le citazioni vengono annotate nel documento. Non c'è modo di rimuovere la serie di citazioni che hai aggiunto tramite la concordanza immediata. Devi rimuovere ogni citazione, una alla volta.

## Annotazione delle citazioni come coreferenze
{: #wks_hacoref}

Per annotare le citazioni come coreferenze alla stessa entità, un annotatore umano seleziona ogni ricorrenza di una citazione che fa riferimento alla stessa cosa. La coreferenza aiuta un modello a riconoscere quali entità a cui viene fatto riferimento in modi diversi devono essere associate alla stessa entità, come il nome di un paese e la sua abbreviazione, il nome di un'azienda e il suo acronimo o il nome di una persona e un prenome che fa riferimento a tale persona.

### Prima di cominciare
{: #wks_hacoref_prereqs}

Devi annotare le citazioni nel documento prima di poter identificare le coreferenze.

### Informazioni su quest'attività
{: #wks_hacoref_about}

Quando annoti le citazioni come coreferenze, il sistema crea una catena di coreferenza. La catena fornisce un modo per visualizzare tutte le citazioni nel contesto e verificare che tutte le ricorrenze appartengano alla stessa entità. Ad esempio, "Barack", "Michelle", "he" e "she" sono tutte dello stesso tipo di entità, `PERSON`, ma "Barack" e "he" sono una entità e "Michelle" e "she" sono un'altra. In questo esempio, crei due catene di coreferenza.

Quando crei una catena di coreferenza, devi selezionare le citazioni che sono state contrassegnate dallo stesso tipo di entità. In alcuni casi, tuttavia, potresti voler includere le citazioni di tipi differenti nella stessa catena di coreferenza. Per far ciò, devi creare più catene e poi unirle. Ad esempio, pensa a come le persone utilizzano le abbreviazioni per evitare di ripetere cose nel testo. In un verbale di un incidente automobilistico, il primo riferimento a un veicolo potrebbe essere "2004 Honda Accord Sedan". Successivamente, l'autore potrebbe voler fare riferimento al veicolo come a "Accord" e dopo ancora semplicemente con "vehicle". Se il sistema tipo include le voci del tipo, del modello e del produttore del veicolo, potresti creare più catene di coreferenza per tipo di entità e poi unirle per creare una catena consolidata. La catena congiunta aiuta a preparare il modello di machine learning in modo che riconosca tutte queste citazioni che fanno riferimento alla stessa cosa.

Un altro modo di combinare le citazioni di differenti tipi di entità è di creare una catena con le citazioni di un tipo di entità. Puoi quindi fare clic su una citazione di un altro tipo di entità e poi sulla catena che hai creato per aggiungere la citazione a tale catena.

A seconda delle tue linee guida di annotazione, potresti voler creare le catene di coreferenza per i verbi così come per i nomi se i verbi citano la stessa istanza di un'azione. Ad esempio, se due citazioni del verbo "encrypts" fanno riferimento alla stessa ricorrenza di codifica, potresti collegare tramite coreferenza le citazioni. Ma se un riferimento a "encrypts" è un riferimento generale o se le due ricorrenze fanno riferimento a due azioni differenti di codifica, non dovresti collegarle con la coreferenza. Se due verbi differenti fanno riferimento alla stessa ricorrenza di un'azione, potresti voler collegare tramite coreferenza le citazioni. Ad esempio, nell'affermazione, "He encrypted the document, and after that processing he sent the file ... ", le citazioni "encrypted" e "processing" potrebbero essere collegate tramite coreferenza perché fanno riferimento alla stessa istanza di un'azione.

La cosa più importante è la coerenza. Decidi come vuoi annotare la coreferenza e specifica le regole, con esempi, in modo chiaro nelle tue linee guida di annotazione.

### Procedura
{: #wks_hacoref_procedure}

Per annotare le citazioni come coreferenze:

1. Accedi come un annotatore umano (o come un amministratore o un gestore del progetto che era stato assegnato ai documenti da annotare). Vengono visualizzati gli spazi di lavoro che contengono le attività che ti sono state assegnate.
1. Apri un spazio di lavoro e poi fai clic su **Machine Learning Model** > **Annotation Tasks**. Vengono visualizzate le attività di annotazioni che ti sono state assegnate.
1. Apri l'attività di annotazione su cui vuoi lavorare. Vengono visualizzate le serie di annotazioni che ti sono state assegnate.
1. Fai clic su **Annotate** per aprire la serie di annotazioni su cui vuoi lavorare. Vengono visualizzati i documenti nella serie di annotazioni.
1. Apri il documento che vuoi annotare. Per impostazione predefinita, il documento viene aperto nella modalità **Citazione**, che è la modalità che utilizzi per annotare le citazioni dell'entità.
1. Fai clic su **Coreferences**. 
1. Crea una catena di coreferenza:

    1. Spostati nel documento e fai clic su ogni citazione che significa la stessa cosa ed è etichettata dallo stesso tipo di entità. Ad esempio, fai clic su ogni ricorrenza di `{{site.data.keyword.IBM_notm}}`, `International Business Machines` e `{{site.data.keyword.IBM_notm}} Corp.`, assumendo che tutte queste citazioni abbiano lo stesso tipo di entità `ORGANIZATION`.
    1. Fai doppio clic sull'ultima citazione che vuoi aggiungere alla catena. Viene creata una catena di coreferenza nel pannello laterale. Il nome della catena corrisponde alla prima citazione che hai selezionato.
    1. Per evidenziare tutte le citazioni in una catena per controllarle nel contesto, passa con il mouse sul nome della catena nel pannello laterale.

1. **Single Mention List** visualizza i termini nel documento che sono stati annotati ma non aggiunti a una catena. Se noti una citazione nell'elenco che appartiene a una catena, puoi aggiungerla da qui.

    1. Da **Single Mention List** nel pannello laterale, fai clic sulla citazione.
    1. Dall'elenco a discesa sotto la descrizione della citazione, scegli il numero che rappresenta la catena a cui vuoi aggiungere la citazione.
    1. Fai clic su **Merge** per aggiungere la citazione alla catena e poi su **OK**.

    La citazione viene rimossa da **Single Mention List** e il numero della catena, a cui ora appartiene, viene visualizzato sotto la citazione nel documento.

1. Puoi annullare il tuo lavoro utilizzando i seguenti metodi:

    - Per rimuovere una catena di coreferenza che hai appena aggiunto, premi Ctrl+Z per annullare l'azione.  
    - Per rimuovere una catena di coreferenza in un secondo momento, dal pannello laterale **Coreference Chains**, fai clic su **X** accanto alla catena che vuoi rimuovere. 
    - Per rimuovere una sola citazione dalla catena, fai clic sull'ID di coreferenza per aprire una finestra che visualizza l'elenco delle citazioni nella catena e poi fai clic su **X** accanto alla citazione che vuoi rimuovere.

1. Fai clic su **Save** in qualsiasi momento per salvare il tuo lavoro.

### Operazioni successive
{: #wks_hacoref_next}

Dopo aver finito di annotare tutte le citazioni dell'entità, di relazione e le coreferenze nel documento, quando applicabile, modifica lo stato del documento da **In Progress** a **Completed**, fai clic su **Save** e poi chiudi il documento.

Dopo aver finito di annotare tutti i documenti e di averli contrassegnati con **Completed**, lo stato della serie di annotazioni viene modificato con **Submitted**. Questo è lo stato in cui i gestori del progetto sanno che possono iniziare a valutare i documenti per l'accordo tra annotatori, rifiutarli o accettarli e promuoverli a ground truth.

## Annotazione delle relazioni
{: #wks_harelation}

Per annotare le citazioni di relazione, un annotatore umano trova la prova testuale di una relazione tra due citazioni dell'entità in una frase e poi applica un'etichetta che descrive nel modo più appropriato il tipo di relazione. Le etichette che possono essere applicate sono i tipi di relazione definiti nel sistema tipo dello spazio di lavoro.

### Prima di cominciare

Devi annotare le citazioni dell'entità nel documento prima di poter definire i tipi di relazione tra loro.

### Informazioni su quest'attività

La citazione della relazione può essere definita solo se il testo descrive esplicitamente la relazione tra due citazioni dell'entità. La prova testuale esplicita potrebbe includere possessivi, strutture soggetto-verbo-oggetto o appositivi. Ad esempio, nella seguente frase, non è valido aggiungere la citazione della relazione `ownedBy` tra `dog` e `owner`.

<pre><code>NON VALIDO: The <u>dog</u> got a treat from its <u>owner</u>.</code></pre>

La citazione della relazione valida è tra `its` e `owner`, perché è questa parte della frase in cui il testo definisce in modo esplicito la relazione tra il cane e il suo proprietario. `Owner` potrebbe essere un proprietario di una casa o di un altro cane, ma questo testo rende chiaro che lo stesso cane che viene menzionato all'inizio della frase è di proprietà di questa persona.

<pre><code>VALIDO: The dog got a treat from <u>its</u> <u>owner</u>.</code></pre>

<pre><code>                                |ownedBy^</code></pre>

Il requisito è che le citazioni dell'entità e il testo che definisce il tipo di relazione tra loro siano presenti in una sola frase potrebbe sembrare rigido. Tuttavia, tieni presente che, come nell'esempio precedente, finché non identifichi anche le coreferenze nel documento, puoi identificare le citazioni della relazione nelle frasi che contengono parole da utilizzare come citazioni dell'entità più informali, come i pronomi. Ad esempio, la seconda frase in `Mary is a scientist. She works for {{site.data.keyword.IBM_notm}}.` contiene la prova testuale valida di una relazione `employedBy` tra Mary e {{site.data.keyword.IBM_notm}}. La coreferenza, `She`, viene intesa come un riferimento al tipo di entità `PERSON` `Mary`. È l'identificazione di una coreferenza tra `Mary` e `She` più l'identificazione di una citazione della relazione tra `She` e `{{site.data.keyword.IBM_notm}}` di entrambi che acquisisce completamente questa relazione. Il modo corretto di annotare la citazione della relazione è in questo modo:

<pre><code>Mary[<i>#1</i>] is a scientist. <u>She</u>[<i>#1</i>] works for <u>IBM</u>.</code></pre>

<pre><code>                         |----employedBy----^</code></pre>

dove il pedice [<i>#1</i>] indica che `Mary` e `She` sono entrambi membri della prima catena di coreferenza nel documento.

### Procedura

Per annotare le citazioni della relazione tra le citazioni dell'entità in un documento:

1. Accedi come un annotatore umano (o come un amministratore o un gestore del progetto che era stato assegnato ai documenti da annotare). Vengono visualizzati gli spazi di lavoro che contengono le attività che ti sono state assegnate.
1. Apri un spazio di lavoro e poi fai clic su **Machine Learning Model** > **Annotation Tasks**. Vengono visualizzate le attività di annotazioni che ti sono state assegnate.
1. Apri l'attività di annotazione su cui vuoi lavorare. Vengono visualizzate le serie di annotazioni che ti sono state assegnate.
1. Fai clic su **Annotate** per aprire la serie di annotazioni su cui vuoi lavorare. Vengono visualizzati i documenti nella serie di annotazioni.
1. Apri il documento che vuoi annotare. Per impostazione predefinita, il documento viene aperto nella modalità **Citazione**, che è la modalità che utilizzi per annotare le citazioni dell'entità.
1. Fai clic su **Relations**. 
1. Per annotare una relazione:

    1. Fai clic su una citazione dell'entità nel testo e poi su una seconda nella stessa frase che vuoi collegare alla prima citazione.
    1. Seleziona il tipo di relazione che vuoi applicare dal pannello sulla destra o immetti il tasto di scelta rapida del tipo di relazione. L'elenco dei tipi di relazione disponibili è limitato dalla prima citazione dell'entità che selezioni e ulteriormente dalla seconda. In alcuni casi, rimane solo un tipo di relazione; devi ancora selezionare in modo esplicito il tipo di relazione per applicarlo.

        Se le linee guida di annotazione sono state precedentemente collegate allo spazio di lavoro e vuoi avere aiuto nella scelta dell'annotazione corretta da applicare, fai clic su **View Guidelines**. A seconda delle autorizzazioni di accesso configurate nel sito in cui sono ospitate le linee guida, potresti doverle aggiornare dopo averle aperte, ad esempio, per aggiungere chiarimenti ed esempi.
        {: tip}

1. Per rimuovere una citazione della relazione che hai appena aggiunto, premi Ctrl+Z per annullare l'azione. Per rimuovere la citazione della relazione in un secondo momento, puoi fare clic con il tasto sinistro sul tipo di relazione e poi premere il tasto **Delete** o fare clic sulla **X** accanto al tipo di relazione.
1. A seconda del sistema tipo, potresti essere in grado di configurare gli attributi di una relazione, come l'assegnazione di una classe, una modalità o un tempo della relazione. Se è così, seleziona una relazione e fai clic su **Attribute View**.
1. Fai clic su **Save** in qualsiasi momento per salvare il tuo lavoro.

### Operazioni successive

Dopo aver finito di annotare tutte le citazioni dell'entità, di relazione e le coreferenze nel documento, quando applicabile, modifica lo stato del documento da **In Progress** a **Completed**, fai clic su **Save** e poi chiudi il documento.

Dopo aver finito di annotare tutti i documenti e di averli contrassegnati con **Completed**, lo stato della serie di annotazioni viene modificato con **Submitted**. Questo è il modo in cui i gestori del progetto sanno che possono iniziare a valutare i documenti per l'accordo tra annotatori e rifiutarli o accettarli e promuoverli a ground truth.

## Informazioni correlate

[Creazione dei dizionari](/docs/services/watson-knowledge-studio/dictionaries.html)

[Risoluzione dei problemi con l'editor ground truth](/docs/services/watson-knowledge-studio/user-guide-help.html)

[Stabilire un sistema tipo ](/docs/services/watson-knowledge-studio/typesystem.html)
